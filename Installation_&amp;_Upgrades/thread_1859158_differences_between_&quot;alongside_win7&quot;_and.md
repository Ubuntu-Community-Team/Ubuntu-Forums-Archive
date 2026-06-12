---
title: "differences between &quot;alongside win7&quot; and &quot;something else&quot;"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by gepolv on 2011-10-13
[SIZE=3][SIZE=2]First of all, the stunning 11.10 is coming out and thank all of you who made this happen.

My question: 
when installing 11.10, there are 3 options:
1: alongside windows 7
2: replace windows 7 with ubuntu
3: something else.

What are the differences between Option 1 and Option 3?

Is Option 1 like wubi installation?

Thanks[/SIZE]    
[/SIZE]

---

### Post by Derek Karpinski on 2011-10-13
#1 automatically partitions your drive and lets you dual boot.
#2 erases windows and installs ubuntu
#3 lets you manually set up your partitions and mount points, and gives you the opportunity to dual boot, or erase. It's more 'hands on'.  A separate /home partition is recommended by most here.
 
Wubi, AFAIK, is a separate download/installation method.

---

### Post by oldfred on 2011-10-13
+1 on Derek Karpinski comments.

Auto install options only give you / and swap. They only work when system can automatically shrink (windows has room) and you have an available primary partition. 

Most Windows 7 installs use two primary partitions and the vendor uses two one for a recovery partition and a utility partition. MBR(msdos) only allows 4 primary partitions so Microsoft & vendor have used all to make it difficult to change. You then have to delete something.

---

