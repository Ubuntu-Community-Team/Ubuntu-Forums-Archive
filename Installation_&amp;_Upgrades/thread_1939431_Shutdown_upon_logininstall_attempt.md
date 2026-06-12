---
title: "Shutdown upon login/install attempt"
date: 2012-03-11
forum: Installation &amp; Upgrades
---

### Post by wvxvw on 2012-03-11
Hello,

I'm trying to update Ubuntu 11.04 to 11.10. I have burned couple of CDs and created a bootable USB disc. Previously, I tried to update using update-manager. The update didn't go smoothly - there were 3 shutdowns during the update, which I attribute to Nvidia drivers (I've checked the logs while I still could, and saw errors coming from Nouveau driver mentioning unsupported chipset.

Whilst I certainly could mess things up during update, the live CD and the pen-driver are fine. Still, I can neither boot from either of them, nor install.

I've ran memory test, HD test, furmark and a bunch of other hardware tests - nothing suspicious.

I'm inclined to believe, it is the video card driver, precisely GeForce GTX 460. Nouveau drivers never worked for this card, but the version distributed with Ubuntu 10.04 could run my videocard in lowres mode. The new install screen fits into "native" screen resolution, but after few seconds it short-circuits and the computer shuts down.

My questions are these:
- Is it possible to boot from the Live CD or USB in such a way, I don't have to run X server, or whatever creates the nice graphical interface of the install wizard?
- Is it possible to replace the drivers on the USB drive with the older versions?
- Could there be some BIOS settings that I might need to try to tweak in order for my videocard to act differently? I vaguely remember there were some graphical output related settings in BIOS once...
- Is it possible I'm "barking on the wrong tree" and I need to try something else, entirely? (I, unfortunately, have no clue what happens during an unsucsessful instal / login attempt, as I've lost all means of access to the file system / can see no console output).

Please, help :(

PS. When attempting to login to the existing installation on the HD:
- in normal mode, I am prompted with a message telling me that it can't load "Ubuntu" session. Beside that option, I only have rescue terminal session, but, unfortunately, to many things are broken, one of them is the network-manager, so I can't access internet, and, subsequently, can't download updates / install packages.
- in rescue mode, after the phase, when all devices are found and mounted, I'm prompted with the message saying that it shuts down Gnome, and it's either stuck there, or it may shut down some time very close to that moment. Keyboard interrupt won't work.

---

### Post by LinuxFan999 on 2012-03-11
> **wvxvw said:**
> Hello,

I'm trying to update Ubuntu 11.04 to 11.10. I have burned couple of CDs and created a bootable USB disc. Previously, I tried to update using update-manager. The update didn't go smoothly - there were 3 shutdowns during the update, which I attribute to Nvidia drivers (I've checked the logs while I still could, and saw errors coming from Nouveau driver mentioning unsupported chipset.

Whilst I certainly could mess things up during update, the live CD and the pen-driver are fine. Still, I can neither boot from either of them, nor install.

I've ran memory test, HD test, furmark and a bunch of other hardware tests - nothing suspicious.

I'm inclined to believe, it is the video card driver, precisely GeForce GTX 460. Nouveau drivers never worked for this card, but the version distributed with Ubuntu 10.04 could run my videocard in lowres mode. The new install screen fits into "native" screen resolution, but after few seconds it short-circuits and the computer shuts down.

My questions are these:
- Is it possible to boot from the Live CD or USB in such a way, I don't have to run X server, or whatever creates the nice graphical interface of the install wizard?
- Is it possible to replace the drivers on the USB drive with the older versions?
- Could there be some BIOS settings that I might need to try to tweak in order for my videocard to act differently? I vaguely remember there were some graphical output related settings in BIOS once...
- Is it possible I'm "barking on the wrong tree" and I need to try something else, entirely? (I, unfortunately, have no clue what happens during an unsucsessful instal / login attempt, as I've lost all means of access to the file system / can see no console output).

Please, help :(

PS. When attempting to login to the existing installation on the HD:
- in normal mode, I am prompted with a message telling me that it can't load "Ubuntu" session. Beside that option, I only have rescue terminal session, but, unfortunately, to many things are broken, one of them is the network-manager, so I can't access internet, and, subsequently, can't download updates / install packages.
- in rescue mode, after the phase, when all devices are found and mounted, I'm prompted with the message saying that it shuts down Gnome, and it's either stuck there, or it may shut down some time very close to that moment. Keyboard interrupt won't work.
The alternate CD contains a text based installer, which should work on a computer that the graphical installer doesn't run on. you cannot replace the drivers on a "live" Ubuntu system, whether it is running from a CD or a USB flash drive. You can replace the drivers on an installation of Ubuntu running from a flash drive. Some motherboards have settings in the BIOS that can change video card behavior. You should only try something else if the alternate CD of 11.10 does not work.

---

### Post by wvxvw on 2012-03-12
Thanks.
[s]Obviously, my next question is: how do I run the text based installer?[/s] OK, sorry, I misread you where you said alternate CD. I'll try that now.
Also, how would I replace the drivers? I've never done that before, and, to be honest, I don't even know where are they. Some insight into how to do that would be really welcomed.

---

### Post by ckasux on 2012-03-12
> **wvxvw said:**
> Thanks.
Obviously, my next question is: how do I run the text based installer?
Also, how would I replace the drivers? I've never done that before, and, to be honest, I don't even know where are they. Some insight into how to do that would be really welcomed.
try installing oem intaller first .load cd when menu starts press F4 pick oem go throw install on reboot you should still have ather installs but working

---

### Post by wvxvw on 2012-03-12
Here are the results so far:
- text mode install fails, which is even worse, it seem to damage the data on the USB, so after one attempt, the USB is no longer usable. 
- trying to boot into rescue mode from alternate install (USB) causes shutdown and the USB is no longer usable. It is not usable up to the level, that once trying to pass the BIOS setup, the loading will hang giving no signs of error.

Interestingly, I was able to login using HD installation, replace xorg.conf with the previous version, copy the Xsession from /etc/ to $HOME directory and I was able to login to runlevel 2 and runlevel 3.
Thus I was able to backup the system and store it to a different HD.
However, the top and bottom panels of Gnome are no more. I'm logging into Nautilus window, which shows my desktop. I'm able to access terminal and launch most other applications.
Unfortunately, network-manager is either broken or improperly configured, so I can't connect to the internet. I've tried to restart the service, tried to restart network interfaces - all to no effect.
```
nmcli con up id <connection id>
```
fails telling the interface is either not managed, or unavailable.
When I try
```
ifconfig
```
and 
```
netstat
```
I can only see lo interface, neither eth nor ppp are listed (I used to be connected on ppp interface... duh).

Other things I've tried: creating live CD of Mint 12 - similarly to others, it fails on startup and computer shuts down.

My questions:
- how would I troubleshoot network manager. I hope that using it, I might be able to further try autofix with aptitude?
- synaptic is gone (uninstalled during upgrade for w/e reason). Is there a way to get it back?
- how do I get the top-bar of Gnome (I don't know how to run all administrative tools from command line, and that bar would be really helpful).

Thanks.

---

