---
title: "Error no data found, after update"
date: 2010-03-20
forum: Installation &amp; Upgrades
---

### Post by ldouble_e on 2010-03-20
This is a common occurrence for me, but I'd like to fix it for good. I have two HDD's in my pc. I have a 640GB with windows 7 loaded on it and I have a 160GB with Ubuntu loaded on it. After a Ubuntu update I restart and get to the grub loader where it asks what I want to load. If I select 2.6.31-20-generic, I get: error no data found. So I press 'c' to enter command line. I type the following:
>set root=(hd1,1)
>linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro
>initrd /boot/initrd.img-2.6.31-20-generic
I get: error file not found
>boot
The system will now boot into 31-20-generic just fine. I login in and go to the terminal. I type 'sudo update-grub' which fixes the issue usually. This time it did not. So I've been doing some troubleshooting, but I'm a bit stuck on where my problem is occuring. I am thinking it has to do with my initrd.img package, but I'm not sure. In the terminal I entered the command:
'sudo grub-probe -t <> /boot/grub' and it returns the following
<device> /dev/sdb1
<fs_uuid> 8c5cc725-cf5b-44ad-80ab-58cbe6a450f5
<fs> ext2
<drive> (hd1,1)
I also ran the boot_info_script*.sh from within the loaded 31-20-generic but not from a live cd. I'll attach it to this post. I've also used the super grub loader cd. It used to fix the problem, but now it won't load the kernel at all. Any help would be appreciated and Thank you for your time. [ATTACH]150824[/ATTACH]

Edit: Let me simplify this encase I've confused everyone. I did an upgrade tonight. Restart the computer and I get to where it says GNU GRUB Version 1.97~beta4 and lists all my options to load. If I select Ubuntu, Linux 2.6.31-20-generic I get a black screen that says "error: Couldn't read file" , "Press any key to continue". Pressing a key returns me to the list of options to load. If I select Ubuntu, Linux 2.6.31-19-generic everything loads up fine. I was using 2.6.31-20 for at least a month before todays updates. What file is it not able to read and how do I fix the file?

---

### Post by ldouble_e on 2010-03-21
I figured it out on my own. If you want to know what I did, I posted the fix in another thread. [http://ubuntuforums.org/showthread.php?p=9005921#post9005921](http://ubuntuforums.org/showthread.php?p=9005921#post9005921)

---

