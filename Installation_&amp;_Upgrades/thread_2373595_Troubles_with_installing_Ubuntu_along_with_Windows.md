---
title: "Troubles with installing Ubuntu along with Windows 10"
date: 2017-10-07
forum: Installation &amp; Upgrades
---

### Post by daniel222 on 2017-10-07
Hi guys, bought some time ago new laptop and today decided to install Linux Ubuntu as i used to before. 
I get some troubles becasue after booting from USB getting some error's(tried already USB 2.0 and 3.0 with Rufus, Unetbootin, Universal-USB-Installer).
First screen:
[ATTACH=CONFIG]277016[/ATTACH]

After that tried with nomodeset and that also didnt help:
[ATTACH=CONFIG]277015[/ATTACH]
Any clues guys? Tomorrow I will try again with CD and maybe with anoter USB-stick. Thanks & regards.

---

### Post by ian-weisser on 2017-10-07
When using Windows, do the same USB sticks read/write normally?

---

### Post by daniel222 on 2017-10-07
yup, everything works propertly. 
just tried installing antergos. same story :/

@edit
unplugged my mouse from USB 3.0 + deleted secure boot keys from UEFI and errors about USB devices & initramfs are already gone but there are still those about kernel channel and claiming resources.
@edit2
did with nomodeset - error about kernel channel gone.
there are only these left about msft0101 - any clues?
@edit3 
finally get rid of errors from msft0101 after disabling TPM.
however i get new errors! FTW!
[ATTACH=CONFIG]277024[/ATTACH]

---

### Post by oldfred on 2017-10-07
What brand/model system? Some require extra boot parameters.
UEFI install?  See also info in link in my signature.

And if nVidia, you normally need nomodeset until you install and then install the nVidia proprietary drivers from the Ubuntu repository (not nVidia directly).
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by daniel222 on 2017-10-08
HP Omen, Win10, UEFI.
All the time was placing nomodeset before quiet splash ._. Will try your way in one moment.

@edit
That also didnt help :/
[ATTACH=CONFIG]277031[/ATTACH]
@edit2
Tried also running Ubuntu in Live Mode - turned off Fast Boot and it says Windows is in hibernate mode..

---

### Post by oldfred on 2017-10-08
UEFI has fast boot and Windows has fast start up which is just hibernation. They are separate settings.

 Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html) 

And Windows will regularly turn fast start up back on with some updates. And Windows updates may be in background, so you may not know for sure setting has changes.
Grub will not boot hibernated Windows nor Windows needing chkdsk. Best to make the Windows repair flash drive now before you have to have it.  You may need it whether installing Linux or not.

---

### Post by daniel222 on 2017-10-09
Ok, it went further but stuck again on "(initramfs) unable to find a medium containing a live file system" besides that I turned off already security boot and cleaned whole keys.

---

### Post by oldfred on 2017-10-09
Have you verified download of ISO was correct?
 [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) 


Have you updated UEFI from HP to latest version?

Older thread, but with updates and variety of suggested solutions.
[https://askubuntu.com/questions/15425/error-when-installing-unable-to-find-a-medium-containing-a-live-file-system](https://askubuntu.com/questions/15425/error-when-installing-unable-to-find-a-medium-containing-a-live-file-system)

---

### Post by daniel222 on 2017-10-09
Downloaded ISO from offical site + checked md5 already and its correct.
Ye, got HP software and that says everything is up to date.
Unfortunely cant try installing from CD because my notebook dont have CD-ROM.
Cant find any option in UEFI to change SATA mode to AHCI.
I will try in a few moments installing it on another PC.

---

### Post by oldfred on 2017-10-09
What SATA modes do you have?
Sometimes settings are hidden or at a lower level.
And sometimes you have to add an UEFI password (never lose that or reset to no password after) to see additional settings.

Lenovo got into trouble for not having an AHCI setting & had to release UEFI update.
 [https://linux.slashdot.org/story/16/09/21/1838252/lenovo-denies-claims-it-plotted-with-microsoft-to-block-linux-installs#comments](https://linux.slashdot.org/story/16/09/21/1838252/lenovo-denies-claims-it-plotted-with-microsoft-to-block-linux-installs#comments) 
[https://mjg59.dreamwidth.org/44694.html](https://mjg59.dreamwidth.org/44694.html)

If no AHCI mode, contact HP.

---

### Post by daniel222 on 2017-10-10
Cant find anything about SATA modes in UEFI even after setting an password.
Did some research and found that people already installed Linux on OMEN. 
I guess it already works on AHCI, however I will try to prove it on first.

@edit
In device manager -> IDE ATA/ATAPI controllers found: Intel(R) 100 Series/C230 Chipset Family SATA **AHCI **Controller, so I guess it already working on AHCI?

@edit2
"[COLOR=#000000][FONT=HPRegular]There are no BIOS settings to change the drive controller in HP consumer notebooks.  Only select business notebooks have that option."
[/FONT][/COLOR]https://h30434.www3.hp.com/t5/Notebook-Hardware-and-Upgrade-Questions/SSD-and-AHCI-mode/td-p/2513591

@edit3
Just read that AHCI mode is needed to get SSD's working propertly, didnt know that before. Anyway i got SSD & HDD, so we can confirm at this moment it works on AHCI?

---

### Post by oldfred on 2017-10-10
If it came with SSD, I would expect they have AHCI implemented.

In my Asus motherboard system many lines down:
```
lspci -nnk
.....
00:1f.2 SATA controller [0106]: Intel Corporation 9 Series Chipset Family SATA Controller [AHCI Mode] [8086:8c82]
    Subsystem: ASUSTeK Computer Inc. 9 Series Chipset Family SATA Controller [AHCI Mode] [1043:8534]
    Kernel driver in use: ahci
    Kernel modules: ahci

```

---

### Post by daniel222 on 2017-10-10
So I guess im already on AHCI mode, no other way. However, still can't get over that.

---

### Post by sharathpro on 2018-02-15
Any luck [COLOR=#000000]daniel222[/COLOR]?

---

### Post by oldos2er on 2018-02-16
sharathpro, please start your own thread if you need help; daniel222 hasn't returned to the forum since last October.

---

### Post by eureka117 on 2018-02-16
This looks like the grub2 was not properly installed. I recommend reading  
 
 
 [https://www.linux.com/learn/how-rescue-non-booting-grub-2-Linux](https://www.linux.com/learn/how-rescue-non-booting-grub-2-Linux)
 
 
 And scrolling down to the section that has the commands:
 
 
 ```
grub> set root=(hd0,1)
grub> linux /boot/vmlinuz-3.13.0-29-generic root=/dev/sda1
grub> initrd /boot/initrd.img-3.13.0-29-generic
grub> boot
```

 It is imperative that when you set the root on the first command that you set it where you Linux partition is. The same applies to the second line at root=/dev/sda1. So you may have your Linux partition on (hd0,8). In that case you’d type:
 
 
 ```
grub> set root=(hd0,8)
grub> linux /boot/vmlinuz-3.13.0-29-generic root=/dev/sda8
grub> initrd /boot/initrd.img-3.13.0-29-generic
grub> boot

```


Now like Carla Schroder says in her article, this is a temporary fix. It’ll allow you to boot into your Linux box…but you’ll have to type that in ever single time after you shutdown.

---

