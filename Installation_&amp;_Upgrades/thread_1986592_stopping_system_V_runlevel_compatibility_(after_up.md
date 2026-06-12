---
title: "stopping system V runlevel compatibility (after update to 12.04)"
date: 2012-05-25
forum: Installation &amp; Upgrades
---

### Post by LancerNZ on 2012-05-25
My Ubunbu 11.10 was fine until the Update Manager said I should update to 12.10 LTS. I said yes, and now it won't boot.

I get a "stopping system V runlevel compatibility" error when Ubuntu tris to start up. That is, as Ubuntu scrolls various start up lines, this is where it stops.

I need this working ASAP because it's seriously affecting my graphics business.

From googling around, I know people are going to say "more detail more detail..." seriously the options are cumbersome but I'm still nowhere near land.

[B]
Option 1: Booting from (recovery mode) previous kernels.[/B]
Same error. I think the "upgrade" broke something.
For the record, previous versions include:
Ubuntu, with Linux 3.0.0-17-generic
Ubuntu, with Linux 3.0.0-17-generic (recovery mode)
Ubuntu, with Linux 3.0.0-16-generic
Ubuntu, with Linux 3.0.0-16-generic (recovery mode)
Ubuntu, with Linux 3.0.0-15-generic
Ubuntu, with Linux 3.0.0-15-generic (recovery mode)
Ubuntu, with Linux 3.0.0-12-generic
Ubuntu, with Linux 3.0.0-12-generic (recovery mode)

For these recovery modes, the generic ones end with "*Checking battery state..." and just sit there. At this point I can issue [CTRL][ALT][F1] (etc) to log in as terminal. The command "startx" however just gives black screen and keyboard dead (as in Caps Lock not even responding). Perhaps it did not help that I previously tried "generic graphics" option from recovery mode before?
The (recovery mode) ones end in "stopping system V runlevel compatibility" just like the default (non previous kernal) boot option.

**Option 2: Recovery mode failsafeX.**
This gives a screen saying "Ubuntu is running in low-graphics mode" but when I proceed to the option to use failsafe "for just one session" it brings me back to the main recovery console options, and resume simply goes back to "checking battery state" and stays there.
I tried “reconfigure graphics” once in this mode and it didn't get things working. Possibly it has bawked my Nvidia setup. :-( 

**Option 3: Load the Live CD and install from scratch:**
I downloaded the live CD-ROM (12.10 LTS) and trying to boot from these is also problematic. On the "Try Ubuntu or Install Ubuntu" screen, I can move my mouse (after a while - it is really slow at first) but I can't click anything. I notice that my keyboard is also dead onthe live CD at this stage - even CapsLock etc doesn't activate the LED lights on the keyboard.

**Option 4: Check BIOS settings**
Why? They were fine before? Someone one a page I googled about the "system V" error mentioned to turn of any CPU virtualisation. Done. Still get the error.

**Option 5: run dpkg (the recovery mode one) and it will magically fix everything.**
Now, doing this, Ubuntu reports “10 to remove and 1 not upgraded... 711 not fully installed or removed. Need to get 268 kB/825 MB of archives”. Looks promising... except that my internet is normally through USB wireless so it's not working in this recovery mode. I do also have dialup, which I can normally activate through a script in my /home dirs, but this recovery option won't let me [CTRL][ALT][F1] to go there and turn dial up on. I can get there through the other recovery options, but then I don't know the dpkg flags to make Ubuntu “continue” the install like this option appears to be wanting to do.

If I go into recovery mode “drop to root shell” and then perform startx, I do get a blue screen with mouse cursor!!! There are no useful right-click options though (only “Create new folder”, “create new document”, “Organize desktop by name”, “Keep aligned” and “Change Desktop background”. It looks like a broken Gnome. No option for shell terminal. The [CTRL][ALT][F1] screen ends in...
(EE) Failed to initialize GLX extension (compatible NVIDIA X driver not found).


I'm getting lost about here. Just need my system back. Damned auto-update. I've had updates go very bad in the past (fixed with complete reinstall) and am beginning to think other distros might be an idea.

Can anyone help me recover my system?

---

### Post by oldos2er on 2012-05-25
12.10 is not LTS; it's very alpha right now. Did you mean 12.04?

---

### Post by LancerNZ on 2012-05-25
Ah - yes, sorry.... 12.04 LTS. The one the Update managed recommended.

Damn - I thought someone has answered my thread with maybe... and answer to the problem? :(

I found that my md5 sum of the 32 bit iso I downloaded was wrong and have re-downloaded it. I can get the CD-Rom to work if I go for the "nomodeset" option that's there when hitting a key as it loads (when it shows a keyboard at bottom of screen) and the F6, so it looks like I can completely reformat and reinstall if I have to, although I'd prefer to simply get my upgraded system to work... although running the CD now does give me access to the internet and for emergency restore / recovery but...

...where to now?

---

