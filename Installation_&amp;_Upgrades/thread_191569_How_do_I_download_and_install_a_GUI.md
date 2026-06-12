---
title: "How do I download and install a GUI?"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by Left Face Down on 2006-06-07
Alright, Ubuntu has been really gay to me. Every instructional thing I can find says Ubuntu auto-installs Gnome, Kubuntu KDE, and Xubuntu the third one I'll never remember... XFSN? 


Anyways, moving on, when I install Ubuntu I get a command prompt. I can log in using my account through the command prompt, but with my past experiences using Arch Linux and Gentoo the only command that works in Ubuntu is the command to shut down the computer/restart it. 


When I installed using the x86 install CD it just restarted itself over and over, and I got help here and was told to use the Alternative CD. So I have and I have installed the "server" because the first CD, one that caused the system just to reboot over and over, was labeled a server CD so I figured installing a server is the correct way to go. Should I have installed the OEM or Text version instead?


So how do I download and install Gnome for Ubuntu? If it's there, how do I get it to work because I had to install it for Gentoo and all the commands to start it that I know aren't working and I realise the two systems are in two different languages, Ubuntu Debian and Gentoo Python, so I figure that's why nothing I know is working. 


I need help... cause this is annoying. ](*,)

---

### Post by 5-HT on 2006-06-07
The server install, as you've noticed, does not include X or a window manager/desktop environment.

To install GNOME and bring your system up to that of a default Ubuntu install, all that is needed are two simple commands: ```
sudo apt-get update 
sudo apt-get install ubuntu-desktop 
``` 
Once ubuntu-desktop is installed,  a reboot will boot up to GDM from which you can log straight into GNOME.

Hope that helps.

---

### Post by Left Face Down on 2006-06-07
Thanks, it seems that it's working.


Edit: Thanks a lot, it works and I'm now in UBUNTU!

---

### Post by sorahl on 2006-06-07
i got a lot of errors
setting up python2.4-numeric
syntaxerror: invalid syntax

sorry it's not more complete i am writing this on another machine (obviously).

anothe error
compiling /usr/lib/python2.4......./HTMLutil.py ...
Sorry: IndentationError: ('unindent does not match any outer indentation level

what is that about???

and there it froze


thought this was only supposed to happen with Microsoft??? :)

---

### Post by sorahl on 2006-06-07
i rebooted the machine
and typed startx at the prompt
it changed to a grey screen with a white box aobut 4 inches wide and 3 inche high (all relative i know) with the cl prompt in it
i'm guessin gthis was not supposed to happen either :(

---

### Post by 5-HT on 2006-06-07
[quote=sorahl]i got a lot of errors
setting up python2.4-numeric
syntaxerror: invalid syntax

sorry it's not more complete i am writing this on another machine (obviously).

anothe error
compiling /usr/lib/python2.4......./HTMLutil.py ...
Sorry: IndentationError: ('unindent does not match any outer indentation level

what is that about???

and there it froze


thought this was only supposed to happen with Microsoft??? :)[/quote] 
Sorry about your problem, are you trying to install a default-install from the alternate CD or through another method?

Did you check the integrity of the installation disk (there's an option in the main menu when you boot with it, or you could check the md5 digests of the iso and burned CD)?

My first guess would be that the disk may be corrupt (bad download/burn).

BTW, it would be best to start a new thread for your problem with a descriptive and appropriately informative title.
 Doing so would assure your problem would get the most attention possible.

---

### Post by sorahl on 2006-06-07
I truly appreciate your reply. I think the problem is actually hardware. Gonna swap out for a different spare i have in the attic tomorrow and try again. if i still have issues i'll start a new thread then.

cheers,

Sorahl

---

