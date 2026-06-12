---
title: "Command line installation - screen unreadable"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by Nick_C on 2012-02-06
Have done a simple command line only installation of 11.10 from the Alternate CD.  Text mode install all went well but on reboot the screen is unreadable.

I can however ctrl-alt-F1 into tty1 and the screen becomes readable.  Any suggestions.

Thanks,
  Nick

---

### Post by jerrrys on 2012-02-06
The only way in is tty.  Terminal (i.e. gnome-terminal) has not been installed yet.  If you are going for a GUI (desktop) then it should be ok when you get a desktop manager installed.

I have not encountered a problem like this with a terminal install, but you could try:

sudo dpkg --configure -a

sudo apt-get install -f

---

### Post by Bucky Ball on 2012-02-06
If you're online, inspired by jerrrys' post, you could just install a desktop environement. I would give code but it all depends on the DE you would like to install ...

---

### Post by Nick_C on 2012-02-06
So would something like the following be correct?
[INDENT]sudo apt-get install --no-install-recommends ubuntu-desktop[/INDENT]

---

### Post by jerrrys on 2012-02-06
> **Nick_C said:**
> So would something like the following be correct?[INDENT]sudo apt-get install --no-install-recommends ubuntu-desktop[/INDENT]

Guess that works; I use:

sudo apt-get install  --no-recommends ubuntu-desktop

Edit:  After you get your desktop installed;  do you want to loose the eye candy?

remove compiz and install gnome-classic (fallback)

---

### Post by Nick_C on 2012-02-06
Ok well ubuntu desktop now installed but still not much progress, obviously still a graphics problem: boot freezes at
[INDENT]* Stopping anac(h)ronistic [ok][/INDENT]
but graphics are all over the place.  Can still get to a tty terminal though.

Any other suggestions what to try next.

---

### Post by jerrrys on 2012-02-06
What kind of box/graphics do you have?

Will --configure -a give you any errors?

Did you checksum; check cd; burn at low speed?

---

### Post by Nick_C on 2012-02-06
Graphics card is an nVidia Quadro NVS295, CPU AMD Phenom II X6.

Not sure how to run your '--configure -a' comands.

Pretty sure I checked the DVD but will run 'check disk for defects' again...  now finished, integrity test successful.

---

### Post by jerrrys on 2012-02-06
[Graphics card is an nVidia Quadro NVS295]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=nVidia+Quadro+NVS295&sa=Search&cof=FORID:9")

Not sure how to run your '--configure -a' commands.  Run in tty (post #2)

[What about checksum?]("https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows")

---

### Post by Nick_C on 2012-02-06
sudo dpkg --configure -a
does not return any results so I assume that means no errors.

Can't do checksum at the moment because the only operating system I have at the moment on this machine is text only Ubuntu, unless there is a way of getting the checksum using that.

---

### Post by jerrrys on 2012-02-06
Yep, no news is good news.

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Linux](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Linux)

You can also try an update:

sudo apt-get update

Followed by:

sudo apt-get upgrade

If it has package to upgrade.  If offered, do not do a partial install.

[http://ubuntuforums.org/showthread.php?t=1641400](http://ubuntuforums.org/showthread.php?t=1641400)

---

### Post by Bucky Ball on 2012-02-06
Tried 'startx' from there? Any terminal will do.

---

### Post by Nick_C on 2012-02-06
> **jerrrys said:**
> Yep, no news is good news.

[https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Linux](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Linux)

You can also try an update:

sudo apt-get update

Followed by:

sudo apt-get upgrade

If it has package to upgrade.  If offered, do not do a partial install.

[http://ubuntuforums.org/showthread.php?t=1641400](http://ubuntuforums.org/showthread.php?t=1641400)

Thanks Jerry, update/upgrades done now.

Still cannot check original iso because it is on an NTFS partition and I have no idea how to connect to that from a copmmand line.

Still freezes but now at
[INDENT]PulseAudio configured for per-user sessions[/INDENT]

---

### Post by Nick_C on 2012-02-06
> **Bucky Ball said:**
> Tried 'startx' from there? Any terminal will do.

Interesting, startx brings up an LXDE desktop.  I thought I had removed that and installed basic ubuntu-desktop in it's place.

LXDE Update manager comes up with a list of updates which I am now installing.  Will get back to you shortly when this has completed...

OK now at position where we freeze at
[INDENT]Stopping System V runlevel compatibility [ok][/INDENT]

but if I go to tty1 and issue startx I get a graphical LXDE desktop, which is very surprising because I have removed LXDE.  This is something which had been suggested on a different thread.  Why is it still there.  More importantly how do I get rid of it and get back to the standard ununtu_desktop.

---

### Post by Nick_C on 2012-02-06
Latest update:

Have now done another completely fresh install of {edit - remove: Server} Alternate CD 11.10 command line only but this time also invoking the nomodeset install option.

Then installed the following
[INDENT]
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install nvidia-current
sudo apt-get install --no-recommends ubuntu-desktop
[/INDENT]

Now still freezes but can asscess desktop manually by startx, ok still need to get it to start automatically but at least some progress.

The first thing I notice about the desktop is that it is restricted to one screen only, any idea how to get dual screens working.

---

### Post by Nick_C on 2012-02-07
And today its has all gone wrong again, for no apparent reason that I can see.  Now after startx I get a blank screen, if I switch back to tty all I can see is a string of No Protocol Specified messages.

---

