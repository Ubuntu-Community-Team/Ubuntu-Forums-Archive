---
title: "Dual boot 2 different distros?"
date: 2005-07-02
forum: Installation &amp; Upgrades
---

### Post by Uta on 2005-07-02
I have installed Kubuntu, configured it, printers, CD burner, wireless card etc...everything works great and I have learned so much from this forum and from the actual hands on of configuring my laptop to run Linux, ah but now I am ready for the next LINUX adventure and that is to dual boot into a different distro (Mandrake, SUSE, not sure). I have a 2nd 20G HD, hdc1, that I would like to install a different distro on. IF I make this a dual boot, when I am installing the 2nd distro on the secondary drive and go to install (let's say this is a Mandrake install) the bootloader, where is this going to get installed, is it like Windows;  will it be placed in the MBR? Is this possible, how stable is this kind of configuration?  Anyone with experience in doing this, I would certainly appreciate you sharing your install steps and suggestions on a complimentary distro. Thanks in advance.

---

### Post by Xian on 2005-07-02
[QUOTE=Uta]when I am installing the 2nd distro on the secondary drive and go to install (let's say this is a Mandrake install) the bootloader, where is this going to get installed, is it like Windows;  will it be placed in the MBR?[/QUOTE]
Most installers will allow you to direct where the bootloader should be installed. If you instruct it to go to the MBR then it will write over any present configuration and replace it with that distro's version. You can also install it to the newer distro's root (or /boot partition if applicable), and that will allow you to continue using your present bootloader. 

You would then just need to go back and add your new distro's pertinent kernel info to the /boot/grub/menu.lst file. Or you could use the [Grubconf](http://www.freewebs.com/bored2k/grubconf_0.5.1-4ubuntu2_i386.deb) program to do this as well once you have all your partitions mounted.

---

### Post by Uta on 2005-07-02
Once I install the new distro and since at that point I won't have made a new entry, where do I get the info to make an entry if I am still booted in Kubuntu? I assume I'll have to hit the escape key to choose which distro I want to boot from once I do enter the additional boot info (no GUI chooser?)?
Is the Grubconf the answer to where I'll gather the info I need to put in my  menu.lst ? Thank you!

---

### Post by Xian on 2005-07-02
[QUOTE=Uta]Once I install the new distro and since at that point I won't have made a new entry, where do I get the info to make an entry if I am still booted in Kubuntu? [/QUOTE]
You will get that info from the /boot/grub/menu.lst file of the new distro installation. Grubconf can assist you in this by providing a nice graphical approach. If you have any difficulties you can just post that menu.lst file.

---

### Post by Uta on 2005-07-03
Back again with more questions. I installed Mandrake 10.1 official on my second HD, which is in the modular bay of my laptop. It's a 40G drive that I divided into to 2 sections. The first 20gigs I used for MAndrake and the other 20G I left alone for that is for sharing and is formatted in FAT32. The install went well though I think the reason the install distro is not showing up in GRUBCONF is the choice I made for the bootloader? I chose "first sector of the root partition" meaning I am installing on /media/hdc1 (which got partition for this install) while /media/hdc2 remains untouched and is used for sharing. When I launch Grubconf it only gives me hdc5(ext3) and hdc6(swap) and hdc7(ext3), no hdc1? When I look at the drive in GParted I see it partitioned correctly...
What do I do now and why isn't it showing up in Grubconf? attached is the partition image.Thanks!

---

### Post by coolclassic on 2005-07-03
I found it hard to configure my own grub menu so the way I got round it is to copy your grub configuration from one menu.lst and paste it into the one that boots. 

Hope it helps

---

### Post by Uta on 2005-07-03
I can't get a look at the new installed distro's menu.lst because when I boot it goes right to Kubuntu, I don't know how to boot to the new system since it's not listed in the default distro's GRUB list. Thanks for your input.
--------------------------------------------------------------
My first install of Mandrake 10.1 I have deleted and will reinstall. Here's my info:
I have Kubuntu installed on my Dell C800 laptop and it's great but for furthering my knowledge of Linux I want to install Mandrake 10.1 on the 2nd HD that is in the modular media bay. It's address is hdc1 & hdc2. I split this 40G drive in half; the 2nd half is 1 primary partition, formatted as FAT32 and the 1st partion I will give to Mandrake. My question is this, when I go to install/partition the hdc1 for Mandrake and it asks where I want to put the bootloader, where do I put it? MBR,1st partition (forget floppy) or nothing? If I chose nothing and just wanted to add this distro to the already installed GRUB for Kubuntu (add to the menu.lst) how do I access the Mandrake info to add to Kubuntu's menu.lst? After I  install Mandrake and do a reboot it's going to boot into Kubuntu, which is fine and I do have Grubconf installed but I don't have the boot/kernel info for Mandrake... How can I best do this? Thanks in advance!

---

### Post by coolclassic on 2005-07-04
You will find menu.Ist here:
/boot/grub/menu.Ist

This is in your root dierctory

---

### Post by Xian on 2005-07-04
[QUOTE=Uta]I can't get a look at the new installed distro's menu.lst because when I boot it goes right to Kubuntu, I don't know how to boot to the new system since it's not listed in the default distro's GRUB list. [/QUOTE]
You only need to mount the new distro's partition, open the /boot/grub/menu,lst file contained therein, then copy over the section that describes that distro's boot info to Kubuntu's menu.lst, and just format it like the rest of the entries.

For example, here's the boot info I once copied over from a Debian install:
```
title		Debian GNU/Linux, kernel 2.6.8-2-k7 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.8-2-k7 root=/dev/hda3 ro vga=791 quiet
initrd		/boot/initrd.img-2.6.8-2-k7
savedefault
boot
```

---

