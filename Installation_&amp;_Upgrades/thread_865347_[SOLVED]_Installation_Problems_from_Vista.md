---
title: "[SOLVED] Installation Problems from Vista"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by ckrause on 2008-07-20
I was having some issues when trying to install the newest version of Hardly Heron from my HP dv1000 running on Vista Ultimate.  Initially, it wouldn't do a full installation so I partitioned my hard drive and tried to install it that way.  I was able to log on to the partitioned version, but when it tried to reboot my computer, it will not power up again.  I know this is not a power problem because the light will turn on and off when I am charging my laptop but it simply won't do anything when i press the power button.  In addition to the power problem, any other hints concerning how to do a seamless installation of Hardly Heron in general.  From Vista, when I tried to boot my computer with the disc in the drive, it just loaded windows like nothing was in the drive.

---

### Post by wpshooter on 2008-07-20
Are you saying that you are not getting any video whatsoever, even the BIOS/startup screens ?

You do have the CD-ROM drive set as the first boot device in BIOS ?

---

### Post by ckrause on 2008-07-20
I was able to get the BIOS initially, but after logging on to ubuntu for the first time, I tried to restart the computer but it literally will not turn on.

---

### Post by wpshooter on 2008-07-20
Are you getting any power to any of the components on the computer, i.e. fans, drives, keyboard lights, etc., etc. ?

---

### Post by misterbk on 2008-07-20
I'm very interested in the outcome of this...  I have an HP laptop on the way that I was going to do the exact same thing with.  (Vista-64, XP-32, and Kubuntu.)

Also I seem to remember seeing another thread asking about a computer becoming entirely unbootable, no bios, after doing something ubuntu-related...  Let me see if I can dig that up.

-edit-
_[LINK: Here's the thread]("http://ubuntuforums.org/showthread.php?t=842772&page=2")_

Quick recap of the thread is he had boot problems with vista and tried Super-Grub.  Probably completely unrelated, at the same time as he was running Super Grub, one of his RAM sticks blew out.  

Last time I saw the thread he hadn't found the RAM stick yet.  So, I guess it ended up having nothing to do with Linux, except that Super Grub had decided to overwrite the MBR of ALL attached disks and not just the one he specified.  (He recommends not using Super Grub.  :) )

---

### Post by ckrause on 2008-07-20
Yes, the lights on the front will flash when I press the power button.  Other than that I havent checked to see if any of the other components have power, but I would assume they do.

---

### Post by flytripper on 2008-07-20
leave it running and see if it boots to the login screen. if it does then you have a splash screen problem. problem being the resolution is set too high and causes the boot process to appear to hang.

---

### Post by misterbk on 2008-07-20
Just a thought, make sure the volume knob is up.  My laptop's bios beeps are silenced if the volume is down.  (hey, you never know!)

Another suggestion...  It's possible something has gone strange with the power adapter.  HP ships power adapters rated pretty close to a typical laptop's power requirements and I've heard of failures.  The laptop might have a dead battery and not enough juice from the AC line to power up.  You could let it charge for a while and then give it another try.

Or maybe take out the battery...  it's possible a battery failure could prevent a correctly-functioning AC adapter from powering the laptop.

Another thought.  I have an Alienware laptop that has a mechanical switch for the laptop lid.  The switch is going bad and not making proper contact all the time, and the result is the screen blanks out, sometimes even during bios.  If I poke the switch with a toothpick I can usually get it to come back.  Don't use anything metal though!  I tried a thumbtack once, it slipped into the hole, and sparks shot out!

If you suspect the system might be starting up correctly but having display problems, and you have a decent router for your internet connection, you can try this:

- plug the laptop in to ethernet and shut it off
- log in to your router using another machine
- find the table of DHCP entries.  Clear it.
- Turn on your laptop and see if a new DHCP entry shows up for it after a few minutes.

If it's booting to linux by default, that trick would also give you the IP address to connect to using SSH (if you installed openssh-server) and you can poke around that way.

---

### Post by ckrause on 2008-07-20
I resolved the problem.  The system didn't have enough power to start up.  It was a coincidence that my power cord stoped working at the same time when I tried to install Hardly Heron.  Thanks for all your help.

---

