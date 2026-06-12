---
title: "Ubuntu gives me a BSOD-ish screen on demo?"
date: 2012-08-01
forum: Installation &amp; Upgrades
---

### Post by aaronfranke on 2012-08-01
Hi, I would like to run Ubuntu just from the CD but that doesn't seem to work. I have a HP Computer with Windows 7 currently, I have downloaded and burned Ubuntu on a CD and rebooted. Startup loads the ubuntu GNU GRUB system, but it is different than what it was on my old computer. A black screen with a white HUD gets displayed (I remember it being purple background) and I have 3 options: Demo Ubuntu, Install Ubuntu, and Check the disc for errors. Whichever option I pick, I get a messed up screen; it has black strips on the top and bottom, the bottom strip has white lines in it, and the middle has a few BSOD-ish screens, they are blue, have white writing that can't be made out, and there are a few of them tiled there. What is going on? Did my download fail? Did my burn fail? Does my computer not support ubuntu? Whats wrong?

---

### Post by Ubun2to on 2012-08-01
It sounds like a problem with the disk itself.
Does the screen look something like this?:
[IMG]http://4.bp.blogspot.com/_ybpq5zhL-RU/TAH6xEs8nII/AAAAAAAAAHc/8s-4z1iXJhA/s1600/Windows_1_0_crash.png[/IMG]
It probably shouldn't-that's the Windows 1.0 BSOD. :lolflag:
You should try burning a new disk.

---

### Post by aaronfranke on 2012-08-02
I have a 64-bit computer btw, I have tried both the 32-bit and 64-bit version now on a few CDs with no luck. I am using Cyberlink Power2Go CD burner.

On the 32-bit, I do not get the GNU GRUB screen, just the 'normal' "Circleguy -> Keyboard" startup image.

Pics: [http://imgur.com/a/EZBDT](http://imgur.com/a/EZBDT)

Whats wrong? :(

---

### Post by Kleenux on 2012-08-02
Sounds like you got a new version of Space Invaders ;)

More seriously, did you have a look at your BIOS settings?
Try maybe a Reset to Defaults, have a look at the various options?
Do you have any special / strange PCI cards, USB (...) connected devices? (that you could remove and try again)

---

### Post by aaronfranke on 2012-08-02
> **Kleenux said:**
> Sounds like you got a new version of Space Invaders ;)

More seriously, did you have a look at your BIOS settings?
Try maybe a Reset to Defaults, have a look at the various options?
Do you have any special / strange PCI cards, USB (...) connected devices? (that you could remove and try again)
I am honestly not sure.
My computer model is HP h8-1237c, I can provide more info but I honestly don't know how to do anything with BIOS :(

---

### Post by Ubun2to on 2012-08-02
> **aaronfranke said:**
> I am honestly not sure.
My computer model is HP h8-1237c, I can provide more info but I honestly don't know how to do anything with BIOS :(

Well, lets check for any PCI or USB cards first.
PCI cards are the in the slots on the back of the computer. There are usually 3 or 4 of them, and some may be plugged up since they aren't being used. Are there any? If so, take a picture of it and post it here.
USB ports are on both the front and back of the computer usually. Look for anything plugged into them. Follow the cord. If it isn't leading to a USB mouse or keyboard, list what it is here. If you have no idea what it is, take a picture and post it here. We can then determine what is on your machine that could be inhibiting it.
We should do that before playing around with the BIOS.

---

### Post by aaronfranke on 2012-08-03
> **Ubun2to said:**
> Well, lets check for any PCI or USB cards first.
PCI cards are the in the slots on the back of the computer. There are usually 3 or 4 of them, and some may be plugged up since they aren't being used. Are there any? If so, take a picture of it and post it here.
USB ports are on both the front and back of the computer usually. Look for anything plugged into them. Follow the cord. If it isn't leading to a USB mouse or keyboard, list what it is here. If you have no idea what it is, take a picture and post it here. We can then determine what is on your machine that could be inhibiting it.
We should do that before playing around with the BIOS.
[IMG]http://i.imgur.com/kNzcD.jpg[/IMG]
Are those the PCI cards? One is being used for my monitor plug and the other 3 are unused.
[IMG]http://i.imgur.com/PXmsU.jpg[/IMG]
The only devices plugged into my USB are a keyboard, mouse, and a webcam.

---

### Post by oldfred on 2012-08-03
the "Circleguy -> Keyboard" is the accessibility icon. If you press any key you get a menu. Try f6 and nomodeset if a video issue which is very common. I have had to use nomodeset for all recent versions until I install the nVidia driver. 
But some older and some very new computers may need other boot options.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by gordintoronto on 2012-08-03
Try this:
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

---

### Post by Ubun2to on 2012-08-03
> **aaronfranke said:**
> [IMG]http://i.imgur.com/kNzcD.jpg[/IMG]
Are those the PCI cards? One is being used for my monitor plug and the other 3 are unused.
[IMG]http://i.imgur.com/PXmsU.jpg[/IMG]
The only devices plugged into my USB are a keyboard, mouse, and a webcam.

Yes, the things you are plugging the monitor cables into are PCI cards. It is most likely a problem with the graphics card.
It appears (from the images you posted) that you have no integrated graphics. But, that's what I'm guessing at from the shots you've provided. Take enough pictures so that we can see everything on the back.
Try booting to a live CD.
The webcam shouldn't cause problems.
Also, we need to know the graphics card type.
1. Boot to Windows.
2. Log in.
3. Click on the Start button.
4. Right click on Computer.
5. Select Properties.
6. Go to the Device Manager, which is on the sidebar on the left of the window that just opened.
7. Go to Video Adapter, Video Cards, or whatever it's called. Figure out the manufacturer and model and post it here. If you can't find it, just post a screenshot of where you are stuck (you can take them by pressing CTRL + PRNT SCR, and paste it in Paint, then save the image and upload it online).

---

### Post by aaronfranke on 2012-08-05
> **Ubun2to said:**
> 
1. Boot to Windows.
2. Log in.

I'm not a retard.
> **Ubun2to said:**
> 
3. Click on the Start button.
4. Right click on Computer.
5. Select Properties.
6. Go to the Device Manager, which is on the sidebar on the left of the window that just opened.
7. Go to Video Adapter, Video Cards, or whatever it's called. Figure out the manufacturer and model and post it here. If you can't find it, just post a screenshot of where you are stuck (you can take them by pressing CTRL + PRNT SCR, and paste it in Paint, then save the image and upload it online).
I get 2 things listed under "Display Adapters", LogMeIn Mirror Driver (I use this software, this is a internal windows program and it did not affect ubuntu on my old computer) and Nvida GeForceGT 520 (It says its PCI bus 1, device 0, function 0.)

---

### Post by aaronfranke on 2012-08-05
> **gordintoronto said:**
> Try this:
[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)
That might work, but I have a 64-bit computer and that screen only shows up on the 32-bit ubuntu CD. I would prefer to use a 64-bit OS if possible.

Also, oldfred basically posted the same thing.

---

### Post by Ubun2to on 2012-08-06
> **aaronfranke said:**
> I'm not a retard.

Did I say you were? No.

> **aaronfranke said:**
> I get 2 things listed under "Display Adapters", LogMeIn Mirror Driver (I use this software, this is a internal windows program and it did not affect ubuntu on my old computer) and Nvida GeForceGT 520 (It says its PCI bus 1, device 0, function 0.)
Is this the card you were talking about? [http://www.ubuntu.com/certification/catalog/search/?csrfmiddlewaretoken=8ef899bed08fd6931781ba4b2f64fb16&query=gt+520](http://www.ubuntu.com/certification/catalog/search/?csrfmiddlewaretoken=8ef899bed08fd6931781ba4b2f64fb16&query=gt+520)
If it is, it might be that the live CD doesn't have the drivers for it included-it said it worked with 11.10, but not anything newer or older.

---

### Post by aaronfranke on 2012-08-06
> **Ubun2to said:**
>  Is this the card you were talking about? [http://www.ubuntu.com/certification/catalog/search/?csrfmiddlewaretoken=8ef899bed08fd6931781ba4b2f64fb16&query=gt+520](http://www.ubuntu.com/certification/catalog/search/?csrfmiddlewaretoken=8ef899bed08fd6931781ba4b2f64fb16&query=gt+520)
If it is, it might be that the live CD doesn't have the drivers for it included-it said it worked with 11.10, but not anything newer or older.
Ok, everyone I got it to work. The "nomodeset" option was not available, so I edited the boot thingy and typed "nomodeset" like the instructions said. The result was a very ugly yet useable interface.

So, thanks to gordintoronto for linking that page, and thanks to Ubun2to for the semi-complete troubleshooting help.

---

