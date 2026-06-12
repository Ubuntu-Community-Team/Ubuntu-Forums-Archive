---
title: "Duel boot - No GRUB"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by CC Inc on 2012-01-21
Hi,
My system has 3 drives. My C: drive is Windows boot, my D: drive is Windows System, and E: is where I installed Ubuntu.
However, After going through the initial Ubuntu setup and rebooting, I would get Error: Cannot Find Device then displays a list of characters and goes into Grub Rescue. I have tried using Boot-rescue but it doesnt work.
How can I get GRUB to load and show my ubuntu and windows installs on seprate drives?

---

### Post by oldfred on 2012-01-21
Welcome to the forums.

From boot repair post the link it creates for boot info script.

Yanni has created a easy way to download boot repair & run script:
HOWTO : easily create a Boot-Info summary
[http://ubuntuforums.org/showthread.php?p=11164270](http://ubuntuforums.org/showthread.php?p=11164270)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration. May be better to run the git/beta version of boot script as it has some fixes.

---

### Post by darkod on 2012-01-21
I installed in E: sounds like wubi. Are we talking about a wubi install inside windows or a dual boot?

The procedures to repair and investigate depend on this. I am not even sure running boot-repair is used for wubi.

---

### Post by CC Inc on 2012-01-21
No, it is a DuelBoot. Boot repair is extremely slow starting up for some reason though.

---

### Post by CC Inc on 2012-01-21
Ok, here it is

[http://paste.ubuntu.com/812427/](http://paste.ubuntu.com/812427/)

---

### Post by darkod on 2012-01-21
There doesn't seem to be XP OS detected on any of the disks. On which disk was it? The 82GB or 40GB disk? Or the 250GB disk?

If you set the 250GB disk as first option to boot from in BIOS, does it load ubuntu or not?

---

### Post by CC Inc on 2012-01-21
I cannot boot from the 250GB disk, and XP is on the 82GB disk.

---

### Post by darkod on 2012-01-21
From live mode if you try to open the /dev/sda1 partition, can it read the files? Can you see it correctly?

---

### Post by CC Inc on 2012-01-21
I think I just fixed that by installing the NTFS  tools, and can mount and see the 82GB (I think thats the /dev/sda1), but not the other two drives.

---

### Post by darkod on 2012-01-21
OK, try this from live mode:
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

It will give you some warning, ignore it, it's normal. That will write a general mbr on /dev/sda and if you set in BIOS to boot from the 82GB disk it should boot XP directly. Lets see if that works, we'll worry about the dual boot later.

---

### Post by CC Inc on 2012-01-22
Yes, that works but in ubuntu i cannot connect to Internet and cannot mount any ntfs drives.

---

### Post by darkod on 2012-01-22
You don't need to mount any ntfs partitions. Not to run those commands and write a generic mbr to /dev/sda.

Ubuntu should work fine with most wired connections. If wireless doesn't work by default, can you connect by cable and run those commands?

---

### Post by CC Inc on 2012-01-22
What's wired is that it can connect, but there is no Internet.

---

### Post by CC Inc on 2012-01-22
That is with wired by the way, and it was working earlier.

---

### Post by darkod on 2012-01-22
Again, is this wi-fi or wired connection?

Usually if it connects to wi-fi the internet should work. If you say it's not, it might be something with the wi-fi router setup, but I guess other computers would not have internet also.

Anyway, if you haven't tried so far, try with a wired connection.

We need to see if XP will boot on its own, regardless of ubuntu or grub. I don't think it will. In that case, it's normal that grub can't find it to boot it.

So, at this moment, lets forget about ubuntu, dual boot, grub, internet, etc. If possible just plug a cable to your router, get the generic mbr installed on /dev/sda as mentioned above, set that disk as first option to boot from and see if XP boots. Or what error it will give if not booting.

---

### Post by darkod on 2012-01-22
> **CC Inc said:**
> That is with wired by the way, and it was working earlier.

OK, cross posting.

So you are trying from live mode and it doesn't work now, right?

And the computer can't boot both windows and ubuntu from the hdd, right?

---

### Post by CC Inc on 2012-01-22
Sorry, yes i am using wired, and using your method it will say ntdlr is missing, or it will boot straight into XP without the xp bootloader.

---

### Post by darkod on 2012-01-22
I just noticed in your results file that it says XP was on /dev/sdb1, not /dev/sda1 (or at least its boot files were there).

That is the 40GB disk.

But XP is not detected anywhere, on any disk. And that is very strange. There are no XP boot files detected, and no XP OS detected.

---

### Post by darkod on 2012-01-22
> **CC Inc said:**
> Sorry, yes i am using wired, and using your method it will say ntdlr is missing, or it will boot straight into XP without the xp bootloader.

OK, so, it can boot XP?

Make another results file and post the link of the new one. Lets see it again.

---

### Post by CC Inc on 2012-01-22
> **darkod said:**
> I just noticed in your results file that it says XP was on /dev/sdb1, not /dev/sda1 (or at least its boot files were there).

That is the 40GB disk.

But XP is not detected anywhere, on any disk. And that is very strange. There are no XP boot files detected, and no XP OS detected.
What is very strange is that when I installed XP, it put my boot files on SDA, and system files on SDB.

---

### Post by CC Inc on 2012-01-22
Ok, here you go:

[http://paste.ubuntu.com/813286/](http://paste.ubuntu.com/813286/)

---

### Post by darkod on 2012-01-22
OK, this looks much better.
Now, boot with the ubuntu cd in live mode, and execute:
sudo mount /dev/sdc5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdc

That will reinstall grub2 to the MBR of /dev/sdc. Restart, enter in BIOS and set the 250GB disk as first option to boot from.
You should get a grub menu with ubuntu and XP in it.

I also notice some left overs of wubi inside /dev/sdb1 but that should not be an issue right now, you can remove them later. Lets see if we get the dual boot with grub2 working.

---

### Post by CC Inc on 2012-01-22
Ok, i can get into grub, but when I select ubuntu, the screen goes black, then the monitor turns off. Would that just be my ubuntu installation?

Edit: nevermind, after a minute my minuter turns back on and ubuntu starts. 

What should I do now?

---

### Post by darkod on 2012-01-22
It might be a video driver issue. What video card do you have?

---

### Post by CC Inc on 2012-01-22
Intel® 865G x86/MMX/SSE2

So how can we get rid of the old WUBI install?

---

### Post by darkod on 2012-01-22
It doesn't look as a install, only traces of the wubildr.mbr and wubildr files, that make a virtual mbr of the wubi install.
First boot XP from the grub2 menu. If it shows a second menu with XP and Ubuntu, ignore that and boot XP from there. That is the leftover of wubi.
Once inside XP, open Add/Remove Programs and see if you have Ubuntu existing there. If yes, uninstall it like any other software. If not, just close Add/Remove Programs.

In XP, set the Folder Options to show hidden files, and open the /dev/sdb1 partition. The boot.ini file should be there. Open it with notepad and delete the line
C:\wubildr.mbr="Ubuntu" (ONLY THIS LINE!!!)
Save and close the file.

Reboot and try booting XP again. This time you shouldn't see a second menu, it load immediately after you select it in the grub2 menu.

Then again open /dev/sdb1 either from XP or ubuntu (better) and if they are still there, delete the wubildr and wubildr.mbr files.

That's it. The wubi traces are gone.

---

### Post by CC Inc on 2012-01-22
Ok, thanks for all of your help!

---

### Post by tstrick90 on 2012-02-03
Dear Darkod;
Thank you very much for the help!  I had the dreaded "No such device.....grub rescue" After installing Ubuntu on a 2nd HD in a Dell w/WinXP.  Been trying to fix it for days!  It gives me the choice now to boot from Win XP or Ubuntu.  I used your fix from above: sudo apt-get install lilo
sudo lilo -M /dev/sda mbr  You are the greatest, may god bless you and your home.  Tina

---

