---
title: "Kernel penic . not syncing: VFS: Unable to mount root fs on unknow-block(0,0)"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by Nordoelum on 2006-06-05
Greetings,

I have started to getting this error on boot. This is after I decided to remove usplash because I hated the Ubuntu splash when I used Xubuntu.

How ever. The removing took a while so I presses CTRL+C and did a reboot. But now I can't enter my computer :(

I did see the post similar to mine just below, but that didn't describe my problem. And I don't have a live CD.

---

### Post by Nordoelum on 2006-06-05
When I look at my boot setting. Is sais something like "root=/dev/hda1 ro quiet splash".

Can I remove that somehow?

---

### Post by Nordoelum on 2006-06-05
That didn't help at all :(

---

### Post by mcwtlg on 2006-06-05
I had a very similar problem.  I was upgrading from breezy to dapper and after a reboot and a usplash issue, I got the same error.  What I did was boot into the old kernel and reinstall the new kernel.  When I tested it and found it worked, I removed the old kernel.

YMMV.

---

### Post by tazzik on 2006-06-05
yup, i have the same problem when i try to go into rescue mode dont know what causes it or how to fix it

---

### Post by Nordoelum on 2006-06-05
The thing is though, that I remove every other kernel on the server :(

Can I boot into one that isn't there?

Ed1t: Thanks alot for the answear :D I thought no one wanted to help me :P

---

### Post by Nordoelum on 2006-06-05
I don't have the opertunity to burn an new 6.06 release CD. But I have an Breezy cd here. Can I use the kernel packed on that to recover the other kernel?

---

