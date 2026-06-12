---
title: "confusion with grub - appears to have installed an old version?"
date: 2014-05-13
forum: Installation &amp; Upgrades
---

### Post by keratos2 on 2014-05-13
so I have installed minimal ubuntu and I installed grub to setup my boot.

I ran grub to make sure it was installed and exited without doing anything.

When I ran update-grub , it flew through during which is asked if I want to create a menu.lst ? WTF I thought. From all the latest distros I've been trying out they tell me a **/boot/grub/grub.cfg i**s used and a **/etc/defaults/grub** ??

So I said "Y" and then rebooted. Didnt boot. Grub entered a "rescue mode".

So I retrieved an old knoppix CD and booted up and somehow (took hrs) managed to get hold of, and run, **grub-install /dev/sda . **tthis did the trick because after a reboot grub counted down to 0 on "Stage1" then booted? Stage 1?? 

Something has gone wrong - the system boots - but when I installed the full blown ubuntu 13.10 unity desktop version, I just ran **update-grub **and it created a /boot/grub/grub.cfg file, and wrote the bootstrap to /dev/sda ; when I rebooted it did so  without a Stage 1 or 2  and appeared different menu?

What have I done and how can I return to the "newer" grub type system?

EDIT: ok, I installed the new grub2 and started over. 
All ok
But I still have to run update-grub and grub-install; I'm sure when I ran update-grub it automatically installed it too? maybe I'm imagining things?

---

### Post by oldfred on 2014-05-13
It sounds like you installed grub legacy (0.97) which uses menu.lst. It is still available. But its package name is grub.
With grub2 the package name is grub-pc for BIOS or grub-efi for UEFI boot.

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
 sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions

And/or you may want to make sure you have uninstalled all of grub legacy.
      
 # purge old and reinstall new to sda
sudo apt-get purge grub grub-pc grub-common
sudo mv /boot/grub /boot/grub_backup
sudo mkdir /boot/grub
sudo apt-get install grub-pc grub-common
sudo grub-install --recheck /dev/sda
sudo update-grub


 # kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)
# HOWTO: Purge and Reinstall Grub 2 from the live-CD/DVD/USB - drs305
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by keratos2 on 2014-05-17
that fixed it. THANKS

---

