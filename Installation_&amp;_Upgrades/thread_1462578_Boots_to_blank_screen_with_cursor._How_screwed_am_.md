---
title: "Boots to blank screen with cursor. How screwed am I?"
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by NinjaSpaz on 2010-04-25
I am a complete Linux newbie and I tried installing the latest release candidate (10.04) as a dual boot with Windows XP. The install seemed to go fine and it said it needed to reboot to finish the install. It rebooted and then displayed a series of errors on a DOS-like screen (which I wish I wrote down).  When I realized that it was definitely hung, I then held the power button to shut it off. After that, all it does is boot to up to a blank/black screen with a cursor.

The box is old and I was actually going to throw it away, but I figured  this was a good opportunity to give Linux a try.  At this point, I'm willing to go to either Windows or Ubuntu... I don't really care which.  I actually just want to recover some files on the box.

Any ideas on next steps?  Any help would be greatly appreciated.

Thanks,

---

### Post by limey_rick on 2010-04-26
Have you tried booking the Live CD? If you can, boot the 10.04 Live CD, or get a 9.10 Live CD and boot this. 

Once you've booted this, follow some of the steps here to see if its because GRUB installed on the wrong disk or something else. 

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Please provide some more information about the number of disks on your machine. Just one, or multiple?

---

### Post by grege on 2010-04-26
If nothing else use a Live CD and a USB stick to recover the files you need to save - and do it before you try anything else.

---

### Post by NinjaSpaz on 2010-04-26
Thanks for your help. Yeah, I actually tried that today (before seeing your posts) and was able to boot successfully from the CD and access the files (which is great).

Oddly enough, without changing anything, I can now boot to the screen where I can select an OS. When I select Ububtu (the default), I see the following error:
[INDENT]There is a problem with the configuration server.
(/usr/lib/libgconf2-4/gconf-sanity-check-2 exited with status 256)
[/INDENT]Then, once I get in, I see the following in the upper-right:
[INDENT]The configuration defaults for Gnome Power Manager have not been installed correctly. Please contact your administrator.
[/INDENT]I tried a few things, but I was unable to get past this. I'm going to install 9.1 over this to see if that works.
 
- James -

---

### Post by NinjaSpaz on 2010-04-27
I installed 9.1 last night. Everything seemed to go fine with the install. It booted up and went right to Ubuntu and I was able to browse around for a little bit. Then, Firefox crashed after installing a Flash plug-in and I couldn't get Firefox to open back up, so I reset.  After a reset (and all susequent resets) I now see that same strange login screen as below with the same error:
[INDENT]The configuration defaults for Gnome Power Manager have not been  installed correctly. Please contact your administrator.
[/INDENT]Any ideas to get around this?  If so, please speak slowly, because I'm a complete Linux newbie.

---

### Post by saliflo on 2010-04-27
it's not grub problem

---

### Post by NinjaSpaz on 2010-04-28
That's what they said about my lawn.

Anyone have any thoughts on what I can do to fix this?

---

### Post by NinjaSpaz on 2010-04-28
I found this link via the forums:
[http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/](http://www.absolutelytech.com/2010/04/13/solved-unable-to-boot-due-to-gnome-power-manager-error/)

As it turns out, the issue was that I was out of space in the root drive.  Didn't realize the install was migrating the pics and MP3s from the windows user, which consisted of a TON of data and completely filled it up.  I reinstalled and omitted those from the profile import. After that, everything is cool.

Looking fwd to seeing what this OS is all about.

---

