---
title: "Unattended install of 22.04 Desktop"
date: 2022-09-19
forum: Installation &amp; Upgrades
---

### Post by jonasb-to on 2022-09-19
I'm back!
But under a different username (actually my third), since I can't seem to get to terms with the Ubuntu SSO system.

I posted this last year: [https://ubuntuforums.org/showthread.php?t=2467953](https://ubuntuforums.org/showthread.php?t=2467953)

Now I'm once again trying to automate (as in hands-off, unattended) install of Desktop 22.04.

Since Ubuntu don't support preseed anymore I'm trying to look at autoinstall, but that seems to be server only - am I correct? If so, how do you autoinstall (for mass deployment) Desktop 22.04?

---

### Post by jonasb-to on 2022-09-26
One solution seems to be to autoinstall 22.04 _server_ and add the `ubuntu-desktop` package.

One question that immediately arises, and which is _not at all_ addressed in the documentation, is - how do one encrypt the boot drive during an autoinstall setup?
And a followup on that: how to do it generically, without pointing the encryption to a _specific_ serial number or WWN - since that will _only_ work for the specific machine, with the specified drive, and not for any other machine or another drive...

---

### Post by ActionParsnip on 2022-09-26
I'd make an image of a desktop system then image drives for the new system (either over LAN or just the disks themselves). You can then change the hostname in /etc/hostname and /etc/hosts, reboot and then add to domain (if required). You can then, if you like, make a new image and reimage the disks instead of updates.

Another way would be to use chef / puppet to control configuration and push it out from a central server.

---

### Post by jonasb-to on 2022-09-27
Image drives? Back to the 2000's? Autoinstall works fine for server - why not for Desktop?

---

### Post by ActionParsnip on 2022-09-27
> **jonasb-to said:**
> Image drives? Back to the 2000's? Autoinstall works fine for server - why not for Desktop?


Clearly doesn't work in IT. Imaging is alive and well for end user systems. Use server and autoinstall the desktop environment of your choice. If you use a LAN based repository rather than the Web then this will be super fast

---

