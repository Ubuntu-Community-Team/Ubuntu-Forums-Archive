---
title: "Trouble installing Freesynd"
date: 2011-09-17
forum: Installation &amp; Upgrades
---

### Post by savetherobots on 2011-09-17
Hi guys,

I'm new to the forum and to Ubuntu, so bear with me. I've been trying to install freesynd, which isn't in the software center and is also a tar.gz file (which is a pain in the ***).

Here's what I did. I unpacked the tar file in terminal:
cd ~/Desktop
tar freesynd-0.5.tar.gz
cd freesynd-0.5

then I tried running the configuration and finishing the install:
~/Desktop/freesynd-0.5$> ./configure

but for whatever reason I got the error that SDL_image could not be found. So I installed the SDL libraries again. That error message went away, but then followed the next line with another error that SDL mixer was not found. I looked and found out that the SDL mixer was already installed. I went ahead and searched for SDL mixer at [http://packages.ubuntu.com](http://packages.ubuntu.com) and found the mixer that was installed (libsdl-mixer1.2), along with the SDL mixer libraries for Haskell programming language (libghc6-sdl-mixer-dev and libghc6-sdl-mixer-prof).

Feeling desperate, since I already had the mixer packages installed, I went ahead and installed the libghc6-sdl-mixer-dev and libghc6-sdl-mixer-prof packages. After that the ./configure went smoothly. The 'make' and 'sudo make install' also went smoothly, with just a few warnings (I didn't see which).

Now I've been trying to run freesynd, but all that happens is I get these errors:
ERROR : Unable to load language file ./lang/english.lng.
Cannot load cursors image: Couldn't open ./cursors/cursors.png
ERROR: Couldn't open file 'ISNDS-0.TAB' (using path: './')
ERROR: Couldn't open file 'ISNDS-0.DAT' (using path: './')
Error : Could not load sounds from file ISNDS-0.DAT

and then freesynd opens as a blank black window (like terminal) and closes immediately. Has anyone successfully installed this program? I love syndicate and would like to play it on linux. This is the most annoying install I've ever done. I'm running Natty Narwhal and it's the 64-bit version. I'm wondering if the game just doesn't support my architecture, but I think I saw somewhere that the newer versions supported amd64....

Any thoughts on how I can fix this? I'd really like to play the game.

---

### Post by Foxcow on 2011-10-12
I'd been trying just as you have to get it running but it looks like Freesynd is strictly 32-bit.

Check out these comments for more info:
[http://www.lgdb.org/game/syndicate_wars_sdl_port](http://www.lgdb.org/game/syndicate_wars_sdl_port)

---

### Post by Rinre on 2012-02-05
I have the same problem(s), I am running Lubuntu 11.04 32-bit however, so the 64-bit architecture can't be the problem.
I needed (?) to install all files with "SDL" and "image" in them that I found with Synaptic in order to do a sucessful ./comfigure command. 
Then the other commands (make and make install) worked fine, but the same error messages appeared trying to run syndicate (with the command "syndicate" in the terminal), or at least three of them :

ERROR: Couldn't open file 'ISNDS-0.TAB' (using path: './')
ERROR: Couldn't open file 'ISNDS-0.DAT' (using path: './')
Error : Could not load sounds from file ISNDS-0.DAT

Does anyone (a developer perhaps) have any idea why this doesn't work??

All the best,
Rinre

---

### Post by chamelboom on 2012-02-23
This error means you have not copied Syndicate DATA folder into Freesynd data folder. You need to have original Syndicate game - ebay might help.

---

### Post by Rinre on 2012-02-23
Ok great thanks for the reply!
Oh, I might have forgotten to do that before, as I recall it it was a bit tricky to find foolproof (me being the fool) step by step instructions for installation and I just followed one I found blindly.

I ended up just deleting freesynd and playing the old game as it is for nostalgia a bit, but with this new info I'll definitely try freesynd out sometime as well.

Thanks again or the tip,
all the best,
Rinre

---

