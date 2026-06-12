---
title: "/boot/vmlinux invalid on PPC running Ubuntu"
date: 2011-09-03
forum: Installation &amp; Upgrades
---

### Post by monstermash161 on 2011-09-03
Just installed 10.10 Maverick Meerkat on an iMac G5 and went through the upgrade to 11.04. On the restart, when it started rebooting, it enters yaboot to load the kernel, but when it tries to load linux (boot: Linux) it gives:
> /boot/vmlinux is not a valid ELF image.
I used the tab key to see what images were available and it gave the following:
> Linux              old
I can still boot to my 10.10 CD before loading yaboot, but I would rather not because I want to get to 11.04 eventually on this thing. Any suggestions?

---

### Post by Hakunka-Matata on 2011-09-03
[http://ubuntuforums.org/forumdisplay.php?f=328](http://ubuntuforums.org/forumdisplay.php?f=328)

I'm not saying you *should *go there, but it's the Apple Users area if you want to check it out.

So you're doing a regular ubuntu install on an iMac G5?  I don't know what yaboot is, I do know it's not the bootloader ubuntu uses.
Please attempt to download, install, and run boot_info_script package.  Post results.

---

### Post by monstermash161 on 2011-09-03
Just using apt-get I can't seem to find boot_info_script. However, I just specified old instead of Linux at the yaboot prompt, and it booted into 11.04. Is that weird? It doesn't have the hardware to run unity.
Looking through other similar threads it seems most people want to do a


sudo apt-get update && sudo apt-get install xorg ubuntu-desktop


and then switch the mirror to ports.ubuntu.com. Do you think that's necessary, or is this thing I have running now good?

---

### Post by spcwingo on 2011-09-03
You can get boot info script from here:

[http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.60/boot_info_script060.zip/download]("http://sourceforge.net/projects/bootinfoscript/files/bootinfoscript/0.60/boot_info_script060.zip/download")

---

### Post by Hakunka-Matata on 2011-09-03
> **monstermash161 said:**
> Just using apt-get I can't seem to find boot_info_script.[COLOR=Red] However, I just specified old instead of Linux at the yaboot prompt, and it booted into 11.04. Is that weird?[/COLOR] It doesn't have the hardware to run unity.
Looking through other similar threads it seems most people want to do a


sudo apt-get update && sudo apt-get install xorg ubuntu-desktop


and then switch the mirror to ports.ubuntu.com. Do you think that's necessary, or is this thing I have running now good?

No, that's not weird at all, it's the graphics thing most likely.  If it's the recovery kernel which it sounds like.
You don't need to run boot_info_script.  But if you want to, and I suggest it would be at the very least 'interesting", you should run it.  

Now that you are able to get up and running, Check to see if there are Additional drivers waiting to be installed.  
**System > Administration>Additional Drivers**

---

