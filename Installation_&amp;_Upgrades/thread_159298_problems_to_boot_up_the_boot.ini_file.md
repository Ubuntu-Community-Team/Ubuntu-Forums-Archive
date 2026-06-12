---
title: "problems to boot up the boot.ini file"
date: 2006-04-12
forum: Installation &amp; Upgrades
---

### Post by corlex on 2006-04-12
Hello.

I have used ubuntu for a long time now, but i am at The Gathering (gathering.org :P) so i had to install windows for using some P2P programs. From the beginning i have a WD 160GB with Linux on, I also have a WD 250GB with an NTFS file system (from my past :P), so i have mounted the 250GB WD to linux so i could read the files from there.
I also got a WD 20GB today, so i could install windows on this HDD, i did. but i could not have the Linux disk in the IDE slots while i booted windows because then it came an error. So i started my computer with the 20GB disk and the 250GB disk.

Later i wanted to go into linux again, so i tried to boot up with the 160Gb disk alone(the Linux disk) since it didn't work to boot up linux with any of the two other disks. I've got an error when i booted it up, it stood: 
"could not load boot.ini"
"loading boot.ini c:\windows\..............."

Something like that, so i have problems to boot ut my linux.
anyone that can help me?

---

### Post by corlex on 2006-04-12
okay, I've found out that it stood "unknown boot.ini-file"
"starting up from c:\windows\"
"LOADING failed"

I think i've need a new boot.ini file in ubuntu so i can load ubuntu again, but i don't know what i should do? how do i make a new boot.ini file?

---

### Post by Herman on 2006-04-12
I 'm not sure I understand perfectly what it is you want to do, but...
It sounds like you would be able to do everything a lot easier if you try out the [GAG Boot Manager]("http://www.users.bigpond.net.au/hermanzone/p12.htm"). Run it from a CD, a floppy disk, or install it to hard disk. 
GAG is very simple to use so you should be able to do a lot of complicated things with it easier than doing complicated things with a complicated bootloader.
Just try it, you'll be able to do everything easy after that. :D

boot.ini is a file for the Windows bootloader, and has nothing to do at all with loading Ubuntu, unless you have edited that file in Windows to boot GRUB or Lilo though a relay system and boot Ubuntu that way. Some people do it that way, but it is very complicated. In that case it might not work, like you say, after removing a disk which might contian one or more of the steps in the relay chain that would be needed for boot.ini to reach GRUB or Lilo.
 boot.ini cannot load any Linux kernel, only Lilo or GRUB bootloaders can load a Linux kernel as far as I know. 
You can't install boot.ini in Ubuntu, you can only use that in Windows. 
You *can* install Lilo or GRUB in Ubuntu though, and boot directly with Lilo, or GRUB, or use GAG to relay to Lilo or GRUB. If you use boot.ini to relay to Lilo or GRUB, it's just far too complicated. Especially if you want to be able to remove or switch hard disks and operating systems around.
GAG Boot Manager is what you need for that job, that's what GAG Boot Manager is made for!

I hope this solves your problems, good luck, (Herman):D

---

