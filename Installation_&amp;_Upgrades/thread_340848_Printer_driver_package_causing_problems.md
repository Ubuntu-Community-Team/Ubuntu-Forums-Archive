---
title: "Printer driver package causing problems"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by dewm_solo on 2007-01-17
Good evening to all,

I am in need of help from you guys.

A couple of nights ago I was looking up for directions on mapquest and wanted to print the map. My printer, a Brother HL-1435, always worked fine, but gave me hell that night.

I let it all go and decide to go to bed. Come back to it in the morning and figure I should reinstall the bugger. Ubuntu couldn't find it again though. So I thought that maybe reinstalling the driver would help.

Found a new package on the Brother website and proceeded to installing it...... *Now that didn't work as expected.*

I ended with an error saying that it couldn't complete the install, but it left it half installed in a way that keeps me from using apt-get or any package utility that's on the system. 

The message I have now is :
*The package hl1430lpr needs to be reinstalled, but I can't find the archive for it.*

Can someone guide me please?

Thanks for your help.

---

### Post by dewm_solo on 2007-01-18
Could anyone help???

---

### Post by dewm_solo on 2007-01-18
Good evening all,

I really need help with this....I can't remove or install anything without getting this message. 

Basically ....I cannot do anything with my installation. I mean I can use what's already on my machine, but I cannot add or remove....I cannot even update anymore.

---

### Post by dewm_solo on 2007-01-18
Googling my message lead me to a similar reported problem with jedit.

The problem in that case was solved by running this command:

```
sudo dpkg --remove --force-remove-reinstreq jedit
```

So I adapted to my problem:

```
sudo dpkg --remove --force-remove-reinstreq hl1430lpr
```

Unfortunately .....it didn't work in my case....here's what was spit back at me:

```

dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 122435 files and directories currently installed.)
Removing hl1430lpr ...
/var/lib/dpkg/info/hl1430lpr.postrm: 3: /etc/init.d/lpd: not found
dpkg: error processing hl1430lpr (--remove):
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1430lpr

```

Can someone help me with this?

---

### Post by dewm_solo on 2007-01-18
WOOHOO....I am the king of kings.....
SOLVED !!!!!!!
```
sudo dpkg --remove --force-remove-reinstreq hl1430lpr
```

Worked:

```

dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `hl1430lpr' missing, assuming package has no files currently installed.
122434 files and directories currently installed.)
Removing hl1430lpr ...

```

First I had to remove all of the files related to 'hl1430lpr' from:
```
/var/lib/dpkg/info/
```

---

### Post by timdoc1 on 2007-06-06
YOu may be a genius, but  Iam not  Yes I am a noobe.  Would any care to guide me through this Brother MPC-3320CN install.

I D-clicked on the driver file I downloaded from brother and the PAckage Installer asked me if I want to re-install?  Yes, I clicked it before, so this time I accepted the "Reinstall option". Nowit says install complete but in the screen below it says...

"Preparing to replace mfc3320cnlpr 1.0.4-1 (using .../mfc3320cnlpr-1.0.4-1.i386.deb) ..."


I try to print and I get nothing.  No test page etc.


Now,  I also tried to install the cups driver too.

If I go to System and the Administration Drop-Down and selct Printers and Install Printer.  I see it detects my USB printer, but unfortunately when I am prompted to choose driver form a list my printer model is not available.  Boo Hoo!!!  Can someone enlighten me?

---

