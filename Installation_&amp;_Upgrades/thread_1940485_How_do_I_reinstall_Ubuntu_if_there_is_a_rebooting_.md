---
title: "How do I reinstall Ubuntu if there is a rebooting problem?"
date: 2012-03-13
forum: Installation &amp; Upgrades
---

### Post by 1928Dodge on 2012-03-13
Bonjour,
    Last night I installed Ubuntu 11.10 on an HP that was running windows Vista. I made it the only operating system, so no more windows. Things were working great. I had rebooted it probably 3 times. My only problem was I was trying to get a DVD to play but it said I needed a decryption codec. So I closed the lid (which put it in Sudspension) and unplugged it to move it. Well, apparently the battery was completely dead, so now when I go to boot it up it takes me to "GNU GRUB Version 1.99 - 12ubuntu5" I've read this problem has occurred before and users have posted how to fix it. I am not a programmer in any way, so I'm not following how to resolve what seems to be a minor problem. 
    Is there a easy way for me to just re-install ubuntu-11.10 desktop-i386.iso ? I don't know what or how to type the command lines to do so. I made my computer go to the CD/DVD drive first for booting, but it just takes me to the Grub screen which eventually leads to the Busybox/(initramfs) . I don't care about losing any data, just want to get a working version of Ubuntu again. If someone could let me know what and how to type in the command line to re-install that would be great.

---

### Post by adstri on 2012-03-13
If you can boot and get to a terminal it might be worth trying the code below to see if this lets you do an update and fixes your problem 

sudo update-grub

Adam :)

---

### Post by oldfred on 2012-03-13
Ab-normal shutdown in any system often causes a file corruption issue. Window will run chkdsk. For Ubuntu you may need to run e2fsck on your Linux partition(s).

#From liveCD so everything is unmounted,swap off if necessary, change example with sdb1 to your partition(s) sda1, sda5 or whatever. If not know run this first to see which partitions are ext:
sudo fdisk -lu
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors:
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by 1928Dodge on 2012-03-13
Adam, I tried typing "sudo update-grub" and the reply line said: "/bin/sh: sudo: not found" I take it I'm entering the line wrong or not correct format?

oldfred, no luck either when I type in any of the commands. I have the boot cd in the computer, but I never get the option to access it. Is there something I'm supposed to type in BusyBox v.1.18.4 to get the Live CD to load?

---

### Post by 1928Dodge on 2012-03-13
Still stuck, everything I type I get "not found" Isn't there a way to just pop in the .iso disk an do a fresh install? I'd rather do that then try to repair the booting problem... I found a boot-repair-disk.iso but I can't get that to load and run either (I have no clue on what to type in order to get the computer to read the disc drive...). :-(

---

### Post by critin on 2012-03-13
> So I closed the lid (which put it in Sudspension) and unplugged it to move it.Always use the shut down button...  sorry--I had to say it.

Do you see a key on the Bio page that says BOOT?  If you can find which key, press it immediately while bio page still shows, with the live CD in.  I know you've set it in Bios to boot CD first, but see if there's a key to push.  Escape, F2, F12, F10 ??    If you can get it to boot, just reinstall the OS. 

**Remember, the CD has to actually boot the system, not just load and run.**  

Shutting power off probably lost the boot grub.  I could never get around the blinking cursor so reinstalling a new install is easier and quicker for new users.

> 
I found a boot-repair-disk.iso but I can't get that to load and run  either (I have no clue on what to type in order to get the computer to  read the disc drive...)

This too, must boot the system, not just load and run.

---

### Post by 1928Dodge on 2012-03-13
Hey Critin, yeah, lesson learned on shut down. I tried all the F keys, can't seem to find a shortcut key that forces a CD drive boot. I did a search for Pheonix Bios boot shortcuts and came up empty handed, although "boot from CD is listed first." So is there a command line I can type whilst in Grub to get it to reinstall? It seems every time I type a  sudo ___ line it gives me "not found" after I hit enter.

---

### Post by critin on 2012-03-14
> **1928Dodge said:**
> Hey Critin, yeah, lesson learned on shut down. I tried all the F keys, can't seem to find a shortcut key that forces a CD drive boot. I did a search for Pheonix Bios boot shortcuts and came up empty handed, although "boot from CD is listed first." So is there a command line I can type whilst in Grub to get it to reinstall? It seems every time I type a  sudo ___ line it gives me "not found" after I hit enter.
[COLOR=Red][B]

> Last night I installed Ubuntu 11.10 [/B][/COLOR]

You do it the same way as you did this.  If the CD booted the machine last night without a boot key, it should do it now.  It's not a 'shortcut key', it's a boot key, but apparently you didn't have to use it the first time.

Have you checked that CD is still first to be booted in Bio?  I use the boot key everytime I boot from usb so don't have to go into the Bio.  Would it reset itself to default to hard disk to let the HD be first?   I have no idea what you can do.

I've had the same problem as you and just keep trying, eventually it will catch and work.  But I have a cranky machine that I know well.  Sorry.

---

### Post by 1928Dodge on 2012-03-16
Thanks for your help gang! Just kept rebooting it over and over and used the boot repair.iso disc. Need to duct tape the power cord to the wall to make sure to never accidentally shut it down again! ;)

---

