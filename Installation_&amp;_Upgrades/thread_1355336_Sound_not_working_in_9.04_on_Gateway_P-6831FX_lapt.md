---
title: "Sound not working in 9.04 on Gateway P-6831FX laptop"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by darkyre on 2009-12-14
After lurking and Googling for far too long, I've decided I need your guys direct help here. I'm running a fresh install of 9.04 after reformatting from 9.10/Vista dual-boot setup thinking that it would alleviate my sound problems (no sound). I still have no sound, but it seems like a different set of problems altogether (although I lack the expertise to be sure). I'm running a Gateway P-6831FX laptop from 2008 with an Intel(R) Core(TM)2 Duo T9300 @ 2.50GHz (non-stock), and a Sigmatel 92HD71B Dual SPDF sound card. Unfortunately, I've heard that both Gateway and Sigmatel no longer exist, so this problem is a bit daunting to say the least.

This thread seemed to go in the right direction, but didn't end up solving my problem.
[http://ubuntuforums.org/showthread.php?t=676550](http://ubuntuforums.org/showthread.php?t=676550)

I've also got this nice link that might help someone more informed than me.
[http://www.alsa-project.org/db/?f=6b8e1ccbc5633b4f1231b9818e01f881823713de](http://www.alsa-project.org/db/?f=6b8e1ccbc5633b4f1231b9818e01f881823713de)

And here are some of the juicy bits:

```
!!################################
!!ALSA Information Script v 0.4.58
!!################################

!!Script ran on: Tue Dec 15 00:10:50 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu 9.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.04"


!!DMI Information
!!---------------

Manufacturer:      Gateway
Product Name:      P-6831FX


!!Kernel Information
!!------------------

Kernel release:    2.6.28-17-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.18rc3
Library version:    1.0.18
Utilities version:  1.0.18


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf4600000 irq 22


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```

Thanks for your help :)
Best of luck to whoever tries to help me out.
I'll try to check this post periodically so I can provide any necessary information to you guys.

I've already tried a handful of fixes that I don't quite comprehend (I've noticed that a majority of you skilled *nix using folks seem to be better at fixing problems than explaining solutions, but no complaints, it gets the job done), so apologies if I broke it even more than before.

---

### Post by phillw on 2009-12-14
> **darkyre said:**
> After lurking and Googling for far too long, I've decided I need your guys direct help here. I'm running a fresh install of 9.04 after reformatting from 9.10/Vista dual-boot setup thinking that it would alleviate my sound problems (no sound). I still have no sound, but it seems like a different set of problems altogether (although I lack the expertise to be sure). I'm running a Gateway P-6831FX laptop from 2008 with an Intel(R) Core(TM)2 Duo T9300 @ 2.50GHz (non-stock), and a Sigmatel 92HD71B Dual SPDF sound card. Unfortunately, I've heard that both Gateway and Sigmatel no longer exist, so this problem is a bit daunting to say the least.

This thread seemed to go in the right direction, but didn't end up solving my problem.
[http://ubuntuforums.org/showthread.php?t=676550](http://ubuntuforums.org/showthread.php?t=676550)

I've also got this nice link that might help someone more informed than me.
[http://www.alsa-project.org/db/?f=6b8e1ccbc5633b4f1231b9818e01f881823713de](http://www.alsa-project.org/db/?f=6b8e1ccbc5633b4f1231b9818e01f881823713de)

And here are some of the juicy bits:

```
!!################################
!!ALSA Information Script v 0.4.58
!!################################

!!Script ran on: Tue Dec 15 00:10:50 UTC 2009


!!Linux Distribution
!!------------------

Ubuntu 9.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 9.04"


!!DMI Information
!!---------------

Manufacturer:      Gateway
Product Name:      P-6831FX


!!Kernel Information
!!------------------

Kernel release:    2.6.28-17-generic
Operating System:  GNU/Linux
Architecture:      i686
Processor:         unknown
SMP Enabled:       Yes


!!ALSA Version
!!------------

Driver version:     1.0.18rc3
Library version:    1.0.18
Utilities version:  1.0.18


!!Loaded ALSA modules
!!-------------------

snd_hda_intel


!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No


!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf4600000 irq 22


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

```Thanks for your help :)
Best of luck to whoever tries to help me out.
I'll try to check this post periodically so I can provide any necessary information to you guys.

I've already tried a handful of fixes that I don't quite comprehend (I've noticed that a majority of you skilled *nix using folks seem to be better at fixing problems than explaining solutions, but no complaints, it gets the job done), so apologies if I broke it even more than before.

Hi, I also have a gateway computer.

Things that kill audio ... the modem driver - not having the restricted repositries loaded
and the default of having the sound muted in System --> Preferences --> Sound.

Does the Sound area show your Hardware, or is it set to nothing ?

The general area for the sound codecs is over here -->  [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

you'll be wanting the [B][Click here to install the ubuntu-restricted-extras package]("apt:ubuntu-restricted-extras?section=universe?section=multiverse")  part of it

Phill.
[/B]

---

### Post by darkyre on 2009-12-14
I've already unmuted everything in alsamixer, and I just installed the restricted extras from that link.

Here's a screencap of a failing audio test if that's of any use.
[http://img189.imageshack.us/img189/4716/screenshotutw.png](http://img189.imageshack.us/img189/4716/screenshotutw.png)
You can see my current playback option selected in the cap, the HDA Intel STAC92xx (lets me choose between digital and analog ALSA and 3 different analog OSS choices), as well as ALSA, OSS, PulseAudio, and auto detect. I dont even know if any of those are right, or if something's missing. 

Oh, and how would I go about tweaking the modem driver if it is messing everything up?

I'm gonna restart to see if anything has changed, and I'll be back after the break.

---

### Post by phillw on 2009-12-14
Okies. I went thru this thread (the sticky) [http://ubuntuforums.org/showthread.php?t=1307019](http://ubuntuforums.org/showthread.php?t=1307019)  and got mine working. Can't, for the life of me, remember which one it was - but i started at the end and worked backwards - if that makes any sense !!

Phill.

---

### Post by darkyre on 2009-12-15
No luck yet, but I have more suspicious stuff to post up in here while I continue this investigation.

```
zachary@laptop:~$ sudo alsa force-reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/zachary/.gvfs
      Output information may be incomplete.
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/zachary/.gvfs
      Output information may be incomplete.
Unloading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-intel snd-hda-codec-idt snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-alloc.
Loading ALSA sound driver modules: snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-seq-device snd-pcm-oss snd-mixer-oss snd-hda-intel snd-hda-codec-idt snd-hda-codec snd-hwdep snd-pcm snd-timer snd-page-allocWARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
WARNING: /etc/modprobe.d/alsa-base.conf.save line 45: ignoring bad line starting with 'sdfsdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 49: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 50: ignoring bad line starting with 'sdf'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 51: ignoring bad line starting with 'sd'
WARNING: /etc/modprobe.d/alsa-base.conf.save line 52: ignoring bad line starting with 'f'
.
zachary@laptop:~$ 

```


so, umm... tat can't be terribly normal. I purged and reloaded alsa-base and pulse audio, but I can't force a reload without getting this madness. There is no software modem for me to disable, I've updated grub, I'm not really sure what a "dummy output" looks like to know if I have one.
(in referencce to this tread: [http://ubuntuforums.org/showthread.php?t=1316634](http://ubuntuforums.org/showthread.php?t=1316634))

Whenever I enter in
```
sudo gedit /etc/modprobe.d/alsa-base-conf
```
I get back a blank gnome text document.  I'm starting to become overwhelmed wit the sheer volume of fixes that are not working... I almost feel like I should keep a checklist of links I have tried to post in here.

alsa-base-conf is a completely empty file when I open it in gedit, and alsa-base.conf.save looks suspicious to me. it reads like:

```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-




sdfsdf



sdf
sdf
sd
f
```

does the end of that file always look that gnarly or did gibberishh somehow get typed into it?

---

### Post by darkyre on 2009-12-16
Could this possibly have anything to do with my issues?

```
zachary@laptop:~$ apt-get install alsa-base alsa-utils
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
zachary@laptop:~$ sudo apt-get install alsa-base alsa-utils
[sudo] password for zachary: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
```

---

### Post by darkyre on 2009-12-17
I recompiled alsa's files with a script:
[http://aldeby.org/blog/wp-content/uploads/2009/04/alsa_setup](http://aldeby.org/blog/wp-content/uploads/2009/04/alsa_setup)
I set the settings to 3stack at the end, which has half-way fixed my sound.

Sound now exists through the headphone jack, and is really low on the pc speakers, but I will work on that. Almost solved!

*edit*

It seems that all of my problems are, in fact, solved, except one little one. I had forgotten that I turned my alsamixer sound low when working on finding a fix, haha.
The final left over relic of this entire sound problem is an issue with my volume controls.
My volume settings in the system tray don't seem to have any effect on my volume. I'm currently using gnome alsa mixer to change volume, but that's a hassle. Does anyone know what might be the problem?

---

