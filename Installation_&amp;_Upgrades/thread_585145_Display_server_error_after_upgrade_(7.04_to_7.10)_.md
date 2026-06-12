---
title: "Display server error after upgrade (7.04 to 7.10) - Can't load Ubuntu"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Robotman on 2007-10-21
I've just tried to upgrade on a 2nd computer.  The upgrade went perfectly on my laptop, but on another desktop, I get the following error message:
```
The display server has been shut down about 6 times in the last 
90 seconds.  It is likely that something bad is going on.  
Waiting for 2 minutes before trying again on display :0.
```
This message appears in black text on a grey background with a blue border.  It occurs when Ubuntu boots, right after
```
Running local boot scripts (/etc/rc.local)                                   [OK]
```
I've tried running the Ubuntu 7.10 Live CD... and noticed that my monitor shuts off (no signal detected) when that desktop is loaded.  The monitor is a ViewSonic P95f+.
How can I fix this, using the Live CD?  Failing that, how can I undo the upgrade and revert that computer to Ubuntu 7.04?
If this problem is already being discussed elsewhere, please point me there. ;)
Thanks

---

### Post by tjdebon on 2007-10-21
I get the same display server error message. I upgraded from 7.04 to 7.10.  My system is a Windows 98SE era Sony Vaio PCV-L630 which I reformatted the HDD and installed 7.04 from CD a month ago. I believe that has ATI Rage 128 Pro video in it with a Sony-unique video cable and LCD monitor.  The display worked with 7.04, now it gives me the display server error message and hangs.  Please help.

---

### Post by nrohluap on 2007-10-25
I have a Thinkpad T60 8744-5BU, currently running dapper (6.06) just fine. I try either the 7.10 ubuntu or kubuntu livecd startup, and I get this exact same error right after the switch to graphics mode.

This has one of the ATI Mobility 1400 chips and a 1680x1050 display panel. The X server starts up at what looks like 1400x1050, and the mouse responds until the attempted start of the GDM.

Anyone have any ideas on this one??

---

### Post by Milkymonsta on 2007-10-29
Hmm... I'm seeing the same error, I haven't upgraded from any previous version of Ubuntu as this is my first install - originally the display started out fine but I needed to change the resolution to 1440 x 900 via a Generic Monitor since my LG monitor wasn't listed, the system then asked me to log out to make such changes and then the problems desicribed above began.

---

### Post by JPorter on 2007-10-29
This issue sounds like the same old problem... the fglrx driver is sometimes required to start xorg without crashing on newer ATI cards.

For those of you with recent ATI cards that haven't been able to get Gutsy up and running, try this... install with the Alternate CD (text install) and then try to boot normally.  If it fails with an error when starting x, especially if it gives you the old "display shut down 6 times" error, try the following:


You will need wired internet access.  Boot to recovery console and do this:
```
sudo apt-get update

sudo apt-get install xorg-driver-fglrx

sudo depmod -a

sudo aticonfig --initial

sudo aticonfig --overlay-type=Xv
```

If your first step failed because you didn't have internet access ("could not resolve" errors), you should run:```
sudo ifconfig eth0 down

sudo dhclient eth0
```

Of course, substitute eth0 for whatever your ethernet connection is (eth1, etc).  Follow the above driver install steps.



And then reboot normally.  Voila, you should be up and running.  Best of luck to you.

---

### Post by Dunrobin on 2007-10-29
I've been experiencing the same problem.  In my case, I upgraded from 7.04 through the Update Manager, and everything ran fine until I had to reboot when the installation was completed.  I even downloaded the Live CD (through my Windows XP partition), but got the same error that Robotman reported when trying to run Ubuntu from it.  I finally gave up and re-installed a new copy of 7.04 from my old CD, since that always ran just fine on my machine.  (Fortunately my data files are all on a separate partition, so nothing terribly vital got lost.)

I'm going to re-try the Update to 7.10 tonight, and then try JPorter's suggestons for the fix.  I will post a reply with the results.

---

### Post by JPorter on 2007-10-30
> **Dunrobin said:**
> I'm going to re-try the Update to 7.10 tonight, and then try JPorter's suggestons for the fix.  I will post a reply with the results.

Any luck?

---

### Post by taah on 2008-01-25
> **JPorter said:**
> Any luck?

I have a Dell Inspiron 1721 with an ATI Radeon X1200 Series controller. I had to install from the ALT CD and after following JPorter's advice with the above commands I was able to get into X. Thank you.

---

