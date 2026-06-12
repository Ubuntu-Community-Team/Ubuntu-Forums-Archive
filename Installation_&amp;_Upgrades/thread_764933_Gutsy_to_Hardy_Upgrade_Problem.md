---
title: "Gutsy to Hardy Upgrade Problem"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by pmendham on 2008-04-24
I have had Gutsy running on a Sony Vaio laptop with no problems.  I upgraded to Hardy today and now it won't boot using kernel 2.6.24.  It says:

Starting up ...
[   25.265141] ACPI: EC: acpi_ec_wait timeout, status = 0, expect_event = 1
[   25.265202] ACPI: EC: read timeout, command = 128

And then it hangs indefinitely.

If I try and boot using 2.6.22 (my Gutsy kernel) a bunch of stuff doesn't work, including my graphics and lots of stuff.  I can't launch the "Hardware Drivers" applet to be able to configure anything (it just silently dies).

Any ideas anyone? Any help appreciated. Completely desperate as my once lovely working machine is now a doorstop.

---

### Post by Partyboi2 on 2008-04-24
There is a bug report about it. ([https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/191137))
One of the solutions that worked for some was to remove quiet as a boot option.

---

### Post by pmendham on 2008-04-24
Great!  Thanks for pointing that out.  So now I can get it to boot by yanking out the power cord (I'll try removing the quiet option too).  But I actually still have the same problems with the 2.6.24 boot as I did with the 2.6.22 boot.  Whenever I try to do anything that should bring up a prompt for a password (is this gksu?) nothing happens.  An item appears on the taskbar for a little while saying "Staring Administrative Program" and then disappears leaving me with nothing.  The process list shows an instance of gksu and sudo, doing nothing.

I'm currently struggling with a ridiculous screen resoultion (800x600? 640x480?) because I can't launch the "Hardware Devices" applet, or anything else that might help me configure the graphics driver.

Any ideas?

---

### Post by pmendham on 2008-04-24
OK, I have new information.  sudo doesn't work.  It says:

sudo: unable to resolve host <my hostname>

If I check /etc/hosts it says:
127.0.0.1 localhost
127.0.1.1 <my hostname>.<my domain>
<Some IPv6 stuff>

Is this not wrong? (Second line) I can't try changing it as I don't have permission to write to it without using sudo :-|

Seems like a catch 22 to me...

---

### Post by Peter09 on 2008-04-24
this is to do with problems with your hostname.

There appear to be two fixes,

1. Change your hostname in /etc/hostname
to a single word.

2. in network manager under the hosts tab, put your correct hostname in 127.0.1.1

You may need to do this in safe mode as you cannot get rights in normal mode.

PC

---

### Post by pmendham on 2008-04-24
Thank you for your reply - that's great, I used recovery mode to edit the /etc/hosts file and sorted it out that way.  However, it seems like my problems aren't over yet :( I enabled the nVidia drivers, hoping that would take me out of 640x480, but it hasn't.  Although the drivers are enabled, the "Screen Resolution" applet is not allowing me to set a higher resolution.  Needless to say, the desktop is not massively usable in this state... ;)

Any ideas on this one?

---

### Post by Peter09 on 2008-04-24
In System->administration

you will find the nvidia settings tool. You might be able to set your resolution in there.

PC

---

### Post by ssj3strife on 2008-04-24
You could try manually editing your /etc/X11/xorg.conf file. There will be a section with a bunch of resolutions listed. The line will read something like:

	SubSection "Display"
		Modes		"1600x1200"	"1280x1024"	"1280x960"	"1152x864"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
	EndSubSection

Put the resolution you want in that format. X will try and use the resolutions in the order you specify. Hopefully that will do the trick for you.

---

### Post by pmendham on 2008-04-24
Thanks for the suggestions - I didn't have an nVidia applet on the menu, so I tried this:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)
which, after some messing around, seemed to work for me (I did the "Run the Autodetect Script Again" section)

Thanks very much to everyone who helped - I now have a system which works, and I only have the ACPI bug left, which I guess I can't do much about :(  Maybe wait for a fix...

---

### Post by ssj3strife on 2008-04-24
Did you try putting "noacpi pci=noacpi" as kernel arguments? Maybe that will help you, but you might lose some functionality too.

---

