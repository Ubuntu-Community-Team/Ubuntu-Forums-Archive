---
title: "cyberlink"
date: 2011-04-17
forum: Installation &amp; Upgrades
---

### Post by OmeRavoch on 2011-04-17
hello everyone.
i'm new on ubuntu.
when i was on window i playd all my video on cyberlink.
is there cyberlink to linux as well.
if there is please give me a link for download.

one other thiing.
i have a 3D movie on my pc, and its a iso file.
i do archive mount and there is a new folder in my desktop and when i try to get inside that folder its ampty.
i try drag the folder inside the movie player and i get that messeage:
Search for suitable plugin?
The required software to play this file is not installed. You need to install suitable plugins to play media files. Do you want to search for a plugin that supports the selected file?

The search will also include software which is not officially supported.

and then:
No packages with the requested plugins found
The requested plugins are:

X-NAUTILUS-DESKTOP protocol source
what i need to do to play a 3D movie.

i try to drag it to VLC player to but it didn't work.

---

### Post by stealth. on 2011-04-17
I'm not positive but, I think it may be because you don't have the right repositories enabled and I think what you want is proprietary and not open source so its not installed/enabled by default. 


First read this thread: [http://ubuntuforums.org/showthread.php?t=1530601](http://ubuntuforums.org/showthread.php?t=1530601)

Use Synaptic to install "ubuntu-restricted-extras" or you can enter the following into the terminal:

sudo apt-get install ubuntu-restricted-extras


If that does not work:
Go to System>Administration>Updates and click settings;
Then you need to enable one of the repo's. I'm not sure which one it is, you just enable all of them then try it again, then revert back to the way it was once your done. 

Tell me how it goes

---

### Post by OmeRavoch on 2011-04-17
Its askin for:
CD/DVD 'Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)' is required
Please insert the above CD/DVD into the drive '/cdrom/' to install software packages from it.

---

### Post by OmeRavoch on 2011-04-17
i don't know what it is

---

### Post by stealth. on 2011-04-18
> **OmeRavoch said:**
> i don't know what it is

Did you try "sudo apt-get install ubuntu-restricted-extras"

---

