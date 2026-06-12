---
title: "Cannot add/upgrade packages"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by Jiokah on 2006-11-26
Hi,

Although I have bit of experience with other distributions and linux in general, I have not used Ubuntu prior to a couple hours ago.

Using either apt-get in the command-line or Synaptic Package Manager in X, I always recieve the same error when trying to install or update a package:

```
dpkg: parse error, in file '/var/lib/dpkg/available' near line 2 package 'libdevian-install4':
 value for 'status' field not allowed in this context
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:
```

After a little bit of research online, I've discovered this error is due to the fact that gcc is not installed. All I need to do is install gcc to fix the problem. The problem is, though, I need gcc to install gcc. How do I get around this? Can I install gcc seperate from apt?

Thanks a lot for the help!

-Matthew

---

### Post by taurus on 2006-11-26
```
sudo aptitude install build-essential <-- to install gcc...
-or-
sudo aptitude -purge libdevian-install4 <-- to remove it...
```

---

### Post by Jiokah on 2006-11-26
Thanks for your reply, but installing gcc using that line will not work, I get the same error message. Like I said, gcc needs to be installed for aptitude to work.

How do I install gcc without aptitude or Synaptic Package Manager?

---

### Post by taurus on 2006-11-26
What if you remove that package, libdevian-install4, first!!!

---

### Post by Jiokah on 2006-11-26
Hey, I had typed out the above error message and had mispelled that package, here's the copied and pasted error:
```

dpkg: parse error, in file `/var/lib/dpkg/available' near line 2 package `libdebian-installer4':
 value for `status' field not allowed in this context
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: parse error, in file `/var/lib/dpkg/available' near line 2 package `libdebian-installer4':
 value for `status' field not allowed in this context
```

"libdebian-installer4" isn't actually installed, and I get the same error message as above when trying to install it, or any other package. Both of your commands do not work (including the second one with a properly spelled package and purge without the dash). Any suggestions?

Thanks a lot!

-Matthew

---

### Post by bapoumba on 2006-11-27
Hi,

your dpkg database is corrupted. You can save the actual /var/lib/dpkg/status corrupted file (just in case) and use the previous one : 
**sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status**
You probably will have to reinstall the last packages you installed just before the problem occured. There may be a better way to fix dpkg database that I am not aware of. (check line 2 in your actual status file). Cheers :)

---

### Post by Jiokah on 2006-11-27
Corrupted eh? Well I hadn't changed any packages at all. I had installed ubuntu 6.06 fresh, then went straight to packages without doing anything else and got this error. Ubuntu was a quick install, I'll just re-install it and see if that helps. I must of done something wrong during the process the first time.

---

