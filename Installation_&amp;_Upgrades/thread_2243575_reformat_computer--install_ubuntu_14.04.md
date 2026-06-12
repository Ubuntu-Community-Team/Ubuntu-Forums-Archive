---
title: "reformat computer--install ubuntu 14.04"
date: 2014-09-09
forum: Installation &amp; Upgrades
---

### Post by pedal2 on 2014-09-09
Hi, I've been having lots of issues with 12.10 kubuntu with an i686 32bit system since I got this computer 2 years ago and have decided to just back-up important things, wipe the hard drive and start fresh with 14.04.  I have downloaded the .iso of 14.04 and saved it to a thumb drive and have tried rebooting the system from the thumb drive as was suggested in other threads.  The system isn't booting automatically from the drive, so I hit f12, but I still can't get it to boot from the thumb drive.  Also, usb creator (nor anything else whatsoever for that matter) won't download from software center, not that I know where that will get me in this process.  Can I just erase the whole drive and then reboot the computer with the .iso on the thumb drive some how?  I don't know if it matters, but there are a few other files on the thumb drive as well as the .iso.  I have searched through many threads and can't find any answers or solutions to any problems I'm having.  Your help would be much appreciated!  Thanks ubuntu community!

---

### Post by sammiev on 2014-09-09
I would try to erase your thumb drive with gparted and try a fresh install of the ISO. 
Did you check the md5sum of the download to confirm your download was good?

---

### Post by pedal2 on 2014-09-09
I can't install anything to my computer.  I get the same message every time--"requires installation of untrusted packages".  If I click "ok" it just doesn't do anything at all.  If I click "repair" (the other option) it appears to start, downloading an "updating cache--querying software sources" thing and the gparted (or any file I try to install) thing says "waiting", but then it fails with a "Failed to download repository information" notice.  It says check internet connection--but I'm clearly connected to the internet and haven't had any problems with that.  I don't know how to check the md5sum of the download, but I downloaded the proper 32-bit version from the official ubuntu website.

---

### Post by pedal2 on 2014-09-09
also, if need be I can just erase the other files and just leave the .iso on the thumb drive.

---

### Post by yancek on 2014-09-09
> Hi, I've been having lots of issues with 12.10 kubuntu 

There's part of your problem.  Support for 12.10 ended in May, 2014 and you can't download software with the usual apt-get and Software Center methods but have to try to find them in archives.

>   I have downloaded the .iso of 14.04 and saved it to a thumb drive and  have tried rebooting the system from the thumb drive as was suggested in  other threads

Downloading the iso to a thumb drive isn't going to make it bootable.  You would have to create a loopback entry for it in your grub.cfg file.  It would be a lot easier to download unetbootin from its site and use it to create a bootable thumb drive.  If you have other directories/files on the thumb drive you need to move them elsewhere if you want to keep them as unetbootin will overwrite everything on the drive.

---

### Post by sammiev on 2014-09-09
unetbootin is what I use as well to flash my ISO to my USB sticks. 
Always try any new ISO first from a USB to confirm it's compatible with your computer first and make sure the md5sum matches.

---

### Post by kansasnoob on 2014-09-09
> **yancek said:**
> There's part of your problem.  Support for 12.10 ended in May, 2014 and you can't download software with the usual apt-get and Software Center methods but have to try to find them in archives.



Downloading the iso to a thumb drive isn't going to make it bootable.  You would have to create a loopback entry for it in your grub.cfg file.  **[COLOR="#FF0000"]It would be a lot easier to download unetbootin from its site and use it to create a bootable thumb drive.  If you have other directories/files on the thumb drive you need to move them elsewhere if you want to keep them as unetbootin will overwrite everything on the drive.[/COLOR]**

+1 to all of that, especially using UNetbootin. It's installable using wget which should work OK even with an EOL distro:

[http://www.pendrivelinux.com/using-unetbootin-to-create-a-linux-usb-from-linux/](http://www.pendrivelinux.com/using-unetbootin-to-create-a-linux-usb-from-linux/)

Rather than typing the commands as suggested there I'll place them in code tags here so you can just copy-n-paste:

```
wget unetbootin.sourceforge.net/unetbootin-linux-latest
```

```
chmod +x ./unetbootin-linux-*
```

```
sudo apt-get install p7zip-full
```

Now, rather than launch it by using the command "sudo ./unetbootin-linux-*" which will launch it as a child process of the terminal, I believe you'll find it in Home. If so you can just right-click and select Open. Then you'll have to enter your password.

But let's **[COLOR="#FF0000"]stop and take a breath![/COLOR]**

UNetbootin will let you either Download the desired distro directly for installation on the flash drive:

[ATTACH=CONFIG]256311[/ATTACH]

Or you can select Diskimage and navigate to the previously downloaded .iso (in this case it's in Comp/home/lance/Downloads):

[ATTACH=CONFIG]256312[/ATTACH]

[ATTACH=CONFIG]256313[/ATTACH]

But **[COLOR="#FF0000"]if you're going to use the previously downloaded .iso you must first check the md5sum[/COLOR]**. In my case the .iso is in Downloads so I open a terminal and run:

```
cd Downloads
```

Then:

```
ls
```

And I see this:

```
lance@lance-desktop:~$ cd Downloads
lance@lance-desktop:~/Downloads$ ls
ubuntu-14.04.1-desktop-i386.iso
lance@lance-desktop:~/Downloads$ 

```

So I can just type md5sum (space) and copy-n-paste the .iso name, then in a minute or so it shows the md5sum:

```
lance@lance-desktop:~$ cd Downloads
lance@lance-desktop:~/Downloads$ ls
ubuntu-14.04.1-desktop-i386.iso
lance@lance-desktop:~/Downloads$ **[COLOR="#FF0000"]md5sum ubuntu-14.04.1-desktop-i386.iso[/COLOR]**
a4fc15313ef2a516bfbf83ce44281535  ubuntu-14.04.1-desktop-i386.iso

```

Then I can just copy that md5sum to a text editor, look up the appropriate md5sum here:

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

And compare:

[ATTACH=CONFIG]256314[/ATTACH]

**[COLOR="#FF0000"]You should assume that all files on the flash drive will be lost![/COLOR]**

Clear as mud?

If something is not clear please ask for clarification.

---

### Post by pedal2 on 2014-09-10
Thanks for the info.  I did all the stuff with the unetbootin and checked md5sum.  All good, and files saved to thumb drive from unetbootin properly.  However, I still can't get the computer to boot from the thumb drive.  I'm given options for 4 different USB things in the bios setup screen for boot order, and I've tried starting the computer in all 4 usb ports but nothing changes and computer boots from hard drive (the last option in the boot order) just like normal.  I have no idea what to do now.  

EDIT: I have tried booting from the thumb drive on another computer with the same version of ubuntu (12.10) and can't get it to boot either.  The 2nd computer gives me an option when I enter bios to boot from usb drive but it still doesn't boot from the thumb drive.  I tried restarting with the thumb drive in each usb port just as I did on the 1st computer.

---

### Post by yancek on 2014-09-10
With all the options to boot from usb tried including every port, the only logical conclusion is that the installation to the flash drive using unetbootin failed.  Review the instructions above and at the unetbootin site and try again.

---

### Post by sammiev on 2014-09-10
> **yancek said:**
> With all the options to boot from usb tried including every port, the only logical conclusion is that the installation to the flash drive using unetbootin failed.  Review the instructions above and at the unetbootin site and try again.

+1 and if you have another USB stick, you can try that as well.

---

### Post by vibhanshu2 on 2014-09-11
I would recommend you to boot to boot your thumb drive using PowerISO software and please download a fresh iso file of ubuntu from official website of ubuntu.

---

### Post by Bucky Ball on 2014-09-11
> **vibhanshu2 said:**
> I would recommend you to boot to boot your thumb drive using PowerISO software and please download a fresh iso file of ubuntu from official website of ubuntu.

Disregard. OP is attempting to install Ubuntu, not mount the image in Windows. 

Have you tried hitting F12 at boot to select the boot device? I have the same issue with USB on some computers (I install Ubuntu about once a month) where it won't boot from USB when set in the BIOS, but will when I hit F12 and select from boot devices there. Should only give you the option of the USB that is plugged in. That will also help confirm, if it doesn't work, that the ISO is dodgy (but the md5sum is fine so doubt it), the USB is dodgy or UNetbootin has done something dodgy.

Also, NOTE WELL: Format the USB stick using Gparted prior to burning the image with UNetbootin so there is absolutely nothing on it. If there are files on it, it sometimes causes problems. Just to be certain ...

---

