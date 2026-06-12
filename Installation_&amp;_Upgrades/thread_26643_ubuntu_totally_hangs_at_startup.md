---
title: "ubuntu totally hangs at startup"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by ultima2k on 2005-04-13
Just installed Ubuntu as dualboot with Windows XP, no problem booting any of them.
The problem is when you try to login and get started, the welcome-sound is fired up and the mouse-pointer is working and that's it...nothing more happends..
If I try go to the session-menu at login and select something it's the same, the clock isn't going anywhere.

Is there anyone who know something about this?


Gonna try reinstall it now, maybe it'll fix it..

---

### Post by jeremy on 2005-04-13
which kernel are you using?

---

### Post by zibius on 2005-04-13
Same here, fresh hoary install on a thinkpad. Warty was working fine.

---

### Post by ultima2k on 2005-04-13
[QUOTE=jeremy]which kernel are you using?[/QUOTE]

It says "2.6.10-5-386" where you select what to boot..

Really want it to work. A friend had no problems installing it :(

---

### Post by ultima2k on 2005-04-13
Can't anyone help me??

I thought I could spend the evening testing Ubuntu, but what a shame  :sad:

---

### Post by ziphnor on 2005-04-13
I have exactly the same problem. X starts up, i have a nice login screen, and some jungle music plays. If i then log in, i get a brown screen with a working mouse cursor and nothing else happens.

I also tried restarting X, and choosing fail Gnome as login, but the exact same thing happens.

This is a clean install of hoary 5.04 from the install CD. 
I chose English as language, Denmark as country, and Danish as keyboard layout.

I can login with failsafe terminal however, but where is the fun in that, except enabling to somehow fix this problem...

Looking in /var/log/Xorg.log i see some warnings about font paths and "Open APM failed". I also get a warning for my monitor's (Dell 2001FP 20" LCD)1600x1200 resolution, says mode clock 162Mhz exceeds DDC max. 160Mhz.
Finally at the end i get some warning: font renderer  ... already registrered, followed by a single Could not init font path element unix/:7100, removing from list.

The /var/log/gdm/* logs have similar font renderer warnings but no real errors.

After being forced to repartition my main HD because the parted couldnt read my partition table, followed by this, im starting to wonder whether or not to just give up and install Feodra core or even just go back to Gentoo, even though it takes ages to install :(

---

### Post by ziphnor on 2005-04-14
Doesnt anyone know anything about this problem, or know where to look for error messages? 

Im now trying to install kubuntu-desktop from the failsafe terminal in case that helps, but i would really like some feedback on this problem.

Update: I can now login to KDE, so i guess the installer somehow made a mistake with Gnome, pretty nasty error.

I guess ill try remove ubuntu-desktop followed by install ubuntu-desktop to see if that helps....

Btw, whats with those jungle drums that KEEPS playing even after you log in, how do i get rid of them?!?

Update 2: Well removing/reinstalling ubuntu-desktop didnt help, i guess because it didnt reinstall all its dependcies as well. How to i force apt-get to reinstall ubuntu-desktop and all its dependcies(ie all the gnome packages?)

---

### Post by Dr Gonzo on 2005-04-14
You really just needed to 'apt-get install gnome'.  You could then 'apt-get remove kde'.

---

### Post by ultima2k on 2005-04-14
what do you mean??

Should I remove gnome and download and install it?

EDIT: can you be a little more specific, cause I'm a total n00b with linux...

---

### Post by ziphnor on 2005-04-14
[QUOTE=Dr Gonzo]You really just needed to 'apt-get install gnome'.  You could then 'apt-get remove kde'.[/QUOTE]

I believe i did try apt-get install gnome, but was told the package didnt exist, but perhaps i made typo.  I have used synaptic to start reinstalling all the gnome packages, perhaps that will help, ill see when i get home.

Btw, i dont want to remove KDE, KDE has some nice programs, but i still want to use Gnome as my main wm, and gmd as my login(right now gdm works nicely for login into KDE, it just wont start Gnome ;)

Btw, do you know how to stop the zulu music in the background, or fix it so it works properly?

---

### Post by ziphnor on 2005-04-14
[QUOTE=ultima2k]what do you mean??

Should I remove gnome and download and install it?

EDIT: can you be a little more specific, cause I'm a total n00b with linux...[/QUOTE]

When you login, click session and choose failsafe terminal. On the terminal do a 'sudo apt-get install kubuntu-desktop' command. This will install KDE alongside Gnome, when asked whether to use kdm or gdm, choose gdm..
After its done, type 'exit' which will return you the login screen, in session choose KDE, and login as before. For me at least, this gave me a working KDE setup, from which i hope it will be easier to repair the Gnome installation. 

You could also just try 'sudo apt-get --reinstall install gnome' at the failsafe terminal, which hopefully reinstall Gnome, and thus might fix whatever is wrong.

Btw, do you also have the annoying zulu/drum music thing in the background ALL the time?

---

### Post by ultima2k on 2005-04-14
[QUOTE=ziphnor]When you login, click session and choose failsafe terminal. On the terminal do a 'sudo apt-get install kubuntu-desktop' command. This will install KDE alongside Gnome, when asked whether to use kdm or gdm, choose gdm..
After its done, type 'exit' which will return you the login screen, in session choose KDE, and login as before. For me at least, this gave me a working KDE setup, from which i hope it will be easier to repair the Gnome installation. 

You could also just try 'sudo apt-get --reinstall install gnome' at the failsafe terminal, which hopefully reinstall Gnome, and thus might fix whatever is wrong.

Btw, do you also have the annoying zulu/drum music thing in the background ALL the time?[/QUOTE]
 I were gonna try go to sessions, but now there was something new and funny. The menu was just clear white and nothing more :S
After reinstalling ubuntu about 3 times I got the choises(spelling?) in the session menu back, but when I choose failsafe terminal it just hangs up like before :(

Tryed booting the ubuntu rescue or what it's called to use the commands, but they aren't working...

I just love problems lite this :(

---

### Post by ultima2k on 2005-04-15
Anyone?

---

### Post by ultima2k on 2005-04-18
I really want som help please...
Just tried installing it with the same disk om a computer with mini-itx motherboard and some other stuff and it worked perfekt without problems :S

So there's something with my hardware that ubuntu doesn't like.

This is my hardware-specs(copy and paste from another site :p):
Antec Plus1080AMG 430W True Power | ASUS A7N8X-X | Athlon XP2800+ @ 3600+ | 2x 512Mb TwinMOS PC3200 | Leadtek 6800LE @ 390/875, 16x1,6vp 1.4v NV5-silencer | 2x 120GB + 200GB = 440GB

===

Tried unplugging 2 of my 3 harddrives and runnign with one of the memmory-sticks at the same time, but the same result.
Also tried the command to install KDE throught the ubuntu-rescue (sudo apt-get install kubuntu-desktop), but it says that it can't find the package.


Someone gotta be able to help :(

---

### Post by z3n on 2005-04-20
I had the same problem with it loading to a brown desktop without any of the gnome panels loading.  It turns out that ACPI was causing all the problems.  I did a reinstallation using  the following: ```
linux pci=noacpi
```  I belive its in the F7 options menu..but I'm not entirely sure.  After that, everything worked perfectly.  Hope this helps!

---

### Post by ultima2k on 2005-04-21
Got this solved some time ago.
I just had to install nvidia-glx, not easy for a n00b to know :S

---

