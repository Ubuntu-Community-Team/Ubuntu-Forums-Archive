---
title: "After reinstall system lock and is unusable"
date: 2012-03-10
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2012-03-10
Hi I have a 64-bit AMD, 16G RAM, with nVidia graphics card PC running 11:10 and 2 monitors.  I also have the HOME Directory separate from the rest of the install to protect and isolate it.

Originally I upgraded from 32-bit (an error as the stock CDs are not marked), which worked well, but I started to get a few issues (as pe other threads), so I decided today to do a new install, this time with the correct CD - 64-bit.  It took 2 goes.

I had the usual issue on 64-bit where the graphics were throwing up alarms because it had used the "recommended" additional drivers for the screen.  I set up the nVidia config to get the two screens and then removed the drive, this then made the built in driver work - do not know why but it seems to work for me.

What I have found is some key apps are missing, like Synaptic
All windows seem to open in the top left hand corner with the control panel outside the screen area, so I have no way of moving it or doing anything unless I hard reboot the machine
When I open a directory or document the machine freezes
Some apps will not start, such a Ubuntu Software Centre, Evolution, etc....

Can anyone help me out here please?  I need this for work on Monday and need to get a CV out tomorrow.

---

### Post by kansasnoob on 2012-03-10
Just noticed your PM so I gave this a look. Sadly I'm totally clueless here as I've never set up a dual-monitor rig :(

Sorry, maybe the free bump will get some fresh eyes looking.

---

### Post by Jonners59 on 2012-03-11
> **kansasnoob said:**
> Just noticed your PM so I gave this a look. Sadly I'm totally clueless here as I've never set up a dual-monitor rig :(

Sorry, maybe the free bump will get some fresh eyes looking.
Thanks for getting back.  It is not a dual monitor problem  That was fine.

I have since done a fresh install as it was impossible to use.  I completely deleted the install partition having booted up using the CD and then using gparted.  I have reinstalled in to that partition.

My new problem and it is sad it it not made simple as so many users do this, but I have a separate HOME directory.  The new install did not recognise it.  I tried installing without the directory mounted and with it mounted.  neither time was it recognised or an option to use it.

So now I have to find a way of merging the two as there are hidden files and folders that come with the new install that I probably need.  I am going to try a simple cut and paste. then  change the fstab to my old one.  I hope it works.

Any help and advise always welcome

---

### Post by Jonners59 on 2012-03-11
OK, I copied all the contents of HOME except the Documents etc folders/directries to the old Directory.  Most merged or replaced the old.

Changed the fstab to reflect the new HOME.

Rebooted and the Old Desktop appeared and then it froze again!

Why and how do I fix?  Any ideas as to what is in there that might be causing this?

---

### Post by Jonners59 on 2012-03-12
OK.  I tried the cut and paste....  Still got the PC locking up.
I decided to resort to just deleting the directory and doing a fresh install.  Shame.  It failed to find my HOME directory, so I had to copy the files and folders over that were in the "new" HOME to the old, replacing all that was in the "old" HOME that was of the same name/type.  Then changed fstab to reflect the new HOME location.  It worked.

I have a new problem, though that goes back to what started all this.  soduers is not happy.  I can not do anything that requires Admin privilages such as sudo.  It says I'm not in soduers.  The folder is empty bar a help doc, yet my other machines have an unopenable document in there.  It happened after using "Kuser" as there is no users and groups any more, I tried this.

[HTML]$ sudo /etc/init.d/stunnel4 start
[sudo] password for baronipc: 
baronipc is not in the sudoers file.  This incident will be reported.
[/HTML]

Tried su also:
[HTML]$ su /etc/init.d/stunnel4 start
Unknown id: /etc/init.d/stunnel4
[/HTML]

tried to get to nautilus:
[HTML]$ su nautilus
Unknown id: nautilus
[/HTML]

Any ideas folks?

---

### Post by Jonners59 on 2012-03-12
Fixed:
By refering to a working machine's /etc/group   I opened using suing the install CD and doing [HTML]sudo gedit (address to file)[/HTML]  The file address is  /etc/group

Seems to now work/

---

