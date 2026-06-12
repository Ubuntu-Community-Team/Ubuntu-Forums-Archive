---
title: "Ubuntu on Dell Inspiron 8600 Laptop Problem"
date: 2013-09-07
forum: Installation &amp; Upgrades
---

### Post by novice_penguin on 2013-09-07
I'm wondering if anyone here has tried/completed an installation of Ubuntu 12.04LTS on a Dell Inspiron 8600?  I tried to DL from a live cd and everytime, the laptop becomes unresponsive about 5 minutes into installation.  I wake the screen, which takes a solid minute to do so, and then I have to very quickly, select the dl icon on the desktop.  At this point, the circle appears, as if it has started the action, then I get horizontal lines across the top of the screen and nothing happens, except that the desktop disappears.  This isn't my primary computer, my desktop is, but I need this laptop to work for my other projects.  It still has Windows XP, because I haven't even made it to the step to do a clean install of Ubuntu.  Also, I know my video card and all other hardware is working correctly, because I can still use XP with no problems.  If anyone can help, I would greatly appreciate any suggestions.  Thanks!

---

### Post by sanderj on 2013-09-07
Isn't that a 2003 laptop? And: how much RAM?

I would start by using Lubuntu 12.04, not Ubuntu.

---

### Post by novice_penguin on 2013-09-07
Yes it's an old laptoo but I'm too cheap to buy a new one, especially if it's not broken.  It has 2 G of ram.  Thanks for th3 suggestion.   I think I'll give Lubuntu a try!

---

### Post by sanderj on 2013-09-07
> **novice_penguin said:**
> Yes it's an old laptoo but I'm too cheap to buy a new one, especially if it's not broken.  It has 2 G of ram.  

Indeed: nothing wrong with older hardware. That is, as long as you run the "fitting" software on it. Lubuntu is great for low/lower spec CPU's.

The 2GB RAM is great.

---

### Post by sudodus on 2013-09-07
Have a try with the OBI, and do the only right thing with that old computer, use the whole disk for a suitable version and flavour of Ubuntu :-)

There is a new alternative to install Ubuntu based operating systems  into computers of various age and kind, the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"), the 'OBI'.

The OBI is designed to be easy to use and have a very small foot-print  and uses only standard programs and shell-scripts in text mode.  Installed systems with non-PAE kernels or fake-PAE are portable between  many computers, and they are stored in compressed tar archive files, ***tarballs***.

```
GnomeClassic1204-oem.tar.gz
GnomeClassic1204.tar.gz
lubuntu-10.04.tar.gz    # good for old systems but past end of life of desktop packages
Lubuntu_13.04sept1.tar.gz
lxle-2013-08-19.tar.gz
OneButtonInstaller_blank-noswap.tar.gz
saucyalfa2.tar.gz
saucybeta1.tar.gz       # new 
ubuntu-10.04.tar.gz     # good for old systems but past end of life of desktop packages
```

The OBI helps you make such a tarball of your own system and use it as a backup or to port the system to another computer.

---

### Post by sudodus on 2013-09-07
See also this post comparing different versions and flavours

[http://ubuntuforums.org/showthread.php?t=2130640&page=2&p=12769646#post12769646](http://ubuntuforums.org/showthread.php?t=2130640&page=2&p=12769646#post12769646)

Furthermore, what graphics chip is there? Someone with the same or similar chip/card may be able to give advice.

---

### Post by mörgæs on 2013-09-07
When you have something Buntu installed please run

```
sudo lshw -sanitize > lshw.txt 
```

and post lshw.txt in CODE tags. It will allow us to (maybe) give an even better suggestion.

---

### Post by novice_penguin on 2013-09-09
Thanks for all of your help.  Unfortunately, the problem persists, except now, I don't even have my previous XP, which was working fine.  I thought I had the problem solved by installing Ubuntu 11, from an old CD that I have, and the prompts were going full speed ahead, it even allowed me to boot over XP.  Now, I have no functional OS and I'm about to just give up.  I have tried Lubuntu 12.04, Ubuntu 12.04, and Ubuntu 11 something.  Also, the disk isn't being read when the computer is restarted.  I have to manually boot from the CD if I want to try to install a different OS.  Ubuntu 11 worked, except when I log in and go to the desktop, the lines that I previously saw on my screen return, but only once I log-in.  The log-in screen looks flawless.  Should I just give up or is there a fix?

---

### Post by novice_penguin on 2013-09-09
@Sudodus:  The graphics chip is AGP 4x - ATI Mobility Radeon 9000 - 32.0 MB DDR SDRAM.  I also made a mistake about the RAM, it's only 512MB.  I thought I bought the max 2G RAM for my wife a while back (it was her laptop).  So, I know Ubuntu probably won't work, but I thought Lubuntu would surely work......

---

### Post by sudodus on 2013-09-09
I have nvidia Riva graphics in my old Dell. There might be a problems with the Radeon graphics. Lubuntu should work with 512 MB.

A. Try to run it ***live*** (booted from the Lubuntu desktop iso without installing). If it runs live, it can also be installed, but you may have problems with the desktop installer with only 512 MB RAM. So after testing live, you could try to install with

1. the Alternate ISO Installer or

2. the One Button Installer.

B. If the live session will not bring you to a graphical desktop environment, try the boot option ***nomodeset*** and some of the other boot options too. See this link

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by mörgæs on 2013-09-09
> **novice_penguin said:**
> Also, the disk isn't being read when the computer is restarted.

This should work regardless of operative system. Have you changed settings in BIOS?

Which BIOS version are you using, by the way?

---

### Post by novice_penguin on 2013-09-09
Problem solved.  Xubuntu 12.04 installed successfully.  What a nightmare.   Thanks for all of your help!

---

### Post by mörgæs on 2013-09-10
Good, please post the solution, as this will benefit other users, and mark the thread 'solved'.

---

### Post by novice_penguin on 2013-09-10
The solution was to pick an OS that's compatible with 512mb ram.  Xubuntu 12.04 requires that but I will be upgrading to 2 gb ram after this fiasco.  The reason I was trying to install an OS that required more ram was because I mistakenly thought I upgraded to 2 gb when indeed I haven't.   Like I said this is an old computer that I haven't used in a while.   Thanks for the help!

---

