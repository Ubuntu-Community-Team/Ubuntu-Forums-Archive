---
title: "Anybody able to run these apps on 16.10?"
date: 2016-10-16
forum: Installation &amp; Upgrades
---

### Post by The Bright Side on 2016-10-16
Hey community!

I've installed Ubuntu 16.10 on my laptop and have been unable to install the following:

[LIST]
[*]VirtualBox
[*]Simple Screen Recorder
[*]DosBox
[/LIST]

Have you guys had any luck with these? I found DosBox in the repos at first using Ubuntu Software, but when I clicked "Install", nothing happened. After rebooting, it had disappeared. In the case of Simple Screen Recorder, the repo seems to be outdated, and I couldn't find any other source to install it from (a deb would be awesome). And VirtualBox simply doesn't seem to be available for 16.10 yet, and the 16.04 version won't install because of dependency issues.

Any luck? I use VirtualBox and Simple Screen Recorder almost daily, so I'm really hoping somebody out there has a solution.

---

### Post by xmegax on 2016-10-16
I had no problem installing VirtualBox from Ubuntu Software on 16.10.
Simple Screen Recorder needs the repo updated for 16.10 and i cant get the source code to compile on it either, I followed all the read me instructions.
I have not tried DosBox.

---

### Post by CantankRus on 2016-10-16
You may have to wait for some repos to catch up if at all.
I would stick to 16.04 if everything was working OK. 
16.10 is only supported for 9 months.
I have another install of 16.10 for having a play with unity8 but stick to LTS releases for main use.

---

### Post by The Bright Side on 2016-10-16
Hmmm, weird. I will tinker with this a bit more later today, but the funny thing is, yesterday, there was one point where it seemed Ubuntu Software only found Snap packages.

For VirtualBox, I set up its repo right away, so perhaps that's why it failed to install - I will disable the VB repo and then install the version that comes with 16.10.

---

### Post by mc4man on 2016-10-16
Simple Screen Recorder should be available from ppa
[https://launchpad.net/~maarten-baert/+archive/ubuntu/simplescreenrecorder](https://launchpad.net/~maarten-baert/+archive/ubuntu/simplescreenrecorder)

---

### Post by xmegax on 2016-10-16
It seems to have failed for 16.10:
[https://launchpad.net/~maarten-baert/+archive/ubuntu/simplescreenrecorder/+packages](https://launchpad.net/~maarten-baert/+archive/ubuntu/simplescreenrecorder/+packages)

The PPA added fine, but:
sudo apt-get install simplescreenrecorder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package simplescreenrecorder

Guess we just have to wait a while..

---

### Post by The Bright Side on 2016-10-16
I'll see if I can drop the Simple Screen Recorder developer a line. :-)

---

### Post by howefield on 2016-10-16
> **The Bright Side said:**
> I found DosBox in the repos at first using Ubuntu Software, but when I clicked "Install", nothing happened.

What do you get from the terminal command.. 

```
apt-cache policy dosbox
```

You should get an Install candidate with a version number which can be installed with..

```
sudo apt install dosbox
```

> After rebooting, it had disappeared. In the case of Simple Screen Recorder, the repo seems to be outdated...

simplescreenrecorder can be installed with this ppa : ppa:maarten-baert/simplescreenrecorder 

> I use VirtualBox and Simple Screen Recorder almost daily, so I'm really hoping somebody out there has a solution.

Virtualbox is in the repository, you can check what version is available for you with..

```
apt-cache policy virtualbox
```

---

### Post by The Bright Side on 2016-10-16
Thanks so much for all your responses, guys! I just installed VirtualBox and DosBox and they both work fine, and I dropped Maarten Baert a line to see if he's planning to update the Simplescreenrecorder PPA soon :-) In the case of the 2 "Boxes", there must have been some issue with Ubuntu Software yesterday. Today, I was able to find both apps and install them without issue (in the case of VirtualBox, I disabled the VirtualBox PPA first though and installed it from the Ubuntu repos).

---

### Post by howefield on 2016-10-16
> **The Bright Side said:**
> ....and I dropped Maarten Baert a line to see if he's planning to update the Simplescreenrecorder PPA soon..

What's up ?

There is a version for Yakkety in the ppa.

[https://launchpad.net/~maarten-baert/+archive/ubuntu/simplescreenrecorder?field.series_filter=yakkety](https://launchpad.net/~maarten-baert/+archive/ubuntu/simplescreenrecorder?field.series_filter=yakkety)

---

### Post by The Bright Side on 2016-10-16
Yeah, I saw it!! Awesome, it seems like it got added late yesterday!

Still not able to install it on my system. "Unable to locate package simplescreenrecorder," even after removing and re-adding the PPA, rebooting etc.. Weird. I might be overlooking something else that I need to do to get Ubuntu to "find" the package?

(of course I have done sudo apt update)

---

### Post by deadflowr on 2016-10-16
Expanding the ppa page to view package details shows it failed to build for Yak.

---

