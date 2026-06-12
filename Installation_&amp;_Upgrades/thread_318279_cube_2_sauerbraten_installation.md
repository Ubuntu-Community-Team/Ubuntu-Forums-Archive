---
title: "cube 2 sauerbraten installation"
date: 2006-12-13
forum: Installation &amp; Upgrades
---

### Post by themerchant on 2006-12-13
How do you install it on ubuntu?

---

### Post by pay on 2006-12-13
Look here [http://www.bitbenderforums.com/forums/showthread.php?p=428705](http://www.bitbenderforums.com/forums/showthread.php?p=428705)
Also if you download it, it should have a run file or something if it is precompilled. try ```
cd sauerbraten
./sauerbraten
```

---

### Post by themerchant on 2006-12-13
cina@cina-desktop:~$ cd sauerbraten
bash: cd: sauerbraten: No such file or directory
cina@cina-desktop:~$ cd sauerbraten_2006_12_04_gui_edition_linux
bash: cd: sauerbraten_2006_12_04_gui_edition_linux: No such file or directory
cina@cina-desktop:~$ cd'/home/cina/Desktop/sauerbraten_2006_12_04_gui_edition_linux.tar.gz' 
bash: cd/home/cina/Desktop/sauerbraten_2006_12_04_gui_edition_linux.tar.gz: No such file or directory
cina@cina-desktop:~$

Thats what it says^

---

### Post by pay on 2006-12-13
I meant after you downloaded it and extracted it.

---

### Post by themerchant on 2006-12-13
I extracted it, and put that in code and it said:
cina@cina-desktop:~$ cd sauerbraten
bash: cd: sauerbraten: No such file or directory
cina@cina-desktop:~$ ./sauerbraten

---

### Post by Brightrock on 2006-12-13
Saurbraten is already configured.  All you have to do is navigate to the folder you extracted the file too (tmp somewhere seems to be default).  I just extracted my downloaded file to my "home" folder.  Then look inside the Sauerbraten folder and you'll see a file called Sauerbraten_unix just double click that and choose "run" and cross your fingers.  If you wanted a nicer way to access it you can create a launcher from the desktop. 

However, I'm having a problem with Sauerbraten.  It freezes, which is kind of awkward, since I was going to compare my Window's install of a Cube game to my Linux install.  I was hoping to compare speed and frame rate, but so far I'm having serious problems with the "just works" aspect of the thing. 

I'm using a Dell 9300 with ATI 300 Graphics card which does work.  I can run beryl (although I'm not trying to run it with the Sauerbraten).   

Any suggestions from anyone?

Thanks,

BR

---

### Post by themerchant on 2006-12-14
Umm, I clicked it, it ran for like 8 seconds in full screen, did something.....its still not installed.

---

### Post by taurus on 2006-12-14
Try to run it from a terminal in case there is an error message...

---

### Post by themerchant on 2006-12-14
I pick the terminal option, it comes to run to the terminal but quickly goes wide screen does something for a few seconds, exits, then it switches back to the terminal and the terminal quickly closes.

---

### Post by taurus on 2006-12-14
You mean you clicked on the program and told it to use a terminal!  Why not open a terminal, Applications -> Accessories -> Terminal, and run it by typing in the name of the program!

---

### Post by themerchant on 2006-12-14
how do I do that (note I'm new to this)

---

### Post by taurus on 2006-12-14
Something like

Applications -> Accessories -> Terminal (that would bring up a gnome-terminal)
```
./sauerbraten
```

---

### Post by themerchant on 2006-12-14
Your platform does not have a pre-compiled Sauerbraten client.
Please follow the following steps to build a native client:
1) Ensure you have the SDL, SDL-image, SDL-mixer, and OpenGL libraries installed.
2) Change directory to src/ and type "make install".
3) If the build succeeds, return to this directory and run this script again.
cina@cina-desktop:~$

---

### Post by taurus on 2006-12-14
Make sure you have those libraries installed on your machine (you an use synpatic to search for them) and install it like what it told you...

```
cd src
sudo make install
cd ..
./sauerbraten
```

---

### Post by themerchant on 2006-12-14
keeps telling me the files don't exist, so I type those code in and drag and drop that file into the terminal to add to each code. Similar problems, any easy walk throughs for this?

---

### Post by BladeOfAnduril on 2006-12-15
I've been trying to install Sauerbraten too, and install keeps failing.  Here is the error returned in the terminal:

root@LinuxFTW:/home/matthew/Desktop/sauerbraten# ./sauerbraten_unix
init: sdl
init: enet
init: video: mode
init: video: misc
init: console
init: gl
Renderer: GeForce Go 6600/PCI/SSE2 (NVIDIA Corporation)
Driver: 1.2 (2.0.2 NVIDIA 87.76)
WARNING: No vertex_buffer_object extension! (geometry heavy maps will be SLOW)
Rendering using the OpenGL 1.5 assembly shader path.
WARNING: No occlusion query support! (large maps may be SLOW)
WARNING: No framebuffer object support. (no reflective water)
WARNING: No texture rectangle support. (no full screen shaders)
init: world
init: sound
open /dev/sequencer: No such file or directory
init: cfg
Could not set gamma (card/driver doesn't support it?)
sdl: Gamma correction not supported on this visual
init: localconnect
init: mainloop
read map packages/base/metl4.ogz (0.1 seconds)
Mining Station by metlslime

2game mode is ffa/default
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  148 (GLX)
  Minor opcode of failed request:  2 (X_GLXRenderLarge)
  Serial number of failed request:  3310
  Current serial number in output stream:  3312
root@LinuxFTW:/home/matthew/Desktop/sauerbraten# 


Any ideas?

---

### Post by themerchant on 2006-12-20
Since I have all the correct development files accesed, I guess I should go to step 2 which is:
2) Change directory to src/ and type "make install".

How do I do that?

---

### Post by themerchant on 2006-12-20
I think I instaled it, now how do I open the game?

---

### Post by iPirates on 2007-03-29
open up the terminal, cd to the sauerbraten folder 
( probably in your home folder, or where ever you saved it to) (not the tar.gz file!)

then in the terminal, type: ./sauerbraten_unix

---

### Post by Talos on 2007-03-29
How i can install SDL libraries?

---

### Post by Talos on 2007-03-30
Sorry for stupid question...
Name of libraries in repository: libSDL-image1.2

---

### Post by whistlerspa on 2007-04-14
I've found this and gaming in general in Ubuntu  hopeless. I get a 0fps frame rate and once in the game I can't get out without a cold reboot of the computer. 

Doom was just as bad as was Quake. The only game I've managed to get working properly  thus far is Wolfenstein3D via dosbox. (but only in a mini screen - same as lxdoom).

Quake was slower than a wet Friday (just like sauerbraten), Quake 2 crashed every time it reached a certain point in the game.

I've installed proprietry ATI drivers for my Radeon 9600 256Mb video card as suggested and have a gig of RAM and a 2GHz processser. 

Gaming on Linux? - I think not. Too much hassle for no reward.

---

### Post by noerrorsfound on 2007-04-14
> **whistlerspa said:**
> I've found this and gaming in general in Ubuntu  hopeless. I get a 0fps frame rate and once in the game I can't get out without a cold reboot of the computer. 

Doom was just as bad as was Quake. The only game I've managed to get working properly  thus far is Wolfenstein3D via dosbox. (but only in a mini screen - same as lxdoom).

Quake was slower than a wet Friday (just like sauerbraten), Quake 2 crashed every time it reached a certain point in the game.

I've installed proprietry ATI drivers for my Radeon 9600 256Mb video card as suggested and have a gig of RAM and a 2GHz processser. 

Gaming on Linux? - I think not. Too much hassle for no reward.
Have you tried creating a thread to get help with these problems?

ATi's Linux drivers are known to be crappy, but you shouldn't have problems running a game like Doom. :-/

I'm able to play Sauerbraten, Doom, and Quake excellently. I'm also able to play newer games such as Quake 4 on the highest settings.

---

### Post by bgryderclock on 2007-05-08
This works in the terminal for me:

> ./sauerbraten

but how do you setup a desktop launcher for it? what is the command?

---

### Post by thepocketdrummer on 2007-05-26
I'm semi-new to this OS as well.

I have no idea which libraries I need to get or what to do after that.

```
Your platform does not have a pre-compiled Sauerbraten client.
Please follow the following steps to build a native client:
1) Ensure you have the SDL, SDL-image, SDL-mixer, and OpenGL libraries installed.
2) Change directory to src/ and type "make install".
3) If the build succeeds, return to this directory and run this script again.

```

That's what I see.

When I go to synaptic and search for OpenGL, I get 235 listed packages. Which do I need?
SDL pops up with a lot too... Does anyone know the exact packages and how to ```
make install
```

This is what I get when I try...
```
make    -C enet/ all
make[1]: Entering directory `/home/pocketdrummer/sauerbraten/src/enet'
Making all in include
make[2]: Entering directory `/home/pocketdrummer/sauerbraten/src/enet/include'
Making all in enet
make[3]: Entering directory `/home/pocketdrummer/sauerbraten/src/enet/include/enet'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/pocketdrummer/sauerbraten/src/enet/include/enet'
make[3]: Entering directory `/home/pocketdrummer/sauerbraten/src/enet/include'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/pocketdrummer/sauerbraten/src/enet/include'
make[2]: Leaving directory `/home/pocketdrummer/sauerbraten/src/enet/include'
make[2]: Entering directory `/home/pocketdrummer/sauerbraten/src/enet'
make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/home/pocketdrummer/sauerbraten/src/enet'
make[1]: Leaving directory `/home/pocketdrummer/sauerbraten/src/enet'
g++ -O3 -fomit-frame-pointer    -Wall -fsigned-char -Ienet/include -I. -Ishared -Iengine -Ifpsgame `sdl-config --cflags`   -c -o shared/tools.o shared/tools.cpp
/bin/sh: sdl-config: not found
In file included from shared/tools.cpp:3:
shared/pch.h:30:17: error: SDL.h: No such file or directory
shared/pch.h:31:23: error: SDL_image.h: No such file or directory
shared/pch.h:36:24: error: SDL_opengl.h: No such file or directory
shared/pch.h:38:22: error: GL/glext.h: No such file or directory
make: *** [shared/tools.o] Error 1

```

---

### Post by thepocketdrummer on 2007-05-26
Ok, I think I found the packages. Someone tell me if I installed the wrong things. This worked though.

cl-sdl
cl-sdl-mix
cl-sdl-img
cl-sdl-opengl

Those allowed me to go to the src folder and use make install.

I can run the game by clicking the file, but I can't make a Launcher for it that works.

I want to add this to the command -w1680 -h1050
It works in terminal, but I don't want to type it every time I want to play

------

I think I figured it out. I made a file in bin_unix and entered the following in the file
```
#!/bin/bash
cd /home/pocketdrummer/sauerbraten/
/home/pocketdrummer/sauerbraten/sauerbraten_unix -w1680 -h1050
```

Then I added that file in the command section of the launcher. Seems to work now.

---

### Post by Chronos6 on 2007-06-26
i have a problem with Cube (sauerbraten), i've installed it, got SDL, but i see this when i run it from console:
[IMG]http://kepfeltoltesbcs.extra.hu/files/woowaa1182877207.png[/IMG]
I think i dont need to say anything more:D

maybe i do: ubuntu 7.04, beryl(tried with metacity), alsa

---

### Post by MustNotSleep on 2007-08-26
[FONT="Courier New"]man[/FONT] is your friend, guys.

the reason sauerbraten wasn't loading for me (and most of you, probably) is because our gfx card is poop and has no pixel shader support (Intel 915GM for me).

to disable pixel shaders in sauerbraten, run this command:
```
sauerbraten -f
```
and hopefully the game will load in all its ~5fps glory. enjoy!

type [FONT="Courier New"]man sauerbraten[/FONT] for more handy command-line switches.

and get an nVidia card if you hope to ever run this at a decent framerate.

---

### Post by mikeize on 2007-09-13
edit:  nevermind ;-)

---

### Post by telemetry on 2007-09-29
I got Sauerbraten running using the tips in these pages.  runs really fast on my modest 7100GS.

I'm wondering though - there doesn't seem to be an option for saving in game progress - other than respawning whilst playing the game but this is lost on restart.

Am I missing something?

thanks
robert.

---

### Post by thedarkdonut on 2007-11-07
> **bgryderclock said:**
> This works in the terminal for me:



but how do you setup a desktop launcher for it? what is the command?

As for me I edited the sauerbraten_unix shell file.  All I did was comment out the the SAUER_DIR=. line, uncommented #SAUER_DIR=/usr/local/sauerbraten, and edited it to point it to the actual folder that I have the sauerbraten folder place at.  So the top of my sauerbraten_unix shell file now looks like the following:

```

#!/bin/sh
# SAUER_DIR should refer to the directory in which Sauerbraten is placed.
#SAUER_DIR=~/sauerbraten
SAUER_DIR=/usr/local/games/sauerbraten
#SAUER_DIR=.

```

As for the launcher the command line I'm using is:
```

/usr/local/games/sauerbraten/sauerbraten_unix

```

Executed the launcher and it works fine for me.

---

### Post by hammertm on 2008-03-24
Its all very easy really - you may have to go to the Synaptic Package manager and mark/install libsdl-image-1.2, then it really is as easy as ./sauerbaten_unix from terminal.

Don't forget to cd to the directory that you unzipped it to.

ATI gfx drivers are the issue if you are getting poor FPS I get 200fps with the nvidia drivers that you install from restricted drivers option.

This game is brilliant/slick/superfast - some of the best deathmatch/captuer the flag gaming to be had.:guitar:

Its easier if you unzip into your home folder somewhere then you don't need to sudo all the time, or change permissions.

---

### Post by red_beard19 on 2008-03-25
Hey,

I am a total noob with Ubuntu, but I was playing with the synaptic package manager and sauerbraten appears under one of the games and entertainment headings. Dunno if this is true for anyone else (I am running 7.10), but it may save some headache.

---

### Post by daninkorea_ on 2008-04-19
> **red_beard19 said:**
> Hey,

I am a total noob with Ubuntu, but I was playing with the synaptic package manager and sauerbraten appears under one of the games and entertainment headings. Dunno if this is true for anyone else (I am running 7.10), but it may save some headache.

Haha, that's quite helpful, thanks!^-^

---

