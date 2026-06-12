---
title: "How to switch graphic drivers? Nouveau to Nvidia official"
date: 2014-02-28
forum: Installation &amp; Upgrades
---

### Post by chaushev on 2014-02-28
Ubuntu 13.10 Unity x64bit on Lenovo G560
```
Linux lenovo 3.11.0-17-generic #31-Ubuntu SMP Mon Feb 3 21:52:43 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

GPU - Nvidia 310M
```
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GT218M [GeForce 310M] [10de:0a75] (rev a2)
    Subsystem: Lenovo Device [17aa:392d]
```
Current driver in use: X.org server: Nouveau
I wish to disable/remove Nouveau and install the newest from nvidia official download page for various reasons.
[http://www.nvidia.com/download/driverResults.aspx/73221/en-us](http://www.nvidia.com/download/driverResults.aspx/73221/en-us) -                                                                                               331.49                                             

I would appreciate if you could provide me detailed instructions as I am a new linux user. 
Do you think I should Install these drivers from nvidia website or chose some of the ones listet in the Additional drivers tab?
[ATTACH=CONFIG]250771[/ATTACH]
Thanks in advance!

---

### Post by slickymaster on 2014-02-28
[BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by grahammechanical on 2014-02-28
What is wrong with the ones from the Additional Drivers tab? Ah, the latest and greatest myth. By activating a proprietary video driver we de-activate the open source driver. The Additional Drivers utility does a good job of doing that in my experience.

If you remove Nouveau you may find that when you need to use Recovery mode there are problems with getting to a desktop. Recovery Resume in 13.10 uses llvmpipe which is part of the open source video driver. Do not remove Nouveau. Just de-activate it.

Regards.

---

### Post by chaushev on 2014-03-01
[COLOR=#333333][FONT=lucida grande]I have already checked the link that you gave me - it doesnt clear enough things for me. The reason I want to switch drivers is because I cannot use the sleep/suspend/hibernate options. When waking or resuming system I get a blank screen with working cursor or sometimes no cursor at all. From what I have read problem might be caused by nvidia drivers.Another issue I came across today, which probably has nothing to do with gpu drivers, but I might as well post it here. Suddenly the window controls color has faded?! I have not touched any settings - just like that. Screenshots below show what I mean. First image is before next after. Do you got any idea how to fix that? It is driving me crazy!
Before:
[/FONT][/COLOR][ATTACH=CONFIG]250799[/ATTACH]
After:
[ATTACH=CONFIG]250800[/ATTACH]

---

### Post by chaushev on 2014-03-02
I found a way to switch to the newest drivers from nvidia's website. In my case version 331.49. Here is what I did:
> [FONT=Verdana]Ubuntu 13.10, just like its predecessors, benefits from a large repository, but Canonical developers don&#8217;t upload the most recent version of the driver for several considerations. The most important is that it they don&#8217;t risk uploading a piece of software that has yet to be proven stable.[/FONT]

[FONT=Verdana]Fortunately, there is a PPA that makes available the latest versions of the drivers, a day or two after the launch. Just enter the following command in a terminal (you will need root access):[/FONT]

[COLOR=#008080][FONT=Verdana]```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-331
```[/FONT][/COLOR]

[FONT=Verdana]If you already have an older version of the driver you will need to replace the last command with [/FONT][COLOR=#008080][FONT=Verdana]sudo apt-get dist-upgrade[/FONT][/COLOR]

[FONT=Verdana]After the process is finished, restart the computer and you&#8217;re set. The next time NVIDIA releases a new driver, you will only have to update the system, without adding the PPA.[/FONT]
What this does is it adds newest drivers in the Additional drivers tab and you can choose the lastest ones.

---

