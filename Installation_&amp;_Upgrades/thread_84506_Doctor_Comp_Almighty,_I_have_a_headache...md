---
title: "Doctor Comp Almighty, I have a headache.."
date: 2005-10-31
forum: Installation &amp; Upgrades
---

### Post by SunshineSmile on 2005-10-31
Aww.. I unwillingly got recruited to the Linux ranks yesterday, after installing an old win OS that wouldnt work with my drivers and in the lack of another boot cd for my PackardBell, I downloaded ubuntu. Hey, it works!! I am online, I have sound, and I have colors!!:KS 

Well okay, down to biznis. I have been sitting here for quite a few hours trying to figure out the essentials, reading through the starterguide at help.ubuntu.com. Unfortunately, there was no help.I amstupid.com page, so I decided to ask here. If this is the wrong place perhaps you would be so nice to point me in the right direction.

I want to figure out the basics: 

**How do I download programs**? I wanna dl videolan, and play my samurai champloo anime. 

I am trying to get familiar with the downloading and installing.. so I wanted to follow an example from the FAQ guide>#

Visit [http://www.real.com/linux/](http://www.real.com/linux/) and download Realplayer 10 for Linux into a convenient directory.
#

Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type

chmod +x RealPlayer10GOLD.bin

**WTF is the *command line??* Where do I find it?**

---

### Post by Pablo_Escobar on 2005-10-31
About VLC, Look for "Synaptic Package Manager" in the menu. There You search for vlc, click to install and presto. (You may need to add extra repositories - go to [http://ubuntuguide.org]("http://ubuntuguide.org") there is a great guide which tells You almost everything You need to know. (Don't know if You're using Hoary or Breezy, but be sure to check it before changing the sources.list file.

Command line = look for open terminal icon in the menu.

---

### Post by SunshineSmile on 2005-10-31
In this guide, when you see black box, means you have to execute the commands in Terminal mode (Applications -> System Tools -> Terminal)

IT IS NOT THERE. Under Applications- system tools, I only have: 

Application menu editor

Bug report

config editor

floppy

Network tools

New login

Run as different user

System Log

System monitor

Ubuntu device database.


I cant believe this.. how can it be so damn hard just figuring out where to find this simple, basic tool.. I feel like"where is the any key... where is the any key"

---

### Post by Pablo_Escobar on 2005-10-31
You can press ALT-F2 and type in gnome-terminal. (if You're using Ubuntu)
But it has to be somewhere, I'm not on my Ubuntu box so I can't guide You.

---

### Post by SunshineSmile on 2005-10-31
ALT- F2 and the type in worked. Thanks!!

...But there has to be a way of getting the terminal onto the application menu where it belongs?

---

### Post by Pablo_Escobar on 2005-10-31
There is a fine way to do it.
1. You need to enable the "universe" repositories (Ubuntu guide)
2. Goto terminal (ALT-F2 way)
3. type in: sudo apt-get update
4. then type in: sudo apt-get install nautilus-open-terminal
5. reboot and now if You right-click on the desktop - Open Terminal is in the menu.

I'd recommend You to browse Your menu, because it simply must be in there.
In 3 hours time I'll be able to pinpoint You to it :)

---

### Post by Pathogenix on 2005-10-31
For some weird, weird, weirder, weirdest reason, Breezy seems to have moved the terminal.

Quick fix: Right click on your toolbar at the top of the screen (I'm assuming you're using Ubuntu, not KUbuntu, and yes, you'd know if you were) and "add launcher"

You'll get a screen up with various things you can add, but you want to add a Custom Launcher.

Set the command to "gnome-terminal", choose an appropriate icon and you've got a shortcut to the terminal.

Repeat the above steps, but use the command "gksudo gnome-terminal" and you've got a second shortcut to a root terminal. If you don't understand the difference, don't worry, you'll know when you need it :)

---

### Post by SunshineSmile on 2005-10-31
[QUOTE=Pablo_Escobar]There is a fine way to do it.
1. You need to enable the "universe" repositories (Ubuntu guide)
2. Goto terminal (ALT-F2 way)
3. type in: sudo apt-get update
4. then type in: sudo apt-get install nautilus-open-terminal
5. reboot and now if You right-click on the desktop - Open Terminal is in the menu.

I'd recommend You to browse Your menu, because it simply must be in there.
In 3 hours time I'll be able to pinpoint You to it :)[/QUOTE]

Argh... Perhaps I have misunderstood the universe repository thingy?

I open my synaptic package manager and it gives me the notice

W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)


I tried installing "terminal" from applications-->add applications-->System Tools-->more programs--> Terminal.. But that doesn t work. 

When I right click on the toolbar where system applications and places is *the main bar.. Then I get to choose Edit menus. I type in the gnome-terminal command and then I have a self made terminal shortcut in the menu.. but strangely it doesn t say Terminal, the header is eine@eine, eine being the loginname I am using. WTF is going on??


AAARGH just forget about it all!!! Should I install my Ubunto ISO over again?? I have 2 OS on this comp, when I whack the cd into the drive, will it automatically format my partition with ubuntu on it?? I give up... damn...

---

### Post by Pathogenix on 2005-10-31
[QUOTE=SunshineSmile]
When I right click on the toolbar where system applications and places is *the main bar.. Then I get to choose Edit menus. I type in the gnome-terminal command and then I have a self made terminal shortcut in the menu.. but strangely it doesn t say Terminal, the header is eine@eine, eine being the loginname I am using. WTF is going on??[/QUOTE]

Aaaaaaaand take a deep breath. Did you name the launcher "Terminal"? You can always right click it and change its name if this bothers you.

Alternatively, if you mean that when you click the launcher, the command prompt says eine@eine then this is perfectly expected, it's so you can see which computer you're logged into and which user account you're operating as. That's not always as obvious as you might think.

---

### Post by Pablo_Escobar on 2005-10-31
It's not a good idea to reinstall if something isn't really messed up :)
About the error you have: Backports aren't yet open, put in sources.list "#" sign in from of the lines shich say backports.
Then > sudo apt-get install nautilus-open-terminal
and then reboot, and Terminal is in the menu when You rightclick the desktop (the most comfortable way for me).
Relax, take a deep breath and report if You have any more problems.

---

### Post by SunshineSmile on 2005-10-31
[QUOTE=Pathogenix]Aaaaaaaand take a deep breath. Did you name the launcher "Terminal"? You can always right click it and change its name if this bothers you.

Alternatively, if you mean that when you click the launcher, the command prompt says eine@eine then this is perfectly expected, it's so you can see which computer you're logged into and which user account you're operating as. That's not always as obvious as you might think.[/QUOTE]

:p Okay, Pathogenix, but in the ubuntu terminal Help file, the examples used "Terminal" I just become a big :confused:  whenever things aint going according to plan..hehe.. 

Well, faghetabout the minor deviations from helpfiles, now I have my terminal up and running. I have downloaded the file; RealPlayer10GOLD.bin to my desktop. How do I use my terminal (I have to be spoonfed this, or I am gonna change my nick into something pathological as well) to install the RealPlayer? First I have to get to the desktop in the terminal.. how do I move to directories in the terminal?? 

FAQ guide says this: #

Make the downloaded file executable. **At the command line, change to the directory where you downloaded the file**,(yeah like how)and type

chmod +x jre-1_5_0_04-linux-i586.bin

#

To install JRE, run the downloaded file. Type

fakeroot make-jpkg jre-1_5_0_04-linux-i586.bin

#

dpkg -i sun-j2re1.5_1.5.0+update04_i386.deb

Thanks 4 the help fellas.. I know ur prolly giggling pretty well, but I was on windows till yesterday and...:???:

---

### Post by Pablo_Escobar on 2005-10-31
To move between directories use "cd" in the terminal.
to get to desktop you need to "cd /home/eine/Desktop" (if eine is Your user name)
then type in "sh RealPlayer10GOLD.bin" (it kinda like chmod +x) :)

---

### Post by SunshineSmile on 2005-10-31
[QUOTE=Pablo_Escobar]To move between directories use "cd" in the terminal.
to get to desktop you need to "cd /home/eine/Desktop" (if eine is Your user name)
then type in "sh RealPlayer10GOLD.bin" (it kinda like chmod +x) :)[/QUOTE]

cool. I try cd/ 

cd/home doesnt work
cd/home/eine doesnt work
cd/home/eine/Desktop doesnt work

Yeah, eine is the name I type when logging on:smile: 

Well, in windows, I could see the name on the folders when browsing so I just typed the path in cmd according to that. Here I open the Home Folder under "Places" on the top menu and "eine - File browser" opens with a clickable desktop. Now how do I find the correct path?

Next posting; how do I tie my shoelace?;)

---

### Post by Pablo_Escobar on 2005-10-31
You must have a space between cd and direcory.
> cd /home/eine/Desktop

Quick question, have You used before a Total Commander or Norton Commander. If so type "sudo apt-get install mc" and when it installs type mc in terminal.
It should give You a quick look how the directories are setup in Linux. 
It's tooooootally different then in Windows.

---

### Post by SunshineSmile on 2005-10-31
eine@eine:~$ cd/home/eine
bash: cd/home/eine: No such file or directory
eine@eine:~$ cd/home
bash: cd/home: No such file or directory
eine@eine:~$ cd/home
bash: cd/home: No such file or directory
eine@eine:~$ /home/eine
bash: /home/eine: is a directory
eine@eine:~$

---

### Post by Pablo_Escobar on 2005-10-31
just copy and paste this int terminal
> cd /home/eine/Desktop
There is a "cd" a blank space and then the directory : "/home/eine/desktop"

---

### Post by SunshineSmile on 2005-10-31
[QUOTE=Pablo_Escobar]just copy and paste this int terminal

There is a "cd" a blank space and then the directory : "/home/eine/desktop"[/QUOTE]

This is what I get when I doubleclick on the file itself
"Couldn't display "/home/eine/Desktop/RealPlayer10GOLD.bin"

This is what the FAQ says I should do: 
   1.

      Visit [http://www.real.com/linux/](http://www.real.com/linux/) and download Realplayer 10 for Linux into a convenient directory.
   2.

      Make the downloaded file executable. At the command line, change to the directory where you downloaded the file, and type

chmod +x RealPlayer10GOLD.bin

   3.

      To install Real Player 10, run the downloaded file. Type

sudo ./RealPlayer10GOLD.bin

      When prompted for a location to install RealPlayer 10, type /usr/bin/RealPlayer

      When prompted to configure system-wide symbolic links, type "y". After that, accept the default prefix for symbolic links.
   4.

      You can now safely remove the downloaded file from your system. Type

rm RealPlayer10GOLD.bin

   5.

      To run Real Player 10, choose Applications->Sound & Applications->RealPlayer 10. 

This is what I type:
eine@eine:~$  cd /home/eine/Desktop
eine@eine:~/Desktop$ chmod +x Realplayer10GOLD.bin
chmod: cannot access `Realplayer10GOLD.bin': No such file or directory
eine@eine:~/Desktop$ sh RealPlayer10GOLD.bin
RealPlayer10GOLD.bin: RealPlayer10GOLD.bin: cannot execute binary file
eine@eine:~/Desktop$ sudo ./RealPlayerGOLD.bin
sudo: ./RealPlayerGOLD.bin: command not found
eine@eine:~/Desktop$ sudo ./RealPlayer10GOLD.bin
sudo: ./RealPlayer10GOLD.bin: command not found
eine@eine:~/Desktop$ sh RealPlayer10GOLD.bin

But I got to the Desktop!! We are getting closer.. soon I am a linux expert!!!

---

### Post by Pablo_Escobar on 2005-10-31
Where did You download Realplayer10GOLD.bin to ??
What directory ?

---

### Post by SunshineSmile on 2005-10-31
The desktop. It is on the nice ubuntu sandy brown background. Should I put it elsewhere?

---

### Post by AgenT on 2005-10-31
What version of Ubuntu are you using? The newest (Breezy)? If so, read on. If not, read on as well but note that the following was written for Breezy.
[B]
DO NOT USE[/B] the UbuntuGuide! It is outdated and may cause more problems than it solves. It is not meant for the newest version of Ubuntu (as of now).

Before you start, you should **READ THE HELP GUIDE**!! Available here: System -> Help. This will give you information about what you need. Note that you should not merely rely on what others tell you. They can be WRONG and mess up your computer. Understand what they are telling you before you do it. Don't just type in random commands.

Also, about the backports error. You are getting that because the backports are not yet available. Do not use backports unless you know what they are beforehand.

Synaptic is available here: System -> Administration -> Synaptic

Terminal is also available (you DO NOT need to install it - it comes by default): Applications -> Accessories -> Terminal.

Note that when you edit system files and do system administration from the command line (terminal), you will need to use sudo. Again, read about this in the Help file available on your system.

To use a command in the terminal (such as cd or ls), you need to have spaces after it. For example, this is WRONG: ```
cd~
``` This is CORRECT: ```
cd ~
``` The "~" is just a shortcut for your home directory. So if your username is eine, then "~" would be the same thing as "/home/eine/".

Do note that for some applications, you will have to use other repositories (all of which are created by Ubuntu). They are disabled by default. Good place to learn how to do things is in the HowTo (Customization Tips & Tricks) section of the forum and the Wiki.

Also, installing outside of the respositories (such as your RealPlayer), is not a good idea. You see, RealPlayer, for example, is not needed to play real files and you could install a normal player using apt-get or Synaptic (the latter is just a nice graphical front end for the former). Actually, RealPlayer is also available in the repositories so you should use that. It is a bad idea for someone new to install stuff at random and not through apt-get/Synaptic because things will end up breaking for you and you will not know why (especially after upgrades).

Again, READ THE HELP FILE. It is well done. Especially the "Starters Guide". There is a link to in on the first page of the guide.

---

### Post by SunshineSmile on 2005-10-31
Megathanx, that was really helpful.

I found terminal under "applications". Just serves to prove how blind I was/searching at the wrong place.

1) The realone example was to figure out how to do a simple operation as stated in the FAQ. I know there are some files I need Realplayer for, otherwise I prefer VLC. How do I get the proper VLC for my comp using the package manager.

and 2) lol, how do I remove the terminal from the menu where I put it.. (directly under applications...)

Thank you guys for taking so much time helping a complete n00b. I'll check out the how to on this forum, and the wiki once I find out what the wiki is! ;)

---

### Post by AgenT on 2005-10-31
> **SunshineSmile]1) The realone example was to figure out how to do a simple operation as stated in the FAQ. I know there are some files I need Realplayer for, otherwise I prefer VLC. How do I get the proper VLC for my comp using the package manager.[/quote]To get the actual program, search for vlc in Synaptic. The actual package name is... "vlc".  said:**
> and 2) lol, how do I remove the terminal from the menu where I put it.. (directly under applications...) Use the same program you did to add it. Applications -> System Tools -> Menu Editor. Find your entry and delete it (Right click -> Delete). You may have to uncheck it first.

> Thank you guys for taking so much time helping a complete n00b. I'll check out the how to on this forum, and the wiki once I find out what the wiki is! ;) A wiki is like a blackboard. People add/modify/delete entries. The difference is that it can be made up of hundreds of pages, etc. and there is usually some group that oversees the editing so that some fool does not just delete everything out of spite. You can get to the Ubuntu Wiki from any of the official Ubuntu sites (like this forum). The link is at the top right of the page ("Official Wiki").

---

### Post by H.E. Pennypacker on 2006-06-07
> **WTF is the command line?? Where do I find it?**

That has to be the best question to have ever been asked on these forums.  I should make that line my signature, not as a way of ridiculing the orignal poster, but to show, in part, how the command line is so far removed from the average Windows user.  On the other hand, Linux users are so used to it.

I loved the question, and it made me laugh. :)

---

