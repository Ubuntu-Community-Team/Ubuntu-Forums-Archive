---
title: "Upgrade killed Edgy sound"
date: 2006-10-12
forum: Installation &amp; Upgrades
---

### Post by jimbob on 2006-10-12
Upgraded Edgy this morning and now I have no sound at all.

Anyone else having this problem?

nvidia CK8S [IEC958]

Realtek ALC850 Rev 0
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by wpshooter on 2006-10-12
No, mine is even worse, I updated and now no desktop.  Thus, for now ends my great Edgy experiment !!!

---

### Post by viciouslime on 2006-10-12
I had this problem, turned out is was because i had install beryl and it uses a -386 kernel instead of the -generic one...

---

### Post by jimbob on 2006-10-12
Well, turns out if I bring up alsamixer in a terminal and un-mute everything they have muted my sound works.

Go figure.  OK, so it still is beta so I won't complain.

---

### Post by viciouslime on 2006-10-12
Hmmm I wonder if that would've worked for me...guess i'll never know

---

### Post by randell6564 on 2006-10-12
> **wpshooter said:**
> No, mine is even worse, I updated and now no desktop.  Thus, for now ends my great Edgy experiment !!!
The same exact happened to me!  I have 6.06 Dapper Drake installed and working flawlessly on hd1, and Edgy installed flawlessly onto hdb1 (dual-boot), but after updating edgy and restarting a few times, I only get the command-line screen with edgy instead of my desktop! Somewhere during the updates, I lost my X!

---

### Post by FerGeCo on 2006-10-18
> **viciouslime said:**
> Hmmm I wonder if that would've worked for me...guess i'll never know

And now you know!

after i installed beryl sound was also gone ..
but the alsamixer tip from jimbob helpt! got sound again! wh00t!

---

### Post by el_itur on 2006-11-02
I still have no sound. even with the jimbob tip.
this is what I get when I test ALSA in sound preferences
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: No se pudo abrir el recurso para escritura.
```

---

### Post by jfilip on 2006-11-02
I have this exact problem also using the intel8x0 driver on my laptop. All the proper sound modules are loaded and if I plug headphones into my system I can just hear a tiny hint of sound being played with all the ALSA volume sliders at full.

> **el_itur said:**
> I still have no sound. even with the jimbob tip.
this is what I get when I test ALSA in sound preferences
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: No se pudo abrir el recurso para escritura.
```

---

### Post by randell6564 on 2006-11-02
Some Advice; 
If Dapper ain't broke, dont try and fix it with an upgrade!  I'm still not seeing much difference between Dapper and Edgy so why upgrade?

---

### Post by jfilip on 2006-11-03
Thanks for the unsolicited "advice" but Dapper wasn't exactly in a state of "ain't broke" before the upgrade.  I couldn't use the supplied kernels and get my wireless card working so I had to compile custom kernels (not a big deal but that's 'broken').  Suspend and hibernate wouldn't work no matter what kernel I was running (packaged or compiled myself from source).  Given that I'm using Ubuntu on my laptop this was a big deal for me.

Both of those problems are fixed in Edgy.  Not to mention the new versions of supported software that I use on a daily basis.  So in all reality losing sound isn't a big problem compared to the things that have been fixed for me in Edgy.  The only thing that no sound really hurts me with is not getting notifications when IM's or e-mail arrives.

Still looking for a solution to the sound problem...

---

### Post by jfilip on 2006-11-03
...and I just found that solution.

Moving along.

**EDGY IS GREAT!**

---

### Post by dannyboy79 on 2006-11-03
> **jfilip said:**
> ...and I just found that solution.

Moving along.

**EDGY IS GREAT!**

Please resist from doing this! This kind of post won't help anyone if they have the same problem! Please post how you solved in detail for anyone else. We all need to work together to get these issues solved. Thank you

---

### Post by jfilip on 2006-11-03
> **dannyboy79 said:**
> Please resist from doing this! This kind of post won't help anyone if they have the same problem! Please post how you solved in detail for anyone else. We all need to work together to get these issues solved. Thank you

You're right.  My apologies.

As I initially said I tried the alsamixer tip just like el_itur and it didn't work for me.  I still had no sound and got the same error when trying to use the sound control panel's test buttons.  I just fiddled around with alsamixer again after looking around the bug tracker for some information about this issue specific to my sound card (intel 8x0).  I saw a bug entry that mentioned unmuting the 'external amplifier' option.

I **thought** I had tried unmuting everything and setting all volume sliders to max but apparently I missed that last one.

So, for me, with my sound card, **unmuting the external amplifier** fixed the sound issue for me.

---

### Post by el_itur on 2006-11-03
Well jfilip. It isn't the external amplifier here. Nvidia Nforce2 with alsa just dont work, Now playing all my sound with OSS :( . At least OSS works

---

### Post by crazedgremlin on 2006-11-04
ME TOO!  I had tried beryl and couldn't get it to work.  I uninstalled it but then I didn't have sound!
I was going to do a complete reinstall.  Now I don't have to go through all of that.  Thanks, jimbob!!  I love edgy now.
Yay :)

---

### Post by JoeMcC00L on 2006-11-04
Unfortunately, I'm still in the same no sound boat. snd_intel8x0 driver is loaded properly, and there are no error messages at all when I try to play stuff (even strace mpg123 test.mp3 looks okay). OSS doesn't work either. I did install beryl, but there's still no sound when I boot up to the login screen, before beryl is even loaded. Everything is unmuted from alsamixer and the permissions for /dev/dsp are correct. This is driving me nuts!!! ](*,)  (btw, ubuntu still rocks).

---

### Post by Sef on 2006-11-04
Here's from another post.

> This is how I got sound:

Quote:
Here's how I got sound on my via82xx:

I commented out 3 lines and changed the 2 to 0 in the 82viaxx line. To comment out a line, put a # before it. I commented out one line above 'options snd-via82xx-modem index=-0' and the two lines below.

Code:

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway) install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; } # Prevent abnormal drivers from grabbing index 0 options snd-bt87x index=-2 options snd-atiixp-modem index=-2 
#options snd-intel8x0m index=-2 
options snd-via82xx-modem index=-0 
#options snd-usb-audio index=-2
 #options snd-usb-usx2y index=-2

Save and exit.

Then System > Preferences > Sound and changed the bottom one to

Then changed sound capture to Via 82C686A/B 50rev.

If you don't have any sound after that, reboot and you should have sound.

---

### Post by JoeMcC00L on 2006-11-04
I tried that, substituting the mentioned via line with the intel line, but there is no change. Another thing to note, my session loaded without XGL does not make the sound work, so I don't think it has anything to do with beryl/xgl. Any other ideas?

---

### Post by JoeMcC00L on 2006-11-04
Wow this is embarassing... Apparently I overlooked "PCM" in alsamixer. It was muted, so I unmuted it. It works. Thanks for the help, sorry for the airheaded-ness :-p.

---

### Post by jimbob on 2006-11-05
It's easy to overlook some settings in alsamixer; if you open it in a small terminal window you may not realize that there are several more settings to the right off the screen.  The window does not give you much indication that there is more stuff out there that is cut off.

---

### Post by turbojugend_gr on 2006-11-05
Same for me, oh and ViciousLime for sure it ain't the beryl stuff... People do tend to get nervous with every update, that should be a annoying issue to the DEVS i think...:-k

---

### Post by Othersider on 2006-11-05
I, too, lost sound upgrading Dapper to Edgy - I went through alsamixer and nothing was amiss.  Sound worked great before.

If this is of any interest:
```

ian@localhost:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 0: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 1: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 2: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CA0106 [CA0106], device 3: ca0106 [CA0106]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Also, in System > Preferences > Sound Preferences, when I try to test sound with Autodetect or OSS, nothing happens (no sound during the test).  If I specify Analog, ALSA, I get the following error:
```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

```

And if I try ESD:
```

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not establish connection to sound server

```

Help would be much appreciated :).  Thanks!

---

### Post by aum11 on 2006-11-06
Please excuse my ignorance here but how do You change the alsamixer settings?  Have displayed them on the terminal and it looks as though PCM and external at 0 may be the answer....but how do You change anything?

Thanks

---

### Post by jimbob on 2006-11-06
The left and right arrows on your keyboard select which item you want to adjust and the up and down arrows change the volume.

The m key turns the mute on and off.

If you really want to get into it type $man alsamixer in the terminal.

---

### Post by el_itur on 2006-11-06
> **Sef said:**
> Here's from another post.Here's from another post.

Quote:
This is how I got sound:

Quote:
Here's how I got sound on my via82xx:

I commented out 3 lines and changed the 2 to 0 in the 82viaxx line. To comment out a line, put a # before it. I commented out one line above 'options snd-via82xx-modem index=-0' and the two lines below.

Code:

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway) install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; } # Prevent abnormal drivers from grabbing index 0 options snd-bt87x index=-2 options snd-atiixp-modem index=-2
#options snd-intel8x0m index=-2
options snd-via82xx-modem index=-0
#options snd-usb-audio index=-2
#options snd-usb-usx2y index=-2

Save and exit.

Then System > Preferences > Sound and changed the bottom one to

Then changed sound capture to Via 82C686A/B 50rev.

If you don't have any sound after that, reboot and you should have sound.

Sorry, I don't get it. Wich file do I have to modify to apply this changes? and where do I get the identifier of my sound card (In my case it's an Nforce 2, but don't know the identifier exactly)?

---

### Post by Othersider on 2006-11-07
Any help?  Seems like a lot of people are having sound problems.

---

### Post by el_itur on 2006-11-08
this soved my problem [http://www.ubuntuforums.org/showthread.php?t=286016&highlight=no+sound+edgy](http://www.ubuntuforums.org/showthread.php?t=286016&highlight=no+sound+edgy)

this command 
asoundconf reset-default-card

---

