---
title: "Ubuntu 9.10 freezes"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by jrsc109 on 2009-12-14
I've searched, but can't see this anywhere, so apologies if this is repeating another post.

I have recently installed 9.10 as an upgrade.  The process ran smoothly, without issue, and the system boots up, again without issue.

However, for no apparent reason, at odd times, when I click a button on screen, the system hangs.

It also happens when I try to mount an external drive.

When it happens, I can't do anything at all.  Nothing I try 'un-freezes' it and I am left with having to switch off the PC at the on/off switch and re-start.

I am running a Dell Dimension PC, which has been running Ubuntu quite happily for nearly 2 years.  It is a dual-boot with WinXP (SP3)

I recently ran System Updates and ran, what appeared to be, a complete upgrade again!!

Again, this ran smoothly, and I was hoping it would include fixes for this.  It was not to be.

Please help, as I am considering reverting back is the only option.

I am extremely frustrated that I don't have a stable solution.

If you need any more information that will help you offer a suggestion, then please let me know.

Thanks in advance.

---

### Post by Joseph.M on 2009-12-14
Ive been having this problem as well with Jaunty right before i upgraded to Karmic Koala and its still freezing at random times, Usually when i click to go somewhere else.

---

### Post by loopiv on 2009-12-14
Same problem here, but with a fresh install of karmic (9.10).  There some people stating that it's firefox.  I'm not entirely sure because I see some kernel disk issues.  E.g., 
```

ata1: lost interrupt (Status 0x51)
ata1.01: qc timeout (cmd 0xa0)
ata1.01: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
ata1.01: cmd a0/00:00:00:00:00/00:00:00:00:00/b0 tag 0
         cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
         res 51/20:03:00:00:00/00:00:00:00:00/b0 Emask 0x5 (timeout)
ata1.01: status: { DRDY ERR }
ata1: soft resetting link

``` 
The whole system hangs and I cannot ssh into the box.  Do you see anything in your logs?  Maybe it some block driver error introduced with karmic?  Things were working fine for me with 9.04.

---

### Post by jrsc109 on 2009-12-14
Try this - change the COMPIZ_NAME to metacity

I did this, this evening, and so far no issues.
You'll probably need to start in Gnome-failsafe, which will not run somethings, but won't freeze, and then make the change.

Fingers crossed.

# Ubuntu specifc compiz-manager configuration file
# goes into /etc/xdg/compiz/compiz-manager
# works with git://anongit.compiz-fusion.org/fusion/misc/compiz-manager
COMPIZ_BIN_PATH="/usr/bin/" 
PLUGIN_PATH="/usr/lib/compiz/" 
#COMPIZ_NAME="compiz.real"
COMPIZ_NAME="metacity"

---

### Post by loopiv on 2009-12-14
I don't have compiz running (disabled earlier because of some other issues).  Anything disk related I could try?  I poked around with hdparm, but I don't think it made a difference (turned off 32-bit IO mode).

---

### Post by Lyleb on 2009-12-14
Sure fire cure. Ditch 9.10 and re-install 9.04. This apparantly is a new feature in Ubuntu, since Microsoft was so successful with the Blue Screen of Death, Ubuntu thought they would try something similar. I'm not buying it.

---

