---
title: "New User of ubuntu trying to install Kylix"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by William English on 2007-05-20
Hi,
 I am a new user to ubuntu, I have installed version 7.04 desktop version and have been trying to install Kylix 3.  I have been trying to follow the installation instructions for Kylix but with no success.   
I performed the following steps but keep getting an error.  Because I am so new to the ubuntu environment I am not sure if I have messed up.  Can some one please help.

Here are the installation steps I have followd:
[COLOR="Blue"]mount /media/cdrom0
cd /media/cdrom0
sh setup.sh
[/COLOR]
This is the error I keep getting:
[COLOR="Red"]setup.sh: 93: Syntax error: "(" unexpected
[/COLOR]

Any help would be greatly appreciated.

---

### Post by DaveB05 on 2007-07-03
I am getting the same problem.  I have partially solved it by editing the setup.sh file.  first I created a directory on the hard disk and copied the contents of the cd into it.  Next press ALT F2 and type gk sudo gedit and open the setup.sh file.

Scroll down until you find the function called findlibrary.  There is () after the word findlibrary which need to be deleted.  Save the changes and change directory to the place you copied the cd and type sh setup.sh again.

This times loads of stuff happens but the install gets stuck again.  At this point I an having trouble myself.  If you have got anything new I would appreciate it.

Dave

---

### Post by junke1990 on 2008-02-21
> **DaveB05 said:**
> I am getting the same problem.  I have partially solved it by editing the setup.sh file.  first I created a directory on the hard disk and copied the contents of the cd into it.  Next press ALT F2 and type gk sudo gedit and open the setup.sh file.

Scroll down until you find the function called findlibrary.  There is () after the word findlibrary which need to be deleted.  Save the changes and change directory to the place you copied the cd and type sh setup.sh again.

This times loads of stuff happens but the install gets stuck again.  At this point I an having trouble myself.  If you have got anything new I would appreciate it.

Dave

Does anyone have any more info on how to install???? 

Removing the function wont help no mater what I do I can't get it to work

---

