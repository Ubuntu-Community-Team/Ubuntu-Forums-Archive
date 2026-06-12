---
title: "My kernel corrupted"
date: 2010-12-19
forum: Installation &amp; Upgrades
---

### Post by familyguy.02 on 2010-12-19
I recently updated my Linux kernel to version 2.6.35-23-generic. It worked great until a power outage cause it to become corrupt on my hard drive; when I try to boot into that kernel now, I am faced with many error messages. I am able to boot my machine into the older Linux kernel (2.6.35-22) but I can not install any programs or update my kernel, for it is already the latest version. What can I do?
Thanks in advance
Dakota

---

### Post by I'mGeorge on 2010-12-19
if you say you have an older kernel available use it and with synaptic uninstall and reinstall the corrupted kernel, and after reboot try to use it again.

---

### Post by familyguy.02 on 2010-12-19
Thanks, I tried that. When I attempted to install the linux image (it said that it wasn't installed) I got an error message..

```
Selecting previously deselected package linux-image.
(Reading database ... 55%dpkg: unrecoverable fatal error, aborting:
 failed to read on buffer copy for files list for package `linux-headers-2.6.35-23': Input/output error
E: Sub-process usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:
```

Any ideas?

---

### Post by tgalati4 on 2010-12-19
You might have some disk damage.  Try renaming the corrupt kernel to a different name, then reinstall.

Do an fsck using a Live CD and install smartmontools.


Then get an UPS.

---

### Post by I'mGeorge on 2010-12-20
> **familyguy.02 said:**
> Thanks, I tried that. When I attempted to install the linux image (it said that it wasn't installed) I got an error message..


Do ```
sudo gedit /var/lib/dpkg/statoverride
```and put # in front of the lines that might contain postfix. If that doesn't works you could also comment all the lines except for ```
hplip root 755 /var/run/hplip
``` 

Anyway here's where you could read more about it
[http://ubuntuforums.org/archive/index.php/t-329560.html](http://ubuntuforums.org/archive/index.php/t-329560.html)
[http://ubuntuforums.org/showthread.php?t=508679](http://ubuntuforums.org/showthread.php?t=508679)

Cheers

---

### Post by hscottyh on 2011-01-19
I was getting:

Selecting previously deselected package linux-image.
(Reading database ... 75%dpkg: unrecoverable fatal error, aborting:
 failed to read on buffer copy for files list for package `linux-headers-2.6.35-23': Input/output error
E: Sub-process usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:

I removed the following file by doing the following:

Saved the file to my home directory just in case I needed to put it back:
cp /var/lib/dpkg/info/linux-headers-2.6.28-15-generic.list ~/

Then removed the following file:
sudo rm /var/lib/dpkg/info/linux-headers-2.6.28-15-generic.list

After removing the file, I was able to update, but was getting a warning. Then I did:
sudo apt-get remove linux-headers-2.6.28-15-generic

This seemed to fix me completely. I didn't need the package since it was from an old kernel, but if it is your current kernal you should reinstall it by:

sudo apt-get update linux-headers-2.6.28-15-generic

I'm not sure this would fix every problem from this sort of message. It's just what worked for me. I thought I should post this, since I couldn't find any solution that would fix me in the forums.

---

