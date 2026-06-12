---
title: "Install hangs at configuring target system"
date: 2012-03-15
forum: Installation &amp; Upgrades
---

### Post by Ghost_Mazal on 2012-03-15
Morning all ,
 
I am failing with an install. Maybe someone can shed some light for me.
 
Technical details:
 
HP Compaq nx8220 laptop.
6 years old
512mb ram
Intel mobile M 1.5ghz cpu
 
Software: Kubuntu 11.10 32bit.
 
I install from usb and everything runs smooth , past copying files up to the point where the installer says: "Configuring target system.........20%" and there it stops and
nothing happens any further. I have tried twice with the same result.
 
I have used the same .iso successfully on other desktop pc's without problems during install.
 
Any ideas ?
 
Thanx

---

### Post by whiskers751 on 2012-03-15
Can you boot up from Kubuntu?

---

### Post by Ghost_Mazal on 2012-03-15
> **whiskers751 said:**
> Can you boot up from Kubuntu?
 
From the .iso yes , but not from the HDD as the install hasn't finished.

---

### Post by Zorael on 2012-03-17
Could this be [bug #955617](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/955617)? Unless you're the reporter, in which case you'd know. :>

> [SIZE="3"]ubiquity hangs (no activity forever) at configuring target system[/SIZE]

*[...]*

This just started happening the last few days. (less than a week, but march 13 and 14 ISOs
for sure) Everything seems to installing fine till the message line says configuring
target system. The progress bar gets about 1/4 over then stops. Disk activity stops, and
nothing more happens. Ubiquity still waiting now over 1/2 hour later. Booted to live
ubuntu studio live DVD ISO from SD card. Then double clicked install icon on desktop.
Ubiquity started up fine took information to install and started installing... worked fine
till hang.

```
Colin Watson (cjwatson) on **2012-03-15**

Changed in ubiquity (Ubuntu):
status:	         New &#8594; In Progress
importance:	 Undecided &#8594; High
assignee:	 nobody &#8594; Colin Watson (cjwatson)
```

So it seems it's a known issue and is being worked on. If you have a Launchpad account, log into it and then click "Yes, this affects me" up top to get notified of updates.

---

### Post by 2F4U on 2012-03-17
This bug has been filed against 12.04. What makes you think that it applies in this case, since my understanding is that the OP uses 11.10?

---

### Post by Ghost_Mazal on 2012-03-17
Indeed I use 11.10 , but that is exactly what happened to me.

I have found however that it is only on one of my laptops. My other laptop and pc
this doesn't happen.

I have given up installing on the affected laptop.

---

### Post by 2F4U on 2012-03-17
> **Ghost_Mazal said:**
> 
Technical details:
 
HP Compaq nx8220 laptop.
6 years old
512mb ram
Intel mobile M 1.5ghz cpu
 
Software: Kubuntu 11.10 32bit.
 

Do you really intend to run Kubuntu on a machine with 512 MB of RAM? The community documentation states 1 GB as minimum requirement:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

While you may get it running it is probably not much fun. I would rather try something lighter such as Xubuntu or Lubuntu. But thats just my personal opinion.

---

### Post by Ghost_Mazal on 2012-03-17
> **2F4U said:**
> Do you really intend to run Kubuntu on a machine with 512 MB of RAM? The community documentation states 1 GB as minimum requirement:

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

While you may get it running it is probably not much fun. I would rather try something lighter such as Xubuntu or Lubuntu. But thats just my personal opinion.

Sjoe you know , one has gotten so used to the fact that linux runs on everything that I never even bother to look at system requirements. I agree that the specific laptop might be a little light. One is just so used that it never used to matter with linux. Guess that isn't so anymore.

---

### Post by Zorael on 2012-03-18
> **2F4U said:**
> This bug has been filed against 12.04. What makes you think that it applies in this case, since my understanding is that the OP uses 11.10?
So he does! My bad.

Refer to the [DebuggingUbiquity](https://wiki.ubuntu.com/DebuggingUbiquity) wiki page instead, then. Try to find some logs.

---

### Post by Ghost_Mazal on 2012-03-19
I managed to resolve this issue. In a way , not completely resolved.

I installed it to a USB stick on a different pc and now run it on the laptop from the usb stick. BUT , I run Xubuntu desktop , not KDE.

So in a way , I am sorted. Don't have ubuntu on the HDD , but at least I can use it.

---

### Post by recluce on 2012-03-19
> **Ghost_Mazal said:**
> I managed to resolve this issue. In a way , not completely resolved.

I installed it to a USB stick on a different pc and now run it on the laptop from the usb stick. BUT , I run Xubuntu desktop , not KDE.

So in a way , I am sorted. Don't have ubuntu on the HDD , but at least I can use it.

You could use Clonezilla to clone your USB installation to your laptop's harddrive.

---

### Post by Ghost_Mazal on 2012-03-19
> **recluce said:**
> You could use Clonezilla to clone your USB installation to your laptop's harddrive.

I can't. The laptop was going to be dual boot. It MUST keep XP on it as well.

---

