---
title: "Unbuntu Fails to Boot on SSD after clean fresh install"
date: 2022-02-19
forum: Installation &amp; Upgrades
---

### Post by hamiltra on 2022-02-19
I have attempted several times and with different flavors of Ubuntu to install on a FitPC3 but each time Ubuntu fails to find a bootable partition after the install. The hardware is a new 500GB Western Digital SSD, the board is a FitPC3 (Phoenix BIOS) (used) with 16GB RAM(new).

First attempt at install, Ubuntu 20.04.3 live server both with and without updated installer fails to produce a bootable drive. Partitions chosen were with Guided setup of complete disk with LVM.
Second attempt at install, Ubuntu 21.10 live server. Same installation steps resulted in unbootable partition.
Third attempt at install, Ubuntu 18.04.6 live server. Same installation steps resulted in unbootable partition.

Meanwhile, the Debian 11, i386 and amd64 installs are both fine.

A colleague of mine _had_ a running Ubuntu server on same FitPC3 hardware with similar SSD and memory configuration that on system upgrade_ no longer boots_.

Both could be related or different problems. If that event is determined, happy to make another post on the upgrade issue if needed.

I'm concluding a couple of things from this exercise that could be going wrong. Either the installer did not properly setup the SSD partitions or the grub boot loader is corrupted and/or not present on the boot partition. Either way, other Linux distros are configuring properly and running.

Please advise on how to correct issue or what test steps are needed next.

---

### Post by MAFoElffen on 2022-02-19
The first thing would be to boot from an Ubuntu Desktop LiveCD to install and run the 'boot-info" script (to that LiveCD)  from the yannubuntu PPA.

Once booted, use "Try" option, then start a terminal session. Then:
```

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt update
sudo apt install -y boot-info
boot-info

```
Use the Advanced option and upload to a pastebin, then post the URL of that pastebin into a post.

That is going to give us a picture of what is being installed (related to booting and Grub2) on your system, and how it is configured. That way we are not guessing on what "might be".

---

### Post by hamiltra on 2022-02-20
Performed the steps to upload to pastebin: [http://paste.ubuntu.com/p/8B7GfzdNFS](http://paste.ubuntu.com/p/8B7GfzdNFS)

---

### Post by ubfan1 on 2022-02-20
Clicking on your link I get: The Paste you are looking for does not currently exist.

---

### Post by hamiltra on 2022-02-21
Sigh, my bad. Here is the correct URL:

[https://paste.ubuntu.com/p/8B7GfzdNF5/](https://paste.ubuntu.com/p/8B7GfzdNF5/)

---

