---
title: "Games crashing as soon as they start"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by hijacktheleft on 2010-01-06
I have Ubuntu 9.10 on my netbook, and the preinstalled games work fine. But every game I've tried to install, SuperTux, SuperTuxKart, and Freedoom, specifically, crashes. I haven't tried any other ones because of this. They will start, and then I'll get to the main menu and choose to start a new game, and then the game just closes. 

All the drivers are updated as of a couple weeks ago. I read something about disabling screen savers and desktop effects, but I already have all that done. Somebody also mentioning installing caffeine, but apparently, that just automatically does the same thing.  Does anybody have any suggestions??

---

### Post by hijacktheleft on 2010-01-06
Sorry for the double post, but I just wanted to say that I installed these games using the Ubuntu Software Center. When I went to the Synaptic Package Manager, it was showing that I could still mark the same games I had already installed for installation. It seems there were a few dependencies required for the games. I am on an incredibly slow public wi-fi connection right now, so it's going to take a while for everything to download, but I may have solved my own issue. Has anyone had this issue with the Software Center not installing everything that's required?

---

### Post by bogdomania on 2010-01-06
Not that is relevant for something,but i use the terminal (aptitude) to install packages..
  However,i don`t think that the problem is you installed packages from within Ubuntu Software Center.. check again if you have the drivers ok.. and btw.. system log,it  might just help

---

### Post by PureChance on 2010-01-06
I had the same problem with SuperTux (I say had, my workaround was simply to not play it) It doesn't however do this for all games, most work fine for me. Glest, Battle for Wesnoth, Nexuiz, Sauerbraten and Tremulous are all ones I have installed which work without issue, once you avoid the resizing bug which caffeine deals with.

---

### Post by UeB on 2010-01-31
I have a similar problem with prboom (freedoom), when I type prboom in the terminal it starts but when I start a new game the game window just closes, right after the screen to chose the difficulty level.

This is the terminal output:

moritz@skynet:~$ prboom
```

prboom v2.5.0 (http://prboom.sourceforge.net/)
I_SetAffinityMask: manual affinity mask is 1
M_LoadDefaults: Load system defaults.
 default file: /home/moritz/.prboom/prboom.cfg
 found /usr/share/games/doom/doom2.wad
IWAD found: /usr/share/games/doom/doom2.wad
PrBoom (built Jun 23 2009), playing: DOOM 2: Hell on Earth
PrBoom is released under the GNU General Public license v2.0.
You are welcome to redistribute it under certain conditions.
It comes with ABSOLUTELY NO WARRANTY. See the file COPYING for details.
V_Init: allocate screens.
 found /usr/share/games/doom/prboom.wad
D_InitNetGame: Checking for network game.
W_Init: Init WADfiles.
 adding /usr/share/games/doom/doom2.wad
 adding /usr/share/games/doom/prboom.wad
W_InitCache

M_Init: Init miscellaneous info.
R_Init: Init DOOM refresh daemon - 
R_LoadTrigTables: Endianness...ok.
R_InitData: Textures Flats Sprites 
R_Init: R_InitPlanes R_InitLightTables R_InitSkyMap R_InitTranslationsTables R_InitPatches 
P_Init: Init Playloop state.
I_Init: Setting up machine state.
I_InitSound:  configured audio device with 1024 samples/slice
I_InitSound: sound module ready
S_Init: Setting up sound.
S_Init: default sfx volume 8
HU_Init: Setting up heads up display.
I_InitGraphics: 640x480
I_UpdateVideoMode: 640x480 (nofullscreen)
V_InitMode: using 8 bit video mode
I_SetRes: Using resolution 640x480
I_UpdateVideoMode: 0x60000000, SDL buffer, direct access
ST_Init: Init status bar.
P_GetNodesVersion: found version 2 nodes
I_SignalHandler: Exiting on signal: signal 8
I_ShutdownMusic: removing /tmp/prboom-music-1UNBaH
I_ShutdownSound: 
moritz@skynet:~$ 

```

---

### Post by UeB on 2010-02-02
Ok there is already a bug report about it:
[https://bugs.launchpad.net/ubuntu/+source/prboom/+bug/375498](https://bugs.launchpad.net/ubuntu/+source/prboom/+bug/375498)
and the known workaround is to use the debian sid version which works.

---

