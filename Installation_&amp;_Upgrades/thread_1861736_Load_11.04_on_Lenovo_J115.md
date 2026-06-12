---
title: "Load 11.04 on Lenovo J115"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by pgh on 2011-10-16
Thanks to all the forum administrators who do great work helping out  everyone.  I write this to let people know how I got 11.04 to run on my  particular desktop machine and it was because of all the advice I read  on this forum and others that I was able to do it.

In short, the  problem was the "ondemand" service.  Whenever it ran, it locked up my  machine.  The lockups occurred within 30 to 45 seconds after I logged  into the machine.  That's why this was so maddening; you would get to  the desktop, use it for a few seconds and the machine would lock up  tight as a drum.  Yet it would run fine in single-user mode.  (ondemand  doesn't load until you go multiuser.)  The vast majority of  lockup/freeze/stop behavior discussed on these forums points you towards  the x11 software and video issues.  In this case, that advice was  wrong.  (Which is why I'm writing.)

If you want to install Ubuntu on a Lenovo 3000 Series J115 (7387-26U) tower computer successfully:

1.  Do NOT download the standard version.  You must use the alternate  installer version.  If you want 64-bit (my choice), then you want the  amd64 version.  I used the desktop version, not server.

2. After  your installation is complete and you get to the desktop on Linux (my  display -- the flat panel that came with my J115 -- would not display  Unity, so I used Gnome), there is a pretty good chance the machine will  lock up and be unresponsive.  You will have to power cycle it to get it  to restart.

3. When you restart, hold down the SHIFT key on your  keyboard and the machine will boot into the recovery mode.  On the  choices that appear, select the second one (the one that says recovery  mode at the end) with the arrow keys on your keyboard and hit ENTER to  run that.  In the window that appears, scroll to the bottom and select  the last item, so you boot into a command-line interface.

4. When  the command line appears at the bottom of the screen, run  sudo apt-get  rcconf  (this is the Debian runlevel configuration tool).

5.  When rcconf is downloaded and installed, run it from the command line by  typing rcconf.  You will get a list of services available on Ubuntu.   Each entry has right and left brackets before the name.  The ones at the  top of the list have asterisks between the brackets; that means they  are going to run when you log in normally.  The ones that do not have  asterisks will not be loaded.  Find the entry for ondemand.  Move your  cursor down the list until the asterisk between the brackets is  highlighted, then press the SPACE bar.  That will remove the asterisk  from between the brackets.  Hit the TAB key so the <OK> choice at  the bottom is highlighted and press ENTER to save your change.  You may  see some grouchy error message, but that's OK.

6. You should be back at the command line now.  Type shutdown -r now   and hit the ENTER key.  The machine will reboot.

7.  You probably will return to the recovery mode screen again.  This time,  hit ENTER on the first line to run a normal session.  When the desktop  comes up, log in and enjoy Ubuntu.

Two final notes:

1. I  am not a Unix/Ubuntu/Linux expert.  I just read the forums, locked up  and rebooted my machine about 60 times until I figured this out.  That  means, I can't help anyone else with their problems because this was my  experience and I wanted to help others who might have the same problem.   We all kick the can a little further down the road and this is my  attempt to do that.

2. I bought this machine about 5 years ago  and it ran XP quite well, even with only 1 GB of RAM.  I only took it  out of service because I got an incredible deal on another machine and I  wanted to put Linux on the Lenovo because XP is going to be dead soon.   My machine now has 4GB RAM, a dual-core Athlon CPU, and a 250 GB  drive.  What was essentially scrap is now a pretty decent machine,  thanks to Ubuntu and the open-source community.

Good luck, everybody.

---

