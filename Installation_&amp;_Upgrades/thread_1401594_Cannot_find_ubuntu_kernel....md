---
title: "Cannot find ubuntu kernel..."
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by vasiq on 2010-02-08
Hi guys...I'm not able to boot the Ubuntu 9.10 OS in my HP Laptop..after the installation it was working perfectly for 2 days and today I updated this "linux general image" file and when I restarted my Laptop ..i got this on my screen..

[B]GNU GRUB version 1.97~Beta4
[Minimal BASH-Like line editing is supported. For the first word. TAB lists possible command completions. Anywhere else TAB lists possible device/file operations.]

sh:grub>[/B]

Any help on this..guys

---

### Post by Madmoose on 2010-02-08
Hey, 

I got this too on my HP Pavilion dv2000. Anyone know what's up? 

Thanks

---

### Post by Madmoose on 2010-02-08
Vasiq, 

If you're running wubi installation like I am I followed the link below, and replaced the wubildr file in my c:/. After replacing it with the new one everything was back to normal. Give that a try. Here is the link: 

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

---

### Post by Madmoose on 2010-02-08
You can also dig through this post if that didn't work for you.

[http://ubuntuforums.org/showthread.php?t=1321107&highlight=Bash-like]("http://ubuntuforums.org/showthread.php?t=1321107&highlight=Bash-like")

 This is where I found the suggestion to replace that file in the first place. I hope you find your solution.

---

