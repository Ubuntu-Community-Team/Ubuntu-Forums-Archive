---
title: "Ubuntu boots and then powers down"
date: 2019-08-18
forum: Installation &amp; Upgrades
---

### Post by xtcmpfn on 2019-08-18
I recently had to replace my hard drive and I'm trying to install Ubuntu on the new one. I booted the installer from a USB drive, partitioned the new hard drive and the installation then went along perfectly. I powered off from the live Ubuntu and restarted my laptop. Ubuntu boots and gets to the GRUB screen where all the usual options are available. When I select Ubuntu on the GRUB screen, the screen turns the regular purple colour of the Ubuntu 19.04 background but then it turns black before the Ubuntu symbol and the row of dots appear and I get a bunch of messages. These are: 

```
 *Couldn't get size*: 0x800000000000000e 
/dev/sda2: recovering journal
/dev/sda2: clean, 213418/61022208 files 7688885/244059136 blocks
```

After I get these messages, the screen flashes and the messages reappear. Then the laptop powers down. 

As far as I can tell the last two lines of messages are just informational and I couldn't find a definitive answer online to what the first line means. It seems people generally have that message appear in conjunction with an error message saying MODSIGN: Couldn't get UEFI db list but I haven't had that error message appear any of the times I've tried to use Ubuntu on this new hard drive. 

I tried this fix: 

 
[LIST]
[*]boot to a Ubuntu Live DVD/USB 
[*]start gparted and determine which /dev/sdaX is your Ubuntu EXT4 partition 
[*]quit gparted 
[*]open a terminal window 
[*]type sudo fsck -f /dev/sdaX # replacing X with the number you found earlier 
[*]repeat the fsck command if there were errors 
[*]type reboot 
[/LIST]

(which I found here: [https://askubuntu.com/questions/924170/error-on-ubuntu-boot-up-recovering-journal](https://askubuntu.com/questions/924170/error-on-ubuntu-boot-up-recovering-journal)) and it worked once. When I restarted my laptop again, I had the same problem as before with the error messages and the computer powering down. I tried the fix again (and this time I also tried the same fix from root in recovery mode but neither managed to solve the problem. The laptop powers down now every time I try to get into Ubuntu. 

I've tried altering the boot settings (turning Secure Boot on and off; I also switched UEFI to Legacy settings and that didn't work but I figured that would be the case) and nothing worked there. 

I can boot the Ubuntu live environment from the USB fine (that's where I'm writing this post) but I cannot get past booting Ubuntu on my hard drive. 

My laptop is an ACER Aspire 315-51 and the hard drive is a Seagate Barracuda 1TB 2.5". If you need any more information, let me know and I'll edit this post to include it. 

I've tried altering the boot settings (turning Secure Boot  on and off; I also switched UEFI to Legacy settings and that didn't  work but I figured that would be the case) and nothing worked there. 

I  can boot the Ubuntu live environment from the USB fine (that's where  I'm writing this post) but I cannot get past booting Ubuntu on my hard  drive. 

My laptop is an ACER Aspire 315-51 and the hard drive is a  Seagate Barracuda 1TB 2.5". If you need any more information, let me  know and I'll edit this post to include it. I'm going to run a Boot Repair from the live Ubuntu on the USB and I'll edit this post so there's a link to the pastebin. 

Does anyone know what could be wrong here? I'm not new to Ubuntu but I've never had to solve a problem like this.

[EDIT] Here's the BootInfo 
: [http://paste.ubuntu.com/p/3DJx57CJnF/](http://paste.ubuntu.com/p/3DJx57CJnF/)

---

### Post by TheFu on 2019-08-18
[https://bugs.launchpad.net/amd/+bug/1776563](https://bugs.launchpad.net/amd/+bug/1776563)  might help. Lots of things to try.
Looks like some fixes got into 18.04 latest but not into 19.04.

---

### Post by crip720 on 2019-08-18
With installing a new hard drive and computer powering off, I am thinking hardware problem.  Could something simple as a connection not push in enough(it is push in, but still needs a bit more)  Had an ATV, would not start, turned out that one connector was still locked together, but had loosen about 1/16in, pushed back together and everything ran.

---

### Post by xtcmpfn on 2019-08-20
I already tried the hardware but I will have another look at it. Hard drive seemed to be fully secured to the connector last time I checked.

---

### Post by xtcmpfn on 2019-08-20
Just to update, I needed an OS so I installed Windows 10 from a bootable USB. I've partitioned so that I can dual boot Windows and Ubuntu. Windows works perfectly (so I'm figuring its not a problem with the hardware) but Ubuntu still has the same problem with shut down after trying to enter Ubuntu from the GRUB screen. The messages I was getting earlier have now disappeared so I'm also figuring that they had nothing essential to do with the problem.

Will try some of these fixes to see if anything works. Cheers guys.

---

