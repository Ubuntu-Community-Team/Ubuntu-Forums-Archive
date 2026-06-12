---
title: "Unity cannot load with Intel card after an update"
date: 2014-06-18
forum: Installation &amp; Upgrades
---

### Post by vibe2 on 2014-06-18
[COLOR=#333333][FONT=UbuntuRegular]I know there is a bunch of similar questions out there, but none of them helpful for me so I created my own. After some updates Unity cannot load with Intel VGA. It's an Optimus configuration with an Intel HD3000. I already tried these steps to repair:[/FONT][/COLOR]

[LIST=1]
[*]First of all I usually use xorg-edgers PPA, so I purged and removed it and the related packages and installed the official stuff.
[*]After that I reinstalled xserver-xorg-core & unity & lightdm.
[*]Purged and reinstalled nvidia-prime.
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]After the third step Unity loads because nvidia set itself to default VGA so I figured out this problem is related only with the Intel VGA. When I try to switch to Intel Unity fails and I only see the desktop background. I changed to command line and it wrote the following: 
[https://i.imgur.com/JydnSD8.jpg](https://i.imgur.com/JydnSD8.jpg)
[https://i.imgur.com/jS5mfaS.jpg](https://i.imgur.com/jS5mfaS.jpg)
Here's my log:
[http://paste.ubuntu.com/7628404/](http://paste.ubuntu.com/7628404/)

And I think this bug ([https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/1263540)) may also related with my problem, because it"s blocked a lot of packages time after time till I reduced the PPAs number to the required limit (what is 40 as far as I know). After decreasing PPAs I had a bunch of update notifications but I think some packages may still missing.

Could someone help please?[/FONT][/COLOR]

---

