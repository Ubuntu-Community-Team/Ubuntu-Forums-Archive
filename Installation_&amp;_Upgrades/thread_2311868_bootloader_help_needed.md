---
title: "bootloader help needed"
date: 2016-01-30
forum: Installation &amp; Upgrades
---

### Post by tasos-lists on 2016-01-30
I have made my laptop a triple boot system ( win7 - fedora - ubuntu ), and after the installation of thr third O.S. I have performed  an update for the Ubuntu, then made a reboot, and since then the fedora O.S. has been disappeared from the bootloader. 
Is there any command sequence that could help solve this problemm?

---

### Post by oldfred on 2016-01-30
Is Fedora in the LVM as its normally does.
If so you need to mount the Fedora LVM before running grub's update, if using Ubuntu's grub to boot with.

And to be able to mount the LVM.
 sudo apt-get install lvm2

I do not know LVM, but have seen this:

        To activate all known volume groups in the system:
       vgchange -a y

---

### Post by tasos-lists on 2016-01-30
The 1st command gave an output, but the 2nd command gave this output: 
tasos@tasos-SATELLITE-T110:~$ vgchange -a y 
  /dev/mapper/control: open failed: &#902;&#961;&#957;&#951;&#963;&#951; &#960;&#961;&#972;&#963;&#946;&#945;&#963;&#951;&#962;
  Failure to communicate with kernel device-mapper driver.
  WARNING: Running as a non-root user. Functionality may be unavailable.
  No volume groups found
tasos@tasos-SATELLITE-T110:~$

After that, i made a reboot, but nothing changed!

---

### Post by oldfred on 2016-01-30
Forgot the sudo, I often do that and when I see the message know I forgot it.
       [http://xkcd.com/149/](http://xkcd.com/149/)
But even with sudo the above does not work for me. :)

Not sure if you have to run other commands also? 
Again you know LVM more than I do if running Fedora.

sudo vgchange -a y
      
 sudo update-grub

---

### Post by tasos-lists on 2016-01-31
Well both commands worked pretty good for me, thus recovering the missing line of fedora, from the bootloader menu.
I have 2 questions, refering to right installation of my entire system.

1) There is one parttion devoted for Win7, then I prepared thru the live CD  an EXTENDED partition ( using the GParted ) where I have installed both other O.S. (Ubuntu and Fedora), which is in use right now.
Earlier, I had used this Unallocated space to install both O.S. (ubuntu and fedora ) , without using the EXTENDED partition, which also worked O.K.
I am wondeing which would be the best choice from any aspect.

2) After I choose from the bootloader menu to start Fedora, I can see on the screen in a dos-mode style,2-3 scrolling pages with all commands  and services which will take place, before the Fedora will be loaded. The same process is repeated again when shuting down the system! How could I make this , not visible?

regrds Tasos

---

### Post by Dennis N on 2016-01-31
> Earlier, I had used this Unallocated space to install both O.S. (ubuntu and fedora ) , without using the EXTENDED partition, which also worked O.K.
I am wondeing which would be the best choice from any aspect.

Creating an extended partition and then creating logical partitions inside allows more partitions to be created in the unallocated space. If you had used only primary partitions, you can only have 4 total (including the extended one), so you quickly run out if you need more than 4.

> After I choose from the bootloader menu to start Fedora, I can see on the screen in a dos-mode style,2-3 scrolling pages with all commands and services which will take place, before the Fedora will be loaded. The same process is repeated again when shuting down the system! How could I make this , not visible?

Check the Fedora menu entry by selecting it in the grub screen and pressing 'e'. Look at the line starting with 'linux'. When I had Fedora in my grub menu, that line originally looked like this as created by the os prober:

```
linux /boot/vmlinuz-4.2.5-201.fc22.x86_64 root=/dev/sda9
```

There is no 'quiet splash' option. This produced your problem of no splash screen. The two words 'quiet splash' needed to be added at the end of the line. Then I continue the boot with ctrl+x. This is a temporary one-boot solution, however.

Do you see 'quiet splash' in that line?

---

### Post by tasos-lists on 2016-01-31
1) I made a test. I have reinstalled the Fedora. Now during the boot proccess, the grub comes from fedora and there is no scrolling screen with commands and services activation.
On the other hand, when choosing to start Ubuntu there is a message saying: **ACPI Probe PCC Failed**.Then it starts loading Ubuntu normally.

2) About the EXTENDED  partitions. I need no other (forth) partiton. 3 are o.k. for me.
So I would like to know if one EXTENDED partition is  o.k. for Ubuntu and Fedora, or would be wise to have SEPERATE EXTENDED partitions for each O.S. ?

---

### Post by oldfred on 2016-01-31
You can only have one extended partition per hard drive.
       [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

Did you reinstall Fedora with LVM? Some that have multiple installs on a drive, change to use just a / (root) partition. One of the main advantages of LVM is when it is the entire hard drive. But Windows will not work in the LVM. You could install Ubuntu inside the LVM.

      
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by Dennis N on 2016-01-31
You cannot have two extended partitions. Only one is allowed, so what you have is correct.

I'm surprised that Fedora would boot Ubuntu from a menu entry that Fedora generated (see added EDIT comment below). When I tried that last year, it would not work without some modifications to the menu entry. The message you see about ACPI probe can be ignored if it otherwise boots up for you. Some users report that it prevents booting, so consider yourself lucky.

Enjoy your Fedora. I found it too much trouble to set up to my liking, but nevertheless, it is widely used by many.

EDIT: I just realized why your Fedora can boot Ubuntu while my Fedora did not. It's because I used UEFI mode installations and you did not. In UEFI, I found you cannot boot Ubuntu with unmodified Fedora-generated menu entries.

---

### Post by tasos-lists on 2016-01-31
I see. Well, it seems to operate **all three O.S**. correctly then.
Now, what I have noticed from those multiply installations is that the last in order O.S. you install, it is its grub bootloader the system keeps as a bootloader. In my case, now the bootloader comes from fedora side, since my last installation is Fedora. ( not the graphical screen the grub with Ubuntu has.)

I am mostly an Ubuntu user, but my son asked me to load on the laptop as third OS the fedora, for some test purposes. 
I appreciate all your help and comments.


regards

Tasos - CRETE ISL., - HELLAS

---

### Post by yancek on 2016-01-31
> Now, what I have noticed from those multiply installations is that the  last in order O.S. you install, it is its grub bootloader the system  keeps as a bootloader. 

Not necessarily although that is the default for pretty much any Linux.  You should always have an option as to where to install the bootloader, usually the default for the device for bootloader installation you see during the install is "/dev/sda" which would put code for that system in the MBR if you are using MBR rather than UEFI.  You should also have an option to install to the root filesystem partition.  That option is available on any Ubuntu derivative when running the install.  You should see (at least with the Something Else option) device for bootloader installation and a drop down arrow from which you can make a selection.  Installing the bootloader to a partition if you already have another bootloader is much easier during the install than later.

Fedora has been historically notorious for NOT detecting other Linux systems but it is better than it was several years ago.

---

### Post by oldfred on 2016-01-31
You can boot into Ubuntu and install its copy of grub to MBR.

       sudo grub-install /dev/sda

But updates to Fedora's grub may reinstall it to MBR, not sure how it works. 
With Ubuntu you can change settings to prevent reinstall.

---

### Post by Dennis N on 2016-01-31
Windows with Ubuntu & Fedora is a good example of why UEFI is proving superior. Windows, Ubuntu and Fedora mind their own business and keep their grub files in separate folders on the ESP. Not only that, but you get a nice easy backup boot path to the other Linux from the UEFI boot menu. And no reinstalling grub to restore what OS boots first.

---

