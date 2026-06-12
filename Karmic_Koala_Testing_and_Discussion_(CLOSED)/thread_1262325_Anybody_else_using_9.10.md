---
title: "Anybody else using 9.10?"
date: 2009-09-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by note32 on 2009-09-09
just wanted to know if anybody else is using 9.10 and what they think of the current version out(alpha 6)

---

### Post by bear24rw on 2009-09-09
i've been using it since alpha 2 working great for me

---

### Post by overdrank on 2009-09-09
Moved to  Karmic Koala Testing and Discussion

---

### Post by Bölvaður on 2009-09-09
I dont find it that exciting at the moment, relatively few bugs, except for the intel one. Ask again on beta2 when we have better idea how the rc will be

---

### Post by Podex on 2009-09-10
There will only be one Beta: [https://wiki.ubuntu.com/KarmicReleaseSchedule](https://wiki.ubuntu.com/KarmicReleaseSchedule)

---

### Post by zenarcher on 2009-09-10
I'm using the current Alpha release of Kubuntu 9.10 (64 bit) on two of my machines here.  I've not experienced any significant problems, at all.  So far as I'm concerned, it's stable enough for my everyday use.

Cheers,
zenarcher

---

### Post by philinux on 2009-09-10
> **note32 said:**
> just wanted to know if anybody else is using 9.10 and what they think of the current version out(alpha 6)

I'm always in pre-alpha, it goes on my second hard drive. This cycle has been a very smooth ride apart from grub2 causing a minor hiccup and nvidia drivers not getting installed.

---

### Post by Funnnny on 2009-09-10
The only thing I hate about testing Karmic is I have to reinstall nvidia driver each time xorg and kernel got updated.

---

### Post by steeleyuk on 2009-09-10
> **Funnnny said:**
> The only thing I hate about testing Karmic is I have to reinstall nvidia driver each time xorg and kernel got updated.

Sounds like a bit of a bug... I've not had to reinstall once. Problem with DKMS maybe?

---

### Post by taavikko on 2009-09-10
> **philinux said:**
> I'm always in pre-alpha, it goes on my second hard drive.

Likewise. As soon as toolchain is uploaded it's time "sed 's/OLD/NEW/g' -i sources.list ; aptitude full-upgrade"

Though, I use them as only OS, no backups/fallbacks for me :D

---

### Post by Vanishing on 2009-09-10
> **note32 said:**
> just wanted to know if anybody else is using 9.10 and what they think of the current version out(alpha 6)

I have been using karmic before alpha 1 come out..:lolflag:
Besides...this is karmic discussion right? i assume everybody here uses it..lol
with a little tweak, its heavens imo.

---

### Post by Funnnny on 2009-09-10
> **steeleyuk said:**
> Sounds like a bit of a bug... I've not had to reinstall once. Problem with DKMS maybe?
Don't know why, the nvidia.ko file still in kernel/drivers/video folder, ubuntu ran fine with 1280x800 res. But I can't get any app that use GL works

---

### Post by ranch hand on 2009-09-10
> **note32 said:**
> just wanted to know if anybody else is using 9.10 and what they think of the current version out(alpha 6)
I am not sure what time zone you are in but A6 is due, here where I am, next week.  I am still having to use A5.

It works, a bit rough right now, getting better.  I am really looking forward to A6.

---

### Post by damarusama on 2009-09-10
I use it everyday for music syth and journaling, apart from a weird bug in ubuntu one few weeks ago I have been using the alpha version for the last few weeks, and it's getting faster and better everyday ! ;)

---

### Post by hikaricore on 2009-09-10
> **Funnnny said:**
> The only thing I hate about testing Karmic is I have to reinstall nvidia driver each time xorg and kernel got updated.

Don't worry it's not just you.  ^_^
In Jaunty I finally got the packaged nvidia drivers working without a hitch, soon as I switched to Karmic I'm back to the same **** again.

---

### Post by philinux on 2009-09-10
> **Funnnny said:**
> The only thing I hate about testing Karmic is I have to reinstall nvidia driver each time xorg and kernel got updated.

Not happening here. I used system>admin>hardware drivers to install. DKMS working as it should here.

---

### Post by Sophont on 2009-09-10
I had it in a VB VM since Alpha 2.

Went onto to bare metal of my new laptop right before Alpha 5 - on which I'm writing this right now. :-)

Occasional small problem - no deal breakers. Very good for an alpha version (had similar good experiences with Hardy and Jaunty - had to skip Intrepid due to PPTP VPN plugin regression).

---

### Post by hikaricore on 2009-09-10
> **philinux said:**
> Not happening here. I used system>admin>hardware drivers to install. DKMS working as it should here.

That's only a frontend for package installation.
The issue is likely an errant file from bad package at one point or another.

---

### Post by VMC on 2009-09-10
> **ranch hand said:**
> I am not sure what time zone you are in but A6 is due, here where I am, next week.  I am still having to use A5.

It works, a bit rough right now, getting better.  I am really looking forward to A6.Do you always re-install from each new alpha? I started at alpha 3 and have kept it way way. I see one reason to use each alpha as it comes along. The only possible reason would be to see if you can boot with new alpha. Maybe I'm missing the point here. When its all said and done, I will most likely re-install the final release, but until then I will just keep up with the updates.

---

### Post by novafluxx on 2009-09-10
> **VMC said:**
> Do you always re-install from each new alpha? I started at alpha 3 and have kept it way way. I see one reason to use each alpha as it comes along. The only possible reason would be to see if you can boot with new alpha. Maybe I'm missing the point here. When its all said and done, I will most likely re-install the final release, but until then I will just keep up with the updates.

NO!

Its amazing how often this question is asked!

Once you install an alpha, simply doing an update through update manager is ALL that is needed to keep your system up-to-date.

The only differences are the installer that may/may not get updated between alpha's and the fact that if you upgrade from Jaunty, you're still going to have GRUB installed, it won't automatically update GRUB to GRUB 2

---

### Post by ranch hand on 2009-09-10
The reason that I have so many variations of 9.10 on my box is that, yes, I do, generally get a clean install of each alpha, either 64 or 32.  I generally update a fresh 9.04 of the other (32 or 64).  I have plenty of room and it is interesting that they all get slightly different updates.

I have been lucky with this recently as none of my 9.10s would boot after one kernal upgrade except for 1 32 and 1 64.  They were both upgrades from 9.04.  The 32 was upgraded back at A2 and the 64 was a fresh upgrade to A5.

I am doing this to try and learn more about how this all works.  I am a noob,  My join date here is when I started with Ubuntu, and linux generally, for the very first time.  This is real interesting.

When testing is over the 2 drives I am using for testing will be formatted and used for other things.  They are getting pretty full now but have enough space to the release (planning).  I also have other OSs on there to see how grub2 interacts with them.  I have 9.04 on there so that I can fall back to something stable if needed or to have a grub-legacy to fall back on (have a time or two).

Some folks play computer games.  I don't.  I play games with my computer.  Linux is the first time in decades that I have enjoyed computing.  I want to learn more.

---

### Post by Funnnny on 2009-09-11
What the point of play games under Linux, Linux itself is a game ;)

---

### Post by ranch hand on 2009-09-11
> **Funnnny said:**
> What the point of play games under Linux, Linux itself is a game ;)
I agree.  I have no time for games.

There is too much to discover in just this distro, let alone all the other interesting distros out there.

I spent most of the day trying to straighten out one of 9 9.10 variations I have on here.  Haven't got it to boot yet but at least the "file not found" message is replace with scrolling text right up to the kernal panic.  This is an big improvement.  May get it to run yet.

---

