---
title: "Feisty killed both Screen and Internet"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by H-Radical on 2007-06-28
Hi all,

I just 'upgraded' from edgy to feisty on my sony VAIO laptop, eventhough I knew I was getting myself into a lot of trouble, and sure enough... I'm in a lot of trouble. I would appreciate if someone help me with these asap, since I feel paralyzed without a functional computer right now.

1. For some weird reason, my screen is not working with X. After the Ubuntu logo, my monitor is completely blank. I hear the drum sound of the username prompt and if I type in my username/password, I'll hear the login sound too, but the screen is totally dead. My card, which I had got working on edgy thanks to a tutorial by tseliot is an NVIDIA GeForce4 420 Go. I checked my log files and the errors with the NVIDIA stuff have something to do with EDIDs, whatever that means. My xorg.conf was left untouched after the upgrade. In order to get the card working on edgy, I had the following line in xorg.conf, if it is of any help:
```
Option         "ModeValidation"   "DFP-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
``` (in the Section "Screen")

I would show you my entire xorg.conf, but I can't because I'm not on my own computer right now... which leads to my second problem.

2. My wireless network card (orinoco_pci)  is not recognized by feisty eventhough I had no trouble with it in edgy. I read somewhere that this is because of the newer kernels, and that I'll have to do something to the kernel and then recompile (big gasp for air). But that might be a fun challenge. 

If I had one of these problems I may not have been panicking so much but the two together are unbearable. As soon as I can I'll be getting lynx so that I can post more details.

Thanks for all your help in advance...
H-Radical

---

### Post by H-Radical on 2007-06-28
OK... now I have X (running on the "nv" drivers out of desperation).
I just checked and found out that my wlan card is  intersil prism 2.5 wlan, which is known to have problems with feisty. I read somewhere that linux-wlan-ng driver should fix the problem but I downloaded it and nothing happened. I don't know if I should activate it somehow or what.
I'm using wired lan right now, which is very inconvenient in my house, due to the location of the outlets... please help.

EDIT: ok... I was searching for a solution to my wlan problem and came across [http://ubuntuforums.org/showthread.php?t=286468&highlight=prism+wlan](http://ubuntuforums.org/showthread.php?t=286468&highlight=prism+wlan)  .
Pay attention to the post by Stani... it links to [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/63989)  . That's the bug report for this problem but the solution is right on that page. I tried
```
$ sudo modprobe -r orinoco_pci
$ sudo modprobe -r hostap_pci
$ sudo modprobe -r prism2_pci
$ sudo modprobe orinoco_pci
```
and right there and then wireless started up.

Now there's the nVidia problem to work out.

---

