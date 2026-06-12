---
title: "Floppy Drive Question 10.10 version"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by Dr. C on 2010-10-18
Is there a way to read floppy disks on 10.10? This is really the same problem that was in 10.04 only the fix of downgrading and locking udisks explained in the following thread [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1511446]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1511446") no longer works in 10.10. as there is only one version of udisks. 

I have tried the floppy on 10.04 after the patch and it works fine, so there is nothing wrong with the floppy or the drive. On 10.10 the floppy drive lights up and then nothing happens or one gets a no media in drive error with a perfectly good floppy in the drive.  

Thanks so much.

---

### Post by plucky on 2010-10-18
This has always worked for me.

Add ```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
``` to /etc/fstab if it is not already there.

Then run ```
sudo mount -a
``` to get the floppy recognized.Miss this step if the line was already in /etc/fstab

Open a terminal and ```
udisks --mount /dev/fd0
``` and the floppy0 icon will appear on your desktop.

Good Luck

---

### Post by psusi on 2010-10-18
<Frakenstein>Floppy drive bad, rawr!</Frakenstein>

Seriously, they were obsolete over 10 years ago.  1.44 MB that can't even read/write as fast as your average Internet connection can transfer these days?  Throw the thing in the trash; it's useless.

---

### Post by Dr. C on 2010-10-18
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
``` is already in /etc/fstab so ```
udisks --mount /dev/fd0
``` by itself worked great. Thanks so much

---

### Post by Dr. C on 2010-10-18
> **psusi said:**
> <Frakenstein>Floppy drive bad, rawr!</Frakenstein>

Seriously, they were obsolete over 10 years ago.  1.44 MB that can't even read/write as fast as your average Internet connection can transfer these days?  Throw the thing in the trash; it's useless.

I beg to differ. My next project is getting the 5.25in floppy working on 10.10. :wink:

---

### Post by Gerhard Maag on 2010-10-23
I have an old Roland/Rodgers W0-50 Keyboard with a floppy drive for running MIDI files, so I need floppy capability.

Downgraded udisks in 10.04 and got around the problem.  Maverick is an new obstacle.

Fix didn't work for me exactly.  With a normal floppy controller on the motherboard, Ubuntu assigns the floppy to fd0.  My home machine is configured that way.  With the correct entry in fstab, I was able to mount using the udisks --mount /dev/fd0 command, but it is read-only.  Haven't figured that out yet, but I don't really need a floppy at home.

My office uses an external usb floppy, which is a different animal.  This is the crucial part:  Ubuntu doesn't recognize it as a conventional floppy, but as a harddrive and assigns it an /dev/sdx location.  The disk utility (palimpsest) will tell you the device name.  That name can change, however, depending on what you have plugged into usb.  I plugged in a pendrive and everything shifted a letter.

I edited fstab to reflect the device name, for example:

/dev/sdc        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

(Adding a UUID to fstab is pointless, for every floppy disk has a different id.)

Actually, this may not be necessary.  I am able to mount with the udisks command, so long as I have the correct location:  udisks --mount /dev/(whatever ubuntu assigns on boot)

Adding "floppy" to /etc/modules doesn't seem to have any effect either.

The icon appears, and I have read-write capability.  If I unmount, and insert a different disk, I am able to mount again with the same command.  I created a desktop launcher, and it works well.

I've lost the auto-mount at insertion function, but that's no problem.

---

### Post by Dr. C on 2010-10-24
Marking thread as unsolved as the, fix although very helpful, does not fully address the problem

---

### Post by richo132 on 2010-11-12
> **FineE said:**
> I beg to differ. My next project is getting the 5.25in floppy working on 10.10. :wink:
I'm with FineE on this one.
My interest is very early PCs eg IBM PC/PCXT/AT, Amiga 1000/2000/3000 etc.
I use Ubuntu as the OS on a Pentium4 'multimedia' PC that can safely access the internet for old software and convert between media formats. This PC has LS120, Zip100, DVDRW, 360Kb & 1.2Mb drives installed + external 8" FDD connected to the internal FDC when required - rarely :)
Next project is get 2.88Mb 'Backpack' FDD working through the parallel port.
Not sure that this would be possible with any other OS but Linux.

---

### Post by Dr. C on 2010-11-13
> **richo132 said:**
> I'm with FineE on this one.
My interest is very early PCs eg IBM PC/PCXT/AT, Amiga 1000/2000/3000 etc.
I use Ubuntu as the OS on a Pentium4 'multimedia' PC that can safely access the internet for old software and convert between media formats. This PC has LS120, Zip100, DVDRW, 360Kb & 1.2Mb drives installed + external 8" FDD connected to the internal FDC when required - rarely :)
Next project is get 2.88Mb 'Backpack' FDD working through the parallel port.
Not sure that this would be possible with any other OS but Linux.

I am curious how is the 8in floppy drive is connected to the FDC? Is there a special adapter from the 50 pin connector on the 8in floppy drive to the 5.25 floppy connector on the cable? Now back to the problem at hand. I did get both the 3.5in and 5.25in floppy drives working at the same time in lucid by the using udisks 1.0.1-1build1. The 5.25in as fd0 and the 3.5in as fd1. Both however show up as floppy making it confusing to tell them apart.

There are two launchpad bugs on this [https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/539515?comments=all]("https://bugs.launchpad.net/ubuntu/+source/udisks/+bug/539515?comments=all") and [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441835?comments=all]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/441835?comments=all")

---

### Post by HunterZ on 2010-11-27
> **plucky said:**
> This has always worked for me.

Add ```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
``` to /etc/fstab if it is not already there.

Then run ```
sudo mount -a
``` to get the floppy recognized.Miss this step if the line was already in /etc/fstab

Open a terminal and ```
udisks --mount /dev/fd0
``` and the floppy0 icon will appear on your desktop.

Good Luck
The udisks command is the only thing that has caused my floppy drive to mount properly in Ubuntu 10.10. Nautilus can't do it (gives an error) and the mount command silently fails. What's the deal? (and thanks for the workaround!)

---

### Post by chideock on 2010-11-27
The udisks work around is working for me but only to read the floppy and copy from the floppy to my hard drive.
Udisks does not allow writing to the floppy - "permissions denied"

I wanted to make a "Smart Boot Manger" floppy and with the write disabled I can not do this. (see comments added below)

Why does Ubuntu not allow the use of the floppy with normal gui tools?

I have now figured out how to write to the floppy - udisks to mount the floppy - then do sudo nautilus - then use that window with another file browser window to copt/paste files.
Using the command in the Ubuntu docs to create a Smart Boot Manger floppy works OK after mounting the floppy with udisks

---

### Post by rootessa on 2011-04-05
> **plucky said:**
> This has always worked for me.

Add ```
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
``` to /etc/fstab if it is not already there.

Then run ```
sudo mount -a
``` to get the floppy recognized.Miss this step if the line was already in /etc/fstab

Open a terminal and ```
udisks --mount /dev/fd0
``` and the floppy0 icon will appear on your desktop.

Good Luck
I tried Plucky's suggestions and received a "permission denied"message.Anyone have a suggestion?

---

### Post by plucky on 2011-04-05
> I tried Plucky's suggestions and received a "permission denied"message.Anyone have a suggestion? 

Which command gave you the "permission denied"?

Have you rebooted since adding the line to "fstab"?

---

### Post by rootessa on 2011-04-05
I tried the /dev/fd0 command in the terminal and got "permission denied." Yes I've tried to reboot hoping something simply magical would happen! lol.

---

### Post by plucky on 2011-04-05
> **rootessa said:**
> I tried the /dev/fd0 command in the terminal and got "permission denied." Yes I've tried to reboot hoping something simply magical would happen! lol.

That is not a command,it is the line you have to add to the /etc/fstab file

To add that line to /etc/fstab you need to use ```
gksudo gedit /etc/fstab
``` as it is a system file,add the line and save the file.

After you do this,post the output from the terminal for ```
cat /etc/fstab
``` just to make sure you have done it correctly.

Then reboot and try the other lines.

Good luck

---

### Post by rootessa on 2011-04-05
I followed your great guidance and got:
Mount failed. did not recieve a reply Possible causes include the remote application did not send a reply......
I've been fighting with this computer for 5 months now and I'm almost completely convinced there is something wrong with it (other than me). This is not the first problem I've tried endlessly to solve that remains unresolved. Thanks for your help![IMG]file:///home/user/Desktop/Screenshot-user@user-laptop:%20%7E.png[/IMG]

---

### Post by frogotronic on 2012-01-11
> **Gerhard Maag said:**
> I have an old Roland/Rodgers W0-50 Keyboard with a floppy drive for running MIDI files, so I need floppy capability.

Downgraded udisks in 10.04 and got around the problem.  Maverick is an new obstacle.

Fix didn't work for me exactly.  With a normal floppy controller on the motherboard, Ubuntu assigns the floppy to fd0.  My home machine is configured that way.  With the correct entry in fstab, I was able to mount using the udisks --mount /dev/fd0 command, but it is read-only.  Haven't figured that out yet, but I don't really need a floppy at home.

My office uses an external usb floppy, which is a different animal.  This is the crucial part:  Ubuntu doesn't recognize it as a conventional floppy, but as a harddrive and assigns it an /dev/sdx location.  The disk utility (palimpsest) will tell you the device name.  That name can change, however, depending on what you have plugged into usb.  I plugged in a pendrive and everything shifted a letter.

I edited fstab to reflect the device name, for example:

/dev/sdc        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

(Adding a UUID to fstab is pointless, for every floppy disk has a different id.)

Actually, this may not be necessary.  I am able to mount with the udisks command, so long as I have the correct location:  udisks --mount /dev/(whatever ubuntu assigns on boot)

Adding "floppy" to /etc/modules doesn't seem to have any effect either.

The icon appears, and I have read-write capability.  If I unmount, and insert a different disk, I am able to mount again with the same command.  I created a desktop launcher, and it works well.

I've lost the auto-mount at insertion function, but that's no problem.

This works perfectly for me on 10.10 with a Dell e6420 - needed to pull some very old data off of 3.5 inch disks with a USB Floppy drive.

Thanks!

---

