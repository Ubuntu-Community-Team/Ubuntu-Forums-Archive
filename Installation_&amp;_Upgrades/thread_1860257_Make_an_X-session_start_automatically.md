---
title: "Make an X-session start automatically??"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by bigbeck89 on 2011-10-14
OK, so I upgraded from 11.0 to 11.1, but I've run into some issues.

Initially I was stuck at a blank screen, but eventually got to where it seemed like ubuntu was booting, but it just sat there as if my monitor was connected to a server without a display set: [http://ubuntuforums.org/attachment.php?attachmentid=204303&stc=1&d=1318621357](http://ubuntuforums.org/attachment.php?attachmentid=204303&stc=1&d=1318621357)


Anyways,  by following the instructions here: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)  I was able to use ctrl+alt+f1 to switch over to a terminal and log in via command line. From there I was able to use the command: **sudo service gdm start** to start up the gui.

The display didn't open quite right as I had a blank screen (except for a thin line where the login panel should be). [http://ubuntuforums.org/attachment.php?attachmentid=204304&stc=1&d=1318621357](http://ubuntuforums.org/attachment.php?attachmentid=204304&stc=1&d=1318621357) I just typed in my login info and it seemed to start up correctly.

My question is, how do I make ubuntu just start in the gui by default? I've never had to manually launch a gui session before... I see my graphic driver is now listed as "unknown": [http://ubuntuforums.org/attachment.php?attachmentid=204305&stc=1&d=1318621357](http://ubuntuforums.org/attachment.php?attachmentid=204305&stc=1&d=1318621357) and my display is a little wonky, is that the reason it isn't starting automatically?

I ran the "additional drivers" and nothing came up.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=204306&stc=1&d=1318621357[/IMG]

---

### Post by MAFoElffen on 2011-10-14
> **bigbeck89 said:**
> OK, so I upgraded from 11.0 to 11.1, but I've run into some issues.

Initially I was stuck at a blank screen, but eventually got to where it seemed like ubuntu was booting, but it just sat there as if my monitor was connected to a server without a display set: [http://ubuntuforums.org/attachment.php?attachmentid=204303&stc=1&d=1318621357](http://ubuntuforums.org/attachment.php?attachmentid=204303&stc=1&d=1318621357)


Anyways,  by following the instructions here: [http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)  I was able to use ctrl+alt+f1 to switch over to a terminal and log in via command line. From there I was able to use the command: **sudo service gdm start** to start up the gui.

The display didn't open quite right as I had a blank screen (except for a thin line where the login panel should be). [http://ubuntuforums.org/attachment.php?attachmentid=204304&stc=1&d=1318621357](http://ubuntuforums.org/attachment.php?attachmentid=204304&stc=1&d=1318621357) I just typed in my login info and it seemed to start up correctly.

My question is, how do I make ubuntu just start in the gui by default? I've never had to manually launch a gui session before... I see my graphic driver is now listed as "unknown": [http://ubuntuforums.org/attachment.php?attachmentid=204305&stc=1&d=1318621357](http://ubuntuforums.org/attachment.php?attachmentid=204305&stc=1&d=1318621357) and my display is a little wonky, is that the reason it isn't starting automatically?

I ran the "additional drivers" and nothing came up.
Please back up a bit...

You have a Radeon X13xx to X15xx video card...
You seem to have Postgres Plus Advanced Server 9.0 installed...
You are having problem booting, possibly with the graphics, but not confirmed yet.

- What edition of 11.04 did you upgrade from (Desktop or Server)?
- Did you install postgre sql server in 11.04 and did you have it **all** configured before you upgraded?
- What video driver were you using in 11.04?
- Can you get to a Grub menu on bootup?

Using the first 3 posts of my sticky (that you referred to above) as referrence, if you can get to a Grub menu...
Press "e", will put you into an edit mode > Arrow down to the line that starts with "linux" > Arrow right to where it says "quiet splash" > Replace "quiet splash" with "--verbose text" > Press <cntrl><x> to boot with those options.

That will boot the kernel to a TTY Text Console with verbose messaging turned on.  Write down any error messages and post.

Post your /var/log/Xorg.0.conf.

---

### Post by bigbeck89 on 2011-10-14
Thanks for the reply!

> **MAFoElffen said:**
> 
You have a Radeon X13xx to X15xx video card... 
Yes, RV516 [Radeon X1300 Pro] , two of them.

> **MAFoElffen said:**
> 
You seem to have Postgres Plus Advanced Server 9.0 installed...

> **MAFoElffen said:**
> 
- Did you install postgre sql server in 11.04 and did you have it **all** configured before you upgraded?

Yes it is, someone else was using this computer before me to do some development in postgres. I assume he had it fully installed and configured, but Im not sure.

I do not need postgres and can uninstall it if it could be part of the problem.

> **MAFoElffen said:**
> 
- What edition of 11.04 did you upgrade from (Desktop or Server)?

I upgraded from the desktop version

> **MAFoElffen said:**
> 
- What video driver were you using in 11.04?

Im not sure as I just got this computer from someone else...

> **MAFoElffen said:**
> 
- Can you get to a Grub menu on bootup?

Using the first 3 posts of my sticky (that you referred to above) as referrence, if you can get to a Grub menu...
Press "e", will put you into an edit mode > Arrow down to the line that starts with "linux" > Arrow right to where it says "quiet splash" > Replace "quiet splash" with "--verbose text" > Press <cntrl><x> to boot with those options.

That will boot the kernel to a TTY Text Console with verbose messaging turned on.  Write down any error messages and post.


Ok I did that, errors were:
**modprobe vboxdrv failed. Please use 'dmesg' to find out why** and
**Stopping automatic crash report generation**


> **MAFoElffen said:**
> 
Post your /var/log/Xorg.0.conf.
Did you want a config file? There is a log file by that name in that directory, but no config. I'm new to linux so I do not know where to look for a config file, or is it supposed to be with the logs?

I attached the log file (by the way, what the difference between Xorg.0.log and the other Xorg.x.logs that are there?)

I also attached the dmesg output, both are in a tar.gz

Thanks for the assistance, I greatly appreciate it.

---

### Post by MAFoElffen on 2011-10-14
> **bigbeck89 said:**
> Thanks for the reply!

Yes, RV516 [Radeon X1300 Pro] , two of them.

Yes it is, someone else was using this computer before me to do some development in postgres. I assume he had it fully installed and configured, but Im not sure.

I do not need postgres and can uninstall it if it could be part of the problem.

I upgraded from the desktop version

Im not sure as I just got this computer from someone else...

Ok I did that, errors were:
**modprobe vboxdrv failed. Please use 'dmesg' to find out why** and
**Stopping automatic crash report generation**

Did you want a config file? There is a log file by that name in that directory, but no config. I'm new to linux so I do not know where to look for a config file, or is it supposed to be with the logs?

I attached the log file (by the way, what the difference between Xorg.0.log and the other Xorg.x.logs that are there?)

I also attached the dmesg output, both are in a tar.gz

Thanks for the assistance, I greatly appreciate it.
Yes, I wanted the log, not the config file.

I see where:
```

[   260.928] (EE) Failed to load module "fglrx" (module does not exist, 0)

```
So your video driver is not loaded.

Reboot your machine. Immediately after bios hold the shift key down. The Grub boot menu should display. Run the Reescue mode boot menu item. At the system rescue menu, hit resume normal boot and once again hold  the shift key. Continue to hold until you hit the login prompt command  line. Login

After Login
```

sudo apt-get install fglrx

```After install... Reboot.

---

