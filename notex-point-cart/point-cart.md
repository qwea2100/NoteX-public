# Notex Points Cart

WordPress + WooCommerce + myCred 點數購物車系統。

## 問題說明
1. 商品僅依附費筆記很難進行推廣，因此與行銷團隊共同決議開發免費點數筆記方案，透過會員日常累積點數換取心儀的免費筆記，提升會員黏著度。
2. 若有推廣需求(如工作坊、演講等場合)，可使用本平台推廣該講者的筆記，讓使用者快速取得筆記，並且以毫無摩擦力的方式完成平台的註冊與Line的帳號綁定。

---

## 專案結構

```
notex-points-cart/
├── notex-points-cart.php        ← 主入口：定義常數、載入所有子模組
└── includes/
    ├── product-meta.php         ← B. 商品後台欄位（允許用 Ns 點數付款）
    ├── gateway-control.php      ← C. 控制 myCred gateway 顯示條件
    ├── product-helpers.php      ← D. 商品分類工具、點數金額、使用者餘額查詢
    ├── cart-groups.php          ← E. 將購物車商品分為現金 / 非現金兩組
    ├── cart-renderer.php        ← F/H. 單列渲染 & 整區塊渲染（含兌換列表）
    ├── cart-ui.php              ← K. 覆蓋購物車頁，注入雙區 UI 與所有 CSS
    ├── cash-checkout.php        ← G/I. 現金結帳表單 & 暫存非現金商品流程
    ├── cart-restore.php         ← J. 回購物車時還原暫存的非現金商品
    ├── cart-guard.php           ← L. 防止非現金商品直接進入 checkout
    ├── user-library.php         ← M. 筆記庫查詢、新增、兌換紀錄
    ├── points-order.php         ← N. 建立 0 元點數訂單並自動完成
    ├── redeem.php               ← O/Q. 兌換 URL 產生 & 單筆立即兌換流程
    ├── thankyou.php             ← R. Thank you 頁顯示點數兌換結果
    ├── ux-guards.php            ← S. 移除再次訂購、已擁有提示、商品排序
    ├── cart-remove-toast.php    ← T. 購物車刪除通知
    └── free-claim.php           ← U. 免費筆記頁面連動
```

---

## 依賴套件

| 套件 | 用途 |
|------|------|
| WooCommerce | 購物車、訂單、商品系統 |
| myCred | 點數系統（餘額查詢、點數扣除） |

---

## 安裝方式

1. 將整個 `notex-points-cart/` 資料夾上傳到 `wp-content/plugins/`
2. 在 WordPress 後台啟用外掛
3. 確認 WooCommerce 與 myCred 已啟用

---

## 商品設定

進入商品編輯頁 → 一般 → 勾選「允許用 Ns 點數付款」，
該商品即會出現在購物車的「Ns 點數兌換筆記」區塊。

點數金額 = 商品的 WooCommerce 售價（自動換算為整數點數）。
