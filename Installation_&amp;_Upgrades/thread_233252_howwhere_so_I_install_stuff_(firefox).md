---
title: "how/where so I install stuff (firefox)?"
date: 2006-08-09
forum: Installation &amp; Upgrades
---

### Post by blackdalek on 2006-08-09
I have just arrived here in linux land from windoze and mac.
Now that I'm here, I don't know what I'm doing.

I downloaded latest firefox 1.5.0.6...
Now I have a firefox-1.5.0.6.tar.gz on my desktop and a folder on my desktop called "firefox" which I extracted from this .gz file.

What do I do now? Do I drag the firefox folder from the desktop to some other folder in my filesystem? where? and how?

I did a file search with Places > Search for files... for "firefox" to see if I could work out where the 1.5.0.3 was located - this just confused me more as there seems to be firefox files all over the place in different locations.

Tried to search the forums for how to install firefox, but maybe I'm searching the wrong words cos all I get is pages upon pages of how to install plug-ins or other stuff not related to installing apps or firefox.

Thank you for helping :)

---

### Post by spin2cool on 2006-08-09
My advice would be to start here:
[http://www.getautomatix.com/](http://www.getautomatix.com/)

Automatix will let you automatically install all sorts of stuff that you might find useful, including new versions of firefox.  

After you run it, go to help>check for updates inside firefox.  firefox's update system should then get you any really recent updates.

---

### Post by enopepsoo on 2006-08-09
Note Well:  On Ubuntu you rarely need to download a file from the web and install it.  Typically there are two ways to install a program

[LIST=1]
[*]apt-get
[*]synaptic
[/LIST]

Using apt-get only works if you know the name of the application you are trying to install.  For example, if you want to install jumpnbump, type this into the console:
```
sudo apt-get install jumpnbump
```
[list]
[*]sudo means Super User - Do, this basically gives you the right to install a program (or do anything else on your system).  You will need to enter your password when you enter sudo before a command.
[*]apt-get is the application that connects to the software repositories, check dependencies and installs the software. 'install' is one of the common uses of apt-get (another is 'remove').  At the end of the line you put the exact package name you wish to install, sometimes knowing this name is tricky, which is why there is synaptic.
[/list]
To use the Synaptic package manager, click on the system menu and load the application.  It has a gui and is fairly self explanatory.  If you feel limited in your choices, you may enter the options menu and add more repositories.

Enjoy Ubuntuing, it is marvellous.

---

