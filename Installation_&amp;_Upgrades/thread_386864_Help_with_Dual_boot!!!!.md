---
title: "Help with Dual boot!!!!"
date: 2007-03-17
forum: Installation &amp; Upgrades
---

### Post by Tim_S on 2007-03-17
I tried to install Ubuntu 6.10 on a Windows XP Home desktop and now my hard drive is a mess, let me explain: I have a 76gb Maxtor hard drive that was formatted in the NFTS file system. I shrank the NFTS partition down to 70gb and created a 5.5gb ext3 partition and a 500mb swap partition. I then installed Ubuntu 6.10 and the GRUB bootloader. When promted to restart the computer I did. The GRUB bootloader popped up so i highlighted Ubuntu and pushed the enter key. the screen went black for about 5 minutes so I shut off my computer and restarted. The BIOS said: "NO OS FOUND." I restarted again and the GRUB bootloader popped up, I selected Windows and it just restarted the bootloader. I booted into the GParted LiveCD and deleted the swap and ext3 partitions. GParted said that my NFTS partition had an error. I tried resizing back to 76gb but it didn't work. So I restarted yet again and this time a text (terminal) like version of GRUB popped up. It wouldn't let me do anything.
Now I am afraid I'll have to wipe out the hard drive and reinstall Windows. My parents' taxes are on the computer and they are very upset. Any help to get my hard drive back to normal is GREATLY appriciated.
Thanks in advance,
Tim

---

### Post by hanzz on 2007-03-22
tim,

first to be said: working around with your partitions - especially on a machine with existing windows installation - is always risky. In fact it is always a good idea to backup your data before doing things like that ;-)

but I don't think everything is lost:

- try to boot up your machine with a live cd or system rescue cd (e.g. [http://www.sysresccd.org/)](http://www.sysresccd.org/)). at least you should be able to mount your NTFS partition and save your data before re-installing windows/ubuntu.

- another try would be to boot the machine with your windows xp install CD and try a "repair installation" -> this should re-write the master boot record (MBR) of your hard drive and could help to fix your boot problems

hth,
hanzz

---

