---
title: "Desktop CD Download isn't exactly a CD"
date: 2008-06-19
forum: Installation &amp; Upgrades
---

### Post by Cyberpawz on 2008-06-19
Ok, now amuse me here, it seems to me that when i download the Desktop image into my Mac the image is 699.1 MB which is .08 MB smaller than 700MB.

When I attempt to burn the disk it says my 700MB CD that there isn't enough space.

Now riddle me this, how do we put a 699.1MB Disk Image into a 700 MB CD when the computer says there isn't enough space.

I don't think they make an 800MB CD, either way it is beyond the point, the Server (which is GUIless) fits on a CD, and this one doesn't...

Does someone else see the issue or is it just me?

How do I get it to burn into a CD on the Mac if Disk Utility says not enough space.

---

### Post by avtolle on 2008-06-19
I've had no problem with this, admitting I'm not using Mac Disk Utility. Is there an overburn option in the utility to allow burning?

EDIT: Which Mac are you using, and which release did you download (presuming 8.04, but just asking)? The size of the iso seems too large at first blush.

---

### Post by shad0w_walker on 2008-06-19
I'd suggest finding an alternative tool to burn the image as the disk utility clearly has some issues calculating space available. I would recommend a tool but I have no Mac experience (Little to expensive for my tastes) so I'll just bump the thread and let it get some more visibility

---

### Post by Dizzle7677 on 2008-06-19
> **Cyberpawz said:**
> 
Now riddle me this, how do we put a 699.1MB Disk Image into a 700 MB CD when the computer says there isn't enough space.


Extract the image to a 1-gig usb drive. 
[http://www.pendrivelinux.com/]("http://www.pendrivelinux.com/")
[http://syslinux.zytor.com/wiki/index.php/The_SYSLINUX_Project]("http://syslinux.zytor.com/wiki/index.php/The_SYSLINUX_Project")
[HOWTO][https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")

---

### Post by Cyberpawz on 2008-06-20
> **avtolle said:**
> I've had no problem with this, admitting I'm not using Mac Disk Utility. Is there an overburn option in the utility to allow burning?

EDIT: Which Mac are you using, and which release did you download (presuming 8.04, but just asking)? The size of the iso seems too large at first blush.


There is no overburn option, and when I try it on a PC (downloading it, and burning the image to disk, etc) it shows an image size of 715,200 MB, Which means to me that the image was compiled a little larger than required...

Although when I try overburning on a PC it freezes the program and drive, because I hit 98% and it craps out... so its close but no cigar.

---

### Post by Cyberpawz on 2008-06-20
> **Dizzle7677 said:**
> Extract the image to a 1-gig usb drive. 
[http://www.pendrivelinux.com/]("http://www.pendrivelinux.com/")
[http://syslinux.zytor.com/wiki/index.php/The_SYSLINUX_Project]("http://syslinux.zytor.com/wiki/index.php/The_SYSLINUX_Project")
[HOWTO][https://help.ubuntu.com/community/Installation/FromUSBStick]("https://help.ubuntu.com/community/Installation/FromUSBStick")


From a Mac?

---

### Post by Gewalop on 2008-06-20
> When I attempt to burn the disk it says my 700MB CD that there isn't enough space.

here are the steps

Applications > Utilities > Disk Utility

Then go to Images > Burn and find your ISO.


Didn't work?
go to some friend with windows and use

PowerISO , ImageBurn , Nero , ..... i don't there's alot

---

### Post by ScaredNoob on 2008-06-20
Might want to check out Xubuntu Hardy.  It's only a 544 meg download/burn. Could it be that you have one of the old-school 650 megabye cdr/rw's?

---

### Post by Gewalop on 2008-06-20
> Could it be that you have one of the old-school 650 megabye cdr/rw's?

Even that's might be possible , but it's like a million years ago, i mean i'm sure his grandpa will be mad for stealing his CDs

but, naaa, i don't think he has one of these

---

### Post by ScaredNoob on 2008-06-20
> **Gewalop said:**
> 
but, naaa, i don't think he has one of these

You don't think or you don't know?

---

### Post by CH1C0 on 2008-06-20
Just delete it and get the Alternate. :guitar:

---

### Post by Cyberpawz on 2008-06-20
> **Gewalop said:**
> here are the steps

Applications > Utilities > Disk Utility

Then go to Images > Burn and find your ISO.


Didn't work?
go to some friend with windows and use

PowerISO , ImageBurn , Nero , ..... i don't there's alot

Right, but the issue, and its simple is that when I attempt to overburn, my 700MB CD craps out because there is more than 702MB of data in the ISO


> **ScaredNoob said:**
> You don't think or you don't know?

I have a SuperDrive on both the Mac and the PC...at home it needs to burn a CD not a DVD because the computer I'm installing it on only has a CD player and that's it...

Company policy and all...

---

### Post by Cyberpawz on 2008-06-20
> **CH1C0 said:**
> Just delete it and get the Alternate. :guitar:

Aren't there things missing on the Alternate? Also isn't that a no GUI installer?

---

### Post by CH1C0 on 2008-06-20
> **Cyberpawz said:**
> Aren't there things missing on the Alternate? Also isn't that a no GUI installer?


But it would fit on a CD and you can get whatever you want for it later. But if don't want to use a non-GUI installer, I guess that's not an option.

I was very happy with TeenPup 2008 until I found Ubuntu, could give that a try. :guitar:

---

### Post by ScaredNoob on 2008-06-20
you could always start with the minimal net-install hardy cd which is only like 10 mb, there are great instructions for it and it's easy to add gnome-desktop ie (slimmer Ubuntu) after u install.  It has the same Amazing wired/wireless card detection as in full version.  Follow some instructions out there.  (in Hardy) minimal+graphicalvitals=faster boot time.

---

### Post by CH1C0 on 2008-06-20
> **ScaredNoob said:**
> you could always start with the minimal net-install hardy cd which is only like 10 mb

Yeah, then sudo apt-get install ubuntu-desktop

:guitar:

---

### Post by ScaredNoob on 2008-06-20
yeah yeah yeah!

---

### Post by Cyberpawz on 2008-06-20
> **ScaredNoob said:**
> you could always start with the minimal net-install hardy cd which is only like 10 mb, there are great instructions for it and it's easy to add gnome-desktop ie (slimmer Ubuntu) after u install.  It has the same Amazing wired/wireless card detection as in full version.  Follow some instructions out there.  (in Hardy) mininal+graphicalvitals=faster boot time.

That is in the download section of this site, or did someone develop it, because I asked if there was a way to download Ubuntu from the net, and people here said no.

---

### Post by ScaredNoob on 2008-06-21
not sure but when you google it and burn the iso it fetches (by default) stuffs from us.ubuntu.com (at least for me).

---

### Post by Dizzle7677 on 2008-06-21
> **Cyberpawz said:**
> From a Mac?

Why not from a Mac?

---

### Post by Cyberpawz on 2008-06-22
> **Dizzle7677 said:**
> Why not from a Mac?


Because it doesn't have the unix commands demanded for the process... beyond that no real reason.

---

