---
title: "Installation"
date: 2013-09-18
forum: Installation &amp; Upgrades
---

### Post by ddubbz1979 on 2013-09-18
Getting confused in the installation process when I get to partitioning.  I want to keep Windows 7 on this machine as well.  I have a 500gb hard drive but installer is only showing 12gb or so and can only partition about half of that for ubuntu.  Do I need to do it manually?  And if so is there a walkthrough?  Thanks in advance.  I'm new and anxious to get into it.  I'm downloading 12.04 by the way.

---

### Post by carl4926 on 2013-09-18
Open Gparted in the live session and post a screen of your HD partitions as they are.

---

### Post by mastablasta on 2013-09-18
you need to have unformatted disk space. use windows disk manager to create it (make sure you defragment the disk first to avoid loosing any data). also make backups. the installer should then offer you to install the OS alongside another operating system. if not use the empty disk space to create / and /swap.

---

### Post by ddubbz1979 on 2013-09-18
i used the disk manager to shrink volume and create free space.  and from a video tutorial i found i created partitions in the "Something Else" selection from my new free 75gb.  I did a / , a / boot, a swap area and a /home partition with varying amounts of space.  Installer worked great for a while but at the end told me something with boot didn't install and I would not be able to boot the new os.

---

### Post by ddubbz1979 on 2013-09-18
Would the 13.04 version be a better option for me?  Been trying to install for 3 days with no luck and with my limited time in my schedule I'm about to give up.

---

### Post by buzzingrobot on 2013-09-18
The installers are essentially the same in 12.04 and 13.04.

What's the specific message you're getting when the installer complains?

Also, now that you've created space for Ubuntu, you might think about trying the "install alongside Windows" option. The installer will then handle partitioning the free space.

---

### Post by carl4926 on 2013-09-18
> **ddubbz1979 said:**
> i used the disk manager to shrink volume and create free space.  and from a video tutorial i found i created partitions in the "Something Else" selection from my new free 75gb.  I did a / , a / boot, a swap area and a /home partition with varying amounts of space.  Installer worked great for a while but at the end told me something with boot didn't install and I would not be able to boot the new os.

You don't need /boot partition

Just use
swap
/
/home (if you like to keep data sep)
Set grub to sda

---

### Post by Bucky Ball on 2013-09-18
*Thread moved to **Installation & Upgrades***

---

### Post by ddubbz1979 on 2013-09-18
> **buzzingrobot said:**
> The installers are essentially the same in 12.04 and 13.04.

What's the specific message you're getting when the installer complains?

Also, now that you've created space for Ubuntu, you might think about trying the "install alongside Windows" option. The installer will then handle partitioning the free space.

Didn't get the option the second time.  Only erase and overwrite existing.  The message I get is about the GRUB boot and says something to the effect of new os will not boot because GRUB boot did not install.  Thanks for your help in this matter.

---

### Post by ddubbz1979 on 2013-09-18
> **carl4926 said:**
> You don't need /boot partition

Just use
swap
/
/home (if you like to keep data sep)
Set grub to sda

Any recommendation on how much space to set for each?  And haven't noticed an option for GRUB in the installer unless I'm missing it.  Thank you so much for the reply.  Should I remove the existing installation before I retry?  And how if so?

---

### Post by Bucky Ball on 2013-09-18
/ = 20Gb should be fine, if you are keeping personal data elsewhere;
/home = whatever you like - big if this is where you're keeping your personal data;
/swap = 2Gb is fine unless you do a heap of hibernating, but the debate continues.

I always install using 'Something Else' or manual partitioning which lets you put grub where you like. You should find the option in there. Don't know about the 'automagic' install as never used it. If you can get Ubuntu booting with grub on any sd*, you can reinstall grub to sda later.

You don't need to uninstall the first install. You are going to wipe it out when you install again, anyhow (you would be doing the same thing, in effect, but wiping the partition to uninstall). You can make the lot free space in the manual partitioning section of the fresh install and start again. ;)

* and +1 to carl4926: you don't need /boot.

---

### Post by Bucky Ball on 2013-09-18
/ = 20Gb should be fine, if you are keeping personal data elsewhere;
/home = whatever you like - big if this is where you're keeping your personal data;
/swap = 2Gb is fine unless you do a heap of hibernating, but the debate continues.

I always install using 'Something Else' or manual partitioning which lets you put grub where you like. You should find the option in there. Don't know about the 'automagic' install as never used it. If you can get Ubuntu booting with grub on any sd*, you can reinstall grub to sda later.

You don't need to uninstall the first install. You are going to wipe it out when you install again, anyhow (you would be doing the same thing, in effect, but wiping the partition to uninstall). You can make the lot free space in the manual partitioning section of the fresh install and start again. ;)

* and +1 to carl4926: you don't need /boot.

---

### Post by buzzingrobot on 2013-09-18
In manual mode -- 'Something Else' -- the location of where the partitioner wants to install the bootloader -- grub -- is on the initial partitioning screen, below the dialogue where you set and size the partitions.

---

### Post by ddubbz1979 on 2013-09-18
> **buzzingrobot said:**
> In manual mode -- 'Something Else' -- the location of where the partitioner wants to install the bootloader -- grub -- is on the initial partitioning screen, below the dialogue where you set and size the partitions.

Don't have it in front of me at the moment, but is there a specific setting I should look for?  Thank you.

---

### Post by ddubbz1979 on 2013-09-18
Wow!  Thanks for all the replies.  One of the quickest forums I've been on.  And very straightforward.  Thanks to all.  Hope tonight is my night for linux.  Havent looked at it since the late 90s.

---

### Post by ddubbz1979 on 2013-09-18
Thanks for the info.  I will be attempting my reinstall shortly and will take your advice.  I never understood the /home.  I see some folks just do /.  I just read somewhere that /home is a good practice for storing the data.  Will the os know to do this for me or will I have to change some settings before saving anything?  Thanks again.

---

### Post by buzzingrobot on 2013-09-18
> **ddubbz1979 said:**
> Don't have it in front of me at the moment, but is there a specific setting I should look for?  Thank you.

 I'm going by memory, but when you select "Something Else" you are shown a page where you are expected to create or change existing partitions. For example, you would see your existing Windows partitions and the free space you created to install Ubuntu.  You can create and size partitions in that free space, assign them a file system, etc.

Below that, you'll see a display of the partition Grub will be installed on, unless you alter it.  I can't recall the exact wording, but it's to do with "boot drive" or "bootloader".  It's easy to spot.

---

### Post by Bucky Ball on 2013-09-18
Yes, /home is completely understood 'automagically' by the system. In the manual partitioning section you will find /home as a default mountpoint you can select, in fact, along with a bunch of others.

Ubuntu will know, if you create a separate /home, what to do with it. If you reinstall, all your personal data is on /home, and if you mark it to use but not to format, your next install will understand there is a /home already there and use that instead of creating one of its own! Cool, huh? ;)

---

### Post by ddubbz1979 on 2013-09-18
The message I'm getting says The 'grub-efi-amd64-signed' package failed to install into /target/.  Without the GRUB boot loader, the installed system will not boot.

---

### Post by ddubbz1979 on 2013-09-18
My disk management doesn't say anything about UEFI on the other partitions.  Found that could be an issue through research here.  Can't figure it out.

Which partition do I select for the boot loader?

---

### Post by carl4926 on 2013-09-19
> **ddubbz1979 said:**
> My disk management doesn't say anything about UEFI on the other partitions.  Found that could be an issue through research here.  Can't figure it out.

Which partition do I select for the boot loader?
You have a EFI machine
Please see: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

You need a small partition in FAT32 (500MB) with the boot flag on it
[COLOR=#333333][FONT=inherit]it uses the grub-efi bootloader (not grub-pc)
And grub-efi should be targeted there[/FONT][/COLOR]

---

### Post by ddubbz1979 on 2013-09-19
Thank you so much.  This will def be something I haven't tried yet.  And I'm assuming by boot flag you mean to select /boot?

---

### Post by ddubbz1979 on 2013-09-19
I have also noticed that my internet goes down during installation.  I have to reset my router to get it back up.  Anyone run into this?

---

### Post by carl4926 on 2013-09-19
> **ddubbz1979 said:**
> I have also noticed that my internet goes down during installation.  I have to reset my router to get it back up.  Anyone run into this?
Just ignore it.
If you mean wireless - it always seems to do funny things.

---

### Post by mastablasta on 2013-09-20
don't install extra drivers and packages (fonts, flash...) during install. you can easilly add those later if needed.

---

### Post by oldfred on 2013-09-20
If you have Windows 7, but a newer computer with UEFI, you may have Windows in BIOS boot mode with MBR partitions. But if system is UEFI Ubuntu can be booted from UEFI menu in either UEFI mode or BIOS mode and how it is booted it how it installs.
A few Windows 7 systems were installed in UEFI mode, so you need to know which way your system is installed as both Windows and Ubuntu need to be UEFI or both BIOS to easily dual boot.
Windows only boots from gpt partitioned drives with UEFI.
Drives partitioned with MBR(msdos) only boot in BIOS mode.
Ubuntu will boot from gpt partitioned drives in either UEFI mode with an efi partition for boot files or a tiny 1MB unformatted partition with the bios_grub flag for grub2's core.img.

---

### Post by ddubbz1979 on 2013-09-20
I understand what you're saying.  So I DO need to manually partition?  how should I set it up?

---

### Post by oldfred on 2013-09-20
Thread closed. Please do not start threads on same topic as now I am confused on where you are at as you are also getting good advice in your other thread.

[http://ubuntuforums.org/showthread.php?t=2175579](http://ubuntuforums.org/showthread.php?t=2175579)

---

