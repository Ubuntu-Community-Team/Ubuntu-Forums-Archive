---
title: "No audio"
date: 2010-02-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2010-02-18
after todays updates I have no audio

```

:~$ lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:22 memory:fdff4000-fdff7fff

*-multimedia
       description: Multimedia audio controller
       product: VT1720/24 [Envy24PT/HT] PCI Multi-Channel Audio Controller
       vendor: VIA Technologies Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ICE1724 latency=64
       resources: irq:21 ioport:ef00(size=32) ioport:ee00(size=128)

``````

:~/Desktop$ aplay -l
**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:3272:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:902:(snd_ctl_open_noupdate) Invalid CTL hw:0
aplay: device_list:232: control open (0): No such file or directory

``````

:~/Desktop$ alsamixer
ALSA lib conf.c:3272:(snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:902:(snd_ctl_open_noupdate) Invalid CTL default
cannot open mixer: No such file or directory

```

---

### Post by MadMan2k on 2010-02-18
yeah, dont upgrade pulseaudio for now. No idea what they broke - the changelog does not seem suspicious...

---

### Post by load.runner on 2010-02-18
I don't know if it's the same problem
I have sound, but very very low (and the volume is at max)
and I get the same errors with aplay and alsamixer

---

### Post by tad1073 on 2010-02-18
guess I will file a bug report

---

### Post by dino99 on 2010-02-18
problem with the new package 0ubuntu8 ?
(i'm listening 0ubuntu6, it's fine)

---

### Post by zika on 2010-02-18
> **dino99 said:**
> problem with the new package 0ubuntu8 ?
(i'm listening 0ubuntu6, it's fine)I just wanted to ask if it is pulseaudio 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu8 or 
pulseaudio 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu7?
I'm on pulseaudio 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu6... It plays OK...
Now, should I upgrade to ubuntu8 or not?
pulseaudio:
  Installed: 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu6
  Candidate: 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu8

---

### Post by tad1073 on 2010-02-18
bug filed 
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/523874](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/523874)

---

### Post by tad1073 on 2010-02-18
pulseaudio:
  Installed: 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu6
  Candidate: 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu6

---

### Post by Schrotthaufen on 2010-02-18
Update is now available. (since ~5 minutes)

I still have to check whether this fixes the bug or not...

---

### Post by zika on 2010-02-18
Upgraded to ubuntu8 and no problems, so far... Huh...
What does this **32** in version stands for?

---

### Post by Schrotthaufen on 2010-02-18
Edit: I had no sound on 6 and 8... strange...

---

### Post by dino99 on 2010-02-18
in doubt, stay with 6 which is good for me, but i've not rebooted since several days and start pulseaudio into console (my hda chipset not recognized)

---

### Post by zika on 2010-02-18
There is a problem:

~$ alsamixer
ALSA lib conf.c:3272: (snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:902: (snd_ctl_open_noupdate) Invalid CTL default
cannot open mixer: No such file or directory

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:3272: (snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:902: (snd_ctl_open_noupdate) Invalid CTL hw:0
aplay: device_list:232: control open (0): No such file or directory
card 1: default [USB Audio DAC   ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have sound in rhythmbox and totem but no sound in any flash... I have pulseaudio set in MultimediaSystemsSelector...

So, there is a problem with ALSA<->PulseAudio integration...

I added this to bug mentioned above...

---

### Post by dino99 on 2010-02-18
unfortunatly we know these problems since jaunty ;)

don't know how to help in this multi embedded problems as apport collect only a part of the big picture and launchpad don't agregate general trouble even if we use ubuntu-bug audio as a generic.

---

### Post by crimsun on 2010-02-18
The root cause of this symptom is a commit in pulseaudio's 0ubuntu7 that broke versioning (see [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/523716](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/523716)). Therefore, when alsa-plugins was uploaded and built against libpulse-dev 0ubuntu7, the pulse plugin was not compiled, which results in the kind of breakage you all have been seeing in this thread.

Recap: cause: pulseaudio (fixed in 0ubuntu8 ); ripple effect into anything building against libpulse-dev, including alsa-plugins (fixed in 0ubuntu5).

In other words, if you run Lucid, you want to update ASAP.

---

### Post by zika on 2010-02-18
There are two bugs seemingly pointing to the same problem, but, I'm not so sure...
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/523874](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/523874)
[https://bugs.launchpad.net/bugs/523716](https://bugs.launchpad.net/bugs/523716)

---

### Post by tad1073 on 2010-02-18
```

:~/Desktop$ apt-cache policy pulseaudio
pulseaudio:
  Installed: 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu8
  Candidate: 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu8
  Version table:
 *** 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu8 0
        500 http://us.archive.ubuntu.com lucid/main Packages
        100 /var/lib/dpkg/status

```

still no sound

---

### Post by crimsun on 2010-02-18
Guys/gals, please *read* what I posted above. Updating pulseaudio is not going to do any good; you need to **_update libasound2-plugins_**. (Of course, you probably want to update pulseaudio packages, too, seeing as they fix other bugs.)

---

### Post by tad1073 on 2010-02-18
> **crimsun said:**
> Guys/gals, please *read* what I posted above. Updating pulseaudio is not going to do any good; you need to **_update libasound2-plugins_**. (Of course, you probably want to update pulseaudio packages, too, seeing as they fix other bugs.)

what is the latest version?

here is what I have.

```

:~/Desktop$ apt-cache policy libasound2-plugins
libasound2-plugins:
  Installed: 1.0.22-0ubuntu4
  Candidate: 1.0.22-0ubuntu4
  Version table:
 *** 1.0.22-0ubuntu4 0
        500 http://us.archive.ubuntu.com lucid/main Packages
        100 /var/lib/dpkg/status
thomas@thomthom:~/Desktop$ apt-cache policy libasound2
libasound2:
  Installed: 1.0.22-0ubuntu2
  Candidate: 1.0.22-0ubuntu2
  Version table:
 *** 1.0.22-0ubuntu2 0
        500 http://us.archive.ubuntu.com lucid/main Packages
        100 /var/lib/dpkg/status

```

---

### Post by zika on 2010-02-18
> **crimsun said:**
> Guys/gals, please *read* what I posted above. Updating pulseaudio is not going to do any good; you need to **_update libasound2-plugins_**. (Of course, you probably want to update pulseaudio packages, too, seeing as they fix other bugs.)But, how to **_update libasound2-plugins_**? I have everything upgraded...
~$ apt-cache policy libasound2-plugins
libasound2-plugins:
  Installed: 1.0.22-0ubuntu4
  Candidate: 1.0.22-0ubuntu4
~$ apt-cache policy pulseaudio
pulseaudio:
  Installed: 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu8
  Candidate: 1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu8
~$ apt-cache policy alsa-base
alsa-base:
  Installed: 1.0.22.1+dfsg-0ubuntu3
  Candidate: 1.0.22.1+dfsg-0ubuntu3

---

### Post by crimsun on 2010-02-18
> **zika said:**
> But, how to **_update libasound2-plugins_**? I have everything upgraded...

No, you don't. As I just pointed out in e-mail to you, your version of libasound2-plugins is the broken one.

---

### Post by crimsun on 2010-02-18
> **tad1073 said:**
> what is the latest version?

here is what I have.

```

:~/Desktop$ apt-cache policy libasound2-plugins
libasound2-plugins:
  Installed: 1.0.22-0ubuntu4
  Candidate: 1.0.22-0ubuntu4
  Version table:
 *** 1.0.22-0ubuntu4 0
        500 http://us.archive.ubuntu.com lucid/main Packages
        100 /var/lib/dpkg/status

```

0ubuntu4 is the **_broken_** one. Please update.

---

### Post by zika on 2010-02-18
> **crimsun said:**
> No, you don't. As I just pointed out in e-mail to you, your version of libasound2-plugins is the broken one.Sorry, I've not checked my e-mail last two minutes... Off to my mailbox...
> 0ubuntu4 is, of course, the broken version.
OK, but what is the action that should be taken, on my side, to remedy that?

---

### Post by tad1073 on 2010-02-18
> **crimsun said:**
> 0ubuntu4 is the **_broken_** one. Please update.

updates not pulling down anything new from main or us

---

### Post by tad1073 on 2010-02-18
> **zika said:**
> Sorry, I've not checked my e-mail last two minutes... Off to my mailbox...

OK, but what is the action that should be taken, on my side, to remedy that?

yes, what you said...

---

### Post by crimsun on 2010-02-18
> **tad1073 said:**
> updates not pulling down anything new from main or us

Be patient; updates are only farmed out once per hour. If you really want the fixed deb, choose your arch under "Builds" at [https://edge.launchpad.net/ubuntu/+source/alsa-plugins/1.0.22-0ubuntu5](https://edge.launchpad.net/ubuntu/+source/alsa-plugins/1.0.22-0ubuntu5), and download the deb from "Built files".

---

### Post by zika on 2010-02-18
> **crimsun said:**
> Be patient; updates are only farmed out once per hour. If you really want the fixed deb, choose your arch under "Builds" at [https://edge.launchpad.net/ubuntu/+source/alsa-plugins/1.0.22-0ubuntu5](https://edge.launchpad.net/ubuntu/+source/alsa-plugins/1.0.22-0ubuntu5), and download the deb from "Built files".This answer satisfies me completely. I'm not inpatient, sorry if You've got that impression. Thank You. I know how things work and I really do appreciate all Your work...

---

### Post by zika on 2010-02-18
> **crimsun said:**
> Be patient; updates are only farmed out once per hour. If you really want the fixed deb, choose your arch under "Builds" at [https://edge.launchpad.net/ubuntu/+source/alsa-plugins/1.0.22-0ubuntu5](https://edge.launchpad.net/ubuntu/+source/alsa-plugins/1.0.22-0ubuntu5), and download the deb from "Built files".~$ apt-cache policy libasound2-plugins
libasound2-plugins:
  Installed: 1.0.22-0ubuntu5
  Candidate: 1.0.22-0ubuntu5
~$ alsamixer
ALSA lib conf.c:3272: (snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:902: (snd_ctl_open_noupdate) Invalid CTL default
cannot open mixer: No such file or directory
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:3272: (snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:902: (snd_ctl_open_noupdate) Invalid CTL hw:0
aplay: device_list:232: control open (0): No such file or directory
card 1: default [USB Audio DAC   ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


No sound in Flash still...

---

### Post by crimsun on 2010-02-18
> **zika said:**
> ~$ apt-cache policy libasound2-plugins
libasound2-plugins:
  Installed: 1.0.22-0ubuntu5
  Candidate: 1.0.22-0ubuntu5
~$ alsamixer
ALSA lib conf.c:3272: (snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:902: (snd_ctl_open_noupdate) Invalid CTL default
cannot open mixer: No such file or directory
~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
ALSA lib conf.c:3272: (snd_config_hooks_call) Cannot open shared library libasound_module_conf_pulse.so
ALSA lib control.c:902: (snd_ctl_open_noupdate) Invalid CTL hw:0
aplay: device_list:232: control open (0): No such file or directory
card 1: default [USB Audio DAC   ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


No sound in Flash still...

First, make sure the file actually exists in /usr/lib/alsa-lib/ . Next, reboot. If the symptom remains reproducible, please use strace and attach the output here, e.g.,

strace -f -o output.txt alsamixer

---

### Post by zika on 2010-02-18
> **crimsun said:**
> First, make sure the file actually exists in /usr/lib/alsa-lib/ . Next, reboot. If the symptom remains reproducible, please use strace and attach the output here, e.g.,

strace -f -o output.txt alsamixer
/usr/lib/alsa-lib$ ls libasound_module_conf_pulse.so -lt
-rw-r--r-- 1 root root 6184 2010-02-18 16:11 libasound_module_conf_pulse.so
I did reboot before I posted my previous answer...
Here comes the output of strace...

---

### Post by dino99 on 2010-02-18
> **crimsun said:**
> First, make sure the file actually exists in /usr/lib/alsa-lib/ . Next, reboot. If the symptom remains reproducible, please use strace and attach the output here, e.g.,

strace -f -o output.txt alsamixer

thanks for the time you share with us about this problem.

but do you realised, devs, all the troubles made by updating packages with one or more packages left behind with errors: forum flood, a bunch of report-bugs sended and add more triaging, buzz ...

please don't create more troubles than necessary.

hey, don't want to be rude ;)

---

### Post by rafalcieslak on 2010-02-18
I updated to 1.0.22-0ubuntu5 and still have no sound. My strace result was mainly the same as Zika's, it seems a program looks for libasound_module_conf_pulse.so in wrong directories. My workaround is ```
sudo cp -l /usr/lib/alsa-lib/libasound_module_conf_pulse.so /usr/lib/libasound_module_conf_pulse.so 

```,
which prevents any errors, everything now runs properly, but I still cannot hear any sound...

---

### Post by zika on 2010-02-18
> **dino99 said:**
> thanks for the time you share with us about this problem.

but do you realised, devs, all the troubles made by updating packages with one or more packages left behind with errors: forum flood, a bunch of report-bugs sended and add more triaging, buzz ...

please don't create more troubles than necessary.

hey, don't want to be rude ;)Errors do occur even in the best organized environments. So, I think, that fact should be, only, appreciated... The important thing is to help correct them. That is the only reason I'm involved in this. My knowledge is not good enough to make anything more that provide required data that could help... As far as I can see, looking at the Launchpad, error was spotted and solution is available. Just wait until new build is cooked for us...

---

### Post by dino99 on 2010-02-18
> **zika said:**
> Errors do occure even in the best organized environments. So, I think, that fact should be, only, appreciated... The important thing is to help correct them. That is the only reason I'm involved in this. My knowledge is not good enough to make anything more that provide required data that could help... As far as I can see, looking at the Launchpad, error was spotted and solution is available. Just wait until new build is cooked for us...

agree 100 % :D

---

### Post by zika on 2010-02-18
> **dino99 said:**
> agree 100 % :DI only wish I could be of more help in solving two bugs that makes my usage of LL less enjoyable: shutdown and random freezes... The first I solve with a switch and the other with not using KMS, but...

---

### Post by godhika on 2010-02-18
Hmmm. Got the newest libasound-plugin but still no sound

---

### Post by tad1073 on 2010-02-18
> **godhika said:**
> Hmmm. Got the newest libasound-plugin but still no sound

same here

---

### Post by paok4 on 2010-02-18
the same for me ... is there any other way to fix this ??? (rollback someway maybe to the previous packages of pulse audio ) or we just have to wait for a new update ???

---

### Post by zika on 2010-02-18
You are getting ubuntu5 version of plugins that I took from the builds and that doesn't work either. Solution is found, it'll come with ubuntu6 version, hopefully...
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/523716](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/523716)

---

### Post by zika on 2010-02-18
After some time away from the machine and reboot or two, one upgrade, I think, I have everything working... Flash, alsamixer...? I'll try to see what was upgraded in the meantime...
As far as I can see,nothing from the list of packages from this thread...

libasound2-plugins was not upgraded through aptitude, it was upgraded directly from .deb...

---

### Post by zika on 2010-02-18
I've lost sound in Flash, again, with no reboot, and several upgrades:
> Aptitude 0.4.11.11: log report
Thu, Feb 18 2010 19:11:27 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 3 packages, and remove 0 packages.
4,096B of disk space will be used
===============================================================================
[UPGRADE] libindicate-gtk2 0.3.2-0ubuntu1 -> 0.3.3-0ubuntu1
[UPGRADE] libindicate4 0.3.2-0ubuntu1 -> 0.3.3-0ubuntu1
[UPGRADE] libindicator0 0.3.2-0ubuntu1 -> 0.3.3-0ubuntu1
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Thu, Feb 18 2010 21:31:57 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 8 packages, and remove 0 packages.
418kB of disk space will be used
===============================================================================
[UPGRADE] indicator-me 0.2.3-0ubuntu2 -> 0.2.4-0ubuntu1
[UPGRADE] indicator-sound 0.1.0-0ubuntu2 -> 0.1.1-0ubuntu2
[UPGRADE] libasound2 1.0.22-0ubuntu2 -> 1.0.22-0ubuntu3
[UPGRADE] libdbusmenu-glib1 0.2.4-0ubuntu1 -> 0.2.5-0ubuntu1
[UPGRADE] libdbusmenu-gtk1 0.2.4-0ubuntu1 -> 0.2.5-0ubuntu1
[UPGRADE] rhythmbox 0.12.6-1ubuntu10 -> 0.12.6git20100218-0ubuntu1
[UPGRADE] rhythmbox-plugin-cdrecorder 0.12.6-1ubuntu10 -> 0.12.6git20100218-0ubuntu1
[UPGRADE] rhythmbox-plugins 0.12.6-1ubuntu10 -> 0.12.6git20100218-0ubuntu1
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Thu, Feb 18 2010 21:44:49 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 0 packages, and remove 0 packages.
===============================================================================
===============================================================================

Log complete.
Aptitude 0.4.11.11: log report
Thu, Feb 18 2010 22:39:02 +0100

IMPORTANT: this log only lists intended actions; actions which fail due to
dpkg problems may not be completed.

Will install 2 packages, and remove 0 packages.
90.1kB of disk space will be used
===============================================================================
[UPGRADE] indicator-messages 0.3.1-0ubuntu2 -> 0.3.2-0ubuntu1
[UPGRADE] indicator-session 0.2.2-0ubuntu2 -> 0.2.3-0ubuntu1
===============================================================================
...

---

### Post by Ibidem on 2010-02-18
Have you tried checking if Lucid muted the sound for you?
 I used pavucontrol (pulseaudio)

---

### Post by LADmaticCA on 2010-02-18
I too have lost sound in flash under firefox. Audio appears fine everywhere else though.

---

### Post by Didius Falco on 2010-02-18
I lost all sound after updating today. I have libasound2-plugins v1.0.22-0ubuntu5_i386 installed.

I read through the bug report and my symptoms are identical. From the bug report, it seems like the best thing to do at this point is just wait for another update to fix it...

---

### Post by crimsun on 2010-02-19
Issues are fixed; fixed source packages of alsa-lib and pulseaudio have been uploaded and built for the majority of supported platforms. Be aware that it may be some hours until your mirror has the available packages:

[https://edge.launchpad.net/ubuntu/+source/alsa-lib/1.0.22-0ubuntu4](https://edge.launchpad.net/ubuntu/+source/alsa-lib/1.0.22-0ubuntu4)

[https://edge.launchpad.net/ubuntu/+source/pulseaudio/1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu9](https://edge.launchpad.net/ubuntu/+source/pulseaudio/1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu9)

---

### Post by dino99 on 2010-02-19
> **crimsun said:**
> Issues are fixed; fixed source packages of alsa-lib and pulseaudio have been uploaded and built for the majority of supported platforms. Be aware that it may be some hours until your mirror has the available packages:

[https://edge.launchpad.net/ubuntu/+source/alsa-lib/1.0.22-0ubuntu4](https://edge.launchpad.net/ubuntu/+source/alsa-lib/1.0.22-0ubuntu4)

[https://edge.launchpad.net/ubuntu/+source/pulseaudio/1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu9](https://edge.launchpad.net/ubuntu/+source/pulseaudio/1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu9)

ok, these packages make sound working again. But pulseaudio still does not start by itself, need to start it into console.

Before starting it, if i check system/pref/sound: a popup say it's waiting for response ( no sound hardware detected).
After started it, sound pref popup open but "hardware tab" still empty, but sound work.

got these errors:

W: module.c: module-detect is deprecated: Please use module-udev-detect instead of module-detect!

 --disallow-module-loading not defined

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/519387](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/519387)

---

### Post by zika on 2010-02-19
> **Ibidem said:**
> Have you tried checking if Lucid muted the sound for you?
 I used pavucontrol (pulseaudio)The first thing I did.

---

### Post by paok4 on 2010-02-19
After the new update this morning everything is OK !!!

Great job guys !!!

---

### Post by zika on 2010-02-19
It looks OK...

---

### Post by Didius Falco on 2010-02-19
> **crimsun said:**
> Issues are fixed; fixed source packages of alsa-lib and pulseaudio have been uploaded and built for the majority of supported platforms. Be aware that it may be some hours until your mirror has the available packages.

Thanks Crimsun, and please pass my thanks along the chain. Audio is back to it's previous superb performance.

Y'all rock, and I'm rocking now too, thanks to y'all. <G>

---

### Post by zika on 2010-02-19
> **didius falco said:**
> thanks crimsun, and please pass my thanks along the chain. Audio is back to it's previous superb performance.

Y'all rock, and i'm rocking now too, thanks to y'all. <g>+1!

---

### Post by lion1969 on 2010-02-19
thanks a lot crimsum
fantastic speedy fix

---

### Post by Jackzor on 2010-02-19
My sound worked when I first upgraded from 9.10 to 10.04 last night but then it quit working with an update I did soon after the upgrade. Afew hours ago I updated again and it fixed the sound. I ended up waking my girlfriend up with how loud I had my volume turned up...(lol) anyways. I have restarted the computer and its not working again. When it does its really quite and if I try to play a song off my computer it starts halfway through and won't let me start it from the beginning...

Is this new? Has anyone else had this happen? Do I need to file my own bug report?

---

### Post by crimsun on 2010-02-19
> **Jackzor said:**
> My sound worked when I first upgraded from 9.10 to 10.04 last night but then it quit working with an update I did soon after the upgrade. Afew hours ago I updated again and it fixed the sound. I ended up waking my girlfriend up with how loud I had my volume turned up...(lol) anyways. I have restarted the computer and its not working again. When it does its really quite and if I try to play a song off my computer it starts halfway through and won't let me start it from the beginning...

Is this new? Has anyone else had this happen? Do I need to file my own bug report?

Your description of the symptom(s) is pretty vague; please use "ubuntu-bug -s".

---

### Post by dino99 on 2010-02-19
> **crimsun said:**
> Your description of the symptom(s) is pretty vague; please use "ubuntu-bug -s".

hm, don't know what "-s" add to ubuntu-bug, i should find and read the doc ;)

---

### Post by mihamtalamac on 2010-02-19
> **crimsun said:**
> Issues are fixed; fixed source packages of alsa-lib and pulseaudio have been uploaded and built for the majority of supported platforms. Be aware that it may be some hours until your mirror has the available packages:

[https://edge.launchpad.net/ubuntu/+source/alsa-lib/1.0.22-0ubuntu4](https://edge.launchpad.net/ubuntu/+source/alsa-lib/1.0.22-0ubuntu4)

[https://edge.launchpad.net/ubuntu/+source/pulseaudio/1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu9](https://edge.launchpad.net/ubuntu/+source/pulseaudio/1:0.9.22~0.9.21+stable-queue-32-g8478-0ubuntu9)
could you please tell which repository to use when downloading this update? i just installed Ubuntu 9.10, updated, and have no sound. at first time, only flash didn't work, but now i have no sound at all.
Thanks in advance

---

### Post by LKjell on 2010-02-19
> **mihamtalamac said:**
> could you please tell which repository to use when downloading this update? i just installed Ubuntu 9.10, updated, and have no sound. at first time, only flash didn't work, but now i have no sound at all.
Thanks in advance

The main server should have it.

---

### Post by zika on 2010-02-19
> **mihamtalamac said:**
> could you please tell which repository to use when downloading this update? i just installed Ubuntu 9.10, updated, and have no sound. at first time, only flash didn't work, but now i have no sound at all.
Thanks in advanceSorry if I ask You about a thing You've checked already, but, did You check that volume is not muted (alsamixer or gnome-volume-control-applet)...?
Dobrodo&#353;li na Forum...
(Welcome to the Forum...)

---

### Post by mihamtalamac on 2010-02-19
just to add, on a Hardware tab under Sound Preferences I don't see any Device. I enabled some chanels with Gnome ALSA mixer, and now i get sound from audio and video players (Mplayer and Amarok), but flash still doesn't work

---

### Post by mihamtalamac on 2010-02-19
> **zika said:**
> Sorry if I ask You about a thing You've checked already, but, did You check that volume is not muted (alsamixer or gnome-volume-control-applet)...?
Dobrodo&#353;li na Forum...
(Welcome to the Forum...)
i just upgraded my system from main server and problem persists. versions of theese two files I have are:
- libasound2-plugins v1.0.20-1ubuntu8
- pulseaudio v 1:0.9.19-0ubuntu4.1

to Zika : Hvala na dobrodoslici ;)

---

### Post by Elfy on 2010-02-19
> **mihamtalamac said:**
> i just upgraded my system from main server and problem persists. versions of theese two files I have are:
- libasound2-plugins v1.0.20-1ubuntu8
- pulseaudio v 1:0.9.19-0ubuntu4.1

to Zika : Hvala na dobrodoslici ;)

Do you know that we are talking about the packages in the 10.04 alpha version.

> i just installed Ubuntu 9.10, updatedI assume that you are not using the development version.

---

### Post by zika on 2010-02-19
> **forestpiskie said:**
> Do you know that we are talking about the packages in the 10.04 alpha version.

I assume that you are not using the development version.You might be right. When I read the message I assumed that "upgraded" meant "from 9.10 to 10.04"... Silly me...

---

### Post by benblout on 2010-02-19
I had this same problem.  For me, choosing the menu option System->prefences->Volume_control brought up a volume control showing that the Output volume was muted, even though the volume control in the notification are did not.  I unmuted, and a day of silence was ended.

---

### Post by david20063 on 2010-02-20
Finally got my sound back on, type alsamixer in the terminal and realized my speaker volume had been turned all the way down turned it back up and like that I had sound again

---

### Post by mihamtalamac on 2010-02-23
> **forestpiskie said:**
> Do you know that we are talking about the packages in the 10.04 alpha version.

I assume that you are not using the development version.
i figured it out at some point that this is developer thread. i just typed "ubuntu no audio" in Google and it led me to this page (i didn't checked the name of the thread) and that's why i ended up here.
anywawy, i solved this problem of mine. what i did was to disable software modem on my laptop and the sound works great now. no need to restart ALSA on every boot (which was the only thing that made my sound working).
if theese kind of things happens on 9.10 you should make sure that it don't happen on version 10.04.
good luck in development

---

