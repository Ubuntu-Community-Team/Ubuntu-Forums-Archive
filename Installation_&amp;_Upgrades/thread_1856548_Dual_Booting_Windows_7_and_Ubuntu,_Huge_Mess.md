---
title: "Dual Booting Windows 7 and Ubuntu, Huge Mess"
date: 2011-10-08
forum: Installation &amp; Upgrades
---

### Post by Vorsaykal on 2011-10-08
I've been using Ubuntu 11.04 for about 3 days now (since I wiped Windows 7 by mistake and had no disk:mrgreen:) and I fell in love and decided it will now be my main operating system, but I still need Windows 7 for some things. So I installed Windows 7, but now I can't boot Ubuntu (On a Ubuntu LiveCD) and I have no clue how to get it working well. I read that I need to use Ubuntu's boot loader, but I have no clue how.

I tried to follow instructions from another thread that said it was outdated, it told me to type a few commands, first one being "sudo grub" which gave me an error "sudo: grub: not found" so I really have no clue what to do now.

I'll do my best to explain how my hard drive is set right now, but I'm not too familiar with Linux's swap and extended stuff. :???: 

So here's what Disk Utility is telling me:

I have a 99GB ext4, (Ubuntu's Partition?) System Reserved NTFS, 147GB NTFS (Windows 7, I believe,) Extended 2.9GB and 2.9 GB Swap.

Could anyone explain any fix or explain any other information I can provide to provide better results?

---

### Post by oldfred on 2011-10-08
Once you install Windows, it puts its boot loader into the MBR and only boots Windows. You need to reinstall grub2 (not grub legacy) to the MBR and update its menu to find Windows and add it to the menu.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version -
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If you need help with specific instructions, post this from the liveCD.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

Some have had issues booting CD and found a cold boot (full power off for a bit) and reboot to CD in BIOS or one time boot key (f12 on my system but it varies).

---

