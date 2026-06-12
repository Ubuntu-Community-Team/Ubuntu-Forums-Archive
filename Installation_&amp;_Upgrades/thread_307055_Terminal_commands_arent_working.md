---
title: "Terminal commands arent working"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by Rmag37 on 2006-11-26
I am using Linux x86 Ubuntu 6.10
I've just spent the last hour trying to install Wesnoth 1.1.12 from a download because the add/remove programs one is 1.0.8 and i need 1.1.12 to play it online. But i cant get it to work, i have it downloaded and im following the steps to install it [http://www.wesnoth.org/wiki/WesnothBinariesLinux#Ubuntu](http://www.wesnoth.org/wiki/WesnothBinariesLinux#Ubuntu)
I do the cd /usr/src step but when i get to   tar -xvzf wesnoth-1.x.x.tar.gz    
   it tells me there is no such file or directory, yes i am changing 1.x.x to 1.1.12 to reflect the actual name of the file, the file is sitting right on my desktop and i cant do it. My terminal reads

luke@luke-desktop:~$ cd /usr/src
luke@luke-desktop:/usr/src$ tar -xvzf wesnoth-1.1.12.tar.gz
tar: wesnoth-1.1.12.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
luke@luke-desktop:/usr/src$ 
luke@luke-desktop:/usr/src$ 


Again, i am 100% sure that both the tar.gz file and the extracted file are sitting on my desktop. 
I'm almost certain i screwed something up because i just started using Linux Ubuntu 6.10 about.... 6 pm my time last night, some 30 hours ago.
I would appreciate any help you can offer, thank you in advance.

---

### Post by taurus on 2006-11-26
When you download something, it is in ~/Desktop, not /usr/src unless you move it there after it's finished downloading!  Therefore, try

```
cd ~/Desktop
tar xvzf wesnoth-1.1.12.tar.gz
```

---

### Post by po0f on 2006-11-26
Rmag37,

tar's -f parameter takes as an argument the tar file, including it's path if you aren't in the directory it resides in; try:
```
$ **cd /usr/src**
$ **tar -xvzf ~/Desktop/wesnoth-1.1.12.tar.gz**
$ **cd wesnoth-1.1.12**
```

---

### Post by Rmag37 on 2006-11-26
Cool ill try those, see i told you i screwed it up =P.

---

### Post by taurus on 2006-11-26
> **po0f said:**
> Rmag37,

tar's -f parameter takes as an argument the tar file, including it's path if you aren't in the directory it resides in; try:
```
$ **cd /usr/src**
$ **tar -xvzf ~/Desktop/wesnoth-1.1.12.tar.gz**
$ **cd wesnoth-1.1.12**
```
The above won't work because you need to be root to write to /usr/src!!!  Therefore, you need to run at least the second command with sudo...  And by the way, you don't have to unpack it in /usr/src.  Just unpack it anywhere you want and build it from there!

---

### Post by Rmag37 on 2006-11-26
Hmm closer i am now to the   make   step  
luke@luke-desktop:~/Desktop/wesnoth-1.1.12$ make
make: *** No targets specified and no makefile found.  Stop.
luke@luke-desktop:~/Desktop/wesnoth-1.1.12$ 

Now i did something else wrong =\ any fixes for this?

---

### Post by wastrel on 2006-11-26
You probably forgot the ./configure step (check the instructions again.)

---

### Post by taurus on 2006-11-26
You probably need to run the "./configure" first before you run "make" & "make install"!  And before you can build anything from source, you need to install build-essential package first...

```
sudo aptitude update
sudo aptitude install build-essential checkinstall
./configure
make
sudo make checkinstall
```

---

### Post by Rmag37 on 2006-11-26
I did remember the ./config step, i retried the hole procceses 5 or 6 more times and wheni  get to the ./configure step on the build essential program thing i get this (last 15 or so lines of terminal)

luke@luke-desktop:~$ sudo aptitude install build-essential checkinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up clamav-base (0.88.4-1ubuntu2) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up clamav-base (0.88.4-1ubuntu2) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base
luke@luke-desktop:~$ ./configure
bash: ./configure: No such file or directory
luke@luke-desktop:~$

---

### Post by taurus on 2006-11-26
First, remove the clamav antivirus thing because you don't need it!!!

Second, you need to be in ~/Desktop/wesnoth-1.1.12 before you can run the ./configure command, okay...

```
cd ~/Desktop/wesnoth-1.1.12
./configure
make 
sudo make checkinstall
```

---

### Post by Rmag37 on 2006-11-26
luke@luke-desktop:~$ cd ~/Desktop/wesnoth-1.1.12
luke@luke-desktop:~/Desktop/wesnoth-1.1.12$ ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
...)
...}  About 10-20 more lines of checking
...)
checking how to run the C preprocessor... gcc -E
checking for X... no
checking for XOpenDisplay in -lX11... no
checking for sdl-config... no
checking for sdl11-config... no
configure: error: *** SDL not found! Get SDL from [www.libsdl.org](www.libsdl.org).
If you already installed it, check it's in the path. If problem remains,
please send a mail to the address that appears in ./configure --version
indicating your platform, the version of configure script and the problem.
luke@luke-desktop:~/Desktop/wesnoth-1.1.12$ make
make: *** No targets specified and no makefile found.  Stop.


From what i can tell at the 6th line "SDL" wasnt working or something, no clue here basically i dont know what any of it means, but basically the ./configure didnt work and niether did make =(
Also i removed Clamav, why did you want me to remove the anti-virus program?

---

### Post by taurus on 2006-11-26
It means that you need to fire up synaptic and look for the development package for sdl!  That's the beauty of building something from source.  You need to have all the dependencies on your system first before you can build it.  And if "./configure" returns with an error, don't even think about running "make" because you will get an error with it as well, wasting time.

For all the years that I've used Linux, never once I get any virus on my machines!!!  So, it's up to you whether you want to install it or not but from my experience, you don't need it...

---

### Post by Rmag37 on 2006-11-26
You know a hell of a lot more about Linux than i do by the looks of things so i'll take your word and not get an AV program, also i looked for SDL in synaptic and all i got was some "SDLJump" and "SDLJump-data" both of which are apparently part of a game where you jump up a tower... i also tried to download it from the SDL website but i got a file that wasnt supported "SDL-1.2.11-1.i386.rpm".

---

### Post by wastrel on 2006-11-26
sudo apt-get build-dep wesnoth 

should get you all the development libraries you need.

---

### Post by Rmag37 on 2006-11-26
=( not a valid source package, i also tried "wesnoth-1.1.12".

---

### Post by wastrel on 2006-11-26
sudo apt-get build-dep wesnoth

worked for me...  I'm using Edgy (6.10).  Should work for Dapper too, as long as there's a wesnoth package... ?  You have to have the universe repository enabled, of course.

---

### Post by Rmag37 on 2006-11-26
1. I have 6.10(edgy)
2. How do i enable the universe repository?

---

### Post by taurus on 2006-11-26
> **Rmag37 said:**
> 
2. How do i enable the universe repository?
Remove the # sign in front of all the lines with universe & multiverse in /etc/apt/sources.list...

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
```

---

### Post by Rmag37 on 2006-11-26
luke@luke-desktop:~$ gksudo gedit /etc/apt/sources.list

(gedit:10351): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Agh, maybe i should just go to sleep its 1:00 here.

---

### Post by taurus on 2006-11-26
> **Rmag37 said:**
> luke@luke-desktop:~$ gksudo gedit /etc/apt/sources.list

(gedit:10351): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Agh, maybe i should just go to sleep its 1:00 here.
But does the window open?  Otherwise, just use a basic text editor then...

```
sudo nano -Bw /etc/apt/sources.list
```

---

### Post by Rmag37 on 2006-11-26
Does what window open? Also the sudo nano -Bw /etc/apt/sources.list gave me a wierd popup window if thats what your talking about

  GNU nano 1.3.12          File: /etc/apt/sources.list                Modified  

v
^v

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
              [ line 3/50 (6%), col 1/1 (100%), char 5/2263 (0%) ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

Does this make sense to you?

---

### Post by taurus on 2006-11-26
> **Rmag37 said:**
> Does what window open? Also the sudo nano -Bw /etc/apt/sources.list gave me a wierd popup window if thats what your talking about

  GNU nano 1.3.12          File: /etc/apt/sources.list                Modified  

v
^v

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
              [ line 3/50 (6%), col 1/1 (100%), char 5/2263 (0%) ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

Does this make sense to you?


Yes...  You see the last two rolls at the bottom.  They are the commands that you can use while in nano.  ^X means hold down the <Ctrl> while hitting x.  ^V means if you want to go to the next page, then hold down <Ctrl> while hitting v...

---

### Post by Rmag37 on 2006-11-26
I dont understand it at all, i flipped through the pages and it was all the same link followed by gibberish "sentences".
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe mu$

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe mult$

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe mul$

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END


Can you make any sense of this?

---

### Post by Rmag37 on 2006-11-26
CRAP i screwed up the add/remove programs thing!!
"[SIZE="6"]Failed to check for installed and available programs[/SIZE]

This is a major failure of your software management system.
Check the file permissions and correctness of the file '/etc/apt/ sources.list' and reload the software information: 'sudo apt-get update'."

I didnt make a new thread because it looks like its related to that nano command you had me do. 

luke@luke-desktop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
luke@luke-desktop:~$ sudo apt-get update
Password:
E: Type 'v' is not known on line 1 in source list /etc/apt/sources.list
luke@luke-desktop:~$ 

Before you ask, I am the root account in fact I'm the ONLY account. So can anybody help with this? This seems pretty serious.

---

### Post by taurus on 2006-11-26
Are you trying to edit your /etc/apt/sources.list again?  My original question for you is what happens when you run this command from a prompt?  Do you see an editing window comes up?

```
gksudo gedit /etc/apt/sources.list
```

---

### Post by Rmag37 on 2006-11-26
When i input that i get:
luke@luke-desktop:~$ gksudo gedit /etc/apt/sources.list
(gedit:6001): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

Than a window pops up labeled "sources.list(/etc/apt) - gedit" is this what you were asking?

---

### Post by taurus on 2006-11-26
Finally...  That is your GUI text editor.  Now, you can modify your /etc/apt/sources.list and make sure you save it before you close it.

---

### Post by Rmag37 on 2006-11-26
Will this fix my add/remove programs problem? Also, how do i do it?

---

### Post by taurus on 2006-11-26
> **Rmag37 said:**
> Will this fix my add/remove programs problem? Also, how do i do it?
Maybe.  Just try to fix your /etc/apt/sources.list first and hopefully, it will cure other problems on your machine as well...

---

### Post by Rmag37 on 2006-11-26
How do i fix it? The    /etc/apt/sources.list    command isn't working it gives me:
luke@luke-desktop:~$ /etc/apt/sources.list
bash: /etc/apt/sources.list: Permission denied
luke@luke-desktop:~$ 

so thats another problem =(, i went from not being able to play Wesnoth online to not being able to install anything.

Edit: Ok now the synaptic thing isnt working either.
Edit2: Neither is the update manager. I think i screwed something up bad.

---

### Post by taurus on 2006-11-26
Maybe you want to start with a new list so here is one that you can use...

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---

### Post by Rmag37 on 2006-11-26
Cool ill try that, i just hope it doesnt screw me up worse XD

---

### Post by Rmag37 on 2006-11-26
Well so far, Add/Remove Applications and Synaptic Package Manager are both working again, However i still don't have the game working when i get to the make step it screws up.

---

### Post by taurus on 2006-11-26
Well, I got your system back to normal again so just have to wait for somebody to help you with your game then...

---

### Post by Rmag37 on 2006-11-26
Well thanks anyway, lol looks like im back where i started, anybody know how to fix this?

---

### Post by Rmag37 on 2006-11-27
Cool i got it working, I turned of the computer and when i fired it up this morning and decided to try again it worked flawlessly, no errors or anything.

---

