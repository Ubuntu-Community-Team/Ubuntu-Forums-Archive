---
title: "How to upgrade Xserver back to 1.13"
date: 2013-01-20
forum: Installation &amp; Upgrades
---

### Post by Asif786i on 2013-01-20
Hi all
 
Afret upgrading to 12.10 I was unable to boot so I downgraded Xserver to 1.12 and installed propietory graphics driver. i am using ATI Radeon HD 4200.
 
However i now want to return to xorg 1.13. Can somebody please advise on how to do that please.
Please keep it simple as i am new to this stuff
Thanx
Asif

---

### Post by tgalati4 on 2013-01-20
Post exactly what steps you performed to downgrade to 1.12.

Open a terminal, post the output of:

```
apt-cache policy xorg
```

How you downgraded with affect how you repair it.

---

### Post by Asif786i on 2013-01-21
Hi tagalati4

I used the makso96 PPA to downdrade Xserver and install proprietory drivers.
I think I am now back to oper source driver but nned to go back to X1.13.

The output from apt-cache is

apt-cache policy xorg
xorg:
  Installed: 1:7.7+1ubuntu4
  Candidate: 1:7.7+1ubuntu4
  Version table:
 *** 1:7.7+1ubuntu4 0
        500 [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status

Thanx for your help.
Asif

---

### Post by tgalati4 on 2013-01-21
If you remove the PPA (comment out the lines in /etc/apt/sources.list) 

and then 

```
sudo apt-get update
sudo apt-get install --reinstall xserver-xorg
```

That might do it.

---

### Post by Asif786i on 2013-01-22
Hi tagalati4

I am sorry to say that the above instructions have had no effect.
Xorg -version still says 1.12 and the performance is still the same.

Any other ideas?
Asif

---

### Post by grahammechanical on 2013-01-22
Synaptic Package Manager is not installed by default in 12.10. I am using the development version of 13.04 and Synaptic tells me that I have xserver-xorg 1:7.7+1ubuntu4 installed. That is the same xorg version as you have but I also have xserver-xorg-core 2:1.13.1.901-0Ubuntu1  and that is listed as the latest version.

If you use Synaptic and search for xserver-xorg-core you might find that you have 2:1:12 etc., and if you select it and right click you might find that you can mark it for upgrade to the latest version>

Regards.

---

### Post by tgalati4 on 2013-01-22
I'm confused.  I'm running 12.10 and I have 1.13 also, that is why I wanted to see what version of xserver-xorg that asif was running.  It's quite strange.  Perhaps there is another PPA (or package from PPA) that is causing a dependency on core 1.12.

tgalati4@Dell600m-mint14 ~/Desktop $ apt-cache policy xserver-xorg-core
xserver-xorg-core:
  Installed: 2:1.13.0-0ubuntu6.1
  Candidate: 2:1.13.0-0ubuntu6.1
  Version table:

Did you install any other ATI graphics utilities?  Like an ATI system tray utility?  That could cause xserver-xorg-core to be pinned.

Install synaptic and look to see if you have both versions of xserver-xorg-core available.

```
sudo apt-get install synaptic
```

---

### Post by Asif786i on 2013-01-23
Hi
 
I have been using Ubuntu since 10.10 and then upgraded to 12.04 when that was released. During that time I remember moving to the proprietry driver as it were supposed to be better and it worked fine for years.
 
When I upgraded to 12.10 apparently this driver is not supported by Xorg 1.13 so I was getting almost a blank screen. The advice was to dowgrade Xorg to 1.12 but that did not fix it for me. I have since then moved to the open source driver and wanted to go back to X1.13 to see if that works.
 
The open source driver currently gives me a gui with reasonable resolution but it is very choppy. Mouse dissappears when its not moving and the launcher area is blank when launcher is hidden. It does not redraw the desktop. The whole experience is very bad under X1.12. Also the laptop is running hotter. Would X1.13 help or should I try something else.
 
Maybe I should clear out all graphics drivers properly (not sure how) and then install Catalyst propriety driver cleanly. I have read that should work with X1.12 (and also with X1.13)
My laptop is HD dv6-2112sa with ATI Radeon HD 4200.
 
Maybe its time to reinstall ubuntu back to 12.04?
 
Regards
Asif

---

