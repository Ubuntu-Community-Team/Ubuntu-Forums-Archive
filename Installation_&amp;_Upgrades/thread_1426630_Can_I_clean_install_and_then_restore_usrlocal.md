---
title: "Can I clean install and then restore /usr/local?"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by desconocido on 2010-03-10
I currently run Ubuntu 8.04 and have installed quite a lot of software, often without using synaptic (latest versions of wine, open office, zilla, addons, plugins etc). I am not entirely sure that I have documented everything I have installed.

I would like to upgrade to say, Ubuntu 9.10. Could I do this by saving /home and /usr/local to backup; doing a clean install of 9.10; copying back /home and /usr/local. Would that work?

Or would my applications have lots of their files spread over lots of other directories? And would there be something new and important in /home that would get overwritten by the old stuff?

---

### Post by jjcv on 2010-03-11
For /home it is just a matter or restoring everything back once you have installed.   I usually use a separate partition for /home and at a reinstall I simply tell it to reuse my /home and mark it not to reformat this partition.

It is hard to say if everything in /usr/local will continue to work.  It depends on if you compiled them and installed their libraries in /usr/local also and if they are still compatible with the new version you are going to install.

You could always boot off the CDROM, mount the old /usr/local and see if any of the programs will run.

It is a good idea to keep sources of these programs around so that you can reinstall them if necessary.  Perhaps a /home/src or /usr/local/src directory.

---

