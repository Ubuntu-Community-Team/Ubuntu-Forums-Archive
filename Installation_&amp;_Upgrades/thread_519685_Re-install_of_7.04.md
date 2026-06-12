---
title: "Re-install of 7.04"
date: 2007-08-07
forum: Installation &amp; Upgrades
---

### Post by FreeSoul on 2007-08-07
It's come down to a re-install. I am running 7.04 in a dual boot config. I lost my sound trying to get my mic to work using the Realtek 4.06a audiopack. I don't know what to do, have tried many fixes but the realtek install hosed my system. Can I somehow remove a command line install?

If not, if I reinstall Ubuntu but don't reformat my home directory will I still retain my audio and video files? Any links or pointers for doing this? ie. What happens to software previously installed in my home dir?

Much thanks,
FreeSoul

---

### Post by wjp.reg on 2007-08-07
> **FreeSoul said:**
> It's come down to a re-install. I am running 7.04 in a dual boot config. I lost my sound trying to get my mic to work using the Realtek 4.06a audiopack. I don't know what to do, have tried many fixes but the realtek install hosed my system. Can I somehow remove a command line install?

If not, if I reinstall Ubuntu but don't reformat my home directory will I still retain my audio and video files? Any links or pointers for doing this? ie. What happens to software previously installed in my home dir?

Much thanks,
FreeSoul

Try it and see, if you don´t reformat it will still be there :-)

You may have to reinstall or reconfigure some things you installed in your home folder but most of the configuration settings should hold.

---

### Post by dabl on 2007-08-07
> **FreeSoul said:**
> 

If not, if I reinstall Ubuntu but don't reformat my home directory will I still retain my audio and video files?

For future reference, if you make a separate disk partition for /home, then you never have to worry about this problem.

>   What happens to software previously installed in my home dir?
FreeSoul

The answer is not different for software packages or audio video files.  (Actually, you DON'T have software "installed" in your /home directory, but that's a technicality, I guess). 

If you have only a single partition in which to install the root directory and everything else including /home, then it's all toast when you re-install. That's why you should make /home a separate partition on the hard drive.

BTW, although I know nothing about your microphone or sound system, that is NOT they type of problem that would normally cause one to think of re-installing a Linux system. (The answer is different in Windows, of course).  Are you sure you don't want to simply remove and re-install the applicable sound packages (alsa-base or whatever you're using)?  :confused:

---

### Post by FreeSoul on 2007-08-07
> **dabl said:**
> For future reference, if you make a separate disk partition for /home, then you never have to worry about this problem.



The answer is not different for software packages or audio video files.  (Actually, you DON'T have software "installed" in your /home directory, but that's a technicality, I guess). 

If you have only a single partition in which to install the root directory and everything else including /home, then it's all toast when you re-install. That's why you should make /home a separate partition on the hard drive.

BTW, although I know nothing about your microphone or sound system, that is NOT they type of problem that would normally cause one to think of re-installing a Linux system. (The answer is different in Windows, of course).  Are you sure you don't want to simply remove and re-install the applicable sound packages (alsa-base or whatever you're using)?  :confused:

Thanks for the reply(ies), I tried fixing my problem by going through the long process of (I forget the name, but it was a sound check process to fix your sound, through this site) and some other suggestions and links. 

If someone could point me in the direction of how to just uninstall the realtek audiopack,  I would be stoked. I tried finding it online but to no avail. It was done from the command line.

I basically ran this:
> $ tar xvjf realtek-linux-audiopack-4.06a.tar.bz2
$ cd realtek-linux-audiopack-4.06a/
$ ./install

There appeared to be errors during the install, lost my sound, and couldn't find how to undo the package. (Perhaps under my nose).


By the way, I do have my /home dir on it's own partition, I did it right this time. Perhaps I could have worded it better, just worried about losing it during install. It still would be allot of work to get my machine back up and running correctly after an install ( - home). I just feel their will be loose ends to find. And I'm not nearly as familiar with Linux now as I was 6 years ago when I last worked in IT.

Much appreciated,
FreeSoul

---

