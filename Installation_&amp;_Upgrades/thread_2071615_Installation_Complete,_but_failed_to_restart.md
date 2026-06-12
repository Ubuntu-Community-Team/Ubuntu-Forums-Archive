---
title: "Installation Complete, but failed to restart"
date: 2012-10-15
forum: Installation &amp; Upgrades
---

### Post by Rbug2006 on 2012-10-15
I am a noob to Ubuntu and Linux in general. I popped in the Live CD and it gave me a black screen with a cursor. (I read that this was fixed by typing "fb=false video=vga:off") That fixed it, and is not my problem. I just thought I might include it in this post because my problem might be related.

So at that point, things were going smoothly. I got all the way through the installation without anymore problems. My problem came in when it finished. I was asked to "Restart Now" or "Restart Later". Well, might as well do it now... right?

I clicked the "Restart Now" button and I was redirected to a black screen with some text on it telling me to "Remove the CD and press Enter". So I did. It restarted the computer, but when it started to boot Ubuntu, I got a purple screen of death. I could not get to menu where I previously typed "fb=false" etc. I can attach some pictures tomorrow too if that would help.

---

### Post by Rbug2006 on 2012-10-16
Bump and Pictures(Sorry in advance for such large images. I couldn't figure out the "Spoiler Tag")

This first image was an attempt to edit the Grub file to force it to show up. I Couldn't save it though... I suppose it isn't really relevant anyways.

[IMG]http://i46.tinypic.com/11rdkt4.jpg[/IMG]

This next image is what Ubuntu told me to do After installation. I Proceded to do so.

[IMG]http://i48.tinypic.com/16026nn.jpg[/IMG]

Once I did so, I saw the typical purple screen, but there was no Keyboard or Stick Dude like last time.

[IMG]http://i48.tinypic.com/24l0d1y.jpg[/IMG]

Finally, after about 10 seconds, I get THIS mess, and it stays that way forever.

[IMG]http://i48.tinypic.com/2qnbpfb.jpg[/IMG]

---

### Post by Bashing-om on 2012-10-16
Rbug2006; Hi ! and Welcome to the forum.

The purple screen is ,as you are aware, indicative of a graphics issue;
Try booting up with the parameter "nomodeset" thus:
Boot up your install, soon as the bios screen clears depress the shift key -> grub menu
As soon as the grub menu appears hit any key to halt the countdown to boot;

Now we are going to edit the kernel command line to boot with the "nomodeset" option:
Arrow up to the first boot entry such that it becomes highlighted, press "e" key to edit;
in the file that expands arrown down to the line similar to this " linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff "
arrow over to -quit splash- and enter the term "nomodeset" with out the quotes;
ctl+x to continue the boot process.
This procedure does not survive a reboot so your system is not altered in any way.
full details here:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)


If you do boot into ubuntu at this time, and have a usable GUI;
on the left side of the screen is the launcher, in the launcher click on "System Settings"
System Settings opens ..second row, 1st icon = Additional Drivers -> click and install the recommended driver.

reboot 

is all good now ?
[INDENT]just try'n to help <==BDQ

[/INDENT]

---

