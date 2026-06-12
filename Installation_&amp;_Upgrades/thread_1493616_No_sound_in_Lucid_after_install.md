---
title: "No sound in Lucid after install"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by svesmeralda on 2010-05-26
I upgraded to Lucid from Jaunty on a 3 1/2 year old toshiba Satellite by doing a clean install.  There is no sound anywhere.  I had no sound problems with Jaunty.

I ran the alsa upgrade script from this site:

[http://ubuntuforums.org/showthread.php?p=6589810#post6589810](http://ubuntuforums.org/showthread.php?p=6589810#post6589810)

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
~$

There was no change I could see after this was done.

In sound preferences>
    hardware--there are no entries;
    input--the input volume is shaded
    output--the entry is Dummy Output stereo

The alsamixer shows only the pcm control, there are no capture controls.  In select sound card (F6) I selected HDA ATI SB (default was only other choice).

I have Linux Mint 9 (based on Lucid) on a Dell mini-9 and the sound works.

Is there anything else I could try?

Jim

Fair winds and calm seas.

---

### Post by alterpinguin on 2010-05-26
if
alsa -l
gives no sound-devices
-
check with
lspci
for any sound hardware. Normally (for most hardware) there should be an entry about "Audio device"
if there is none ... find the hardware manufacturer specs and try to search about linux-modules used for this
if there is a hardware entry
check with
lsmod
what modules are loaded. Are any snd-modules loaded?

---

### Post by dino99 on 2010-05-26
install paprefs and gnome-alsamixer (set your prefs with it)


[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

---

### Post by svesmeralda on 2010-05-26
AlterPenquin

Thanks for the reply, here are the results.

The sound icon shows that it is muted and the muteall seclection is not enabled (shadowed).

gnome alsa mixer
    program preferences
        soundcard Names and visibility
            LSI ID 1040
        slider style
            single slider with pan
        slider toggle style
            Checkbox

    sound card properties
        sound card element names and visibility
            PCM checked (there are no others)

    The gnome alsa mixer window shows a horizontal slider across the bottome set to the mid-point and a second vertical one in the middle above the horizontal one with the slider fully up and the bar grayed.  Sliding the slider down causes the bar to become orange.  Had no effect on the lack of sound.

pulseaudio preferences
    none of the boxes in any of the tabs were checked.  

:~$ alsa -l
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
:~&

:~$ lspci 
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
(Other devices are listed)

:~$ lsmod
Module                  Size  Used by
snd_hda_intel          23593  0 
snd_hda_codec          91922  1 snd_hda_intel
snd_hwdep               5668  1 snd_hda_codec
snd_pcm_oss            41611  0 
snd_mixer_oss          13461  1 snd_pcm_oss
snd_pcm                78086  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1498  0 
snd_seq_oss            30866  0 
snd_seq_midi            5101  0 
snd_rawmidi            19879  1 snd_seq_midi
snd_seq_midi_event      5939  2 snd_seq_oss,snd_seq_midi
snd_seq                51494  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19106  2 snd_pcm,snd_seq
snd_seq_device          5990  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62362  14 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7140  2 snd_hda_intel,snd_pcm
snd_seq_device          5990  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62362  14 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7140  2 snd_hda_intel,snd_pcm
:~$

I hope this helps.  I have been using Ubuntu for three years and this is the first sound problem I have had since Fiesty Fawn.  It had no sound originally but apparently an update fixed it because one day it had sound.  Think, maybe, that is what I should do, just wait to see if a fix is coming?  Fixing these kind of problems is way over my head right now.

See my next post for what I did from Dino99's suggestions.

Jim

Fair winds and calm seas.

---

### Post by WinRiddance on 2010-05-26
I had an almost identical problem which was fixed with the gnome alsa mixer ... not in the conventional way though. The post that I'd read at that time claimed that the alsa-mixer GUI would absolutely positively be able to correct this issue, also on an older laptop computer.

So, being completely new to Ubuntu at that time and believing what I read, I ended up installing the alsa mixer. Then I opened it up to show all of the available checkmarks/settings that could be enabled and disabled. **Started playing a song from a CD** and just messed around with all of the different mute/enable/disable selections until all of a sudden ... I had sound ... awesome** !!!** It only took a few minutes but I'm sure the key was that I had a playing sound file going since I would not have been able to hear the improvement otherwise. Just a thought ...

---

### Post by svesmeralda on 2010-05-26
dino99,

I went to:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

This is a summary of what I did.

jim@jim-laptop-ubuntu:~$ sudo aptitude install linux-ubuntu-modules-`jim-laptop-ubuntu -r` linux-generic
jim-laptop-ubuntu: command not found
[sudo] password for jim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package matching "linux-ubuntu-modules".  However, the following
packages contain "linux-ubuntu-modules" in their description:
  lirc-modules-source 
Couldn't find any package matching "linux-ubuntu-modules".  However, the following
packages contain "linux-ubuntu-modules" in their description:
  lirc-modules-source 
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
jim@jim-laptop-ubuntu:
Still no sound

I ran this next:
:~$ find /lib/modules/`jim -r` | grep snd
There was a very long list returned

I tried the next step.  I could only edit etc/group from the root terminal.  Still no change.

:~$ aplay /usr/share/sounds/alsa/Front_Center.wav
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
aplay: main:654: audio open error: No such file or directory

:~$ fgrep -ie 'audio' /etc/group
audio:x:29:pulse,jim
:~$ fgrep -ie 'sound' /etc/group
:~$

:~$ alsa -l
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
:~&

:~$ lspci 
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
(Other devices are listed)

I rebooted, still no sound, however the speaker icon shows it is unmuted and the muteall slection is enabled.

Next I ran:
:~$ lspci -v | less
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
        Subsystem: Toshiba America Info Systems Device ff10
        Flags: bus master, slow devsel, latency 64, IRQ 25
        Memory at c0500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

Is this a bug?  Should I report it?  If so can you direct me to something that will explain how to report bugs?  I am beginning to think that my computer likes Jaunty so much that it justs throws a fit if I try to use something else on it.

Thanks for you suggestion.

Jim

Fair winds and calm seas.

---

### Post by svesmeralda on 2010-05-26
Winriddance,

I would try that but I have nothing to try.  The only mute I have is in the sound icon and it did not seem to make any difference.

Interesting note, I ran the usb stick I used for the installation as a live CD and the sound worked.  In preferences it showed the hardware as Internal Audio--Analog Stereo Duplex and both the input and output tabs showed Internal Audio Analog Stereo.

I would like to try an earlier kernel and the disk check but that does not seem to be available.  I pressed esc after the BIOS was done and after Ubuntu justed started booting.  Nothing.

I am going to leave alone at least until tomorrow.

Jim

Fair winds and calm seas.

---

### Post by svesmeralda on 2010-05-26
I have solved the problem.  I burned a new live-CD to a disk and reinstalled Lucid.  The sound is okay now.  There may have been a glitch in the usb version I had used initially.  I probably should have reinstalled from the usb to see what effect that would have had.  I might try it tomorrow before I do my customization. 

Thanks to everyone who responded.  I hope this information will be of use to someone.

Jim
aboard Esmeralda
Mazatlan, Sinaloa, Mexico

Fair winds and calm seas.

---

### Post by alterpinguin on 2010-05-27
about install from usb-version failed to detect sound,
try the live-system from this usb-stick
and check if the sound dont works there too.
When the boot-menu from the usb-stick appears onscreen,
press a key (up-key/down-key) to open the menu to
select the live-system.

---

### Post by svesmeralda on 2010-05-28
Alterpenquin,

I did run the live session from the usb and there was sound.  Thus, I figured that there was a glitch in the install.  I burned a cd from the same iso file and installed it.  Everything works now and two other problems also disappeared.  Frequently the panels would not load.  I could still use the keyboard shortcuts and the terminal.  The panels would load on a restart.  Also sometimes the wifi would just cut out.  They are not happening now.  Skype is also working better than it ever has since I with Ubuntu.

I was going to try the usb stick one more time, but, for some reason, the computer would not boot from it again so I am leaving well enough alone.  I may try it again when and if I reinstall with a dual boot with windows.  My mates Nokia CS 10 modem does not work on Linux so I need to have windows if I want to do my emails when we are at anchor.  Then again, if it does not run on Linux, do I really need it?

Is there some way to mark this thread as solved?  I am still learning my way around the forums.  For the last 18 months I have had so few problems and I was able to solve them without posting that I have been kind of lazy about keeping up with the forums.

Thanks again and, in the future, if I ever have a serious problem with an install I will just try it over again first.

Jim

Fair winds and calm seas.

:popcorn:

---

