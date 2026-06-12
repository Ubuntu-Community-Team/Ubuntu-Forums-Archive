---
title: "Fresh Install - Config Files?"
date: 2012-12-12
forum: Installation &amp; Upgrades
---

### Post by EchoTech on 2012-12-12
I am replacing my HDD with an SSD and would like to do a "fresh install" after3 years of just applying upgrades..  I will be keeping my "old" Home, it's on a separate partition, and transferring it to the SSD.

  My question is about various config files in /etc I have modified, e.g. commenting out dnsmasq in Network Manager.  Should I just backup /etc and restore to the new install, try to remember what I changed, or.......?

 --Dave

---

### Post by p-dh on 2012-12-12
I have done fresh installs in the past and have tried both of the ways you mentioned. It ended up being much easier to just edit the files in /etc, using the info from the previous install. This works if you will still have access to your old HDD - in an enclosure or something.
At the end of the day, I found that I needed the changes from only a few files - most of my changes had been work-a-rounds that had been fixed in later versions. I did a fresh install on both my desktop and laptop and had them both going quickly.

Just my two cents...

Paul :cool:

---

### Post by dannyboy79 on 2012-12-12
i normally just backup all the configs from /etc/ onto a seperate drive that I will be able to access once the new install is accomplished, then open the new file and the old file side by side and copy paste what I need in case anything in the config files changed formatting or what not.

---

### Post by drmrgd on 2012-12-12
> **dannyboy79 said:**
> i normally just backup all the configs from /etc/ onto a seperate drive that I will be able to access once the new install is accomplished, then open the new file and the old file side by side and copy paste what I need in case anything in the config files changed formatting or what not.

This is exactly what I do too with both the config files in /etc as well as the hidden config files in ~/.  It goes pretty fast using these old files to configure the system as I like, and it allows me to remember what I tweaked and why I tweaked it.

---

### Post by EchoTech on 2012-12-13
Thanks for all the tips.  I'll probably have a go at it this weekend using the "compare files, copy & paste method" Thanks again

  --Dave

---

### Post by drmrgd on 2012-12-13
Just to add one more thing, if you're not familiar with the 'diff' command, have a look at the manpage for that one.  In short, you can run something like:

```
diff old_file new_file
```

That will tell you the changes between the two file and help you isolate config changes you might want to import into the new config files.

Good luck with the transfer!

---

### Post by Cheesemill on 2012-12-13
I just read through my home network documentation to see which changes I made last time and apply these to the new install :)

---

### Post by dannyboy79 on 2012-12-13
> **drmrgd said:**
> Just to add one more thing, if you're not familiar with the 'diff' command, have a look at the manpage for that one.  In short, you can run something like:

```
diff old_file new_file
```

That will tell you the changes between the two file and help you isolate config changes you might want to import into the new config files.

Good luck with the transfer!+1
also sdiff makes a side by side comparison. both these commands should be installed by default

---

### Post by EchoTech on 2012-12-14
Thanks again for the additional info.

---

### Post by EchoTech on 2012-12-16
Just to let everyone know all went well.  Everything works.  Thanks for the help.

---

