---
title: "[SOLVED] network problems with linux 2.6.27-4 (I think)"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ubername on 2008-09-27
Hi

I recently upgraded my intrepid install using the normal method (i.e. automatic updates). I lost any network connectivity (internet or local network)

So, to address this without troubling this forum, I tried to reinstall from an 'Intrepid nightly builds alternative' CD (high risk I know, but I have other partitions / computers!), which said it could not find my NIC card. So, to get round that I reinstalled  ubuntu 8.04 from the AMD64 desktop disk. This worked, so I then followed this thread for updating to intrepid from hardy [http://ubuntuforums.org/showthread.php?t=834808](http://ubuntuforums.org/showthread.php?t=834808), and rebooted, following all the advice about not doing partial upgrades. Again, success (i.e. I had a working ubuntu which system manager told me was Intrepid, but running the 2.6.24-19 kernel) So then again I followed the automatic updates route, to find that my  connectivity was gone.

Thankfully I have an 8.04 install on this machine so I can report this. 

Any one else seeing this problem? - I can see how it would be difficult to report if your connectivity has gone.

TIA (Posting from my 8.04 setup)

---

### Post by nanog on 2008-09-27
run lspci and see if you have an 82566 or 82567 based nic.

```
lspci | grep 8256[67]
```

If so your card has now been disabled due to a serious kernel bug. 

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/263555](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/263555)

A temporary work around will get you back online:

```
sudo apt-get install linux-headers-2.6.26-1-rt linux-image-2.6.26-1-rt linux-headers-rt
``` 

If you are running nvidia you may have to reboot or reinstall the dkms module. 

```
sudo dkms build -m nvidia -v 177.76; sudo dkms install -m nvidia -v 177.76
```

replace 177.76 with whatever nvidia-driver you are using. (dpkg-l | grep nvidia-glx). you may still have to reboot.

---

### Post by mc4man on 2008-09-27
It sounds if your nic is on the new blacklist as you can read about in the sticky (using intel e1000e driver.

If you run 
```
sudo lshw -html > hardware.html
```
you should be able to see what driver it's using. ( look in home directory for hardware.html, (listed under id- network

---

### Post by oldsoundguy on 2008-09-27
IF you need to change out cards .. consider one of those USB plug in networking units.  (a nic on a USB plug). I got one recently and now use it on all kinds of platforms.  Linux builds see it right away! .. and talk about cheap!  You can get them from dozens of Chinese sellers on eBay for MUCH less than getting a replacement card.
Prior to getting the thing, I had used a 3com 3C905 series PCI card, which worked all the way back to Win 98 and on every Linux build I ever used.

---

### Post by ubername on 2008-09-28
> **nanog said:**
> run lspci and see if you have an 82566 or 82567 based nic.

```
lspci | grep 8256[67]
```

If so your card has now been disabled due to a serious kernel bug. 

[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/263555](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/263555)

A temporary work around will get you back online:

```
sudo apt-get install linux-headers-2.6.26-1-rt linux-image-2.6.26-1-rt linux-headers-rt
``` 

If you are running nvidia you may have to reboot or reinstall the dkms module. 

```
sudo dkms build -m nvidia -v 177.76; sudo dkms install -m nvidia -v 177.76
```

replace 177.76 with whatever nvidia-driver you are using. (dpkg-l | grep nvidia-glx). you may still have to reboot.

Thanks

A couple of questions, if I may

FWIW:
john@USB-ubuntu:~$ lspci | grep 8256[67]
john@USB-ubuntu:~$ 

i.e. no evidence of dodgy card, but I am sure it is the issue.


But:
My grub doesn't automatically see the new version (I used synaptic but when I thought that was the problem this was the result:

sudo apt-get install linux-headers-2.6.26-1-rt linux-image-2.6.26-1-rt linux-headers-rt
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.26-1-rt is already the newest version.
linux-image-2.6.26-1-rt is already the newest version.
linux-headers-rt is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19 linux-headers-2.6.24-19-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

I am not going to get rid of 2.6.24-19, as I am using it to access the set-up.

So question 1 is what should I put in /boot/grub/menu.lst to see the new version.

Question 2 is

I downloaded kgrubedit (and all the associated packages with that) using synaptic and I can't find it anywhere, to update grub. In the past it would pop up in a menu item called 'System' (or similar) but I have no such menu item. I tried 

 sudo kgrubedit
sudo: kgrubedit: command not found

TIA

---

### Post by ubername on 2008-09-28
Sorted.

I added this to menu.lst

title		USB Ubuntu intrepid (development branch), kernel 2.6.26-1-rt
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.26-1-rt root=UUID=189d5806-5f5a-4a56-80bb-7d24c2efc84c ro splash 
initrd		/boot/initrd.img-2.6.26-1-rt

---

