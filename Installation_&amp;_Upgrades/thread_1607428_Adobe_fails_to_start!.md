---
title: "Adobe fails to start!"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by Ceiber Boy on 2010-10-27
I installed Ubuntu 10.10 64-bit, downloaded Adobe reader '.bin', from the terminal

$chmod a+x 'file name'.bin
$./'file name'.bin

it extracted and asked me for a installation location, to which i put [~]

it then finished the installation.

but when i click on the icon in the start menu or on desktop it fails to start, when i also click on a .pdf document it also fails to start!

I'm stumped!

any ideas or help would be greatly appreciated

Thanks

---

### Post by efflandt on 2010-10-27
It does not run because ~ is not in your PATH.  You should have created a **bin** directory in your home directory (**mkdir ~/bin**).  Then if you just wanted it for you only you should have installed it to ~/bin

Next time you logged in your **bin** would have been automatically included in your path:

**echo $PATH**
/home/efflandt/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

I was going to suggest adding your home directory to your PATH (in ~/.profile), but that is not normally accepted practice. Programs (binaries) are usually in a bin directory.

But you could create a bin directory and then put a symlink there that points to the Acrobat reader.

**mkdir ~/bin**
**link -s ~/acroread_or_whatever ~/bin/.** (with the dot at the end)
log out of X, log back in, and see if it works.

I just haven't used the Acrobat Reader in Linux for a long time, so I don't know if it is still called acroread or something else.

---

### Post by Ceiber Boy on 2010-10-28
> **efflandt said:**
> It does not run because ~ is not in your PATH.  You should have created a **bin** directory in your home directory (**mkdir ~/bin**).  Then if you just wanted it for you only you should have installed it to ~/bin

Next time you logged in your **bin** would have been automatically included in your path:

**echo $PATH**
/home/efflandt/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

I was going to suggest adding your home directory to your PATH (in ~/.profile), but that is not normally accepted practice. Programs (binaries) are usually in a bin directory.

But you could create a bin directory and then put a symlink there that points to the Acrobat reader.

**mkdir ~/bin**
**link -s ~/acroread_or_whatever ~/bin/.** (with the dot at the end)
log out of X, log back in, and see if it works.

I just haven't used the Acrobat Reader in Linux for a long time, so I don't know if it is still called acroread or something else.


Thank you for replying.

So.. I should of installed it in the '/bin/' folder in the root directory?

---

