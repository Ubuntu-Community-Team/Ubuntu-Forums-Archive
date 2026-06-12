---
title: "Help for installation on HP NC6220"
date: 2005-10-17
forum: Installation &amp; Upgrades
---

### Post by axe510 on 2005-10-17
Hi All,
I am quite new to Ubuntu and I apologize if my question might appear silly. 
I would like to install Ubuntu on my new HP nc6220 on an external usb Hd (30 GB) and I am afraid that the installation program will overwrite at least the MBR of my main HD on the notebook, which must be left untouched because used at work.
Is it possible to install Ubuntu on external HD, via usb port?
Is the installation program able to install on external HD without overwriting the main HD?
Thanks in advance for your support.

---

### Post by phen on 2005-10-17
it should be able to, so try it! you can tell the installation script what hd to use. plug you usb-drive in, and look through your bios: if you find something like "usb legacy support" it might be helpful to enable it. but you can try without it first.

during the installation, you have to be careful at two steps:
1.when the partition dialog comes up, you have to select your usb disk. 
2.when the grub installation dialog comes up, you have to choose your usb disk, too. note: this only makes sense if you can select "boot from usb" in your bios. if your bios is not able to boot from usb, you should be able to write grub to your internal hd without damaging your old system. you can make the old one you default, and use grub on every boot. otherwise you have to change the bios setting from "harddisk" to "usb" to switch between linux and your old system (windows?) 

i am in a bit of a hurry now, but if you ve other questions, feel free to ask. i am using a nc6120, and i think the bioses should be similar.

funny: today my father got a brand new hp nc6220 for work, too :-) maybe i know were youre working :) because the whole staff (the two of them using laptops...) changed their laptops from siemens/fujitsu to hp... if youre really working where i think, you are not able to change bios settings. so you're not able to use ubuntu. :-(

you can ask via pm, in case you're from germany...

---

### Post by axe510 on 2005-10-17
Thanks a lot.
I am writing from Italy, however I lived in Berlin for 1 year...
I will try it. 
Final question (..be patient...) I am not able to download the special custom version of ubuntu hoary for hp nc6220.
Can I try with the latest distribution (the 5.10)?
Thanks again in advance.

---

### Post by phen on 2005-10-18
then youre not working in the same company... it would have been a funny coincidence :-) All changes made for the hoary-hp version are included in breezy. i am using it right now and it works. I did not test everything yet, but there will be a wiki page soon! (about nc6120, but they have a lot of similar hardware!)

cheers

---

