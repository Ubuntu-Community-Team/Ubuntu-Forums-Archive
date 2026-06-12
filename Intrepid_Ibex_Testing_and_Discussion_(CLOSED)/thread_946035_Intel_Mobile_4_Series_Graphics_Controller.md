---
title: "Intel Mobile 4 Series Graphics Controller"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bull205 on 2008-10-12
I have a sony vaio SR-165E and was running Hardy.  When I ran lshw, the output said that I had Intel Cantiga Integrated Chipset.  I upgraded to 8.10 Beta (with luck, the wireless networking works like a charm!) and now the output says that i have a "Mobile 4 Series Chipset Controller" instead of the Cantiga.

Also, my screen resolution only goes to 800x600 and it should be more than that (i think 1200x800, it's a 13.1 widescreen)

I am trying to get all the nifty desktop visuals and I can't enable desktop effects.  Where can I get a driver for this?  How do I find exactly who makes my driver?  Thanks

---

### Post by overdrank on 2008-10-12
Moved to Intrepid Ibex Testing and Discussion :)

---

### Post by bull205 on 2008-10-14
bump

---

### Post by Jim March on 2008-10-14
I spent hours wrestling with this on a friend's brand new Sony lappy.

Short form: you're screwed for at least a short time - with any luck the Intel driver support for this will be done by the time Intrepid goes live.

This particular video chipset is just too new.  Sigh.

Hmmmm...one thing you could try: supposedly there is a .deb file for the Intel 2.4 driver to get it working under Hardy.  The 17" screen on the Sony I was dealing with at 1600xsomedamnthing resolution was puking and dying in everything I tried, but just maybe Hardy plus that .deb will work on your setup.  Let's see if I can find the link...ah, here's one, slightly fractured English but not too bad :):

[http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/](http://melchiorre.wordpress.com/2008/07/31/driver-intel-240-deb-package/)

WARNING: because you have to operate at the command line with X just blown to hell and gone, you need some basic command line experience.  You have to download this .deb, then at a command line apt-get remove the i810 driver and then dpkg -i thisthing.deb.

Again: in my case it failed but that could be because of the monster resolution on that Sony or something wonky in BIOS (Sonys are turds that way sometimes).  At lower res your setup may be more standard than mine.

If you can get Hardy going at all, I'd do that and wait on Intrepid.  I have an Intel 965/X3100 and you'd think that would be more stable, and it is...but there's obvious video driver funkiness going on here and there, to a point I'd call it "barely working".  Intrepid is doing a LOT of video-related alterations...it ain't all sorted out yet, much less for a cutting-edge card.

---

### Post by bull205 on 2008-10-18
Um, great.  most of that post went over my head.  I am really enjoying Intrepid.  Wireless is fixed, which it wasn't in Hardy.  So I'm gonna stick it out and hope that development goes on with the newer chips in mind.  If I can help by posting anything I sure will.

---

### Post by psyke83 on 2008-10-19
> **bull205 said:**
> Um, great.  most of that post went over my head.  I am really enjoying Intrepid.  Wireless is fixed, which it wasn't in Hardy.  So I'm gonna stick it out and hope that development goes on with the newer chips in mind.  If I can help by posting anything I sure will.

Don't install the deb mentioned in the previous post (Intrepid already ships with the 2.4.1 Intel driver).

If you're limited to a 800x600 resolution and compiz doesn't work, then you're probably using the (generic) VESA driver. You should attach your /var/log/Xorg.0.log so we can take a look.

**After** attaching the log here, try:

```
$ sudo dpkg-reconfigure -phigh xserver-xorg
```

Log out and back in, and see if it helps.

---

### Post by AreonEpta on 2008-10-19
Give this a try to see if you can enable the drivers. I'm no pro, but I know this has solved plenty of my problems.

1. Go to "System-->Administration-->Software Sources"
2. Enter your password when prompted
3. Browse to the "Updates" tab
4. Mark "Pre-released updates (Intrepid Proposed)"
5. Click Close
6. Click reload
7. Go to "System-->Administration-->Synaptic Package Manager"
8. Look for updates
9. Install them
10. Reboot
11. Go to "System-->Preferences-->Hardware Drivers"
12. If there are drivers there for your graphics, then enable them. Now you should be fine. If not, I'm spent.

Hope that works for you.

---

### Post by psyke83 on 2008-10-19
AreonEpta,

The OP is using Intrepid, so your information won't help very much. During the development cycle, the security, backports and proposed repositories won't contain any packages - it is only after release they are used.

The Intel drivers are 100% open source. The Restricted Drivers Manager (jockey) only applies to the proprietary nvidia and fglrx graphics drivers, not intel.

---

### Post by AreonEpta on 2008-10-19
> **psyke83 said:**
> The OP is using Intrepid, so your information won't help very much.

Oops. Didn't know that it did no good for Intel. I just knew it worked for my wireless drivers and it may have worked for him, too.

---

### Post by bull205 on 2008-10-20
how do I...
> You should attach your /var/log/Xorg.0.log so we can take a look.

If i try to open it in the terminal with nano, it tells me it is a directory.

---

### Post by psyke83 on 2008-10-20
> **bull205 said:**
> how do I...


If i try to open it in the terminal with nano, it tells me it is a directory.

Don't paste it, attach it. Use the forum's Manage Attachments button and navigate to the file.

---

### Post by bull205 on 2008-10-25
It's telling me that it is not a format that can be uploaded.

---

### Post by kempo on 2008-10-26
Hello all,

I'm having exactly the same problem with my new Sony SR19XN. 800x600 is rubbish... here's my xorg.0.log file.

I've renamed it to a .zip to get around file extension and size limits.

Thanks for your help in advance...

---

### Post by kempo on 2008-10-26
Just in way of an update, having been scouring the 'net for information, a new intel driver package was posted to the universe respositories yesterday

[http://launchpad.net/~thjaeger/+archive]("http://launchpad.net/~thjaeger/+archive")

I've installed this (it make some changes to libdrm2), and i think it may help the issue... but...

how do i now edit xorg.conf to use these drivers?

Thanks guys!

---

### Post by kempo on 2008-10-28
Having spent a great many hours looking around... I stumbled across this guide

[URL="http://www.claudiocamacho.org/tech/sr11m_debian.php#graphics"]
http://www.claudiocamacho.org/tech/sr11m_debian.php[/URL]

which gives you the xconf.org settings required to get 1280x800 resolution using the vesa drivers.

This will suffice until the intel drivers are available/fixed.

Note that it's written for Debian. grub.conf doesn't exist in ubuntu - so edit /boot/grub/menu.lst instead.

---

