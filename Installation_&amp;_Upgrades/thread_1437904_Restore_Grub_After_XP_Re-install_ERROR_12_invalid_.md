---
title: "Restore Grub After XP Re-install ERROR 12: invalid device requested"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by pushkar_k on 2010-03-24
Hello ,
        My friend had Xp and ubuntu 9.04 Dual boot. He had some problems with Xp so he re-installed XP(only C:\ Drive was formatted). This wiped Grub .
         Then we tried to re-install grub by booting through ubuntu live cd(same cd which was used for ubuntu installation).

```
>sudo grub

>find /boot/grub/stage1                 //this worked fine
(hd0,5)

>root (hd0,5)

>setup(hd0)
```
        However ,the setup command gave Grub error 12 invalid device requested.
I had followed similar procedure before on different machine and it worked fine.
       Can someone explain what went wrong ?
       Is there some alternative to do this ?
       or some other method using live cd ?

---

### Post by andrewthomas on 2010-03-24
> **pushkar_k said:**
> Hello ,
        My friend had Xp and ubuntu 9.04 Dual boot. He had some problems with Xp so he re-installed XP(only C:\ Drive was formatted). This wiped Grub .
         Then we tried to re-install grub by booting through ubuntu live cd(same cd which was used for ubuntu installation).

```
>sudo grub

>find /boot/grub/stage1                 //this worked fine
(hd0,5)

>root (hd0,5)

>setup(hd0)
```        However ,the setup command gave Grub error 12 invalid device requested.
I had followed similar procedure before on different machine and it worked fine.
       Can someone explain what went wrong ?
       Is there some alternative to do this ?
       or some other method using live cd ?This should help you.
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by pushkar_k on 2010-03-24
Thanks for your reply . I had been to that page before. But it doesn't mention anything specific about error 12.

---

### Post by bumanie on 2010-03-25
Form a live ubuntu cd, post the output of > sudo fdisk -lI suspect you have windows installed in a logical partition and that's why it won't boot - of course, I could be wrong, but that output should clear that up, one way or another. That's a lower case L, not the digit one.

---

### Post by pushkar_k on 2010-03-25
Tried running " fdisk -l " through but it gave no output . Will menu.lst be helpful ?
Windows is installed on primary partition but ubuntu is installed on logical partition. Can that be the cause of the error ? If yes , then what's the solution ? thanks for your reply.

---

### Post by andrewthomas on 2010-03-25
> **pushkar_k said:**
> Windows is installed on primary partition but **ubuntu is installed on logical partition. Can that be the cause of the error ?** 
No, try to post the output of this script.
 
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[[COLOR=#444444]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

