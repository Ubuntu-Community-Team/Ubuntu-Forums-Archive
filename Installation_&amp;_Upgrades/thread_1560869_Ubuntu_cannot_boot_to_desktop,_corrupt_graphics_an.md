---
title: "Ubuntu cannot boot to desktop, corrupt graphics and a useless PC."
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by Ubuntarded on 2010-08-25
As the name implies, I'm new to Ubuntu (and Linux in general). I installed Ubuntu on my desktop about a week ago, have had zero problems and the experience with it was highly enjoyable. However, after said week, my monitor went jaggedy with corrupt graphics, and ever since my bootup consists of a jagged, pixelated CROSSHAIR icon (my mobo), corrupt graphics (blinking music notes and omega symbols, though they seem to generate randomly and are not exclusive), and the Ubuntu splash that quickly disappears and goes to a black screen that ceases activity afterwards. 
 
Quite the n00b here, yet I've tried every remedy I've found via Google on the subject, it seems others are having the same problem but there's not a universal fix (as far as I've seen). I have an Nvidia GeForce 7800 GTX but I can't figure out how to go about installing any new driver because I can't even get to my desktop. Any help with this is much appreciated, as my desktop is now on hiatus :(
 
...Other than that Ubuntu is awesome and works very well.

---

### Post by lechien73 on 2010-08-25
What happens if you try and boot from a Live CD, do you get the same problem?

The fact that your motherboard logo is also showing jagged and pixellated, would indicate that it is a hardware issue - rather than to do with your operating system - perhaps faulty video RAM?

---

### Post by Ubuntarded on 2010-08-25
> **lechien73 said:**
> What happens if you try and boot from a Live CD, do you get the same problem?
 
The fact that your motherboard logo is also showing jagged and pixellated, would indicate that it is a hardware issue - rather than to do with your operating system - perhaps faulty video RAM?
 
Yes, even the Live CD fails to get to the desktop. However, it does get me to at least some form of GUI, albeit offering me little to no help. The Live CD gets me the same pixelated and corrupt graphics I see when my mobo's logo is displayed, no solutions.
 
I've learned that yes it is a hardware problem, particularly with my Nvidia driver. 1 in about 50 (no exaggeration) consecutive reboots actually gets me to my desktop with success, but after literally 30 seconds of using my desktop the graphics, like the flip of a switch, become corrupt and Ubuntu fails to respond afterwards. I reboot, and it's back to corrupt mobo logo and inactivity. I understand it's with my video driver but my problem is that I haven't any way of fixing the problem because I have such little access to my computer as it is. 
 
I feel it's important to note that my video card has been working flawlessly for several years, I purchased it right as it came out and haven't had any issues with it until Ubuntu.
 
Would a video of my boot process aid in the diagnosis?

---

### Post by lechien73 on 2010-08-25
> **Ubuntarded said:**
> Would a video of my boot process aid in the diagnosis?

Yes - as much information as possible would be useful :)

Does plain text appear ok? For example, do you get the Grub menu when starting your PC, and is this legible?

If so, you could press 'E' at the Grub menu to edit the startup config. Then enter the words **nomodeset xforcevesa** after the words **quiet splash**. Press **CTRL+X** to reboot.

I'd still be fairly sure it's a physical hardware problem, rather than anything to do with software and drivers, though, but I could be wrong. Please post a video, though, and we'll see what happens.

---

### Post by Ubuntarded on 2010-08-25
After a grueling 45 minutes of my Droid trying to upload 13MB worth of video...I finally have it on video.
 
This is as far as it goes:
 
[http://www.youtube.com/user/ASFXE8#p/a/u/0/Xal-SoD3osY](http://www.youtube.com/user/ASFXE8#p/a/u/0/Xal-SoD3osY)

---

### Post by lechien73 on 2010-08-25
Thanks for the effort to do that :)

I'm sorry to say that it is almost certainly a fault with the graphics card, and not linked to Ubuntu.

You could try the following:

[LIST]
[*]Open the box and make sure that the card's heatsink isn't dusted up and the fans are working.
[*]Remove and re-seat the card.
[*]Make sure that your earth (ground) connection is ok.
[*]Try a BIOS update for your PC.
[*]Try replacing the card with a different one, and see if the problem goes away.
[/LIST]

Sorry that's all I can come up with, but it looks like it's a problem separate from your operating system.

---

### Post by Ubuntarded on 2010-08-25
> **lechien73 said:**
> Thanks for the effort to do that :)
 
I'm sorry to say that it is almost certainly a fault with the graphics card, and not linked to Ubuntu.
 
You could try the following:

[LIST]
[*]Open the box and make sure that the card's heatsink isn't dusted up and the fans are working.
[*]Remove and re-seat the card.
[*]Make sure that your earth (ground) connection is ok.
[*]Try a BIOS update for your PC.
[*]Try replacing the card with a different one, and see if the problem goes away.
[/LIST]
Sorry that's all I can come up with, but it looks like it's a problem separate from your operating system.
 
Tried 1, 2, and 3. Made zero changes at all. Haven't tried a BIOS update, how would I go about doing that?
 
All of this happened AFTER I installed Ubuntu and had been using it. I was previously using Windows 7 (the partition no longer exists, I cannot tolerate Microsuck) and had zero problems with my graphics. Booted right up every time.
 
It just seems **too **coincidental for my video card to go up only after uninstalling Windows and switching to Lucid Lynx. Don't have another PCI-E card, that 7800 GTX was a huge investment years ago when I bought it. I might be able to borrow a PCI-E card from a friend, but I have my doubts. 
 
Any other suggestions you could think of? You've been extremely helpful thus far, much appreciated.

---

### Post by lechien73 on 2010-08-25
The BIOS update should be available from Asus' website - [http://www.asus.com](http://www.asus.com). Find your motherboard model number in the support section, and updates will be available there.

Try downloading the BIOS upgrade and applying it according to the instructions for your motherboard. I do think trying another card is also a good idea.

I know it seems too co-incidental, but hardware does degrade over time. Maybe the card overheated and some RAM chips are now damaged. The fact that, as can be seen on your video, the screen corruption starts before boot - as in before any Ubuntu files have been loaded into memory - indicates that it's not a graphics driver issue.

---

