---
title: "No Sound in Gutsy"
date: 2008-01-20
forum: Installation &amp; Upgrades
---

### Post by VoiceOvGod on 2008-01-20
I am not getting sound from my onboard soundcard.

I tried to click on preferences, and I get the following:

```
No volume control GStreamer plugins and/or devices found.
```


When attempting to access Restricted Drivers, I get this:
```

You need to install the package

  linux-restricted-modules-2.6.15-23-386

for this program to work.

```


I tried to follow this:

[https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29%C%28intel%29](https://help.ubuntu.com/community/HdaIntelSoundHowto?highlight=%28hda%29%C%28intel%29)

When I tried to run sudo ./configure I get the following:

```
$ sudo ./configure
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

```

I have the Nvidia CK804 for my soundcard

---

### Post by Pumalite on 2008-01-20
Post:
lshw -C sound

---

### Post by VoiceOvGod on 2008-01-20
```
lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2

```

---

### Post by Pumalite on 2008-01-20
Bad news. Your Sound card was not recognized by the kernel. I'm in a new system; I have to reboot to give you some instructions. I'll be back.

---

### Post by VoiceOvGod on 2008-01-20
Lovely.

The odd thing is that it's worked before, and the LiveCD audio worked fine too.

---

### Post by Pumalite on 2008-01-20
Run this at the Terminal:
sudo apt-get install linux-backports-modules-generic
Reboot. Post again:
lshw -C sound

---

### Post by VoiceOvGod on 2008-01-20
```
 *-multimedia            
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: driver=Intel ICH latency=0 maxlatency=5 mingnt=2 module=snd_intel8x0

```

---

### Post by VoiceOvGod on 2008-01-20
Hrm, that allowed me to also access the restricted drivers.

I tried to install the Nvidia proprietary drivers, and now, my X is showing up in low graphics mode.

---

### Post by Pumalite on 2008-01-20
+

---

### Post by Pumalite on 2008-01-20
Type in Terminal:
alsamixer
And tell me what you see or post a screenshot.

---

### Post by VoiceOvGod on 2008-01-20
```
~$ lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2
~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
 

```

Had some issues after trying to install the backport. Ended up having to reinstall.

---

### Post by Pumalite on 2008-01-21
Run my command again.

---

### Post by VoiceOvGod on 2008-01-21
```
~$ sudo apt-get install linux-backports-modules-generic
[sudo] password for :
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-backports-modules-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
~$ lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@0000:00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2

```

---

### Post by Pumalite on 2008-01-21
Looks like you have to get a Sound Blaster

---

### Post by VoiceOvGod on 2008-01-21
Keep in mind because I reinstalled, I don't have any additional packages installed right now.

And Synaptic won't register updates either, it says my system is up to date, I haven't actually updated anything yet.

---

### Post by Pumalite on 2008-01-21
How did you get this then:
'sudo apt-get install linux-backports-modules-generic'??
(You ran my command)

---

### Post by VoiceOvGod on 2008-01-21
Sorry, let me clarify:

I did not update anything (i.e. security, etc)

All that I have installed was the backports, and alsamixergui (the latter of the two from the package manager).

I enabled all the repositories, but did not install anything else.

---

### Post by Pumalite on 2008-01-21
Well, let me know if you need help when you have done everything.

---

### Post by VoiceOvGod on 2008-01-21
Ok, got nearly everything updated, but I am getting the following:

```
E: /var/cache/apt/archives/linux-headers-2.6.22-14_2.6.22-14.47_all.deb: corrupted filesystem tarfile - corrupted package archive
```

---

### Post by Pumalite on 2008-01-21
I would stick to 14.46

---

### Post by VoiceOvGod on 2008-01-21
Ok I rebooted.

Also appears that the Optical drives are not being able to read some disks (i.e. Ubuntu Disk) but others, such as an audio CD are.

```
Cannot mount volume.

The volume 'Ubuntu 7.10 i386' uses the  file system which is not supported by your system.


```

---

### Post by VoiceOvGod on 2008-01-23
```
lshw -C sound
WARNING: you should run this program as super-user.
  *-multimedia UNCLAIMED  
       description: Multimedia audio controller
       product: CK804 AC'97 Audio Controller
       vendor: nVidia Corporation
       physical id: 4
       bus info: pci@00:04.0
       version: a2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=0 maxlatency=5 mingnt=2
       resources: ioport:f000-f0ff ioport:ec00-ecff iomemory:febfd000-febfdfff irq:11

```

This is after a fresh install of 7.04, and updates.

---

### Post by dominik_ap on 2008-01-31
Hi i have also a problem with sound in Gutsy. It was working few weeks, but now it doesnt. I tried to run Amarok from the console and it wrote:
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Hi i have Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?

And when i tried lshw -C sound
it wrote:
WARNING: you should run this program as super-user.
/proc/cpuinfo

and nothing more, i cant write more to console, so where is the problem?


I dont know what does it mean, but its not good :) can you help me please somehow? I can send you more info if you need something

---

### Post by Pumalite on 2008-01-31
Did you update or upgrade recently?

---

### Post by dominik_ap on 2008-02-01
> **Pumalite said:**
> Did you update or upgrade recently?

Hi yes i think i did, i do it usually, so maybe some package caused it, but i have no idea which one...

---

### Post by Pumalite on 2008-02-01
Was it 'update' or 'upgrade' that did it?

---

### Post by dominik_ap on 2008-02-01
> **Pumalite said:**
> Was it 'update' or 'upgrade' that did it?

Well i think it was just update of some packages, BTW what is the difference between update and upgrade? Upgrade means to have new version of Ubuntu? (like from Feitsy to Gutsy?)
If yes, then i did just update, i am going on gutsy from my beginnings with linux (few months)

Hm it really seems to be like some problem with packages, when i tried somthing with Timidity (or what is the name) there was an error connected with Amarok and some other libraries / but i am not sure what it wrote, sorry i wasnt able to safe it and post on internet at this time)

---

### Post by Pumalite on 2008-02-01
If you cannot use your Terminal, your problem is more than sound.

---

### Post by dominik_ap on 2008-02-02
> **Pumalite said:**
> If you cannot use your Terminal, your problem is more than sound.

Hehe thank you for your great piece of advice...:)

i will try to call this error with timidity again and if i will have the results i will post it here

---

### Post by Pumalite on 2008-02-02
I mean, if you cannot use your Terminal, is better to do a clean install.

---

### Post by arman.haghi on 2008-02-09
One *Possible* Solution:

I have the same hardware (Abit Mobo with CK804 / AC'97 audio) and had the same problem; After ensuring Kubuntu was [_[COLOR="Blue"]recognising my hardware[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=205449") etc I kept searching for 'software' answers, but it turned out to be a hardware issue all along.

I was modding my box and had removed the front panel audio connections from my mobo. Having no connectors, I've learnt, disables the back panel audio unless you use jumpers across 5/6 and 9/10. Also, ensure that onboard sound is enabled (or auto) in your BIOS menu.

i.e.

If pins are

[FONT="Courier New"]: : : ' :[/FONT]

aka

[FONT="Courier New"]2  4  6  8  10
1  3  5     9 [/FONT]

then jumpers should be placed across 5/6 and 9/10

so

[FONT="Courier New"]: : | ' |[/FONT]

aka

[FONT="Courier New"]2  4  |  8  |
1  3  |     |[/FONT]


Hope this helps,

Arman.

NOTE: Check your motherboard manual first, hardware may vary.

My manual (ala example above) was at
[http://file.abit.com.tw/pub/download/manual/english/kn8-sli.zip]("http://file.abit.com.tw/pub/download/manual/english/kn8-sli.zip")

Solution Source
[http://forums.fedoraforum.org/showthread.php?t=171686]("http://forums.fedoraforum.org/showthread.php?t=171686")

---

