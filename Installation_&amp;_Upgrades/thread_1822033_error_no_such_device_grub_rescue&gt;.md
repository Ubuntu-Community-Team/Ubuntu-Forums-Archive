---
title: "error: no such device: grub rescue&gt;"
date: 2011-08-10
forum: Installation &amp; Upgrades
---

### Post by Nearl-86 on 2011-08-10
Hello i am having a slight problem with booting into ubuntu. I currently have ubuntu 11.04 installed on my internal hdd on my laptop. I was trying to install the same version of ubuntu on an external hdd for my wife to try with a live cd and was successful. But now my laptop wont even boot into the os selection screen in grub with out that external hdd connected to my laptop. it only displays, error: no such device: (long series of numbers for name of device) grub rescue> any help in fixing this would be fantastic as i feel like im going to put my forehead through the screen......

---

### Post by YesWeCan on 2011-08-10
Please dont do a head-plant in your monitor! :P

It's simple, but irritating. When you installed to the external the installer put the new Grub boot code on your internal disk rather than the external one. Which is idiotic but there you go. The new code looks for grub files on the external drive only. You probably cannot boot the external drive either, right?

To fix this, you need to reinstall the grub codes to both drives:
boot from a live CD/USB
[COLOR="Navy"]sudo  fdisk -l[/COLOR]      to see what the internal disk partition name is that contains your boot directory, eg: sda1
[COLOR="Navy"]sudo mount /dev/sda1 /mnt
sudo grub-install --root-partition=/mnt /dev/sda[/COLOR]

Then repeat this for you external, using the external partition and drive name, eg: sdc1
[COLOR="Navy"]sudo umount /mnt
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-partition=/mnt /dev/sdc[/COLOR]

---

### Post by raja.genupula on 2011-08-10
> **YesWeCan said:**
> Please dont do a head-plant in your monitor! :P

It's simple, but irritating. When you installed to the external the installer put the new Grub boot code on your internal disk rather than the external one. Which is idiotic but there you go. The new code looks for grub files on the external drive only. You probably cannot boot the external drive either, right?

To fix this, you need to reinstall the grub codes to both drives:
boot from a live CD/USB
[COLOR=Navy]sudo  fdisk -l[/COLOR]      to see what the internal disk partition name is that contains your boot directory, eg: sda1
[COLOR=Navy]sudo mount /dev/sda1 /mnt
sudo grub-install --root-partition=/mnt /dev/sda[/COLOR]

Then repeat this for you external, using the external partition and drive name, eg: sdc1
[COLOR=Navy]sudo umount /mnt
sudo mount /dev/sdc1 /mnt
sudo grub-install --root-partition=/mnt /dev/sdc[/COLOR]


dont mind if this is silly 

was the same process will be applicable if i have a grub rescue problem , i mean if i have two linux's and if i deleted the grub installed one and wanna move with second one .

---

### Post by YesWeCan on 2011-08-10
> **raja.genupula said:**
> dont mind if this is silly 
Nothing is silly when it comes to Grub questions. :)

> was the same process will be applicable if i have a grub rescue problem , i mean if i have two linux's and if i deleted the grub installed one and wanna move with second one .
When you get a grub-rescue prompt it usually means that the Grub program that is installed (usually) to the MBR "area" (first approx 50 sectors after the MBR sector) has looked in the partition it has been told to look in but either cannot find the partition or cannot find its files there. I believe if it does find its files but cannot understand or execute grub.cfg you get a grub> prompt and a lot more functionality.

Each time you install a new OS that uses Grub2, the Grub program gets reinstalled and is told to look in the boot partition of that OS. This is why if you delete the latest OS Grub won't work.

Unfortunately, the way Grub2 is normally installed it is not stand-alone and it depends on files in the OS it was installed with.

---

### Post by raja.genupula on 2011-08-10
> **YesWeCan said:**
> Nothing is silly when it comes to Grub questions. :)


When you get a grub-rescue prompt it usually means that the Grub program that is installed (usually) to the MBR "area" (first approx 50 sectors after the MBR sector) has looked in the partition it has been told to look in but either cannot find the partition or cannot find its files there. I believe if it does find its files but cannot understand or execute grub.cfg you get a grub> prompt and a lot more functionality.

Each time you install a new OS that uses Grub2, the Grub program gets reinstalled and is told to look in the boot partition of that OS. This is why if you delete the latest OS Grub won't work.

Unfortunately, the way Grub2 is normally installed it is not stand-alone and it depends on files in the OS it was installed with.
aah! great explanation man ..
 then now assume a case which i had experienced  previously . i have ubuntu at one partition and after this i had installed redhat . i had formatted redhat by using live cd . then if i used the above process then is it useful to do solving grub rescue issue for storing the grub to ubuntu

---

### Post by Nearl-86 on 2011-08-10
Awesome should have checked this thread sooner, I tried something else that worked. I inserted my live disk and chose the option to upgrade 11.04 to 11.04 so this way I could keep all my files. That fixed the grub the way it was supposed to be but I lost my system settings in the process. No big deal though took 5 min to set up again. Thanks for the info!

---

