---
title: "Can't find build-essential"
date: 2008-10-19
forum: Installation &amp; Upgrades
---

### Post by amup on 2008-10-19
Hello, I am new to ubuntu and am very confused.  I downloaded the server version and installed on an old thinkpad 600e laptop so that I can play with it to learn linux. 

The biggest issue is getting internet access right now with my belkin wireless pcmcia modem.  I think I need to install ndiswrapper.  But It can't find it.

So reading through as many threads here as possible, I think I need to install build-essential. It can't find that either.

I have mounted the cdrom.  I see the cdrom in the sources.list.  yet I can't get it to install either ndiswrapper or build-essential.

I use sudo apt-get install build-essential or sudo aptitude install build-essential.  Neither can find it.

The cd was made from the download and I did a cdrom check before installing and all was fine.

I'm at a loss here.  I find alot of people with the problem over the years in these threads but there is never a resolution that I can see.

Please help with detailed instructions please as I am a newbie.

Thanks so much.

---

### Post by oldos2er on 2008-10-19
Can you please post the output of "cat /etc/apt/sources.list"?

---

### Post by amup on 2008-10-19
Thanks for your reply. Obviously I'm much more together in the morning.  I looked at the sources.list file again and finally noticed that the cdrom line was commented out with a # sign.  So I took out the #.  And it worked, sort of.  

(I am unable to post anything here as it is on a different machine that doesn't yet have internet access.  I haven't figured out how to get it to read the USB memory thing yet).

Anyway, during the build-essential install I got some errors:

Buffer I/O error on device sr0 
and
Failed to fetch cdrom:[Ubuntu blah blah  /pool/main/l/linux/linux-linux-libc-dev_2.6.24-19.34_i386.deb Hash Sum mismatch
and same error for make

And at the end it said: Unable to fetch some archives, maybe run apt-get update or try with -fix-missing?

edit:  the second time around it was able to fetch 'make' but not the 
'libc' and seem to finish ok

Now however it cannot find 'ndiswrapper' or 'ndiswrapper-common' or 'ndiswrapper-utils'

---

### Post by amup on 2008-10-19
So I burned a new cd at 8x speed and it works find to install build-essential.

Now I need ndiswrapper-utils and it can not find it.  I have tried ndiswrapper, ndiswrapper-common, ndiswrapper-utils with and without the 's'.

---

### Post by oldos2er on 2008-10-19
Try reading this: [http://ubuntuforums.org/showthread.php?t=734003](http://ubuntuforums.org/showthread.php?t=734003)

---

