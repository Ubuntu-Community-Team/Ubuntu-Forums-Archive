---
title: "Oh my god, it's full of stars!"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Zerp64 on 2010-03-27
So I just installed the 3/26 daily, but I had to do a hard reboot when I first tried to use the system. Anyways, I got the regular plymouth "checking disks for errors" message which was on for about 20 minutes, then ran updates, then rebooted. For whatever reason, I think that fsck was run again...

I say 'I think' because instead of the usual 'checking disks' message from Plymouth, I was greeted by a new screen, with a new Ubuntu logo, that began filling up with glowing snowflake-like stars. This happened for about twenty minutes again, with more and more stars filling up the screen, to the point of causing nasty screen lag.

So my question is, is this seriously the new 'checking disks' screen, or did I just come across something very uniquely bizarre? It was without a doubt the ugliest thing I've ever seen...

---

### Post by arashiko28 on 2010-03-27
> **Zerp64 said:**
> So I just installed the 3/26 daily, but I had to do a hard reboot when I first tried to use the system. Anyways, I got the regular plymouth "checking disks for errors" message which was on for about 20 minutes, then ran updates, then rebooted. For whatever reason, I think that fsck was run again...

I say 'I think' because instead of the usual 'checking disks' message from Plymouth, I was greeted by a new screen, with a new Ubuntu logo, that began filling up with glowing snowflake-like stars. This happened for about twenty minutes again, with more and more stars filling up the screen, to the point of causing nasty screen lag.

So my question is, is this seriously the new 'checking disks' screen, or did I just come across something very uniquely bizarre? It was without a doubt the ugliest thing I've ever seen...

I've had already about 2 disk checks on lucid and never seen anything like that.

---

### Post by kansasnoob on 2010-03-27
I noticed the stars also, but with about a 43 second boot time.

Up until about one week ago my boot times were in the low 20's, now always 40+ seconds :o

---

### Post by jaoc223 on 2010-03-27
I had that happen once after doing some updates last evening, it only happened once. I've not seen it again. It was strange.

---

### Post by grandtoubab on 2010-03-27
maybe you are using 
plymouth-theme-solar

check in synaptic

---

### Post by bwallum on 2010-03-27
Not sure if this is related but it's the same area.

When I boot up grub2 comes up fine and the grub menu. I have a background image for the grub menu screen and the text is displayed ok in a 1024x768 format.

However when the system moves beyond grub to I presume a splash screen, I get some graphics garbage at the top of the screen. I can't see whats going on, could be 'checking disk' i guess when the os bootstrap is delayed.

The Desktop comes up ok.

Similar garbage happens upon exit.

As well as changing the resolution for the grub menu screen I run the nVidia driver for normal graphics.

I presume that the grub menu uses the vga pass through function of the graphics card.

What does the Ubuntu entry and exit splash use? Could the splash(es) be trying to use the nVidia driver before it is loaded?

---

### Post by mafitzpatrick on 2010-03-27
It's from package plymouth-theme-fade-in

I didn't install this, so presumably pulled in with other updates. But, damn is it ugly - feels like I'm back in the 1990s, now where's my shellsuit....

Does anyone know what the 'original' purple background splash package is - I thought that was very nice.

EDIT: plymouth-theme-ubuntu-logo

I think it's fixed with the latest updates

---

### Post by Zerp64 on 2010-03-27
It looked like one of those art dudes was showing their kid the wonders of GIMP copy and paste...

---

### Post by victor9098 on 2010-03-27
:D Happened to me too, but only on my Netbook Edition, never happened desktop. Thought it was weird that they were regressing back to the previous Ubuntu branding (but then, I heard in an interview on Ubuntu UK Podcast they have only a dozen or so letters finished!).

Went into synaptic and noticed that "plymouth-theme-ubuntu-logo" had been uninstalled. Not even sure what did it. Though have to admit that I do like the snowflake affect while booting.

---

