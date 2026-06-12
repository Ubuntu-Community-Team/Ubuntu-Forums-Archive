---
title: "how I installed Cinelerra After a clean install of Fiesty"
date: 2007-06-04
forum: Installation &amp; Upgrades
---

### Post by kelvin spratt on 2007-06-04
How I Installed Cinelerra in fiesty after a clean install 
Install Cinelerra before you start installing any other multimedia software if possible. Do not download the Fiesty version of Cinelerra as it does not work
the author tells you he has not tested it as he does not have Fiesty on his computer but thinks it should work? well not on my computer!
 1, terminal, sudo gedit /etc/apt/sources.list  2,IMPORTANTadd a space between deb http and paste these two entries to the end of the list.
debhttp://www.kiberpipa.org/~gandalf/ubuntu/dapper/mjpegtools./                  
debhttp://www.kiberpipa.org/~gandalf/ubuntu/dapper/cinelerra/i686/ ./  
          
3, press save then close. 4, in terminal paste sudo apt-get update  5, 
sudo apt-get install cinelerra  5, reboot, Cinelerra in all its glory on my computer.
if you tried to install Cinelerra using the Fiesty version see my other post
How I installed Cinelerra in Fiesty

---

### Post by Dread Knight on 2007-06-16
It finally worked! Thanks!
I'm a bit disappointed by the application, anyway I'll have a closer look soon.
It's the latest version? And if it's not, are there any major changes in the latest one (like the GUI) ?

Thanks again!

---

### Post by blakegrover on 2007-06-18
It looks like it installs 2.0 but the latest is 2.1, I am not sure what the differences are.

Blake

---

### Post by blakegrover on 2007-06-18
I found out that if you have feisty this is the repository you need to add to /etc/apt/sources.list:

> 
    1. Make sure you have universe, multiverse and restricted repositories enabled
    2. Add the following repository to your sources.list file, according to your CPU type:

    - i686:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./
    - athlonxp:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/athlonxp/) ./
    - pentium4:
    deb [http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/pentium4/) ./

    3. apt-get update ; apt-get install cinelerra 

[http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu](http://cvs.cinelerra.org/getting_cinelerra.php#ubuntu) This will give you the latest 2.1 Cinelerra

Blake

---

### Post by blakegrover on 2007-06-18
You will notic ewhen you run it, it will say to run a certain command before you run cinelerra, so I mad a script that will run the command as root and then run cinelerra:

```
#!/bin/bash

gksudo echo '0x7fffffff' > /proc/sys/kernel/shmmax

cinelerra

```

Make sure to stick this file in /usr/local/bin/ and make sure it is executable.  It works great for me on 3 computers.

Blake

---

### Post by kelvin spratt on 2007-06-19
The reason for using the version i use is simply the latest version does not load raw mov files from my SD card
this version does its not a UBUNTU problem its the same with Debian, PcLinux, Elive, ETC the ealier version is the best one to use

---

### Post by tubunu on 2007-06-28
Version 2.0 works fine, but I can't get it to render my .mov files to .avi (rendered files don't play) so I edited the sources.list to include the latest 2.1 version. Now Cinelerra refuses to launch, in Konsole the error is shown as: 

```
cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen 
```

Somewhere in another thread I read about the faac being buggy and the need to downgrade it. Would anyone know how to do that? Thank you.

---

### Post by tubunu on 2007-06-29
I did but no joy... :(

---

### Post by efreddi on 2007-07-04
This is the way I made cinelerra to run on my laptop after many unsuccessfull trails.

At this page

[INDENT][http://cvs.cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_2.html]("http://cvs.cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_2.html")
[/INDENT]
I found this repository:

[INDENT]***deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./***[/INDENT]

that I added in my repositories list. Then I installed cinelerra using Synaptic.
Cinelerra started giving the error message regarding *shmmax*. This should be the amount of memory shared between process by the kernel. After some work with google I found an easy solution - in the terminal I gave:

[INDENT]**sudo gedit /etc/sysctl.conf**[/INDENT]

and at the end of this file I added the line

[INDENT]***kernel/shmmax=0x7fffffff***[/INDENT]

I saved the file and I made

[INDENT]**sudo sysctl -p**[/INDENT]

Now cinelerra run fine.
It's a very powerfull software, it's worth some troubble.
Ciao


Elia

---

### Post by silvagroup on 2007-07-10
Thanks efreddi, followed your directions and cinelerra is running on my amd 64 x2.
I used deb [http://giss.tv/~vale/ubuntu64](http://giss.tv/~vale/ubuntu64) ./ instead. Same error message, but your fix took care of that.
Now to play with it and see how ell it works. :popcorn:

---

### Post by zhinker on 2007-07-15
> **blakegrover said:**
> You will notic ewhen you run it, it will say to run a certain command before you run cinelerra, so I mad a script that will run the command as root and then run cinelerra:

```
#!/bin/bash

gksudo echo '0x7fffffff' > /proc/sys/kernel/shmmax

cinelerra

```

Make sure to stick this file in /usr/local/bin/ and make sure it is executable.  It works great for me on 3 computers.

Blake
THANK YOU!!!  I couldn't figure out how to solve this error anywhere

---

### Post by Sabot on 2007-07-15
Open Synaptic

On the menu bar select Settings>Repositories
Click the Third-Party Software Tab
Click the Add button
Enter the repository below:
```
deb http://giss.tv/~vale/ubuntu32 ./
```

Close the software sources window and reload your repositories by clicking on the reload button.
Search for Cinelerra by using the search button in Synaptic  and install it.

Cinelerra needs a little extra memory to run in the Kernel.  To add this extra memory you need to edit a file.

Open a terminal and enter the commands below:

```
sudo gedit /etc/sysctl.conf
```

and at the bottom of this text file add the line:

```
kernel/shmmax=0x7fffffff
```

Restart your computer for this new Kernel setting to take effect.

You will find Cinelerra under Applications>Sound & video>Cinelerra.

Now you are ready to enjoy Cinelerra!

One quick note on how I use Cinelerra.  I import using kino from my camcorder. Then I open the dv files with Cinelerra.  After I have made my edits, I render to a raw dv file in Cinelerra.  Kino is used to open and put the video back on my camera. If I want to export to an mpeg file, I use the export feature in Kino.

---

### Post by kelvin spratt on 2007-07-20
Sabot
         Thats the reason i use version 2 not 2.1 i import raw files direct into Cinelerra, saving time and better resolution and quality, version 2.1 the latest does not import raw files from my Sanyo  for some reason its not Cinelerra but the sound codecs that are at fault but the dapper version is fine then i author with DeVeDe the jobs done i do weddings family parties etc.with excellent results. I had similar probs in Xp and ended up using Sony Vegas but its slow but is the industry standard Cinelerra is very close on Quality but does lack some of the effects.

---

### Post by tubunu on 2007-07-21
Followed this thread up to this point. Now what to do about this problem? I can't get past it to run Cinelerra... 

```
user@feisty704:~$ cinelerra
cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen
```

---

### Post by Sabot on 2007-07-21
> **tubunu said:**
> Followed this thread up to this point. Now what to do about this problem? I can't get past it to run Cinelerra... 

```
user@feisty704:~$ cinelerra
cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen
```

I think you have mixed repositories.  You need a libfaad2-0 file from Ubuntu repositories and then just the one additional repository for Cinelerra.

---

### Post by tubunu on 2007-07-22
```

~$ sudo apt-get install libfaad2-0
libfaad2-0 is already the newest version.
libfaad2-0 set to manual installed.
```

one cinelerra entrance in sources.list:
```

## CINELERRA REPOSITORY
deb http://giss.tv/~vale/ubuntu32 ./
```

:confused:

---

### Post by Sabot on 2007-07-22
> **tubunu said:**
> ```

~$ sudo apt-get install libfaad2-0
libfaad2-0 is already the newest version.
libfaad2-0 set to manual installed.
```

one cinelerra entrance in sources.list:
```

## CINELERRA REPOSITORY
deb http://giss.tv/~vale/ubuntu32 ./
```

:confused:

If you look at my above post on how to install Cinelerra you will notice that you have the wrong repository.  It should be:

```
deb http://www.kiberpipa.org/~muzzol/cinelerra/feisty-i386/ ./
```

Remove the other one and try the newer one made for feisty.

---

### Post by tubunu on 2007-07-24
Yup, I did so and here's the outcome:
```

tubunu@feisty704:~$ sudo apt-get install cinelerra
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cinelerra: Depends: libquicktimehv (= 2.1.0+svn20070109-0ubuntu1) but 1:2.1.0-2svn20070221 is to be installed
             Depends: libmpeg3hv (= 2.1.0+svn20070109-0ubuntu1) but 1:2.1.0-2svn20070221 is to be installed
E: Broken packages
```

and when I hit libquicktimehv or libmpeg3hv it tells me these are already the newest versions...

---

### Post by kelvin spratt on 2007-07-24
read this it explains how i installed Feisty after trying to install the other version
[http://ubuntuforums.org/showthread.php?t=463275](http://ubuntuforums.org/showthread.php?t=463275)

---

### Post by tubunu on 2007-07-26
Thanks **kelvin spratt**, I managed to install cinelerra BUT it's version 2.0 and I was hoping to get *version 2.1* running on my system. :( V2.0 doesn't render properly into avi format for me and V2.1 has no such issues. So I'm still puzzled... :confused:

Hopefully I will be able to install cinelerra 2.1 under gutsy...

---

### Post by kelvin spratt on 2007-07-26
I know what you mean but 2.0 does not have any issues loading files, 2.1 has a bad issue with audio a really bad issue it won't load mov divx or mp4 any thing with mp3 sound etc on my computer, i have both versions and at the end of the day 2.1 is so limited on what you can load and 2.0 renders quicklime for Linux MP4 with super quality that play with all players and authors direct to DeVeDe,  i do weddings videos version 2.0 loads straight from my SD. card.2.1 won't load the sound it does not accept files done in avidmux only Kino. Version 2.0 accepts them all and good quality mp4 is as good a quality as DVD, so you make the choice Something that woks or something ithat looks good

---

### Post by tubunu on 2007-07-27
While still on Edgy I managed to import mov files into cinelerra 2.1, edit them and make a nice DVD (out of rendered avi files), so it might be that your configuration is at fault. :confused: 
Anyway, I'm going to try to work with version 2.0 for the time being...

---

### Post by kelvin spratt on 2007-07-27
Unfortunatly its not its the codecs that are wrong in the latest version ive tried it with Pclinux,Elive Gem, Suze 
and Gentoo, the dependencies to the codecs are wrong, and the forum is like +++++++ against the wall when you file a bug. install a old version its perfect on all of them even the older 2.1 was ok. but they did something to it and it updaded the codecs and that was that.

---

### Post by dennus on 2007-07-28
I have tried entering the code in a terminal, and this is what I get;

```
gksudo echo '0x7fffffff' > /proc/sys/kernel/shmmax
bash: /proc/sys/kernel/shmmax: Permission denied
```

Does anyone know what to do now?

---

### Post by codypumper on 2007-07-28
Thanks efreddi! So glad to get this working!

---

### Post by ArtInvent on 2007-08-01
> **tubunu said:**
> Now Cinelerra refuses to launch, in Konsole the error is shown as: 

```
cinelerra: symbol lookup error: /usr/lib/libquicktimehv-1.6.0.so.1: undefined symbol: faacDecOpen 
```

Somewhere in another thread I read about the faac being buggy and the need to downgrade it. Would anyone know how to do that? Thank you.

I had Cinelerra 2.1 going very nicely until yesterday. I added a new repo to get some other packages going, and then updated my system as well. Later that day, Cinelerra crashed and would not start again. I got the same error as reported above. 

As far as I know, the solution to this error has not been posted. The fix was indicated on another thread, but not explicitly. I mucked around on this forum quite a bit, uninstalled and re-installed Cinelerra from different repos, no luck. The way I finally solved it was simple of course, it generally is - 
[LIST=1]
[*]start Synaptic (gui version)
[*]find the package called libfaad2-0 and highlight it.
[*]menu: Package | Force version
[*]I had two versions to choose from, I chose the one called** 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3**.  It will warn you that it's not advised etc. Go ahead and do it anyway.
[*]When it is finished, I restart Cinelerra and am back in business.
[*]Make sure you do not allow upgrades to this package in the future. The package will be highlighted yellow in Synaptic, indicating that it can be upgraded. Leave it alone.
[/LIST]
 
Maybe this will cause problems with other apps that depend on it, not sure yet. Like I said, everything worked until yesterday. YMMV.

If you do not have these versions to choose from, you may be using different repos. Here is the repo I am using for Cinelerra 2.1 - 
[LIST]
[*][http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/](http://www.kiberpipa.org/~gandalf/ubuntu/feisty/cinelerra/i686/) ./
[/LIST]
The offending repo that I have since disabled is 
[LIST]
[*][http://repoubuntusoftware.info/](http://repoubuntusoftware.info/) feisty all
[/LIST]
This is what triggered the 'upgrade' that screwed everything up. I was trying to install a video package called ProjectX that is in this repo. Well, ProjectX won't run and it screwed up Cinelerra. Bad trade. I disabled the repo in Synaptic and now libfaad2-0 shows being up-to-date. So another way to solve this problem is to make sure the offending repo is deleted or disabled, uninstall libfaad2-0, then reinstall it. Hope this helps someone.

Cinelerra is a powerful app. It's about the only thing that can edit HD video on linux, so we all need to work on getting it going, solving it's quirks, improving it. It is truly a nightmare of dependencies, and is also really picky about the kind of video files you try and feed it. But once you find the formats that work, it's quite a decent editor. Hopefully the powers that be are working on it so that it can become an officially supported and maintained Ubuntu package without conflicting dependencies.

---

### Post by kelvin spratt on 2007-08-02
You need to go into Synaptic highlight the package then click package left hand top on the dropdown menu click lock package this will stop that package from being upgraded. this is a problem with useing feisty or any of this type of Distro things are not tested as they are in Debian thats why Debian is always far behind with software but everything works,

---

### Post by ArtInvent on 2007-08-02
> **kelvin spratt said:**
> You need to go into Synaptic highlight the package then click package left hand top on the dropdown menu click lock package this will stop that package from being upgraded. this is a problem with useing feisty or any of this type of Distro things are not tested as they are in Debian thats why Debian is always far behind with software but everything works,

That's a useful thing to know. Thanks Kelvin. I probably ought to just mark that on everything to do with Cinelerra.

Debian vs Ubuntu is a catch-22. Use Debian, you're fairly sure that everything that can be installed on it will work. The trouble is, the latest versions of apps just shouldn't be installed on it. But the latest version might actually be *more* stable because bugs have been fixed. Also, a lot of Linux software I like and need the most is just not that mature and the latest versions add features and functionality that make it far more useful. Media creation and most especially VIDEO software on Linux is fairly behind the curve. 

Hey, I even get impatient with Ubuntu's latest release - the latest app version not being in the repos for weeks. Grr.

---

### Post by kelvin spratt on 2007-08-02
I totaly agree with you DeVeDe is a good example the latest version 3.0 now add menu which is a good step forward I use Feisty with Cinelerra 2.0  So i can import from my SD. card, and I use Elive Gem which is Debian etch. with Cinelerra 2.1 but the latest is not as good as v2.0 for importing and as i only import from SD cards 2.1 is really lacking for me its going backwards my SD cards hold 4GB that covers 1 wedding i don't want to have to convert it then Edit it when v2.0 does the lot.

---

### Post by tipdrinker on 2007-08-11
i tried to install it but got this error:

kev@ubuntu:~$ sudo apt-get install cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cinelerra: Depends: libquicktimehv (>= 1:2.0.0) but it is not going to be installed
             Depends: libquicktimehv (= 1:2.0.0-1svn20060611.1) but it is not going to be installed
E: Broken packages

I looked up libquicktimehv in the package manager but it says its not installed! Im not sure what to do :confused:

---

### Post by kelvin spratt on 2007-08-12
Try Synaptic type Cinelerra in search then see what it brings up also the libquicktimehv if their are any thing to do with Cinelerra completely uninstall them the two packages that i use contain all the dependenciesthat are required for Feisty, and Dapper, but you must use those packages.Also if you have tried to install different packages all Traces must be removed to ensure the ones i use are installed correctly it is worth spending  time on this project as 
Cinelerra works flawless for me and has never crashed.this i just another thought in Synaptic click on custom filters and then broken and completely remove any broken packages  also if you have already tried to install a different version
read this [http://ubuntuforums.org/showthread.php?t=463275](http://ubuntuforums.org/showthread.php?t=463275)

---

### Post by tipdrinker on 2007-08-13
Theyre all not installed, but when i tried right clicking and installing libquicktimehv and libquicktimehv-dev i get this error message:

libquicktimehv:
  Depends: libfaac0 (>=1.24+cvs20060416) but 1.24clean-0ubuntu4 is to be installed
  Depends: libfaad2-0 (>=2.0.0+cvs20060416) but 2.0.0+cvs20040908+mp4v2+bmp-0ubuntu3 is to be installed

is ther somethin missing on my installation of ubuntu i need?

---

### Post by kelvin spratt on 2007-08-13
I suggest you uninstall every thing to do with cinelerra including jmegtools and start again the dependecies that will not install because different versions are installed, you need to remove them before you can install the correct ones and i did that in synaptic, to make it easy. but you can use the terminal to force them to install but i do not know the code to do that, my method worked very well for me thats all i can say.

---

### Post by kelvin spratt on 2007-08-13
Also make sure you have both the repositories enabled and the ubuntu main as well i have used this method on a dozen or so installations with no problems.

---

### Post by JohnCraickkciarc on 2007-08-29
> **efreddi said:**
> This is the way I made cinelerra to run on my laptop after many unsuccessfull trails.

At this page

[INDENT][http://cvs.cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_2.html]("http://cvs.cinelerra.org/docs/split_manual_en/cinelerra_cv_manual_en_2.html")
[/INDENT]
I found this repository:

[INDENT]***deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) ./***[/INDENT]

etc etc ...

Elia

Thanks everyone, esp. effredi. I tried lots of things from here but eventually the version at giss.tv installed straightforwardly on my system and the kernel memory fix removed the error message which most people seem to get.

Cinelerra now runs fine : now to get my head around it & get some work done with it !  

The giss.tv version seems preferable to those at kiberpipa.org which I also tried. Perhaps I was lucky : there was no need to chase down broken dependencies - which is a lot of effort & best avoided if possible. A little sad that the version in the current Ubuntu repositories is so broken.

Again,  thanks.

JohnC

---

### Post by carlinuxlearner on 2007-09-06
Thanks a million! I tried about 10 different ways before I found this. I works great!

C@RL

---

