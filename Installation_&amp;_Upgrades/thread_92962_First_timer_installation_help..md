---
title: "First timer installation help."
date: 2005-11-20
forum: Installation &amp; Upgrades
---

### Post by kerunt on 2005-11-20
Hello,
Today I decided to try out the Ubunto Linux distro on my laptop (currently running XP Pro). 

I followed the following tutorial to resize my current partition and create a new one:
[http://www.ioerror.us/2005/06/18/partitioning-to-dual-boot-linux-and-windows-walkthrough](http://www.ioerror.us/2005/06/18/partitioning-to-dual-boot-linux-and-windows-walkthrough)

Everything went smoothly.

I downloaded the Ubuntu ISO. When I tried burning the ISO to a DVD using Nero's 'Burn Image to Disc' feature, Nero kept telling me that I had an incorrect disc, and would not burn. Maybe this is because I was trying to burn to a DVD instead of a CD? (I have no CDs.) Anyways, I decided to trick Nero. Using Daemon Tools I mounted the Ubuntu image as a virtual drive, copied all files to my hard drive, then burned them onto the DVD like I normally would. Now, here is my problem: I pop the DVD into the drive and reboot, the laptop apparently tries to read the disk, since I hear it spinning, and during the same time a command promt-like screen is shown. I see an underscore (flashing), like in Windows command prompt, but I cannot enter anything. Pressing enter results in some error-like beep. After 10-15 seconds, this screen dissapears and XP continues to boot.

What am I doing wrong? Is the problem in the way I burned the files? Do I need to get a CD? (I already ordered some Ubuntu CD's, but obviously they will take a while to get here...) 

By the way, I have never used nor installed any Linux distro before, so don't be too hard on me :P. 

Any help would be appreciated.

---

### Post by kerunt on 2005-11-20
Ok I got a CD from my neighbour, burned the ISO. This time the setup booted up real quick.  I pressed enter to run the regular setup, and now it seems to have frozen after the message 'Uncompressing Linux... Ok, booting the kernel.'. The underscore is flashing, but nothing is happening - has been this way for over 5 minutes.

---

### Post by aysiu on 2005-11-20
Maybe the image is corrupt? Did you do a checksum on the ISO before burning it?

---

### Post by kerunt on 2005-11-20
Ok, I got past that error with acpi = off. Had a partitioning problem which I also figured out. Then the network wouldnt get auto setup, so I did it manually. The installer just got to the part where it asked me to remove the CD and reboot. Doing that now :)

---

### Post by kerunt on 2005-11-20
Now this is strange, it seems to have installed fine, it was booting up, then the screen went completely black and I heard some "turum-turum" sound. The screen just stays black. Same thing after a reboot. :(

---

