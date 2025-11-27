---
layout: post
title: 測試策略：開發者如何寫出有效的測試
date: 2025-01-07 10:00:00
description: 分享 10 年開發經驗中，關於測試策略和測試寫法的心得。
tags: testing tdd quality-assurance
categories: methodology
---

測試是軟體開發中非常重要的一環，但很多開發者對測試有誤解。這篇文章分享我對測試的理解和實踐。

## 為什麼要寫測試？

1. **信心**：有測試的程式碼，重構時更有信心
2. **文件**：測試就是最好的文件，說明程式碼應該如何運作
3. **設計**：寫測試的過程，會強迫你思考設計
4. **回歸**：防止新功能破壞舊功能

## 測試金字塔

```
        /\
       /  \      E2E Tests (少)
      /____\
     /      \    Integration Tests (中)
    /________\
   /          \  Unit Tests (多)
  /____________\
```

- **Unit Tests**：測試單一函數或類別，應該最多
- **Integration Tests**：測試多個組件的整合
- **E2E Tests**：測試完整的使用流程，應該最少

## 如何寫好測試？

### 1. 測試行為，不是實現

```python
# ❌ 不好的測試：測試實現細節
def test_calculate_total():
    result = calculate_total([1, 2, 3])
    assert result._sum == 6  # 測試內部變數

# ✅ 好的測試：測試行為
def test_calculate_total():
    result = calculate_total([1, 2, 3])
    assert result == 6  # 測試公開介面
```

### 2. 一個測試一個概念

不要在一個測試中測試太多東西，每個測試應該只驗證一個概念。

### 3. 測試邊界情況

不只是測試「正常情況」，也要測試：
- 空值
- 極值
- 錯誤輸入
- 邊界值

### 4. 測試名稱要清楚

測試名稱應該清楚說明測試的內容：

```python
# ❌ 不清楚
def test_function():
    ...

# ✅ 清楚
def test_calculate_total_returns_sum_of_items():
    ...
```

## TDD 的實踐

TDD (Test-Driven Development) 的流程：

1. **Red**：寫一個會失敗的測試
2. **Green**：寫最少的程式碼讓測試通過
3. **Refactor**：重構程式碼，保持測試通過

TDD 不是萬能的，但在某些情況下很有用，特別是當需求很明確時。

## 結語

測試不是負擔，而是投資。好的測試能讓開發更快、更安全、更有信心。

---

*50 天寫作挑戰 Day 9*

