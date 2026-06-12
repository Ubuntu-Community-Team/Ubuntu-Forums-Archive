---
title: "mountall:  disconnected from plymouth"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by jimbo99 on 2010-10-21
Several messages fly by, the screen flickers a few times, then I'm presented with this the message mountall:  disconnected from plymouth.

I've followed various threads that have similar errors.  I've attempted the solutions in those threads, to no avail.

After the above message is displayed I can't type at the keyboard to log in.  I've managed that machine in the past from SSH so I tried to SSH into it.  That allows me access to the box and it's how I tried those other thread's attempted solutions.

> **dino99 said:**
> 
sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a
sudo dpkg-reconfigure jockey
sudo dpkg-reconfigure plymouth
sudo dpkg-reconfigure gdm

Those were tried with no solution to the problem.

I reinstalled the video drivers which had caused similar errors on several of my other Ubuntu boxes in the past.

Of all the releases of Ubuntu, so far, this one has been the worst when it comes to upgrades.

Suggestions?

---

### Post by varun.kapoor on 2010-10-22
I had the same error, I logged in and then i typed sudo su and logged in as super user, immediately after that I was taken to the normal log in screen and it worked fine and am back in the system! So just log in as super user and the problem goes away.:guitar:

---

### Post by jimbo99 on 2010-10-22
The problem is that I can only log in via SSH.

The system worked prior to this update.  I'd been using it for well over a year, maybe two.

Edit:

Just tried it with SSH.  Didn't work.  Didn't change anything.

---

### Post by anypundit on 2010-10-24
> **varun.kapoor said:**
> I had the same error, I logged in and then i typed sudo su and logged in as super user, immediately after that I was taken to the normal log in screen and it worked fine and am back in the system! So just log in as super user and the problem goes away.

I had the same error after fooling around with mediatomb then apt-get upgrading.  I can TTY in and su, but still the same error on my linux box.  I have the latest stable Kubuntu.

SOLVED:
Mediatomb's log had expanded to fill my entire hd.  Log deleted, problem solved.  All of my future linux installs will have a separate var partition.

---

### Post by garvinrick4 on 2010-10-24
Do you all get a plymouth splash screen or does mountall hit before graphic drivers and fail to get your splash screen? If so make drivers hit before / mounts.
This is a fix from launchpad. Will force graphic drivers to hit before mountall package.
I have used for that purpose. If you feel problem is different and you get a splash then
just save for reference. This is only to get plymouth to start and nothing else.

```
sudo -i
``````
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
update-initramfs -u
```

---

### Post by jimbo99 on 2010-10-25
> **garvinrick4 said:**
> Do you all get a plymouth splash screen or does mountall hit before graphic drivers and fail to get your splash screen? If so make drivers hit before / mounts.
This is a fix from launchpad. Will force graphic drivers to hit before mountall package.
I have used for that purpose. If you feel problem is different and you get a splash then
just save for reference. This is only to get plymouth to start and nothing else.

```
sudo -i
``````
echo FRAMEBUFFER=y > /etc/initramfs-tools/conf.d/splash
update-initramfs -u
```

The real question is "WHAT IS PLYMOUTH" and why isn't it starting?  This isn't isolated.  This is major.  I now have two computers inflicted with this problem.

I cannot get into Ubuntu.  No desktop.  On one machine I can get into the terminal via SSH and the other from that computer.  I can issue normal commands.

No one here seems to have come up with a cogent solution.  Why is this not working and why is it giving this problem and can't anyone trace the issue and tell us what the cause is?

Before anyone goes further I think the PLYMOUTH issue is a non-starter.  I think the issue has to do with the xorg.conf file.  Starting with the failsafe version of the file the desktop is achievable.  Once you install the video drivers getting to the gui desktop is not.

---

### Post by jimbo99 on 2010-10-25
What I did to finally get both of my computers working was:

1) When presented with the login prompt that I couldn't type at, press alt + ctrl + F2 to switch to the next terminal.  I could then log in.

2) Go into the /etc/X11 folder and rename the xorg.conf to some other file such as xorg.conf.jimbo.backup.  Copy the xorg.conf.failsafe to xorg.conf.

3) Issue the two commands above about initramfs and the framebuffer.

4) Uninstall the nvidia driver by running sudo nvidia-installer --uninstall.  Then reboot.

5) When given the desktop go to the System>Administration>Additional Drivers and install the latest nvidia drivers through that. (I'm sure you can download and reinstall the latest drivers from nVidia's website, but no guarantees on that).

6) Reboot.

If you are using KDE as your DM then you may have to log into gnome first and rename your .kde folder (and possibly others), then log back out and change to the KDE DM and try again. (I have to revise this--after installing the downloaded nvidia drivers I was able to get to the kde desktop without modifying the KDE install by getting rid of the .kde folder).

The other errors about PLYMOUTH and moutall seem to be simply status messages from the boot sequence attempt.  They probably aren't error messages.

I'm not sure you need to do the two commands regarding initramfs and framebuffer as explained above by another poster.

Either way, this is nasty and all too common an occurrence to not have Canonical fix it promptly.

In the second computer's case, I didn't get window title bars with buttons.  After a while they showed up.  Also, there were no additional drivers available for it using the System>Adminstration>Additional Drivers option, so I downloaded from nVidia's site the updated 260.19.xx drivers and installed them.  Those brought me to a normal desktop, albeit gnome (when I use KDE normally).

---

### Post by javipas on 2010-11-23
> **jimbo99 said:**
> What I did to finally get both of my computers working was:

1) When presented with the login prompt that I couldn't type at, press alt + ctrl + F2 to switch to the next terminal.  I could then log in.

2) Go into the /etc/X11 folder and rename the xorg.conf to some other file such as xorg.conf.jimbo.backup.  Copy the xorg.conf.failsafe to xorg.conf.

3) Issue the two commands above about initramfs and the framebuffer.

4) Uninstall the nvidia driver by running sudo nvidia-installer --uninstall.  Then reboot.

5) When given the desktop go to the System>Administration>Additional Drivers and install the latest nvidia drivers through that. (I'm sure you can download and reinstall the latest drivers from nVidia's website, but no guarantees on that).

6) Reboot.

Thank you so much. It has been a lifesaver for me. After a Maverick update I wasn't able to login, and after the "mountall: disconnected from Plymouth" message the keyboard was not recognized (weird). 

Anyway, this is the right solution. I renamed the xorg.conf file from another disto I had installed, but the same can be accomplished from a LiveCD or LiveUSB,

Cheers and thanks for the little solution. If you ever come to Madrid, I owe you a beer and a pincho de tortilla de patatas :P

---

### Post by CupcakeM on 2011-03-08
Hello, 
when I run sudo nvidia-installer --uninstall, I get the message that the command nvidia-installer does not exist. Perhaps I should be writing it differently? 
Also, in X11 I didn't find an xorg.conf.failsafe so I copied the new xorg.conf.backup back to xorg.conf .
Any help with the nvidia-installer would be great (sorry for such a  basic question).

---

### Post by evilsectoid on 2011-09-12
> **jimbo99 said:**
> What I did to finally get both of my computers working was:

1) When presented with the login prompt that I couldn't type at, press alt + ctrl + F2 to switch to the next terminal.  I could then log in.

2) Go into the /etc/X11 folder and rename the xorg.conf to some other file such as xorg.conf.jimbo.backup.  Copy the xorg.conf.failsafe to xorg.conf.

3) Issue the two commands above about initramfs and the framebuffer.

4) Uninstall the nvidia driver by running sudo nvidia-installer --uninstall.  Then reboot.

5) When given the desktop go to the System>Administration>Additional Drivers and install the latest nvidia drivers through that. (I'm sure you can download and reinstall the latest drivers from nVidia's website, but no guarantees on that).

6) Reboot.

If you are using KDE as your DM then you may have to log into gnome first and rename your .kde folder (and possibly others), then log back out and change to the KDE DM and try again. (I have to revise this--after installing the downloaded nvidia drivers I was able to get to the kde desktop without modifying the KDE install by getting rid of the .kde folder).

The other errors about PLYMOUTH and moutall seem to be simply status messages from the boot sequence attempt.  They probably aren't error messages.

I'm not sure you need to do the two commands regarding initramfs and framebuffer as explained above by another poster.

Either way, this is nasty and all too common an occurrence to not have Canonical fix it promptly.

In the second computer's case, I didn't get window title bars with buttons.  After a while they showed up.  Also, there were no additional drivers available for it using the System>Adminstration>Additional Drivers option, so I downloaded from nVidia's site the updated 260.19.xx drivers and installed them.  Those brought me to a normal desktop, albeit gnome (when I use KDE normally).

This works!
I was installing the 280.26 nvidia drivers from nvidia.com and it caused this issue.
Thank you

---

### Post by 9melon on 2011-12-02
Can't seem to find xorg.conf for 11.10 (Oneiric). Any ideas how to resolve this on Oneiric?

---

### Post by Petro026 on 2012-01-02
As an FYI I also had this same problem when installing VirtualBox gummed up my xorg.conf file.  Once I restored the original xorg.conf the plymouth error went away and the desktop actually started

---

### Post by slythen on 2012-03-08
> **CupcakeM said:**
> Hello, 
when I run sudo nvidia-installer --uninstall, I get the message that the command nvidia-installer does not exist. Perhaps I should be writing it differently? 
Also, in X11 I didn't find an xorg.conf.failsafe so I copied the new xorg.conf.backup back to xorg.conf .
Any help with the nvidia-installer would be great (sorry for such a  basic question).
I'm having the same issue. it installed the drivers for me for another built in nvidia card and i installed a seperate one

---

### Post by csbac on 2012-03-14
Hi!
Seems the problem also appears if the swap device "disappears".
Then, you have to create one again and enter the correct uuid in /etc/initramfs-tools/conf.d/resume, and re-create the initramfs (update-initramfs -u).
I'm not sure in how far this no-swap influences the graphical boot, as the system I had this problem does not start any x11 on startup.

Yours,
Sebastian

---

### Post by pkaramol on 2012-07-11
Hi,

I am getting the same problem after removing GNOME (I have KDE installed).

The previous posts did not help.

Now the boot halts in the annoying "disconnected from Plymouth" message and then I have to Alt+Ctrl+F2 --> login --> manually startx.

But even before being able to do that I had to add a "exec startx" line in the /etc/X11/xinit/xinitrc cause I was getting a "$DISPLAY not set" error.

BTW there is no xorg.conf file on my machine.

---

### Post by BigMcGuire on 2012-10-09
I too did the same thing as the above poster. However, I'm on an Acer Chromebook and CTRL ALT F2 doesn't seem to be doing anything after I get the mountall: disconnect from plymouth.

Am I SOL and have to reinstall Ubuntu?!

Thanks,
-Paul

---

### Post by pingle on 2013-03-04
I resolve the problem by rebooting into recovery mode and selected each option in the list on the dialog, then rebooted and was able to proceed.

---

### Post by steamer360 on 2013-08-17
> **BigMcGuire said:**
> I too did the same thing as the above poster. However, I'm on an Acer Chromebook and CTRL ALT F2 doesn't seem to be doing anything after I get the mountall: disconnect from plymouth.

Am I SOL and have to reinstall Ubuntu?!

Thanks,
-Paul

I too am on an Acer C7 Chromebook with ChrUbuntu installed, and I have been having the same issue. When I try to boot up, I get the usual "invalid iomen size, you may experience problems" message, but it doesn't boot in any more, it jut stays on that screen. Pressing CTRL ALT F2 brings me to the "mountall: disconnected from plymouth" screen. I thought this had something to do with the Paw OSX splash screen that I tried to install (did not work), but after I deleted the theme and reset the defaults, I still get the same message. However, I am able to access my machine by inserting any usb key into it until it boots into the login screen. Any sort of usb key seems to work (not sure why), but it is slightly inconvenient to have to carry around a usb key everywhere I go. Does anyone have a solution for this?

---

### Post by steamer360 on 2013-08-18
Try deleting your cache, and then opening up the Netflix Desktop app again. It should reinstall everything and will (hopefully) be working like normal. This worked for me and I am happily watching Netflix Desktop on my linux machine :)

**[SIZE=5]EDIT: [/SIZE]**[SIZE=5]Please D**[SIZE=5][/SIZE]**isregard this post, incorrect thread.[/SIZE]

---

