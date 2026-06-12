---
title: "Ubuntu 10.10 Desktop has Udated to Server"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by wisie on 2010-10-13
This morning I upgraded my desktop Ubuntu to 10.10 and rather then updating to the desktop version, it has updated to the server version. 

I'm a little confused to how this has happened and *hoping* someone might be able to push me in the right direction to revert back to the desktop version without having to do a clean install.

Thanks and I appreciate any help :)

---

### Post by NightwishFan on 2010-10-13
Do not worry. There are really no separate "versions". They all share the same software repositories. What do you mean by "server" where does it say that?

[QUOTE="Ubuntu Server FAQ"]What's the difference between desktop and server?

    * The first difference is in the CD contents. The "Server" CD avoids including what Ubuntu considers desktop packages (packages like X, Gnome or KDE), but does include server related packages (Apache2, Bind9 and so on). Using a Desktop CD with a minimal installation and installing, for example, apache2 from the network, one can obtain the exact same result that can be obtained by inserting the Server CD and installing apache2 from the CD-ROM.
    * The Ubuntu Server Edition installation process is slightly different from the Desktop Edition. Since by default Ubuntu Server doesn't have a GUI, the process is menu driven, very similar to the Alternate CD installation process.
    * Ubuntu server installs a server-optimized kernel by default.
    * Ubuntu Desktop will receive 3 years of support, while Ubuntu Server will be supported for 5 years. [/QUOTE]

---

### Post by wisie on 2010-10-13
Thanks for the quick reply NightwishFan :)

I *think* it's the server as when it boots it now has a login screen saying Ubuntu 10.10 server and asks me to login. Previously it would boot straight to desktop.

---

### Post by NightwishFan on 2010-10-13
So you do not see the login screen, just a console? Either way run this command. This will ensure all the ubuntu desktop packages are installed.
```
sudo apt-get install ubuntu-desktop
```

If you have the problem where you are unable to see the login screen and just get a console run:
```
sudo apt-get install gdm
```
If that say "already installed" run:
```
sudo dpkg-reconfigure gdm
```
Choose "gdm" if prompted.

Run this command to find out which kernel you are running:
```
uname -a
```

If it says "generic" you are fine. If it says "server" do not worry it just means we need to install the generic kernel. The server kernel is fine for desktop use (i use it instead of the desktop one).

---

### Post by wisie on 2010-10-13
Once again thanks for the quick reply. :)

Both were already installed and upon reconfiguring gdm, nothing happened.

Linux server 2.6.35-22-generic #34 Ubuntu SMP is the kernel.

Any tips?

Cheerss

---

### Post by NightwishFan on 2010-10-13
Then you are using the desktop version. Is the console login your symptom? Try running:
```
sudo apt-get --reinstall install gdm
```

---

### Post by wisie on 2010-10-13
Oops. Server is actually my box name hence why I got confused.

After reinstalling, what next from there? I seem to be stuck in console.

---

### Post by NightwishFan on 2010-10-13
So you only have a console? Try running:
```
sudo start gdm
```

---

### Post by wisie on 2010-10-13
Yep only have console.

When entering that apparently gdm is already running.

---

### Post by NightwishFan on 2010-10-13
Press CTRL+ALT+F7, if that does nothing, press CTRL+ALT+F8, if that does nothing, run this:
```
sudo restart gdm
```

If THAT does nothing, try:
```
sudo stop gdm
```
Then run:
```
startx
```

Post any error messages here, if you can.

---

### Post by wisie on 2010-10-13
Thanks again for your help. I really appreciate it.

Upon running the last cmd I receive:

Fatal server error: 
No screens found.

Ixinit: No such file or directory (errno2): unable to connect to x server
Ixinit: no such process (errno 3): server error.

---

### Post by NightwishFan on 2010-10-13
Ok then that slims it down. What graphics card are you running. If unsure run this command:
```
sudo lshw -C display
```

Knowing what model it is will help later, run this command:
```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.nwbackup
```

Then try:
```
sudo kilall Xorg && sudo stop gdm
```
Then:
```
sudo start gdm
```

Does it work? If not reboot and see then.

---

### Post by wisie on 2010-10-13
Interesting. When running the first cmd I get: mv: cannoy stat '/etc/x11/xorg.conf': no such file or directory.

---

### Post by NightwishFan on 2010-10-13
It is case sensitive, use "X11". Though if you did that might mean you have no xorg.conf which is normal.

---

### Post by wisie on 2010-10-13
Same error unfortunately.

---

### Post by NightwishFan on 2010-10-13
I know something is stopping X from starting. I will need to know what type of graphic card you are using then. (Sorry no luck so far however we are getting closer to the root of the problem).

---

### Post by wisie on 2010-10-13
That's ok! I appreciate your persistance and help.

Description: VGA 
Product: N10 family integrated graphics controller.
Vendor: intel corporation
Physical id: 2
Bus info: pci@0000:00:02.0
Version: 02
Width: 32 bits
Clock: 33mhz
Capabilities: msi pm vga_controller bus_master cap_list
Configuration: latency=0


Excuse any typos. Writing this on my phone :)

---

### Post by NightwishFan on 2010-10-13
It is ok sorry to make you type so much. After this post I am going to the store real quick it will take 5 mins. I can still help when I am back.

Ok, this might be a toughy. I figured ATI card or malfored Xorg server... Not either, so looks like this might be a packaging issue. Did this happen after an update? Also is this a fresh install of 10.10?

Try fully updating the system:
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get -f install
```

Any errors? If so report them. After that run:
```
sudo apt-get --reinstall install ubuntu-minimal ubuntu-standard xserver-xorg-video-intel
```

Report any errors. If it is a lot of tying, just give the gist of it if possible. I will return shortly.

---

### Post by wisie on 2010-10-13
Okay no errors there.  After running the last command I was left with:

ldconfig deferred processing now taking place.

The problems started occuring once updating from the previous release to the current. Unfortunately i'm about to go to bed but will jump on in the morning. Thanks again for your help!

---

### Post by slakkie on 2010-10-13
It might be handy to post the contents of your X log file:

```

cat /var/log/Xorg.0.log
cat /var/log/Xorg.0.log.old

```

This will help in troubleshooting the issue :)

---

### Post by NightwishFan on 2010-10-13
He is on a phone, and that might prove hard. :) If possible please do so. Or something that jumps out at you as an error. I suggest for now disabling mode-setting to see if that helps.

Boot ubuntu holding shift until you see the grub menu, highlight the kernel you want and push "E". A bunch of text should appear. Find the line that starts with "linux" Add a space at the end of that line and then this: (**without quotes**) "i915.modeset=0"

Then push ctrl+x to boot. If that does not work as a temporary workaround, and perhaps to enable us to troubleshoot easier run this command (case sensitive):
```
sudo nano /etc/X11/xorg.conf
```

Should be a blank console text editor. If there is already text there, get back to us with the fact there is. If it is indeed blank type this _exactly_:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

Then press ctrl+x, and then Y when prompted to save. Then reboot with ctrl
+alt+delete.

---

### Post by wisie on 2010-10-13
We're back in action!

> **NightwishFan said:**
> 
Boot ubuntu holding shift until you see the grub menu, highlight the kernel you want and push "E". A bunch of text should appear. Find the line that starts with "linux" Add a space at the end of that line and then this: (**without quotes**) "i915.modeset=0"


This part didn't work but after moving onto the next part, the system booted to desktop as per usual.

However one slight problem. Upon placing the machine in my cupboard without a screen plugged in, I can't connect to the machine through tightvnc as normal. If I ssh the box and run 'x11vnc' I can connect. But it seems strange as I didn't have to run that before when connecting previously. Instead I had remote desktop setup in the preferences which worked fine. Any ideas what might be going on there?

Once again, thank you for all your help as I really appreciate it. Would have been incredibly lost without your help.

---

### Post by NightwishFan on 2010-10-13
I am fairly unfamiliar with VNC. Also the solution I gave is not great as a permanent one as you are using a generic vesa driver for the display (it does work though but probably slow). I do not know if that is why the vnc is not connecting and am unsure if that is why it is not conneting.

---

### Post by wisie on 2010-10-13
That's ok. Do you have any suggestions to make it a mor permanent fix? 

Thanks.

---

### Post by NightwishFan on 2010-10-13
Try changing the line that says:
```
Driver          "vesa"
```
To:
```
Driver          "intel"
```

---

### Post by wisie on 2010-10-13
Done.

Thanks again for all your help :)

---

### Post by NightwishFan on 2010-10-13
Does it all work now? In any case, it is no trouble at all, glad to help. :)

---

### Post by wisie on 2010-10-15
> **NightwishFan said:**
> Does it all work now? In any case, it is no trouble at all, glad to help. :)

Sure is :) Thanks again.

Must admit, I'm a little scared to update to the next version in case it happens all over again. I wonder what caused it? Could it be that I was updating without a screen plugged in (via remote)?

---

### Post by NightwishFan on 2010-10-15
Possible but I doubt it. For some reason it will not auto detect your screen without forcing it to use the right driver.

---

### Post by lordm on 2010-10-15
Thank you NightwishFan for your great help .. i had the same issue just one hour ago with my laptop after upgrading to Ubuntu 10.10
That solution worked great with me.

The problem now is just that my monitor is not detected and am having an 1024 x 768 resolution. Do i need to configure xorg.conf to the correct configuration of my laptop ??

P.S.: Nightwish are my 4th favourite band :)

---

### Post by wisie on 2010-10-15
I don't suppose you're using an Intel Atom based laptop? I wonder if it's a problem relating to their chipset.

---

### Post by NightwishFan on 2010-10-15
Yes, run:
```
sudo Xorg -configure
```

Then press alt+f2 and type (X is capital):
```
gksudo gedit /etc/X11/xorg.conf
```

Here are some tips:
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

Essentially edit this part:
```
Section "Screen"
    Identifier      "Primary Screen"
    Device          "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
    DefaultDepth    24
    SubSection "Display"
        Depth           24
        Modes   "1280x1024" "1024x768" "640x480"
    EndSubSection
EndSection
```

Make sure Device and Modes are correct for your hardware.

---

### Post by lordm on 2010-10-15
@wisie i'm afraid it is. It's HP Compaq 6720s

@NightwishFan Thx again for your great help :)

---

