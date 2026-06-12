---
title: "should I be worried about this?"
date: 2016-05-10
forum: Installation &amp; Upgrades
---

### Post by chopra on 2016-05-10
I hope this is a quick problem to solve.  After a recent upgrade, in which the /boot/ directory was updated with the following files,
-rw-------  1 root root  5833888 May 10 11:25 vmlinuz-3.13.0-86-generic
-rw-------  1 root root  3393573 May 10 11:25 System.map-3.13.0-86-generic
-rw-r--r--  1 root root   165918 May 10 11:25 config-3.13.0-86-generic
-rw-r--r--  1 root root  1166060 May 10 11:25 abi-3.13.0-86-generic

a restart was required.  Before the restart, though, there was an error message about an update to some audio package not installing properly.  I wish I'd copied and pasted the error report, but I just hit "send error report" and it went away.
Anyway, I restarted, and everything was fine, I ran the software updater again, and it said everything was up to date, which confused me because the package supposedly hadn't updated.  Perhaps it updated on its own?
Anyway, in my root directory, there are two broken links:
lrwxrwxrwx 1 root root 33 May 10 11:25 initrd.img -> boot/initrd.img-3.13.0-86-generic
lrwxrwxrwx 1 root root 33 May 10 11:25 initrd.img.old -> boot/initrd.img-3.13.0-86-generic

I don't know what happened, but my natural inclination is to just run:
sudo apt-get install linux-image-3.13.0-86-generic
but I didn't know if doing that manually would screw anything up, as it isn't prompting me to. 
I also don't know if I need to as there weren't any problems with the restart.

Chopra

---

### Post by Bucky Ball on 2016-05-10
Do this:
```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Any errors? So far so good. When you say the kernels are broken, what do you mean? When you boot them, they don't work? 

Which release and flavour of Ubuntu are you using?

---

### Post by chopra on 2016-05-10
Thanks for the reply.  What I had said was that the links were broken.  In other words, the symbolic links that are in the root directory pointed to nonexistent files, but it wasn't causing any problems.
I don't know why it would update the symlinks and not create the files. 
Anyway, I ran the commands you mentioned, and no errors occured.
 
In the process, it created:
 boot/initrd.img-3.13.0-86-generic

so the links aren't broken anymore.  Thanks.
Not sure what happened.

Chopra

---

### Post by Bucky Ball on 2016-05-10
All good. Please mark the thread as solved if you're happy. This will not close the thread to further discussion. ;)

---

