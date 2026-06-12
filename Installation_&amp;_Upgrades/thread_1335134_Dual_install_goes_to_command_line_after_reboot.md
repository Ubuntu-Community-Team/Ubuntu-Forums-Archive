---
title: "Dual install goes to command line after reboot"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by skyplex on 2009-11-23
I have tried to install using the Ubuntu 9.10 Alternate iso downloaded with bitorrent on a HP XW6000. 
I chose to install in the free space on a drive that also has Windows XP installed on the 1st partition.
After install reboot and selecting the Ubuntu normal from GRUB2 the screen goes to 
```
fsch from util-linux-ng 2.16
/dev/sda5: clean, 38406/5603328 files, 549952/22390585 Blocks
*Setting prelimary keymap...
*Setting up console font and keymap...
Ubuntu 9.10 XW6000 tty1
XW6000 login:
```I logged in as root and did fsck -v; some repairs were done but reboot into Ubantu normal still goes to command line.
I rebooted into recovery mode and I am back to the command line.
I have typed 'help' and a list starting with 'complete' to while COMMANDS shows.
What should to do now to repair the install?
Any help would be appreciated.
Thank you, Jeremy

---

### Post by darkod on 2009-11-23
I haven't used alternate iso but I think if you missed to select desktop gui to be installed, it's not. So this is not an error, you have only text based system.

You do not have to reinstall, you should be able to add the desktop with:

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
sudo /etc/init.d/gdm start

```

---

### Post by skyplex on 2009-11-23
Thank you.
That worked but not before I re-burned the disk image(.iso) file to a DVD-R disk using the open source InfraRecorder. The install command ran slowly and had lots of can't get errors. 

My problems since I started this sojourn have been with the burning process.(I cant say I wasn't warned but I thought I was checking the disks data integrity as I went.) I think after a while I will start again with a new burn of the Ubuntu-9.10-Desktop.iso just to see how it is supposed to work.

---

