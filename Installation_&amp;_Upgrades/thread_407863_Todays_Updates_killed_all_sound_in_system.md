---
title: "Todays Updates killed all sound in system"
date: 2007-04-12
forum: Installation &amp; Upgrades
---

### Post by bourger on 2007-04-12
Well, those famous "todays updates"...
I let them be performed, and after reboot got no sound at all. The Volume Control icon is displayed with red cross. When I click it it says: ```
The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.
```
If I click Applications > Sound&Video > Volume Control, I get this: ```
No volume control GStreamer plugins and/or devices found.
```

```
alsaconf
``` does everything as it should, but ```
alsamixer
``` outputs this: ```
alsamixer: function snd_ctl_open failed for default: No such device
```.
What to do?

---

### Post by zvacet on 2007-04-12
I don´t want to be ironic but tomorow updates will probably fix it.I´m speaking from expirience,because similar thing gives me trouble and next day all fixed with new updates.I hope it is your case too.

---

### Post by bourger on 2007-04-13
**zvacet**
Well, I would be happy if you were right but... day pased, no upgrades available, no sound in system...

---

### Post by Skidpad on 2007-04-13
I don't know how appropriate or relevant my post will be to your situation, but I lost my sound with this last round of updates as well.  I didn't get the same errors as you are, but I used [***this***]("http://ubuntuforums.org/showthread.php?t=205449") thread to fix mine.

Be especially wary of this statement by the thread starter in his first post:
[b]"VERY IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following:

Code:
sudo apt-get install gdm ubuntu-desktop"
[/b]

Still being an X n00b myself, I wasn't fully aware of what that statement meant.  I saw the desktop package being removed in the terminal, but I wasn't prepared for the results.  Just a "terminal" looking "desktop" at next boot.  Luckily a quick command restored graphical law & order to my little world.

HTH

---

### Post by Shinoda on 2007-04-14
Less confusingly, try reinstalling ALSA:```
sudo aptitude purge linux-sound-base alsa-base alsa-utils
sudo aptitude install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
```(replace [FONT=Courier New]ubuntu-desktop[/FONT] with [FONT=Courier New]xubuntu-desktop[/FONT] if you're running Xubuntu) and reboot.

Alternatively follow e.g. [these]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide#ALSA_driver_Compilation") instructions to compile it yourself.

---

### Post by Skidpad on 2007-04-14
^^^^  Thanks for the tip Shinoda!  I wish I had done it that way.  :)

---

### Post by Shinoda on 2007-04-14
No prob. Just prefer [FONT=Courier New]aptitude[/FONT] to [FONT=Courier New]apt-get[/FONT] as it's got a better dependency resolution system. More info:```
aptitude -h
man aptitude
```

---

### Post by Jun-Dai on 2007-04-15
I'm running Edgy and I'm having the same problem.  An update I did last week killed my sound after I rebooted today.  So far none of the suggestions I've found here have resolved the problem (oddly enough, it seems that HDA-Intel sound broke in Feisty at the same time?).  I saw the defect for Feisty, but since I'm not running off of 2.6.20, I didn't feel it was appropriate to add a "me too".  Is there a defect for this for Edgy?

Reinstalling linux-sound-base, alsa-base, and alsa-utils as recommended above did nothing.  In any case, my symptoms are identical to the original poster.  Also, running this:
```

sudo modprobe snd-hda-intel 

```
errored out with:
```

WARNING: Error inserting snd_timer (/lib/modules/2.6.17-11-generic/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error inserting snd_timer (/lib/modules/2.6.17-11-generic/kernel/sound/core/snd-timer.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_pcm (/lib/modules/2.6.17-11-generic/kernel/sound/acore/snd-pcm.ko): Unknown symbol in module, or unknown parameter (see dmesg)
WARNING: Error running install command for snd_pcm
WARNING: Error inserting snd_hda_codec (/lib/modules/2.6.17-11-generic/kernel/sound/pci/hda/snd-hda-codec.ko): Unknown symbol in module, or unknown parameter (see dmesg)
FATAL: Error inserting snd_hda_intel (/lib/modules/2.6.17-11-generic/kernel/sound/pci/hda/snd-hda-intel.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

dmesg produces a whole bunch of stuff that looks like this:
```

[17182141.064000] snd_hda_codec: disagrees about version of symbol snd_ctl_add
[17182141.064000] snd_hda_codec: Unknown symbol snd_ctl_add
[17182141.064000] snd_hda_codec: disagrees about version of symbol snd_card_proc_new
[17182141.064000] snd_hda_codec: Unknown symbol snd_card_proc_new
[17182141.064000] snd_hda_codec: disagrees about version of symbol snd_ctl_find_id
[17182141.064000] snd_hda_codec: Unknown symbol snd_ctl_find_id
[17182141.064000] snd_hda_codec: disagrees about version of symbol snd_ctl_new1
[17182141.064000] snd_hda_codec: Unknown symbol snd_ctl_new1
[17182141.064000] snd_hda_codec: disagrees about version of symbol snd_component_add
[17182141.064000] snd_hda_codec: Unknown symbol snd_component_add
[17182141.064000] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_read
[17182141.064000] snd_hda_codec: Unknown symbol snd_ctl_elem_read
[17182141.064000] snd_hda_codec: disagrees about version of symbol snd_ctl_elem_write
[17182141.064000] snd_hda_codec: Unknown symbol snd_ctl_elem_write
[17182141.064000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_list
[17182141.064000] snd_hda_codec: disagrees about version of symbol snd_device_new
[17182141.064000] snd_hda_codec: Unknown symbol snd_device_new
[17182141.068000] snd_hda_codec: Unknown symbol snd_pcm_hw_constraint_step
[17182141.068000] snd_hda_codec: Unknown symbol snd_pcm_format_width
[17182141.068000] snd_hda_intel: Unknown symbol snd_pcm_new
[17182141.068000] snd_hda_intel: Unknown symbol snd_pcm_limit_hw_rates
[17182141.068000] snd_hda_intel: disagrees about version of symbol snd_card_register
[17182141.068000] snd_hda_intel: Unknown symbol snd_card_register
[17182141.068000] snd_hda_intel: disagrees about version of symbol snd_card_free
[17182141.068000] snd_hda_intel: Unknown symbol snd_card_free
[17182141.068000] snd_hda_intel: Unknown symbol snd_pcm_lib_preallocate_pages_for_all
[17182141.068000] snd_hda_intel: Unknown symbol snd_hda_bus_new
[17182141.068000] snd_hda_intel: Unknown symbol snd_hda_build_pcms
[17182141.068000] snd_hda_intel: Unknown symbol snd_hda_codec_new
[17182141.068000] snd_hda_intel: Unknown symbol snd_hda_queue_unsol_event
[17182141.068000] snd_hda_intel: disagrees about version of symbol snd_card_new
[17182141.068000] snd_hda_intel: Unknown symbol snd_card_new
[17182141.068000] snd_hda_intel: Unknown symbol snd_pcm_lib_malloc_pages
[17182141.068000] snd_hda_intel: Unknown symbol snd_pcm_lib_ioctl
[17182141.068000] snd_hda_intel: Unknown symbol snd_pcm_lib_free_pages
[17182141.068000] snd_hda_intel: Unknown symbol snd_hda_calc_stream_format
[17182141.068000] snd_hda_intel: Unknown symbol snd_pcm_set_ops
[17182141.068000] snd_hda_intel: Unknown symbol snd_hda_suspend
[17182141.068000] snd_hda_intel: disagrees about version of symbol snd_device_new
[17182141.068000] snd_hda_intel: Unknown symbol snd_device_new
[17182141.068000] snd_hda_intel: Unknown symbol snd_pcm_suspend_all
[17182141.068000] snd_hda_intel: Unknown symbol snd_hda_resume
[17182141.068000] snd_hda_intel: Unknown symbol snd_pcm_hw_constraint_integer
[17182141.068000] snd_hda_intel: Unknown symbol snd_hda_build_controls
[17182141.068000] snd_hda_intel: Unknown symbol snd_pcm_period_elapsed

```

I will keep searching the Internet for more help.

---

### Post by Jun-Dai on 2007-04-15
I created a defect for this, in case anyone else wants to chime in on it (I didn't see any other bugs reported against this problem, at least not for Edgy).

[https://bugs.launchpad.net/ubuntu/+bug/106755](https://bugs.launchpad.net/ubuntu/+bug/106755)

Pardon me, bourger, for plagiarizing your initial post in the bug report :-)

Also, some people have reported the same problem in Edgy in a thread related to a similar problem that surfaced last week in Feisty: [http://ubuntuforums.org/showthread.php?t=402351&highlight=update+sound](http://ubuntuforums.org/showthread.php?t=402351&highlight=update+sound)

---

### Post by Shinoda on 2007-04-15
> **Jun-Dai said:**
> Reinstalling linux-sound-base, alsa-base, and alsa-utils as recommended above did nothing.What about compiling latest ALSA?

Additionally have you tried booting to an older kernel where sound was known working to see if it still is (if compiling ALSA yourself you'll likely need to recompile it under the different kernel)?

---

### Post by louieb on 2007-04-15
I've gotten use to it. FC5 was my first Linux distro. One of early updates killed my sound in it. I believe its related more to Gnome that any Linux distro, Ubuntu, FC5, or whatever. Haven't had a problem with sound in Dapper. Never installed Edgy. I did install Feisty beta last week and so far no problems.

---

### Post by Jun-Dai on 2007-04-15
Actually, I haven't, mostly because sound isn't that crucial (this is my workstation) and I'm short on time.  If, however, I don't see any simpler (less risky?) path to resolving this later in the week, I'll try that next and report my results.  I put up the defect because it seemed like others had the exact same problem from the same update.

---

### Post by Jun-Dai on 2007-04-16
Building 1.0.14 from source resolved the problem.  Looks like I had installed 1.0.13 from source before in an attempt to fix my non-functioning microphone port (I didn't remember having done that on this installation, but I guess I did).  I'll update the defect.

---

### Post by bourger on 2007-04-16
Well I reinstalled ALSA from the repositoires. 
No effect.
Then I uninstalled alsa 1.0.13 (which I previously built from source) -
nothing happened - 
and built it again.
No change.
I'm thinking of building and installing 1.0.14rc3 now, but remember what it had done last time I tried to do that: I had to build 1.0.13 from terminal because the desktop session didn't start.
By the way, I haven't told that: I run Dapper Drake, my soundcard is built-in VIA8235 on MS I6712 Mobo, and I reported that bug too - [https://bugs.launchpad.net/bugs/106669](https://bugs.launchpad.net/bugs/106669) :)

---

### Post by bourger on 2007-04-17
OK, I really don't know what happened and how that could happen, but today after booting into new kernel (.28 ) sound have begun to work great...
There weren't any updates and I didn't do any changes in settings...
Perplexed but happy :).

---

### Post by Shinoda on 2007-04-17
Glad to know. Anyways, .28?

---

### Post by bourger on 2007-04-17
Ya, 28 :).
I think now that last time in was booted in that new kernel, I rebuilt alsa but didn't restart to see the result. 
The point is - I actually can't yet figure out after which changes I should restart to get the results and after which there is no need in restarting...

---

### Post by Michal77 on 2007-04-19
[QUOTE=Shinoda;2450551]Less confusingly, try reinstalling ALSA:```
sudo aptitude purge linux-sound-base alsa-base alsa-utils
sudo aptitude install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
```(replace [FONT=Courier New]ubuntu-desktop[/FONT] with [FONT=Courier New]xubuntu-desktop[/FONT] if you're running Xubuntu) and reboot.

I use Feisty and got similar problem after yesterday update - microphone die, but reinstall have solved problem. 
:guitar: 
Thank for good hint!
M.

---

### Post by mrwednesday on 2007-04-19
Hi! Im completely new to Ubuntu and this forum and I need some help!

Ive been using Ubuntu for a month now and I was having problems with my Radeon 9600 card, I went to the ATI website, downloaded and installed their Linux driver... I solved my graphics problem but now I reboot I didnt get any sound... I get this message:

"The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu."

I tried to reinstall ALSA with the codes mentioned here but I got no sucess... Strange thing i that I still hear the african drums when Ubuntu asks for my user name and password... 

You guys got any clues? I looked around the forum and on the internet but cant seem to find anything..

---

### Post by Shinoda on 2007-04-19
Have you tried [this]("http://ubuntuforums.org/showthread.php?t=409116")?

---

### Post by mrwednesday on 2007-04-19
> **Shinoda said:**
> Have you tried [this]("http://ubuntuforums.org/showthread.php?t=409116")?

Shinoda... YOU SIR are an angel!! :) Thanks a lot! I was beginning to panic here... I needed to write some lyrics for a couple of songs to my band's rehearsal tonight but I couldnt do much without listening to the songs... :P Once again thanks a lot! This forum is really great! Im going to use it more often... And maybe in the future I might help others aswell... But first I gotta get a little more intimate with Ubuntu first... ;)

---

### Post by Shinoda on 2007-04-19
> **mrwednesday said:**
> Shinoda... YOU SIR are an angel!! :) Thanks a lot! I was beginning to panic here...Heh, anytime, mate, although jcraveiro is the one to praise here.> **mrwednesday said:**
> This forum is really great! Im going to use it more often... And maybe in the future I might help others aswell... But first I gotta get a little more intimate with Ubuntu first... ;)Giving back to the community whenever you can is great.

---

### Post by rrwo on 2007-04-20
[QUOTE=Shinoda;2450551]Less confusingly, try reinstalling ALSA:```
sudo aptitude purge linux-sound-base alsa-base alsa-utils
sudo aptitude install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop
```(replace [FONT=Courier New]ubuntu-desktop[/FONT] with [FONT=Courier New]xubuntu-desktop[/FONT] if you're running Xubuntu) and reboot.


That didn't fix the problem for me!

---

### Post by Shinoda on 2007-04-20
What about my 2 other suggestions (following [these instructions]("http://ubuntuforums.org/showthread.php?t=409116") and compiling ALSA from source), or even upgrading to Feisty?

---

### Post by WireMX on 2007-04-21
I having the same problems...

In system-sound I get this:


audiotestsrc wave=sine freq=512 !
audioconvert ! audioresample ! gconfaudiosink:
Could not open resource for writing.


Please helpme, I'm new in Linux, I was using Feisty Beta and everythings was working fine, but with the final release, i got muted!

---

### Post by Shinoda on 2007-04-21
If [this]("http://ubuntuforums.org/showpost.php?p=2487449&postcount=7") doesn't help, post back the output of```
cat /proc/asound/cards
cat /etc/modprobe.d/alsa-base
```

---

### Post by rrwo on 2007-04-21
> **Shinoda said:**
> What about my 2 other suggestions (following [these instructions]("http://ubuntuforums.org/showthread.php?t=409116") and compiling ALSA from source), or even upgrading to Feisty?

Um, I upgraded to Feisty. That's why I have the problem!

I tried the latest ALSA release candidates. Still no help.

I get no errors as far as I can tell, but checked alsamixer and it looks like all the channels are enabled and volumes are up.

---

### Post by rrwo on 2007-04-21
> **Shinoda said:**
> If [this]("http://ubuntuforums.org/showpost.php?p=2487449&postcount=7") doesn't help, post back the output of```
cat /proc/asound/cards
cat /etc/modprobe.d/alsa-base
```

cat /proc/asound/cards

```

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xa0000000 irq 20

```

cat /etc/modprobe.d/alsa-base

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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

options snd-hda-intel model=laptop


```

The last line was added in order to try to fix this.

---

### Post by Shinoda on 2007-04-21
I don't think there's anything wrong with those. What about```
aplay -l
cat ~/.asoundrc
cat ~/.asoundrc.asoundconf
cat /etc/asound.conf
```

---

### Post by karhulitos on 2007-04-21
I have the very same as WireMX:

cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xc0000000 irq 18

...clip..
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
options snd-hda-intel model=3stack

I have compiled the Alsa rc3. Tried basically all workarounds found on this forum. No sound. And after one suggestion I lost my speaker icon from systray and it never came back (guess it was the "kill blaa blaa" fix which stopped all and tried to reload stuff).

In Edgy there was very little sound problems. Perhaps I just need to wait.

---

### Post by karhulitos on 2007-04-21
```

aplay -l
**** Luettelo PLAYBACK laitteista ****

```
(above means no playback devices found)

```

cat ~/.asoundrc
cat: /home/nalle/.asoundrc: No such file or directory

```

```

cat ~/.asoundrc.asoundconf
cat: /home/nalle/.asoundrc.asoundconf: No such file or directory

```

```

cat /etc/asound.conf
cat: /etc/asound.conf: No such file or directory

```


Also, in Sound settings (as well as in the systray icon) I only have PCM and no other channels available. Alsamixer gives me same results.

---

### Post by never been to spain on 2007-04-21
Upgrade killed the sound.  I'm running an old X24.  Sound worked fine before...

> 
aplay: device_list:222: no soundcards found...


> cat /etc/modprobe.d/alsa-base
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388


---

### Post by Shinoda on 2007-04-21
Excuse me for not being very helpful, but everything I'm suggesting here is based on my past experience solving audio issues I had in Edgy with my on-board card, which is of the type usb-audio (i.e. not hda-intel or anything else), so I can't be very specific in my advice. Also my upgrade to Feisty went smoothly as far as audio is concerned, unlike yours unfortunately.

Most of you probably came across the [HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto") at some point during your search for a fix. The "Update to the latest version of alsa" section, which has instructions on how to compile ALSA for hda-intel, can be useful for other sound card types too, as long as you specify which one(s) should be used in [FONT=Courier New]--with-cards=hda-intel[/FONT] (e.g., for me this would read [FONT=Courier New]--with-cards=usb-audio[/FONT]) or omit the whole argument if in doubt (in which case all drivers are installed).  Additionally you may want to append [FONT=Courier New]--with-sequencer=yes[/FONT], as well as [FONT=Courier New]--with-oss=no[/FONT] and [FONT=Courier New]--with-isapnp=no[/FONT], unless you actually want or need OSS and have an ISA sound card respectively. Of course you'll have to replace the version numbers in the commands there ([FONT=Courier New]1.0.14rc1[/FONT] as of writing) according to the names of the files you'll get from the ALSA site. Anyway feel free to experiment with the arguments and compile as many times as needed (always rebooting afterwards), possibly until you get it right.

Before following the above though, I would remove ALSA from my system with```
sudo aptitude purge linux-sound-base alsa-base alsa-utils
sudo aptitude install gdm ubuntu-desktop
```and reboot (in any case you may always reinstall those 3 packages replacing [FONT=Courier New]purge[/FONT] with [FONT=Courier New]install[/FONT]).

Before getting too frustrated, if nothing seems to solve your problem you could download the Feisty LiveCD and check if the sound card works "out-of-the-box", i.e. in a clean install. If so then all hope is not lost, meaning at least your card **does** work under Feisty, and it'll be just a matter of finding out why it's not in your current install (I know that's what we're already trying to do, but still).

---

### Post by karhulitos on 2007-04-22
Thanks Shinoda for your patience and help.

I one more time did what you suggested, purge and then recompile the rc3 sources. No help. No sound, no systray icon (speaker) anymore.

Having terminal open I get these: ALSA lib pcm_dmix.c:864:(snd_pcm_dmix_open) unable to open slave every now and then

Trying to play the test sounds throw me: audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Ei voitu avata resurssia kirjoittamista varten.
(couldn't open resource for writing)

I also saw people filed bugs but I am not 100% sure this exactly same. Would you suggest I (we) should just wait and see if this gets fixed?

[edit] I'm now on Live CD (15.3.2007, so this is some Herd, can't remember which) and I have perfect sound. So the problem is either of following:
- something is wrong with the final Ubuntu 7.04 (I guess I could download and burn latest CD instead of the Herd X I'm using now)
- something went wrong in the upgrade as sound was OK on Edgy but not anymore

Any hints what I should be looking for?

---

### Post by Shinoda on 2007-04-22
As far as I understand, the problem appeared with Feisty's final release, so you should test that version's LiveCD.

Since we're in a sort of trial-and-error wave, do this in your current install:```
sudo mv -t ~/.Trash ~/.asoundrc ~/.asoundrc.asoundconf /etc/asound.conf
gksudo gedit /etc/modprobe.d/alsa-base
```In the file just opened, look for a line containing [FONT=Courier New]options snd-hda-intel[/FONT] (add it if it doesn't exist) and change it to```
options snd-hda-intel index=0
```or, if it previously had e.g. [FONT=Courier New]model=3stack[/FONT] in it,```
options snd-hda-intel index=0 model=3stack
```(in the same way you could compile ALSA with varying arguments, you may try different models (flavours) here, or even omitting the whole option). Make sure all other indexes there are set to [FONT=Courier New]-2[/FONT]. Save and reboot.

As for whether you should just wait, depends on how important having sound is for you, or how persistent you are. If similarly to my case that's a "very" for both, keep searching the net and experimenting at will (never forgetting your good sense). If anything you'll learn stuff and gain experience from all this.

---

### Post by chuvisco on 2007-04-22
> **Shinoda said:**
> As far as I understand, the problem appeared with Feisty's final release, so you should test that version's LiveCD.

Since we're in a sort of trial-and-error wave, do this in your current install:```
sudo mv -t ~/.Trash ~/.asoundrc ~/.asoundrc.asoundconf /etc/asound.conf
gksudo gedit /etc/modprobe.d/alsa-base
```In the file just opened, look for a line containing [FONT=Courier New]options snd-hda-intel[/FONT] (add it if it doesn't exist) and change it to```
options snd-hda-intel index=0
```or, if it previously had e.g. [FONT=Courier New]model=3stack[/FONT] in it,```
options snd-hda-intel index=0 model=3stack
```(in the same way you could compile ALSA with varying arguments, you may try different models (flavours) here, or even omitting the whole option). Make sure all other indexes there are set to [FONT=Courier New]-2[/FONT]. Save and reboot.


This solved my problem.  I'm not sure if it was the removal of the config files or the addition of "index=0".  My card is an NVIDIA nForce3.

---

### Post by chipper_30 on 2007-04-23
Thanks Shinoda,

I basically had the same problem, also with a NForce3 (I also have a TV card so maybe this created the problem?). Adding the line "options snd-hda-intel index=0" to /etc/modprobe.d/alsa-base and rebooting worked.

---

### Post by chuvisco on 2007-04-23
Yes, I also have a TV card.

---

### Post by rrwo on 2007-04-26
Last night, adding the line "options snd-hda-intel index=0" to /etc/modprobe.d/alsa-base and rebooting worked. I was happy.

Then I powered up my computer this morning and it's not working again. Reboots didn't help.
Even cold reboots.

---

### Post by Shinoda on 2007-04-26
What about removing the 3 config files I mentioned?

Don't just add that entire line if you already had [FONT=Courier New]options snd-hda-intel model=laptop[/FONT] there. Change the existing one to [FONT=Courier New]options snd-hda-intel index=0 model=laptop[/FONT] instead. Also try without [FONT=Courier New]model=laptop[/FONT] at all.

---

### Post by chipper_30 on 2007-04-27
I'm sorry to say that it's the same for me, it seems I sometimes have sound, sometimes not..., so I'm not even sure that "options snd-hda-intel index=0" even helped...
I tried "sudo mv -t ~/.Trash ~/.asoundrc ~/.asoundrc.asoundconf /etc/asound.conf" and I got "no such file or directory" for all 3.

---

### Post by Shinoda on 2007-04-27
Sorry to read so, but I've ran out of ideas. As I suggested earlier though, you can always check whether the whole thing works flawlessly in Feisty's final LiveCD.

---

### Post by TheAxeR on 2007-04-29
I dont know if anyone that is still having problems has tried this yet but after going through everything and trying everything that people were suggesting I went through alsamixer and turned everything that I could up and I found that my problem was wave was muted, I have a soundblaster live card.  

I sure kicked myself in the butt because I though I had checked that earlier.  But I thought I would post it because most people mention to check PCM but I never saw a suggestion to check the level for Wave.

my 2cents whatever that is worth.

---

### Post by chipper_30 on 2007-05-08
I am having some good persistent results with the following line
```
options snd-hda-intel model=3stack
```
I can't remember where I found it but it might have caught my eye because "integrated sound" was mentioned.

---

