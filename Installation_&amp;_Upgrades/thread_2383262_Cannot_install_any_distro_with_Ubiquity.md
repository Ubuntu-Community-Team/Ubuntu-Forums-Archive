---
title: "Cannot install any distro with Ubiquity"
date: 2018-01-22
forum: Installation &amp; Upgrades
---

### Post by RCXtest on 2018-01-22
For a few years (yes years) I have at various times tried to install Ubuntu based distros. No matter what distro, from what medium Ubiquity installer ALWAYS gives me error 5 during install.

I have burnt probably 20 DVDs over the years, including 3 yesterday: Kubuntu twice and Mint. I have checked the MD5 checksum. I have made bootable USBs. 

I can install Fedora, Puppy, Elementary, Debian.... not Ubuntu or Mint. I have tried on 2 different HDs on my desktop.

My next step, which I have never tried, is to remove my SSD  and put it in my old desktop and try to install it there.

Also tried ubiquity --no-migration-assistant but it says no such option.

Hardware issue with Ubiquity maybe? But 2 different HDs.

Any ideas? Will there be an install log somewhere?

Thanks

---

### Post by cruzer001 on 2018-01-22
You could install any flavor with the mini.iso or use the server.iso install for UEFI systems.  Neither use Ubiquity.

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by RCXtest on 2018-01-24
Thank you for the reply.

I had looked on the Kubuntu download page and there was no mention of a net install. And there is none for mint.

The mini.iso works and got me thru the install process without error 5. 

But ubuntu would still not run after install, hanging at various journal/file system errors trying to boot.

So I installed Debian again. This time with KDE just to try out plasma. Install and boot worked perfectly.

I can't mark the thread solved as this does not address the issues I have had with Ubiquity installer. I have seen other posts about error 5. Is this a hardware comparability problem with the installer? Is there a bug report?

---

### Post by cruzer001 on 2018-01-24
Have a look through here:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity](https://bugs.launchpad.net/ubuntu/+source/ubiquity)

---

