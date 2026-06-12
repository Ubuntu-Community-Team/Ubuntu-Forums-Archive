---
title: "A few questions"
date: 2005-09-10
forum: Installation &amp; Upgrades
---

### Post by Porkchop on 2005-09-10
I have a few questions concerning Linux since im still really new to them.

1) Defragmentation tool - is there one like windows had? If so do i have to download it or is it already on the ubuntu OS? How do i run it?

2) Anti-virus/Firewall - Are these needed in Linux? If so can someone point me to a free version of one or both with instructions on how to install?

3) Mobo Drivers - Im on a nForce3 Motherboard, should i install drivers for my motherboard or will i be fine without them?

4) Kernell - When a new kernell(sp?) or something equaly major (is there?) comes out fixing bugs, etc... do i have to burn a new OS disc and re-install or can i do it via the updates thingy by the clock?

5) Quick Launch Icons - The icons by the system drop down menu, is there a way i can create more of these, ex: Make gnomebaker an icon there instead of the Applications drop down menu?

Thats all i can think of now, if i have more ill either edit this post or make a new one depending on how long this one has been dead :)

---

### Post by Leif on 2005-09-10
1) you don't need a defragmenter, as the filesystem is robust against this

2) no, not really. if you want them, you can find instructions at ubuntuguide.org (read this regardless)

3) don't have one, so I can't answer

4) no, upgrades are seamless, even between distribution releases. you will never have to re-install again

5) just drag and drop the icons from the menu to the taskbar

---

### Post by angkor on 2005-09-10
1) No need for defragmentation on Linux
2) No need for anti-virus except for protecting windows-boxes in the network, if you really want a firewall, use firestarter, a front-end to iptables.
3) It's your choice
4) Update thingie
5) Right-click the top panel and select add to panel

---

### Post by Steve1961 on 2005-09-10
[QUOTE=Porkchop]I have a few questions concerning Linux since im still really new to them.

1) Defragmentation tool - is there one like windows had? If so do i have to download it or is it already on the ubuntu OS? How do i run it?

2) Anti-virus/Firewall - Are these needed in Linux? If so can someone point me to a free version of one or both with instructions on how to install?

3) Mobo Drivers - Im on a nForce3 Motherboard, should i install drivers for my motherboard or will i be fine without them?

4) Kernell - When a new kernell(sp?) or something equaly major (is there?) comes out fixing bugs, etc... do i have to burn a new OS disc and re-install or can i do it via the updates thingy by the clock?

5) Quick Launch Icons - The icons by the system drop down menu, is there a way i can create more of these, ex: Make gnomebaker an icon there instead of the Applications drop down menu?

Thats all i can think of now, if i have more ill either edit this post or make a new one depending on how long this one has been dead :)[/QUOTE]


Not sure about the defragmentation option but every 30 boots my system does a file structure check at start-up.  From what I can gather defragmentation isn't much of a problem with linux anyway.

You can download a firewall and anti-virus package.  Just typethe following commands:

sudo apt-get install firestarter
sudo apt-get install clamav

You don't really need anti-virus but if you share files with windows it means that you don't infect your windows system with viruses that have no effect in linux.

You shouldn't need to install motherboard drivers.  I have an nforce4 board and everything was set up automatically at the time of the installation.

You can set up more icons on your panels.  Just right click on the panel, choose add to panel, and follow along.

As for a new kernel, other than the updates that come down the line automatically, a new version of ubuntu is released very 6 months.  You can install a new system from scratch then, or upgrade your existing system as is.  The choice is yours.

---

### Post by Porkchop on 2005-09-10
Awesome! Thx all!

one more questions, When i go into file browser, i cannot do anything with the filesystem part of File Browser.

Im the only one using this computer so i should be the "owner" of everything but when i try to paste, make a folder, etc in the filesystem it says im not the owner and i only have read access. How do i change this?

---

### Post by Leif on 2005-09-10
by default you do not have administrative privileges to files outside your home directory in linux. if you do need to play around with things, you need to change to root mode. open a terminal and type "gksudo nautilus", then enter your normal password.

keep in mind that there's a good reason you can't play around with the filesystem without being root, and that it is highly discouraged unless you have a good reason and know what you're doing.

---

### Post by angkor on 2005-09-10
and to create a menu-item for gksudo nautilus look here:

[http://www.ubuntuguide.org/#browsefilesfoldersasrootnautilus](http://www.ubuntuguide.org/#browsefilesfoldersasrootnautilus)

Take a look at the rest of the guide as well, while you're at it. You won't regret.

---

### Post by Porkchop on 2005-09-10
alright, i dont know what im doing so....

Ill ask this instead:

I downloaded 2 games for the WAN thingy goin on and i dont know how to work either of them in linux.
Both are supposed to be Linux capable.
The first is Wesnoth-0.9.7
The other being Nexuiz12

i cannot figure out how to get either of them up and running under linux.
I try to get to the folders via Terminal
They are located in:
Wesnoth- /home/porkchop/wesnoth-0.9.7
Nexuiz- /home/porkchop/Nexuiz
But when i go to terminal and type "cd /home/porkchop/gamename" it says that there is no file/folder.

Any help would be greatly appreciated :)

---

### Post by Leif on 2005-09-10
what do you get when you do a "ls /home/porkchop" ?

also, you can get wesnoth using synaptic and avoid any hassle.

---

### Post by Hairy_Palms on 2005-09-10
yeah but synaptic is a waaay old version of wesnoth and you cant play online without the latest version, remember that the terminal is case sensative so Porkchop isnt the same as porkchop etc

---

### Post by Porkchop on 2005-09-10
[QUOTE=Leif]what do you get when you do a "ls /home/porkchop" ?

also, you can get wesnoth using synaptic and avoid any hassle.[/QUOTE]

I got the latest version of wesnoth for the WAN gaming thingy later on this month i think :)

As for ls /home/porkchop, i get:
"Desktop  Firefox_wallpaper.png  Nexuiz  wesnoth-0.9.7"

---

### Post by Leif on 2005-09-10
then you should cd to /home/porkchop/wesnoth-0.9.7. there'll probably be a README or INSTALL file, follow the instructions there. in general, things to compile come in .tar.gz packages. you do "tar xzvf name.tar.gz", change to the directory you just created, "./configure", "make" and "make install"

---

### Post by Porkchop on 2005-09-10
Thats what the readme says to do but when i do
./configure
make
make install

None of those work completely :(
./configure error:
"configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details."

make- "make: *** No targets specified and no makefile found.  Stop."
make install- "make: *** No rule to make target `install'.  Stop."\

Now the install file tells me to go to: [http://www.libsdl.org](http://www.libsdl.org) and [http://www.freetype.org/](http://www.freetype.org/)
Ive only hit the libsdl.org link but i dont know what the game wants me to download and install.

---

### Post by new2ubuntu on 2005-09-11
[QUOTE=Porkchop]Thats what the readme says to do but when i do
./configure
make
make install

None of those work completely :(
./configure error:
"configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details."
[/QUOTE]

install GCC. open a terminal then type:
sudo apt-get install gcc

or in synaptic search packages for gcc and install them :)

You can't compile and make any program without gcc the Gnu C Compiler

---

### Post by Porkchop on 2005-09-11
Alright, ive installed gcc and ran ./configure but now i get this error:
"configure: error: *** SDL not found! Get SDL from [www.libsdl.org](www.libsdl.org).
If you already installed it, check it's in the path. If problem remains,
please send a mail to the address that appears in ./configure --version
indicating your platform, the version of configure script and the problem."

I go to that website but i dont know what i need to download.

---

### Post by Leif on 2005-09-11
the easiest and preferred way to install most things in ubuntu is via apt-get. fire up synaptic, search for libsdl, and install libsdl1.2debian, maybe also libsdl1.2-dev

---

### Post by Porkchop on 2005-09-11
Okay, i see it. According to synaptic, i already have libsdl1.2debian, I just removed my CDRom to get my GFs PC onto Ubuntu linux and will be recieving a new one shortly. After i recieve my new one i will post later on how things go :)

---

