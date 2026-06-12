---
title: "Grub error 17 Ubuntu"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by simonlugi on 2008-05-24
I have Vista, Ubuntu 8.04 and Xubuntu 7.10 installed on my 250Gb HDD drive on separate partitions. In attempting to uninstall Xubuntu I deleted a partition that I thought Xubuntu was on. 
Subsequently got the Grub Error 17 immediately after trying to boot. I got back to the page (using SuperGrub) that allows me to select OS options.  Vista boots up fine, Xubuntu boot is incomplete and I am left with an Orange screen. Ubuntu gives me the Error 17 message immediately after selection.

I have checked using the BIOS that the HDD is detected and the Mode is set on Auto and I have attempted to install the grubs using a live CD of Ubuntu 8.04.
These have failed and I still cannot get Ubuntu to boot.

Please can someone help. If need be (not the preferred option) I am OK if I have to uninstall and then do a reinstall Ubuntu as I do not have anything important.
Thanks Simon
Apologies if this is a repeat however I thought I had posted this message last night but cannot find the original this morning.

---

### Post by Pumalite on 2008-05-24
You can reinstall Ubuntu on top of the old one. Go Manual and choose the old partitions.

---

### Post by meierfra. on 2008-05-24
Try this to boot into ubuntu:

At the grub menu press "c"

Then type

```
find /boot/grub/stage1
```
(stage1 ends in the number one)

The output will be of the form

(hd0,2)
(hd0,4)

Of course the numbers will be different and if you actually deleted the xubuntu partition you might only get one line. Remember or write down the output.

Press "esc" to get back to the grub menu. Select ubuntu, But do not press "enter", press "e" instead. Press "e" again to edit the first line.

The line should look like

root (hd0,3)

You need to edit it so that it matches the output of "find /boot/grub/stage1". Probably you will just have to lower the second number by 1.

Press enter  and then "esc" to get back  to the Grub menu.

You should now be able to boot into Ubuntu.



The changes you just did  have  been only  temporarily. To make the changes
permanent you need to edit  "menu.lst"  via

```
gksudo gedit /boot/grub/menu.lst
```
(l is a lower case L)

Change "#groot (hd0,3)" the same way you just changed "root (hd0,3)"

Then in the terminal

```
sudo update-grub
```



If this does not work, boot from a live CD and post the output of "sudo fdisk -l" (l is a lower case L)

---

### Post by pietjanjaap on 2008-05-25
Install ubuntu, then choose to do the harddisk(wich partition to use) install yourself, delete your old xubuntu partion.
Then go back to the begin of install, and install again.

---

### Post by simonlugi on 2008-05-25
Thanks all for your suggestions greatly appreciated.
I ended up using meierfra's suggestion and this has worked with couple of tweeks.
When I had changed the root (hd0,3) to (hd0,2) I needed to press enter and then b (for boot). When I pressed esc after enter as suggested, the change was not saved,

Then for the permanent change in the menu.lst I changed the #groot (hd0,3) to #groot (hd0,2) as per meierfra's instruction plus all other references to (hd0,3) in the menu. 

Thanks again especially to meierfra. Fantastic has made my day. 

Simon

PS I am still only getting an orange screen at the end of the xubuntu boot. I am a bit nervous of trying to delete a partition again so maybe reinstall may be the way to go.

---

### Post by meierfra. on 2008-05-25
> When I pressed esc after enter as suggested, the change was not saved,
Oopps, my bad.


> plus all other references to (hd0,3) in the menu. 

"sudo update-grub" will do that for you. (That's actually the only reason to run "sudo update-grub". 

> PS I am still only getting an orange screen at the end of the xubuntu boot. I am a bit nervous of trying to delete a partition again so maybe reinstall may be the way to go

I'm pretty sure that your Xubuntu is deleted. At least you deleted SOME partition. (The advice I gave you was based on that assumption.) Just look at your partition with gparted (the Partition Editor)  If its really gone, just delete the Xubuntu item from "menu.lst" and you should be all set.

---

### Post by simonlugi on 2008-05-26
Thanks I will give it a go with the Xubuntu but it will have to be next week. 
Currently travelling so away from the PC with Xubuntu on it.

---

