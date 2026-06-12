---
title: "Compiling pymol 1.4.1 fails in ubuntu 11.04, runs perfectly in 10.10"
date: 2011-05-12
forum: Installation &amp; Upgrades
---

### Post by sirverdemer on 2011-05-12
Hi, everyone!
So, I like to keep my pymol molecular viewer as recent as possible. With svn and compiling it used to be easy, up until ubuntu natty. Now I get the following error every time I try to compile:

layer1/Scene.c: In function ‘SceneClick’:
layer1/Scene.c:4557:11: internal compiler error: in set_jump_prob, at stmt.c:2319
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.5/README.Bugs> for instructions.
error: command 'gcc' failed with exit status 1

This is for EVERY version I have tried. I have even downloaded the source code you can find in the ubuntu repositories (current version for 64 bit is pymol 1.2r2) and tried to compile that one, just as prove of concept. I still get the same error. I think I might need something else beyond what I have already, because if the package maintainers could build the older version for natty, I should be too, with the proper packages, shouldn't I?
That's why I' asking for help, to see if someone has run into the same problem and has found a solution.
Thank you very much!

---

### Post by jocko on 2011-05-15
I had the exact same error. I managed to build it using python 2.6 instead of the default 2.7.
So this is how I build and install it:
```
python2.6 setup.py build
sudo python2.6 setup.py install
sudo python2.6 setup2.py install
```

---

### Post by sirverdemer on 2011-05-15
Hi Joko!
Alreadz tried it, I get the same error... any other ideas?
Thanks!

---

### Post by jocko on 2011-05-15
Weird... There must be something "wrong" with python 2.6 after my upgrade from maverick to natty on my desktop.
I just tried to build pymol on my laptop (fresh install of natty) and it gives the same error even with python 2.6...
Something is probably misconfigured in natty's python, but I have some left-over configuration from maverick...

---

### Post by sirverdemer on 2011-05-15
Hi, that's what I suspected, actually. 
What I am trying to do now, is to reinstall maverick, compile pymol and upgrade to natty. The main problem I'm having is that I'm working on a Samsung series 9. It has an sandy bridge processor with an integrated intel 3000 HD. Now, to obtain full performance for the graphic card, as far as I've read, you need ubuntu natty. But there is a known problem with intel based graphic solutions and stick representation in pymol that was corrected in version 1.4.
Therefore, the only workable configuration for me would be natty+pymol1.4
Ok, will keep on trying stuff, thanks for your input, and please send me any new ideas you might have!

---

### Post by sirverdemer on 2011-05-21
Solved it (sort of)
Luckily for me, I always keep dd images of whatever I do. I had one for my current system in which Maverick was installed. I compiled it in maverick, installed it, upgraded to natty and everything is working like a charm.
Thanks for everything, and I do hope that our friends at Delano Scientific update to python 2.7 soon, because I think that compatibility problems with it are causing the compilation faults.

---

### Post by dexter4096 on 2011-05-22
My experiments:
 for distutils, use gcc-4.4 instead of gcc-4.5.
 for GNU autotools, also correct a reference to ce_types.h in Executive.c in layer3 directory

This seems to work. Please confirm.

---

### Post by sirverdemer on 2011-05-22
Ok, I suppose I can give the python setup.py build command the --compiler=gcc4.4 string, but what do you mean by correct the reference to ce_types.h?
What should I correct it for?
I'm sorry, but even though I've compiled a couple of things, I'm still pretty much a noob in this kind of stuff. Thanks for the explanations!

---

### Post by dexter4096 on 2011-05-22
> I'm sorry, but even though I've compiled a couple of things, I'm still pretty much a noob in this kind of stuff. Thanks for the explanations! 
No problem at all. Probably similar level here. Anyway, these scientific stuff are always buggy in some way. ](*,)

> What do you mean by correct the reference to ce_types.h?
What should I correct it for?  
When I compiled the autotools way, I got an error. I modified a line in the file trunk/pymol/layer3/Executive.c to fix the error, 
#include"ce_types.h" into #include"../modules/cealign/src/ce_types.h". The error does not occured if compiled the distutils way. 

> Ok, I suppose I can give the python setup.py build command the --compiler=gcc4.4 string,
I took a somewhat more dramatic approach. I modified the gcc symbolic link. :twisted:

---

### Post by sirverdemer on 2011-05-22
Ok, now it is officially and fully solved beyond any doubt.

> **dexter4096 said:**
> 
When I compiled the autotools way, I got an error. I modified a line in the file trunk/pymol/layer3/Executive.c to fix the error, 
#include"ce_types.h" into #include"../modules/cealign/src/ce_types.h". The error does not occured if compiled the distutils way. 

I actually did not try to to compile over autotools, I decided to just go for the python compilation with the silly --compiler=gcc-4.4 flag and, of course, python complained that he didn't know what to do with that strange gcc-4.4.
So what I did, was to go for your
 > 
somewhat more dramatic approach.  I also modified the gcc symbolic link to point to gcc-4.4. As a result, everything compiled like a charm and didn't need to change the ce_types.h.
I am now officially the happy owner of an Ubuntu Natty systen running pymol 1.4.1, without needing to go through maverick.  Yei for me!  \\:D/
Thanks a lot, Dexter, next time I think I'll be a little bit more aggresive with the system (although my dd policy will remain) :biggrin:

---

### Post by zengyro on 2011-05-23
So I get a slightly different problem. When I begin to compile using the python setup.py way I get the following:

```
In file included from layer0/Block.c:19:
layer0/os_gl.h:30: fatal error: GL/glew.h: No such file or directory
compilation terminated.
error: command 'gcc' failed with exit status 1
```Presumably its missing a dependency. Any ideas which one and how to resolve it? 

Feel free to speak to me like I am an idiot :)

---

### Post by sirverdemer on 2011-05-23
Hi Zengyro!
Now, I think that your problem is that you don't have the required glew libraries installed. To tell you the truth, when I first started trying to compile pymol, I got the same error. To solve it, I decided to be a little bit unscientific and just install anything "glew" like that I found in the repositories.
Now, since you asked me to explain this in an idiot-proof way, I shall go for a level of simplicity that probably is too simple for you, but that's what you get for underestimating yourself! :)
To do this, just go into synaptic (if you're working with unity, just type the windows key and start writing synaptic... it'll appear. If you're working with classic desktop, just go to System --> administration --> synaptic package manager). Write your administrative password in, and search for "glew". You should get a picture like the screenshot I got in the post, only at least some of your squares should be hollow, instead of green, as with mine. The hollow squares mean you don't have those packages installed. Right click on the hollow squares and select: mark for installation. Then click on Apply, and enjoy the wonders of modern compiling!

---

### Post by jocko on 2011-05-23
I have found a better solution than downgrading to maverick.
I thought maybe the error message about a bug in gcc 4.5 was correct and tried to compile it with gcc 4.4 instead. It works fine with python2.7, so the problem is with gcc 4.5, not python.



This is my complete guide to compile pymol from the latest svn source code in natty (works in a live session, so should work in a fresh install):

1: Enable "universe" repos. Makes it easier to install most of the build dependencies for pymol with one simple command.
Easiest way is to open up synaptic, and make sure "Universe" is active in Settings-->Repositories.

2: Only necessary during the first install:
```
cd ~/
sudo apt-get update
sudo apt-get install subversion build-essential gcc-4.4 g++-4.4 libglew1.5-dev python-pmw
sudo apt-get build-dep pymol

svn co https://pymol.svn.sourceforge.net/svnroot/pymol/trunk ./
```3: Update to latest svn, build and install pymol:
```
cd pymol/
svn up [COLOR=Blue]#not necessary during the first install (source already up to date)[/COLOR]
export CC=/usr/bin/gcc-4.4
python setup.py build
sudo python setup.py install
sudo python setup2.py install
sudo ln -s ~/pymol/pymol /usr/bin/pymol [COLOR=Blue]#only necessary during the first install[/COLOR]
```Hope this was helpful.

---

### Post by sirverdemer on 2011-05-23
Thanks Joko!
Yeah, it appears that the gcc-4.5 compiler is causing the problem. Any idea why this is happening? Do you think it will get smoothed over quickly from delano scientific's side of the problem?

---

### Post by jocko on 2011-05-23
I'm not a programmer, but I'm guessing that the problem is either that they (Schrödinger, who took over pymol from Delano scientific when Warren Delano died) haven't upgraded to gcc-4.5 yet, or there is something wrong with gcc-4.5 in natty.

I found this [bug report in launchpad]("https://bugs.launchpad.net/ubuntu/+source/pymol/+bug/756147") about a failed automatic build of the pymol package during natty development with the exact same error message we get. Weirdly enough the build worked later (with  what I think is a newer version of gcc-4.5 than the one present in the natty repos).
From that I'm guessing the problem is in natty's current gcc-4.5 version, and hopefully it will get fixed...

---

### Post by zengyro on 2011-05-24
Thanks Silverdermer - compiled correctly. I was indeed missing a single package. 

> Now, since you asked me to explain this in an idiot-proof way, I shall  go for a level of simplicity that probably is too simple for you, but  that's what you get for underestimating yourself! :smile:

Yeah i should probably stop doing that :)

Thanks!

---

### Post by rooseal on 2011-07-19
So I'm very new to Linux, so I'm having a hard time trying to install the new pymol in 11.04. 
I tried the previous suggestions and I still haven't been able to get it to work. I tried searching for "glew" in synaptic manager and updated the packages, but when I use "sudo python setup.py install" I get the error: > /usr/include/python2.7/pyconfig.h:1155:0: warning: "_POSIX_C_SOURCE" redefined
/usr/include/features.h:214:0: note: this is the location of the previous definition
layer1/Scene.c: In function ‘SceneRay’:
layer1/Scene.c:6458:9: warning: unused variable ‘volume_layers’
layer1/Scene.c: In function ‘SceneClick’:
layer1/Scene.c:4565:11: internal compiler error: in set_jump_prob, at stmt.c:2319
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.5/README.Bugs> for instructions.
error: command 'gcc' failed with exit status 1
When I try to run the command "sudo apt-get install subversion build-essential gcc-4.4 g++4.4 libglew1.5-dev python-pmw" I get the error:> E: Unable to locate package g++4.4
E: Couldn't find any package by regex 'g++4.4'
I'm assuming because there is a problem with this command, then that is the reason why I still can't build pymol in python because when I use the command: python setup.py build, it outputs the error:> unable to execute /usr/bin/gcc-4.4: No such file or directory error: command '/usr/bin/gcc-4.4' failed with exit status 1

If someone could help me this would be awesome :(

---

### Post by jocko on 2011-07-20
> **rooseal said:**
> So I'm very new to Linux, so I'm having a hard time trying to install the new pymol in 11.04. 
I tried the previous suggestions and I still haven't been able to get it to work. I tried searching for "glew" in synaptic manager and updated the packages, but when I use "sudo python setup.py install" I get the error: 
When I try to run the command "sudo apt-get install subversion build-essential gcc-4.4 g++4.4 libglew1.5-dev python-pmw" I get the error:
I'm assuming because there is a problem with this command, then that is the reason why I still can't build pymol in python because when I use the command: python setup.py build, it outputs the error:

If someone could help me this would be awesome :(
I apparently had a typo in the command (the package name is g++[COLOR=Blue]**-**[/COLOR]4.4, not g++4.4)...
So the correct command is (I fixed it in the original post as well):
```
sudo apt-get install subversion build-essential gcc-4.4 g++-4.4 libglew1.5-dev python-pmw
```

---

### Post by rooseal on 2011-07-20
thanks joko, I think that solved the command, although it I don't think it installs: > build-essential is already the newest version.
g++-4.4 is already the newest version.
gcc-4.4 is already the newest version.
libglew1.5-dev is already the newest version.
python-pmw is already the newest version.
subversion is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic-pae
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
also when I try using  either python setup.py build or sudo python setup.py install, it still gives me the same error as before: > layer1/Scene.c: In function ‘SceneRay’:
layer1/Scene.c:6458:9: warning: unused variable ‘volume_layers’
layer1/Scene.c: In function ‘SceneClick’:
layer1/Scene.c:4565:11: internal compiler error: in set_jump_prob, at stmt.c:2319
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.5/README.Bugs> for instructions.
error: command 'gcc' failed with exit status 1

---

### Post by jocko on 2011-07-20
> **rooseal said:**
> thanks joko, I think that solved the command, although it I don't think it installs: 
also when I try using  either python setup.py build or sudo python setup.py install, it still gives me the same error as before:
Did you do all the steps in my post, in the exact order they are written? From that error, I think you missed that you have to run this command:
```
export CC=/usr/bin/gcc-4.4
```
And you have to run it *before* running the setup scripts and in the same terminal session.

---

### Post by rooseal on 2011-07-20
Thanks joko I've finally installed it. 

I still have one problem though. When I use ./pymol, only the pymol viewer comes up and not the text editor. I don't know if this is still in your expertise and if not, I can try to ask elsewhere.
This is what comes up after ./pymol:

> PyMOL(TM) Molecular Graphics System, Version 1.4.1.
 Copyright (c) Schrodinger, LLC.
 All Rights Reserved.
 
    Created by Warren L. DeLano, Ph.D. 
 
    PyMOL is user-supported open-source software.  Although some versions
    are freely available, PyMOL is not in the public domain.
 
    If PyMOL is helpful in your work or study, then please volunteer 
    support for our ongoing efforts to create open and affordable scientific
    software by purchasing a PyMOL Maintenance and/or Support subscription.

    More information can be found at "http://www.pymol.org".
 
    Enter "help" for a list of commands.
    Enter "help <command-name>" for information on a specific command.

 Hit ESC anytime to toggle between text and graphics.

 Detected OpenGL version 2.0 or greater.  Shaders available.

---

### Post by sirverdemer on 2011-07-23
Hi everybody!
I saw the your question, rooseal, but I have juts really really busy lately, sorry to not have responded earlier...
And thanks Joko for all the kind help you've been providing long the way!

Now, rooseal, one thing I can tell you about the sudo apt-get install command is that you can always replace with a use of synaptic, just open synaptic and look for whatever comes after "sudo apt-get install", in our case g++ and so on. If you're not accostumed to command line, this is an easier way, I think. Either way, remember that you also have auto-complete on command line for apt-get, that is, if your not sure what the package name is called, just start writing it and press tab twice. You will get a list of all packages that start with whatevr you've already written.
Now, as for only getting the text editor... can you post a screenshot, perhaps? I'm not quite sure what you mean with it...
Could it be perhaps that you don't have tcl/tk installed? (just a wild guess). On the install readme for pymol, you can read the following:
> Note that you must have OpenGL, glut, libpng, tcl/tk, python,
freetype2, and Pmw already installed on your system for this to work.
Nowadays, you can typically use the package manager to automatically
download and install the required components

So, you really need to install all that. To do it, just go on synaptic, search for everything called like that and install it. As I said, I think that you might be missing some tcl/tk stuff...
I hope that helps... 

BTW, have you all seen that there is a coot ppa now? Finally! So glad about that!
Well, have fun, and see you!

---

### Post by sirverdemer on 2011-07-23
Just in case it's useful for you, I just made a couple of screenshots where I show every package I have installed for tcl and tk.
I hope it helps.

---

### Post by firebug2 on 2011-08-02
> **sirverdemer said:**
> Hi Zengyro!
  ...I decided to be a little bit unscientific and just install anything "glew" like that I found in the repositories...


It appears that the only thing needed to get past the error is  libglew1.5-dev package (as kinda expected, since the error indicated  that the header files can't be found).

On a different note, I had to edit the setup.py to point at /usr/lib  instead of /usr/X11R6/lib, don't know if this is mentioned in this  thread or elsewhere.

For the sake of full disclosure, I am trying to make a non-systemwide  pymol on Lucid (which already has the pymol from repositories installed,  so I guess at least the runtime dependencies should be satisfied).  Of  course, the reason is to have the latest pymol yet not mess with the  system.

---

### Post by jakobb on 2011-08-23
Strange, 
I just downloaded 1.4.1 from sourceforge, and followed the installation guide. When I launch pymol, it states that it is 1.2r2

Anyone know how this can be?
I use Ubuntu 11.04 64bit on a Lenovo x200

---

### Post by jocko on 2011-08-24
> **jakobb said:**
> Strange, 
I just downloaded 1.4.1 from sourceforge, and followed the installation guide. When I launch pymol, it states that it is 1.2r2

Anyone know how this can be?
I use Ubuntu 11.04 64bit on a Lenovo x200
That's probably because you have installed v. 1.2r2 from the ubuntu repos. Uninstall it:
```
sudo apt-get remove pymol
```
Then install from the source package (or svn repo) again according to [my post]("http://ubuntuforums.org/showpost.php?p=10853579&postcount=13").

---

### Post by jakobb on 2011-08-24
> **jocko said:**
> That's probably because you have installed v. 1.2r2 from the ubuntu repos. Uninstall it:
```
sudo apt-get remove pymol
```
Then install from the source package (or svn repo) again according to [my post]("http://ubuntuforums.org/showpost.php?p=10853579&postcount=13").

BOOM BABY !

thanks for your help, the instruction you made is really good.

---

### Post by jakobb on 2011-08-26
btw, does anyone know how likely it is that we will get a globalmenu integration with pymol?

I mean the menu bar in the second window (The one with terminal on white background)

it would look so smooth on Ubuntu 11.04

---

