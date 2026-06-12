---
title: "Intel Smart Response Technology with dual boot"
date: 2016-06-02
forum: Installation &amp; Upgrades
---

### Post by lukebenes on 2016-06-02
I solved the issue of the installer not recognizing drive with Intel Smart Response Technology by 

To get the Ubuntu live installer (normal version) to detect the drive,  in the 'Try Ubuntu before Installing' option, open a terminal and try  the commands on this page:  [https://wiki.archlinux.org/index.php...ID#Load_dmraid]("https://wiki.archlinux.org/index.php/Installing_with_Fake_RAID#Load_dmraid").  I think all that is needed is 
# modprobe dm_mod
# dmraid -ay
# ls -la /dev/mapper/
Then you can open the installer in the Live session and install.

You must also go back to Windows and open the 'Intel Rapid Storage  Technology' application and go to the 'Accelerate' Tab.  Disable  acceleration (this will not lose any data but will automatically back up  some data if you are using maximised option).  Then you should be able  to restart into GRUB.  You may need to try reinstalling GRUB (Google  it).  If the GRUB screen is present then you can go back to Windows and  re-enable acceleration in 'Intel Rapid Storage Technology'.

but now how can I get the Rapid boots to work on Windows 10?

---

### Post by oldfred on 2016-06-03
Post this:
sudo parted -l

These are now older threads, so do not know if they still apply. Intel SRT seems to be identical across brands.
 HP Envy  Windows 7 with MBR & SRT
[http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx](http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

---

