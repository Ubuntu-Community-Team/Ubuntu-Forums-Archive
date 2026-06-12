---
title: "Regarding Karmic (some questions)."
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ugriffin on 2009-10-19
Ok, I upgraded a spare PC to Karmic (and then reverted it to Jaunty due to sheer unstability. I'm selling that spare PC).

The Karmic experience was overall buggy (that's ok due to it being Beta), but I have a few questions regardless to all of you Karmic users (I downloaded the original Beta and haven't tried Karmic since. Thus, things could change).


1) Does the USplash-Xsplash combo work properly? I got text boot all the way to AppArmor, including FScheck. The Circle of Friends usplash before the actual XSplash sounds quite nice, trouble is, it doesn't work.

2) How on earth am I going to select my Windows partition if GRUB 2 won't give me a timeout option, and, apparently, the entire graphical selector is being pushed back? Alternatively, will this be pushed to Lucid or will we have to wait even longer?


Overall Karmic is a move forward and I understand it's bugginess... after all, it's a big leap. However, I depend on some Karmic features that have nothing to do with XSplash (Amarok 2.2. I hate using Banshee, personally), but I don't want a buggy system just for a few updated apps and some badly made eye-candy. Alternatively, if GRUB 2 is useless under Karmic (no Graphical selector), I might just upgrade Jaunty to Karmic and not do a full reinstall just to get GRUB 2.

Those are my little issues, I hope someone can clarify them.


Thanks in advance. :guitar:

---

### Post by cariboo on 2009-10-19
This is not the proper forum for your questions, it is not a support forum. Moved to Karmic Testing & Discussion.

---

### Post by ikt on 2009-10-20
> **ugriffin said:**
> 
1) Does the USplash-Xsplash combo work properly? I got text boot all the way to AppArmor, including FScheck. The Circle of Friends usplash before the actual XSplash sounds quite nice, trouble is, it doesn't work.

About a week or 2 ago it started to get very close, there is pretty much no text on my screen booting up. It's improving every day and I imagine will continue to improve on the way till 10.04.

> **ugriffin said:**
> 
2) How on earth am I going to select my Windows partition if GRUB 2 won't give me a timeout option, and, apparently, the entire graphical selector is being pushed back? Alternatively, will this be pushed to Lucid or will we have to wait even longer?


I'm not 100% but there will be a key (ie F2) that you can press to stop the boot up at grub or it will always have a longer timeout if there are other os's installed.

---

### Post by ugriffin on 2009-10-20
> **cariboo907 said:**
> This is not the proper forum for your questions, it is not a support forum. Moved to Karmic Testing & Discussion.

Sorry for that :(

Now, will Lucid have the graphical selector? Or is it being pushed back even further?

---

### Post by psyke83 on 2009-10-20
> **ugriffin said:**
> 1) Does the USplash-Xsplash combo work properly? I got text boot all the way to AppArmor, including FScheck. The Circle of Friends usplash before the actual XSplash sounds quite nice, trouble is, it doesn't work.

Works fine here.

> 2) How on earth am I going to select my Windows partition if GRUB 2 won't give me a timeout option, and, apparently, the entire graphical selector is being pushed back? Alternatively, will this be pushed to Lucid or will we have to wait even longer?

You can configure GRUB2 easily - you just need to know where to look. Edit /etc/default/grub - the timeout options are listed. Once you've finished editing the file, run "sudo update-grub" and the configuration will be updated.

---

### Post by forumache on 2009-10-20
> **ugriffin said:**
> 
2) How on earth am I going to select my Windows partition if GRUB 2 won't give me a timeout option, and, apparently, the entire graphical selector is being pushed back? Alternatively, will this be pushed to Lucid or will we have to wait even longer?


The timeout option works here. It is supposed to work like that:
- if you have only Ubuntu it will not give you an graphical selector. If you want it you need to press a key (I believe it is Esc).
- if it will detect Windows on your computer it will display the graphical selector and will allow you to choose.

I see the first behaviour at home (Linux only) and the second at work (Linux and Windows).

Everything works like it is supposed to do for me. If it does not work for you, you might want to enter a bug report.

---

