---
title: "LOTRO Wine"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by ginderhulk on 2010-11-08
I seem to be having a problem with Wine Program Loader. When I try to run this file, the Wine Program Loader doesn't run, or at least it isn't showing up. Any suggestions as to why?

Wine Version: 1.1.42

File : [http://www.lotro.com/support/download-lotro](http://www.lotro.com/support/download-lotro)

---

### Post by gradinaruvasile on 2010-11-08
As a rule, try the non-launching wine stuff in a terminal to see the error messages.

It works perfectly fine for me in Wine 1.3.6 (i compiled it) on Debian. I previously installed Directx9.

The installer worked without problems.
Specific issues:
- Install the full directx9 package with winetricks
- Use the pylotro launcher, the default one does not work in Wine (maybe it does with hacks and stuff, but its not worth it)
- Switch to PulseAudio within the game for better sound quality
- I am not aware of other specific settings, i did not set anything up (apart of compiling Wine myself and possibly some forgotten registry settings related to video memory or something)

I had to download and install a launcher ([PyLotRO]("http://crossover.codeweavers.com/redirect/pylotro")) that replaced the crappy .NET default launcher that does not work in Wine. 
After that everything is peachy, i have a lowly nvidia 8200 integrated card (+ Athlon II 250 x2 @3.0 GHz CPU) that handles medium-high graphic effects @1280x1024 (Directx9 level, no AA) with no problems. I had no crashes or any problems for 4-5 hours of play.
Interestingly, the game can directly use ALSA/PulseAudio for sound playback regardless of Wine's settings (i had it set to Esound and the sound was choppy, then i switched it to PulseAudio from the game and everything is ok).
I am amazed how fast it is running (in contrast, the native Linux Regnum Online client is dissapointingly slow even with reduced settings) - even with water reflections turned on and the scenery objects rendered at full distance ( i am no 60-fps-is-required-to-play kinda guy, 20-25 is enough for me if i can see water reflections and all kinds of shadows).

---

### Post by ginderhulk on 2010-11-11
Ran it through the terminal, this is what it spit out:

```
err:seh:raise_exception Unhandled exception code c0000005 flags 0 addr 0x8

```

Besides that I have winetricks and the alternate launcher installed.

---

### Post by ginderhulk on 2010-11-14
help anyone?

---

### Post by lacrosse_man16 on 2010-11-25
Please do not go crazy on bumping someone will get to your issue sooner or later. I personally find it very aggravating that people are so impatient,  and normally lose all desire to assist people like this.  Since the solution for yours is pretty simple and you should have realised it earlier completely uninstall wine and install the newest version along with winetricks.  You should have noticed that your version was different than the guy who previously commented and had it working.  Unless of course you skipped over it because he didn't exactly spell it out for you.  You are a user of Ubuntu you should be familiar with having to figure things out yourself a little get your hands dirty. Each problem can have a different cause so its hard to really give you a step by step guide.

---

### Post by Mark Phelps on 2010-11-25
In future, when you have Wine-related problems, instead of posting HERE in this forum -- and bumping repeatedly -- post your question in the Wine subforum.  Folks THERE will see your post and you are likely to get sooner and better answers than here.

---

### Post by 5PUTN|K on 2010-12-22
well im no expert in this but i got mine working using [this]("http://lorebook.lotro.com/wiki/LOTRO_under_Linux_and_Mac_OS/X") howto
so the credit goes to those guys who wrote the lorebook entry and a.jackson for making the gui launcher
1- update your wine version (well u don't really have to)
2- execute these three commands
```
wget [http://www.kegel.com/wine/winetricks](http://www.kegel.com/wine/winetricks)
bash winetricks vcrun2005
bash winetricks vcrun2005sp1
```3- right click on [this]("http://pub.kxd.cc/ddo/freebsd/fakeNET11.reg") and save it on your desktop then go to
```
nautilus /home/USERNAME/.wine/drive_c/windows
```launch the regedit.exe select registry from the top then click on import and select the file  you have just downloaded
4- run this command (if you are using another version write its name  instead of maverick)
```
deb http://ppa.launchpad.net/ajackson-bcs/ppa/ubuntu maverick main
```
5-right click on [this]("http://www.lotrolinux.com/ajackson-public.key") and save it on your desktop launch synaptic and add that file to your list (system>administration>synaptic>settings>repositories>othersoftware>add)
6- search for "pylotro" and install it then the working launcher will be in applications>games>thelordoftheringsonline

if you want to you can remove the keys and authentication stuff later using synaptic

---

