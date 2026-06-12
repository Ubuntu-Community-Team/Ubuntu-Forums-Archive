---
title: "could not enable desktop, remove packages?"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by jdrodrig on 2007-10-26
Hi,

I just upgraded to 7.10 with no major problems...but...

1) I get a "Could not enable desktop effects" if I tried to set it to "Normal" in Appearance Preferences...I already enabled restricted drives (nvidia-glx-new)....

background: I have an old nvidia 5200 Fx Go..on 7.04 I could get Desktop Effects to work like for 20 minutes before the famous nvidia redraw problem appeared with empty windows....but I heard 7.10 fixed that...and now I am not even getting my 20 minutes!

2) I skipped the "remove packages" of the upgrade process because I thought I read at the beginning of the upgrading that those packages could be marked for removal just because Gusty turned off some repositories....I went to Synaptic and re-marked all repositories....should I remove some of those packages? could that be the source of my problems with Desktop Effects?

Btw, I still have the section "Desktop Effects" on System-> Preferences...isnt supposed to be included in Appearance only?

Thanks...

---

### Post by jdrodrig on 2007-10-26
As an update...

If I run compiz on terminal I get:
jdrodrig@trino-ubuntu:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0324 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity

I guess the last line is the problem, but as I said, on 7.04 at least I got to use the cube for a few minutes...is there a workaround or the desktop effects on 7.10 requires 64mb of video memory?

---

