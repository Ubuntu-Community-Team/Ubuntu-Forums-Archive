---
title: "After upgrade from 18.04 to 22.04 system will not boot and no wifi"
date: 2023-01-16
forum: Installation &amp; Upgrades
---

### Post by James Wilde on 2023-01-16
I upgraded my Ubuntu 18.04 to 22.04.  Had hoped to upgrade but that option was not offered so I had to reinstall.  After install I had a lovely desktop, but couldn't get a copy of dmesg to see why the wifi card had not loaded.  I discovered that no users had been created notwithstanding that I created one in the installation process.  After creating two users I decided I would have to reboot and log in as one of them (no login och switch user options available). After restarting I got the following messages:

System BootOrder not found. Initializing defaults.
Creating boot entry "Boot0072" with label "ubuntu" for file "\EFI\ubuntu\shimx64.efi"

And then, after a very long time it drops me into a grub prompt.

I've been away from computer technology for a long while, so I would much appreciate some help.  If nothing else, I would like to see the dmesg to find out what happened to my wifi card.

Thanks in advance

---

### Post by James Wilde on 2023-01-16
Further to the above, I have now reloaded (but not tried to install) from the DVD.  This time I noted that there was no problem with the wifi, other than that it needed the password. In other words, there is no problem with drivers for the wifi card on the DVD.

---

### Post by James Wilde on 2023-01-18
Same DVD same DVD reader, same USB port - this time the installation worked.  So problem solved.

---

