---
title: "Lots of options/OS versions in Grub - needed?"
date: 2013-02-09
forum: Installation &amp; Upgrades
---

### Post by HughJarse on 2013-02-09
After regular updates there is now a large number of options when Grub comes up. (Grub 1.98)
I have two HDDs one with many versions of 10.04

> System.map-2.6.32-21-generic
System.map-2.6.32-22-generic
System.map-2.6.32-23-generic
System.map-2.6.32-24-generic
System.map-2.6.32-25-generic
System.map-2.6.32-26-generic
System.map-2.6.32-27-generic
System.map-2.6.32-28-generic
System.map-2.6.32-29-generic
System.map-2.6.32-30-generic
System.map-2.6.32-31-generic
System.map-2.6.32-32-generic
System.map-2.6.32-33-generic
System.map-2.6.32-34-generic
System.map-2.6.32-35-generic
System.map-2.6.32-36-generic
System.map-2.6.32-37-generic
System.map-2.6.32-38-generic
System.map-2.6.32-41-generic
System.map-2.6.32-42-generic
System.map-2.6.32-43-generic
System.map-2.6.32-44-generic
System.map-2.6.32-45-generic

There is a similar list underneath for 12.04 LTS.
Question is can I removed these old files from the **boot** folder as I will always select the latest version anyway.

---

### Post by MadmanRB on 2013-02-09
Yes you can remove old kernels, most of the time old kernels are given to aid in any bad updates to the OS.
You can even do it with ubuntu tweak.

---

### Post by ahallubuntu on 2013-02-09
~

---

### Post by QIII on 2013-02-09
I will typically leave at least the previous kernel installed in case something goes wrong with the current one.  That will gives you a backup plan.

Some folks suggest two back.

So get rid of the oldest and keep at least the previous one.

---

### Post by HughJarse on 2013-02-10
Ok, next question. How and which files do you delete?
I looked for 'tweak' but can't find it.

---

### Post by sammiev on 2013-02-10
[Ubuntu Tweak]("https://launchpad.net/ubuntu-tweak/+download")

---

### Post by Bucky Ball on 2013-02-10
Grub Customizer is your friend.

[http://ubuntuforums.org/showthread.php?p=10340183](http://ubuntuforums.org/showthread.php?p=10340183)

---

