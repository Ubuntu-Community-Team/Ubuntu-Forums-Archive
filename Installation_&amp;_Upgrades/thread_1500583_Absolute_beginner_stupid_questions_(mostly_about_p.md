---
title: "Absolute beginner stupid questions (mostly about package installation)"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by Istrebitel on 2010-06-03
Greetings.

I have recently tried to migrate to kubuntu. I am reading manuals and studying the matter right now, trying to find help via googling and stuff, but for some (i suppose, trivial) matters i just cannot seem to get help and reading manuals leads me nowhere.

I am sorry if my questions seem trivial or are answered in manpages or on this forum, i tried searching and didnt found...

1) how to correctly install something, for which a "Stable Source Release" is provided. Especially when options are to be set

2) how to get knowledge about what version of something (in this case, ntfs-3g) is installed in my system, and what kind of options were set when it was installed

3) what exactly happens when i type "make" withing a folder i just extracted my "stable source release" gzip to?

4) what exactly happens when i type "make install", how does it know where to put what files, make changes to my system etc...

5) how to undo what it (make install) has done (because i had already corrupted one installation of kubuntu by simply doing an unsuccessfull make install of an x-fi driver package and then an alsa package)

6) when i install something with "apt-get install <packagename>" does the downloading of "source stable" happens and "make install" is ran for me, or something else? 

7) Do gui package managers just do the "apt-get install <package name> " for me when i check to install something or do they do something extra aside from that? Like synaptic?

8) when i install something with the same name, but different version, what happens? like if i do an "apt-get install XYZ" of version 2.0 when i already have XYZ of version 1.0 installed, will 1.0 get overwritten by 2.0 or will i have both installed in my system?

9) how do i know which "options" are used when i do apt-get install of a package? for example, if package says "build with this option to achieve this result" how do i know if this option is on or off or can i control it when i apt-get install this package?

10) if i installed something with "make install" - can i later uninstal if with apt-get uninstall package or i have to somehow manually remove files? what is the common procedure?

11) if i installed something with "make install" - can i later upgrade it with "apt-get"?

12) why i read in books, like for example here ([http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)), that i should partition my disk in multiple partitions:
- one for swap
- one for / file system 
- one for /usr 
- one for /tmp 
- one for /var
- remaining space goes for /home
because then if one gets overflown, full or broken, it wont affect the others, and you can afford to loose some and it eases the recovery of system in case of a fault
but then, kubuntu installs itself just in two partitions, swap and the rest? Is multiple partitions scheme outdated or?

13) Why if i ctrl-alt-f1 out of my KDE and run kate (any gui program), it says "cannot connect to X server" while xserver is indeed running on my pc (otherwise how would kde work?)

14) what is under ctrl-alt-f12, f11 etc, it is a blank screen with a cursor in top-left

15) is there a way to set the vga mode for tty's that are accessible with ctrl+alt+f(1-6) to 80x50 (i prefer that over the 80x25 that is set by default there)
i've read that you could do that in lilo config files you just do vga=extended
but now kubuntu uses grub so... how do i do that?

16) i've read that "linux is good because you can shut down an app that hangs your pc by going to terminal and sending a kill signal, something you cannot do in windows because windows has no way to escape a frozen gui"

But when i had a way to test that in practice (today i tried some decoration scheme for my KDE and it froze my desktop) i found out i have a freaking lot of processes running (with ps -A) and.... well, what should i have done to unfreeze my desktop? And how do i know what exactly hangs my PC in order to terminate it? (like in windows - you very frequently have a nearly dead non-responding pc, but doing CtRL-ALT-DEL shows that "system idle" has about 3/4 of your processor time and there is no problem with memory consumtion either, yet system barely can respond to your input")

17) i've heard and read about "linux needs no reboot" but in practice, installing nvidia drivers requires reboot, for example. So, is it really true or there is a way to make those drivers go without rebooting, they just tell me to reboot because i'm considered a newbie who doesnt know that "linux does not need reboot"?

18) KDE is very annoyingly preventing me from doing anything in "LEAVE" menu without a 30second-confirmation box (shutting down in 30 s...)... and i dont seem to see any settings for that in the gui... same goes for asking me to close my tty's - can it do it by itself? what config file should i edit?

19) As i read, linux filesystem philosophy is that settings go into /etc and that everything is a file, so, in order to change anything in my system it boils down to editing a file. Now, why do the files are so scattered? For example, why does alsa config file live as a hidden file (starts with .) in my home, and a file to set up mounting behavior lies in /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla or /usr/share/polkit-1/actions/org.freedesktop.udisks.policy. 

Do only system apps like mount use /etc for their configs, and how do i generally know where to look if i want to change something (like in windows, i'd  go look in the application path, in my user folder's corresponding folders - my documents, application data etc and in registry). 

20) As i read, linux ideology is about program scattering istelf all over the file system. Countrary to windows where program occupies a folder in which it nests its own folder tree (like data, sound, themes), a linux is said to put binaries into /bin, configs into /etc and so on. What happens if programs are called the same or use same files? For example, if two people make a program with a same name or use same file (for example, alot of windows programs used to use settings.ini to store user settings, if that would be in a same folder...?) or make a same short name for their program (like a long program name abbreviated to three letters for simplicity, but what if two programs have same abbreviations?). How are such situations usually resolved? 
Because in windows, user gets to choose where to install the program, which makes it easy (if i got two apps with same name, both would want to go into c:\Program Files\AppName but i would make second program take \AppName(another_app) for example)
But in linux, you only do make install or apt-get and its there for you...

Once again, sorry if i'm being noobish, but i tried to find answers and i didnt or i found lousy explanations that didnt explain anything truly...

---

### Post by dino99 on 2010-06-03
[http://kubuntuguide.org/Lucid](http://kubuntuguide.org/Lucid)

follow this little help to prepare the needed partitions:

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by ankspo71 on 2010-06-03
Hi,
Synaptic Package Manager, Kpackagekit, and "apt-get install", all install pre-compiled packages. There is nothing to 'configure', 'make', or 'make install' because the packages have already been built for us by someone else.

However, if someone recommended that you compile a package yourself with some special options, you can use the command 'apt-get source' and Ubuntu will download the source code for you so you can compile it yourself. If anyone wanted the source to Amarok, all they have to do is open the terminal and type:
```
apt-get source amarok
```
and it would download the source code to their home folder. "sudo" in this case is not required because there is no installing involved (yet).  The person could also find the source code on the internet and download it themselves.

To find special instructions for source codes, you can look in the source code's files, or at their homepage. I usually try to read any "readme" files, "install" files, "configure" files, "make" files etc. By trying to read those files, I can check to see if they include an uninstall option, see the directories it will install to, the dependencies needed, special options for configuring the source code, and so on.

Here is a good link about installing software in Ubuntu, which can apply to Kubuntu as well.
[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

Hope this helps.

---

### Post by sanderd17 on 2010-06-03
> **Istrebitel said:**
> Greetings.

I have recently tried to migrate to kubuntu. I am reading manuals and studying the matter right now, trying to find help via googling and stuff, but for some (i suppose, trivial) matters i just cannot seem to get help and reading manuals leads me nowhere.

I am sorry if my questions seem trivial or are answered in manpages or on this forum, i tried searching and didnt found...

1) how to correctly install something, for which a "Stable Source Release" is provided. Especially when options are to be set

the normal installing happens via apt-get or their GUI frontends like synaptic, software center ...
> 
2) how to get knowledge about what version of something (in this case, ntfs-3g) is installed in my system, and what kind of options were set when it was installed

Most packages have a "-v" option. if you don't know if it exists, try getting help with the -h or --help option, there you can see what you need to do to get the version
> 
3) what exactly happens when i type "make" withing a folder i just extracted my "stable source release" gzip to?

4) what exactly happens when i type "make install", how does it know where to put what files, make changes to my system etc...

5) how to undo what it (make install) has done (because i had already corrupted one installation of kubuntu by simply doing an unsuccessfull make install of an x-fi driver package and then an alsa package)

Can't answer those
> 
6) when i install something with "apt-get install <packagename>" does the downloading of "source stable" happens and "make install" is ran for me, or something else? 

it installs a precompiled package.
> 
7) Do gui package managers just do the "apt-get install <package name> " for me when i check to install something or do they do something extra aside from that? Like synaptic?

they just execute a apt-get command and somethimes place the output in some nicer form. The advantage of GUI package managers is the capability of searching for the wanted package.
> 
8) when i install something with the same name, but different version, what happens? like if i do an "apt-get install XYZ" of version 2.0 when i already have XYZ of version 1.0 installed, will 1.0 get overwritten by 2.0 or will i have both installed in my system?

If those versions are different packages in the manager, they will be installed next to each other. If there could be problems, the manager will warn you.
> 
9) how do i know which "options" are used when i do apt-get install of a package? for example, if package says "build with this option to achieve this result" how do i know if this option is on or off or can i control it when i apt-get install this package?

the options needed when build are normally to adapt the application to your architecture/OS sindce these pacakges are precompiled, the correct options are already given.
> 
10) if i installed something with "make install" - can i later uninstal if with apt-get uninstall package or i have to somehow manually remove files? what is the common procedure?

11) if i installed something with "make install" - can i later upgrade it with "apt-get"?

Can't answer those
> 
12) why i read in books, like for example here ([http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)), that i should partition my disk in multiple partitions:
- one for swap
- one for / file system 
- one for /usr 
- one for /tmp 
- one for /var
- remaining space goes for /home
because then if one gets overflown, full or broken, it wont affect the others, and you can afford to loose some and it eases the recovery of system in case of a fault
but then, kubuntu installs itself just in two partitions, swap and the rest? Is multiple partitions scheme outdated or?

It's not outdated but it's for big servers. For home use, I would propose a three partition scheme:

about 20 GB for / file system
about 1.5 times your RAM for the swap
and the rest for your home partition.

That way, if you reïnstall ubuntu, your settings (which are in the home partition) will be remained.

> 
13) Why if i ctrl-alt-f1 out of my KDE and run kate (any gui program), it says "cannot connect to X server" while xserver is indeed running on my pc (otherwise how would kde work?)

it's impossible (or at least difficult) to communicate between the different instances of the terminal. xServer is running in the ctrl+alt+F7 terminal so it can't be found by the ctrl+alt+F7 terminal.
> 
14) what is under ctrl-alt-f12, f11 etc, it is a blank screen with a cursor in top-left

I guess ubuntu only starts 7 different terminals. Don't know why. But 7 seems enough :P .
> 
15) is there a way to set the vga mode for tty's that are accessible with ctrl+alt+f(1-6) to 80x50 (i prefer that over the 80x25 that is set by default there)
i've read that you could do that in lilo config files you just do vga=extended
but now kubuntu uses grub so... how do i do that?

16) i've read that "linux is good because you can shut down an app that hangs your pc by going to terminal and sending a kill signal, something you cannot do in windows because windows has no way to escape a frozen gui"

But when i had a way to test that in practice (today i tried some decoration scheme for my KDE and it froze my desktop) i found out i have a freaking lot of processes running (with ps -A) and.... well, what should i have done to unfreeze my desktop? And how do i know what exactly hangs my PC in order to terminate it? (like in windows - you very frequently have a nearly dead non-responding pc, but doing CtRL-ALT-DEL shows that "system idle" has about 3/4 of your processor time and there is no problem with memory consumtion either, yet system barely can respond to your input")

What were you doing to freeze linux? I once did this and it was with a maple calculation. My 3GB ram was just full and the system used the swap in a very inefficient way :P. That's btw the most common problem, you can get more into the ram if you force to swich of the swap
```

sudo swapoff -a

```
and back on
```

sudo swapon -a

```
If you are in terminal, you can use the killall command if you know the name of the process (you can find the name with the ps -A command)
> 
17) i've heard and read about "linux needs no reboot" but in practice, installing nvidia drivers requires reboot, for example. So, is it really true or there is a way to make those drivers go without rebooting, they just tell me to reboot because i'm considered a newbie who doesnt know that "linux does not need reboot"?

there are packages to make a system install it's updates without reboot. Never tried them cause the standard system only asks for reboot when new drivers or a new kernel is installed.
> 
18) KDE is very annoyingly preventing me from doing anything in "LEAVE" menu without a 30second-confirmation box (shutting down in 30 s...)... and i dont seem to see any settings for that in the gui... same goes for asking me to close my tty's - can it do it by itself? what config file should i edit?

I don't know, I use gnome
> 
19) As i read, linux filesystem philosophy is that settings go into /etc and that everything is a file, so, in order to change anything in my system it boils down to editing a file. Now, why do the files are so scattered? For example, why does alsa config file live as a hidden file (starts with .) in my home, and a file to set up mounting behavior lies in /var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla or /usr/share/polkit-1/actions/org.freedesktop.udisks.policy. 

Do only system apps like mount use /etc for their configs, and how do i generally know where to look if i want to change something (like in windows, i'd  go look in the application path, in my user folder's corresponding folders - my documents, application data etc and in registry). 

user settings normally go in your /home, the rest in /etc but there are exceptions, historically grown.
> 
20) As i read, linux ideology is about program scattering istelf all over the file system. Countrary to windows where program occupies a folder in which it nests its own folder tree (like data, sound, themes), a linux is said to put binaries into /bin, configs into /etc and so on. What happens if programs are called the same or use same files? For example, if two people make a program with a same name or use same file (for example, alot of windows programs used to use settings.ini to store user settings, if that would be in a same folder...?) or make a same short name for their program (like a long program name abbreviated to three letters for simplicity, but what if two programs have same abbreviations?). How are such situations usually resolved? 
Because in windows, user gets to choose where to install the program, which makes it easy (if i got two apps with same name, both would want to go into c:\Program Files\AppName but i would make second program take \AppName(another_app) for example)
But in linux, you only do make install or apt-get and its there for you...

If you only install precompiled packages, there will be no problem. There are no files that use the same name in the same directory. When you compile the packages yourself, you have the code so you can alter it if needed (never had to do that).
> 
Once again, sorry if i'm being noobish, but i tried to find answers and i didnt or i found lousy explanations that didnt explain anything truly...
i didn't aswer to everythin but I think you know something more

---

### Post by Istrebitel on 2010-06-09
forgot to say THANK YOU everybody

---

### Post by roschern on 2010-06-09
> **Istrebitel said:**
> Greetings.

3) what exactly happens when i type "make" withing a folder i just extracted my "stable source release" gzip to?

4) what exactly happens when i type "make install", how does it know where to put what files, make changes to my system etc...


If you are still interested — even though you hopefully have learned that in most cases this is not relevant — this is  a high level introduction. 

make will look for a file called "Makefile", and based on the instructions in this file, it will perform different tasks. 

It will invoke a compiler, to compile the source code, and then it will invoke a linker to link the newly built files to the needed libraries. 

In most cases, all of this happens within the folder you are calling make from (and perhaps sub folders), and then make install will copy the newly built executables etc to the places on the system specified in the Makefile. Usually you want to build (i.e. call make) as your regular user, and then you call make install as root (sudo). 

> **Istrebitel said:**
> 
5) how to undo what it (make install) has done (because i had already corrupted one installation of kubuntu by simply doing an unsuccessfull make install of an x-fi driver package and then an alsa package)



This is not necessarily easy. Either you have to manually remove/delete all the files you have installed to your system, or you can call for instance 'make confclean' to do this. This will work only if there is written in the Makefile what this command should do.

---

### Post by Istrebitel on 2010-06-09
Yes thank you thats the answer i was looking for EXACTLY! Now i'm off to study makefiles :)

---

