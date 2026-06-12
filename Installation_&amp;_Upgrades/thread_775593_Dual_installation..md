---
title: "Dual installation."
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by thrylos97 on 2008-04-30
Hi I'm trying to installing dual-boot with ubuntu and windows.I follow the steps in the link [http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing).
In the step 5 I see only the 3 choices below:

Guided-used entired disk
Guided-used the largest continous free space
Manual

For some reason I don't see the choice 
Guided-resize SCSII(0,0,0)partition 1# and used free space.That means I do somethnig wrong.
So I can't dealing with partitioning with ubuntu and windows.I know I can use the Manual choice but because I'm a beginner in ubuntu                         I don't try this.My desktop cd is from last version 8.04.
Thanks in advance thrylos97.

---

### Post by Partyboi2 on 2008-04-30
You might have to jump in the deep end and choose manual partitioning or use "Guided - use the largest continuous free space" If you use "**G**uided - use the largest continuous free space" then after you have installed use  gparted (Partition editor) on the live cd to resize your windows parrtion to the size you want.

---

### Post by ssican on 2008-04-30
A Guide/Tutorial for Install Dual Boot using the Ubuntu installer's 'Guided Partitioning' feature:
[http://www.herman.linuxmaniac.net/p24.html](http://www.herman.linuxmaniac.net/p24.html)

---

### Post by dksau on 2008-04-30
I'm sorry if this is a hijack but I can't find an appropriate thread.  I have a dual boot computer (first attempt at it) using Windows XP Pro and Ubuntu 6.06.  I can't get to the upgrade button to upgrade on line but I have a 8.04 ISO CD burned that I would like to use to upgrade from 6.06 using that partition without upsetting grub or MBR.  How should I go about this.:)

---

### Post by ssican on 2008-04-30
**dksau**, using the guide/tutorial of the link:[http://www.herman.linuxmaniac.net/p24.html](http://www.herman.linuxmaniac.net/p24.html)
on the **figure 019 --step 7of7--** click on the button **ADVANCED**.

EDIT 1:
On this Guide/Tutorial:[http://www.herman.linuxmaniac.net/p23.html](http://www.herman.linuxmaniac.net/p23.html)
on the **step7 fig35** there is a screenshot of **ADVANCED OPTIONS**, after the click on button **ADVANCED**.
EDIT 2: 
Whithot the Grub, there is not BOOT.
EDIT 3 :
**UPGRADE FROM 6.06 LTS TO 8.04 LTS**:
[https://help.ubuntu.com/community/HardyUpgrades?#head-db224ea9add28760e373240f8239afb9b817f197](https://help.ubuntu.com/community/HardyUpgrades?#head-db224ea9add28760e373240f8239afb9b817f197)

---

### Post by lemming465 on 2008-04-30
In general you can't easily upgrade an existing Ubuntu install from a CD.  If it's one of the *alternate* CD's (as opposed to a live desktop) you can use the CD to cut download time by copying the *.deb files into /var/cache/apt/archives (I used *find*).

Did you follow the directions at [Hardy Upgrade]("https://help.ubuntu.com/community/HardyUpgrades")?

Note that Hardy includes a lot of new technologies including automatic X configuration and Pulseaudio sound; it's still a little rough around the edges.  Bleeding edge folks are welcome to use Hardy now - I like it better than any of its predecessors, but for folks needing stability Canonical is recommending holding off until June when they plan to release a 8.04.1 respin with accumulated bug fixes.

---

### Post by dksau on 2008-04-30
ssican, lemming 465, Thanks guys I would like to upgrade on line but there is a problem after hitting the check button it won't load all of the updates and sometimes say it can't access admin something or other 
so I never can get to the upgrade button.  I tried the offered solution in terminal which also is not possible.  There is nothing on the 6.06 partition that I need to save so I could do a clean install of 8.04 to that same partition if I knew how to stay out of trouble.  Whats my method there?

---

### Post by dksau on 2008-05-01
ssican

Thank you for your help.  I went to hermanlinuxmaniac and studied the page.  I liked the idea of shrinking the existing 6.06 partition and installing 8.04 on the newly formated vacated space.  So  booted gparted and created a ext3 partition for that operation.  I then started by booting windows and selected the last option and booted into Ubuntu.  I have a beta CD and a released version CD of 8.04 I tried to use both.  They both go into Ubuntu but with the beta the floppy drive kept hunting for files and nothing else happened.  I next tried a fresh ISO CD made after Hardy Heron was released.  This CD worked very slowly for what it did.  Twice it stalled at 66% of the bar while search for partition data.  Twice it went into guided partitioning although manual had been selected.  The third time I just quit.  When I rebooted thankfully 6.06 was still operable, all I had to do was set the clock.  Oh the install program also stalled a couple times at USA so I selected USA alternative for keyboard layout and it got into asking for personal data but was typing incorrect characters so I aborted the install.  I think I'll wait until a corrected version is released later to try again.  I did successfully install 8.04 on a new hard drive  that only has Ubuntu installed and it works great there except for firefox shutting down every time a second video is started.  Thankfully session manager puts it back where it was before the shut down.  I thought for a moment that had been corrected with some of the updates but its back and I believe that problem is in firefox.

---

### Post by dksau on 2008-05-02
After thinking about how the two CDs failed to perform I decided to burn a new 8.04 ISO and install.  This time it worked.  There is one reason that I won't mention here why you definitely should shrink your 6.06 partition and keep that OS as well.   Thanks all for  your help and consideration.

---

### Post by dksau on 2008-05-02
Now that 8.04 is installed there is just one problem so far.  The computer has to be shut down with the button.  A black screen with white text says “Make sure the message bus daimon is running and also Network messenger nm_dbus_signal status change assertion 'cb_data-> data-> dbus_ connection failed.

How can I correct that?

---

