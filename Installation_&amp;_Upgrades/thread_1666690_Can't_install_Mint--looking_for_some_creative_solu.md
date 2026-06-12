---
title: "Can't install Mint--looking for some creative solutions"
date: 2011-01-14
forum: Installation &amp; Upgrades
---

### Post by gringo guy on 2011-01-14
I've got a no-brand PC that I've been trying to put Mint on for a couple of weeks, but the ubiquity installer refuses to work on this machine. The alternate Ubuntu install CD worked great, so I've got 10.10 running. 

For several reasons, I'd *really* like to get Mint 10 working on this PC--posting on the Mint forums didn't help, so thought I'd try over here. Any suggestions would be greatly appreciated! Is there a way to install the Mint 10 desktop and menus on top of Ubuntu?
Thanks! 


From the Gory Details Dept: I get the nasty "[Errno5] Input/Output error" during the file copy process, and have tried various things to get this working including this list from [a defect that I filed]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/700208") against ubiquity: 
.  replaced an old CD ROM drive with a new CD/DVD RW drive 
.  burned the CDs and DVDs at a slower speed
.  burned a DVD on the same drive used to run the install
.  ran badblocks with write mode on the failing partition
         (found 1 bad block, which was added to the BBT)
.  ran memtest through several passes
         (found "block move" errors, so swapped memory DIMMs)
.  re-ran memtest through 10 complete passes
         (no further memory errors were detected)
.  removed half of the installed memory (per other posts)
.  confirmed that the computer was not overheating

Also tried installing from a LiveUSB.

The same "Errno 5" also occurs when trying to install Mint 9, Ubuntu 10.04.1, and Ubuntu 10.10. Of course I check the MD5 hashes and, in all cases, have successfully installed from each ISO to a VirtualBox on my primary PC. Only the alternate install CD that does not use the ubiquity installer has worked successfully on this box.

---

### Post by 71GA on 2011-01-14
maybee mint has some sort of a bug... try to google for your error report.

---

### Post by amsterdamharu on 2011-01-14
You tried starting Mint in compatibility mode and then install?

Did you mean you could only install the 10.10 alternate install disk?

You got 10.10 installed but you say 10.10 gives you an error5 as well.

---

### Post by gringo guy on 2011-01-14
@[71GA]("http://ubuntuforums.org/member.php?u=971474") - everything that I have been able to find points to problems with ubiquity. 

@[amsterdamharu]("http://ubuntuforums.org/member.php?u=898154") - trying just now, compatibility mode fails sooner than non-compat mode.  It doesn't even get to the file copy stage. And yes, only the non-ubiquity alternative install CD works to install Ubuntu on this PC, but that works great.

---

### Post by amsterdamharu on 2011-01-14
One way of trying to do this would be to add the mint repo's and install the mint menu and some other mint specific packages but I would not know if this would work well.

For a live mint CD you could try to start ubiquity with some options:

[http://www.linuxcertif.com/man/8/ubiquity/](http://www.linuxcertif.com/man/8/ubiquity/)
press alt + F2 and type "ubiquity --debug **--no-migration-assistant**" then click run
[COLOR=Red]*Note that passwords will be logged in debugging mode!*[/COLOR]
If the installer drops you into command prompt you could copy the debug files to a usb stick and post them
I assume you have one harddisk and sdb is the usb disk with 1 fat formatted partition to copy the files to.
```
sudo mount -t vfat /dev/sdb1 /mnt
sudo cp /var/log/installer/debug /mnt/
sudo cp /var/log/syslog /mnt/
sudo cp /var/log/partman /mnt/
```

---

### Post by jackharvest on 2011-01-14
Ah, you're in luck! You CAN install the Mint 10 menu and desktop into Ubuntu...

[http://www.ubuntugeek.com/how-to-install-mint-style-gnome-menu-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-mint-style-gnome-menu-in-ubuntu.html)

---

### Post by amsterdamharu on 2011-01-14
Sorry, I see I forgot to post my /etc/apt/sources.list
```
deb http://packages.linuxmint.com/ isadora main upstream import
deb http://archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse
deb http://archive.canonical.com/ubuntu/ lucid partner
deb http://packages.medibuntu.org/ lucid free non-free
```

I use isadora based on lucid so you might have to change that.

---

### Post by gringo guy on 2011-01-14
@[jackharvest]("http://ubuntuforums.org/member.php?u=927482") - brilliant, this is great. thank you! 

@amsterdamharu - installer still crashes, but at least got some better details this time.

First try: I also added the '--only' option but using this ubiquity wouldn't even start. Then tried your option list without the '--only' but still wouldn't start. 

Second try: rebooted and tried your option list. Ubiquity started but after selecting language and clicking [Forward] it failed with a 'ubi-partman crashed with exit code 10' message. This time it actually included a python trace in a 2nd dialog window. First time I've seen that. It's the same info that at the end of the installer/debug log file.

---

### Post by amsterdamharu on 2011-01-15
The sys.log has a whole bunch of "SQUASHFS error: squashfs_read_data failed to read block"
Suggesting that the squasfs is corrupt but as you stated before you used several different media and checked the MD5 hashes.

I found this page
[https://help.ubuntu.com/community/SquashfsErrors](https://help.ubuntu.com/community/SquashfsErrors)

suggesting you can add
```
ide=nodma acpi=off
```
acpi=off is already part of the try in compatibility mode but the other one can be added manually by pressing tab to edit when in the boot menu.

The strange part is that you can boot into a live session (that uses the squasfs file) only to get a message that the squashfs file is corrupt during installation.

You did boot into live session and tried installing clicking the icon on the desktop did you?

The alternate does not use a big squashfs but downloads the packages needed during installation (last time I tried was with Hardy so not sure if this still is the case).

---

### Post by gringo guy on 2011-01-26
Hey, amsterdamharu, thank you for looking at this and sorry for not replying sooner! I didn't see that you'd added something. 

Okay, tried adding the 'ide=nodma' option to the compat boot entry (as you said, 'noapci' was already added). Same thing: Ubiquity aborts during file copy, and there are squashfs errors in syslog. 

Yes, strange indeed and yes, I do boot into a live session and then click the icon on the desktop to start the install. Starting a terminal window works, both before and after ubiquity aborts, but I haven't tried running anything that's memory intensive. 

Ubuntu is installed and, thanks to jackharvest, the Mint menu is working great. However, I may try getting a 1GB DIMM for this. . . maybe there's a problem with how video is stealing 64MB from RAM. Or I might try a graphic card with some on-board memory. Can't hurt to try, and the upgrades would make the system a little nicer. 
Thank you again,

---

