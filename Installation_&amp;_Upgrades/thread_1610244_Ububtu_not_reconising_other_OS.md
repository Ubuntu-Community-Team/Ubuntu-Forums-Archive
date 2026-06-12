---
title: "Ububtu not reconising other OS"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by Chazz44able on 2010-10-31
I'm new to Linux, so please be simple. i just downloaded Ubuntu 10.10 onto a USB key and am attempting to instsll it next to Windows XP. The Ubuntu install wizard has giot to the point where i have already chosen my language and asked it to install upgrades as well, when i click "Foward" it only displays two options:
1) Erase and use entire disk
2) Specify partition manually
 
It is supossed to give the option to "Install along side other operating systems". This option is not being shown -si what do i do? thanks for your help in advance

---

### Post by wilee-nilee on 2010-11-01
You want to resize the XP partition leaving a open space for Ubuntu to begin with. You can resize with gparted on the live cd, but defragg and make sure the XP partition is in good shape not needing any chkdsk run beforehand. After resizing the XP partition reboot it to make sure it is still working before installing Ubuntu.

So there is a install alongside option for dual booting you will use that I believe, and the open space left after resizing XP is Ubuntu destination.
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)

Here is a picture of gparted on my dual boot set up if this helps.
[ATTACH]174218[/ATTACH]

Last of all have everything backed up and have the ability to do a full reinstall of XP if needed, you really want to be prepared for anything. Most of the time everything goes fine but always being prepared for the worse possible situation, has kept me safe.

---

### Post by Chazz44able on 2010-11-01
I can partition it manually, but I don't want to do that, as I'll almost certainly end up mucking it up! If the option to run the two OS' side-by-side is available in the Ubuntu install menu, I would far prefer to use that. So i suppose that what I'm really saying is that it want to try to work out how to get the option to "Install along side other operating systems" back

---

### Post by Quackers on 2010-11-01
As wilee-nilee infers, if there is no free space on the disc the Ubuntu installation will not offer the option you want. The only way to get free space is to resize the XP partition.

---

### Post by wilee-nilee on 2010-11-01
> **Chazz44able said:**
> I can partition it manually, but I don't want to do that, as I'll almost certainly end up mucking it up! If the option to run the two OS' side-by-side is available in the Ubuntu install menu, I would far prefer to use that. So i suppose that what I'm really saying is that it want to try to work out how to get the option to "Install along side other operating systems" back

On occasion we see people on the forum who have just let the installer resize the MS partition while installing Ubuntu. This will cause irreparable damage at times, and sometimes these are people who have not backed up and have no images of the hard drive, and no ISO or install discs for MS installs. I think this back correlation is more that most people just don't use some basic protective means for the OS.

To be honest people that have rushed into the idea of how cool or nice a dual boot is, but not really having the correct tools to have that experience.

Hope you get done the way you want but I advise against the auto resizing and installing at the same time. Others will feel different I am sure so follow your bliss.

---

### Post by Rubi1200 on 2010-11-01
I am in complete agreement with wilee-nilee on this one.

Here are the steps you need to take (if you do so, the chances of "mucking it up" will be way less than if you blindly rush ahead without a plan):

1. make backups of all important data to external media

2. use a LiveCD to boot the computer and take a screenshot from GParted of your current setup

3. post the screenshot here so we can advise you on the best partitioning setup for your system

4. follow the instructions we offer

5. install Ubuntu and happily dual-boot with Windows knowing that you have not had to reinstall anything or go through the nightmare of data recovery

In any event, I wish you the best of luck whatever course of action you decide upon.

---

### Post by Chazz44able on 2010-11-01
I've tried to use GParted, however, when i reboot the system after burning it to the Live USB, it comes up with the message:

SYSLYNUX 3.85 2010-02-20 EBIOS Copyright (C) 1994-2010 H. Peter Anvis et al No DEFAULT or UI configuration directive found!
boot:

---

### Post by Rubi1200 on 2010-11-02
I thought you already had 10.10 on the USB? At least, that is what you wrote in your first post.

GParted is installed by default on the LiveCD/USB; no need to download/install it again.

Look under System > Administration > GParted

---

### Post by Chazz44able on 2010-11-02
oh, i did,i just didn't realize that it worked that way, i did already have it!

Thanks for all of your help guys, I've installed Ubuntu using Wubi so I'm running within windows, which suits me well. This way there is no way at all of loosing things like the full Adobe master suite i have (it was came installed on the laptop when i brought it so i don't have the original disk). Once I get a new computer (hopefully soon) then I'll load ONLY Ubuntu onto it, and keep this one for my other software. Thanks again for all of your support, other forums could learn a lot from you guys.
Charles

---

### Post by Rubi1200 on 2010-11-02
You are more than welcome and I am glad you found a solution that suits your needs at this time.

Don't forget to ask questions here anytime you want; there will always be someone willing to lend a helping hand.

Enjoy :)

(Please mark this thread Solved using the Thread Tools near the top of the page)

---

### Post by Chazz44able on 2010-11-02
Will do, thanks again

---

