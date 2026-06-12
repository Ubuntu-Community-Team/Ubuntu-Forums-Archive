---
title: "Matlab R2006b on Ubuntu 7.10"
date: 2007-11-19
forum: Installation &amp; Upgrades
---

### Post by simocusi on 2007-11-19
I successfully installed this matlab version. I put it on /home/myname/matlab/ (any problem with this?). I don't know why I don't have permission to modyfy the usr folder for example..

Well, my actual problem is that it runs on the -nodesktop mode but when I run it on desktop it won't work. A grey screen appears and I cannot edit anything there. Seems I am missing some extra application..? I just installed the sun java 6, don't know if it has anything to do with it, but keeps the same error..

any help?

thanks a lot

---

### Post by Joshgray on 2007-11-20
i am having the same problem with R2007b. How do you run matlab in the nodesktop mode? What does that mean, that there is no GUI interface?

Thanks,
Josh

---

### Post by Joshgray on 2007-11-20
Here is the [solution]("http://ubuntuforums.org/showthread.php?t=357870&highlight=matlab") (if you haven't already found it)

And a direct link if that doesn't work: [http://ubuntuforums.org/showthread.php?t=357870&highlight=matlab](http://ubuntuforums.org/showthread.php?t=357870&highlight=matlab)

It worked for me

Cheers,

Josh

---

### Post by simocusi on 2007-11-20
Thanks Josh,

it works!!

i am really enjoying ubuntu!!

---

### Post by simocusi on 2007-11-20
However when i restart the terminal i have to type all this to get it working.

Do you know how can I fix it so that i just have to type Matlab?

export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre && matlab

thanks

simo

---

### Post by Joshgray on 2007-11-21
Yeah, you are going to have to edit the matlab launch file to add that export line.

So, enter a command similar to:

[FONT="Courier New"]sudo gedit /usr/local/matlab75/bin/matlab[/FONT]

Here /usr/local/matlab75 is just the root directory where you installed it, that is where mine happens to be.

So, in that file just add the line

[FONT="Courier New"]export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre && matlab[/FONT]

right after the first line (#!/bin/sh)

I don't know about the [FONT="Courier New"]&& matlab[/FONT] part, my system did not require that. 

Cheers,

Josh

---

