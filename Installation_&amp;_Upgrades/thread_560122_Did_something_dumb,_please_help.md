---
title: "Did something dumb, please help"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by Bogus83 on 2007-09-25
Hi all,

I'll preface this by saying I've been using Ubuntu for about two and half weeks now, and it is my first foray into the world of linux.  So yes, I am a newb, though I'm a fairly advanced user on the windows end of things.  I'm donning my flame suit now and hoping someone might take pity... :biggrin:

I downloaded and installed an upgrade without being fully aware of what that implied.  I know, I know, that's a rookie mistake.  I booted up to find that new updates were available, included among them the linux kernel 2.6.20-16.  I downloaded and installed it.  Shortly thereafter I noticed that my clock was not updating.  It got stuck on 8:05pm for about an hour.  Figuring something was wrong, I tried to get the clock to sync with internet time servers, which had no effect.  I tried manually setting the time, that didn't seem to work either, although in the manual configuration screen it displayed the correct time (but on the toolbar it did not).  So I rebooted.

Booting up, GRUB launched a new entry (Ubuntu, kernel, 2.6.20-16).  I got this message:

"Error 18:  Selected cylinder exceeds maximum supported by bios.
Press any key to continue..."

Pressing any key brought me back to the GRUB menu.  I was able to sucessfully boot into the Ubuntu, kernel, 2.6.20-15, which is where I'm working from right now.  However, my clock is still wrong.  It is saying 3:38am, when it's really 11:38.  And I still can't change it.

Does anyone know if installing the new kernel might have affected my clock?  I can't see why it would, but I didn't make any other changes before it stopped showing the correct time.

My second question is, although I am proficient enough to modify GRUB to remove the entry that won't load, does anyone know why I got that message?  I'm using a 160GB Hard drive, with about 30Gig free.  I don't think it's a space issue, and I'm single booting (no other OS loaded on this disk).  Below are my system specs, in case that helps:

1.6ghz Athlon single core processor
1.5gig RAM
NVidia fx5200 video card
Sound Blaster Live! audio card


No errors until today.  Any help would be greatly appreciated.

Thank you,

Bogus

---

### Post by lisati on 2007-09-26
Does "right-clicking" on the clock bring anything up on your screen, a menu or anything? There should be one there saying something like "adjust date/time"

As for the update, I'm mildly surprised because usually the updates are *meant* to make life eaiser. Perhaps someone more knowledgable than myself can help.

---

### Post by Bogus83 on 2007-09-28
I actually fixed the clock issue, by unchecking "use UTC" in the preferences for the clock app.  (So yes, right clicking did bring up the menu.)

However the .16 Kernel still doesn't let me boot to it, I'm not sure why.

---

### Post by rsambuca on 2007-09-28
That is an absolutely bizarre error to be getting with one kernel but not another.  Have you tried re-installing the new kernel?  You can do so in the Synaptic Package Manager (System -> Administration -> Synaptic Package Manager).  Should be under linux-image.  Try complete removal and then re-install it.

---

