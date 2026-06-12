---
title: "how do i install games in Ubuntu?"
date: 2008-08-30
forum: Installation &amp; Upgrades
---

### Post by mountnrydr on 2008-08-30
I am a new Linux user and have had no kind of programing training.  I have searched through Google for Linux games and have found a few I would like to play, Boson is one of them for example.  I downloaded and opened the files with the archive manager, then extracted all files to desktop.  

This is where I get stuck.  I have no idea what I have to do next to be able to play these games.  Everything I have found says stuff about using the terminal to do something.  Compiling or installing or something about a makelist file or something.  I am very confused as you can probably tell at this point.

I guess it just comes down to the fact that I don't know what to type in the terminal to make it do what I want.

Thanks in advance for all help and patience in helping me deal with this.

---

### Post by Partyboi2 on 2008-08-30
You can open up add/remove (Applications>Add/Remove) and look for games to install. eg search for boson and install it.
If you are wanting install windows base games you can look at using [[COLOR=Blue]wine[/COLOR]]("http://www.winehq.org/"). More info [[COLOR=Blue]here[/COLOR]]("https://help.ubuntu.com/community/Wine")

Edit: Here are a few useful links
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by mountnrydr on 2008-08-30
I have installed wine and attempted to install World of Warcraft and it failed after disk 3 so I haven't had any luck with wine yet.

I went to applications>add/remove programs and installed PCSX and now what?  it doesn't do anything.  of couse it is and emulation program allowing you to run PS games on your PC.  Do you have to download the games or is it supposed to allow you to use the actual game disk?

Sorry i know i'm a noob.

---

### Post by Partyboi2 on 2008-08-31
Have you followed a guide to install wow like [[COLOR=Blue]this[/COLOR]]("https://help.ubuntu.com/community/WorldofWarcraft") one?

> I went to applications>add/remove programs and installed PCSX and now what? it doesn't do anything. of couse it is and emulation program allowing you to run PS games on your PC. Do you have to download the games or is it supposed to allow you to use the actual game disk?
I don't use pcsx, but I did come across [[COLOR=Blue]this[/COLOR]]("http://maketecheasier.com/guide-to-playstation-emulator-on-ubuntu/2008/03/19")

---

### Post by mountnrydr on 2008-08-31
thanks for the link but the other games are still confusing to me.  the archive name is "sauerbraten_2008_06_20_ctf_edition_linux.tar.bz2"

I have no idea how to make it work, all the readme and install.txt files tell me a bunch of code i do not understand.  If you could help me with this i would be greatful.  Thanks

---

### Post by Partyboi2 on 2008-08-31
sauerbraten is in the ubuntu repository you can install it by opening add/remove (Applications>Add/Remove) searching for it and installing it. Or you can open a terminal (Applications>Accessories>Terminal) and typing
```
sudo apt-get install sauerbraten
``` Its easiest to install programs from the ubuntu repository then compiling. If you cannot find the program you are wanting to install in the ubuntu repostiories  and find the program elsewhere online try and download the deb package version if you can find one as they are easier to install. But if you cannot find the deb package version then download the source and compile it.
If you need to compile a program you can follow a few guides like:
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html) and the ones listed in my 1st post
(make sure you install build-essential package to compile with)

---

