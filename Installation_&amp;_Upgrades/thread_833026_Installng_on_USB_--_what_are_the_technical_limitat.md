---
title: "Installng on USB -- what are the technical limitations?"
date: 2008-06-18
forum: Installation &amp; Upgrades
---

### Post by randysparks on 2008-06-18
Hi

I'm experimenting with installing Hardy on a USB key stick. _I'm not actually looking for help with this_, but want to know what the technical problems are that makes it so tricky.

Most of the guides out there (or the liveusb software) create a persistent copy of the Ubuntu install CD on the USB stick.

I've tried using the Ubuntu installer to install straight to the keystick (setting the USB keystick for the GRUB boot loader) but it doesn't work. Why is this? Is it because, as I suspect, there's no master boot record on a USB key stick?

---

### Post by Pumalite on 2008-06-18
There is a MBR in the Pen Drive. You have to edit menu.lst after you've made sure that Grub gets installed to first partition of Pen Drive. I just did it on an 8 GB Flash Drive.

---

### Post by randysparks on 2008-06-18
> **Pumalite said:**
> There is a MBR in the Pen Drive. You have to edit menu.lst after you've made sure that Grub gets installed to first partition of Pen Drive. I just did it on an 8 GB Flash Drive.

So you're saying that it's possible to install Ubuntu to a USB stick, just as if it were a normal hard disk? 

What do you have to edit in menu.lst?

---

### Post by Pumalite on 2008-06-18
That's right. 8 GB would be best. You might make with 4

---

### Post by iheartubuntu on 2008-06-18
What would be th need for this? Certainly not for storing music. For storing files you wouldnt need an OS... sorry its too early in the morning for me to think.... OK, you can have your OS with all your settings, bookmarks, etc all in your pocket and stick it into any computer and boot into your OS... is that the plan?

---

### Post by randysparks on 2008-06-18
> **shirteesdotnet said:**
> What would be th need for this? Certainly not for storing music. For storing files you wouldnt need an OS... sorry its too early in the morning for me to think.... OK, you can have your OS with all your settings, bookmarks, etc all in your pocket and stick it into any computer and boot into your OS... is that the plan?

The main need is if you use a public computer that may be riddled with viruses/keyloggers. Stick in your USB Ubuntu and boot from it. Of course, you might have to request a wifi password, but that's fine. 

I use this when I go to my sister's house. Her computer has Windows on it and it's weighed down with all kinds of crap so it takes 10 minutes to even boot. I just boot from USB Ubuntu instead. 

Rescuing computers, too. Similar to a boot CD but you can add your own toolkit. You can also get files off the computer.

---

### Post by randysparks on 2008-06-18
> **Pumalite said:**
> There is a MBR in the Pen Drive. You have to edit menu.lst after you've made sure that Grub gets installed to first partition of Pen Drive. I just did it on an 8 GB Flash Drive.

OK, when I first tried to install to a USB key stick, I got no where. Once installed (I set GRUB to be installed to /dev/sdx1), it just froze at bootup after the self-testing. No mention of GRUB starting. 

I tried again, same settings, and this time it's worked.

I edited the GRUB menu to read (hd0,0) and it boots fine to the login prompt.

The only problem is that, after this, when I type my username/password, it freezes on a blank screen. 

Any ideas?  I've tried deactivating the swap file in /etc/fstab and also made a permanent mention of /dev/sda1, rather than the UUID for the root mount.

---

### Post by randysparks on 2008-06-18
I've tried every which way of installing Ubuntu Hardy to a USB stick.

It installs OK, via the standard installer, and then boots OK, but freezes after login. 

Switching to a virtual terminal shows everything is fine. I can login OK and all the /home files are in place.

I'm not the first person to find this, and I followed tips mentioned here (these tips are from during Hardy's beta):

[http://ubuntuforums.org/showthread.php?p=4766675#post4766675](http://ubuntuforums.org/showthread.php?p=4766675#post4766675)

... so I removed the .gnome2 directory. Still no dice.

I'm pretty sure that GVFS is causing this because it's getting confused about being on a USB device. But logging in with GNOME failsafe doesn't fix it either. 

Anybody got any ideas? Any guesses? I know about liveusb/casper installs, but that's not what I'm looking for. There's a bug in caspter's initfs right now that stops persistence happening too.

---

### Post by randysparks on 2008-06-18
It's a gnome-keyring bug. Looking at dmesg I see a lot of 

gnome-keyring-d: segfault at xxxxxx

---

### Post by Herman on 2008-06-18
:) Hello randysparks,
You should find the answer you're looking for in these two threads, [USB install from live CD]("http://ubuntuforums.org/showthread.php?t=827580") and  			[How to install ubuntu on USB drive and carry entire computing system in pocket?]("http://ubuntuforums.org/showthread.php?t=789528")

Regards, Herman :)

---

### Post by randysparks on 2008-06-18
> **Herman said:**
> :) Hello randysparks,
You should find the answer you're looking for in these two threads, [USB install from live CD]("http://ubuntuforums.org/showthread.php?t=827580") and  			[How to install ubuntu on USB drive and carry entire computing system in pocket?]("http://ubuntuforums.org/showthread.php?t=789528")

Regards, Herman :)

Thanks, Herman. That seems to have fixed it, particularly this message:

[http://ubuntuforums.org/showpost.php?p=4929429&postcount=4](http://ubuntuforums.org/showpost.php?p=4929429&postcount=4)

To summarize here, 

1) switch to a virtual console (Ctrl+Alt+F2)
2) kill the X-server (sudo killall gdm)
3. empty the /tmp folder (sudo rm -rf /tmp/*
4) Type startx, and then set the system to login automatically when the desktop appears (use 'System'-->'Administration'-->'login window -- bear in mind this program takes ages to start, another bug in Ubuntu 8.04)
5) Update as soon as possible -- apparently this is now fixed. 

Bugs, eh? Ubuntu has known a few.

---

