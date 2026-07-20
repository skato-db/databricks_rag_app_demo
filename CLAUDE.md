# databricks_rag_app_demo — CLAUDE.md

本プロジェクトの開発ルールの**正本**。ここでは **ブランチ / PR 運用（GitHub Flow）** を定める。

---

## ブランチ戦略（GitHub Flow）— 厳守

これは交渉不可のルール。すべての作業はブランチを切ってから始める。

- `main` は**常にデプロイ可能**な状態を維持する。直接コミットしない。
- 1 ブランチ = 1 機能（または 1 Issue）。複数機能を混在させない。
- マージは**必ず Pull Request 経由**で行う。
- PR マージ後は**リモート・ローカル両方からブランチを削除**する。

命名規則:

```
feature/<topic>   # 機能開発
fix/<topic>       # バグ修正
docs/<topic>      # ドキュメント更新
chore/<topic>     # 依存・設定変更
```

作業の流れ:

```bash
git checkout main && git pull origin main
git checkout -b feature/<topic>
# 実装 → commit
git push -u origin feature/<topic>
gh pr create --base main --head feature/<topic>
# マージ後:
git push origin --delete feature/<topic>
git checkout main && git pull && git branch -d feature/<topic>
```
