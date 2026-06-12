---
title: "apt-? how do I get the feature whatprovides?"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by sdide on 2007-04-17
Hi, 

I need a file X11/xpm.h and I do not know which package provides it. 
Is there a command,  apt-get or apt-cache, with a certain option/switch, that provides this feature.

something like.

~$ apt-? -apropiateoption "whatprovides" X11/xpm.h 
libxpmwhatever
~$ 
 
Regards.

---

### Post by kornhead127 on 2007-04-17
I'm guessing you want the X11 pixmap library? If so...
```
sudo apt-get install libxpm4
```

---

### Post by sdide on 2007-04-17
Thanks.
That may be true. (actually I think I need libxpm-dev, but that is beside the point.)  
But what i wanted was a tool, that could tell me this, like fedora has "yum whatprovides blablabla"

Does apt have a similar feature?

---

### Post by kornhead127 on 2007-04-17
Damn, you know what I don't think it has a feature like that. May I ask why you would require a piece of source (xpm.h).

---

### Post by sdide on 2007-04-19
I needed xpm.h, because I wanted to compile bbbutton. But its a shame that I can't get apt to do this for me.
yum - which I usually consider inferior, has this nice feature. 

oh well. Thanks anyways.

---

### Post by eentonig on 2007-04-19
> sudo apt-get update
apt-cache search <keyword>

Will let you search packages in the repositories. It searches the name and description of the available packages.

---

### Post by sdide on 2007-04-20
Yeah, I guess apt-cache search is the closest I'll get. 
However it doesn't catch what files are provided by each package. Maybe its because the information provided in the package desciption - the one apt-cache search does regex search through - does not contain which files are provided with that package.

so 
~$ apt-cache search ".*xpm.h"

returns nothing even though, the package libxpm-dev installs that file, and its actually located in 
/usr/include/X11


however the command 
~$ dpkg-query -S "*xpm.h"

returns 
libxpm-dev: /usr/include/X11/xpm.h

Which is great, only - thats what it returns because I have the package already installed! If I remove the package it returns nothing, so it is no good.

What i needed was a feature that could return this result before I installed the package...

Solution install EVERY package, make a list of packages installed find out which one contained the file, and the remove all other packages again. 
Which is ofcourse - retarded.

---

### Post by kb00heda on 2007-04-22
Hi,

This is not the solution to your query, but at least---I guess---it is an acceptable workaround:

Visit

[http://packages.ubuntulinux.org]("http://packages.ubuntulinux.org")

and use the "Search the contents of packages" option. The keyword could be "xpm.h", in which case a search among the Feisty packages would tell us that, e.g., "libxpm-dev" provides this file.

But I agree: This nice feature should really be available from the CL using apt/aptitude. (And probably it is... but we have still to figure it out!)

Best regards,
David

---

### Post by milstead on 2008-03-05
The functionality you were looking for is supplied by apt-file. To install:

sudo apt-get install apt-file

To use:

sudo apt-file update

sudo apt-file search <filename>

Enjoy,

Tim.

---

