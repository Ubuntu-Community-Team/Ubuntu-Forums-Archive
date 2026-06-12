---
title: "[SOLVED] Rigged: Intrepid Screen Resolution not detected"
date: 2008-10-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by orbish on 2008-10-09
06:27 AM EST    9 OCT 2008

OS: Ubuntu 8.10 64bit, updated to time and date above

Hardware:
Gigabyte GA-G33M-DS2R (intel video driver)
Q6600 cpu
HP LP2465 Monitor (1920x1200)



Ok, here's my experience and how I rigged it to work.  GDM will start-up in 4:3 sometimes, other times it would startup in 1920x1200, when I log-in my max resolution is 1360x768.  I should also note that /var/log/Xorg.0.log seems to see everything just fine.  Screen resolution also doesn't know my monitor type (did in hardy).  I just now realized that since 8.04 we haven't been using xorg.conf (didn't have these problems with hardy), so I was at a loss.

(writing my thought process, might help someone?)
I searched forums and googled for an hour before starting to really think about where that new display information would be saved.  If the resolution is changing when I log-in, the information is probably going to be found in my home directory.

Rigged solution: 

gedit /home/$user/.config/monitors.xml
set width, height, and rate.
save
logout
login

This doesn't fix the wrong resolution showing up in Screen Resolution.  I don't really mind since this is a single monitor setup, and I just need 1 resolution (until virtualbox/starcraft install).  I can wait for a fix via updates unless it's something simple.  Anyways, I didn't find much information around about this monitors.xml file, and since it fixed my problem pretty easily, I figured it would be best to share.

---

### Post by D10 on 2008-10-10
I have been having the same problem. I have tried (X,K) Ubuntu 8.10 betas none will detect my monitor. I will give this a try tonight and see how it goes. Hopefully this will be fixed soon, as like you I never  had this problem with Hardy.

---

### Post by wgrant on 2008-10-10
> **D10 said:**
> I have been having the same problem. I have tried (X,K) Ubuntu 8.10 betas none will detect my monitor. I will give this a try tonight and see how it goes. Hopefully this will be fixed soon, as like you I never  had this problem with Hardy.

We can't often fix things without knowing about them. Please file a bug!

---

### Post by ronacc on 2008-10-10
I have a similar problem , but in my case I can't blame it on x or Ubuntu , it's a known bad edid on the monitor :mad: atleast I know how to make it play nice :)

---

### Post by Nerd_bloke on 2008-10-10
Probably after this bug, hot plug is a nice idea but EDID is still a tad iffy

[https://bugs.launchpad.net/bugs/194760](https://bugs.launchpad.net/bugs/194760)

---

### Post by wgrant on 2008-10-10
> **ronacc said:**
> I have a similar problem , but in my case I can't blame it on x or Ubuntu , it's a known bad edid on the monitor :mad: atleast I know how to make it play nice :)

File a bug - it can hopefully have a quirk added.

---

### Post by ronacc on 2008-10-10
In my case it actualy is a broken edid , google returns about a zillion hits on this make/model , but what can you expect from a 21"WS lcd for less than $200 ? works fine as long as I hand configure it :lolflag:

---

### Post by wgrant on 2008-10-10
> **ronacc said:**
> In my case it actualy is a broken edid , google returns about a zillion hits on this make/model , but what can you expect from a 21"WS lcd for less than $200 ? works fine as long as I hand configure it :lolflag:

Yes, but we can add an EDID quirk in X so that it doesn't need manual configuration.

---

### Post by ronacc on 2008-10-10
if it will help it is a starlogic hds20w  , it is 1680x1050 but comes in as 1400x1050 , the max res avail through screens - resolution is 1440x900 as detected but I can add 1680x1050 to the appropriate mode line in /etc/x11/xorg.conf and all is well . note this info is from hardy I havent tried intrepid on that box yet but it has been like that since dapper so I don't expect anything different . you don't need to make any special efforts on my behalf but If you can mabye help some others that are stuck with one of theese and aren't able to correct it themselves I'm sure they would appreciate it .

---

### Post by orbish on 2008-10-11
Ok solved my problem, KVM switch was throwing off EDID.  Searched some more and found some troubleshooting techniques:

sudo ddcprobe
if your edid fails, that's your problem.

[Here's some more information and troubleshooting tips on EDID failure]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/194760")

---

### Post by Batti5 on 2008-10-11
i installed ibex, i have a intel 815 1280x1024 24bit,85hz integrated, x only detects
1024x768 16bit 85hz

---

