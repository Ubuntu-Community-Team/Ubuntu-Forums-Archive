---
title: "unnecessary failsafe reboot leaves user locked out"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by bunty on 2010-11-21
Hi,

subsequent to a 10.4 update not having an option to turn off the computer 
[http://ubuntuforums.org/showthread.php?p=10143284#post10143284](http://ubuntuforums.org/showthread.php?p=10143284#post10143284)
, the user used shutdown command to force it off.

This now seems cause a failsafe reboot leaving the user at a login prompt in a failsafe boot without networking and unable to do resolve the problem and without the possibility for me as remote admin to even see what is going on. 

After command line login , both reboot command and cntl-alt-del do not clear the problem and kubuntu reboots to this crippled state. 

After a painfully long international phone call with "enter this " " now what do you see" type of debugging with a totally non-tech user I was finally able to find out it was automatically booting in failsafe mode. 

Having got the user to interrupt grub and select the normal boot option it booted perfectly, there was NO problem OTHER than the damn thing automatically and presistantly doing a failsafe reboot and without it even warning the user. 

I see several problems here:

1/ A shutdown command is not the cleanest way to turn off but should generate a persistent non-existent error condition on restarting and then change the boot option.

2/ Having logged into the console and done either reboot or cntl-alt-del the false error condition still remained. 

3/ Masking over the grub menu seems to be all the fashion these days (we have to make it as much like windows don't we !)  BUT if the system "thinks" it needs to change the boot options it had better display what is happening clearly to the user.  Doing this sort of fundamental change of functionality behind the curtains is the best way spread confusion and panic in your dumbed down target user base. 

What is causing it to boot failsafe grub option after using shutdown? I don't see this on other distros.

TIA.

---

