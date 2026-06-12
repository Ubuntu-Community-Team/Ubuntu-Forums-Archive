---
title: "Can't install 8.04 with Alternate CD in Safe Graphics Mode"
date: 2008-05-17
forum: Installation &amp; Upgrades
---

### Post by fromgi on 2008-05-17
I liked the idea of the data encryption available when using the Alternate CD; however, there is no provision to install using the Safe Graphics Mode.  After installation I could not read the screen.  I was forced to reinstall using the Live CD.

Does anyone know how to install 8.04 using the Alternate CD in the safe graphics mode?

[Here is the link]("http://news.softpedia.com/news/Encrypted-Ubuntu-8-04-85271.shtml") which convinced me to use the Alternate CD method versus the Live CD.

Thank you.

---

### Post by zvacet on 2008-05-17
I hope [this]("http://users.bigpond.net.au/hermanzone/") will help you.

---

### Post by fromgi on 2008-05-17
Thank you for your response.  Could not find anything relating to the safe graphics issue.  It doesn't make much sense to me; if one of the reasons this CD was created was to help those with low resources, then I think they made a big mistake.

---

### Post by zvacet on 2008-05-17
@ **fromgi**


> if one of the reasons this CD was created was to help those with low resources, then I think they made a big mistake.

It is one reason,but not the only one.Read [this]("http://hr.releases.ubuntu.com/hardy/") and you will see other options with alternate CD.Try to press F1 or F4 ans see if you can get any help from there.Sorry,I was not much help to you.

---

### Post by Herman on 2008-05-17
What did you mean by 'install in safe graphics mode'? 
I guess you mean the installation itself goes alright, (you can see what you're doing while you are performing the installation),  but *after the installation is complete* you didn't get a working Xserver. Is that what you mean?

Please describe what you did see.
Did it boot to the black screen with the orange progress bar as Ubuntu is booting up? (usplash).

Or did you just get a black screen with some white text scrolling on it for a while?
Did that stop at a login prompt?

Or, did you get as far as the Ubuntu login screen, (where you type in your username and password)?

Did you log in only to find a tan or brown screen with a mouse pointer in the middle of it and nothing else?

What are your system specs?
If your computer can run the Ubuntu 'Desktop' Live CD then you must not have 'low resources'. 
The 'Desktop' CD will install in computers with at least 256 MB of RAM, but you might need to pre-partition with GParted LiveCD first in order to make a Linux swap area which the 'Desktop' CD can use in the absence of sufficient RAM.
The Ubuntu 'Alternate' CD can be used to perform an installation in a computer with as little as 32 MB of RAM.

Video problems are a different issue, but as far as I  understand, the 'Alternate' CD installs exactly the same operating system as the 'Desktop' CD, if you're just installing a plain ordinary system, so the video drivers should be the same. :)

---

### Post by fromgi on 2008-05-17
**What did you mean by 'install in safe graphics mode'? **
When using the Live CD, I pressed F4 and selected the "Safe Graphics" mode before installing 8.04.  The Alternate CD does not have this option.

**Please describe what you did see.**
When the Alternate CD installation completes and when I reboot, I get the black screen with the orange progress bar; however, when I get the login screen the image looks like a comic book.  After I enter my username/passwork, the comic book image is displayed once again in Ubuntu.  Everything is very hard to read.

I have a Gateway 1.7 GHz P4 with 2 GB ram and a 32MB Radeon Video card.

Thanks you for responding!

---

### Post by Herman on 2008-05-17
> when I get the login screen the image looks like a comic book. After I enter my username/passwork, the comic book image is displayed once again in Ubuntu. Everything is very hard to read.Oh, okay, so your Xserver seems to be not setting itself up correctly for your hardware then, by the sounds of things. 

I wonder why the 'Desktop' CD's Xserver for Hardy would be any different from the Xserver you'd get for Hardy with the 'Alternate' CD? Like I said before, they should be the same. 

I tried out Hardy Heron's new  [X window system]("http://www.x.org/"), Xorg 7.3 in all the computers I have by installing Hard Heron in a USB flash memory stick and booting it up in different computers to see if it would be able to automatically configure itself for each different computer at boot time. It worked in all my computers, I was very impressed indeed! I have one computer with an ATI Radeon 9200 graphics card, which Hardy works great in.
I was just using a plain ordinary installation from the Desktop CD though.

I just bought a brand new 8.0 GB [SanDisk Cruzer Micro USB2 flash drive]("http://www.sandisk.com/Products/Catalog%281168%29-SanDisk_Cruzer_Micro_USB_Flash_Drive.aspx"), I'll try the encrypted LVM installation from the 'Alternate' CD myself and see what happens.

If you like encryption, 'seahorse' comes standard in Hardy Heron now, so all you have to do is this, ( [seahorse how-to)]("http://users.bigpond.net.au/hermanzone/p5.htm#Install_Seahorse"), and you'll have the option for encrypting and decrypting files on your right-click menu from your mouse.
That doesn't give you an entire encrypted file system though, but at least you can encrypt a few files whenever you want to. 

If you still want an encrypted file system, (and now that you have brought it to my attention, it would be great, especially for USB drives), and you re-install with the alternate CD, you might just be lucky and things will turn out better next time. Sometimes an install can be a little defective for some reason, a tiny speck of dust floating past the optical lense or something, causing a bad read is all it takes.
If the Xserver fial again,  I don't know how you would go about fixing it, but I can give you this link, which might be helpful, [How do i manually configure xorg.conf]("http://ubuntuforums.org/showthread.php?t=788765") ?

I'll let you know how my new encrypted Hardy USB flash stick turns out in a little while...

---

### Post by Herman on 2008-05-18
:rolleyes: After the installation took almost three hours, it took ages at the usplash trying to boot, before dropping to an initrams busybox shell.
I tried several times.

Booting my hard disk installed Hardy Heron and looking at it with Gnome Partition Editor, the file system appeared to be corrupt, ( I'm not sure if that's normal for an encrypted file system or not), e2fsck could not fix it, nor did trying to replace the superblock with a backup copy of the superblock. It has a small ext3 /boot partition that seems to be okay, but I don't see any swap area there anywhere, that it said it would make.
I tried to fix the file system and boot a few more times.

I have deleted the partitions and set a new disk label (MBR) as well, just to make sure, and I'm starting all over again, if it takes as long as last time I won't have any more news on this subject for another three hours at least.

EDIT: I tried again for the encryped LMV installation in the USB flash memory stick but still with the same result.
As a test to see if the memory stick will work for installing an operating in at all, I tried plain ordinary installation in it, and that worked fine, although this particular memory stick seems to be particularly slow to write to. Even the regular installation (without the encrypted file system) still took about three hours. 
Installing Ubuntu in two other USB flash drives using the same computer only took an hour and five minutes in a 4.0 GB Toshiba flash memory stick last weekend. 
I expect to need to do this, [Hardy Beta Fine, Now Blank Screen (with working pointer) after Login]("http://ubuntuforums.org/showthread.php?t=793081") each time I install in a USB flash memory stick now. That's quite alright. I'm used to it now.
I will try the encrypted file system with LVM installation again in a real hard disk and see if that works okay or not. I expect that it will.

---

### Post by fromgi on 2008-05-18
Thank you for ALL your efforts!

After installation of the Alternate CD, I tried to configure Xorg manually, but could not read the screens.  I then re-ran the Live CD.

After the Live CD finished installation, I copied both the grubs menu.lst and xorg.conf onto a floppy and re-ran the Alternate CD's installation.   After the installation, I then replaced these two files with the one's on the floppy and then re-booted.  Still have the problem.

What I did notice is the menu.lst from the Live CD has xforcevesa as a parameter, and the xorg.conf has Driver	"vesa" under the heading "Configured Video Device" where the xorg.conf from the Alternate CD has nothing.  I would gather that by simply copying these files does not configure anything at boot (not an expert, just suspect this might be true).

I still can't understand why Ubuntu would not add the "Safe Graphics" to the F4 key for both installations and just be consistent.

I hope this helps!

Thanks again!

---

### Post by cdtech on 2008-05-18
I had to go into safemode and reinstall the nvidia driver with:
sudo apt-get install nvidia-glx-new

My video:
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)

my xorg.conf file video:
Section "Device"
        Identifier      "nVidia Corporation NVIDIA Default Card"
        Driver          "nvidia"
        BusID           "PCI:0:18:0"

but that was me and my nvidia.

---

### Post by fromgi on 2008-05-18
Found the official document page for the Alternate CD installation.  Wouldn't you know, all links are bad.  Unfortunately I feel the documentation has gotten worse since 7.04 and continues down that path.  Anyway here is the [link]("https://help.ubuntu.com/8.04/") to the page.  Go to the bottom of the page under "Installing Ubuntu via the alternate CD - choose your architecture".

---

### Post by Herman on 2008-05-18
Try this link instead, Community Docs: [Installation]("https://help.ubuntu.com/community/Installation")

---

### Post by Herman on 2008-05-18
Success! It took an hour and six mins in a hard disk, to install Ubuntu from the 'Alternate' CD with an encrypted file system with LVM.
The video display is perfect in the computer I'm using here.

---

### Post by fromgi on 2008-05-18
Glad you got yours loaded!  Now I feel like getting loaded!!

I tried your link, and then used the link "Installation/I386".  I read the page and seen the section "You may need to set advanced boot options by pressing F6".  I don't know what these advanced option are, so I did a search on that page for "advanced boot options", and guess what, no hits.

This is certainly discouraging.

---

