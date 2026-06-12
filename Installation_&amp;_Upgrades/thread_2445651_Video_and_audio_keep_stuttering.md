---
title: "Video and audio keep stuttering"
date: 2020-06-17
forum: Installation &amp; Upgrades
---

### Post by darthlinux2 on 2020-06-17
I have just done a fresh install of ubuntu 20.04 and everytime I play a video file with audio either online or from my hard drive every 30-40 the video and audio cuts out, really annoying as I never had this issue on windows 10

Currently in my system I have ryzen 3, nvidia gtx 1050ti 4gb and 16gb ddr4 ram 

If anyone can help me please as I can't use ubuntu like this as I watch alot of media on my pc

---

### Post by ajgreeny on 2020-06-17
Have you installed the recommended nvidia driver by going to ***"Additional Drivers"*** from ***Applications*** at top left, (I think that's where you find it but I use Xubuntu not Ubuntu, so I'm not sure)?

---

### Post by darthlinux2 on 2020-06-17
yes I have tired all of available drivers and same result

---

### Post by daniewicz on 2020-06-17
Which NVidia driver is currently installed?

---

### Post by darthlinux2 on 2020-06-18
> **daniewicz said:**
> Which NVidia driver is currently installed?

I have tried all Nvidia driver that come with 20.04

---

### Post by CelticWarrior on 2020-06-18
> **darthlinux2 said:**
> I have tried all Nvidia driver that come with 20.04

That in itself can be a problem, depending on *how *you did such experiments. Anyway, people are trying to help you here, please answer the pertinent questions to which I'll add a couple:
[LIST=1]
[*]How did you installed the Nvidia drivers?
[*]Is Seciure Boot disabled? If not why not?
[/LIST]

---

### Post by SeijiSensei on 2020-06-18
Have you tried using mpv?

---

### Post by darthlinux2 on 2020-06-18
when I installed ubuntu it installed version 440 so I went on to additional hardware and worked down that list and tested each one that was listed 
not sure about secure boot, can this affect it?

---

### Post by CelticWarrior on 2020-06-18
The automatically installed and newer version should be the best. Confirming it was installed and troubleshooting from there is what should have been done, not experimenting with older versions. Fortunately you did it with the Additional Drivers tool. Supposedly it removes all nvidia files before installing a different version, otherwise it would create problems with mismatched versions.

Yes, Secure Boot is likely the problem. If enabled it prevents loading unsigned drivers even if correctly installed. Please check in UEFI settings and disable it if enabled. If the symptom persists then we need to check the nvidia driver installation status.

---

### Post by darthlinux2 on 2020-06-19
I have tried to disable to secure boot but its grayed out and I can seem to find an option to change this

---

### Post by CelticWarrior on 2020-06-19
If Secure Boot is greyed out then most likely you installed in legacy ("BIOS") mode in a modern UEFI PC. Why?
Modern hardware is designed to work in UEFI mode.

---

### Post by darthlinux2 on 2020-06-19
I have managed to disable secure boot, I had to clear the secure boot keys and it still happening, seem to be even worse now.

---

### Post by CelticWarrior on 2020-06-19
Secure Boot can be disabled without clearing keys. So, I suspect you have lots of things going wrong at once.

---

### Post by VMC on 2020-06-19
Are you watching through YouTube or something else?

---

### Post by darthlinux2 on 2020-06-19
Happens on you tube and when using VLC player

---

### Post by darthlinux2 on 2020-06-19
> **darthlinux2 said:**
> I have managed to disable secure boot, I had to clear the secure boot keys and it still happening, seem to be even worse now.

Any idea of where to go now then?

---

### Post by darthlinux2 on 2020-06-20
Update - I tested linux mint and didn't have any issues so I am thinking this gnome issue - is there anyway to downgrade gnome or any setting I can adjust to help

---

### Post by CelticWarrior on 2020-06-20
If you've tested the same live session of Ubuntu you used to install you'd likely see the same result. The problem is with that installation, not Gnome.

---

### Post by darthlinux2 on 2020-06-20
> **CelticWarrior said:**
> If you've tested the same live session of Ubuntu you used to install you'd likely see the same result. The problem is with that installation, not Gnome.

what would suggest then?, I installed mint and used it for around 1hr and had no issues, but with Ubuntu I have an issue, I have used other distros using ubuntu as a base and have the issue which point to gnome but again I am rather new to this.

---

### Post by CelticWarrior on 2020-06-20
Mint has Ubuntu as base like any other derivative, official or otherwise.

---

### Post by darthlinux2 on 2020-06-20
> **CelticWarrior said:**
> Mint has Ubuntu as base like any other derivative, official or otherwise.

As I said I am new to this lol, so do you have any suggests to fixing this issue?

---

### Post by CelticWarrior on 2020-06-20
My implicit suggestion in previous post is reinstall in UEFI mode as it should be, with Secure Boot disabled. Check the option to install third-party drivers and updates.

---

### Post by darthlinux2 on 2020-06-20
I have reinstalled with FAST boot disabled and Secure boot disabled and I still have issue, strange as you say linux mint is based off ubuntu but I have no issues with this

---

### Post by VMC on 2020-06-20
On YouTube, do you use Firefox or stream using VLC? Also have you tested with another player, maybe the default video player.

---

