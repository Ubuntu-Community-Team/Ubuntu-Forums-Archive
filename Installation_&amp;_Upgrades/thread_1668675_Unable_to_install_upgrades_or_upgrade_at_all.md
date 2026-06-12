---
title: "Unable to install upgrades or upgrade at all"
date: 2011-01-16
forum: Installation &amp; Upgrades
---

### Post by shawfield on 2011-01-16
Hi

Tried doing standard updates. Failed with 'incomplete installation' error.

Tried the various support forum advice. Tried sudo update manager -d.
Got this message...no updates done.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  cups gnome-bluetooth gnome-system-tools gnome-user-share ibus-pinyin
  ibus-pinyin-db-open-phrase indicator-applet indicator-applet-session
  indicator-application indicator-me indicator-messages indicator-session
  indicator-sound libappindicator1 linux-generic linux-headers-generic
  linux-image-generic network-manager-gnome ntfs-3g python-appindicator
  python-mako ubuntu-desktop
0 upgraded, 0 newly installed, 0 to remove and 22 not upgraded.


Help ?

---

### Post by shawfield on 2011-01-17
Bump

Managed to do a 'partial' upgrade, now wont reboot & stops at a Grub command line, inviting me to press tab to see a list of commands

---

### Post by Rubi1200 on 2011-01-17
Hi,
which version of Ubuntu are you using?

Try these commands and post back with errors (if any):

```
sudo apt-get install -f

sudo dpkg --configure -a

sudo apt-get update
```

---

### Post by shawfield on 2011-01-17
Many thanks

Unfortunately as I cant boot into Ubuntu I cant use the sudo command at all. Grub simply does not recognise the command.

I was using 10.10 & just tried to do the standard update but it wouldnt let me unless I agreed to do do a partial update.

It rebooted & now stops at the grub command line.

---

### Post by Rubi1200 on 2011-01-17
Were you trying to upgrade to 11.04? You do understand it is in alpha right?

So we can get a better overview of your current setup please do the following from a LiveCD/USB:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command      Code:
     sudo bash ~/Desktop/boot_info_script*.sh 
  This will create a RESULTS.txt file on the desktop. Paste the  entire contents of that file back here. Once pasted highlight all text  and click the # sign on the toolbar to place code tags around the text.

---

### Post by shawfield on 2011-01-17
Hi thanks again

Does this boot script work on windows ?  As thats the only OS I can boot into on the affected machine due to the 'stall at grub' problem.

---

### Post by Rubi1200 on 2011-01-18
No, the script needs to be run from within Ubuntu or by booting the computer with a LiveCD or LiveUSB.

I have a question, though: if you can boot Windows normally is this a Wubi install?

---

### Post by shawfield on 2011-01-18
Hi

No its a dual boot installation. Its only 10.10 thats caused me update problems & only recently.

Sounds to me as if I need to do a complete re instal ?

---

### Post by Rubi1200 on 2011-01-18
I don't think you necessarily need to do a reinstall (although you may have to).

I still suggest running the boot script and posting the results:

Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command

```
 sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

