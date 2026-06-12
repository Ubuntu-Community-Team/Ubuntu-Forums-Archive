---
title: "Macbook Pro 2,1 - Ubuntu 12.04 - External Optical CD/DVD Drive Install Issues"
date: 2014-03-05
forum: Installation &amp; Upgrades
---

### Post by canvasfly on 2014-03-05
Hello

I have a 2006 MacBook Pro 2,1 that I upgraded to have 2 internal hard drives, removing the optical.
I have the rEFInd boot manager installed.
I previously installed Ubuntu successfully, dual booting with OS X, using a Mac specific ISO from Ubuntu's cdimage repository.
Now I would like to attempt a dual boot install again. This MacBook Pro has issues booting other OSes from USB, that's a known issue. I've tried creating a Live USB stick, but can't get it boot from that. So my only option is an Optical drive install.
I tried the previous install media I created and was receiving "*Error Reading Sector XXXX" *messages. I downloaded the ISO again and created a new DVD and now, when I boot from that DVD I get a message stating that[I] "install/vmlinuz cannot be found."
[/I]I've done some research on this error and it seems to be a problem that people run into when trying to install from USB Sticks, not from ISO's.
Then I started wondering if this had anything to do with trying to Boot from an external drive. Even though the Mac is allowing it (though it takes a few reboots before the install DVD shows up in the boot menu), maybe there's an issue with the Mac's EFI vs the custom ISO build for Macs.

I've done a lot of searching but I'm stuck and I'm wondering if anyone has suggestions. The answer could just be that its not going to work. If that's the case, I'll install using VirtualBox.

Thank you for any suggestions.

---

### Post by phidia on 2014-03-05
Rather than reinvent the wheel I'm going to direct you to [this sticky]("http://ubuntuforums.org/showthread.php?t=1046568") in the Apple section of the forums.

Just a note-I use a Macbook Pro (not your model) and I'm surprised that you can get it to boot from an external but I learn something every minute-maybe. I also think; A) You need to deal with EFI (which most modern PC's have now too) and B) perhaps a network install could work for you?

---

### Post by canvasfly on 2014-03-06
Thank you for the link. I need to try building a usb stick with EFI. Some of the resources in that sticky are gone, so the long search continues.
I did find that I was able to get a Mint install DVD to boot by using the 32bit version which might be a good option on my older MacBook pro.
I also realized that I burned the mac specific Ubuntu ISO to a DVD instead of a CD. How I was able to install it before, I don't know.

---

### Post by canvasfly on 2014-03-07
So I figured out what I need to do to get the configuration I want. There are two things I want to do with this MacBook Pro 2,1:
1)Dual Boot Mac OS X and Ubuntu 12.04
2)Increase the internal storage by replacing the optical drive with hard drive.

First, I had to install Ubuntu while the optical drive was installed internally. Trying to do a fresh install from an external optical drive would lead to errors like those I mention in my original post and lastly,[I] (initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed.
[/I]With the drive installed internally, I was able to run the install using the Mac specific ISO available @ [http://cdimages.ubuntu.com/releases/12.04.4/release/](http://cdimages.ubuntu.com/releases/12.04.4/release/).
Then I was able to reinstall my second hard drive. Out of curiosity, I then tried to boot from the install CD with an external DVD drive, wondering if the existence of grub on my drive would make a difference, and it did.
After the initial install, I was able to boot from the install CD using an external drive and rerun the installation process. I decide to resize my Ubuntu partition to make it larger and then reinstall and worked without issue.
The missing piece, to boot for an external optical drive was grub.

---

