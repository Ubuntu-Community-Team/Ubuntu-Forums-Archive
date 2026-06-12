---
title: "Installation of 12.04 fails - &quot;unrecoverable error&quot;"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by paranat on 2012-04-27
I am trying to do a clean install of Ubuntu 12.04 from a self-burned DVD. I have tried it now several times, and each time after the user name / password dialog the following message appears:

> Installation failed

The installer encountered an unrecoverable error. A desktop session will now be run so that you may investigate the problem or try installing again.I have no idea what the problem might be. Do you have any suggestions?

I chose the right version of the image file, the DVD burn is uncorrupted... To me it should be fine.

---

### Post by kc1di on 2012-04-27
> **paranat said:**
> I am trying to do a clean install of Ubuntu 12.04 from a self-burned DVD. I have tried it now several times, and each time after the user name / password dialog the following message appears:

I have no idea what the problem might be. Do you have any suggestions?

I chose the right version of the image file, the DVD burn is uncorrupted... To me it should be fine.

Will that machine boot to the live session? or are you trying to install without going to the live session. I know there was a bug that prevented some machines from doing the install if it was not installed from the live session,  If it will not boot to live session then there be other problems.

---

### Post by paranat on 2012-04-27
> **kc1di said:**
> Will that machine boot to the live session? or are you trying to install without going to the live session
 
It boots to the live session without problems. (I wrote my first message running on the live session.) I have tried installing both through the live session and without.

---

### Post by dino99 on 2012-04-27
you might then try with bootoption

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by nicks27 on 2012-04-27
I'm having the same issue installing on two (relatively old) separate machines (see below). I'm installing the Xubuntu12.04 LTS desktop 32-bit edition, md5 checksum correct and CD verified after the burn.

1) An Athlon 850Mhz with 512MB RAM (clean install, was previously running 10.04, not dual boot)

[LIST]
[*] install (not from the live session) failed with the "unrecoverable error" message.
[*] boots into a live session ok (but I've yet to try a reinstall from there)
[/LIST]
 
2) An Athlon XP 3200+ with 1GB RAM (clean install, was previously running 11.10, dual boot with Win7)

[LIST]
[*] install (not from the live session) failed with the "unrecoverable error" message.
[*] boots into a live session ok, an install from there eventually gives an empty desktop with the hourglass mousepointer, a reboot went straight into Windows7 (no GRUB menu), I'm now trying another install from the live session and I'll leave the hourglass ticking over for a while...
[/LIST]
  If it helps here's the tail from my /var/log/syslog on the second machine:

```

Apr 27 13:40:05 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/83haiku
Apr 27 13:40:05 xubuntu 83haiku: debug: /dev/sdb6 is not a BeFS partition: exiting
Apr 27 13:40:05 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90bsd-distro
Apr 27 13:40:05 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90linux-distro
Apr 27 13:40:05 xubuntu 50mounted-tests: debug: running subtest /usr/lib/os-probes/mounted/90solaris
Apr 27 13:40:06 xubuntu migration-assistant: info: setting ostype from: '/dev/sda1:Windows 7 (loader):Windows:chain'
Apr 27 13:40:06 xubuntu migration-assistant: info: got ostype of: 'windowsxp', mountpoint is: '/mnt/migrationassistant'
Error: Could not find the path /target/WINDOWS/system32/config/software
Error: Could not find the path /target/WINNT/system32/config/software
Fatal: Could not find the SOFTWARE registry hive at /target/WINNT/system32/config/software.
Apr 27 13:40:06 xubuntu ubiquity[3952]: migration-assistant: filtering out Windows 7 (loader) (/dev/sda1) as it has no users
Apr 27 13:40:06 xubuntu ubiquity[3952]: debconffilter_done: ubi-migrationassistant (current: ubi-migrationassistant)
Apr 27 13:40:06 xubuntu ubiquity[3952]: Step_before = stepUserInfo
Apr 27 13:43:15 xubuntu install.py: Exception during installation:
Apr 27 13:43:15 xubuntu install.py: Traceback (most recent call last):
Apr 27 13:43:15 xubuntu install.py:   File "/usr/share/ubiquity/install.py", line 689, in <module>
Apr 27 13:43:15 xubuntu install.py:     install.run()
Apr 27 13:43:15 xubuntu install.py:   File "/usr/share/ubiquity/install.py", line 129, in run
Apr 27 13:43:15 xubuntu install.py:     self.copy_all()
Apr 27 13:43:15 xubuntu install.py:   File "/usr/share/ubiquity/install.py", line 465, in copy_all
Apr 27 13:43:15 xubuntu install.py:     self.db.progress('SET', 10 + copy_progress)
Apr 27 13:43:15 xubuntu install.py:   File "/usr/lib/python2.7/dist-packages/debconf.py", line 60, in <lambda>
Apr 27 13:43:15 xubuntu install.py:     lambda *args, **kw: self.command(command, *args, **kw))
Apr 27 13:43:15 xubuntu install.py:   File "/usr/lib/python2.7/dist-packages/debconf.py", line 65, in command
Apr 27 13:43:15 xubuntu install.py:     self.write.flush()
Apr 27 13:43:15 xubuntu install.py: IOError: [Errno 32] Broken pipe
Apr 27 13:43:15 xubuntu install.py: 
Apr 27 13:50:31 xubuntu kernel: [ 1128.666340] [drm] nouveau 0000:03:00.0: Setting dpms mode 1 on tmds encoder (output 1)
Apr 27 13:50:56 xubuntu kernel: [ 1153.939066] [drm] nouveau 0000:03:00.0: Setting dpms mode 0 on tmds encoder (output 1)

```

---

### Post by 8Kuula on 2012-04-27
Alternate installation worked on Amilo K 7600 laptop.

---

### Post by dreltuc on 2012-04-27
I am having the same problem trying to install 12.04 from the desktop image downloaded on 4-26-12 to a CD. The live session appears to work but install fails.
I get the "unrecoverable error" if I attempt to install without the live session.
If I try to install from the live session the process hangs with the mouse pointer showing the little circle with rotating dots.
My system is a very basic MSI KM4M mother board with AMD processor and 1.5G ram.
I have independently successfully installed Xubuntu 10.04, Kubuntu 12.04, and ubuntu 11.04 on this system during the past few days.
I hope this help give someone an idea on how to resolve this issue. I really would like to get 12.04 going on my system.
Thank you
don

---

### Post by nicks27 on 2012-04-27
Machine 2 from my post above also failed with:

[LIST]
[*]a fresh install of 11.10 followed by an upgrade to 12.04 in a live session from the cd
[*]a fresh install of 12.04 from a live session from bootable USB
[/LIST]

On machine 1 I've done a fresh install of 10.04 followed by system updates... when they are complete I'll try an upgrade to 12.04 over the web through update manager.

Machine 1 (the 850MHz Athlon with 512MB RAM) has an ATI Rage 128 graphics card.
Machine 2 (the Athlon XP 3200+ with 1GB RAM) has an NVidia GeForce FX 5200 graphics card.

---

### Post by dreltuc on 2012-04-28
I wanted to pass along that I was also successful with the 12.04 alternate installation
(thank you '8Kuula' for the suggestion).
The "alternate" installation seems to be working well for me.
I hope this somehow is resolved before too many users get discouraged trying to install 12.04

---

### Post by paranat on 2012-04-28
Alternative installation worked for me also. Thank you.

---

### Post by nicks27 on 2012-04-29
Glad you're sorted paranat. The alternate cd has also worked fine for my two old machines.

---

### Post by ilpiero on 2012-04-29
Alternate cd did't worked for me... hangs during the system installation.
I managed to skip the failing step, i can boot but not even Xorg is installed.
Thanks!

---

### Post by robmontag on 2012-05-15
Maybe this workaround works for all of you users with old AMD processor:

- Start Xubuntu Live CD Session (Try Xubuntu)
- Open Terminal
- execute command: sudo apt-get purge ubiquity-slideshow-xubuntu
- Install Xubuntu 12.04 

It works for me and my AMD Sempron 2600+ / Asus a7v600x / 2 GB RAM desktop.

note: screens of installation process change (not so pretty) but system is installed.

---

### Post by cristian.ene on 2012-05-23
is there a solution for this? i have the same problem with AMD 2200+

---

### Post by cristian.ene on 2012-05-23
> **cristian.ene said:**
> is there a solution for this? i have the same problem with AMD 2200+

anyone?!?

---

### Post by jadtech on 2012-05-23
I found this if if its any help ?? 

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/985354](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/985354)

---

### Post by cristian.ene on 2012-05-23
can be marked as [solved]

Who has the same problem, use the following steps:

1.TRY Ubuntu from USB or CD

2.Open terminal, and type:
```
sudo apt-get remove ubiquity-slideshow-ubuntu
```

3.Start the installation :)

---

### Post by gam01hr on 2012-05-23
Same problem on older PC with AMD Athlon XP2200, the solution above works for me! Thank you. I have corrected my view on ubuntu 12.04  :smile:

---

### Post by garageguy on 2012-05-29
> **cristian.ene said:**
> 
Who has the same problem, use the following steps:

1.TRY Ubuntu from USB or CD

2.Open terminal, and type:
```
sudo apt-get remove ubiquity-slideshow-ubuntu
```

3.Start the installation :)

Had the same problem here (AMD Athlon XP 1600+, VIA 8235 chipset), and this solution works for me also.  (AMD platforms seem to tickle this bug.)

One note, in case it's not obvious how to do step 3: right click on desktop to get a menu, then Applications -> System -> Install Xubuntu.

Thanks christian.ene!

--garageguy

---

### Post by leillo1975 on 2012-05-31
> **cristian.ene said:**
> can be marked as [solved]

Who has the same problem, use the following steps:

1.TRY Ubuntu from USB or CD

2.Open terminal, and type:
```
sudo apt-get remove ubiquity-slideshow-ubuntu
```

3.Start the installation :)


Thanks

---

### Post by ps57 on 2012-06-05
OK, so I too have an older Athlon 1600+ and got this bug. After the install failure, I hit OK, and eventually an Ubuntu desktop appeared. 

For step 2, to open a terminal,  I had to poke the top-left "Dash Home" icon, then search for application xterm . Then I removed the ubiquity package.

Then started (resumed?) the install from the desktop icon.  It completed normally. :P

---

### Post by phispi on 2012-06-08
Same here with an 32 bit installation of 12.04 to an Athlon AMD XP on an empty harddisc: At the time the slideshow would be shown (after entering the user name and password) the installation routine stops with the "unrecoverable error" message described in the first post. The corresponding lines in /var/log/syslog were similar as described above:

```

Jun  8 09:37:37 ubuntu install.py: Exception during installation:
Jun  8 09:37:37 ubuntu install.py: Traceback (most recent call last):
Jun  8 09:37:37 ubuntu install.py:   File "/usr/share/ubiquity/install.py", line 689, in <module>
Jun  8 09:37:37 ubuntu install.py:     install.run()
Jun  8 09:37:37 ubuntu install.py:   File "/usr/share/ubiquity/install.py", line 102, in run
Jun  8 09:37:37 ubuntu install.py:     self.db.progress('START', self.start, self.end, 'ubiquity/install/title')
Jun  8 09:37:37 ubuntu install.py:   File "/usr/lib/python2.7/dist-packages/debconf.py", line 60, in <lambda>
Jun  8 09:37:37 ubuntu install.py:     lambda *args, **kw: self.command(command, *args, **kw))
Jun  8 09:37:37 ubuntu install.py:   File "/usr/lib/python2.7/dist-packages/debconf.py", line 65, in command
Jun  8 09:37:37 ubuntu install.py:     self.write.flush()
Jun  8 09:37:37 ubuntu install.py: IOError: [Errno 32] Broken pipe
Jun  8 09:37:37 ubuntu install.py:

```The 
```
sudo apt-get remove ubiquity-slideshow-ubuntu
```worked for me as well. I

[LIST]
[*]started the direct install method from DVD
[*]at the time, the first dialog (welcome) is shown I switched to a text console by pressing Ctrl+Alt+F1.
[*]There, I typed in the command mentioned above. I ignored the warning of a locked file and confirmed that the package was successfully deinstalled by typing in the command again.
[*]I switched back to the graphical installer by pressing Alt+F7.
[*]Now the installation run through smoothly & successfully (with a "file not found" message at the location where the slideshow would have been).
[/LIST]
Thanks to all of you that posted solutions!


Best regards,
Philipp

---

### Post by phispi on 2012-06-08
I created a bug report for this problem:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1010461](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1010461)

---

### Post by gjansen on 2012-08-08
> **robmontag said:**
> Maybe this workaround works for all of you users with old AMD processor:

- Start Xubuntu Live CD Session (Try Xubuntu)
- Open Terminal
- execute command: sudo apt-get purge ubiquity-slideshow-xubuntu
- Install Xubuntu 12.04 

It works for me and my AMD Sempron 2600+ / Asus a7v600x / 2 GB RAM desktop.

note: screens of installation process change (not so pretty) but system is installed.

Thank you robmontag, your recipe also worked for ¨Xubuntu 12.04 i386 dektop¨ on this system:
AMD Athlon XP2000+ / Asus A7V8X-X [KT400 (Northbridge) & VT8235 (Southbridge)]  / 750MB RAM

Thanks also go to phispi for mentioning the shortcuts to enter terminal (Ctrl+Alt+F1) and how to return to the graphical interface (Alt+F7).

---

### Post by bobwdn on 2012-08-21
I had experienced the same issues everyone else did in previous posts here.

I resolved this issue by installing the 11.10 Mythbuntu livecd. Upgrading the 11.10 version with latest 11.10 upgrades (several hundred packages and security updates.)

At this point I have not configured anything, in an attempt to keep the upgrade as simple as possible.

I then restarted the computer, checked again to confirm that no other 11.10 upgrades were available. When there weren't any upgrades, I then selected to upgrade to 12.04LTS via the 'Update Manager' and all went well. I now have a 12.04LTS Mythbuntu install to configure for my next Mythbuntu frontend.

Granted a long way around to get a 12.04 install. Hopefully others will discover what is causing the 12.04 Mythbuntu livecd install to stop suddenly.

It seems there are quite a few of us users experiencing this "unrecoverable error" issue.

---

### Post by drdre on 2013-01-02
sudo apt-get purge ubiquity-slideshow-xubuntu worked for me 2. Thanks guys! on 12.10 xubuntu and lubuntu.

---

### Post by geocomp on 2013-01-16
Removing the slide show worked on installing 12.10 on a AMD Athlon XP 3000 with a Radeon Graphics card.

---

### Post by Xusn96 on 2013-01-24
@nicks27: I feel your pain bro, I am running 11.10 on my Athlon 3200+ 2GB with an XFX 7600GS after having the same issues trying to install 12.04 LTS.  Will have to look into this alternative install method... Its funny though a couple years ago I was running the latest Ubuntu on a Pentium II 400 Mhz with 384 MB ram, and while maybe a little slow, it always worked.. used it for a private Teamspeak server.

---

### Post by piercing on 2013-02-26
Hi, I have this same issue with an AMD Athlon in an old PC.

The bad thing is that when I use

> sudo apt-get remove ubiquity-slideshow-ubuntu

I get
> 
ubiquity-slideshow-ubuntu could not be found

I have tried different variants like only ubiquity-slideshow (without the ubuntu) but with no results.

I'm trying to install from Ubuntu 12.04 live CD

I have tried before Xubuntu 12.10 but the installation gets stucked in a black screen and doesn't move for hours, so I decided to try Ubuntu 12.04.

Any help would be much appreciated! :D

---

### Post by Xusn96 on 2013-03-06
sudo apt-get remove ubiquity-slideshow-ubuntu

Worked for me.
AMD Athlon 3200+, 2GB PC2700, 160 GB HDD, Nvidia 7600GS.

Next step working out the broadcom USB wifi dongle...

---

### Post by ThePenciler on 2013-06-22
Just wanted to add, that in trying to install XBMCbuntu without booting the live session I ran into this problem as well. What I did was type Ctrl+Alt+F1 to get to the command line. You are already logged in as root. Type ```
[COLOR=#000000]sudo apt-get remove ubiquity-slideshow-xbmcbuntu[/COLOR]
```[COLOR=#000000] (though I think I left out sudo). Then Ctrl+Alt+F7 back. It installs, but there's an ugly "Unable to load page" placeholder, which, after seeing it, I reacted to with "Boom! Gotcha, ya little bastard!" Make sure you add that last part. [/COLOR]:D

---

