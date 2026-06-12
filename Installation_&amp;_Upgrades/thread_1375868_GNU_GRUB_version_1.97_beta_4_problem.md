---
title: "GNU GRUB version 1.97 beta 4 problem"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by zzaets on 2010-01-08
After getting some updates like 3 days ago, I get this message: "minimal BASH-like editing is supported. For the first word TAB list possible command completions. Anywhere else TAB lists possible device/file completions.

sh:grub>_ 


What do I do to boot my system? Previously I was able to select from the grub menu. But not in this case. Any suggestions. I have an XP system as well on the same hard drive. I used wubi to install Ubuntu 9.10.

---

### Post by kansasnoob on 2010-01-08
Wubi has been a pain the past few days, sadly I know little to nothing about Wubi. You might want to look at these links:

[http://ubuntuforums.org/showthread.php?t=1375035&highlight=wubi+kansasnoob&page=2](http://ubuntuforums.org/showthread.php?t=1375035&highlight=wubi+kansasnoob&page=2)

Wish I could be more help.

---

### Post by drs305 on 2010-01-08
Welcome to Ubuntu zzaets!

See meierfra's post # 7.

---

### Post by Tutun on 2010-01-09
I also had the same problem........after following the instruction given by [centaure]("http://ubuntuforums.org/member.php?u=992677") in [http://ubuntuforums.org/showthread.php?p=8635224#post8635224](http://ubuntuforums.org/showthread.php?p=8635224#post8635224) the prob disappeared.......:)

---

### Post by stig3824 on 2010-01-09
I too had the same problem after updating from -16 to -17 and as per [Tutun]("http://ubuntuforums.org/member.php?u=994257") reply, the suggested fix worked for me.

---

### Post by weichimaster on 2010-01-09
I had this problem. I ended re-installing using the traditional approach, not wubi. (So now I have Grub as my primary boot manager.)

Thanks for the ideas here, though

---

### Post by meierfra. on 2010-01-09
Edit:  If you follow the links of various of the earlier suggestion, they  mostly all point to this solution: Boot into Windows and then follow these instructions:

[https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210]("https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210")

If that works you can ignore the rest of my post.

> 
```

ls
[COLOR="Red"]set root=(hdX,Y)[/COLOR]
linux /vmlinuz root=/dev/sdXY loop=/ubuntu/disks/root.disk ro
initrd /initrd.img
boot   # or CTRL-X

```


That is the wrong root for Wubi (it needs to be "(loop0)"). But since the OP got to the "grub" shell and not the "rescue>" shell,   "root" should already  be set correctly.  So just leave out the red line. If you don't know the correct parameters for "sdaXY" type

```
search -f /ubuntu/disk/root.disk
```
to determine the partition. hd0,1 usually means /dev/sda1, hd0,2 means /dev/sda2 and so on.

---

