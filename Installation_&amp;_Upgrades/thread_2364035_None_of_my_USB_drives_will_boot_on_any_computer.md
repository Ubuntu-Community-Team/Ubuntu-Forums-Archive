---
title: "None of my USB drives will boot on any computer"
date: 2017-06-17
forum: Installation &amp; Upgrades
---

### Post by mimuwhen on 2017-06-17
Hello everyone,

I've made several successful ubuntu and other linux installations over the years.  Many of them with the same flashdrive i'm using now, it's a 32GB Kingston usb flash drive.  For some reason however I am now unable to make any successful Ubuntu bootable USB drives.  I also tried making bootable drives using other distros such as lubuntu and puppy linux with no success.  They all simply get ignored when I try to boot from them.  I've tried on different computers with the same results.  I even tried using Plop Boot Manager to try and force one of the computers to boot from the drive but after it detects the drive nothing else happens.  

I'm currently stuck in a remote area so I don't have access to any other USB rives to try and see if maybe the drive is the problem.  However I don't think the drive itself is the issue.  I think I'm doing something wrong.  I've tried making the bootable drives using unetbootin and universal USB installer with the same results.  Before this the drive had been used to make a windows 7 install drive which worked fine.  Perhaps there is some kind of formatting issue?  Just to add, it's not a bios setting issue as some of the computers that I always test USB drives on aren't booting from this either.

Your help would be greatly appreciated!

I tried searching this issue in order to try and not make a repeat thread but most of the issues people seem to have involve a single computer not wanting to boot from a working flash drive.

Thank you!

---

### Post by RobGoss on 2017-06-17
Hello and welcome to the forums, It is my opinion if you tried a number of Linux ISO files and are not able to boot the USB stick may be corrupted

If you can use another machine and it will boot then it might be something you're doing incorrectly. This is really odd because I can understand if one version of Ubuntu won't boot but when you stated you've tried many that make we wonder

By any chance do you have a DVD that you can try installing Ubuntu on to your machine and see if that works

---

### Post by mimuwhen on 2017-06-17
Unfortunately no DVDs or anything.  This is very strange.  I tried re-partitioning the drive and everything and still no go.  I even tried making the bootable drive using another computer with the same results.  When I plug in the drive after creating a bootable image I can open up the folder and see all the files inside but still gets completely ignored when booting.  Something weird I noticed is that when I mount the drive on windows it shows up as F where it should show up as E.  Sometimes I even get a listing for a drive called E but when I click on it, windows asks me to insert a disk.

I wonder if this had something to do with me having used it to create a windows bootable drive?

EDIT:  NVM I just realized drive E is my card reader.  Oh well the mystery continues!

---

### Post by ubfan1 on 2017-06-17
Did you hashcheck the downloaded ISO?
  See [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
  Check the number against the listing in the link for your release listed at
  [http://releases.ubuntu.com](http://releases.ubuntu.com) under the MD5SUMS link.
  For other releases' hashes, like lubuntu, see:
  [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by mimuwhen on 2017-06-17
The thing is I've already used those same iso files successfully on other occasions so it can't be the files.  Something else is afoot. Driving me nuts.

---

### Post by RobGoss on 2017-06-18
> **mimuwhen said:**
> Unfortunately no DVDs or anything.  This is very strange.  I tried re-partitioning the drive and everything and still no go.  I even tried making the bootable drive using another computer with the same results.  When I plug in the drive after creating a bootable image I can open up the folder and see all the files inside but still gets completely ignored when booting.  Something weird I noticed is that when I mount the drive on windows it shows up as F where it should show up as E.  Sometimes I even get a listing for a drive called E but when I click on it, windows asks me to insert a disk.

I wonder if this had something to do with me having used it to create a windows bootable drive?

EDIT:  NVM I just realized drive E is my card reader.  Oh well the mystery continues!

Please see here for the naming of drives using Linux [https://askubuntu.com/questions/56929/what-is-the-linux-drive-naming-scheme](https://askubuntu.com/questions/56929/what-is-the-linux-drive-naming-scheme) it's a lot different from Windows

---

### Post by RobGoss on 2017-06-18
> **mimuwhen said:**
> The thing is I've already used those same iso files successfully on other occasions so it can't be the files.  Something else is afoot. Driving me nuts.

If I were you I would download the latest **LTS** version of Ubuntu and create another bootable USB using Pendrive [https://www.pendrivelinux.com/](https://www.pendrivelinux.com/) give it a go and see how that works. If you're trying to install Ubuntu with that **USB** stick and are unsuccessful you may need a new ISO file, just saying

---

### Post by mimuwhen on 2017-06-18
I managed to make a bootable drive finally!  What made it work was using start up disk creator instead of the other programs I was using.  I still managed to use the same iso files which are up to date.  Don't know why it wouldnt work with the other programs.  Im curious to try and use the other programs again to see if perhaps somehow something managed to "unlodge" itself.  Weird things like this always seem to happen when working on computers.  

The problem now is that the computer I wanted to load Ubuntu or Lubuntu onto will not boot from the USB still.  In fact when I go into the bios to change the boot order it doesn't show me the USB option unless the USB stick is plugged into the port.  This computer still ignores the USB yet it works on other computers.  I will try making a bootable drive using another distro to see what happens.  The computer has an MS-6712 Ver 1.1 mother board.

EDIT: I went ahead and used unetbootin to make a lucid distro bootable drive and it worked.  Seems the drive is back in the mood for making bootable drives.  Very strange.  Still however the computer I planned to load linux onto is refusing to boot from USB.  Any settings I should look out for?  I again tried to use Plop boot manager to manually try and boot the computer from the USB but even though it seems to detect the drive, it will not boot.  Just stays stuck.

---

### Post by RobGoss on 2017-06-18
You may also want to try another USB port just in case the one you've been using is bad, after you plug in the USB drive are you hitting F-12 in order to boot from the USB?

---

### Post by Autodave on 2017-06-18
Just a thought here: is he having UEFI problems? I had a machine once that would not boot from a USB stick. I had to change something in the UEFI, however I do not remember what it was :-(

---

### Post by mimuwhen on 2017-06-19
I just ended up caving in and getting the DVD.  Im back to civilization now so I don't have to work with just my USB thumb drive.  Unfortunately now I have other issues with the installation process as grub does not seem to wanna install.  I think I should start a seperate thread for this particular issue.  Thanks a lot for your help, much appreciated! Cheers.

---

