---
title: "Can't boot Gutsy live cd on Dell Inspiron E1705"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by bubbawv on 2007-10-21
I hoping someone will be able to offer some help.  I've tried booting several ways from my Gutsy live cd.  Regardless of what I try I get the following error after the display flashes a few time:

The display server shutdown about 6 times in the past 90 seconds.  It is likely something bad is going on.  Waiting for 2 minutes before trying again on display :0

After 2 minutes the screen flashes some more and the same error pops up.

Here is my laptop specs:
Dell Inspiron 9400 "aka. e1705"  (widescreen)
ATI Radeon X1400
1 GB Ram
2.0 Ghz Core 2 Duo

---

### Post by brunjes on 2007-10-21
Sorry to say, but welcome to the club. I posted a message several days ago for my T60 with ATI X1400 video card and got no responses that I saw (as of a day or so ago). 

I do believe you are suffering from "bullet-proof X" not being able to figure out your graphics card. Strange thing is, Ubuntu 6.10 can work well enough to give me 800x600 resolution at least. 7.04 could not handle it and neither can 7.10.

I am not upgrading until I see that ATI has released the latest driver 8.42 (8.41?). I hear it is any day now. I'm not sure how that will help though because what I see is the message you quote and when I press Ctrl-Alt-F1, I can log in in a terminal, but the characters are double high and double wide and I cannot see what I type until the command has executed and I press Return 12 times (literally 12 times). This means any script execution that is interactive (which the usual ATI installation script is) will NOT be helpful at all.

If I could put an nVidia card in my laptop, I would, but this is my company's machine and I cannot muck with it.

I wish I could offer real help and not just hope that either this gets fixed real soon now and in a way that does not involve executing scripts  -- wget, dpkg and such are fine, but not the ATI script which prompts you to select options -- if you cannot see the options without pressing return 12 times (and then it's too late -- you've responded incorrectly to some prompt 12 times by then), that type of "help" is no help at all.

---

### Post by Dreamglider on 2007-10-21
i have the same problem, neither 7.04 nor 7.10 will run :/

specs:
Dell Inspiron 9400
ATI Radeon X1400
2 GB Ram
2.0 Ghz Core 2 Duo

---

### Post by bubbawv on 2007-10-22
I did some searching today and came across some past threads for Feisty.  Here is what I was able to do to get the Live CD to boot (note:  you will need a wired network connection for this to work):
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm restart
```
You will have to execute the last line of code twice.  GDM will fail to restart on the 1st attempt.

I will be installing Gutsy later tonight.  I will post back when done to let everyone know how it went.

---

### Post by bubbawv on 2007-10-22
Ok here is how the install went.  After getting the Live CD to run the install completed as normal.  Upon reboot after the install I was prompted saying that the default video driver could not be found.  You can configure, shutdown, or continue.  None of these options will work.  At this point do not select any of the option.  You will have to switch to a new terminal (Shift-Alt-F1).  Log on as yourself and do the following:

```
sudo /etc/init.d/gdm stop
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
reboot
```

This will setup your video driver and once you reboot you will be good to go.  One odd thing you will notice, even though it will no prevent linux from boot.  When booting the screen will go black until you are prompted by Ubuntu for the user name & password.  I hope this helps.

---

### Post by entropic_existence on 2007-10-24
I haven't tried upgrading yet, but I know the solution with Feisty for the x1400 cards was to use the alternate install cd (text based install) instead of the Live-CD.

I was really hoping we wouldn't be having this issue again but it looks like we are.

---

