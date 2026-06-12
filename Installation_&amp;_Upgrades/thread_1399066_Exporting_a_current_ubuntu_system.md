---
title: "Exporting a current ubuntu system"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by bigboss0101 on 2010-02-05
Hello everyone. I have Ubuntu Karmic installed on my desktop PC. Hvae lot of applications installed and customizations etc. I want to shift this exact setup to my laptop that doesnt have any Ubuntu installation yet.

What could be the effective way of doing this? Any help would be greatly appreciated. Thank you.

---

### Post by tommcd on 2010-02-05
There is a tool called **remastersys** that should let you make a custom live CD that you can use for this.
See this:
[http://www.ubuntugeek.com/create-custom-ubuntu-live-cd-with-remastersys-in-karmic.html](http://www.ubuntugeek.com/create-custom-ubuntu-live-cd-with-remastersys-in-karmic.html)
Hope this helps.

---

### Post by amac777 on 2010-02-05
You'll probably gets lots of different answers for this so wait a bit before you attempt any so you can pick the way that seems best for you.

My way is maybe not the "easiest" way, but it's the "most geeky" (in my opinion). Here is what I'd do: (don't attempt this unless you understand it and make sure you have backups)

1. Boot a Karmic (same version you are running your desktop) live CD on the laptop and make sure it runs and that the laptop can handle Karmic OK etc.

2. Make sure you have backups of all important files on the laptop (and desktop too just incase)

3. Use the live CD on the laptop to repartition (format) the hard drive in the laptop to ext4 (or ext 3 - use the same as what you are using on the desktop). This will erase all files on the laptop so that's why you need a backup from step 2.

4. Use Rsync to copy almost the entire system (base folder / and almost all sub directories) from your desktop to the laptop. (you may need to install ssh on your desktop so you can do this accross your LAN network) I said almost all because some folders should be excluded as follows:

```
sudo rsync -a --exclude='/dev' --exclude='/proc' --exclude='/lost+found' --exclude='/sys' user@desktop_ip_address:/ /media/laptop_mount_point

```
note: you may also exclude the /media and or /mnt directories if you don't need to copy all these over.

6. Add empty directories on the laptop for all the excluded directories:

```
sudo mkdir /media/laptop_mount_point/dev
sudo mkdir /media/laptop_mount_point/proc
etc

```

7. Then need to fix UUID (command: 'sudo vol_id --uuid /dev/sdb1') for laptop disk in:
- fstab
- grub menu

Basically, figure out what the proper UUID for the laptop's harddrive is and change the laptop's fstab and grub menu accordingly.

8. Install Grub bootloader on the laptop hard drive. I still use Jaunty so my instructions are probably not valid for Karmic so I won't type them here, but this should be easy to lookup for Karmic's grub.

9. Reboot laptop and it should boot up into a cloned version of your desktop system.

---

