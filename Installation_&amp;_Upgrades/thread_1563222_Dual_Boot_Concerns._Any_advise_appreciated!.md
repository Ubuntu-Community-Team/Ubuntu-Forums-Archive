---
title: "Dual Boot Concerns. Any advise appreciated!"
date: 2010-08-28
forum: Installation &amp; Upgrades
---

### Post by JoshDN on 2010-08-28
Ubuntu Community,

I have a hp zv6000 with XP and 9.10 WUBI, which works great. I would like to get rid of WUBI and do a dual boot, installing Ubuntu on it's own partition. I am familiar with the procedure, but i have a few minor concerns I would like opinions on. My greatest concern is I don't have the winXP CD that came with this computer, so if I have a booting problem down the road I might not be able to use the "fixmbr" program. However I do have a winXP CD for a Compaq computer. Would that CD also work for the hp for fixing the MBR?

I apologize that this is more of a windows question, but I'm sure there are plenty of dual booters with this knowledge. My preference would be to get rid of windows altogether, but I still have need for some proprietary programs:(.

Also, please let me know if you feel that any problems I may encounter could be solved entirely without a win CD. (This includes windows problems, which are most likely anyway.)

Thanks!!

---

### Post by xtracool_protik on 2010-08-28
Hi Josh,
 Here are few things u need to check for dual boot:
 1. Do u already have separate drive for Ubuntu/linux installation?
 2. If no r u willing to format and change drive mapping? - u'll lose ur windows drive and installation. And if u do that u'll need Windows CD/DVD to reinstall it. As much as I know u can't use compaq CD to install on ur HP (different machine)
 3. If yes for step 1 then just go ahead and install Ubuntu on separate drive - u won't have to worry about booting. it would be same as u see now for Wubi (only difference is Ubuntu will be shown with kernel)
 4. if u r through 2/3 steps then u will have windows as well as Ubuntu without any issue. U'll face problem only if u install windows after Ubuntu in that case there are few posts around let me know I'll point out one for u

 Hope that helps :)

---

### Post by presence1960 on 2010-08-28
> **JoshDN said:**
> Ubuntu Community,

I have a hp zv6000 with XP and 9.10 WUBI, which works great. I would like to get rid of WUBI and do a dual boot, installing Ubuntu on it's own partition. I am familiar with the procedure, but i have a few minor concerns I would like opinions on. My greatest concern is I don't have the winXP CD that came with this computer, so if I have a booting problem down the road I might not be able to use the "fixmbr" program. However I do have a winXP CD for a Compaq computer. Would that CD also work for the hp for fixing the MBR?

I apologize that this is more of a windows question, but I'm sure there are plenty of dual booters with this knowledge. My preference would be to get rid of windows altogether, but I still have need for some proprietary programs:(.

Also, please let me know if you feel that any problems I may encounter could be solved entirely without a win CD. (This includes windows problems, which are most likely anyway.)

Thanks!!

You can fix the MBR to be a windows MBR by booting the ubuntu live cd, boot to desktop and open a terminal. Run ```
sudo apt-get install lilo
```Ignore warnings. This will install lilo to the live session. Then from terminal run ```
sudo lilo -M /dev/sdX mbr
```where x = your disk, i.e. sda, sdb sdc, etc. Reboot without live cd and you will boot right to windows.

---

### Post by JoshDN on 2010-08-28
> 1. Do u already have separate drive for Ubuntu/linux installation?No.
> 2. If no r u willing to format and change drive mapping? - u'll lose ur  windows drive and installation. And if u do that u'll need Windows  CD/DVD to reinstall it. As much as I know u can't use compaq CD to  install on ur HP (different machine)I'm pretty sure I won't loose windows if I select the install side by side option. All the partitioning is done automatically. I know I can't use the compaq CD to install windows on the HP, I just need to know if i can use it for the FixMBR utility on it.
> sudo apt-get install lilo Thats very interesting. I had thought the LInux LOader was dead since GRUB. I'm not saying I don't believe you, I'm just curious how that works. I'm still very new at linux, so further explanation would be great.

Thanks for all the input so far!

---

### Post by Rubi1200 on 2010-08-28
According to their website, Lilo is actively maintained:
[http://lilo.alioth.debian.org/](http://lilo.alioth.debian.org/)

I have seen a few posts here where it has been suggested to use it in certain situations.

Hope this helps.

---

### Post by dFlyer on 2010-08-28
If you have an external hd, download Macrium which is free and clone xp before you begin. That way should you have problem you can always restore xp. As far as I know only an hp xpwin cd can be installed you your hp.

---

### Post by JoshDN on 2010-08-28
> **Rubi1200 said:**
> According to their website, Lilo is actively maintained:
[http://lilo.alioth.debian.org/](http://lilo.alioth.debian.org/)

I have seen a few posts here where it has been suggested to use it in certain situations.

Hope this helps.

I checked the link out and it looks like the project was recently restarted. I just thought that it was interesting because I was just reading the GRUB2 manual on the GNU website which gives LILO a bad name. They describe LILO as the boot loader that "everyone uses, but no one likes". Thats why the suggestion was interesting to me.

So let me make sure I understand all this. If i install LILO as described and run "sudo lilo -M /dev/sda mbr" this will restore the MBR to windows specs, correct?

Of course i would only use this if i run into a boot problem later. I just like planning for the future.

---

### Post by JoshDN on 2010-08-28
> **dFlyer said:**
> If you have an external hd, download Macrium which is free and clone xp before you begin. That way should you have problem you can always restore xp. As far as I know only an hp xpwin cd can be installed you your hp.
I'm pretty sure i've made it clear twice now that i do not plan to use the CD to install windows, i just want to know if i can use it for the "fixmbr" utility. I've also stated I do not have a second hard drive. I appreciate all comments but PLEASE READ the post before you reply to it!:D

---

### Post by wilee-nilee on 2010-08-29
I suspect the Compac will work if it is a single install cd for XP. Here is another just to be safe that I know works.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

Edit: So the Compac isn't a install cd , really your guess is as good as ours, how would we know, call Compac.

---

### Post by JoshDN on 2010-08-29
> **wilee-nilee said:**
> I suspect the Compac will work if it is a single install cd for XP. Here is another just to be safe that I know works.
[http://www.aspireoneguide.com/xpinstallu3.html](http://www.aspireoneguide.com/xpinstallu3.html)

Edit: So the Compac isn't a install cd , really your guess is as good as ours, how would we know, call Compac.
The CD is a WinXP install CD, but it has a compaq label. I would not be  using it to install windows on the HP machine. I would be using for the  fixmbr utility. If you boot the computer with the CD in the drive you  can run this utility. What i'm really trying to figure out is if the manufacturer's WinXP CD's are generic or built specifically for the Model. Ultimately, will it write the MBR correctly?

It sound like, so far, that any WinXP CD will work for this. Thanks for the link to the ISO!!

I'm concerned about this because with every computer i've put ubuntu on,  at some point in time i've had boot problems. Usually the fix involved  this fixmbr utility followed by reinstalling grub. Before I do this  install, i just wanted to know if the WinXP install CD from my compaq  would also work with my HP.

I will be marking this as solved, and i'm going ahead with the install. It sounds like there are plenty of ways to fix things should I run into problems.


Many thanks everyone for your help!!!!
-Josh

---

### Post by presence1960 on 2010-08-29
> **JoshDN said:**
> I checked the link out and it looks like the project was recently restarted. I just thought that it was interesting because I was just reading the GRUB2 manual on the GNU website which gives LILO a bad name. They describe LILO as the boot loader that "everyone uses, but no one likes". Thats why the suggestion was interesting to me.

So let me make sure I understand all this. If i install LILO as described and run "sudo lilo -M /dev/sda mbr" this will restore the MBR to windows specs, correct?

Of course i would only use this if i run into a boot problem later. I just like planning for the future.

[http://ubuntuforums.org/showthread.php?p=9749850#post9749850](http://ubuntuforums.org/showthread.php?p=9749850#post9749850)

See that thread which the OP had ubuntu on one hard disk and windows on another hard disk. The disk which has ubuntu was taken out and put into another machine. Now windows would not boot. The lilo method was used to fix the MBR. Lilo installs a generic windows MBR so that windows can boot. It allows you to accomplish the same task as fixmbr from the windows CD. I know lilo works with XP, Vista & 7.

---

### Post by JoshDN on 2010-08-29
That is very good info to know. Thanks very much for passing that along!

---

