---
title: "Shutdown/Restart Freeze -- Why must K/Ubuntu's upgrades always break things?????"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by myke on 2008-01-07
Things have been going so well for the last few weeks.  Nothing broken.  Everything working smoothly.   Then as of last week following the latest 'security upgrade', my Kubuntu Gutsy laptop freezes on either shutdown or restart.   It goes thru the motions in the sense that the Kubuntu splash screen and horizontal scroll bar does it's thing ... but then it moves to an old (shudder) DOS style screen with the bottom line always reading something like "sending kill signal".    The screen freezes there.   

I've read several threads offering advice from changing the default session settings to altering part of the grub file to altering the kdrmc (i think that was the file) to fix the problem because apparantly it's pandemic.   However, nothing has worked.   It ALWAYS freezes whether I choose a restart of full shutdown.   The only thing I can do when it does freeze is tap the main power button ... don't even have to hold it down ... and the laptop shuts off.   The I have to do a normal start up with the power button.    I'm sick of this! 

When K/Ubuntu runs right .... it runs great ...  but every other time there is a minor upgrade and EVERY time I've moved from a Dapper to an Edgy or a Feisty to a Gutsy ... it's always a nightmare and breaks things left and right.

I love this distro.  Really I do.  I've used it since Breezy.  But the upgrade process has become horrendous.   Very buggy.

This shutdown/restart freeze problem sure as hell is a bug.   Unless ... of course ... someone has yet another possible solution I can try ... and I'm certainly willing to give it a go!!!

---

### Post by dgcoffman on 2008-02-26
I am having a similar problem since my (much delayed) apt-get upgrade this morning.

I'm running KDE4 on Kubuntu 7.10 2.6.22-14-generic (AMD64). 

Selecting either Shutdown or Restart from the menu or using reboot/shutdown etc from the console results in a blank screen and no power down.

---

### Post by miciurin on 2008-02-29
I have the same problem but with one notable difference: If I type in a terminal sudo poweroff or sudo reboot everything goes normally. If I choose the GUI buttons the computer hangs with a blank screen. 
This only happened after instaling Ati proprietary driver and compiz.

---

### Post by vivedekananda on 2008-03-15
it might be a problem with ati drivers, try:
[http://wiki.cchtml.com/index.php/Troubleshooting](http://wiki.cchtml.com/index.php/Troubleshooting)

---

