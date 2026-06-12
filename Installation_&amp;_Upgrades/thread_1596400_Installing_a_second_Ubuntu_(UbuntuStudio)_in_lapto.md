---
title: "Installing a second Ubuntu (UbuntuStudio) in laptop"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by McCorby on 2010-10-14
Hi all,
Sorry I could not find a proper thread for this.
I got installed Ubuntu 9.10 in my laptop. That's the sole OS in the machine.
I would like to install UbuntuStudio in the same machine so that I will have both OS.
Can I have both Ubuntus installed? Maybe using GRUB? I'm a bit newbie to installation processes.

I've already got UbuntuStudio in DVD for install.

Thanks,

Jose C.

---

### Post by renzokuken on 2010-10-14
yes you can. my advice would be to create a second empty partition on your hard-drive. then install ubuntu-studio on that partition (making sure not to touch your existing ubuntu install)

installing ubuntu studio should detect that you already have another OS installed and automatically set-up the grub bootloader for you so you can choose which one to boot when you start your computer

---

### Post by cchhrriiss121212 on 2010-10-14
You can also just upgrade your existing Ubuntu to Ubuntu Studio with the DVD, it will be much easier and there are basically no downsides.
Open synaptic package manager and add the DVD as a source, then install the studio meta package.

---

### Post by garvinrick4 on 2010-10-14
Put in a live ubuntu cd (install cd) and open gparted:
They way it is usually done is to go into gparted and make a new partition whatever size you want. (read up on use of gparted is really pretty simple but have to stay focused.)
 Choose manual at install and select sda2 to install (or whatever open space made in gparted) if 2 gig or over RAM forget about swap. Put grub in sda or the name of drive. NOT in sda1 or sda2 or sda5 but sda. Hit install and done will put your new install in sda2 or whatever you choose to put it in and put grub in right place. 

*While using gparted you must hit green apply arrow to apply the change.
* You can google gparted and get info on use of. 
* If you feel uncomfortable with using manual install and making your own partitions can use side by side and will give half to first install and half to second install and make  partitions for you. When you see anything to do with grub it always go's in drive you are installing on. sda if a second drive sdb if a third drive sdc, Ok. You are using sda never put in sda1 or sda2 always the drive sda and then it will get into your mbr (master boot record) where it belongs.
* To make a new grub config file with grub boot menu always ```
 sudo update-grub
```
* To see what grub boot menu looks like: ```
grep menuentry /boot/grub/grub.cfg
```

---

