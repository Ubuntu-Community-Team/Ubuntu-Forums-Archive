---
title: "Hardy 8.04: No sound for Intel Q35 ALC883 audio"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by lptr on 2008-05-02
[Solved] I played around with mixer settings again. Well - that's it. Sound working, now.


Successfully installed 8.04 Kubuntu on a 4 GByte USB stick as a full installation. Not a Live-CD transfer! ([see here: http://ubuntuforums.org/showthread.php?p=4831104#post4831104#27]("http://http://ubuntuforums.org/showthread.php?p=4831104#post4831104#27"))

When I started on the desktop system I definitively heard a sound. This has been gone since I rebooted first time. asound mixer settings all ok.

dmesg tells me:
```
hda_codec: Unknown model for ALC883, trying auto-probe from BIOS...
```nothing else.

Found this in the hardware manual for mainboard:
Realtek ALC883 8-channel High Definition Audio CODEC with Jack-detection support, Enumeration and streaming

Some further search lead me to this:
```
$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfe970000 irq 23

# cat /proc/asound/modules
 0 snd_hda_intel

```So it seems that something did find and initialize it at least once. 

Anywhere online I found that Jack-detection having some issues.

Anyone knowing something regarding? Is there a known workaround so sound works?

Thanks in advance

rob*

---

### Post by kraymore on 2008-05-07
I have a GA-965P-DS3 with the same chipset audio and using Ubuntu (Gnome) Hardy without sound.  I found a thread that suggested a fix as seen here [http://ubuntuforums.org/showthread.php?t=687726](http://ubuntuforums.org/showthread.php?t=687726) by getting module assistant to rebuild alsa then issuing a 

sudo /etc/init.d/alsa-utils reset

i get the following:

 * Resetting ALSA...                                                            amixer: Invalid command!
                                                                      [ OK ]

something of note, when i logged into GDM this boot, i heard a sound, going into the desktop though i hear no starup sounds and unable to play soundfiles.   

would appreciate any help anyone can give.

edited.  tried sudo /etc/init.d/alsa-utils start instead of 'reset' and get the following error:

@sputnik:~$ sudo /etc/init.d/alsa-utils start
 * Setting up ALSA...                                                            * warning: 'alsactl restore' failed with error message 'alsactl: set_control:989: warning: name mismatch (IEC958 Capture Switch/IEC958 Default PCM Playback Switch) for control #35
alsactl: set_control:991: warning: index mismatch (0/0) for control #35
alsactl: set_control:993: failed to obtain info for control #35 (Operation not permitted)'...                                                                   amixer: Invalid command!
                                                                         [ OK ]

please help.  thank you

---

### Post by bruceb85 on 2008-05-07
I had somewhat the same issue. I unistalled anything pulse audio in synaptic. Now it all works.

---

