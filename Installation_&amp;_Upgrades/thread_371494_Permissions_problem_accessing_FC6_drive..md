---
title: "Permissions problem accessing FC6 drive."
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by elmerfud on 2007-02-27
I backed up my Fedora Core 6 installation to a USB drive today.  Then I wiped my hard drive clean and installed Kubuntu 6.10.  So far so good. 

I'd like to copy some of my old installation info to my new OS, but I am having a problem.   It seems that kubuntu sets up new users with a UID of 1000, whereas the UID on the files from the old archive are 500 or so.  It doesn't appear that one can edit the UID of a Ubuntu user either. 

So how do I easily copy the files from my old archive to Ubuntu without doing a bunch of fooling around with UIDs ?

Thanks

---

### Post by aysiu on 2007-02-27
**Step 1**: Press Alt-F2 

**Step 2**: Type ```
kdesu konqueror
``` 

**Step 3**: Copy the files to your home folder

**Step 4**: Change ownership of the files by typing this command in the terminal: ```
sudo chown -R elmerfud:elmerfud /home/elmerfud
``` Substitute in your actual username for *elmerfud*, of course.

---

### Post by elmerfud on 2007-02-28
I was looking for something simpler than that, something that I could change once and it would work forever.  But what you stated works, obviously. 

Thanks.

---

