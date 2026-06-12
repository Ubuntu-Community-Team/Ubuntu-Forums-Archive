---
title: "display issue observations on nvidia graphics card"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by ketansp on 2010-06-11
my observations in after ubuntu 10.04 display issue.


i ve been using karmic koala x86_64 with my nvidia 8400 gs graphics card. it worked fine.

i upgraded to lucid lynx 4 weeks back. after tthe installation was complete, it wanted a restart. when i restarted it, i could not see anything, not even the bios, neither the grub. nothing. not even live cd worked. _complete blank screen_. i could though listen to the login sound.

after i upgraded to lucid, the display was gone but i ve noted down some of my observations. these might help someone to figure out and fix the display problem.

1. if you have nvidia version 173 driver activated and your desktop effects are at max level. after display **try removing your laptop's battery and putting it back or completely power off your pc.** this might just help and there wont be any display problem. whenever there is, repeat this trick.

2. if you have installed nvidia current or 195.x and have activated it, it will ask for a restart. after restart the bios, the grub, ubuntu desktop, windows, live cd.... nothing works.
SO THERE MUST BE PROBLEM IN VERSION 195 DRIVER

3. i uninstalled jockey-gtk blindly from the command line. i logged into ubuntu , with alt+cntrl+f3 i got into text mode (note, the display wasnt still working.) i uinstalled using the command
```
sudo aptitude remove jockey-gtk jockey-qt
```
i restarted and it worked. the display started after the splash screen. it got a pop up asking me a few options. [B]i selected 'run in low graphics mode for this session only' and that was my biggest mistake. i should have reconfigured graphics at that point only.
[/B]
4. when i shut down that session and started next time, i could see the bios and grub. i was hoping for the display to work in ubuntu also, but it didnt. the display did not work next time onwards.

5. **if you have same problem as mine, i would say, dont shut down once you get display working, just put it by standby.**

6. the reason behind a completly blind display (no bios, no grub, no live cd, no lucid, no windows) is that **my pc is not able to force my os into in low graphics mode**. in some pcs, the ubuntu still works with low graphics mode.

7. i ve tried FRAMEBUFFER, NOMODESET, XORG RECONFIGURING a lot. but none of them really worked.

8. **if by any mean i could login into safe graphics mode, i would be able to rescue my machine **(which is completely unusable right now.)

9. **if by any means, i could reconfigure the xorg or display setting, i could login for at least one time with display working in low graphics mode. **


i guess i ve given a lot of information about this issue. if somebody could help me with these things
1. starting ubuntu in low graphics mode (from command line)
2. reconfiguring the xorg file (from command line only, i ve no gui, no display)

p.s.- i dont have access to internet due to my blindness


thank you.

---

### Post by ketansp on 2010-06-11
i removed my laptop's hard disk and tried to boot fronm a live cd. still i could not get any display (no bios, no grub, nor the live cd).

so even if i format my hard disk, i wont get any display. :confused:

---

### Post by maphew on 2010-06-12
I don't have a solution to your video problem, still trying to fix my own, but if you have access to another machine try logging on through the network via ssh. I'm able to do so using WinSCP + PuTTY from a Windows laptop, so at least I can get to my files and run some commands.

---

### Post by ketansp on 2010-06-12
@ matt

i ve tried the ssh thing and it did not really work out.

---

### Post by kaustubhvp on 2010-06-14
ketan
i have searched a lil on forum n got two links for ur two requests! i haven;t looked into it deeply but it might help
for reconfiguring the xorg  use command : sudo dpkg reconfigure xserver-xorg
or a lasrge process: [http://www.linux.com/news/software/applications/8201-editing-basics-for-the-xorgconf-file](http://www.linux.com/news/software/applications/8201-editing-basics-for-the-xorgconf-file)

for starting ubuntu in low gfx mode use:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by efflandt on 2010-06-14
When I had an issue with no X video (blank screen with no backlight) on an old laptop after activating nvidia(96) and rebooting, I stumbled on something somewhere that said that with laptop displays or when using digital output only, the nvidia binary drivers may assume VGA.  The fix described there that worked for me was to add the following to the "Screen" section of xorg.conf:

Option "UseDisplayDevice" "DFP"

Apparently that is so it recognizes a flat panel display.  Worked for me, but I did not have a problem with BIOS splash or text consoles in (recovery) boot.  It was just X that had been blank.

---

