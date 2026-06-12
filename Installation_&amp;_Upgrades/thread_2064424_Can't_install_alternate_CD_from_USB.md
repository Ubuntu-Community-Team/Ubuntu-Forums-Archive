---
title: "Can't install alternate CD from USB"
date: 2012-09-29
forum: Installation &amp; Upgrades
---

### Post by mmmattias on 2012-09-29
Hi im trying to install ubuntu 12.04 with full hard disk encryption.
After downloading and installing the Ubuntu live CD, I learned that truecrypt doesnt support full disk encryption on linux. I also learned that the best way to get "nearly full disk encryption" on ubuntu is by installing it from the alternate install CD.
I tried that, but something is wrong with my CD reader/burner so it doesnt boot up when i insert the cd.

My thought here was to take the .iso that I downloaded on my unencrypted Ubuntu system, use Unetbootin to make the usb drive.

The usb drive used for this is exactly the same brand as one that I know has worked with a previous ubuntu live system on the same computer. I also used unetbootin for that usb, but I created it from windows that time.

The usb stick boots up fine and i get through the first couple of steps in the installation process. However, After a while I get a "box" with the following error message

"Load Installer components from CD

There was a problem reading data from the CD-ROM. Please make sure it is in the drive. If retrying does not work, you should check the integrity of your CD-ROM.
Failed to copy file from CD-ROM. Retry? "

Then I cant get any further.

I googled a lot and found this page which seems to tackle this very problem:

[http://www.dotkam.com/2010/11/29/install-alternate-ubuntu-image-from-usb/](http://www.dotkam.com/2010/11/29/install-alternate-ubuntu-image-from-usb/)

I tried to do what it said. After pressing TAB, I wrote

	cdrom-detect/try-usb=true

without quotes because that's what i think is right.

When I press TAB, there already is a text saying

	/ubnkern initrd=/ubninit vga=788 -- quiet

which can be removed. I have tried to both delete the text before the "--" and just inserting cdrom-detect/try-usb=true before it.

Any idea of what can be wrong? I would like to do a full system encryption, or as full as it is possible. I dont want to just encrypt my /home folder. Maybe this isnt the easiest way.

I use SanDisk usb sticks. I know there is a problem with U3 launcher on some SanDisks, but I never had to remove U3 before from similar disks, and the alternate install does boot up, so I dont think using U3 removal would help me.

Any help or indication to an easier way to do this would be appreciated

---

