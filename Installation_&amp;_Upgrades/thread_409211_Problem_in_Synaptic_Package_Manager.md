---
title: "Problem in Synaptic Package Manager"
date: 2007-04-14
forum: Installation &amp; Upgrades
---

### Post by Elior on 2007-04-14
I can't open the "Synaptic Package Manager", because this  message:

```
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
```

* I new in Linux and I use in Ubuntu 7.04.

---

### Post by bulldog on 2007-04-14
Try in a terminal the command```
sudo aptitude update && sudo aptitude upgrade
```
If this isn't satisfying try ```
sudo aptitude dist-upgrade
```

New users shouldn't use Beta applications!!

---

### Post by Elior on 2007-04-14
this is not work =\

```
E: I wasn't able to locate a file for the virtualbox package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

```

---

### Post by bulldog on 2007-04-14
Did you use the sudo command?
Because it asked if you where root,I don't think so :D 

Well the answer is in the first line,you'll have to find the package manually,and install it.

---

### Post by Elior on 2007-04-14
if I understand you, I don't  want to install "virtualbox'. I want to open Synaptic Package Manage  without install that.

---

### Post by bulldog on 2007-04-14
Yes I understand,but you did something which needed the virtualbox install,this wasn't completed,and now synaptic refuse to open.

You,by all means,should know what you did before this was happening.

---

### Post by Elior on 2007-04-14
I install the virtualbox .  at the same time  happen  electrical blackout.

---

### Post by bulldog on 2007-04-14
Yes,that happens some time :( , but now you need to reinstall the virtualbox like you where doing before the blackout,and hope it repairs your problem.
After the success full install you can remove it of course.

---

### Post by Elior on 2007-04-14
If I want to install virtualbox I don't because this message:
[IMG]http://img185.imageshack.us/img185/7923/untitledmoo6.jpg[/IMG]

---

### Post by bulldog on 2007-04-14
Well,download it again,and try to install it.
It can be damaged,but to install you must use the sudo command,if not you can't install anything.

---

### Post by Elior on 2007-04-14
You can to show me   "sudo command"

edit :

I  writer in terminal :  sudo apt-get install VirtualBox_1.3.8_Ubuntu_edgy_i386.deb
and again show this message : 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

---

### Post by bulldog on 2007-04-14
sudo means you have to provide your to password,for instance,type in a terminal```
sudo -s
``` it will ask you for your root password.when you enter your password,you'll be a root in the terminal.
You have to type exit to leave the root status.

This provide you the rights to install and remove items or copy them,basically you can do anything you like.
So if you are not  familiar with the system,you could wipe out your ubuntu install without an error notification,so be very careful when you're operating as root.

To avoid people to be running around as root all the time,you can use the sudo command,to get root privileges for a short time or a command.
So if you want to install something```
apt-get install virtualbox 
``` wouldn't do anything,but```
sudo apt-get install virtualbox
``` will install the application,if it is in the repositories of course.


EDIT:
You have a .deb file somewhere on your disk,it seems to be corrupted,how did you get this file?

---

### Post by Elior on 2007-04-14
This is a output:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.

```

And I downloads in this web [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by bulldog on 2007-04-14
Just download the same .deb again and install it by right clicking the .deb and choose install with Gdebi.

---

### Post by TheWizzard on 2007-04-14
you can try
```
sudo dpkg --configure -a
```

but, as bulldog mentioned, beta versions are not for newbies. try edgy instead.

---

### Post by carusoswi on 2007-04-14
> **TheWizzard said:**
> you can try
```
sudo dpkg --configure -a
```

but, as bulldog mentioned, beta versions are not for newbies. try edgy instead.

Perhaps, but the solution to the problem I found in another thread:

sudo dpkg --purge --force-remove-reinstreq virtualbox

This will get a clean uninstall of the messed up one so that the package uninistaller will start like it is supposed to.

Now, then, perhaps someone can tell me why the package installer stalls at the "configuring virtualbox" screen after I spent four hours searching for the above to "unlock" my machine.

Presently, the package installer reports that all dependencies are satisfied, then, starts to install the package, the cute little orange thingies run back and forth in the bar forever.  If I click on the arrow to display the terminal window, I see a screen that says "configuring virtualbox".  The beginnings of a license agreement show up, but the screen is otherwise static.

If I stop this install, I am instructed to run some other code to force the package installer to quit so that I can try again.

Frustrating - I know that part of is that I don't know what I'm doing - but am trying to learn.

Assistance would be appreciated.

Caruso

---

### Post by carusoswi on 2007-04-14
oops, I meant to type package installer, not package uninstaller.

Sorry.

Caruso

---

### Post by TheWizzard on 2007-04-14
> **carusoswi said:**
> 
Now, then, perhaps someone can tell me why the package installer stalls at the "configuring virtualbox" screen after I spent four hours searching for the above to "unlock" my machine.


i'm not sure, but sometimes you need to give input during install. i'm using kde and therefore adept. in adept there is a button for more detail if such questions need to be answered.
i would advice you to use the command line for installing software. this gives you the questions during install more directly.  and makes it easy to track down what you actually did with the history command. 

cheers

---

