---
title: "kernel update"
date: 2010-12-31
forum: Installation &amp; Upgrades
---

### Post by pr3zident on 2010-12-31
I have researched everywhere(i think) to try and find a simple way of updating my kernel (which is 2.6.35-24-generic) to linux-2.6.36.2.tar.bz2 hopefully which is the right thing to do..can someone please give me clear instructions on how to do so ?

---

### Post by snowpine on 2010-12-31
Welcome to the forums!

First off can you back up a step and explain your reasons for wanting to use a newer, unsupported kernel? (so we can answer your "is it the right thing to do?" question) While the Ubuntu kernel is not the latest and the greatest, it does receive constant bug fixes and security patches, therefore it certainly cannot be said it is "outdated." (I personally use kernel 2.6.18 on my work computer, if it makes you feel better. :))

Second, a .tar.bz2 file is an archive (like .zip in Windows) that usually contains source code. I guess this means you want to compile your own kernel for some reason (see my first question above). [Here are instructions for compiling a kernel in Ubuntu]("https://help.ubuntu.com/community/Kernel/Compile").

Third, a much easier way to get a newer kernel is from [the Ubuntu Kernel PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"). These are in .deb file format (not source code) which means you can install them using the GUI package manager simply by downloading and clicking (the "Windows way"). Just make sure you choose the correct .deb's for your architecture (amd64 or i386) and install the appropriate linux-image package. (You might also want the linux-header packages if you are a developer or need to compile your own modules.)

To summarize, you can certainly use a newer kernel in Ubuntu if you wish, there are several methods for doing so, and you will be responsible for your own support/upgrades/security since you won't be using the supported kernel any more. Good luck!

---

### Post by pr3zident on 2010-12-31
awwwwwww mannnnnn i was in the middle of updating to the new kernel then i closed the terminal soooo, is this somehow some way going to mess up my computer when i turn it off..

lol thanx for the reply i just like updating stuff smh...

---

### Post by snowpine on 2010-12-31
I'm not sure what exactly you were doing in the terminal, but have you tried simply repeating the commands to finish the process?

---

### Post by pr3zident on 2010-12-31
Sorry for the late responses I'm having all type of internet issues but ok here is what I did, I downloaded the kernel tar file, I extracted it and then cd to it, after that make oldconfig, make dep, make dzImage, and after that it did a bunch of things that took long but b4 it finish I cancelled it...
Note: I want to keep the kernel I have currently, but I'm scared to shutdown my cpu fearing that all my files will be deleted O_O is everything going to be ok I need some type of hope !?

---

### Post by snowpine on 2010-12-31
Adding a new kernel will not delete your old kernel. You will still be able to select the old kernel from the GRUB boot menu if something goes wrong with the new one.

---

### Post by pr3zident on 2010-12-31
Thanx my ubuntu brother lol that's the knowledged I needed !

---

### Post by snowpine on 2010-12-31
Any time! :)

---

### Post by islandBilly on 2011-01-20
> **snowpine said:**
> Welcome to the forums!

First off can you back up a step and explain your reasons for wanting to use a newer, unsupported kernel? (so we can answer your "is it the right thing to do?" question) While the Ubuntu kernel is not the latest and the greatest, it does receive constant bug fixes and security patches, therefore it certainly cannot be said it is "outdated." (I personally use kernel 2.6.18 on my work computer, if it makes you feel better. :))

Second, a .tar.bz2 file is an archive (like .zip in Windows) that usually contains source code. I guess this means you want to compile your own kernel for some reason (see my first question above). [Here are instructions for compiling a kernel in Ubuntu]("https://help.ubuntu.com/community/Kernel/Compile").

Third, a much easier way to get a newer kernel is from [the Ubuntu Kernel PPA]("http://kernel.ubuntu.com/~kernel-ppa/mainline/"). These are in .deb file format (not source code) which means you can install them using the GUI package manager simply by downloading and clicking (the "Windows way"). Just make sure you choose the correct .deb's for your architecture (amd64 or i386) and install the appropriate linux-image package. (You might also want the linux-header packages if you are a developer or need to compile your own modules.)

To summarize, you can certainly use a newer kernel in Ubuntu if you wish, there are several methods for doing so, and you will be responsible for your own support/upgrades/security since you won't be using the supported kernel any more. Good luck!
I hope it's okay to jump in here. The reason I would want to update my kernel (I'm running 2.6.35-24, Maverick) is because I read that I can get support for my Acer Aspire ENE multi card reader if I upgrade to 2.6.37-6. Does that make sense? I have been wondering exactly how one does this, and so it looks like I can go to that link and download it, then click to get the package manager to install it, right? sounds easy...

---

### Post by randiroo76073 on 2011-01-21
@ islandbilly
I've a desktop and just uped to 2.6.37.12 on maverick(10.10) as it was in synaptic yesterday. So far so good, but still keeping a close eye. Sometimes it'll break you, but you can flip back to previous kerenel if it does :)

---

### Post by snowpine on 2011-01-21
> **islandBilly said:**
> I hope it's okay to jump in here. The reason I would want to update my kernel (I'm running 2.6.35-24, Maverick) is because I read that I can get support for my Acer Aspire ENE multi card reader if I upgrade to 2.6.37-6. Does that make sense? I have been wondering exactly how one does this, and so it looks like I can go to that link and download it, then click to get the package manager to install it, right? sounds easy...

Sounds like a plan, good luck! :)

---

### Post by islandBilly on 2011-01-21
Thanks, randiroo, I decided to go to that PPA page and downloaded the generic 2.6.37 package. clicking it brought up the installer, as promised, though it was not Synaptic as I thought it would be. Anyway, the install went fine, and as with you, all is well so far - AND the thing instantly recognized my sd card when I put it into the reader, no problem.

Well, there was a bit of a problem when I went to safely remove it. I did that by right clicking the desktop icon it had put up when it saw the card. It gave a message about not being able to stop the disk, but going on anyway. It did unmount it, and I removed the card, with no harm to it.

The only other wrinkle here is that I downloaded the header file, although it did not seem necessary. I have no intention of working on the kernel myself, being more of an application-level guy. Anyway, when I clicked on that package, the installer said there was an unresolvable dependency problem. So I just tried doing without it, and as I say, it seems to work very well. So far. I think the machine may even be doing things faster than before :D

---

