---
title: "Keyboard problems in Breezy - possible SOLUTION"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by bertilow on 2005-10-14
A lot of people have reported problems using their various national keyboard layouts after upgrading to Breezy. I had such problems too, and I was on the brink of throwing out Kubuntu for good. But then I had some luck getting my Swedish keyboard to rise from the grave. I'll explain what I did.

This is a drastic solution, so only try it if you've already tried everything else you can think of. Be warned. Please read through the whole explanation before trying anything.

Open up Synaptic (the package manager).

Search for "xkeyboard-config". Mark that package for _complete removal_.

Synaptic will tell you that it needs to remove several other packages too. Among them are "x-window-system-core", "xlibs" and "ubuntu-desktop". This is the scary part.

Make a note of the names of all the packages Synaptic wants to remove. In my case they were "xlibs", "x-window-system-core", "python-opengl", "ubuntu-desktop", "kubuntu-desktop" and of course "xkeyboard-config".

Accept removing all those packages. You will shortly reinstall them. Hopefully nothing goes wrong inbetween. I lived through this, but be warned.

Choose "Apply".

Watch Synaptic remove the guts of your Breezy installation. :)

Use search too find all those packages again. Mark them for install. Choose "Apply". Watch Synaptic reinstall those guts again.

(I guess you can do all of the above with the "sudo apt-get" command too, or with some other package manager, but I'm not sure exactly how.)

After this you should hopefully be able to activate your national keyboard or keyboards using "System settings", "Control center" or whatever you usually use. If you use "System settings" you might need to first remove your keyboards. Choose apply. And then reselect them, and choose apply again.
You can also activate keyboard layouts with the command 'setxkbmap -layout "se"' (using the desired abbreviation instead of "se" which stands for Sweden).

I must add that before I found this solution, I manually removed most of the files that "keyboard-config" installs. (That was a desperate move.) I removed them both where they seem to live in Breezy, and where they used to live in Hoary. Those locations are "/etc/X11/xkb/symbols/" and "/usr/X11R6/lib/X11/xkb/symbols/" respectively. I have no idea if that manual removal played a part in getting this solution to work. Probably not. Manually removing those files is a very drastic step, so I don't recommend it. Using the above solution should however reinstall them in the new location for Breezy. The problem is probably some kind of collision between the old Hoary setup and the new Breezy setup for keyboard layout definitions.

I still haven't gotten everything to work though. Dead keys (for accents) still don't work. It seems that Breezy is ignoring the settings in the "Compose"  file. I'm still working on that, but don't set your hopes too high. I hardly know what I'm doing.

Good luck!

---

### Post by bertilow on 2005-10-14
UPDATE: Dead keys (now) work for apps started from a command line (console) but not in other cases. Only if I start e.g. gvim or OpenOffice.org from a command line are the settings in the Compose file being used. Really strange... Anyone? Any developers?

---

### Post by metafor on 2005-11-08
your tip worked for me, at least i can change my keyboard on the console with setxkbmap, and not the most confortable way, but i feel not handicapped anymore. note for swissgerman user, use "ch" instead of "de_CH" with setxkbmap. 

for me persoanally it worked with the commandline apt-tools, i think it's easier to copy the packages marked for removal then find them in synaptic for a later reinstall and probably prevents you from missing something important.

---

### Post by deleta on 2005-11-10
I don't know if I am having the same problem as you.  After I upgraded using Synaptic and rebooting, I was not able to login because I could not type anything.  I have a Spanish keyboard on a Thinkpad T42 laptop.  However, I even connected a US external keyboard via USB and that did not help either. Since I can't log in, I can't use Synaptic or anything else.  However, my keyboard does work from the command line interface when I log in using recovery mode.  Any ideas?

Diego

---

### Post by bertilow on 2005-11-10
[QUOTE=deleta]I don't know if I am having the same problem as you.  After I upgraded using Synaptic and rebooting, I was not able to login because I could not type anything.  I have a Spanish keyboard on a Thinkpad T42 laptop.  However, I even connected a US external keyboard via USB and that did not help either. Since I can't log in, I can't use Synaptic or anything else.  However, my keyboard does work from the command line interface when I log in using recovery mode.  Any ideas?[/QUOTE]

Sorry. I think you have a different problem if you can't type anything.

Anyway, I was never able to make my upgrade to Breezy to work correctly. So I had to do a new install from scratch. I still got a few strange problems, but in the end it worked out, although it took a long time to get all my programs set up again.

---

### Post by deleta on 2005-11-10
Well.  Thanks anyway.  Posted elsewhere to see if I get any ideas.

---

### Post by Vaxis on 2005-11-13
If you have the new Breezy and you want to turn on deadkeys next to your US layout without having to edit config files etc., do the following:

* Go to System > Preferences > Keyboard > Layouts
* Press "Reset to Defaults"
* Add the "U.S. English (with deadkeys)" layout
* Make this layout default and then move it up
* Add another random layout (say Albania)
* Move "U.S. English (with deadkeys)" down and then up again
* Delete the random layout (here: Albania)

It should be fixed!
Let's hope that this quirk will be ironed out soon :)

---

### Post by Henc on 2005-12-24
i removed xkeyboard-config completely. Synaptic asked only for lsb, lsb-graphics, opera, xlibs; nothing like ubuntu-desktop and other "guts". Strange, but I removed them ; After that reinstalled.

And nothing changed - errors still show up and i am not able to switch to my native language keyboard.

Im kinda of f***ed up deep inside - none of the solutions worked so far. There is only two ways - reinstall ubuntu completely or return to previous OS. I just dont have time to mess with these kinds of problems (this one appeared, of course, when i upgraded to 5.10)

---

### Post by UphillSkier on 2005-12-24
I just found the solution in another thread.  Check out 

[http://ubuntuforums.org/showpost.php?p=465307&postcount=13](http://ubuntuforums.org/showpost.php?p=465307&postcount=13)

Works like a dream!

---

### Post by jimw on 2006-01-21
Just recently I was steered to a new Kazakh keyboard layout.  I downloaded it and saved it in the  appropriate place.

However, I have had no luck in calling it up

I used the command 'setxkbmap -layout "se" but with "kz" substituted for "se."  The message came back that it had failed to reset.

Just as a test, I used the command to switch to the Swedish board, and that did work.

Further, the System>Preferences>Keyboard>Keyboard layout comes with the Kyrgyz layout, which works fine.

Unfortunately, I'm no expert, so I'm asking for advice.  What steps must be gone through to set up sch a layout?  Obviously I've missed something, but I don't know enough to be a ble to say just what.

Thanks,

JimW

---

### Post by omer_swe on 2007-03-23
setxkbmap -layout "se"

this worked for me . thankx a lot.:guitar:

---

