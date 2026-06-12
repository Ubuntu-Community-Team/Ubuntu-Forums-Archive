---
title: "Overall thoughts and question about installations"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by the_photon on 2011-01-07
Hello all,

Although my overall experience with Ubuntu has been positive in most senses, please pardon me while I blow off a bit of steam, in a polite way. 

My question is this:  what they h*ll is wrong with Ubuntu in particular and computers in general!  Is it just my machine?  Does everyone struggle to install programs on Ubuntu the way that I do?

I suppose that what I really mean to say is that I have been a Ubuntu user for about eight months now, and I am constantly finding that "Program X" cannot complete a make install, because "Error 1: Abort source could not locate file /home/name/blahbla.  File wtf-apt-get-pseudo.src must not be installed properly." (and no of course that's not a real error message, and yes I'm being a bit facetious.) 

After several hours of searching the internet, I find a download for wtf-apt-get-pseudo.src.  After another hour of studying a README file, I think I have figured out what is necessary to get wtf-apt-get-pseudo.src to install, and then it won't complete a make file because it can't find some other file -- a fool's errand it seems.

To state some more concrete (and less emotionally slanted) examples, I currently cannot get CUPS, hplip, Tcl/Tk, and a long list of other programs to install (or make install, I suppose) on my Ubuntu machine.  I am currently a graduate student in computer science (who seems to be lagging behind in his linux family knowledge -- much of our work is on windows, visual studio, etc.)

I am curious to know if all Ubuntu/Linux users have a long list of programs that should install but won't, and have to have an additional Windows machine like I do just to do normal stuff that should be easy.

Again, forgive the rant, but I am curious if I am the only one who has these difficulties in general with installing anything on my Ubuntu machine.  I am currently using Ubuntu release 10.04 (lucid).  Suggestions are welcome -- but yes I already own several linux books, and if you want to see my error messages (in the situations above), I might be willing to post them, but a long line of Linux users have already been unable to really fix any of the problems.

the_photon

---

### Post by oldos2er on 2011-01-07
Are you compiling source code (it sounds like it)? Cups and hplip are both in the repositories, which should always be one's first choice for installing software.

---

### Post by Rubi1200 on 2011-01-07
Did you install the  build-essentials package?

```
sudo apt-get install build-essentials
```

More information:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

