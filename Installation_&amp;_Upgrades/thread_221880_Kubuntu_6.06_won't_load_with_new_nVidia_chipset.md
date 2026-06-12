---
title: "Kubuntu 6.06 won't load with new nVidia chipset"
date: 2006-07-24
forum: Installation &amp; Upgrades
---

### Post by wrp on 2006-07-24
I have tried to load Kubuntu 6.06 Desktop for AMD64 on a new PC
Asus A8N-VM CSM Mainboard (NVIDIA GeForce 6150 GPU and nForce 430 MCP)
Athlon 3500+ CPU with 1Gb RAM.
80 GB Seagate SATA HDD. 

Regardless of whether I use the normal or safe graphics mode the boot process gets to "mounting root file system" after "loading essential drivers" and then hangs. 
Has anyone else encountered this problem. 

(Windows 2000 has already been installed to a partition without problems and the machine appears to function perfectly with the MS O/S)

I have also tried with 5.10
Drops to text mode part way through and defaults to text login without x. 
Similar result with Mandriva One

I assume that I am missing required nvidia video drivers but is there anyway to get a functioning Kubuntu 6.06 system?
 
Any ideas??

---

### Post by BuffaloX on 2006-07-24
I have excact same mobo, but I have geforce 7600 gt graphic.
Everything works here.
LAN / USB / ata / SATA / graphics
I just installed nvidea using easy ubuntu
I haven't tried audio because I have a really nice audio card.
I think it may be the geforce 6150, that causes your problems.
I read somewhere that you need beter than geforce 6200 to use the nvidea drivers.

Try the vesa drivers, or the NV driver.

---

### Post by wrp on 2006-07-24
The problem is that I simply can't get the system to start and install!
Are there boot parameters I should modify or BIOS changes I can make so that I can get past this stage.

---

### Post by orb9220 on 2006-07-24
You could check your mobo website for firmware upgrades. I had seen threads of mobo with nvidea chipsets that solved thier problem with flashing thier mobo. Don't know if it applies to you tho.

Good Luck Sorry I couldn't be more help.

---

### Post by wrp on 2006-07-25
I have been using a KVM switch to swap between new and existing PC. (so I can stay on line etc)
I tried to load again but because I was not that hopeful I kept working on the other machine - it has worked!!
I still can't boot with the monitor connected but can boot without the monitor connected. 
I have tried to configure monitor and video card (KDE System Settings) and when I use the VESA driver (Generic) for my NVidia 6150 on board video and NEC Multisync 1550V Monitor I get a message from the Xserver "Sorry, this configuration video card driver and monitor does not appear to work".

---

### Post by wrp on 2006-07-25
Further
I can't find a combination of driver and monitor that doesn't give this error message. 
Clearly need the proprietary nvidia drivers but also need them for the nforce 430 chip setup as well. No lan connection so no internet. 
I have tried downloading the drivers directly 
needed binutils - loaded via usb key and dpkg - would have worked but 
Now the driver install wants linux source which doesn't come on the CD either and there seem to be too many dependencies to get a single file with  dpkg but still don'thave an internet connection......
Who said windows sucks.....?

---

### Post by BuffaloX on 2006-07-25
OK I have this problem that might give you a hint.

If I use Windows XP, I have to turn off the computer completely.
Before booting Ubuntu. If I try to boot Ubuntu after XP, my lan dosn't work.

Ubuntu has the drivers for the LAN, but XP does something, so it's not working in Ubuntu, except if I turn the PC off before booting Ubuntu.
Maybe there is solution for that, I haven't looked, because I use XP very rarely.

I haven't installed any special drivers for anything except the nvidea driver.

---

### Post by tseliot on 2006-07-25
Please follow these instructions:

1) Install Ubuntu using the **alternate installation CD**.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

---

### Post by wrp on 2006-07-30
Thanks so much for your help
I think I have probably misdiagonsed the problems.
With the Alternate CD I was unable to get started at all! 
The system would just hang after booting the kernel and trying to mount root file system. 
I had a look at the thread
  'booting stalls during "mounting root filesystem" '
and it seemed to describe my problem.
I have the mobo in an Antec case with built in card readers attached. 
When I disconnected these the installation went without hitch. 
I still don't know if it was coincidental but seems to boot reliably now without any special drivers apart from the std Ubuntu ones.
Will try the nVidia installation scripts next for improved graphics performance.
wrp

---

### Post by BuffaloX on 2006-07-30
Nice you have it working now. :D 


BTW.
The XP / Ubuntu swap works flawlessly now, and I didn't do anything for it to work, except installing the Nvidea network management software from the Asus CD. I found it annoying so it's disabled, but now I don't have to turn off after I have used XP.
I don't know if it was that, or a kernal update that fixed it.

---

