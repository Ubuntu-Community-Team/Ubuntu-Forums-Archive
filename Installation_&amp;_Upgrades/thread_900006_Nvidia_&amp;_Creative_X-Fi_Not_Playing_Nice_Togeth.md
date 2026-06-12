---
title: "Nvidia &amp; Creative X-Fi Not Playing Nice Together"
date: 2008-08-24
forum: Installation &amp; Upgrades
---

### Post by ScarEye on 2008-08-24
Hey guys, 

I have a machine with a Nvidia card with a SB X-Fi card.  Now this is what I have done.  If I install a fresh copy of Ubuntu 8.04 and then following these steps [http://ubuntuforums.org/showpost.php?p=4823915&postcount=675](http://ubuntuforums.org/showpost.php?p=4823915&postcount=675)
I have sound working with no problem. But as soon as I install my Nvidia drivers either using envy-ng or manually running the Nvidia (NVIDIA-Linux-x86-173.14.12-pkg1.run) script it breaks my sound.

I then did another fresh install this time I installed the video driver first which worked perfectly and then installed the sound drivers using the instructions above and the sound doesn't work.

Any idea's on what could be the problem. 

user@p390:/etc$ lsmod |grep ctalsa
ctalsa                493270  1
snd_pcm                80004  2 ctalsa,snd_pcm_oss
snd                    55268  8 ctalsa,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               9056  4 ctalsa,ctsfman,emupia,snd
ctossrv               137776  7 ctalsa,haxfi,cthwiut,ctexfifx,ct20xut,ctsfman,emupia


It seems as if sound drivers are loading.  But I am stuck here. Any suggestions or help is appreciated.


Thanks
ScarEye

---

### Post by Idealist_ on 2008-09-07
I have the exact same problem as you, only with ubuntu as opposed to kubuntu. I installed the X-Fi using the alsa method, everything worked like a charm. However upon installing the nvidia graphics driver, the X-Fi can no longer be found? :confused:

Not sure why this is happening, but I can't find a workaround at all. This is what I get in the system log:

ctalsa: no version for "bytes_to_order" found: kernel tainted.

and the sound preferences says, "could not open audio device for playback". Hardware Drivers is also empty, where I don't believe it was before. :(

---

### Post by Shazaam on 2008-09-07
Creative problem (old), not Nvidia. The Creative cards try to share IRQ's with the video card slot.
Here are some links.....
[http://ubuntuforums.org/showthread.php?t=870001&highlight=Creative](http://ubuntuforums.org/showthread.php?t=870001&highlight=Creative)
[http://ubuntuforums.org/showthread.php?t=903451&highlight=Creative](http://ubuntuforums.org/showthread.php?t=903451&highlight=Creative)
[http://forums.creative.com/creativelabs/board?board.id=soundblaster](http://forums.creative.com/creativelabs/board?board.id=soundblaster)
[http://forums.creative.com/creativelabs/search?board_id=soundblaster&submitted=true&q=linux](http://forums.creative.com/creativelabs/search?board_id=soundblaster&submitted=true&q=linux)

---

### Post by Idealist_ on 2008-09-08
> **Shazaam said:**
> Creative problem (old), not Nvidia. The Creative cards try to share IRQ's with the video card slot.
Here are some links.....
[http://ubuntuforums.org/showthread.php?t=870001&highlight=Creative](http://ubuntuforums.org/showthread.php?t=870001&highlight=Creative)
[http://ubuntuforums.org/showthread.php?t=903451&highlight=Creative](http://ubuntuforums.org/showthread.php?t=903451&highlight=Creative)
[http://forums.creative.com/creativelabs/board?board.id=soundblaster](http://forums.creative.com/creativelabs/board?board.id=soundblaster)
[http://forums.creative.com/creativelabs/search?board_id=soundblaster&submitted=true&q=linux](http://forums.creative.com/creativelabs/search?board_id=soundblaster&submitted=true&q=linux)


Wait, I should mention that I'm fairly new to linux, but, "new" includes compiling the new kernel to get the X-Fi working. You say the reason they don't work together is because the X-Fi driver is trying to use the same IRQ as the graphics card, but I don't know how to change the IRQ ctalsa is trying to use, or if there are even any that are free. Do you know how to change the IRQ?

---

### Post by Shazaam on 2008-09-08
Not off hand I don't. Keep searching, I am sure you are not the only ones with X-Fi/linux problems.

---

