---
title: "initrd.img-2.6.31-20-generic in latest update is corrupt"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by ldouble_e on 2010-03-21
I posted earlier about loading problems. It was far beyond anyone's knowledge in this forum. So I'll update on the issue. I ran sudo apt-get update and everything went fine. I restart and my grub loads and I arrive at GNU GRUB Version 1.97~beta4. If I select Ubuntu, Linux 2.6.31-20-generic or its recovery I get "error: Couldn't read file Press any key to continue". However, if I select 2.6.31-19-generic everything loads fine. Also when I tried using the command line everything went fine until "grub sh> initrd /boot/initrd.img-2.6.31-20-generic" it returns file not found. I got into 31-20-generic using the super grub loader disk. Once in I tried update-grub, apt-get update and upgrade, aptitude upgrade, apt-get -f install, dpkg --configure -a with negative results. The final thing I tried was sudo update-initramfs -u and still I can't load unbuntu unless I change my /boot/initrd.img file from 2.6.31-20 to 2.6.31-19-generic. I'm almost 100% that the latest update has a bug in it. Anyone have any other suggestions? I should also mention the initrd.img-2.6.31-20-generic file is located in my /boot/ directory right next to 31-19-generic and 31-14-generic packages so it is finding the file but is unable to read it.

---

### Post by ajgreeny on 2010-03-21
It's OK here so the download when you updated must have been corrupted.

Try ```
sudo apt-get clean
``` and then reinstall the 2.6.31-20 kernel again. It will have to be downloaded again for the install, and perhaps this time it will be OK.

---

### Post by ldouble_e on 2010-03-21
Clean did not work. I was able to fix it on my own. For anyone reading this with the same issue, here is how I fixed it. 2.6.31-19-generic worked so I booted that up. I went into the synaptic package manager. In the Quick Search box type: 2.6.31-20 and press enter. You should have three green boxes in there. Select all three of them. They should be called linux-headers-2.6.31-20, linux-headers-2.6.31-20-generic, and linux-image-2.6.31-20-generic. mark them for re-installation. Press apply. It will require restart. After restart my grub wouldn't load but that's common for me. Before you restart do this just encase you have the same issue. In terminal enter the following commands and write down the results.
```
sudo grub-probe -t device /boot/grub
``````
sudo grub-probe -t drive /boot/grub
```Device will list /dev/<root location> you need to know the root location. It will be sda1 or sdb1 or something like that. 
Drive will show where to set your root. It will be some thing like (hd1,1) or (hd1,0) or possibly even (loop0) if you have a wubi install. 
I have Device /dev/sdb1 and Drive (hd1,1)
Now restart and if everything works great! If instead you see grub sh> which is the command line don't worry you have what you need already, to load your grub.
Type the following substituting (hd1,1) for what you wrote as your Drive and sdb1 for what you wrote for Device
```
set root=(hd1,1)
``````
linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sdb1
```**If you have a wubi install, after sdb1 press spacebar and enter:
loop=/ubuntu/disks/root.disk ro
```
initrd /boot/initrd.img-2.6.31-20-generic
``````
boot
```Now ubuntu will load if everything was typed correctly. Once in ubuntu open the terminal and type the following:
```
sudo update-grub
```Next time you restart the grub will load and so will your vmlinuz-2.6.31-20-generic kernel. Life will be good once again!

---

### Post by ldouble_e on 2010-03-25
Now it won't find the linux headers. I've reinstalled them several times with no luck. I know I'm not going to get an answer to this question. I just realized why Windows is better than linux and that sucks. I guess I'm going to be stuck in 2.6.31-19 until version 10.04 comes out.

---

