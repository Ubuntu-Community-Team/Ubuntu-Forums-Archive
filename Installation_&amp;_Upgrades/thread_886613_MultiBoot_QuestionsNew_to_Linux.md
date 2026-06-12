---
title: "MultiBoot Questions:New to Linux"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by lemtargatwing on 2008-08-11
I am very new to Linux.  The only real multiboot including Linux I have ever had was on my Playstation 3.  I'm sure there is a topic on this or a guide buried somewhere, but my ADD makes it hard for me to search for things.  I came here hoping someone could help me.  I am running an HP laptop with Vista Home Premium x86 preinstalled.  I plan on installing xubuntu on this laptop next to Vista, but I don't want to screw anything up and have to spend a day troubleshooting and fixing things.  What are the steps I need to take to install these side by side?  Will the install disk partition the harddrive for me, or do I need to do it myself?  Should I install the Commander bootloader for extra security?  Thank you in advance for all of your help.  Oh, and please keep in mind, I am fairly new at this.  The only thing I'm really advanced into is programming and a bit of Security testing (call it hacking if you want, I don't go the evil route).  Thank you again.

:guitar:  <== I like that smiley :)

---

### Post by timcredible on 2008-08-11
when you install ubuntu, the default is to keep windows and dual boot, so no need to do anything.  whatever 'commander' is, no, you don't want it.

---

### Post by logos34 on 2008-08-11
> **lemtargatwing said:**
>   I am running an HP laptop with Vista Home Premium x86 preinstalled.  I plan on installing xubuntu on this laptop next to Vista, but I don't want to screw anything up and have to spend a day troubleshooting and fixing things.  What are the steps I need to take to install these side by side?  Will the install disk partition the harddrive for me, or do I need to do it myself?

I would highly advise you to shrink vista using it's own disk utility rather than let ubuntu do it during installation. As always, defrag thoroughly and run error-checking before you resize.

---

### Post by lemtargatwing on 2008-08-11
So pretty much I have nothing to worry about right?  Sorry, I just don't want to screw up this laptop, it took me two months working extra shifts at McDonalds to pay for it.  Thank you guys for all your help.

Oh, and the commander I was talking about was System Commander 7.05.  It's a really nice piece of software, completely compatible with whatever.

---

### Post by logos34 on 2008-08-11
Grub shouldn't have a problem chainloading vista, but nothing's perfect.  I thought I should at least make you aware of that.

> **Master boot record and boot manager**

 Windows Vista may stop your GRUB - Boot manager from reaching (booting ) your Ubuntu installation, when for any reason you try to repair Boot on MBR (Master Boot Record) on your Bootable HDD (Hard Disk Drive). To avoid such a mess many of you may opt to gracefully let Vista have the MBR, and its boot manager should then point to boot partition of your Ubuntu. Windows Vista no longer utilizes boot.ini, ntdetect.com, and ntldr when booting. Instead, Vista stores all data for its new boot manager in a boot folder. Windows Vista ships with an command line utility called bcdedit.exe, which requires administrator credentials to use. You may want to read [http://go.microsoft.com/fwlink/?LinkId=112156](http://go.microsoft.com/fwlink/?LinkId=112156) about it. 
Using a command line utility always has its learning curve, so a more productive and better job can be done with a free utility called [EasyBCD]("http://neosmart.net/dl.php?id=1"), developed and mastered in during the times of Vista Beta already. 

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Repairing+the+Windows+Vista+Bootloader](http://neosmart.net/wiki/display/EBCD/Repairing+the+Windows+Vista+Bootloader)

So basically, if you don't have the vista install dvd (most laptop vendors don't suppy them), then you want to make a recovery disk which you can use to restore vista bootloader if vista won't load via grub.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

That will then allow you to get back to windows and use EasyBCD method to add linux to vista bootloader.

---

### Post by lemtargatwing on 2008-08-11
Thank you very much, your responses were speedy and very helpful.  Much appreciated.

---

### Post by logos34 on 2008-08-11
ok, good luck to you.

---

### Post by Bucky Ball on 2008-08-11
I did just that, made the recovery dvd disk from a 10GB partition HP put there, deleted everything, piece of paper and drew up how I was going to partition my one 80GB laptop drive, partitioned for a Windoze install when loading Vista, loaded Gutsy 7.10 and used the partitioner in that for its partitions (a fat32 partition is also handy for sharing with Vista).

Wouldn't boot and grub errors. 

I ran SuperGrubDisk on the advice of someone on these forums as I had no idea how to fix it manually then, and 9 months later am using Hardy 99.9% of the time and loving it.

Bottom line and maybe easiest? As outlined above, but download supergrubdisk with your windoze install before you start, when it's all over, if you can't boot, plug that in and boot from it;

[html]http://www.supergrubdisk.org/[/html]Welcome and as logos34 said, good luck.

---

### Post by ramnarayan on 2008-08-11
> **logos34 said:**
> I would highly advise you to shrink vista using it's own disk utility rather than let ubuntu do it during installation. As always, defrag thoroughly and run error-checking before you resize.

I agree

and once thats done - download the latest Ubuntu and also run a search for your machine and installation of ubuntu on that machine, possibly someoe has already done that and has some guide ready.

Once you boot into alive session and begin the install - Ubuntu should take care of dual booting. Though please read the post of Vista causing problems

***
During the install on Ubuntu you will be asked to partition your disk - chose manual 

The partition manager will show you the existing partitions - even a cute wincedows ;-) icon against the windows partition.

Just avoid doing anything to this and focus on the free space you created in vista.

Remember you cannot have more than 4 primary partitions - so if your laptop comes with a recovery section (or vista) it means Vista has two partitions to itself.

This is my suggestion for the minimum partitions you will require to install ubuntu nicely and keep your data secure in the long run

swap-twice your RAM (memory) - this is a kind of virtual RAM
/boot - 100 mb - where your boot loader will be
/ (/root) - where you linux os will be 
/home - where all your work will be

depending on the space you have try and allocate a huge amount to /home 

and /(/root) anything for 4 GB to 10 GB should do - it depends on what software you want to install - and if  you will install a lot keep it on the bigger side.

Optional partition could be to have a VFAT section which you can share with  Vista and Linux - though if you have a later version of Ubuntu 8.04.1 then there is very good NTFS read write support and you don't really need a Shared section (though even on windows its good to keep data separate from the OS).

To repeat about partitioning - if you create a primary partition you can create many logical partitions under that.

Finally do a bit of net research before installing and keep your notes handy.

have fun
ram

---

