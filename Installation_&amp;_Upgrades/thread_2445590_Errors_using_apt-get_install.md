---
title: "Errors using apt-get install"
date: 2020-06-16
forum: Installation &amp; Upgrades
---

### Post by Softa on 2020-06-16
I've downloaded the  install file for Zoom, but can't get it installed.  If I try using the GUI, it just blinks and I'm back where I started.  If I try it from a terminal using ```
sudo apt-get install zoom
``` I get this:

The following packages have unmet dependencies:
 zoom:amd64 : Depends: libglib2.0-0:amd64 but it is not installable
              Depends: libxcb-shape0:amd64 but it is not installable
              Depends: libxcb-shm0:amd64 but it is not installable
              Depends: libxcb-xfixes0:amd64 but it is not installable
              Depends: libxcb-randr0:amd64 but it is not installable
              Depends: libxcb-image0:amd64 but it is not installable
              Depends: libfontconfig1:amd64 but it is not installable
              Depends: libgl1-mesa-glx:amd64 but it is not installable
              Depends: libegl1-mesa:amd64 but it is not installable
              Depends: libxi6:amd64 but it is not installable
              Depends: libsm6:amd64 but it is not installable
              Depends: libxrender1:amd64 but it is not installable
              Depends: libpulse0:amd64 but it is not installable
              Depends: libxcomposite1:amd64 but it is not installable
              Depends: libxslt1.1:amd64 but it is not installable
              Depends: libsqlite3-0:amd64 but it is not installable
              Depends: libxcb-keysyms1:amd64 but it is not installable
              Depends: libxcb-xtest0:amd64 but it is not installable
              Depends: libdbus-1-3:amd64 but it is not installable
              Depends: libxtst6:amd64 but it is not installable

What will I need to do to fix this?

---

### Post by TheFu on 2020-06-16
Try 
```
sudo **apt** install /path/to/zoom-xxxx-yyy--dddd-zzzz.deb
```
You can use absolute or relative paths, whatever is shorter. May try drag-in-drop of the file from a file manager after you enter everything except the path too. That should paste the fill path+filename into the terminal for you.  In theory. Just depends on the file manager and terminal capabilities. If in the same directory where you downloaded the .deb file, I'd use:
```
sudo **apt** install ./zoom-xxxx-yyy--dddd-zzzz.deb
```

I&#8217;ve never used or installed zoom so don't know what sort of install it actually has. Those instruction above assume it is a debian package.

**apt** is a little different than **apt-get**. it will install .deb files which apt-get will not, but only if a path of some sort is included to the .deb file. In general, apt is easier for humans, does more useful stuff, except some fairly specific things that apt-get handles nicer but we humans seldom need.

---

### Post by grahammechanical on 2020-06-16
I would like to confirm that you are using Xubuntu 16.04. The version of Zoom Client on the Zoom web site is for Ubuntu 14.04. That could be the cause of the problem. I installed that version of Zoom Client on 20.04 using the download centre on the Zoom web site. It worked fine and placed Zoom Client into Ubuntu Software.

I have since removed the deb version and used the Ubuntu Software store to install a snap version of Zoom Client that is based on newer versions of Zoom Client. Newer versions fix some of the security vulnerabilities that some were worried about. This snap version has been updated a couple times since I started using it. I now notice that the connection between my client and the host has stronger encryption which it did not have before.

The snap version contains all the libraries (dependencies) the application needs. Even those that are not in the repositories of a Ubuntu version we may be using. And yes, Snap apps should install and work in 16.04. But you may not find it in the 16.04 Software Centre.

[https://snapcraft.io/install/zoom-client/ubuntu](https://snapcraft.io/install/zoom-client/ubuntu)

Regards

---

### Post by deadflowr on 2020-06-16
>  The version of Zoom Client on the Zoom web site is for Ubuntu 14.04. 
It's actually for 14.04 and newer, hence they add the + sign on the download page.
It's installable up to at least 18.04.

I'm more surprised that most of the depends aren't already installed.
Is this a 64-bit OS, even?

---

### Post by ajgreeny on 2020-06-17
And the .deb version from the zoom website is now the same as the snap version so you are good with either.

---

### Post by Softa on 2020-06-18
I went to the directory containing the .deb and followed your instructions using ./ as the path, but apt couldn't find it.  I tried again, without the path and got this:

> Building dependency tree       
Reading state information... Done
E: Unable to locate package zoon_amd64.deb
E: Couldn't find any package by glob 'zoon_amd64.deb'
E: Couldn't find any package by regex 'zoon_amd64.deb'

I'm beginning to suspect that there's something wrong with the .deb itself.

---

### Post by ajgreeny on 2020-06-18
I hope you did not search for zoon.deb; it is zoom!

The problem may be with your spelling, not the .deb package.

---

### Post by TheFu on 2020-06-18
> **ajgreeny said:**
> I hope you did not search for zoon.deb; it is zoom!

The problem may be with your spelling, not the .deb package.

OP, do you know how to _use tab-completion_?  Using that, you'll almost never misspell anything on the shell again. It is hard to explain in text, but trivial to use once you see someone else using it.  Nobody types those full names out. We have the computer fill it in for us after providing a little hint and pressing {tab} one or 2 times. If this isn't clear, find a youtube video about it. Takes 10 seconds to learn and will make you love using bash.

Or you could _try using filename globbing pattern matching_. If only 1 file in the directory begins with a 'z' character, you might be able to use **sudo apt install ./z*deb**.  I'm not positive whether apt will work that way, but most commands do. It is called "shell filename globbing."  99% of the time, it will work.  The old MS-Dos *.* was the same idea, but in Unix, we just need *, since shells don't care about extensions at all. On Unix, filename extensions are handy for humans and just a few GUI programs which filter file lists using extensions, but not actually required for the file contents to be handled correctly.

If you want to know more things that your shell can do, there are books or this relatively quick summary: [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) page down and start reading when the guide shows up. Don't worry about the first page being all codey.  The FIRST thing in the "Everyday Use" section is tab-completion.

That's a bunch of words just for "spell it correctly and have the computer do that for you."

---

