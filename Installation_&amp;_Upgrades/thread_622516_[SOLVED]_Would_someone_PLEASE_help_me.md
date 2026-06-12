---
title: "[SOLVED] Would someone PLEASE help me"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by netsurfau on 2007-11-24
I posted this problem a week ago and haven´t received any help at all. :confused:

I upgraded my old system to gutsy and after rebooting am unable to get back in.

System boots properly, gets to the Gnome login screen, I put in my UN+PW
and then all I get is a pale blue screen with a black mouse curser. Nothing
happens after that.

Sys is an AMD XP2800+ with 1Gb of RAM.
Is dual boot & Grub loads & works properly.

The upgrade was done on-line.
ie; Performed upgrade using Ubuntu&#347; built-in ¨Update Manager¨.

Let it do it&#347; thing overnight, then rebooted in morning.
Prob appeared straight after entering UN+PW.

I get no error messages or anything else other than, the system hanging at this
pale blue screen with the black mouse arrow which I can move around.

Would someone PLEASE help me (it sucks no end when your problem is ignored)

---

### Post by mmmichael on 2007-11-24
I'm no expert, but it sounds like it might be a problem with xorg. I would try booting from a live cd and, assuming gnome gets up and running properly, try:```

sudo mkdir /media/disk
sudo mount -t ext3 /dev/hda1 /media/disk
```
This mounts your hard drive, just substitute your actual root partition for hda1.
```
sudo cp /media/disk/etc/X11/xorg.conf /media/disk/etc/X11/xorg.backup
```
This creates a backup of your xorg.conf.
Then copy the working xorg.conf from the live session:
```
sudo cp /etc/X11/xorg.conf /media/disk/etc/X11/xorg.conf
```
then reboot from your hard drive.
Again, I'm no expert, but this is what I would try.

---

### Post by netsurfau on 2007-11-24
Thanks Michael,

Have to D/load a copy of the Live CD.  After I´ve burnt it, I´ll try your suggestion
and let you know how I went.

---

### Post by willca on 2007-11-24
When you get the initial login screen. Instead of logging into that. Press ALT-F2 or CTRL-ALT-F2 (not sure its been a while)  to get a CLI login prompt. Go in via that and check your xorg.conf.

---

### Post by linux noooob on 2007-11-24
thats happened to me too see what happened was i installed a debain partition for a little experimenting but it seems it clung to my swap and Ubuntu didn't get any and therefor didn't load. so you may want to check the partitions on gparted in the live cd.

---

### Post by netsurfau on 2007-11-25
Live CD seems to get to the same point and ¨hangs¨.

Only minnor difference was I could hear the ¨loading¨ wave file but, it was brocken up.

I´ve got a copy of the ¨Alternate¨ install CD, might try a repair.

Let you know how it goes.

---

### Post by netsurfau on 2007-11-25
¨Spoke too soon¨

I´m running two systems through a KVM switch & when I went back to the sys with 
booting problem, I had the Live CD desktop.

Will try Michael´s suggested fix.

---

### Post by netsurfau on 2007-11-25
Wilca - Thanks helped me get in to check xorg.conf (BTW: CTRL-ALT-F2 worked)

linux noooob - went through xorg.conf & couldn´t find any (obvious) errors.

All the different entries were correct for the H/ware setup of the system.

Now, I might try the Repair Install on the Alternate Install CD.

Keep you all posted.

---

### Post by netsurfau on 2007-11-25
Tried to run a repair.

Unfortunately, all the help does is give you a list of available commands & now
other info on what you´re supposed to do with them.

Does anyone out there know how to actually run the Rescue from CD??

So, I´m still stuck with the same issue.  

Could it be a problem with Gnome?  I was able to log in via CLI and move around
within the contents of my drive.  Ideas??

---

### Post by ubukool on 2007-11-25
I would burn the Live CD at a slow rate to make sure there are no errors on it, and then try again to see if you can get the Live CD to boot successfully.  If so, then I would start with a clean install.  I believe they are thinking of making it possible to retain your /home directory with the next release (Hardy Heron), but you could move your /home directory to its own partition so that you don't have to go and reinstall and customise so much stuff if you start from clean install in the future.  Here's how to do it:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Good luck! :)

---

### Post by mmmichael on 2007-11-25
Before you try a complete reinstall, try CTRL-ALT-F2 then
```
sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop

```

---

### Post by netsurfau on 2007-11-25
Hi Michael,

Pardon me if I take a day or so, to get back to you.  This is the last week of the semester
and I have three assessment items to get in.  One today, one Wednesday & one on Friday.

Will post result as soon as I get a chance to do it.  Am currently in XP partition on same sys
to get work done.

---

### Post by netsurfau on 2007-11-26
Michael,

**_You are a genious!  The last thing you asked fixed the problem._** =D>=D>

After going to a CLI login, I logged in as "root" and then ran 'apt-get remove ubuntu-desktop'.
This came back with the message: "dpkg was interrupted, you must manually run 
'dpkg --configure -a' to correct the problem"

So obviously I ran that command, & other than having to answer a few questions about whether
I wanted to update about three packages, it seemed to almost replace most of the OS.

I tried logging in normally after this but, got same reult as before.

Rebooted, went back into CLI & logged in as root.  Then ran the second command (apt-get
install ubuntu-desktop), which "did it's thing". Rebooted sys again, logged in as myself with
the usual graphical interface and it came up with my desktop, as good as before the upgrade.

Thank you.  You have been a "life saver".

Regards
Luke

---

