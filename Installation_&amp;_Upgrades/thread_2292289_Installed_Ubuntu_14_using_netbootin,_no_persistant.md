---
title: "Installed Ubuntu 14 using netbootin, no persistant install now."
date: 2015-08-26
forum: Installation &amp; Upgrades
---

### Post by leotemp on 2015-08-26
I dont have a usb drive or DVD player so i followed the instructions to install Ubuntu without a usb drive found on the top voted answer here:

**Install Ubuntu without CD and USB , how?**
[http://askubuntu.com/questions/484434/install-ubuntu-without-cd-and-usb-how](http://askubuntu.com/questions/484434/install-ubuntu-without-cd-and-usb-how)

The top voted answer; "To install Ubuntu without CD/DVD or USB pendrive, follow these steps:" is what I followed.

After completing the install as instructed I then Clicked the "Install Unbuntu 14 LTS" option on the dekstop and completed the install as normal. I thought everything went fine and installed some apps, a web server and cloned some repos. I needed to reboot and when I did the unetbootin was still the boot option which i thought was weird but I booted up and everything is gone. Settings, folders, files. I'ts a completely fresh install just like a live usb would do but I installed Ubuntu..

Does anyone have an idea of what is going on here?

---

### Post by grahammechanical on 2015-08-26
What do you mean "everything is gone?" All the extra stuff that you installed gone? Or Ubuntu gone as if it was not installed?

Remember, you were running a Ubuntu live session. So, you were running it not from a DVD disc or USB stick but from a hard disk. It was still a live session running in RAM. Close the live session and restart and we get the installed Ubuntu without anything we may have installed during the live session.

---

### Post by yancek on 2015-08-27
The link you posted explains how to boot the Ubuntu installation medium from a hard drive, apparently from a windows system.  It stops there and gives you no instructions on which options to select during the install so we have no idea what you did there.  

> completed the install as normal. I thought everything went fine and  installed some apps, a web server and cloned some repos. I needed to  reboot and when I did the unetbootin was still the boot option which i  thought was weird but I booted up and everything is gone

As indicated above, that is because you are still using the install medium which is read-only.  Everything is lost on reboot.  On re-boot, you should see a new option for Ubuntu if this method works and was done properly but not if you select the unetbootin boot option.

So, do you have an Ubuntu boot option?
What can you boot now?
In order to use the method described in the link you posted, you would need to have some operating system installed but you do not indicate what you have?  You might try taking a look at the tutorial below which has an explanation of what you would see during an install of Ubuntu 14.04 as well as other details that are very useful.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by leotemp on 2015-08-27
> As indicated above, that is because you are still using the install medium which is read-only. Everything is lost on reboot. On re-boot, you should see a new option for Ubuntu if this method works and was done properly but not if you select the unetbootin boot option.

No I do not have an Ubuntu boot option. I ran netbootin from Windows as indicated in the url i pasted in my question. I selected my hard disk and ran the install, upon booting the first time I had a "netbootin" boot option. I selected that, boot to ubuntu and ran the "Intstall Ubuntu 14 LTS" link on the desktop, completed it successfully and rebooted. This is when I was presented with the option to either boot Windows or netbootin but not an Ubuntu option. I made a poor choice of assuming I would have to rename the boot option in grub later and chose to ignore it (my bad). However I don't understand what's happening here. Does running the Ubuntu install from a live session not install Ubuntu? I tried once more this morning with the same results and from a user perspective this behavior is baffling to me, what else would "Install Ubuntu 14 LTS" mean other than installing Ubuntu 14 LTS? I can only assume that there's something wrong with what I am doing otherwise this is wacky and needs at least a better caption for the install icon. 

I just drove to the store and bought another USB drive for my roommates to lose so for today I will install via the trusty USB method but I would really like to know wtf is going on with this particular issue so I can do it correctly at some point in the future. ]

Thanks for the replies!

---

### Post by leotemp on 2015-08-27
Figure I would just add to this thread and mention that after using the pendrive tool to make a bootable USB drive, booting from it, selecting Install Ubuntu and then from the Ubuntu install selecting "Delete Ubuntu and reinstall" from the install menu I am still presented with unetbootin as the boot option and Ubuntu is still read only..

I guess i will manually remove netbootin partition but this all seems completely daft.

---

### Post by leotemp on 2015-08-27
So now, after uninstalling unetbootin, the boot option is gone but the install still exists according to the Ubuntu install which i am using from a bootable USB. The problem now is that I can't select any install option whatsoever. "Erase Ubuntu 14.03 LTS and reinstall", "Erase Disk and install Ubuntu" and "Something else" cannot be used because when I select any of these options the "Install Now" button is greyed out and unavailable for clicking. I've installed Ubuntu probably 100 plus times and have never seen anything like this happen before. I really really hate unetbootin right now and I regret not just going to the store and buying a usb drive to avoid all of this. I honestly have no idea what to do now other than run some windows based partition tool and try to excise Ubuntu from the machine.


EDIT:

So... i clicked back and continue a whole bunch of times and that fixed it.. this is really JANK and has shaken my faith in this distro considerably.  I still don't know if this install will work but random behavior from the install app is hardly reassuring especially after all the other problems I have dealt with in the last couple days. A google search revealed a ton of people with the same issue. What's going on with this distro? I feel like going back to crunchbang right now regardless of what work thinks.

---

### Post by sudodus on 2015-08-27
You are frustrated because things did not work out well. I can understand that, but you tried an unconventional method and there was probably some strange thing written to the internal drive. From a running live session of Ubuntu even in a pendrive made bootable with Unetbootin, you should be able to run ***gparted*** and get the internal drive clean.

Is there a Windows system in the computer, so you must be careful and not overwrite it? That will decide my next step advice (if gparted does not help).

---

### Post by yancek on 2015-08-27
> Does running the Ubuntu install from a live session not install Ubuntu?

Of course it does.  You indicate that you have previously done it yourself a number of times in a later post.  I've never done this with unetbootin but booting an Ubuntu iso file from a hard drive and installing it to another or the same hard drive can also be done.  That's the only way I have installed for several years.  The method I use is with a Grub2 bootloader rather than unetbootin but since all you seem to have on your computer is some version of windows, you obviously can't use Grub.

Which version of windows are you using as this can make a big difference, particularly if you have 8 or later and are using UEFI.  Can we safely assume you want to keep whichever version of windows you now have?  Posting more details on exactly what is going on and your drive/partition and boot files would help.  The simplest way to do that is to boot the flash drive you now have the Ubuntu on.  The go to the site below and download boot repair and run it.  Do NOT try any repairs but simply select the option 'Create Bootinfo Summary'.  this should output a text file and you can post that info here and someone should be able to make a suggestion.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by C.S.Cameron on 2015-08-27
I have not tried 14.04 yet,.
With previous versions:

At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table".
Click Continue on the drop down.
Set up your disk to suit.
Confirm "Device for boot loader installation" points to the root of the hard drive. (Default should be ok).
Click "Install Now".
This should give you the option of booting either Windows or Ubuntu or Live HD using grub2.
If you delete the Live HD install, run update-grub.
As noted above, things can get more complicated with a modern UEFI computer, but are still solvable.

---

### Post by C.S.Cameron on 2015-08-27
The previous post was for adding a Full install to the hard disk.
If you just want to make your Live HD install Persistent.
Open filesystem / cdrom and then open syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Obtain a casper-rw file and put it in the root HD directory or make a partition named casper-rw if you need more than 4GB persistence.

---

