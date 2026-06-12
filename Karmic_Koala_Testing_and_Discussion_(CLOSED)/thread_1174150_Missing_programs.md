---
title: "Missing programs?"
date: 2009-05-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jfernyhough on 2009-05-30
Is there anyone else with programs missing despite the package being installed?

The two I've noticed so far are vol_id (from udev package) and asoundconf (from alsa-utils). It's a little annoying. :)

A reinstall or purge,install of the package doesn't seem to help.

64-bit now, btw.

---

### Post by taavikko on 2009-05-30
vol_id
```
udev (141-3+gitf079968) karmic; urgency=low

  * Update to GIT HEAD:
    - vol_id removed, rules converted to using blkid.

  * Rebuild to hopefully fix FTBFS due to bad diff.gz

 -- Scott James Remnant <scott@ubuntu.com>  Mon, 11 May 2009 11:44:04 +0100

```

Will look into asoundconf...
But probably due to ALSA's autoconfiguration...

```
alsa-utils (1.0.19-1) unstable; urgency=low

  * New upstream release (closes: #509176, #485661)

  [ Elimar Riesebieter ]
  * Get rid of asoundconf. (closes: #505089, #433134)
    - Remove python dependencies (closes: #508563)

```

---

### Post by jfernyhough on 2009-05-30
Nice, thank for that.

Trust me to be trying to use programs that don't exist any more!

Ah, there we go. UUIDs for my drives by running $ sudo blkid

---

### Post by psyke83 on 2009-05-30
> **jfernyhough said:**
> Nice, thank for that.

Trust me to be trying to use programs that don't exist any more!

Ah, there we go. UUIDs for my drives by running $ sudo blkid

FYI, the asoundconf program is obsolete now. PulseAudio chooses the default card and does not respect the ALSA card indexes or .asoundrc configuration. You should use pavucontrol to set the default card.

---

### Post by seeker5528 on 2009-05-30
> **psyke83 said:**
> FYI, the asoundconf program is obsolete now. PulseAudio chooses the default card and does not respect the ALSA card indexes or .asoundrc configuration.

Asoundconf being obsolete and PulseAudio having no respect for ALSA are two unrelated issues. 

Just thought I would point that out. ;)

Later, Seeker

---

### Post by psyke83 on 2009-05-30
> **seeker5528 said:**
> Asoundconf being obsolete and PulseAudio having no respect for ALSA are two unrelated issues. 

Just thought I would point that out. ;)

Later, Seeker

;). I meant to say "obsoleted by PulseAudio". I have no idea why they removed the program, though - it's useful for cases where PulseAudio isn't used (e.g. Kubuntu).

---

