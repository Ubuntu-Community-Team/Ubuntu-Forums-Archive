---
title: "Restoring Windows MBR and booting from USB external drive"
date: 2008-04-11
forum: Installation &amp; Upgrades
---

### Post by ozyank on 2008-04-11
When I installed Ubuntu to my external USB drive I intended to be able to boot from the external drive through the BIOS option. Unfortunately I missed something and grub overwrote the MBR.

Now, when the external drive is removed, Grub croaks with error 21, naturally. What I would like to do is restore the Windows MBR, that is the easy part, then fix the external drive in such a way so that it will be bootable. That's the part I don't understand. I hope someone can help.

---

### Post by alexsabree on 2008-04-11
Yeah, tired to install ubuntu onto my friends external harddrive and I had the same prob.

I would also like to know how to go about this?

---

### Post by wolfen69 on 2008-04-11
1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Open a root terminal (that is, type "su" in a non-Ubuntu distro, or "sudo -i" in Ubuntu). Enter root passwords as necessary.

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines. Note that you should have mounted the partition which has your Linux system before typing this command. (e.g. In Knoppix Live CD partitions are shown on the desktop but they're not mounted until you double-click on them or mount them manually)

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

---

### Post by Pumalite on 2008-04-11
To restore your Windows MBR, use Super Grub:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Next time you install to USB, in step 8, press 'AdvancedTab' and replace (hd0) for /devxxx, where xxx is your USB. This you can find out running:
sudo fdisk -lu (at the Terminal)
While having your USB connected.
[http://ubuntuforums.org/showthread.php?t=492136](http://ubuntuforums.org/showthread.php?t=492136)

---

### Post by ozyank on 2008-04-11
I've had a bit of a re-think about what I want to do. I want to leave Grub as the boot loader but have it find its configuration on the internal hard drive. I resized the "D" drive so it now has a bit of ext2 available. I need to know how to get the boot loader to look there for the configuration files and how to I install the configuration files there? This is /dev/sda6

---

### Post by Herman on 2008-04-11
[How to make a dedicated GRUB partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_Grub_Partition_")
That's a good idea, GRUB is a great boot loader/manager.
If you installed Ubuntu in an external hard drive, then you won't find any GRUB configuration files in your internal hard drive at all. 
Your main GRUB files are all in /boot/grub in Ubuntu, in the external hard drive.
All that's in your internal hard drive is a little code in the MBR, to make it piont to your external hard drive's GRUB files.

If you make a dedicated GRUB partition then you will have some GRUB configuration files in your internal hard disk and then you can play with those to boot anything you want. You can chainload your external hard drive's MBR or use the configfile command the boot the other GRUB's GRUB menu.
[Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems")

:) Regards, Herman

---

### Post by ozyank on 2008-04-12
Herman,

You are leading me down the path I want to go! I haven't done tried anything in the first link yet but will do that tomorrow.

Many thanks.

Dennis

---

### Post by ozyank on 2008-04-12
Herman,

It was pretty simple and you gave me the correct answer. I left Grub as the boot loader but copied the files from the external drive /boot/grub to an ext2 partition on the laptop. The links you sent gave me the proper syntax for setting the loader to look on the internal drive.

I can now unplug the External drive and still load Windows on the laptop.

Many thanks and another cup of Ubuntu for you! Where in Oz are you?

---

### Post by Herman on 2008-04-12
:) Good on ya Dennis! :)
I'm up here in the middle of the 'sunshine state', (the also called the 'smart state'). :)

I'm glad you got it working, GRUB rules!

Regards, Herman :)

---

