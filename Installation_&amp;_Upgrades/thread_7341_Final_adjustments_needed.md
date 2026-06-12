---
title: "Final adjustments needed"
date: 2004-12-06
forum: Installation &amp; Upgrades
---

### Post by hashimoto on 2004-12-06
Hi,

After a little hesitation I decided to give Ubuntu Warty a go and Mandy 10.0 had to go on my desktop machine. Ubuntu was already running on my laptop and I like it, so I decided I could give it a go on the desktop, too.

Hardware:
Mobo Abit KX7-333 (VIA KT333 chipset) with AMD 1700+XP. 512 Mb, 60Gt HDD, ATI Radeon 7000LE, dual boot with XP.

Issues:
1. During boot I get the following two error messages:
modprobe: FATAL: error inserting shpchp... operation not permitted
modprobe: FATAL: error inserting pciehp... operation not permitted

***
Edit: Nothing new with these yet. Haven't really done any googling on these, but will soon.
***

2. Power off is not working. The last prompt on the screen is something like acpi_power_off_called and I got to shut off pushing the power button some 5 secs.

***
Edit: Added acpi=off apm=off to grub menu and now the shutdown process ends with "Power off" at prompt. Got to shut down pushing the button, but now it shuts down immediately, not after five secs.
***

3. Screen resolution. Highest avail is 1024x768, but I know that higher is possible (HP 1700M display)

***
Edit: Added 1280x1024 to XFree config file. I can now choose this resolution and it works OK, BUT I can't make it stay. After every boot it has reverted to 1024x768. Even if I tell to use the bigger resolution as default. Even if I run the display tool as root. What do I have to select/edit to make the bigger resolution default. Annoying!
***

So the questions are:
What are the errors? I can't see any problems (except the power-off) so what is causing them? How to fix? ANYBODY?

How to get the power off working? What params to try? Nolapic didn't work, acpi=on is no  go... It worked OK on Mandy...

And why doesn't Ubuntu detect my screen resolutions correctly? Somehow I can't even remember the expert installation asking me that.

I was previously running MDK10 and I know none of these should not be an issue. I had no errors, shut-off worked without a hitch and the resolution was properly detected.

Otherwise a great, clean distro and I love it, but would like to solve these so I don't have to go back to Mandy  

Hashimoto

---

