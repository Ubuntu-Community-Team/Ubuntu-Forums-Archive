---
title: "hardy package manager"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by bluetwinkle on 2008-04-26
I have just upgraded to Hardy by doing a complete installation, since it wouldn't work via the update manager. 

Now, I'm trying to download the MS core fonts package, but the Package Manager wouldn't download. I'd get the download window, it'd say "downloading package" with the progress bar, but it wouldn't download. 

Is there a problem with the Ubuntu repositories?

---

### Post by martrn on 2008-04-26
According to [http://packages.ubuntu.com/hardy/x11/msttcorefonts]("http://packages.ubuntu.com/hardy/x11/msttcorefonts") msttcorefonts uses cabextract and wget to fetch and install the fonts.  So in effect it is downloading the fonts from somewhere else.  If the repository you use is working for everything else, then it will be the wget fonts and the place were the fonts are downloaded from that will be having problems.  I would only suggest to try later.

I do not think this would be an ubuntu repository problem.

---

### Post by bluetwinkle on 2008-04-26
It has just tried to download a driver, and it still wouldn't download:

W: Failed to fetch [http://ca.archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb](http://ca.archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_011-1_i386.deb)

---

### Post by Despotic on 2008-04-26
I'm having similar problems. My updates are all timing-out, sometimes it's 1 source, sometimes it's 10, never the same.

I'm thinking it might be the Canadian Servers, either being bogged down, or maybe something else.

I just changed software sources to the "main server" and I was successful, except for the 1 day 4 hours projected completion time. I'm going in to the office to see if a faster connection helps.

---

