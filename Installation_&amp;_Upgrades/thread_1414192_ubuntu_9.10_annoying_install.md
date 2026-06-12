---
title: "ubuntu 9.10 annoying install"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by longdog on 2010-02-23
[COLOR=black][FONT=Verdana]After initial configuration and install, the computer reboots to ask for login...[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I type my login name, press ‘Enter,’ then it asks for password and my keys do not work. The only key that works is 'Enter' which processes it and reports 'Invalid Username.' [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]While at the password part, I can hit enter and then quickly type my password (or whatever) and it works, but it does not process. The 'Invalid Username' still comes up.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I did not miss type my username as it is very easy and I tried many different names, phrases (all computer related) and the password line was always frozen. [/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Any ideas?[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Thank You[/FONT][/COLOR]

---

### Post by dabl on 2010-02-23
> **longdog said:**
> 

Any ideas?

Clearly there's some issue with your hardware.

Can you choose "Recovery Mode" from the boot screen, and try that?  The question is, does the keyboard work correctly when the system is running text only?  If "yes", then the issue is with the Gnome desktop.  If "no", then it is something more fundamental about your keyboard and hardware platform (which you'll have to disclose in detail).

---

### Post by elmosim2 on 2010-02-23
Isn't there an option somewhere to have it not even show how many characters you're typing?  Maybe you are putting in your password and it isn't showing it.

---

### Post by longdog on 2010-02-23
[COLOR=black][FONT=Verdana]I don't see how it could be the keyboard; typing the username and initially typing the password (when '*******' comes up) it works.  I don't know exactly what you mean by GNOME desktop.  It's just DOS-like text for goodness sake!  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I'm going to try the 'Recovery Mode' trick and try configuring the keyboard differently tonight, I can always reinstall, its a fresh hard drive.    [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR][COLOR=black][FONT=Verdana]And no luck with the ghost type.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thanks Again all…  Any more info on the GNOME desktop or other ideas are much appreciated.[/FONT][/COLOR]
 
LD

---

### Post by dabl on 2010-02-23
Reading your original post again, I'm wondering if you inadvertently had capslock on, or used a shift-character when you entered your user name during installation?  That would be a cause of the "Invalid Username" error, even if you put in the correct password.

Is it the same in text (DOS-like) mode as with the GUI login?

---

### Post by longdog on 2010-02-24
[COLOR=black][FONT=Verdana]Im in after trying with ghost type again last night so thank you.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Im now having other issues.  I'll take a step back...[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]This is my first linux install and I decided to go with Ubuntu bc I was told it was the easiest.  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Im installing the Ubuntu 9.10 Server Platform PC from CD and going right along with the article "The Perfect Server - Ubuntu 9.10 Server" @[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][[COLOR=#800080]http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3[/COLOR]]("http://www.howtoforge.com/perfect-server-ubuntu-9.10-ispconfig-3")[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]After installing the base system, I try and have problems with the following:[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]1. Configuring the Network (Page 3) - The "primary network interface"  [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-This is elementary but can I make up any IP addresses for the address, netmask, network broadcast, and gateway? (As long as it's good practice, netmask 192.255.255.0).[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-DO I need a website for this install?  I intend on getting one in the future of course.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-Is ubuntu desktop installed with Ubuntu 9.10 Server?  I know how to get it (sudo apt-get install ubuntu-desktop) but how do you get TO it?
-hostname -f does not show my server1.example.com.. is this a big problem? A fix? [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]2. Getting LAMP and all the goodies (Page 4)[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-Don't I need to connect to the internet to get these??[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]-If so, how do I connect to the internet in the command line? This is network correct?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I haven't gotten past here because I believe I need the proper network connections for everything to run smoothly.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Also, can I just SHUTDOWN and install from the cd again, and erase everything and start over?[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Thank you[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]LD[/FONT][/COLOR]

---

### Post by longdog on 2010-02-24
Also, I forgot to mention I have Comcast Cable Internet, for what it is worth.

---

