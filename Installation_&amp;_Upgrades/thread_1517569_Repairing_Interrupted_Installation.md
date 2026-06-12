---
title: "Repairing Interrupted Installation"
date: 2010-06-25
forum: Installation &amp; Upgrades
---

### Post by abdullah.shafiq on 2010-06-25
Hi,
I was installing chromium web brower. During installation, the system got stuck and I had to reset my computer. Now when I try to install any software, the following error appears 

" The installation could have failed because of an error in the corresponding software package or it was cancelled in an unfriendly way. You have to repair this before you can install or remove any further software."

Please help me how to fix this. 
Thanks

---

### Post by lechien73 on 2010-06-25
Try opening a terminal window and typing:

```
sudo apt-get install -f
```

This will attempt to correct broken dependencies. Hope it helps :)

---

### Post by abdullah.shafiq on 2010-06-25
Hey thanks for reply.
When I run the command you told, it gives the following error 

"E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem".
And when I run "sudo dpkg --configure -a", it gives error  "dpkg: parse error, in file '/var/lib/dpkg/updates/0001' near line 0:  MSDOS EOF (^Z) in field name `"

I am new user of Ubuntu and don't know how to resolve it !

---

### Post by lechien73 on 2010-06-25
You can remove the offending update files and try again. So:

```
sudo rm /var/lib/dpkg/updates/*
sudo dpkg --configure -a
```

---

### Post by abdullah.shafiq on 2010-06-25
Hey thanks alot. The issue is resolved now  ! :)

---

### Post by lechien73 on 2010-06-25
Great - you're welcome :)

If you get chance, could you click on Thread Tools at the top of the thread and mark it as [Solved]?

Thanks

---

### Post by abdullah.shafiq on 2010-06-25
O yes, I was about to do it but had to go away thus forgot it.

Now I have marked it as Solved.

---

