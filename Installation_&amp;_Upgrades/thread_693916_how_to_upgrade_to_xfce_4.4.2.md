---
title: "how to upgrade to xfce 4.4.2?"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by kystorms on 2008-02-11
i would like to upgrade my xfce ( because its devoid of so much for some reason) to the newwer version of 4.4.2 but I have no idea how to do it

Is this not possible in  the synaptic manager? Newbie here, is there a how to on how to upgrade?

thanks

---

### Post by codeslicer on 2008-02-11
Try going to System->Administration->Update Manager. After it loads, click Update and wait for Ubuntu to check for new versions of the software. If it does, update all of it.

---

### Post by drummingpariah on 2008-02-11
There's a command-line way to do this as well.

Open a terminal and type:
```
sudo apt-get update
sudo apt-get upgrade
```

and that should prompt you for your password and automatically update all the software you have installed that has a newer version available on any site in your sources.list (located in /etc/apt/sources.list).

---

### Post by kystorms on 2008-02-11
hi

did both ways, and nothing changed, no upgrades.
I have downloaded the 4.4.2 tar.bz2 file to my desktop

but now I have no idea where to extract it to or how to open and run it????

again, I am a newbie with this file stuff

:confused:

---

### Post by drummingpariah on 2008-02-11
> **kystorms said:**
> hi

did both ways, and nothing changed, no upgrades.
I have downloaded the 4.4.2 tar.bz2 file to my desktop

but now I have no idea where to extract it to or how to open and run it????

again, I am a newbie with this file stuff

:confused:

That tarball(that's what we call almost anything that's a .tar file, this particular tarball is a bzip2) really isn't the way you want to go about this.  Ideally, you want your apt sources to **automatically** update for you.  If you were to install from a tarball, it'd be just like installing a Windows application, where you'd be in charge of upgrading it yourself (which takes away all the fun-factor of having .deb files).  It's possible that you aren't using xubuntu Gutsy Gibbon, which would keep your apt sources from updating.  Try this to update your entire system:
```
sudo apt-get dist-upgrade
```That should bring you up to the latest (stable) version of XFCE (so far I've been assuming 4.4.2 is the latest blessed version).

*edit*
I just checked, and 4.4.1 is the latest version of XFCE offered in Gutsy, and that's definitely the version I recommend.  Try to find out exactly what version of Xubuntu you're running(I'm not sure what the specific console command is but it should be available in one of your drop-down menus) and what version of XFCE you currently have.

Assuming you've downloaded this link:
[http://rapidshare.com/files/78432733/xfce4_4.4.2_gutsy.tar.bz2.html](http://rapidshare.com/files/78432733/xfce4_4.4.2_gutsy.tar.bz2.html)

and it's compatible with your version of Xubuntu (meaning you already have gutsy), and you want to leave the safely beaten and blessed path that the Xubuntu official development team has approved and tested for compatibility, you can install that tarball (which is like a zip file) using the .deb file it contains.  You'd want to start by untaring it (just like unzipping) by typing:
```
tar -zxjf xfce4_4.4.2_gutsy.tar.bz2
``` (just make sure you're in the right directory; if it's on your desktop you'll want to type ```
cd ~/Desktop
```) and hit enter first.
That will give you a .deb package on your desktop.  You can install that using Synaptic, but I can't stress how much I don't recommend this method.  If you aren't intimately familiar with how the .deb system works, adding a non-native app can be very difficult to reverse.  If you're familiar, it's as easy as ```
sudo apt-get remove xfce4_4.4.2
``` but there's a good chance that you won't remember or even that the source was not compiled correctly to begin with (for your system).  If you really want to go nuts with non-blessed software, your question should be geared toward "how do I switch from 'stable' to 'testing' or 'unstable' versions of Xubuntu".  That way you'll have a somewhat compatible pile of apps.  Mixing and matching can have unforseen consequences and should be avoided.

Now that I'm done ranting (bear in mind, I'm not trying to say that you shouldn't do this, just that it's not a good idea... I do tons of stupid things ALL the time, myself), what is it about 4.4.2 that you want so badly?

---

### Post by kystorms on 2008-02-12
hi

wow thanks for that walk through its the first one i could understand!
When i followed the road map, and this is what i got in code:

lisac@lisac:~/Desktop$ tar -zxjf xfce4_4.4.2_gutsy.tar.bz2
tar: Conflicting compression options
Try `tar --help' or `tar --usage' for more information.
lisac@lisac:~/Desktop$ 
lisac@lisac:~/Desktop$ 

now the tar.bz2 is on my desktop , so I dont know what I am missing here???

thanks SO much for the help so far tho, as its made me understand a bit of what its needed to do with these pesky things.

I should have added here that I am infact running Gutsy Gibbon, off the CD from here.

---

### Post by drummingpariah on 2008-02-13
> **kystorms said:**
> hi

wow thanks for that walk through its the first one i could understand!
When i followed the road map, and this is what i got in code:

lisac@lisac:~/Desktop$ tar -zxjf xfce4_4.4.2_gutsy.tar.bz2
tar: Conflicting compression options
Try `tar --help' or `tar --usage' for more information.
lisac@lisac:~/Desktop$ 
lisac@lisac:~/Desktop$ 

now the tar.bz2 is on my desktop , so I dont know what I am missing here???

thanks SO much for the help so far tho, as its made me understand a bit of what its needed to do with these pesky things.

I should have added here that I am infact running Gutsy Gibbon, off the CD from here.

Sorry, my bad.  I wasn't paying attention to my typing.  You want to use ```
tar -jxvf xfce_4.4.2_gutsy.tar.bz2
```

That should give you better results :)  I just want to make sure I drive home the fact that you're probably going to break your system by doing this.  Fair warning.  There are much easier ways to go about all this using graphical user interfaces, but I'd really rather you type out the commands so you'll glean at least a bit of what's actually going on.  Let me reiterate:

**You want to use testing or unstable instead of hacking a different build of xfce**

If you do manage to squeeze this version of xfce in that you have now, bear in mind that it depends on libraries of commands that you have.  Those libraries need to be the exact version that your particular build of xfce is compatible with.  Right now, your libraries are carefully tailored to be compatible with xfce 4.4.1, not 4.4.2.  If you install 4.4.2, it may cause dependency problems and keep your system from booting.  Even if it **does** work, the next time your libraries are updated, your xfce 4.4.2 will likely break.  You really want to change over to testing/unstable because that will include the correct libraries to run the latest xfce4.

You can either switch all your apt sources over, or you can install Hardy Heron right from the start:
[http://cdimage.ubuntu.com/xubuntu/releases/hardy/alpha-3/](http://cdimage.ubuntu.com/xubuntu/releases/hardy/alpha-3/)

Good luck, and keep asking questions!

---

