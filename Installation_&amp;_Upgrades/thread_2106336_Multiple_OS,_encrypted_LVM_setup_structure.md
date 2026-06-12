---
title: "Multiple OS, encrypted LVM setup structure?"
date: 2013-01-18
forum: Installation &amp; Upgrades
---

### Post by markuswells on 2013-01-18
SO I have done a LOT of research and am still not entirely sure how this is going to work 'in real life'. So I would like to get some input before I start building this out.

I would like to setup a FDE (Full Disk Encryption) Ubuntu system, but really that means I would like to have (I think):
1) a raw (not encrypted) /boot (512mb)
2) an encrypted /swap  (2-3 x ram)
3) a raw /home (ubuntu will encrypt /home/users)
4) an encrypted /

I do not even understand how this part will 'act', but its really only part of the story.

q1) Will I have to enter a password for EVERY one of the above thats encrypted?
One for swap, another one for / and then the user signs in and that decrypts the /home/user
q2) can I put all of that into a LVM group?

PART 2 of this is:
I would like to be able to take advantage of LVM and make a snapshot (or copy or mirror or...) of the OS, then (tweek something), reboot and be able to choose which of the NOW 2 OS's to load.
Then update 1 of them (making it different from the other). Decide if I like the changes and either delete 1 or NOT

The important part of this is that I will be doing testing and want to be able to choose which to 'start' at boot.

Considerations:
I 'might' decide to have a different disto on this also, maybe MINT or Arch.
So I need to give consideration to how many LVM groups I create or whatever the structure needs to be to handle the additional OS's.

Thanks for the advice.
Markus

---

### Post by Herman on 2013-01-18
:)   Normally I'm not a fan of multiple partition installations but that sounds like an Interesting and fun project, and it's for a  completely different purpose compared a normal everyday user who's looking for an operating system for practical ease of  use.
I am quite interested in LUKS and LVM at the moment.

If I were beginning a project like that I would start by using the Ubuntu 12.10 LiveCD and boot it to the desktop. 
I would then use GParted in  to create a number of small partitions for /boot partitions. 
You'll need one /boot for each operating system if you're planning to install more than one OS. The /boot partitions will not be encrypted.  
Then I would create one more large partition for the encrypted LVs, taking up the remaining free space in the disk.  

Encrypt your partition with a LUKS and then unlock your LUKS fornatted partition.  
To create your LVM, you can use the command line or enabled universe repository and install system-config-lvm, which is a nice GUI toolkit for working with Logical Volumes.  

Then while the LUKS partition is still unlocked, start the Ubuntu installer in the 12.10 Live CD and begin your installation in the usual way. 
 Stop when you get to the  "Installation Type" frame and choose 'something else'.  Ubiquity in 12.10 can recognize your logical volumes and you can select them, format them with a file system, specify their various mount points and proceed to install Ubuntu pretty much as per normal.

---

### Post by Herman on 2013-01-18
There's an option in the 12.10 installer to set the file system type as 'physical volume for encryption' and that's what I used when I was experimenting with re-installing an operating system in a LUKS encrypted LVM recently. I think that may have been a mistake. Logic tells me the partition was already encrypted and choosing this could be double-doing things and maybe result in a slower system. I won't be sure until I run through the process again and try the operating system out. 

In the end I found that after the installation was complete, it couldn't boot.  

I had to chroot into the new installation and create an /etc/crypttab  file, edit /etc/initramfs-tools/modules and rebuild the ramdisk, roughly  in accordance with the following how-to: final preparation - Ubuntu  Community Docs. After that it has been booting and running just fine.

---

### Post by helpee on 2013-01-18
A nickle's worth of free advise?

Try this on a virtual machine first. VirtualBox is free and it's great for testing crazy and dangerous ideas before you really bung up a real machine.

Cheers

---

### Post by markuswells on 2013-01-28
Bump.

So has no one done a FDE and left room to take advantage of the LVM?

Will grub handle the various login options is that how this would work?

Markus

---

