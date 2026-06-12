---
title: "Problem with Hardy alternative CD/dual boot"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by Yumi on 2008-05-07
Am trying to install a XP/Hardy dual boot system. I created a CD from ubuntu-8.04-alternate-i386.iso and follow the detailled instructions given at [http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm")

The installation process and the partition of the single HD works up to "Select and Install Software". This step and any further on fails. So it also refuses to install GRUB boot loader.

I tried with and without "Network Mirror". I also tried different Mirror locations.

Checked the CD for integrity with a positive response.

Noticed some difference in the partition table to the guide

**Guide:**
SCSI1 (0,0,0) (sda) - 40.1 GB ATA SAMSUNG SP0411N
       #1 primary   15.1 GB   K  ntfs       /media/sda1
       #2 primary   19.0 GB   f  ext3       /
       #5 logical    5.0 GB   f  fat32      /windows
       #6 logical  954.1 MB   f  swap       swap 

**Mine:**
SCSI3 (0,0,0) (sda) - 80 GB ATA SAMSUNG SP0411N
       #1 primary   30.3 GB      ntfs       
       #2 primary   37.7 GB   F  ext3       /
       #6 logical    2.0 MB   F  swap       swap 
       #5 logical   10.0 GB   K  fat32      /windows

Any advice appreciated

Michael

---

### Post by Herman on 2008-05-07
:) Hello Yumi,
I am the author of that web page, and thanks for using it too, by the way.

The partitions I used are only for an example and you don't need to use the same partition sizes I used, everyone should make up their own mind about how big to make each partition. For your swap area though, I recommend around 1. GB, if you have the hard disc space, unless you have a lot of RAM.

About your installation failing while installing the software, I don't know what could be causing that for you, but I have had that happen to me a few times over the years and every time it was because either my CD was dirty or the CD/DVD lens was dirty. In both cases the dirt may be invisible to the naked eye. I am not saying for sure that that is your problem is, only that's what caused the problems when it happened to me. 
I used a tissue dipped in some 'metho' (ethyl alcohol) to wipe my CD with, or a cotton bud, (QTip), dipped in 'metho' to clean the CD/DVD lense. 
The fact that your CD passed it's self-check is a sign that the CD and CD/DVD drive are okay though, so I am not sure. I don't know what else to suggest.

Regards, Herman

---

### Post by Herman on 2008-05-07
Oh, and about the GRUB boot loader, that was a problem before Hardy Heron was officially released, but that problem is gone now, you should be able to leave your network plugged in and GRUB should be installed without any problems.

---

### Post by Yumi on 2008-05-07
Thank you for the reply and your useful website I quoted above. As you are the publisher, the guide is very clear, step by step and easy to follow. Just one suggestion: It might be nice to have a print out version as the website is not accessible during installation.

Michael

---

### Post by Yumi on 2008-05-07
After posting my first problem I encountered a more serious problem. I can not boot from HD or CD anymore. Eventually found out that only the windows CD and a older Ubuntu CD will. All my Hardy alternate and another windowsXP CD do not??? So it is not a hardware problem.

I am now on a live CD and using geparted I found no boot flag on any partition. I set it on the windows partition 1 and will see what happens after reboot.

One question for Hermann. In your guide it shows that partition 2 for hardy has the boot flag set to off. Is this correct or do both partitions have the boot flag set?

You might be right with the dirty CD. I found another thread with the same problem at the same place. He reported that it went when he burned again at a slower speed. I tried this but have not booted yet.

Michael

---

### Post by Herman on 2008-05-07
> Thank you for the reply and your useful website I quoted above. As you are the publisher, the guide is very clear, step by step and easy to follow. Just one suggestion: It might be nice to have a print out version as the website is not accessible during installation.
:) Thanks Micheal. :) 
I did try making .pdf files of the installations for people to download and that was okay when the rest of the website was still small, but it doubled the amount of disc space I was using in the server, so after a while I had to give up on that idea so I could fit the other pages in. 
You are welcome to download the web page if a Windows computer can do that, or copy it or something, and then print out the copy of the .html page, or whatever works for you. You would probably want to remove the background color from the page so it won't waste too much of your printer ink. Apart from that, if you interview a few of your freinds and find out who has a laptop, you might be able to persuade one of them to come and visit you with their laptop for an hour or so. Thanks for the comment though, it is a valid comment and I'd like to be able to do that, a video you can downlaod might be even better. Have you been to [Ubuntu Screencasts]("http://screencasts.ubuntu.com/")?  They have some nice installation videos there. You would definitely need another computer to watch a video while you install though. :)

> After posting my first problem I encountered a more serious problem. I can not boot from HD or CD anymore. Eventually found out that only the windows CD and a older Ubuntu CD will. All my Hardy alternate and another windowsXP CD do not??? So it is not a hardware problem.:confused: Hmmm, I don't know...
 > I am now on a live CD and using geparted I found no boot flag on any partition. I set it on the windows partition 1 and will see what happens after reboot.
One question for Hermann. In your guide it shows that partition 2 for hardy has the boot flag set to off. Is this correct or do both partitions have the boot flag set?
 Yes, it is best to have one boot flag in your partition table. Some computers need it, mainly to boot Windows. Some computers can boot with no boot flag apparently, if we use GRUB. More than one boot flag is not usually necessary (unless you're doing some kind of an expert trick), and might cause problems. GRUB can make the boot flag with it's 'makeactive' command. Grub can also move the boot flag around for you automatically as needed, usually we don't need to worry too much about the boot flag during an installation. Normally, there's one there already.
> You might be right with the dirty CD. I found another thread with the same problem at the same place. He reported that it went when he burned again at a slower speed. I tried this but have not booted yet.Yes, or even bad quality CDs too, let's face it, most of us buy the cheapest CDs we can get, and that increases our chances of getting a package of CDs from a bad batch. 
Keep on trying and you will succeed.

---

