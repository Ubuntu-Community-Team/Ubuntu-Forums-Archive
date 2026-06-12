---
title: "Opera repository error"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by zamolxis on 2010-11-29
I recently updated an older notebook in dual boot with Windows from 8.04 to 10.10. I kept /home which was on an older partition and reformatted / to ext4. So far so good, everything is perfect, except that I cannot install Opera. I installed the repository according to the community wiki but it does not seem to work. I could download the .deb and install it manually, but I cannot understand what is wrong with the repository - it works on my other computers.

```

$ tail /etc/apt/sources.list
...
deb http://deb.opera.com/opera/ stable non-free
deb-src http://deb.opera.com/opera/ stable non-free
$ sudo apt-get update
...
Fetched 490B in 2s (233B/s)
W: Failed to fetch http://deb.opera.com/opera/dists/stable/Release  Unable to find expected entry  non-free/source/Sources in Meta-index file (malformed Release file?)

E: Some index files failed to download, they have been ignored, or old ones used instead.

```

---

### Post by no2498 on 2010-11-30
? why not just go to opera and get the deb package

id not get the beta yet if was me

10.63 is what i use

[http://www.opera.com/](http://www.opera.com/)

---

### Post by Chrisy91 on 2010-11-30
That would be the best bet, got to Operas website and download it from there, if you are using Ubuntu their website detects it automatically so you dont need to look around for the right format.

---

### Post by sikander3786 on 2010-11-30
Just remove the deb-src line from sources.list and the error would just go away.

And you'll still be able to install opera.

Moreover, installing from repositories is recommended because you get the updates as soon as they are available ;-)

---

### Post by zamolxis on 2010-11-30
> **sikander3786 said:**
> Just remove the deb-src line from sources.list and the error would just go away.

It took me a while to figure it out, but you're right, that's what was wrong. It seems that Synaptic adds the src line automatically, which does not work if the repository is commercial (no source provided). This seems like a bug to me - I could not find it documented anywhere. There should be better error handling.

> Moreover, installing from repositories is recommended because you get the updates as soon as they are available ;-) That's why I was trying so hard :)

---

### Post by sikander3786 on 2010-12-01
Glad to hear it is sorted out :-)

(On behalf of all the contributors), You can mark this thread Solved using **[COLOR="Red"]Thread Tools [/COLOR]**near the top of this page.

Happy Ubuntu-ing!

---

### Post by missmoondog on 2012-03-07
ancient thread, but just worked for me on xubuntu 11.10!!  :)

---

