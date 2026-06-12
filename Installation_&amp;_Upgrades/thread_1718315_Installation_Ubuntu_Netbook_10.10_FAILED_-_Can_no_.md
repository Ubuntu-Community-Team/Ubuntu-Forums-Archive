---
title: "Installation Ubuntu Netbook 10.10 FAILED - Can no longer access Windows"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by mcam101 on 2011-03-31
Yesterday, I tried Ubuntu 10.10 after occasionally using other distros of Linux from time-to-time on friends' machines. After deciding it trumped Windows in almost every way, I decided to install if from a USB stick. The installation appeared to work and I followed the instructions that were given on the Ubuntu download page. After it restarted, it booted back from the USB stick asking again if I wanted to try Ubuntu or install it. I tried to shut down however the only options I get in the power off menu (on the top right) are Suspend and Hibernate. I ended up turning the computer off by holding the power button on my computer (I know this has probably hindered me more than helped but I needed to shut down). When the power was off, I removed the USB stick and tried turning on the laptop again, however, I no longer get any options to get into my BIOS settings, and NOTHING will boot. I just get a black screen with a blinking white cursor in the top left corner.

I can still use Ubuntu by using the ''Try Ubuntu'' option when running from the USB stick but quite obviously this is not ideal.

I know I have probably wiped Windows Vista from my system (I had most data backed up a week or so ago, so all the important things I still have, however, if there is any way, I would like it all back). If anyone knows of any way to do a Super-System-Restore to revert back to Windows (if this is even possible) I would be very grateful.

Any help anyone can give me is greatly appreciated.

Kind regards,

Martin.

---

### Post by IWantFroyo on 2011-03-31
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
Plug in your backup stuff (assuming it was a full system backup, and not just the files) during the recovery, and it should find the image. 
You have an odd error.
Do you get anything while booting and holding esc? It sounds like an acpi error (I may be wrong). If you can get to the grub menu and press e on the first option, and put in acpi=off somewhere, it may boot.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

