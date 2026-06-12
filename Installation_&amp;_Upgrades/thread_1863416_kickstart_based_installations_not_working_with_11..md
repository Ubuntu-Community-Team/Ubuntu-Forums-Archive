---
title: "kickstart based installations not working with 11.10"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by netllama on 2011-10-17
Greetings,
I run a large server farm (several hundred systems), where I need to frequently perform automated, kickstart based installations of assorted Linux distributions.  I've been doing this with Ubuntu since the 7.xx days, and its usually mostly worked fine.  

However, since 11.10 came out, I cannot get any kickstart based installation to work at all.  It appears that the layout & design of the installation ISO images has changed dramatically, such that they no longer include the standard pool/main/* packages, and have instead seemingly stuffed all of them into some squashfs file.  

The basic process that I've followed for all previous versions (up to & including 11.04) was to:
0) Download the OS DVD ISO 
1) Extract its full contents, as-is, on a web server
2) Create a kickstart file and put it on the web server
3) Grab the netboot kernel & initrd from the extracted content, and boot the target system(s), with appropriate parameters.  For example:
vga=normal ramdisk_size=16384 ks=http://10.31.40.58/distros/ubuntu/os/x86_64/11.04/ks.cfg root=/dev/rd/0 rw -


With 11.10, step 3 fails miserably, reporting "There are no packages matching the running kernel 3.0.0-12-generic in the archive".  Which is true, because the 11.10 ISO images ships with almost no packages at all, which happens to include the lack of a 'linux' kernel package.

I've spent a chunk of time googling for an answer, but kickstart seems to be the red-headed step child feature in Ubuntu, and barely gets documented at all, even when it is working ok.  Hopefully there's some relatively trivial solution for this?

thanks

---

