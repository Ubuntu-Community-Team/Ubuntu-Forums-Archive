---
title: "installation on aspire 5532"
date: 2010-03-27
forum: Installation &amp; Upgrades
---

### Post by lxtreeml on 2010-03-27
I have read that 9.10 works fine on my laptop with no issues whatsoever and I used to love older versions of ubuntu on my old laptop. I haven't used linux in forever so forgive me for my not uptodate use of words and lack of knowledge.

heres what I'm running, and what i plan on doing:
AMD Athlon 64bit TF-20(1.6GHz)
ATI Radeon HD3200
3GB RAM
160gb HDD

the laptop in disk management(windows 7) shows three partitions, one thats empty, but NTFS and 12Gb, another for about 140Gb NTFS and 100Mb
I shrunk the 140 and freed up 20Gb for Ext4 for ubuntu using Gparted live and disk management in windows 7. I used unetbootin to make the i386 image of ubuntu on my USB drive bootable but it hangs on installation at "Kernel_thread_helper+0x7/0x10" so I deleted the old image and im trying the amd64 image. I want to dual boot Ubuntu and windows 7. and on a side note I would like to install the security hacking suite from BT4 on ubuntu so if anyone has any input on that i would like to know.

my questions:
should switching images fix the hang on bootup of the ubuntu live image?

how do I setup my bootloader(i think its called GRUB) to boot ubuntu or windows 7 at my choice?

and is there anything special about that 12Gb partition? can I use it for transferring files between OS's?

and should I do anything special when installing Ubuntu?

---

### Post by lxtreeml on 2010-03-27
Using the amd64 image I was able to boot to Ubuntu desktop. I began the install process and set sda4(the 20gb partition) mount point to "/" and tried install. I got errno5 at about 31% which if i remember correctly is a read/write error, but it doesn't state specifically whether its my USB drive or my hard drive.. or if this is really neither.. can someone help me?

---

### Post by lxtreeml on 2010-03-28
I'm sorry I seem to be fixing my own problems..but it's a learning experience right?

well I have successfully installed Ubuntu 9.10 on my extra 20gb partition with the alternate install image burned to a CD(because it wouldn't work on usb, said cannot read CD) after a few hours of downloading and installing updates it seems to be up-to-date now. I'm on windows 7 right now making sure GRUB is working for dual boot. my last question, is how can I get the backtrack 4 applications into Ubuntu? I know some people frown upon ubuntu with the backtrack repo's installed but backtrack gave me no sound, never loaded the right graphics drivers and would never recognize my wireless adapter. Since they both are based off of Ubuntu (well BT4 is anyway) I want to put the apps on that.. but I can never connect to offensive security's repo link..it seems to be down. Is there an alternate method of retrieving the applications like airckrack-ng?

---

### Post by lxtreeml on 2010-03-29
well once again I fix my own problem before any one of you "experts" chime in, I got more information from my fricken auto instructor at school then I did from a Ubuntu forum! I'm beginning to think this place is just for linux gurus to laugh at newbies mistakes. anyway, I successfully installed the aircrack-ng suite, and learned all about it, and used it. so if anyone ever comes across this and reads this thread, PM me so I can help you rather than post newb-comics for the mods

---

