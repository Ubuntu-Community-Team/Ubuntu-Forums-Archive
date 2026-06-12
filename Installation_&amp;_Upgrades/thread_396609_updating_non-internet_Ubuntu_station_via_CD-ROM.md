---
title: "updating non-internet Ubuntu station via CD-ROM"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2007-03-29
I am wanting to setup a demo installation of Ubuntu on an old computer at work (**so** **that my fellow employees there can see what they are missing out on**) which does NOT have an internet connection.

Can someone give me a synopsis of how to pull the updates as they become available on my home Ubuntu computer to a CD-RW and how I would the go about loading them to the computer at work ?

If there is a write-up on this already can you point me to it or tell me what expression(s) to use for a search ?

Thanks.

---

### Post by ricflomag on 2007-03-29
This thread might help:

[http://ubuntuforums.org/showthread.php?t=310020](http://ubuntuforums.org/showthread.php?t=310020)

---

### Post by ricflomag on 2007-03-29
Maybe you could try to burn everything from /var/cache/apt/ to a CD (from an up-to-date internet connected computer) and copy it to the same place to your computer that doesn't have internet. This directory contains a cache of all downloaded .debs files and also the cache of the packages list.

Then see if "sudo apt-get upgrade" works.

I know it works for the .deb files (they don't get downloaded if they are present in the cache) but i don't know for the package list. I often copy the deb files to a computer that has a dial-up internet connection: just use the internet to update the package list and then spare much time by getting the deb files from the cache...

Hope it helps...

---

