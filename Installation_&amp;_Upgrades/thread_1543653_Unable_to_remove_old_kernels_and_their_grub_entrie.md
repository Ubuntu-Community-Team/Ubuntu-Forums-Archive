---
title: "Unable to remove old kernels and their grub entries"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by peterv6 on 2010-08-01
I have a grub menu with a ton of old kernel entries that I want to delete.  I've scoured this forum, and haven't found anything that works.  I've tried:```

"the easiest way to get rid of old kernels from grub is to uninstall the package, 
the post-install scripts will update grub

for example my current kernel is:

uname -a
Linux hemma 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux

then remove older kernels found in /boot like this:

sudo aptitude remove linux-image-2.6.31-15-generic"
```

When I tried that, the output showed the package being removed, but nothing was removed from the grub menu.  I tried running the kernel I supposedly removed, and it wouldn't start, which is promising, but how do I get it out of the grub menu?  I've also tried using Synaptic, but that didn't work either.

---

### Post by Rubi1200 on 2010-08-01
> **peterv6 said:**
> I have a grub menu with a ton of old kernel entries that I want to delete. I've scoured this forum, and haven't found anything that works. I've tried:```

"the easiest way to get rid of old kernels from grub is to uninstall the package, 
the post-install scripts will update grub
 
for example my current kernel is:
 
uname -a
Linux hemma 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:02:15 UTC 2009 x86_64 GNU/Linux
 
then remove older kernels found in /boot like this:
 
sudo aptitude remove linux-image-2.6.31-15-generic"
```
 
When I tried that, the output showed the package being removed, but nothing was removed from the grub menu. I tried running the kernel I supposedly removed, and it wouldn't start, which is promising, but how do I get it out of the grub menu? I've also tried using Synaptic, but that didn't work either.
Did you run```
 sudo update-grub 
```yet in the terminal?
 
Also, there are 2 linux headers files associated with each kernel version that also need to be removed (I suggest using Synaptic for this).

---

### Post by peterv6 on 2010-08-01
Yes, I ran sudo update-grub.  I did remove the headers files with Synaptic, but I did this after I had already removed the kernel using synaptic.  (I didn't know about the headers at first.)  The grub menu still shows the kernel that I deleted.

---

### Post by sinurge on 2010-08-01
Another way is to get this app Ubuntu Tweak ..there is an option to clean Kernals, select the ones to remove and it runs update-grub automatically so that should solve your issue.

Synaptic is also a recommended way

---

### Post by drs305 on 2010-08-01
Take a look at the /boot/grub/grub.cfg file and see where the extra kernels are located. The grub.cfg file is divided into sections. There is a 10_linux section for the current OS, and there is also a 30_os-prober section which incorporates kernels from other partitions, as well as listings in other menu.lst and grub.cfg files.

If the kernels are located in the 30_os-prober section you may need to do a search of your other partitions for offending kernels and grub configuration files.

I've found the easiest way to uninstall kernels and remove them from the Grub menu is to use Ubuntu-Tweak. If you want to read a short bit about how to install and use it, refer to the "Removing older kernels" section of this thread:
[HOWTO: StartUp Manager & Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by sinurge on 2010-08-03
I Agree with drs on how to remove this but any mess up there and basically grub is a gonner. Hence the suggestion of ubuntu-tweak

---

### Post by ahbart on 2010-08-03
> **drs305 said:**
> I've found the easiest way to uninstall kernels and remove them from the Grub menu is to use Ubuntu-Tweak. If you want to read a short bit about how to install and use it, refer to the "Removing older kernels" section of this thread:
[HOWTO: StartUp Manager & Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

@drs305: You suggest using Ubuntu-tweak and refer to startupmanager?! :confused:

@Peterv6: I use the last one: startupmanager. You can find it in synaptic. You can even limit the number of kernel lines in there. very useful.

---

### Post by drs305 on 2010-08-03
> **ahbart said:**
> @drs305: You suggest using Ubuntu-tweak and refer to startupmanager?! :confused:


The linked thread deals with hiding kernels in the Grub menu. StartUp-Manager is one method, especially with Grub Legacy. 

Later in the post, in the section "Removing older kernels" is a section describing how to install Ubuntu-Tweak and use it to remove the older kernels. Linux usually has more than one way to do things.

---

### Post by ahbart on 2010-08-03
@drs305, Sorry You are right.

---

