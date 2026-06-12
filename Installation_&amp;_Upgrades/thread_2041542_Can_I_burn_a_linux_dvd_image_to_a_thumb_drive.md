---
title: "Can I burn a linux dvd image to a thumb drive?"
date: 2012-08-12
forum: Installation &amp; Upgrades
---

### Post by sofasurfer on 2012-08-12
Can I burn a linux dvd image to a thumb drive? I'm out of DVDs but I do have a thumb drive. How can I do this?

---

### Post by ajgreeny on 2012-08-12
Use unetbootin, available in the repos.  If it is a ubuntu family OS you can also use USB startupdisk creator, in your menu.

---

### Post by uRock on 2012-08-12
> **sofasurfer said:**
> Can I burn a linux dvd image to a thumb drive? I'm out of DVDs but I do have a thumb drive. How can I do this?

This is how I do it,> **cariboo907 said:**
> Just to add a bit of info as far as the command options go,

if = input file
of = output file

You can also use the same command to create an iso image of a cdrom for example:

```
dd if=/dev/sr0 of=name_of_cdrom.iso
```

I used to create and store iso images of cdroms that I use all the time, as they are so susceptible to damage.

---

### Post by sofasurfer on 2012-08-18
I just installed unetbootin. Looks like just what I need. But, it does not list 12.04 as an option. How to I do dat?

---

### Post by sofasurfer on 2012-08-18
Never mind. I found out how. I have it installed on USB now. Will try running it a little later.

---

### Post by sofasurfer on 2012-08-18
I had to go to BIOS and set USB to run as DVD and as 1st boot option (I hope thats the correct terminology). Then I rebooted and I got a blank screen with a prompt and it just did nothing more than that.

My partitioning looks like this...

---

