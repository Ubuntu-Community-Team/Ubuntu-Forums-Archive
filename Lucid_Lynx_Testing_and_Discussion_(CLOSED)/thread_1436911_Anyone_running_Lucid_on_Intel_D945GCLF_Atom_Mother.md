---
title: "Anyone running Lucid on Intel D945GCLF Atom Motherboard"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by pharnet on 2010-03-23
Does anyone have an Intel D945GCLF Atom based motherboard they could test Lucid i386 or UNR on? 

I think I am having a weird IRQ issue? ([https://bugs.launchpad.net/bugs/536699]("https://bugs.launchpad.net/bugs/536699")) and I am wondering if it is just me or if there is something happening with newer versions of the kernel.

It is generating the following messages:

hda-intel: spurious response 0x0:0x0, last cmd=0x000000
hda-intel: spurious response 0x0:0x1, last cmd=0x000000
hda-intel: spurious response 0x0:0x0, last cmd=0x000000
hda-intel: spurious response 0x0:0x1, last cmd=0x000000
...
...

Intermittently slows the machine and/or prevents starting to the gdm while logs fill up with this message. Turning off audio in the BIOS will stop the messages.

[COLOR="Red"]_Work Around for Problem_[/COLOR]
***NOTE - Just an update on this problem (Oct. 20, 2010). Setting the IGD Aperture size from 128MB to 256MB cured the problem for me.**

---

### Post by pharnet on 2010-04-10
*** UPDATE (Oct 20, 2010) ignore the following suggestions and stick to the update in the first post about changing video aperture size to 256MB.**

Problem continues in Lucid Beta2.

Two other possible work arounds:

1) Prevent hda intel driver loading and (unfortunately) startup without sound:

```
sudo gedit /etc/modprobe.d/blacklist.conf
```

and add **blacklist snd_hda_intel** to the last line. Save and reboot.

2) Installing alsa backports seem to allow audio to work (so far):

```
sudo apt-get install linux-backports-modules-alsa-lucid-generic 
```

I am not sure if this is a kernel, driver or alsa problem.

---

### Post by pharnet on 2010-04-10
Even with alsa backports installed the machine seems to intermittently have the "spurious response" problem.

There seems to be other problems. I also notice that there is no wired network when resuming from sleep.

---

### Post by HoTMetaL on 2010-04-25
pharnet,

I'm testing Lucid *Release Candidate* with the **D945GCLF2** board. Everything seems to be working great, no "spurious response" messages. Are you still having these problems with Lucid RC? If you are, make sure the BIOS is up-to-date. The [latest version]("http://www.intel.com/p/en_US/support/highlights/dsktpboards/d945gclf") is 0278, released on 4/14/2010. Newer revisions of the BIOS may fix these issues if the problem is hardware-related.

@AlexanderDGreat: You likely will have _no_ issues using the D945GCLF2 board with 10.04 LTS. I'm using it right now with no problems whatsoever. If you wish to update the BIOS on all of your workstations, you'll need to visit the Intel support site linked in the above paragraph and follow the instructions for updating the D945GCLF2 BIOS on Linux systems.

---

### Post by pharnet on 2010-04-26
Yes, it is still occurring with Lucid RC.

Unfortunately, it is not the D945GCLF2 that I am using. It is the older D945GCLF motherboard and it has the latest BIOS for that model. 

Thanks anyway for the advice. It is a test machine for me and was the first one I ran Lucid against. No big deal for me but I thought I would report the problem. I assume other users will emerge after final release. If you are interested in using Ubuntu on this motherboard, I would recommend using 9.10 for now.

---

### Post by AlexanderDGreat on 2010-04-28
> If you are, make sure the BIOS is up-to-date. The latest version is 0278, released on 4/14/2010. Newer revisions of the BIOS may fix these issues if the  problem is hardware-related.

Hi HotMetal! We have 15 workstations all Intel Atom D945GCLF2. I'm planning to install Lucid Lynx 10.04 LTS (Final) on them. "If" I encounter this error, can you teach me how to UPDATE THE BIOS? I have no idea how.

Thanks. :)

PS I'm planning to replace our server with the new Intel Atom D510MO - I read it's good for a basic small home / office server coz it only uses 18W and can use 4GB RAM 800mhz.

Do you think Lucid Lynx will perform ok and no errors with this?

---

