## Step 1 - Problem
Online Shopping Website တစ်ခုတည်ဆောက်နေတယ်လို့ စဉ်းစားကြည့်ပါ။
Team မှာ Developer သုံးယောက်ရှိတယ်။
-   Developer A - Product Page
-   Developer B - Shopping Cart
-   Developer C - Payment System

Developer တစ်ယောက်ချင်းစီက ကိုယ်တာဝန်ယူထားတဲ့ Feature အတွက် သီးခြား Branch တစ်ခုစီဖန်တီးပြီး Development လုပ်ကြမယ်။

Development ပြီးသွားတဲ့ အခါ အားလုံးရဲ့ ဖန်တီးထားတဲ့ ပြောင်းလဲမှုတွေကို `main` Branch ကို ပြန်ပေါင်းထည့်ရမှာပါ။

ဒါဆိုမေးစရာ တစ်ခုရှိလာပါပြီ။
### Branch တွေကို `main` Branch ထဲ ဘယ်လိုပြန်ပေါင်းထည့်မလည်းဆိုတာပါပဲ။
## Step 2 - Concept 
Git မှာ Branch တွေကို ပေါင်းစည်းဖို့ နည်းလမ်းအမျိုးမျိုးရှိပါတယ်။ အဓိက အသုံးပြုတာကတော့ နည်းလမ်း (၄) မျိုးရှိပါတယ်။
### 1. Fast-forward Merge 
`main` Branch ရဲ့ လက်ရှိ commit ဟာ `feature` Branch ရဲ့ History မှာပါဝင်နေပြီး `main` မှာ သီးခြား commit အသစ်မရှိတဲ့အခါ Git က Branch Pointer ကိုရှေ့တိုးပေးပြီး Merge လုပ်နိုင်ပါတယ်။ 

ဒီနည်းလမ်းမှာ Merge Commit အသစ်ဖန်တီးစရာမလိုပါဘူး။

### 2. Merge Commit
Branch နှစ်ခုရဲ့ History ကို မူလအတိုင်းထိန်းသိမ်းထားပြီး commit အသစ်တစ်ခုနဲ့ ပြန်လည်ချိတ်ဆက်ပေးတဲ့ နည်းလမ်းပဲ ဖြစ်ပါတယ်။

Merge လုပ်တဲ့အခါ Git က Parent နှစ်ခုပါဝင်တဲ့ Merge Commit အသစ်တစ်ခု ဖန်တီးပေးပါတယ်။
### 3. Squash Merge
`feature` Branch တစ်ခုမှာရှိတဲ့ commit အများအပြားရဲ့ ပြောင်းလဲမှုတွေကို commit တစ်ခုတည်းအဖြစ် စုစည်းပြီး လက်ရှိ Branch ထဲထည့်သွင်းတဲ့ နည်းလမ်းပဲဖြစ်ပါတယ်။

ဒီနည်းလမ်းက Feature တစ်ခုအတွက် commit အများကြီးလုပ်ထားပေမဲ့ `main` Branch ရဲ့ History ကို ပိုမိုရှင်းလင်း ရိုးရှင်းစွာ ထိန်းသိမ်းချင်တဲ့အခါ အသုံးဝင်ပါတယ်။
### 4. Rebase
`feature` Branch ရဲ့ commit တွေကို Base အသစ်အပေါ်ပြန်လည်အခြေခံပြီး commit အသစ်တွေအဖြစ် ပြန်ဖန်တီးပေးတဲ့ နည်းလမ်းဖြစ်ပါတယ်။

ဒီနည်းလမ်းက commit History ကို Linear ဖြစ်စေပြီး ပိုမိုသပ်ရပ်စွာ ထိန်းသိမ်းနိုင်စေပါတယ်။

သတိပြုရန် - Rebase လုပ်တဲ့အခါ commit အသစ်တွေပြန်ဖန်တီးတာ ဖြစ်တဲ့ အတွက် commit Hash တွေပြောင်းလဲသွားနိုင်ပါတယ်။
## Step 3 - Lab Start
### 1.  Lab လုပ်ဖို့အတွက် Folder ကို ဖန်တီးပြီး Git Repository ကို Initialize လုပ်ပါမယ်။
```bash
mkdir shopping-store-lab
cd shopping-store-lab
git init -b main
```
.   `mkdir` - Folder အသစ်တစ်ခုဖန်တီးတယ်။

.   `cd` - ဖန်တီးထားတဲ့ Folder ကို ဝင်မယ်။

.   `git init -b main` - Git Repository ကို Initialize လုပ်ပြီး Default Branch ကို main အဖြစ်သတ်မှတ်ပေးလိုက်မယ်။

### 2.   ပြီးရင် ပထမဆုံး File တစ်ခု ဖန်တီးပြီးတော့ first commit တစ်ခုလုပ်ပါမယ်။
```bash
echo "Online Shopping Store v1" > shop.txt
git add shop.txt
git commit -m "Create shopping store project"
```

.   `echo` - File ထဲထည့်မယ့်စာသားကို ရေးပေးလိုက်မယ်။

.   `>` - Output ကို File ထဲ ရေးပေးတယ်

.   `git add` - File ကို Staging Area ထဲ ထည့်ပေးတယ်။

.   `git commit` - Staging Area ထဲက ပြောင်းလဲမှုတွေကို Commit အဖြစ် သိမ်းဆည်းပေးပါတယ်။

### 3.   အခု git log နဲ့ commit History ကို ကြည့်ကြည့်ပါမယ်။ 
```bash
git log --oneline --graph --all
```

.   `--oneline` - commit တစ်ခုစီကို တစ်ကြောင်းတည်းပြပေးပါတယ်။

.   `--graph` - commit History ကို Graph ပုံစံနဲ့ပြပေးတယ်။

. `--all` - Git ကသိထားတဲ့ Branch အားလုံးရဲ့ History ကိုပြပေးပါတယ်။

### 4.  commit တစ်ခု ဖန်တီးသွားတာကို အခုလိုတွေရမှာပဲ ဖြစ်ပါတယ်။
```bash
* 784e855 (HEAD -> main) Create shopping store project
```

ဒီနေရာမှာ `784e855` က commit Hash ရဲ့ အတိုကောက်ဖြစ်ပြီး ကိုယ့်စက်မှာတော့ မတူညီတဲ့ Hash ဖြစ်နေပါလိမ့်မယ်။

`HEAD -> main` ဆိုတာ လက်ရှိ `HEAD` က `main` Branch ကို ညွှန်ပြနေပြီး `main` Branch ကလည်း ဒီပထမဆုံး commit ကို ညွှန်ပြနေတယ်လို့ ဆိုလိုပါတယ်။

## Step 4 - Fast-forward Merge
### Problem 
Developer A က Product Page ကို `feature-product` Branch မှာရေးသားနေတယ်လို့စဉ်းစားကြည့်ပါ။

လက်ရှိအခြေအနေမှာ `feature-product` Branch က `main` Branch ရဲ့ နောက်ဆုံး commit ကနေ လာတာဖြစ်ပြီးတော့ `main` Branch မှာ သီးခြား commit အသစ်လည်းမရှိသေးပါဘူး။

ဒါကြောင့် `feature-product` Branch ကို `main` Branch ထဲ `Fast-forward Merge`  နဲ့ ပေါင်းလိုက်လို့ရတာဖြစ်ပါတယ်။

### Lab 1 - Fast-forward Merge
### 5.  `feature-product` Branch ကို ဖန်တီးမယ်။
```bash
git switch -c feature-product
```
### 6. Product Page အတွက် ပြောင်းလဲမှု တစ်ခု ပြုလုပ်ပြီး commit ဖန်တီးမယ်။
```bash
echo "Product page" >> shop.txt
git add shop.txt
git commit -m "Add product page"
```
### 7.  commit History ကို စစ်ဆေးကြည့်မယ်။
```bash
git log --oneline --graph --all
```
### 8. အခု `HEAD` က `feature-product` Branch မှာရှိနေပြီး `main` Branch ကတော့ ပထမဆုံး Commit မှာပဲရှိပါသေးတယ်။
```bash
* 270d110 (HEAD -> feature-product) Add product page
* 784e855 (main) Create shopping store project
```
### 9. `main` Branch ကိုပြန်သွားပြီးတော့ `fast-forward` Merge လုပ်လိုက်မယ်။ 
```bash
git switch main
git merge feature-product
```
### 10.  Merge ပြီးရင် commit History ကို ပြန်စစ်ဆေးကြည့်လိုက်မယ်။
```bash
git log --oneline --graph --all
```
### 11. အခုဆိုရင် `main` နဲ့ `feature-product` Branch နှစ်ခုစလုံးက က `Add product page` commit  ကိုညွှန်ပြနေပါပြီ။
```bash
* 270d110 (HEAD -> main, feature-product) Add product page
* 784e855 Create shopping store project
```
### ဘာကြောင့် `Fast-forward` ဖြစ်တာလည်း?
`main` Branch ရဲ့ နောက်ဆုံး commit က `feature-product` Branch ရဲ့ commit History မှာရှိနေပြီး Branch နှစ်ခုရဲ့ History က မကွဲထွက်သေးလို့ ဖြစ်ပါတယ်။

ဒါကြောင်း Git က `Merge Commit` အသစ် မဖန်တီးပဲ `main` Branch Pointer ကို `feature-product` Branch ရဲ့ နောက်ဆုံး commit ဆီ ရှေ့တိုးပေးလိုက်တာပဲဖြစ်ပါတယ်။

## Step 5 - Merge Commit
### Problem
Developer B က Shopping Cart ဆိုတဲ့ feature ကို `feature-cart` Branch မှာရေးသားနေတယ်လို့ စဉ်းစားကြည့်ပါ။

Developer B က Feature အတွက် commit အသစ်တစ်ခု ဖန်းတီးထားတဲ့ အချိန်မှာ `main` Branch မှာလည်း တခြား commit အသစ်တစ်ခု ရှိလာတယ်ဆိုပါစို့။

ဒီ အခြေအနေမှာ Branch နှစ်ခုစလုံးက မူလ commit တစ်ခုတည်းကနေ သီးခြား commit တွေနဲ့ ဆက်လက် သွားတာဖြစ်ပါတယ်။

ဒါကို `Diverged History` လို့ ခေါ်ပါတယ်။

Branch နှစ်ခုရဲ့ History ကို ပြန်ပေါင်းစည်းဖို့ အတွက် `Merge Commit` ကို အသုံးပြုကြည့်ပါမယ်။ 
### Lab 2 - Merge Commit
### 12. `feature-cart` Branch ကို ဖန်တီးမယ်။
```bash
git switch -c feature-cart
```
### 13. Shopping Cart အတွက် commit အသစ် တစ်ခုဖန်တီးမယ်။
```bash
echo "Shopping cart" >> shop.txt
git add shop.txt
git commit -m "Adding shopping cart"
```
### 14. commit History ကို စစ်ဆေးမယ်။
```bash
git log --oneline --graph --all
```
### 15.  `feature-cart` Branch commit အသစ်တစ်ခုတိုးလာတာကို တွေ့ရပါမယ်။  

```bash
* d751bc1 (HEAD -> feature-cart) Adding shopping cart
* 270d110 (main, feature-product) Add product page
* 784e855 Create shopping store project
```
ဒီအချိန်မှာ `HEAD` က `feature-cart` Branch မှာရှိနေပါတယ်။

`main` Branch ကတော့ `Add product page` commit မှာပဲရှိပါသေးတယ်။
### 16.  `main` Branch မှာလည်း သီးခြား commit အသစ်တစ်ခု ဖန်တီးပါမယ်။
```bash
git switch main
echo "Store homepage" >> shop.txt
git add shop.txt
git commit -m "Add store homepage"
```
အခုဆိုရင် `main` နဲ့ `feature-cart` Branch နှစ်ခုစလုံးမှာ သီးခြား commit ကိုယ်စီရှိလာပါပြီ။

### 17.  commit History ကို ထပ်မံစစ်ဆေးကြည့်မယ်။
```bash
git log --oneline --graph --all
```
### 18.  Branch နှစ်ခုရဲ့ History ကွဲထွက်နေတာကို တွေ့ရမယ်။
```bash
* f688b4e (HEAD -> main) Add store homepage
| * d751bc1 (feature-cart) Adding shopping cart
|/  
* 270d110 (feature-product) Add product page
* 784e855 Create shopping store project
```
`main` Branch မှာ `Add store homepage` commit ရှိနေပြီး `feature-cart` Branch မှာ `Adding shopping cart` commit ရှိနေပါတယ်။

commit နှစ်ခုစလုံးက `Add product page` commit ကို အခြေခံပြီး သီးခြား ခွဲထွက်သွားတာပဲ ဖြစ်ပါတယ်။

### 19.  `feature-cart` Branch ကို `main` ထဲ Merge လုပ်မယ်။
```bash
git merge --no-ff feature-cart -m "Merge shopping cart"
```
.   `git merge` - Branch နှစ်ခုကို ပေါင်းစည်းဖို့။

.   `--no-ff` - Fast-forward ဖြစ်နိုင်တဲ့ အခြေအနေမျိုးမှာတောင် `Merge Commit` ဖန်းတီးစေဖို့။

### 20.  `main` နဲ့ `feature-cart` Branch နှစ်ခုလုံးက shop.txt ရဲ့ တူညီတဲ့နေရာမှာ  ပြောင်းလဲမှုလုပ်ထားလို့ git က Auto-merging လုပ်မရပါဘူး။

ဒါကို `Merge Confilct` လို့ခေါ်ပါတယ်။

ဒီအချိန်မှာ Merge လုပ်ငန်းစဉ် မပြီးဆုံးသေးပါဘူး။ Conflict ကို ဖြေရှင်းပြီးမှ `Merge Commit` ကို အပြီးသတ်နိုင်မှာဖြစ်ပါတယ်။
```bash
Auto-merging shop.txt
CONFLICT (content): Merge conflict in shop.txt
Automatic merge failed; fix conflicts and then commit the result.
```
## Step 6 - Resolve Merge Conflict
### Problem
`feature-cart` Branch ကို `main` Branch ထဲ Merge လုပ်တဲ့အခါ `shop.txt` file မှာ Merge Conflict ဖြစ်ခဲ့ပါတယ်။

Branch နှစ်ခုစလုံးက ဖိုင်ရဲ့ တူညီတဲ့နေရာမှာ စာကြောင်းအသစ်တွေထည့်ထားတဲ့ အတွက် Git က ဘယ်အပြောင်းအလဲကို ထားရမလည်းဆိုတာကို အလိုအလျောက် မဆုံးဖြတ်နိုင်တာမျိုးဖြစ်ပါတယ်။

### Lab 3 - Resolve Merge Conflict
### 21. Conflict ဖြစ်နေတဲ့ `shop.txt` ကိုဖွင့်ကြည့်မယ်။
```bash
cat shop.txt
```
File ထဲမှာ အောက်ပါအတိုင်း Conflict Marker တွေကို တွေ့ရနိုင်ပါတယ်။
```bash
Online Shopping Store v1
Product page
<<<<<<< HEAD
Store homepage
=======
Shopping cart
>>>>>>> feature-cart
```
### 22.  Conflict ဖြစ်နေတာတွေကို ပြင်ပြီး save လုပ်လိုက်ပါမယ်။

Store homepage နဲ့ Shopping cart နှစ်ခုစလုံးကို သိမ်းထားချင်တဲ့အတွက် shop.txt ဖိုင်ထဲက Conflict Marker တွေကို ဖယ်ရှားပြီး အောက်ပါအတိုင်း ပြင်ဆင်မယ်။

```bash
Online Shopping Store v1
Product page
Store homepage
Shopping cart
```
### 23.  Conflict ဖြေရှင်းပြီးသွားတဲ့ အခြေအနေကို ပြန်လည်စစ်ဆေးကြည့်ပါမယ်။

```bash
git status
```
Conflict Marker တွေကို ဖယ်ရှားပြီး ဖိုင်ကို Save လုပ်ထားရုံနဲ့ Git က Conflict ဖြေရှင်းပြီးပြီလို့ မသတ်မှတ်သေးပါဘူး။

### 24. Conflict ဖြေရှင်းပြီး Merge Commit ကို အပြီးသတ်ရပါမယ်။
```bash
git add shop.txt
git commit -m "Resolve shopping cart merge conflict"
```
### 25. git log ထုတ်ကြည့်လိုက်ပါမယ်။
```bash
git log --oneline --graph --all
```
### 26.  Branch နှစ်ခုရဲ့ History ကို Merge commit နဲ့ ပြန်ချိတ်ထားတာကို မြင်ရပါမယ်။
```bash
*   bd70d52 (HEAD -> main) Resolve shopping cart merge conflict
|\  
| * d751bc1 (feature-cart) Adding shopping cart
* | f688b4e Add store homepage
|/  
* 270d110 (feature-product) Add product page
* 784e855 Create shopping store project
```
ဒီ Merge Commit မှာ Parent Commit နှစ်ခုရှိပါတယ်။

.   `Add store homepage` — main Branch ဘက်က commit

.   `Adding shopping cart` — feature-cart Branch ဘက်က commit

## Step 7 - Squash Merge
### Problem
Developer တစ်ယောက်က Checkout Feature ကို `feature-checkout` Branch မှာ ရေးနေတယ်လို့ စဉ်းစားကြည့်ပါ။

Feature တစ်ခု ပြီးမြောက်ဖို့ commit နှစ်ခု ဖန်တီးထားတယ်ဆိုပါစို့။ 

.   `Add checkout page`

.   `Add order confirmation page`

ဒီ commit နှစ်ခုရဲ့ အပြောင်းအလဲတွေကို `main` Branch ထဲ ပေါင်းစည်းတဲ့အခါ commit တစ်ခု တစ်ခုတည်းအဖြစ် စုစည်းသိမ်းဆည်းချင်တယ်ဆိုရင် `Squash Merge` ကို အသုံးပြုနိုင်ပါတယ်။

Squash Merge က Feature Branch ရဲ့ အပြောင်းအလဲတွေကို စုစည်းပြီး Current Branch ရဲ့ Staging Area ထဲ ထည့်ပေးတာဖြစ်ပါတယ်။

### Lab 4 - Squash Merge
### 27.  `feature-checkout` ကို ဖန်တီးပြီး ပထမဆုံး commit တစ်ခု ပြုလုပ်လိုက်ပါမယ်။

```bash
git switch -c feature-checkout
```
```bash
echo "Checkout page" >> shop.txt
git add shop.txt
git commit -m "Add checkout page"
```
### 28. Commit History ကို စစ်ဆေးမယ်။
```bash
git log --oneline --graph --all
```
### 29. `feature-checkout` Branch မှာ Commit အသစ်တစ်ခု ရှိလာတာကို တွေ့ရမယ်။
```bash
* 3a3299f (HEAD -> feature-checkout) Add checkout page
*   bd70d52 (main) Resolve shopping cart merge conflict
|\  
| * d751bc1 (feature-cart) Adding shopping cart
* | f688b4e Add store homepage
|/  
* 270d110 (feature-product) Add product page
* 784e855 Create shopping store project
```
လက်ရှိ `HEAD` က `feature-checkout` Branch မှာရှိနေပါတယ်။

### 30. Order Confirmation Page အတွက် ဒုတိယ commit ဖန်တီးမယ်။
```bash
echo "Order confirmation page" >> shop.txt
git add shop.txt
git commit -m "Add order confirmation page"
```
### 31. Commit History ကို ထပ်မံစစ်ဆေးမယ်။
```bash
git log --oneline --graph --all
```
### 32. `feature-checkout` Branch မှာ commit နှစ်ခု ရှိလာတာကို တွေ့ရပါမယ်။
```bash
* f3d0c37 (HEAD -> feature-checkout) Add order confirmation page
* 3a3299f Add checkout page
*   bd70d52 (main) Resolve shopping cart merge conflict
|\  
| * d751bc1 (feature-cart) Adding shopping cart
* | f688b4e Add store homepage
|/  
* 270d110 (feature-product) Add product page
* 784e855 Create shopping store project
```
### 33. အခု`main` Branch ထဲပြန်သွားပြီး `feature-checkout` Branch ကို Squash Merge လုပ်ပါမယ်။
```bash
git switch main
git merge --squash feature-checkout
```
```bash
git status
```
ဒီအချိန်မှာ Git က `feature-checkout` Branch ရဲ့ အပြောင်းအလဲတွေကို စုစည်းပြီး Staging Area ထဲ ထည့်ပေးထားတာပါ။

ဒါပေမဲ့ commit အသစ်တစ်ခုကို မဖန်တီးရသေးပါဘူး။

ဒီအပြောင်းအလဲကို commit တစ်ခုတည်းအဖြစ်သိမ်းဆည်းလိုက်ပါမယ်။
```bash
git commit -m "Add checkout feature"
```
### 34. Commit History ကို စစ်ဆေးမယ်။
```bash
git log --oneline --graph --all
```
### 35. အခုလိုတွေ့ရမှာပဲ ဖြစ်ပါတယ်။ 
ဒီနည်းနဲ့ `feature-checkout` Branch ရဲ့ ပြောင်းလဲမှုတွေကို `main` Branch ထဲမှာ `Add checkout feature` ဆိုတဲ့ Commit တစ်ခုတည်းအဖြစ်သိမ်းလိုက်တာပါ။ `feature-checkout` Branch မှာ မူရင်း Commit နှစ်ခုရှိသေးပေမဲ့ `main` Branch မှာ Checkout အတွက် Commit တစ်ခုတည်း ဖြစ်နေတာကို သတိထားကြည့်ပါ။
```bash
* 22eaacd (HEAD -> main) Add checkout feature
| * f3d0c37 (feature-checkout) Add order confirmation page
| * 3a3299f Add checkout page
|/  
*   bd70d52 Resolve shopping cart merge conflict
|\  
| * d751bc1 (feature-cart) Adding shopping cart
* | f688b4e Add store homepage
|/  
* 270d110 (feature-product) Add product page
* 784e855 Create shopping store project
```
## Step 8 - Rebase
### Problem
Developer C က Payment System ကို feature-payment Branch မှာ ရေးသားနေတယ်လို့ စဉ်းစားကြည့်ပါ။

Developer C က Payment Feature အတွက် Commit အသစ်တစ်ခု ဖန်တီးထားတဲ့အချိန်မှာ main Branch မှာလည်း Add customer profile ဆိုတဲ့ Commit အသစ်တစ်ခု ရှိလာတယ်ဆိုပါစို့။

ဒီအခြေအနေမှာ main နဲ့ feature-payment Branch နှစ်ခုရဲ့ Commit History က ကွဲထွက်သွားပါပြီ။

feature-payment Branch ရဲ့ Commit ကို main Branch ရဲ့ နောက်ဆုံး Commit အပေါ်မှာ ပြန်လည်အသုံးချဖို့ Rebase ကို အသုံးပြုကြည့်ပါမယ်။ 

### Lab 5 - Rebase 
### 36. feature-payment Branch ကို ဖန်တီးပြီး Commit တစ်ခု ပြုလုပ်မယ်။
```bash
git switch -c feature-payment
```
```bash
echo "Payment system" >> shop.txt
git add shop.txt
git commit -m "Add payment system"
```
### 37. Commit History ကို စစ်ဆေးမယ်။ 
```bash
git log --oneline --graph --all
```
### 38. feature-payment Branch မှာ Commit အသစ်တစ်ခု ရှိလာတာကို တွေ့ရမယ်။
```bash
* 4e03225 (HEAD -> feature-payment) Add payment system
* 22eaacd (main) Add checkout feature
| * f3d0c37 (feature-checkout) Add order confirmation page
| * 3a3299f Add checkout page
|/  
*   bd70d52 Resolve shopping cart merge conflict
|\  
| * d751bc1 (feature-cart) Adding shopping cart
* | f688b4e Add store homepage
|/  
* 270d110 (feature-product) Add product page
* 784e855 Create shopping store project
```
လက်ရှိ HEAD က `feature-payment` Branch မှာရှီနေပါတယ်။

### 39. main Branch မှာ သီးခြား Commit အသစ်တစ်ခု ဖန်တီးမယ်။
```bash
git switch main
echo "Customer profile" >> shop.txt
git add shop.txt
git commit -m "Add customer profile"
```

အခုဆိုရင် main Branch မှာ Add customer profile Commit ရှိလာပြီး feature-payment Branch မှာ Add payment system Commit ရှိနေပါတယ်။

### 40. Commit History ကို ထပ်မံစစ်ဆေးမယ်။
```bash
git log --oneline --graph --all
```
### 41. Branch နှစ်ခုရဲ့ History ကွဲထွက်နေတာကို တွေ့ရမယ်။
```bash
* 769d66c (HEAD -> main) Add customer profile
| * 4e03225 (feature-payment) Add payment system
|/  
* 22eaacd Add checkout feature
| * f3d0c37 (feature-checkout) Add order confirmation page
| * 3a3299f Add checkout page
|/  
*   bd70d52 Resolve shopping cart merge conflict
|\  
| * d751bc1 (feature-cart) Adding shopping cart
* | f688b4e Add store homepage
|/  
* 270d110 (feature-product) Add product page
* 784e855 Create shopping store project
```

commit နှစ်ခုစလုံးက `Add checkout feature` commit ကို အခြေခံပြီး သီးခြားစီကွဲထွက်သွားတာ ဖြစ်ပါတယ်။

### 42.  feature-payment Branch ကို main Branch အပေါ် Rebase လုပ်မယ်။
```bash
git switch feature-payment
git rebase main
```
### 43.  ဒီတစ်ခါလည်း `main` နဲ့ `feature-payment` Branch နှစ်ခုလုံးက commit တွေမှာ `shop.txt` ကို နေရာတစ်ခုတည်းမှာ ပြင်ဆင်မိထားလို့ merge conflict တက်သွားတာပါ။
```bash
Switched to branch 'feature-payment'
Auto-merging shop.txt
CONFLICT (content): Merge conflict in shop.txt
error: could not apply 4e03225... Add payment system
```
## Step 9 - Resolve Rebase Conflict
### Problem
feature-payment Branch ကို main Branch အပေါ် Rebase လုပ်တဲ့အခါ shop.txt ဖိုင်မှာ Conflict ဖြစ်ခဲ့ပါတယ်။

main Branch မှာ Customer profile ကို ထည့်ထားပြီး feature-payment Branch မှာ Payment system ကို တူညီတဲ့နေရာမှာ ထည့်ထားတာကြောင့် Git က အလိုအလျောက် ပေါင်းစည်းလို့ မရခဲ့ပါဘူး။

ဒါကြောင့် Conflict ကို ကိုယ်တိုင်ဖြေရှင်းပြီး Rebase လုပ်ငန်းစဉ်ကို ဆက်လက်လုပ်ဆောင်ရပါမယ်။
### Lab 6 - Resolve Rebase Conflict
### 44. Conflict ဖြစ်နေတဲ့ `shop.txt` ဖိုင်ကို စစ်ဆေးကြည့်ပါမယ်။

```bash
cat shop.txt
```
```bash
Online Shopping Store v1
Product page
Store homepage
Shopping cart
Checkout page
Order confirmation page
<<<<<<< HEAD
Customer profile
=======
Payment system
>>>>>>> 4e03225 (Add payment system)
```
### 45. Conflict ကို ဖြေရှင်းမယ်။ 
Customer profile နဲ့ Payment system နှစ်ခုစလုံးကို သိမ်းထားချင်တဲ့အတွက် အောက်ပါအတိုင်း ပြင်ဆင်လိုက်ပါမယ်။
```bash
Online Shopping Store v1
Product page
Store homepage
Shopping cart
Checkout page
Order confirmation page
Customer profile
Payment system
```
ပြင်ဆင်ပြီးတဲ့အခါ shop.txt ဖိုင်ကို Save လုပ်ပါမယ်။

### 46. Conflict ဖြေရှင်းပြီး Rebase ကို ဆက်လုပ်မယ်။
```bash
git add shop.txt
git rebase --continue
``` 

`git add shop.txt` က Conflict ဖြေရှင်းထားတဲ့ File ကို Staging Area ထဲသို့ ထည့်သွင်းပြီး Stage လုပ်ပေးပါတယ်။

git rebase --continue က ခေတ္တရပ်ထားတဲ့ Rebase လုပ်ငန်းစဉ်ကို ဆက်လက်လုပ်ဆောင်ပေးပါတယ်။

Commit Message Editor ပွင့်လာရင် မူလ Commit Message ကို ထားပြီး Save လုပ်ကာ Editor ကို ပိတ်နိုင်ပါတယ်။ 

### 47. Rebase ပြီးဆုံးသွားတဲ့အခါ Commit History ကို စစ်ဆေးမယ်။
```bash
git log --oneline --graph --all
```
### 48. feature-payment Branch ရဲ့ Commit ကို Base အသစ်အပေါ် ပြန်လည်ဖန်တီးထားတာကို တွေ့ရမယ်။

```bash
* 07cf26a (HEAD -> feature-payment) Add payment system
* 769d66c (main) Add customer profile
* 22eaacd Add checkout feature
| * f3d0c37 (feature-checkout) Add order confirmation page
| * 3a3299f Add checkout page
|/  
*   bd70d52 Resolve shopping cart merge conflict
|\  
| * d751bc1 (feature-cart) Adding shopping cart
* | f688b4e Add store homepage
|/  
* 270d110 (feature-product) Add product page
* 784e855 Create shopping store project
```
Rebase မလုပ်ခင် Add payment system commit ရဲ့ Hash က 4e03225 ဖြစ်ခဲ့ပါတယ်။

Rebase ပြီးနောက်မှာတော့ 07cf26a ဆိုတဲ့ Hash အသစ်နဲ့ commit ကို ပြန်လည်ဖန်တီးထားတာ တွေ့ရပါတယ်။

ဒီအချိန်မှာ HEAD က `feature-payment` Branch ပေါ်မှာ ရှိနေပြီး `main` Branch က `Add customer profile` commit မှာပဲ ရှိနေသေးပါတယ်။

### 49. Rebase ပြီးဆုံးသွားကြောင်း စစ်ဆေးမယ်။

```bash
git status
```
Rebase အောင်မြင်စွာ ပြီးဆုံးသွားပြီး Working Tree မှာ တခြားအပြောင်းအလဲ မရှိရင် အောက်ပါအတိုင်း တွေ့ရပါမယ်။

```bash
On branch feature-payment
nothing to commit, working tree clean
```

### 50. အခုဆို `main` Branch ကိုသွားပြီး  `feature-payment` Branch ကို `fast-forward` Merge လုပ်လိုက်ပါမယ်။
```bash
git switch main
git merge feature-payment
```
Rebase ပြီးနောက် main Branch ရဲ့ နောက်ဆုံး Commit က feature-payment Branch ရဲ့ History ထဲမှာ ရှိနေပြီးသားဖြစ်လို့ Fast-forward Merge လုပ်နိုင်ပါတယ်။

ဒီအဆင့်မှာ Merge Commit အသစ် မဖန်တီးဘဲ main Branch Pointer ကို ရှေ့တိုးပေးမှာ ဖြစ်ပါတယ်။
### 51. Merge ပြီးနောက် Commit History ကို စစ်ဆေးမယ်။
```bash
git log --oneline --graph --all
```
### 52. `main` နဲ့ `feature-payment` Branch နှစ်ခုစလုံးက Commit တစ်ခုတည်းကို ညွှန်ပြနေတာကို တွေ့ရမယ်။

```bash
* 07cf26a (HEAD -> main, feature-payment) Add payment system
* 769d66c Add customer profile
* 22eaacd Add checkout feature
| * f3d0c37 (feature-checkout) Add order confirmation page
| * 3a3299f Add checkout page
|/  
*   bd70d52 Resolve shopping cart merge conflict
|\  
| * d751bc1 (feature-cart) Adding shopping cart
* | f688b4e Add store homepage
|/  
* 270d110 (feature-product) Add product page
* 784e855 Create shopping store project
```