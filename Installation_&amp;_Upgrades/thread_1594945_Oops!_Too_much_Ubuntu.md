---
title: "Oops! Too much Ubuntu"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by zander x on 2010-10-12
I found myself needing Microsoft Windows XP because I absolutely needed to use Photoshop, so I tried to install it on the win partition. Of course, MS being MS, it "hid" my other OSes. I don't have any recovery tools but I remembered that Ubuntu install is smarter than the average bear and that it would give me my boot menu back and maybe just restore my old Ubuntu installation. 

Instead, it gave me a new Ubuntu installation that I don't need. How do I get rid of this newest Ubuntu 10.4 installation? And totally unrelated, is there a program that comes very close to PhotoShop (Adobe is greedy too)?

---

### Post by VMC on 2010-10-12
> **zander x said:**
> I found myself needing Micro$oft Window$ XP because I absolutely needed to use Photoshop, so I tried to install it on the win partition. Of course, M$ being M$, it "hid" my other OSes. I don't have any recovery tools but I remembered that Ubuntu install is smarter than the average bear and that it would give me my boot menu back and maybe just restore my old Ubuntu installation. 

Instead, it gave me a new Ubuntu installation that I don't need. How do I get rid of this newest Ubuntu 10.4 installation? And totally unrelated, is there a program that comes very close to Photo$hop (Adobe is greedy too)?

Lets start with how you tried to install the second Ubuntu. Was it to another partition? If so then the original Ubuntu is still intact.

I think what your wanting to do is recovery or re-install grub.

In re-reading your post, it looks like the second cup of Ubuntu was installed and your wanting to get rid of the first. I'm I close?

---

### Post by zander x on 2010-10-12
> **VMC said:**
> Lets start with how you tried to install the second Ubuntu. Was it to another partition? If so then the original Ubuntu is still intact.

I think what your wanting to do is recovery or re-install grub.

In re-reading your post, it looks like the second cup of Ubuntu was installed and your wanting to get rid of the first. I'm I close?

I installed the second Ubuntu to another partition. I *WAS* trying to do recovery or re-install grub but XP wiped out my menu and I'm not Ubuntu-classy enough yet to know how else to get in, so that's why I did an install thinking it might say "yo bro, you already have an installation of Ubuntu; do you want to just get back in?"

So what I want to do is keep the first install and get rid of the second (it ends in the word "pae").

---

### Post by faceless-21 on 2010-10-12
If you are looking for a linux version of PS then check out GIMP [http://www.gimp.org/downloads/](http://www.gimp.org/downloads/)  It is a very powerful photo editor that any "linux only" photographer will use for editing.  I myself either dual boot or use windows inside linux using virtual box and install PS inside that, its a tad slow but works well enough :)

---

### Post by scrooge_74 on 2010-10-12
There is even a Gimp version for Windows (not that I used it myself) 

[This]("http://www.ubuntugeek.com/how-to-restore-grub-boot-loader-after-installing-windows.html") may shed some light on your original problem

---

### Post by zander x on 2010-10-13
> **scrooge_74 said:**
> There is even a Gimp version for Windows (not that I used it myself) 

[This]("http://www.ubuntugeek.com/how-to-restore-grub-boot-loader-after-installing-windows.html") may shed some light on your original problem

I got the boot loader back, I just need to totally remove this second installation of Ubuntu.

---

### Post by VMC on 2010-10-13
> **zander x said:**
> I got the boot loader back, I just need to totally remove this second installation of Ubuntu.

You can use the livecd and run gparted(System>Administration>Gparted) to remove the Ubuntu partition in question. Do you know what the partition number is?

---

### Post by zander x on 2010-10-13
> **VMC said:**
> You can use the livecd and run gparted(System>Administration>Gparted) to remove the Ubuntu partition in question. Do you know what the partition number is?

I think sda7 is the new one (3 gigs used of 52 gigs unused) and sda5 is the old [present] one (11 used/56 unused).

---

### Post by oldos2er on 2010-10-13
[https://wiki.ubuntu.com/Grub2#Restore%20GRUB2%20-%20Recovering%20from%20a%20Windows%20XP%20/%20Vista%20/%207%20Reinstallation](https://wiki.ubuntu.com/Grub2#Restore%20GRUB2%20-%20Recovering%20from%20a%20Windows%20XP%20/%20Vista%20/%207%20Reinstallation)

---

### Post by zander x on 2010-10-13
> **oldos2er said:**
> [https://wiki.ubuntu.com/Grub2#Restore%20GRUB2%20-%20Recovering%20from%20a%20Windows%20XP%20/%20Vista%20/%207%20Reinstallation](https://wiki.ubuntu.com/Grub2#Restore%20GRUB2%20-%20Recovering%20from%20a%20Windows%20XP%20/%20Vista%20/%207%20Reinstallation)

Not only did that not work, now all I get is:

error: no such device: e2dc-7786
grub rescue>

---

### Post by wilee-nilee on 2010-10-14
Lets see the whole picture, post the bootscript in my signature, in code tags. The code tags can be generated by clicking on the # in the reply and putting the text in between. The script will show us what is where.

---

### Post by zander x on 2010-10-15
> **wilee-nilee said:**
> Lets see the whole picture, post the bootscript in my signature, in code tags. The code tags can be generated by clicking on the # in the reply and putting the text in between. The script will show us what is where.

Hey wilee-nilee; no worries beef curries! I stayed up a few more hours and got it back. I'm not sure how I did it, but it's back. I really like Ubuntu especially seeing as how in 4 months, its only crashed twice, but when it has technical problems, its scary.

Now the only problem is that Win 7 wants to wipe the entire HD to restore itself, so I need a tool to back up my entire Ubuntu installation.

---

