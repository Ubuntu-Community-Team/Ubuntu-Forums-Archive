---
title: "Need help installing NDISwrapper"
date: 2007-05-29
forum: Installation &amp; Upgrades
---

### Post by mikledet on 2007-05-29
(Cliff's at the bottom)
System: Dell e1705 laptop, Intel wireless N, nVidia 7900gs
I'll save you all the yada yada yada...  and get to it (and yes, I am a TOTAL newbie to this).
Installed Ubuntu 7.04 (Feisty) in dual boot with vista.  I think installation went well, however, since I have a dell e1705 laptop with wireless N, I realized that my only option to get network access is via NDISwrapper.
I d/l the latest version through a different computer and copied the file to Ubuntu's desk top, then I tried following several tutorial to install NDISwrapper, but non worked..  :(
- I tried through the package manager but it keeps trying to connect to the net (which I don't have..).
- I also tried inserting the Live install cd, and install through that, but that didn't work either.
- Finaly I tried messing around through the terminal window, but... you guessed it, didn't work either.
One of the errors I got through the terminal window were that I don't have enough permissions...?!  I mean I have only one user, and I don't remmember ever being asked (while installing) to set a root user/pass, so unless my user is with root priveleges, then I don't know how to get permissions.
Can anyone help with a simple step by step guide to solve this issue?

Again, though I followed various methods, I'm sure I'm doing something wrong, though I'm not sure what exactly yet..

still to come from this n00b:
If I'll get NDISwrapper then I'll need help installing the wireless N driver itself, and then the 7900 gs graphics driver, and then the beryl, but I'll try following tut's before bothering you again.

Cliff's:

- n00b, Ubuntu 7.04, NO wireless, No graphics
- d/l latest version of NDISwrapper & placed it on Ubuntu's (Feisty) desktop.
- didn't manage to install.
- need a simple step by step guide.

---

### Post by Yoeri on 2007-05-29
EDIT: sorry for the wrong answer, I didn't noticed you don't have internet access...

Have you tried installing NDisWrapper via Automatix?

A very easy way to install it...

you can find the debian package for feisty here:
[http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.04_.28Feisty_i386.29](http://www.getautomatix.com/wiki/index.php?title=Installation#Ubuntu_7.04_.28Feisty_i386.29)

just dblclick the package to install.

Afterwards you can start automatix via Programs > System Tools (correct me if i am wrong).
Under the drivers section, you can select NDiswrapper an click apply to install

---

### Post by mikledet on 2007-05-29
Let me try and translate what you said to n00b language and tell me if I got it right:
1. I d/l automatix via some other computer with network.
2. I copy the automatix installation to my Ubuntu desktop.
3. I double click the file --> it installs itself.  (now I have automatix installed...?)
4. I do the Programs > System Tools thing, I go to drivers, and there should be NDISwrapper there?  (that come with automatix? or one I need to d/l?)
5. I click on the NDISwrapper, and it should install it..

Hope that's correct.  Anyway, what about the privelleges problem?  Is my default user (the one I created during Ubuntu install) a one with /root permissions or do I need to change to root somehow (if so please advice how..)

Thanks

---

### Post by mi_were on 2007-05-29
I for one like using the script produced by synatpic (no reason just the first thing that I learnt!)

1. select the packages you want to install in synaptic
2. click on "file" then "generate package download script".
3. transfer the script that has been created to a computer that has internet connectivity and run it ( if it is a windows machine edit the script file and comment the first line - put "#" at the beginning)
4 transfer the packages downloaded back to the linux box (hopefully in a folder) then in synaptic click on "file" and then "add downloaded packages" and the apply as usual

long process but effective.

---

### Post by mikledet on 2007-05-30
Now I managed to get ndiswrapper-utils and ndiswrapper-common to show up in synaptic manager after downloading and installing them manually, also I have the actually installation file of ndiswrapper-1.45 on my desktop.  How do I continue installation from here?  I tried something that had to do with sudo make and sudo make install but for some reason I got errors, so it failed.  Help...

---

### Post by jman82s on 2007-05-30
Ugh, I feel for you, dude.

The most vivid memory I have starting out with Linux was getting my wireless card to work via ndiswrapper. 

On Ubuntu, I recall having difficulties using  the source package (which is what you have if you need to "make" and "make install". Scince you don't have net access, I would suggest going to [packages.ubuntu.com]("packages.ubuntu.com"). Do a searh for "ndiswrapper," and save ndiswrapper-common and ndiswrapper-utils to cd or a flash drive (if you have one). Simply click on the .deb files to install. 

Then go to a termial and type:

     sudo ndiswrapper 

If you see some usage options, then the installation was successful, if you see "command not found," then there was a problem with the installation.

Once you get it installed properly, follow through with normal instructions; I found this guide useful:

[http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318](http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318)

Good luck!

---

### Post by irpotential on 2007-05-31
If you have the same new Intel pro wireless card a friend of mine just got (4965AGN) you need to use ndiswrapper 1.45 but the ubuntu package is 1.3 somthing.  we followed ndiswrappers instructions (make uninstall several times, make clean, make) but the make failed with some errors that looked like it couldn't find some gcc libraries (stdlib.h was one i belive).  how would you work around this problem?  we found the appropriate driver but apparently versions below 1.45 dont install the card properly and the script was fixed in 1.45.

thanks and hope this helps the n00b out a bit

---

### Post by pavkb on 2007-06-06
I am trying to do this with edubuntu. Hope the mechanism is same.

First planning to try with AutoMatix suggestion.
Been browsing through packages.ubuntu.com, where would find the ndiswrapper related packages, which section.

When i search there ndiswrapper, i seem to get the source packages.

I am trying to get my DLINK DWL-G132 wifi USB device to work.
Thanks

---

