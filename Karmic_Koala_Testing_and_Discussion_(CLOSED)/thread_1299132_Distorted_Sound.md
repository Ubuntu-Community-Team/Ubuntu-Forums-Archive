---
title: "Distorted Sound"
date: 2009-10-23
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by chriswyatt on 2009-10-23
Hi, I'm getting distorted sound on Karmic Koala.  I can alleviate this by going into ALSAMixer and reducing the volume of PCM.  Trouble is whenever I adjust the volume again using Sound Preferences it always sets it back to 100% again.  The PCM channel seems to feed into the Master channel so I basically get distortion at all volume levels unless I turn down PCM volume.  Anyway I could manually cap the PCM volume level?

I have an HDA Intel sound card with the Conexant CX20551 (Waikiki) chipset.

I guess I never had these problems before as I never tend to have my mixer levels at 100% for just this reason.  Is hiding away all of these channels a good idea?

---

### Post by Neezer on 2009-10-23
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

about a third of the way down is a section titled saving sound settings...

```

sudo alsactl store 0

```

that worked for me, but I had the opposite problem, my volume was way too low.

---

### Post by chriswyatt on 2009-10-23
Tried this but Sound Preferences still throttles it to 100%.  Thanks for the suggestion though.

---

### Post by caish5 on 2009-10-29
Same problem here with...
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)

Any solution yet?
I discovered that if i set it to stereo instead of 5.1 it is ok, but i want 5.1 to work since it's a media center computer.

I'm using karmic 64bit

---

