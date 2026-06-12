---
title: "Ubuntu install on Acer Aspire one"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by havok2 on 2008-12-01
I have an Acer Aspire one netbook which comes with Windows XP/ 120G hd and 1G mem.   I am trying to get ubuntu on it, everything I have tried with UNR images on usb or booting iso from external cdrom fails.  What am I missing here or does somebody have better instructions with good images as the usb one says its missing an image in the path.  Also when booting from cdrom it immediately goes to windows even though I tell it to boot to CDROM, which looks like it doesn't like what it sees.  I have booted off this same cdrom on another machine with an internal cdrom.

---

### Post by jaminthorns on 2008-12-01
I simply downloaded the latest ubuntu 8.10 image and put it on my usb drive using unetbootin. When I booted up my One, I used F12 to boot from the USB Drive. When a menu comes up just hit "default" and let the LiveCD boot up. I used the installation method that wiped the whole disk and left no trace Windows. When I first logged on I had to install MadWifi to get the wireless to work.

MadWifi: [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz)
-uncompress the package with the package manager
-go to the terminal and type in "cd *whatever_folder_you_just_extracted*" and enter
-type "make" and enter
-type "sudo make install" and enter
-type "sudo gedit /etc/modules"
-add "ath_pci" to the very end
-reboot!

---

### Post by havok2 on 2008-12-01
I tried the unetbootin and tried to boot up on default, it wouldn't come up, then tried the OEM option and got further but still errored out.  I will try the default again after reburning it to usb.

---

### Post by jaminthorns on 2008-12-01
Fore some reason, when I first downloaded the iso, i tried to get the image on the USB Drive under Ubuntu but it didn't work, then I downloaded  and put the file onto the USB drive in windows Vista and it worked flawlessly. If youhave a Windows system you should try that.

---

### Post by havok2 on 2008-12-01
I reinstalled the image via unetbootin and it worked this time.  I don't know what changed but all is good.  Thanks for the wifi link, I'll get that installed.  Appreciate the help.

---

