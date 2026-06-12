---
title: "Happy with 6.06 LTS, I just want to upgrade my hardware"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by xenophon on 2007-02-10
Hi to all.

I've been running Dapper on a low-end system (Intel 915 mobo, Celeron 2.8GHz), off a 200-Gb IDE disk.

My experience with this setup has been so fantastic, now I want to migrate it to a new rig - perhaps one with a Core 2 Duo processor and a new motherboard, with a SATA boot disk.

I can't figure out how to move all my stuff over, which includes applications, themes, etc, with the minimum hassle possible. Oh, I don't really care for Beryl and Cairo, but maybe upgrading to 6.10 wouldn't hurt. Still, my main concern is how to move everything over *verbatim,* without having to install tons of stuff all over again.

Out of curiosity, would the IDE disk be bootable on a different (x86) configuration?

Any help would be appreciated.

With greetings from Athens,

Xen

---

### Post by laidback on 2007-02-10
I have moved a 6.06LTS from one PC to another via a Qparted partition backup which was stored on my USB drive. Now the two systems that I used are of similar vintage so I haven't tried moving to a newer mobo etc but I have read on the forum of people who have done this, their reports were very positive. The last one I read suggested that he simply took the hdd out of the old pc and put it in the new one, booted up and off he went.

My experience suggests that my copy worked exactly the same as the original even though it was on a different mobo, CPU, RAM, video. My internet, email and apps all seem to work fine.

Hope this helps.

---

### Post by xenophon on 2007-02-11
Thank you.

I am very impressed - I thought only Mac OSX could do that!

Still, would it be possible to clone an IDE disk to a SATA disk and still be bootable?

Xen

---

### Post by reiki on 2007-02-11
Cone an IDE disk to a SATA disk...

yes!

In fact I have done exactly that. AND... the IDE disk was originally in my old machine ... a P4 1GHz with 512MB of ram. I upgraded to a newer dual core on a new motherboard with 2 gigs of ram and also replaced the graphics card with a bigger nvidia card.

I put the old IDE drive in the new system and booted from it. Worked fine. Ok so a bit later on (I was on a budget) I bought a SATA drive. Gee, I'd rather have my OS on the sata drive....

I used partimage to clone the IDE onto the sata drive. It worked PERFECTLY. Actually... a bit TOO perfectly because now I had 2 drives with the same UUID. I had to do a little reading about UUIDs, but they're easy to change so this becomes a non-issue.

In other words... what you want to do can certainly be done.

---

### Post by laidback on 2007-02-11
I have had a further thought.
I have been wondering what would be the effect on fancy video cards of this idea. My experience was with simple video cards which were configured to run VGA, not 3D graphics.

reiki may have more info on this.

reki. Could you post info on your mobo and Sata please. I'm interested in upgrade possibilities but have read some bad stories re Sata, sounds as if you have it sorted.

It's been nice to be of help to someone.

---

### Post by reiki on 2007-02-11
I'm using an ASUS P5LD2, PentiumD 930 (3GHz)
This was a cheap way for me to get into dual core and use a processor that could handle virtualization.

Graphics card is an nVidia 7300GT with 512MB (another VERY inexpensive way to improve my graphics capability without breaking the bank)

The P5LD2 allowed me to use my old IDE drive and CD burner. It has LOTS of IDE connections (you can acually have 6 IDE devices hooked up). It has 2 IDE controllers. ONE of them states SPECIFICALLY that you can not run ATAPI devices on it (in other words.. hard drives only... no ATAPI optical drives). It also has enough sata connectors and the capability to do sata raid (I don't use that).

I originally booted from the IDE. When I installed the new SATA drive I was STILL booting from the IDE as primary. When I later decided to boot from the SATA drive I switched it in bios and away we went. No problems. I think I had to edit grub because I had now switched the boot order. That was pretty easy to figure out.

Not one problem from Ubuntu with any of this. I didn't do anything special to get anything running or recognized. Ubuntu finds everything out of the box.

FURTHER THOUGHT regarding graphics card: When I booted the the old IDE drive on the new machine it was using an nvidia-legacy driver. My old card was... well... old!
I uninstalled the legacy driver and installed the nvidia-glx driver and no problems there either.

---

