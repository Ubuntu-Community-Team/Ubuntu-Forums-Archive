---
title: "how to get a grub menu"
date: 2018-09-10
forum: Installation &amp; Upgrades
---

### Post by skaiser on 2018-09-10
Hello, 
I have installed Ubuntu 16.04, which works, but now I installed Ubuntu 18.04 on my second harddisk, the installation process detected correctly the 16.04, but it does not show a grub menu, it boots directly into 18.04
I can boot 16.04, which is still my working Ubuntu by changing the UEFI order, but that works only once, the next boot is again 18.04 which is not yet ready for my critical wife.
I have tried to change grub/default but to now avail. Is there something I can do?
Thanks, Siegfried

---

### Post by #&amp;thj^% on 2018-09-10
A Menu should appear if you press and hold Shift during loading Grub.

For permanent change you'll need to edit your /etc/default/grub file -- place a **"#"** symbol at the start of line "GRUB_HIDDEN_TIMEOUT=0"
So it looks like this:
```
.
#GRUB_HIDDEN_TIMEOUT=0
```
Save changes and run "**sudo update-grub**" to apply changes.

---

### Post by yancek on 2018-09-10
Are both 16.04 and 18.04 UEFI installs?  Do you have a separate EFI (FAT32) partition on each drive?  Boot one of the systems and run this command and post the output here:

```
sudo efibootmgr
```

---

### Post by ajgreeny on 2018-09-10
I like to have a quick view of the grub menu at every boot so have edited the **/etc/default/grub** file to contain the following lines which do just that; it shows for just 2 seconds.
```
     	GRUB_DEFAULT=0
     	# next line will make countdown time show menu by default
     	GRUB_TIMEOUT_STYLE=MENU
     	# next line changed from 0 to 2 for 2 second delay; set delay you want.
    	GRUB_HIDDEN_TIMEOUT=2
    	# next line changed from true to false to allow delay countdown to show
    	GRUB_HIDDEN_TIMEOUT_QUIET=false
    	GRUB_TIMEOUT=2
        #Real OS name in next line in "" is helpful if more than one *ubuntu distro on machine.
    	GRUB_DISTRIBUTOR="Xubuntu-18.04-Bionic" 
    	GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
    	GRUB_CMDLINE_LINUX=""
```

On a UEFI booting machine you have to use Esc, not shift to show the menu, but that can still be difficult to get to work; repeated pressing of Esc will sometimes work but I have occasionally had to have many tries before it was successful.
This edit has removed that annoyance as the grub menu shows always.

---

### Post by oldfred on 2018-09-10
May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by skaiser on 2018-09-11
here is the output of eifbootmgr:
sudo efibootmgr
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,000D,000C,0003,0005,0006,0007,000E
Boot0000* ubuntu
Boot0003* UEFI: Built-in EFI Shell 
Boot0005  CD/DVD Drive 
Boot0006  Unknown Device 
Boot0007  Hard Drive 
Boot000C* ubuntu
Boot000D* UEFI OS
Boot000E  Unknown Device 

Hope You can see anything

---

### Post by oldfred on 2018-09-11
I prefer Boot-Repair as it also includes a full output of efibootmgr -v. The -v parameter includes lots of details on the UEFI boot entry that are needed, but then rest of report is needed to see that details match your UUID, GUIDs and other settings.

---

