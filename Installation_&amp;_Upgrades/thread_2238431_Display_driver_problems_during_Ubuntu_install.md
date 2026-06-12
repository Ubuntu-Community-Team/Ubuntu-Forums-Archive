---
title: "Display driver problems during Ubuntu install"
date: 2014-08-07
forum: Installation &amp; Upgrades
---

### Post by the-z-469 on 2014-08-07
Hey all,

So I was installing 14.04 LTS on my XPS M1710 laptop and about halfway through the installation the screen display began to crap out on me. I have a Geforce GO 7800 graphics card and had previously updates the drivers. When I restart the computer I'm able to see the BIOS and get into the settings and boot options, but once it gets to actually trying to run the OS I'm no longer able to see, I get a nice black and white striped screen.

I was able to start up in recovery mode which let me into the terminal but I don't know what to run in order to fix my issue.

I'm still a newbie with Linux so I was wondering if there is a way to determine if this is a hardware problem or not, and if not what my next option should be.

Thanks for any help.

~Jester

---

### Post by yancek on 2014-08-07
What did you previously update the drivers on?  Your installing it from a DVD/flash drive, right?  Are you getting the black/white striped screen from an installed system or are you still in the installer?

You could try adding nomodeset to the linux line on boot

---

### Post by the-z-469 on 2014-08-07
I previously updated the drivers while running Debian Wheezy.

 I was in the installer when it first started having problems with the display. You can notice some "graphical discrepancies" in the BIOS boot up. I was installing Ubuntu 14.04 from a DVD.  After seeing this I thought maybe I had a bad DVD so I moved back to a Zorin OS 8 DVD that I had used to install the system on another laptop I have that runs fine. During the Zorin OS 8 install, the display will seem to fix itself and will properly render the graphic for the Zorin OS logo, but once it gets to showing a system menu (or whatever the next step of that was) it will revert back to the black and white striped screen.

I've also tried restoring default BIOS settings just in case I had changed something, but it was to no avail.  I've had this problem with this laptop before, but I was able to get into the OS and properly update the driver. This was a few years ago when I install Ubuntu 12.04.

I'm sure I'm missing something simple here.

---

