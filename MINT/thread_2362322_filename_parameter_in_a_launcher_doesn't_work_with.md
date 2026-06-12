---
title: "filename parameter in a launcher doesn't work with gedit"
date: 2017-05-26
forum: MINT
---

### Post by ineuw on 2017-05-26
I am trying to launch gedit with an existing filename, but it opens a blank file. 

**gedit "/home/ineuw/Google Drive/installation order.txt"**

This is copied from the Linux Mint launcher, but I also tried it in the terminal with the same result. The community instructions mention anything about enclosing the path & filename with quotes when it contains spaces. 

What am I doing wrong?

---

### Post by howefield on 2017-05-26
Thread moved to the "*MINT*" forum.

You will have to escape the spaces in the path and file name.

---

### Post by ineuw on 2017-05-26
howefield, thanks for your reply, but it is meaningless as given. An example would have been most helpful. I tried 

[B]gedit /home/ineuw/"Google\ Drive"/"installation\ order.txt
gedit "/home/ineuw/Google\ Drive/installation\ order.txt"
gedit /home/ineuw/Google\ Drive/installation\ order.txt[/B]

none worked, so it's obvious I that I don't know what I am doing.

If you mean that you moved it to the Linux Mint forums, it is not there. It is not under my name, and no clue in which forum.

---

### Post by yancek on 2017-05-27
> **gedit "/home/ineuw/Google Drive/installation order.txt"**

The above entry is telling gedit to open a file named "Installation order.txt" in the Google Drive directory and if you did have a file named "Installation order.txt, it would open.  Easy to test.  Is that what you want?  Didn't think so.

If you are trying to open a file named order.txt in the Installation directory, you need to tell gedit that "Installation" is a directory by putting a forward slash after Installation as below.

> gedit "/home/ineuw/Google Drive/Installation/order.txt"


---

### Post by ineuw on 2017-05-27
yancek, thank you, and you were absolutely right. I pointed to the wrong folder. It should have been gedit "/home/ineuw/Google Drive**/linux/**installation order.txt", which unsurprisingly works fine. I blame this aberration to trying to get too much done all at once. Thanks again.

---

