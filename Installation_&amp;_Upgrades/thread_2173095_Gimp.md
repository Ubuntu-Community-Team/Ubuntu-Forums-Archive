---
title: "Gimp"
date: 2013-09-08
forum: Installation &amp; Upgrades
---

### Post by reggler on 2013-09-08
Hi,

I just wanted to install gimp and when I try to start it I get this:
```

$ gimp
Segmentation fault (core dumped)

```
Why, what is going on here? I made sure with apt-get install -f that there's no missing depencies... :(
any help is appreciated!

---

### Post by carl4926 on 2013-09-08
Just install via the software centre or synaptic

---

### Post by reggler on 2013-09-08
i did use the software centre for installation...

---

### Post by ibjsb4 on 2013-09-08
What are you rinning?  12.04, 13.04 ?

---

### Post by reggler on 2013-09-08
> **ibjsb4 said:**
> What are you rinning?  12.04, 13.04 ?

13.04

---

### Post by ibjsb4 on 2013-09-08
Try a purge and install

```
sudo apt-get remove --purge gimp && sudo apt-get install gimp
```

---

### Post by ibjsb4 on 2013-09-08
One last thought before I go to bed :)

You could also try the ppa install.

[http://www.ubuntugeek.com/gimp-2-8-6-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/gimp-2-8-6-released-and-installation-instructions-included.html)

---

### Post by reggler on 2013-09-08
> **ibjsb4 said:**
> Try a purge and install

```
sudo apt-get remove --purge gimp && sudo apt-get install gimp
```

That was the first thing I tried, just retried again but no, not working, same seg fault.... now giving the ppa a go, let's see... uh, that downloaded additional stuff i.e. gimp-data and libgimp2.0 but guess what, in te end:
```

$ gimp
Segmentation fault (core dumped)

``` :(

---

### Post by carl4926 on 2013-09-08
So it's installed? Just not loading?
Did you test the guest login?

---

### Post by sudodus on 2013-09-08
> **reggler said:**
> Hi,

I just wanted to install gimp and when I try to start it I get this:
```

$ gimp
Segmentation fault (core dumped)

```
Why, what is going on here? I made sure with apt-get install -f that there's no missing depencies... :(
any help is appreciated!

I just tried the same (what I think is the same) procedure to install gimp into an updated Lubuntu 13.04 32-bit. And it works. Not only can I start the program with ```
gimp
``` I can also use it to edit a picture and save it.

```
guru@pae4pm:~$ [COLOR=#0000ff]sudo apt-get update[/COLOR]
...
guru@pae4pm:~$ [COLOR=#0000ff]sudo apt-get dist-upgrade [/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
guru@pae4pm:~$ [COLOR=#0000ff]lsb_release -a[/COLOR]
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring
guru@pae4pm:~$ [COLOR=#0000ff]uname -a[/COLOR]
Linux pae4pm 3.8.0-29-generic #42-Ubuntu SMP Tue Aug 13 23:12:18 UTC 2013 i686 i686 i686 GNU/Linux
guru@pae4pm:~$ [COLOR=#0000ff]gimp[/COLOR]

** (gimp:16222): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/null.png,
borders don't fit within the image

** (gimp:16222): WARNING **: Invalid borders specified for theme pixmap:
        /usr/share/themes/Lubuntu-default/gtk-2.0/images/scrollbar_vertical.png,
borders don't fit within the image
guru@pae4pm:~$ 
```

There are warnings, but gimp works for me. Are you running the same version i686 alias 32-bit, or are you running the 64-bit version?

- if you are running the 32-bit version, either you have some other bad package or a system, that is not fully updated/upgraded.

- if you are running the 64-bit version, someone else might check if gimp works in an up to date system.

---

### Post by reggler on 2013-09-08
> **carl4926 said:**
> So it's installed? Just not loading?
Did you test the guest login?

Yes but what guest login are you talking about, different user?

---

### Post by reggler on 2013-09-08
Yes, I got my system on a x86_64 version

---

### Post by carl4926 on 2013-09-08
> **reggler said:**
> Yes but what guest login are you talking about, different user?

Just for testing purposes: Create a new user and try gimp

---

### Post by sudodus on 2013-09-08
> **reggler said:**
> Yes, I got my system on a x86_64 version

Someone running *ubuntu 13.04 x86_64, please test if gimp works on your system (after update/dist-upgrade)!

And *reggler*, please let us know if you have installed something from a downloaded deb file or if you are using some ppa!

---

### Post by reggler on 2013-09-08
interesting, i can launch it just fine with an other user... hmm, why might that be :o

---

### Post by carl4926 on 2013-09-08
Flucked up hidden settings

I'd try deleting the hidden config files for Gimp, well at least rename it
Look for** .gimp-2.8** folder
rename it to .OLD-gimp-2.8

---

### Post by sudodus on 2013-09-08
> **carl4926 said:**
> Flucked up hidden settings

I'd try deleting the hidden config files for Gimp, well at least rename it
Look for** .gimp-2.8** folder
rename it to .OLD-gimp-2.8

I'll take this as a warning, that gimp 2.8 can have problems with the user specific settings.

Thank you, carl4926 :KS

---

### Post by reggler on 2013-09-08
> **carl4926 said:**
> Flucked up hidden settings

I'd try deleting the hidden config files for Gimp, well at least rename it
Look for** .gimp-2.8** folder
rename it to .OLD-gimp-2.8

There is no .gimp directory in my home as it never got there, the seg fault appears immediately...

---

### Post by carl4926 on 2013-09-08
> **sudodus said:**
> I'll take this as a warning, that gimp 2.8 can have problems with the user specific settings.

Thank you, carl4926 :KS
I have not experienced the OP's issue but had one or two odd usability issues and ended up just doing as described. Only slightly annoying in my case, but still a pain as I do a fair bit of work with Gimp. Fortunately I keep a list of my colour codes elsewhere too.

---

### Post by carl4926 on 2013-09-08
> **reggler said:**
> There is no .gimp directory in my home as it never got there, the seg fault appears immediately...

So this is a clean installation that never used gimp?

---

### Post by reggler on 2013-09-08
> **carl4926 said:**
> So this is a clean installation that never used gimp?

no, just wanted to install it. the system is not necessarily fresh anymore, i've been using it for quite a while already...

---

### Post by carl4926 on 2013-09-08
> **reggler said:**
> no, just wanted to install it. the system is not necessarily fresh anymore, i've been using it for quite a while already...

OK. So we established that Gimp is fine in a new user - which pretty much suggests the system is fine.
So the issue must be in your user settings
You can reset the user back to like a new user, but that is perhaps the last option.

I don't have time now to look deeper in to what gimp is playing with. I'll be back later to see how you get on with others here

---

### Post by sudodus on 2013-09-08
> **reggler said:**
> There is no .gimp directory in my home as it never got there, the seg fault appears immediately...

Are you sure? Try

```
sudo find ~ -name ".gimp*"
```

---

### Post by carl4926 on 2013-09-08
From my netbook
```
lsb_release -aNo LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring
kernelcruncher@kernelcruncher-1015PEM:~$ uname -a
Linux kernelcruncher-1015PEM 3.8.0-30-generic #44-Ubuntu SMP Thu Aug 22 20:52:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
kernelcruncher@kernelcruncher-1015PEM:~$ gimp

I have:
gimp           2.8.4-1ubunt amd64



```

---

### Post by reggler on 2013-09-08
> **sudodus said:**
> Are you sure? Try

```
sudo find ~ -name ".gimp*"
```
Didn't find nothing...

---

### Post by sudodus on 2013-09-08
I see, but I don't understand.

Please let us know if you have installed something from a downloaded deb file or if you are using some ppa!

Do you have the same version as carl4926? Try if you reach far enough to get the version output

```
gimp -version
``` or try ```
man gimp
```

The version number should be at the very end of the man page.

---

### Post by SeijiSensei on 2013-09-08
All my GIMP settings are in ~/.gimp-2.8.  (I also have a .gimp-2.6 directory hanging around.)  I also looked in ~/.config, there is nothing GIMP-related there.  

Are you sure you don't have a .gimp-2.8 directory at all?  The fact that it works with a new user but not your own makes me think the directory has to be hiding there.  If you're using a graphical file manager, make sure you have it set to show "hidden" files, or just use "ls -la ~" from the command line.

---

### Post by reggler on 2013-09-08
> **sudodus said:**
> I see, but I don't understand.

Please let us know if you have installed something from a downloaded deb file or if you are using some ppa!

Do you have the same version as carl4926? Try if you reach far enough to get the version output

```
gimp -version
``` or try ```
man gimp
```

The version number should be at the very end of the man page.

Yep, that still works:
```

$ gimp -version
GNU Image Manipulation Program version 2.8.6

```

---

### Post by reggler on 2013-09-08
> **SeijiSensei said:**
> All my GIMP settings are in ~/.gimp-2.8.  (I also have a .gimp-2.6 directory hanging around.)  I also looked in ~/.config, there is nothing GIMP-related there.  

Are you sure you don't have a .gimp-2.8 directory at all?  The fact that it works with a new user but not your own makes me think the directory has to be hiding there.  If you're using a graphical file manager, make sure you have it set to show "hidden" files, or just use "ls -la ~" from the command line.

Yep, nothing there:
```

~$ ls -la .gimp*
ls: cannot access .gimp*: No such file or directory

```

---

### Post by sudodus on 2013-09-08
> **reggler said:**
> Yep, that still works:
```

$ gimp -version
GNU Image Manipulation Program version 2.8.6

```

So your version is newer than carl's
```
gimp           2.8.4-1ubunt amd64
```
I wonder why. Maybe gimp           2.8.4 would work for you.

---

### Post by reggler on 2013-09-08
> **sudodus said:**
> So your version is newer than carl's
```
gimp           2.8.4-1ubunt amd64
```
I wonder why. Maybe gimp           2.8.4 would work for you.
The most recent verson I have should come from the ppa,

---

### Post by sudodus on 2013-09-08
Ok, but if you purge gimp

```
 sudo apt-get purge gimp
```

and remove the ppa, and install the regular version of gimp from the regular repository

```
sudo apt-get update
sudo apt-get install gimp
```

Will it work?

Have you installed something else, that might interfere? Something available to your user, but not to the other one, where you could run gimp?

Do you have some wine programs installed? Or some alias?

---

### Post by reggler on 2013-09-08
> **sudodus said:**
> Ok, but if you purge gimp

```
 sudo apt-get purge gimp
```

and remove the ppa, and install the regular version of gimp from the regular repository

```
sudo apt-get update
sudo apt-get install gimp
```

Will it work?

Have you installed something else, that might interfere? Something available to your user, but not to the other one, where you could run gimp?

Do you have some wine programs installed? Or some alias?
 
Well no, that's what I had tried first... i'll retry now but I wouldn't know why it should work now...

---

### Post by sudodus on 2013-09-08
You are right. 

But have you installed something else, that might interfere? Something available to your user, but not to the other one, where you could run gimp?

Do you have some wine programs installed? Or some alias?

---

### Post by reggler on 2013-09-09
> **sudodus said:**
> You are right. 

But have you installed something else, that might interfere? Something available to your user, but not to the other one, where you could run gimp?

Do you have some wine programs installed? Or some alias?

I can't really think of anything THAT special, only Synapse Portal maybe ([http://forums.synapse-wireless.com/upload/Portal-Linux-2.4.37.zip](http://forums.synapse-wireless.com/upload/Portal-Linux-2.4.37.zip)) which I could get rid of now, too if required...

---

### Post by carl4926 on 2013-09-09
The solution is staring you in the face, though it's somewhat laborious and tedious.
Backup all your personal files and hidden settings that you require > Login to your other user account > Delete your user (inc, /home folder) > Re-create the user > Login > Copy back your files

---

### Post by sudodus on 2013-09-09
> **reggler said:**
> I can't really think of anything THAT special, only Synapse Portal maybe ([http://forums.synapse-wireless.com/upload/Portal-Linux-2.4.37.zip](http://forums.synapse-wireless.com/upload/Portal-Linux-2.4.37.zip)) which I could get rid of now, too if required...

You can try to uninstall the Synapse Portal (and reinstall it, if it made no difference). It is much easier than to backup, wipe and re-create your whole user account. But I tend to agree with *carl4926* about the solution.

---

