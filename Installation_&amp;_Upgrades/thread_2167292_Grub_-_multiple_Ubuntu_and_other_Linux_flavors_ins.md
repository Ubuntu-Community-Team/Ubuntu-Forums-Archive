---
title: "Grub - multiple Ubuntu and other Linux flavors installed"
date: 2013-08-13
forum: Installation &amp; Upgrades
---

### Post by kornelix on 2013-08-13
I use multiple Linux installs to test my apps on multiple Linux flavors. This used to work OK with a custom Grub menu to show the name and release of each Linux flavor in the boot menu. No longer, apparently. The last two times I updated Ubuntu 12.04 (via Update Manager) I got a grub menu that included every grub.cfg on every disk and partition. Using update-grub and grub-install to reinstate my custom menu did not help - the total mess was always installed. I had to find and rename all grub.cfg files to stop this from happening. Now the custom menu works as always. 

Is there a way to stop this? Update Manager used to politely ask if I wanted to replace my custom Grub menu. No longer.

---

### Post by oldfred on 2013-08-13
I have the same issue of too many and some not really usable anymore installs. So I turn off os-prober and just use my 40_custom or config files.

 In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

      
 Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)


 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by kornelix on 2013-08-13
I do that too, but it no longer works.

I did a 'sudo update-grub' and a 'sudo grub-install /dev/sda', 
using a grub install with '30_os-prober' execute bit set off.

The mess comes back anyway.
The fix so far is to find all the grub.cfg files and rename them. 

This is hard to believe but I have verified this is happening 3 times.

---

### Post by oldfred on 2013-08-13
I would think that should have worked. Some do get confused on which grub is in charge and try fixing one that is not the boot grub.

You can post the BootInfo report to see if anything looks out of place.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by grahammechanical on 2013-08-14
It sounds like you are seeing the kind of Grub menu mess that happened when Grub 2.0 was introduced. Ubuntu 12.04 was released using Grub 1.99 but 12.10 was given Grub 2.0 which brought in submenus. When we have multiple installs then we get a Grub menu that duplicates the menu lists from the config files of every install.

This does not happen if every install is using Grub 2.0 or we do not update Grub on the install still using Grub 1.99. We need to use one version of Grub or the other and keep that in the MBR.

Regards.

---

