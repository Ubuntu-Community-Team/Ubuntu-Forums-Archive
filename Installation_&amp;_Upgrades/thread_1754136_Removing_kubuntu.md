---
title: "Removing kubuntu"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by jacqueshappy on 2011-05-09
I use ubuntu and wanted to try kubuntu. Installation worked fine and when I tried it out after a while I wanted to get rid of it and go back to ubuntu. There was no errors or anything, I just wanted to give it a trial run and I just prefer gnome. 
Back on ubuntu, how do I remove the kde packages?

---

### Post by AlphaLexman on 2011-05-09
```
sudo apt-get remove kdebase
```

---

### Post by wilee-nilee on 2011-05-09
Lower left corner in panel playing around, be very careful here there are cross shared applications.
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

---

### Post by jacqueshappy on 2011-05-09
> **AlphaLexman said:**
> ```
sudo apt-get remove kdebase
```

Thanks for replying but that just gives me this

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by wilee-nilee on 2011-05-09
> **jacqueshappy said:**
> Thanks for replying but that just gives me this

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Follow my link that command does very little altogether, as far as a complete removal.

The errors mean you have something else open like the software center or synaptic, or the silent update is going on in the background probably.

---

### Post by jacqueshappy on 2011-05-09
That link doesn't tell me anything about removing kubuntu

---

### Post by wilee-nilee on 2011-05-09
> **jacqueshappy said:**
> That link doesn't tell me anything about removing kubuntu


Go to the section I mention you need to look closer it will link you to a page where you get the list of every single kde application to pop in your terminal and wipe away.;)

Here is what your looking for, you should also mention the exact distro you are running always in a situation with such a great change. It says maverick in your sidebar, but many change the distro and not that notification
[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

---

### Post by AlphaLexman on 2011-05-09
You apparently have three different problems in three different threads, and they are all related to a common problem.

You have over-installed window managers and you still have a package manager open...

Logout and login again so you can clear your system...

Then post back with the results of the suggestions offered to you.

Good Luck.

---

### Post by jacqueshappy on 2011-05-09
> **wilee-nilee said:**
> Go to the section I mention you need to look closer it will link you to a page where you get the list of every single kde application to pop in your terminal and wipe away.
[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Ah yes, sorry. 
I have tried this one before and it didn't work (I made sure it was the code for 10.10)
I get this message:


The following packages have unmet dependencies.
 odbcinst1debian2 : Depends: odbcinst but it is not going to be installed
E: Broken packages

---

### Post by wilee-nilee on 2011-05-09
> **jacqueshappy said:**
> Ah yes, sorry. 
I have tried this one before and it didn't work (I made sure it was the code for 10.10)
I get this message:


The following packages have unmet dependencies.
 odbcinst1debian2 : Depends: odbcinst but it is not going to be **installed**
E: Broken packages

You get this on a removal or install, you want kde gone.

---

### Post by AlphaLexman on 2011-05-09
LOGOUT and LOGIN

Pretty please, with sugar on top!!!!

---

### Post by jacqueshappy on 2011-05-09
> **wilee-nilee said:**
> You get this on a removal or install, you want kde gone.

Yep I get that even though I'm trying to remove.
Also loads more lines of words preceding that saying certain things can't be removed because they aren't there but that's it's conclusion.
I know something's still there because it gives me the option to log in to kde still.

---

### Post by jacqueshappy on 2011-05-09
> **AlphaLexman said:**
> LOGOUT and LOGIN

Pretty please, with sugar on top!!!!

Yes, I've done that and I still get the options to open different variants

---

### Post by AlphaLexman on 2011-05-09
> **jacqueshappy said:**
> Yes, I've done that and I still get the options to open different variants
Have you executed the commands I gave you to un-install xfce4 & kdebase ??

---

### Post by jacqueshappy on 2011-05-09
> **AlphaLexman said:**
> Have you executed the commands I gave you to un-install xfce4 & kdebase ??

Yep done them both.
Nothing has happened. 
This is the entire text I get back when I do xfce4

jack@ubuntu:~$ sudo apt-get remove xfce4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xfce4 is not installed, so not removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

And this is what I get when I do kde

jack@ubuntu:~$ sudo apt-get remove kdebase
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'kdebase' can't be removed
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

As you can see, they both give me the option to remove 'blah-blah'
Should I?

---

### Post by AlphaLexman on 2011-05-09
The packages 'xfce4" and 'kdebase' are meta-packages that install the entire xfce and kde window managers respectively, it is possible you may have installed a dependent xfce or dependent kde package and the package manager automatically installed the dependencies. 

So you would have to remove the initial package that required the dependencies in order to completely remove the xfce and kde window managers.

I cannot guess or even predict / postdict what you did.

Can you use Synaptic Package Manger from the menu, System -> Administration -> Synaptic Package Manager to remove the desktop environments ??

---

### Post by jacqueshappy on 2011-05-10
Ok i'm going in package manager and marking everything for removal that has the letters xfce in it. Hopefully this will do the job. I'll do the same with kde if it works.

---

### Post by jacqueshappy on 2011-05-10
I've found that lots of things have randomly also decided to mark themselves for removal. I'm concerned some of them shouldn't be removed. Nautilus? Network manager gnome? Lots of open office programmes? Pidgen, Quadrapassel, Abiword, Python?!
It seems to want to get rid of everything!
It also puts stuff up for installing. This is just from me marking everything with xfce in it's name for removal.

---

### Post by jacqueshappy on 2011-05-10
Ok some weird issues now....
Having removed everything xfce related from the synaptics package manager, I still had a load of excess programmes that came with xfce (also kde) so I went into the ubuntu software centre to remove all of them (I realised these were probably most of the ones that it was prompting me to remove in synaptics as worried about above - I was too scared to let synaptics do it so I had to do it manually this way). I did that and then logged out, hoping to see that the option to log in with xfce would be gone! It was...but... so was the option to log in on kde. I hadn't got down to business with kde in synaptics yet...
I'm worried that perhaps kubuntu is still there somewhere but I just can't access it and it's some dead weight hard drive clogger. 
Also, another weird thing - when I turn on the computer and select ubuntu (instead of vista) Instead of getting the purple ubuntu loading screen, I get the blue kubuntu loading screen, even though I can't get onto kubuntu. And weirder yet - the log in screen is based on xubuntu, and has a little mouse/rat logo. 
So I guess xubuntu problem solved but kubuntu problem lives on....

---

