---
title: "Xubuntu fresh install gives wrong Grub label"
date: 2013-10-09
forum: Installation &amp; Upgrades
---

### Post by madtom1999 on 2013-10-09
Just installed 13.04 64 bit alongside a whole bunch of others and the Grub label for it is "ubuntu"  which is not quite right.

---

### Post by oldfred on 2013-10-09
It is Ubuntu and grub does not really know what desktop you are using.

I turn off os-prober and add my own boot stanzas to 40_custom. Then I can label them any way I want.

       Copy the  entries from this:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
gksudo gedit /etc/grub.d/40_custom
Then do:
sudo update-grub

IF new entries work ok, you can turn off os-prober.
      
 In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

You can also use some gui tools like grub customizer, but it seems to create a lot of extra grub files in the scripts.
      
 New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)

      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by madtom1999 on 2013-11-28
All other intallations seem to know which release/version they are installing and update grub accordingly.

---

