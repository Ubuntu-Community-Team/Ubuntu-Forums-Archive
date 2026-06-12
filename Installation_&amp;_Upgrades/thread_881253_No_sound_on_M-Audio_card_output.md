---
title: "No sound on M-Audio card output"
date: 2008-08-05
forum: Installation &amp; Upgrades
---

### Post by jerrywo on 2008-08-05
This is my 3rd attempt at articulating my problem (I'm desperate!)

Sound comes out my M-Audio jack when I'm using "Rhythmbox".

All other sounds, flashplayer, Ubuntu startup theme, etc., come out the motherboard jack.  Here's a snapshot from /etc/modprobe.d/alsa-base:
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388

Does this give any hints?  I would much prefer one output - the M-Audio card!

I've tried all possible configurations on the Preferences Sound GUI.
Thanks
jerry

---

### Post by spiderbatdad on 2008-08-05
what output do you get from ```
asoundconf list
```

---

### Post by jerrywo on 2008-08-06
Here's what I get:

Revolution51
NVidia

---

### Post by spiderbatdad on 2008-08-06
You might try```
asoundconf set-default-card Revolution51
```doesn't look to promising though, I expected to see some numbers, as parameters. You could read through ```
man asoundconf
```for some clues.
The gui too is very good. I'm using the Intrepid Ibex alpha release and it works better than ever, for me

---

### Post by jerrywo on 2008-08-06
well the man page for asoundconf was not too illuminating.  I tried that command (set default), which took, but I see no difference in my symptoms (sound coming out of mobo in some instances & sound coming out M-audio jack in Rhythmbox).

I think I've tried every possible command in the preferences/sound GUI.  I don't know what GUI you're speaking of....What is Intrepid Ibex?

"Linux Format" magazine has a recent article on ALSA tips and they  talk about changing the sound card order in the /etc/modprobe.d/alsa-base file.

It's over my head but this may be where my problem lies.  

Any other hints?
Jerry
p.s.
my wife and I just spent the weekend in the Springfield, VT area.  Nice place!

---

### Post by spiderbatdad on 2008-08-06
after setting the default sound card did you restart?

Intrepid is the upcoming release of Ubutnu 8.10 due in October. It is available in alpha release now. Alpha3 i believe. The downside of alpha is generally the possibility of breakage due to instability and upgrades. But I must say I've been through 100's of updates without one hitch in this release.  I think it's the best I've seen. I've been using Ubuntu since 5.10.
Anyway, if you're game: [http://cdimage.ubuntu.com/releases/intrepid/alpha-3/](http://cdimage.ubuntu.com/releases/intrepid/alpha-3/)

---

### Post by jerrywo on 2008-08-07
Hmmm
If I swap distro's, I'd be inclined to go back to Fedora which recognized my sound card in the installation and it was smooth sailing from there on.  I actually moved off Fedora because of the frequent update cycle - that's why I moved to the LTS support version of Ubuntu!

I've diddled with the sound GUI and I now (at least) have all the sound coming out of the mobo jack.  I set all the settings to OSS.  In doing so, i've lost the output from my M-Audio card.

Thanks for your help Spiderbatdad

I'm gonna ponder this for a while
jerry

---

### Post by spiderbatdad on 2008-08-07
Regards, sound issues are very frustrating. I find the LTS's loose their luster long before the support runs out. I like staying current. I can't say enough good about Intrepid so far. And my sound works, whereas with Hardy I had to stay with the alpha kernel: 2.6.22-14
In interpid I'm on 2.6.26-3server

One way of dealing with release cycles is to manually create a separate partition for your /home. That way you always have all your personal stuff in spite of distribution upgrades.

---

### Post by jerrywo on 2008-08-07
I actually have a separate partition for /home.  I did it when i moved off Fedora.  I've got /boot, / (root), swap, and /home.  Tell me, when you do a clean install, can you do it so it doesn't touch your /home?  I guess I've never paid that much attention.  
Jerry

---

### Post by spiderbatdad on 2008-08-07
> **jerrywo said:**
> I actually have a separate partition for /home.  I did it when i moved off Fedora.  I've got /boot, / (root), swap, and /home.  Tell me, when you do a clean install, can you do it so it doesn't touch your /home?  I guess I've never paid that much attention.  
Jerry

Indeed as long as you don't "use the entire disk" and wipe out your /home in the process:)

---

### Post by jerrywo on 2008-08-07
aren't there some "config" files (hidden) that get written to your home folder?  Do they then just get over-written?

---

### Post by spiderbatdad on 2008-08-07
config files in user space would be fine, as they pertain to packages that are upgraded in the root file system. It is possible...occasionally that a package gets updated and handles symbols in config files differently...This is not specific to /home however: The wvidal (for dial-up) was updated once but the routine that wrote the config file continued to prepend lines with ";" whereas the newer program saw these semi-colons as comments, causing no end of frustration for some dial-up users.
So, no, no significant or insurmountable problems should arise regarding user config files.

---

