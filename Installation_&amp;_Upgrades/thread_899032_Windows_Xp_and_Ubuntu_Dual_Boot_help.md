---
title: "Windows Xp and Ubuntu Dual Boot help"
date: 2008-08-23
forum: Installation &amp; Upgrades
---

### Post by brucem91 on 2008-08-23
Hello. Recently, about 2 weeks ago, I was dual booting XP and Hardy via Wubi. Well, i turn on the computer after doing that for about a week, and the partition table is messed up. Luckily, all my files were on an external HD anyway. So I completly wiped the HD and installed Hardy Heron. Iv'e been playing around with/using various distros of linux for almost a year(Ubuntu, Fedora, Puppy). So I was completly fine. Well, one of my hobbies is video editing and vfx and such. I could do alot in Ubuntu, I tried a few apps, ect. But I realized I will still need XP for a few things. So I created a 34 gb partition to install XP on. The install worked great, but now I have one problem. I can't seem to boot Hardy Heron. Does this mean I have to open Gparted(I burned a live cd) and reorder the partitions, then edit grub in Ubuntu? How would I go about doing this. I wish for Ubuntu to be my main OS, and just fall back on XP for a small amount of things that I may need to do.

Thanks
Bruce

---

### Post by Partyboi2 on 2008-08-23
If you installed windows after you had install ubuntu you will need to restore the grub so you can boot into ubuntu. See [[COLOR=Blue]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351")

---

### Post by brucem91 on 2008-08-24
> **Partyboi2 said:**
> If you installed windows after you had install ubuntu you will need to restore the grub so you can boot into ubuntu. See [[COLOR=Blue]here[/COLOR]]("http://ubuntuforums.org/showthread.php?t=224351")
Sweet, thanks. I was able to get back into Ubuntu, using it now to type this message. Now I have another problem. How do I add windows xp to the grub list. I know I have to 

sudo gedit /boot/grub/menu.lst

and then something to the effect of

title Windows
map (hd0) (hd1)
map (hd1) (hd0)
root (hd1,0)
chainloader +1

would just that work. Windows XP is my second partiton. I included a picture of gparted with the two partitons.

Thanks

Bruce

---

