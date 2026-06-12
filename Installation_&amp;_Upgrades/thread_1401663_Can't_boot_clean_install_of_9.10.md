---
title: "Can't boot clean install of 9.10"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by bmcsorley on 2010-02-08
Hi,

A few months back I did a clean install of 9.10 from 9.04 (wanted to clear room so decided against upgrade path) and since then I've been really struggling to boot into it. I've used Ubuntu since 7.04 and never had any issues with it - these issues have only started happening since my upgrade to 9.10. And I was hoping that 9.10 would be the release I could persuade her indoors to not boot into Windows XP!

Anyway my problem is that when I choose Ubuntu 9.10 from the boot list it gets to the point where the Ubuntu symbol is splashed up (with the brown background and the light shining on it) and then the little progress bar underneath freezes and the whole box freezes. It doesn't respond to any keypresses like the "magic" ones and I have mashed CTRL ALT F1 plus others keys repeatedly. Caps lock doesn't respond either so looks like completely frozen, though worth noting that the hard drive still sounds like it's spinning.

I've tried with every boot command under the sun (noapci, nosplash, quiet, noapic etc.) and none of them make any difference bar two - apci=noirq starts the desktop occasionally but with no windows manager, and irqpoll stops the freeze but it never loads the desktop or manager. Both these last two commands work about 1 in 10 boots or so but usually it freezes. I can also sometimes press Escape as soon as the Ubuntu symbol shows on screen and sometimes (about 1 in 5 tries) it gets into the desktop, but only if I hit it before it freezes up. The above does point to an IRQ issue but wondering what has changed since 8.10 and 9.04 which worked perfectly?

I've also booted into recovery mode and updated/fixed packages but the same thing happens with the recent 2.6.31-19 generic as well as -17, -14 etc. As per above I'm dual booting with Windows XP as the default boot option (wife's orders) but don't think this is related.

I've used Ubuntu a lot but not a command line guru by any means so appreciate any help or pointers people may have.

Cheers,
Barry

---

### Post by bmcsorley on 2010-02-08
Sorry - forgot to add it's a fairly old Compaq Presario 6195EA desktop with 1Gig RAM (max possible due to BIOS) but it's fairly raced along with Ubuntu before - unlike Windows XP which gets slower by the day.... ;-)

Processor is an AMD Athlon XP 2200+ MMX 1.8GHz and graphics card is NVIDIA GeForce4 MX 420.

I'm hoping someone can point me in the right direction as don't want to downgrade to 9.04 again!

---

### Post by bmcsorley on 2010-02-10
BUMP......

Anyone got any ideas? I really don't want to revert back to 9.04 unless I absolutely have to. I'm hoping this isn't cause I rushed into EXT4 or something like that..... :confused:

---

### Post by darkod on 2010-02-10
I would dare to say it's the graphics card, but it's a wild guess. :)
If you select the recovery mode entry in the grub menu, does it load to command prompt OK?
In case you have only ubuntu and you don't get the menu, you can see it by hitting Esc but you have to time it after BIOS is done and before ubuntu actually starts loading.

If you're willing to try, there is a video driver handling package you can install in text mode once you reach the command prompt (there is one other menu and make sure you select something like "root with networking" to have internet access, wired at least).

At the command prompt install with:
sudo apt-get install envyng-core envyng-qt

Run in text mode with:
envyng -t

For my ATI it had only one driver to offer so I didn't have to choose anything, just follow the prompts. I didn't need to remove old driver, the Envyng menu will have that option if you want to. For Nvidia I think it offers 3 different drivers and if it doesn't pick one automatically, your guess is as good as mine.

I had an issue with my onboard ATI HD3200 (the pc was restarting itself) and doing this sorted it out right away. No problem since, even after kernel updates.

---

### Post by Sef on 2010-02-10
> Anyone got any ideas? I really don't want to revert back to 9.04 unless I  absolutely have to. I'm hoping this isn't cause I rushed into EXT4 or  something like that..... :confused:

How well does the Live CD work?

---

### Post by bmcsorley on 2010-02-10
Darko - I can boot into the recovery menu as been using that to update all the packages. I had great hopes when it upgraded the kernel to -19 but it made to difference at all.... :( I will try command prompt with networking now and try to those commands to see if that helps thanks.

Sef - Live CD works fine. Is there any way I can use that to check that the install of 9.10 is valid?

---

### Post by darkod on 2010-02-10
> **bmcsorley said:**
> Darko - I can boot into the recovery menu as been using that to update all the packages. I had great hopes when it upgraded the kernel to -19 but it made to difference at all.... :( I will try command prompt with networking now and try to those commands to see if that helps thanks.

Sef - Live CD works fine. Is there any way I can use that to check that the install of 9.10 is valid?

Hmm, it doesn't sound like graphics then. In my case the live desktop was doing exactly the same as when I installed. But once the new driver was installed, no problem.
You can still try it though.

---

### Post by bmcsorley on 2010-02-10
Tried the above commands but no joy - still freezing at the same point...... :(

---

### Post by bmcsorley on 2010-02-14
I think I may have found a way round this - going to try a few more reboots to be sure then will mark as solved, though not entirely happy with 9.10 just now....

Anyway I firstly disabled my automatic login so that I had to log in with my username and password and this seemed to make it easier to get in, though still always required a press of Escape on the splash screen before it freezed up. Once I got to this stage I was able to do a lot more playing around with settings and reboots as could almost guarantee getting logged in again.

I was trying with various windows managers (mainly Metacity) as people elsewhere on these forums seemed to think disabling Compiz had helped but it didn't make any difference for me. Then I finally got around to disabling the advanced Nvidia accelerated graphics drivers (version 96) and it now seems to be running and starting up fine. I haven't noticed much difference yet (and I don't play many games on Ubuntu to be honest) and if it's more stable then happy to stay this way.

However it has raised two questions for me:
[LIST]
[*]Why is version 96 broken for me in 9.10 when I'm pretty sure it worked for me in 9.04? Surely it would have been ported across as is?
[*]Anyone know of any plans for version 97 that may fix my issue?
[/LIST]

Anyway I'm off to try a few reboots and will post back with results.

---

### Post by bmcsorley on 2010-02-16
I'm going to mark this as solved as reverting back to the old Nvidia drivers seems to have fixed my freezing issues but if anyone can answer my question about version 96 in 9.04 or an update to version 97 that would be great.

---

