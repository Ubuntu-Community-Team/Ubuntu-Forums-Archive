---
title: "[SOLVED] Update error"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by solitaire on 2008-02-13
I'm running the updates and there is a single update that fails to install:

"linux-headers-2.6.22-14-generic"

```

E: /var/cache/apt/archives/linux-headers-2.6.22-14-generic_2.6.22-14.52_i386.deb: unable to stat `./usr/src/linux-headers-2.6.22-14-generic/include/config/dvb' (which I was about to install)

```

It looks like it's having a problem with a DVB device i did install one but it's not plugged in.

any ideas?

---

### Post by solitaire on 2008-02-13
Bump

anyone got any ideas?

---

### Post by solitaire on 2008-02-14
How do you set the permissions for the /usr/src/* folders?

I'm trying to install the "linux-headers-2.6.22-14-generic" update but I am getting an error saying "Permission denied" when running the update :
```

"./usr/src/linux-headers-2.6.22-14-generic/include/config/dvb" unable to stat (Which i was about to install) : Permission denied"

```

---

### Post by dgermann on 2008-02-14
solitaire--

When I run into permission denied errors, sometimes running with sudo does work. Not sure, but there are times when that is not safe and you need to use gksudo. eg: sudo apt-get ....

disclaimer: I have no knowledge about these things, I sometimes only experiment. So take what I offer with a grain of salt.

Good luck!

---

### Post by solitaire on 2008-02-14
I'll check that out in the morning :D

Thanks!

---

### Post by solitaire on 2008-02-14
No luck! here is the output
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-headers-2.6.22-14-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/581kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 121008 files and directories currently installed.)
Preparing to replace linux-headers-2.6.22-14-generic 2.6.22-14.51 (using .../linux-headers-2.6.22-14-generic_2.6.22-14.52_i386.deb) ...
Unpacking replacement linux-headers-2.6.22-14-generic ...
dpkg: error processing /var/cache/apt/archives/linux-headers-2.6.22-14-generic_2.6.22-14.52_i386.deb (--unpack):
 unable to stat `./usr/src/linux-headers-2.6.22-14-generic/include/config/dvb' (which I was about to install): Permission denied
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.22-14-generic_2.6.22-14.52_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by dgermann on 2008-02-14
solitaire--

Well, you might try your intuition and chmod the files and directories it is referring to.

Before I did that, I would man apt-get and see if there is some way to get it to move past errors. Seems to me there is some way to force an install.

Again, I am doing a lot of guessing.

Have you tried posting at other forums, such as linuxquestions or justlinux?

---

### Post by solitaire on 2008-02-14
Checked the folder and it does not exists.
I tried  to create it using 
```
Sudo mkdir dvb 
```
But said "permission denied"

Tried using the following
```

sudo apt-get --force-yes dist-upgrade

```
But i get he same error as in my last post.

I'll be posting the problem to other sites now!

---

### Post by dgermann on 2008-02-16
solitaire--

Be sure to report back when you find the soltuion, so others can learn from your experience.

---

### Post by solitaire on 2008-02-18
I finally worked out how to fix the problem ( by typing commands randomly! :/ ) lol!!

in effect i managed to give "root" full privilages to the "/usr/src/linux-headers-2.6.22-14-generic" folder and moved it to a new backup folder.
I then ran the update again and it worked with no errors.

i just need to get rid of the backup folder :D

thanks for all your suggestions.

---

### Post by dgermann on 2008-02-18
solitaire--

Who would have thought?!

Congratulations!

---

### Post by solitaire on 2008-02-18
typing random commands while root does work form time to time...

*Note*
just make sure you got a good backup first lol!! :D

---

