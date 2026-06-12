---
title: "How do I increase size of Home folder"
date: 2012-06-16
forum: Installation &amp; Upgrades
---

### Post by Chet Hardin on 2012-06-16
Hey. 

I installed Ubuntu dual-boot alongside Windows to see if it would work on my Thinkpad. It did, so I decided to re-install Ubuntu, this time wiping Windows. 

I can't figure out why, even though I have about 300 gb free on my hard drive my Home directory only has 2.5 gb of open space. 

Any help would be appreciated. 

Thanks.

---

### Post by wilee-nilee on 2012-06-16
> **Chet Hardin said:**
> Hey. 

I installed Ubuntu dual-boot alongside Windows to see if it would work on my Thinkpad. It did, so I decided to re-install Ubuntu, this time wiping Windows. 

I can't figure out why, even though I have about 300 gb free on my hard drive my Home directory only has 2.5 gb of open space. 

Any help would be appreciated. 

Thanks.

Boot the live cd or usb flash which ever you uses to install with, and take a screenshot of gparted which is on the live set up looking at the hard drive. 

Post it using the paperclip in the reply panel.

---

### Post by Chet Hardin on 2012-06-16
Hey, here you go. 

Thanks.

---

### Post by wilee-nilee on 2012-06-16
Looks like your HD is correct, and you are just booting to the sdb which is a full install as well.

sbd looks like it could be a usb flash or something, try booting without it plugged in.

You may have changed the boot order in the bios to the sdb first read change it to sda as well.

Both installs are one partition as well you can't resize home unless it has its own partition.

---

### Post by Chet Hardin on 2012-06-16
OH. I think that that's an SSD drive. Lenovo calls it a Hard Disk Driver Performance Booster. And I think that that's where Windows was installed.

---

### Post by wilee-nilee on 2012-06-16
To small for a windows install. unplug it and see if you boot to the HD, or can just run in the SSD.
```
sudo update-grub
```To have the HD install added to the grub menu.

If the HD is not booting by itself the update on the SSD may get you in where we can load the HD's mbr with the grub from the HD setup.

---

### Post by Chet Hardin on 2012-06-16
Hey Wilee-Nilee

Since it was a newish install, I just went ahead wiped the two drives, and installed the root and swap on the SSD and /home on the sata.

Thanks for the help.

---

### Post by wilee-nilee on 2012-06-16
I don't use a separate home myself, but when I have seen this advised I think the root would not be as small as the SSD is with a swap, I would look around for more info.

Just a heads up is all.

---

### Post by Chet Hardin on 2012-06-17
Appreciate it!

---

