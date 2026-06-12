---
title: "dual boot Ubuntu 32 and Ubuntu 64 bit"
date: 2008-11-07
forum: Installation &amp; Upgrades
---

### Post by christoforever on 2008-11-07
So i've installed ubuntu 32 bit. Then I went ahead and installed the 64 bit version, and during the installation it simply installed it on the free space on my hard drive... So my question is.. How do I get to that 64 bit version? There is no dual boot menu and yet it is physically there. I assume im missing something simple but I cant figure it out. Any help?

Sincerely,
Chris Dancy

---

### Post by cariboo on 2008-11-07
Do you know which version you are actually booting up to? I suspect you are using 64bit if you installed it after 32bit, to find out in a Applications-->Accessories-->Terminal type:

```
uname -a
```

the result should look something like this:

```
 uname -a
Linux willy 2.6.27-7-server #1 SMP Fri Oct 24 07:20:47 UTC 2008 **x86_64** GNU/Linux

```

See the bolded section.

Jim

---

### Post by christoforever on 2008-11-07
no. its booting into the 32 bit version. I've no way to reach the 64 bit unless I need to set some variable somewhere to give me the option to dual boot.

---

### Post by FrostyFlames on 2008-11-08
If you know it's installed you can venture into the grub list. I highly recommend you know what you're doing when you edit or change the file. If you can get into the grub bootloader you can edit the entries but they will reset. If you edit the grub list in linux and you screw up you're toast.

---

### Post by bulldog on 2008-11-08
Are they both on the same hdd,or do you have two hdd's?
Maybe ```
sudo fdisk -lu
``` in a terminal can give you some answer on how your hdd is partitioned.
Put the output of this command on the forums,so we can have a look at it.

---

### Post by christoforever on 2008-11-09
yes both OS's are on the same hard disk.

---

### Post by bulldog on 2008-11-09
Still want to see the output of```
sudo fdisk -lu
``` please :D

---

### Post by Otustelija on 2008-11-09
Can you get to Grub by hitting escape after BIOS boots?

If there is no option there for the 64 installation (which would be surprising), you need to edit /boot/grub/menu.lst to add an option for it. Just copy the option for your 32-bit installation and change the partition - like (hd0,0) to (hd0,1) or whatever your configuration is.

You shouldn't be able to do any lasting harm if you leave the other options as they are. Backing up the file is a good idea in any case, though.

---

### Post by christoforever on 2008-11-12
Sorry for replying so late. My hard drive crapped out and I just had newegg send me a new one 2nd day shipping. So listen to this... My first time around I installed Kubuntu64 first then ubuntu32 and thats when it started messing around... This time however I installed Ubuntu 64 bit and then Ubuntu 32 and it worked... Booting up brought me up a choice to pick which one... Unfortunately my wireless for both systems didnt work which i cant understand. So I reverted back to just 32 bit ubuntu where everything just works.

---

