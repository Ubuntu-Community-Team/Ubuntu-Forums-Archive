---
title: "ubuntu first windows second? dualboot"
date: 2015-07-28
forum: Installation &amp; Upgrades
---

### Post by peter203 on 2015-07-28
Hello, I'd like to know if its possible to install ubuntu first and windows second and have the possibility to dual run, if not, how do I save current settings I have on xubuntu so I dont have to do everything all over again? thanks a lot in advance

---

### Post by coffeecat on 2015-07-28
Yes it is possible to install Ubuntu first and then Windows and end up with a dual-boot, but that is not the best way to go about things because Windows will overwrite the bootloader which you then have to re-install from a live CD/USB session. Which is tedious.

That is with a legacy BIOS and MBR partition table. Things get more exciting with the newer UEFI BIOS and a GUID partition table (GPT).

Perhaps you can tell us more about your system and what you intend to do. You say install Ubuntu first, but then go on to mention your Xubuntu system. Do you mean that you want to keep Xubuntu and then install Windows? Or do you mean that you want to replace Xubuntu with Ubuntu and keep your home partition (if you have one)? Or something else?

Post the terminal output of this command from Xubuntu:

```
sudo fdisk -lu
```

And tell us as much as you can about what you wish to do.

---

### Post by peter203 on 2015-07-28
Well I used to have windows XP preinstalled but its support ended, so I was looking for some alternatives, I did upgraded my HDD to SSD & got the xubuntu, but then I was missing some stuff from windows AND most importantly I got the feeling that Im not having full potentional of the SSD coz its kinda slow & the system is kinda laggy whilst on browser or such + it keeps ask me for update in kinda huge files if I dont do it everyday 50mb & sometimes it dont even let me do the update cause it says there's not enough space which is obviously not true. But I guess its my mistake because Im new, but I kinda dont rly have time right now to dig the stuff all the time (+ I think I dont have the correct drivers but maybe its just my guess). For now I kinda like it but I thought maybe I can have 2 systems & use one or the other depending on what I want to do, but since I dont wanna go all over again the stuff to set up the xubuntu so it works or looks close to my needs I was hoping for some shortcuts.

PS: what does mean /dev/mapper/sdb5_crypt doesn't contain a valid partition table 
                               /dev/mapper/xubuntu--vg-root doesn't contain a valid partition table

---

### Post by oldfred on 2015-07-28
Did you install with full drive encryption? That uses LVM.
Many users with LVM are not correctly housecleaning old kernels. The /boot partition with LVM is not huge and fills up. Many many threads in Forum and other sites on full /boot when using LVM.
LVM is an advanced partitioning tool, but required with full drive encryption.

I do not use LVM, not sure if it works well with SSD or may need different settings.
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

When I added my SSD to my part 2006 and part 2009 system in 2011, I could not justify the new system that I wanted. It worked so fast with the SSD, that I lasted until last fall before new system. And new SSD, lots of RAM and just newer hardware makes for a very fast system. But somehow I still only type at same old slow speed. :)

---

### Post by peter203 on 2015-07-28
yes I installed full drive encryption coz I thought it might be ok, but now Im not sure heh I use only 1 storage drive tho.
you said "Many users with LVM are not correctly housecleaning old kernels" how do I make proper cleaning?
Also do you know if there's some tool or command or something that could save my current settings so I dont have to do it all over again if I decide to reinstall or such? 
Last question if u can, how do I know I have proper firmware? I remember I did install some drivers long time ago (cant remember exactly how now) but is there some way to know the drivers are correct? Also Im thinking maybe the graphic driver is not updated or such coz its old notebook and I assume it uses some integrated GPU instead of normal one. big thanks again

---

### Post by oldfred on 2015-07-28
If Intel there is only one open source driver. (although that may change). But some need boot parameters to make them work with correct X by Y to match monitor's size.

Another thread.
[http://ubuntuforums.org/showthread.php?t=2288602](http://ubuntuforums.org/showthread.php?t=2288602)

I prefer to use synaptic, but if you do not have space it may not install.

 Updates, backups, delete old kernels - TheFu in Forums
[http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](http://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs)

   RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

From live installer you should be able to mount encrypted partition and it will ask for passphrase. But you should have really good backups as any drive issue can damage the encryption and then there is no way to recover data.

 Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

