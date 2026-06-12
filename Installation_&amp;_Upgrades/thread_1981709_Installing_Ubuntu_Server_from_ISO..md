---
title: "Installing Ubuntu Server from ISO."
date: 2012-05-17
forum: Installation &amp; Upgrades
---

### Post by tciszar on 2012-05-17
I am trying to set up a file/media server for my home network. I have a self built "Franken-Computer". I made a Live CD of Puppy Linux to make sure the old thing would work before I tried putting a bigger OS on it. 

So, I put the Puppy Linux CD in and it runs fine. Using Puppy I got online and downloaded the 32 bit ISO of Ubuntu Server 12.04. I tried burning the image onto a CD using the Puppy Linux built in ISO burner software. 

The CD said it was successful, so I rebooted the PC and tried to boot to the Ubuntu Server CD. The message "Missing Operating System" appeared, just like before I had booted from Puppy Linux. 

So here's my question, is their any way to install the Ubuntu Server ISO while running Puppy Linux? Or do I HAVE to make a Live CD? Also, I want to avoid using Wubi.

Thank you, I look forward to your replies.

Tyler Ciszar

---

### Post by zvacet on 2012-05-17
You can install it from usb using [Multisystem.]("http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/")Of course before putting iso to usb check [md5sum.]("https://help.ubuntu.com/community/HowToMD5SUM")

---

### Post by darkod on 2012-05-17
That sounds like it's trying to boot the hdd before the cd. Or the cd boot process is not made correctly. Don't forget you need to burn the cd from image, not simply the ISO file onto the cd as a data cd.

Try confirming in the BIOS that cd-rom is before hdd in boot devices.

You can also see if the board has a key to enter a boot menu during POST, like F12 or similar. That can bring up boot menu where you can select to boot from cd-rom.

---

