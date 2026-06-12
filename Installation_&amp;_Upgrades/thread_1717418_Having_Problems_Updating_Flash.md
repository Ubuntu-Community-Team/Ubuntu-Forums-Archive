---
title: "Having Problems Updating Flash"
date: 2011-03-29
forum: Installation &amp; Upgrades
---

### Post by hollyann on 2011-03-29
Hi,

I'm having problems updating my Flash.  

I typed in about plug-ins in my browser window and it looks like I have an old version of Flash, despite having downloaded the latest Adobe Flash, and as far as I know of, I installed it.  I think... :|

Can anyone help me to make sure I have the most updated Flash?  I have Ubuntu 10.04, and I'm using Firefox 3.6.15

The reason is that I've been noticing my Facebook games have been not working properly, they all seem to be having the same problem lately, so I thought that maybe it might be a Flash problem.

Can anyone help me out please?

---

### Post by mikewhatever on 2011-03-29
Can you, may be, tell us what version of flash is installed according to [noparse]about:plugins[/noparse].

---

### Post by collisionystm on 2011-03-29
Are you using 32 bit of 64 bit linux? 

Just go to adobe.com download the newest flash for linux. It comes in a .tar.gz file. Extract the file into your home folder

Open terminal and type, sudo nautilus
enter your password

When the sudo nautilus window comes up, go to filesystem (on the left) go to home, yourusername, desktop and right click on the libflash file you extracted, hit CUT

Now go back to file system, usr, lib, firefox addons, plugins, and paste the file there

close nautilus, close firefox

When you load firefox again, you are now updated

---

### Post by collisionystm on 2011-03-29
and i asked 64 or 32 bit because adobe has the 64 bit flash player square beta for linux that you should use. 32 bit will cause you problems.

---

### Post by hollyann on 2011-03-29
Sure!

Here's what it says in the About Plugins section:

**Shockwave Flash**

 File:  libflashplayer.so
Version:   Shockwave Flash 10.0 r45

And at the bottom of the page it has this:

**Shockwave Flash**

 File:  npwrapper.libflashplayer.so
Version:   Shockwave Flash 10.2 r153

---

### Post by mikewhatever on 2011-03-29
Flash 10.2 r153 is the latest version, and 10.0 r45 is apparently the version of the installer in Lucid.
> Filename: pool/multiverse/f/flashplugin-nonfree/flashplugin-installer_10.0.45.2ubuntu1_i386.deb


---

### Post by hollyann on 2011-03-29
Coll: Ok, I downloaded the Adobe Flash "Square" and followed your instructions, I think it worked?  One of the games on Facebook that was stuck loading before seems alright, but there's still a major one that isn't loading.  Maybe it's something wrong on the game side, I don't know?

Mike: Oh, so would I need a latest update the installer for Lucid Lynx?   

Sorry if I'm asking such newb questions, even after making the switch to Linux a year ago, I'm still trying to iron out a few things.

---

### Post by collisionystm on 2011-03-29
are you using 64 bit or 32

---

### Post by collisionystm on 2011-03-29
And... you are using firefox 3.6.15. In my experience flash compatibility with firefox 3.6 on linux just sucks anyways. Firefox 4.0 is much faster and you should upgrade.

---

### Post by mikewhatever on 2011-03-30
> **hollyann said:**
> ...

Mike: Oh, so would I need a latest update the installer for Lucid Lynx?   
...

No, since the installer just downloads the latest version of flash, but anyway, that's irrelevant, because you've done it all manually.

---

