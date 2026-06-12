---
title: "Ubuntu 10.10 and OpenOffice"
date: 2010-12-10
forum: Installation &amp; Upgrades
---

### Post by ronti69 on 2010-12-10
Hello,
I just upgraded to Ubuntu 10.10. I used to run version 9.1. OpenOffice used to work great, but now it won't open ANY Microsoft Office files. It tries to import them using an ASCII filter, and the result is a bunch of garbish.
I don't have much experience with Linux at all. I tried uninstalling OOo and re-installing it - didn't work. I tried deleting all Linux partitions (it's a dual-boot laptop with Windows Vista <yuk!>) and then re-installing Ubuntu10.10 - didn't work either.

Can anybody help?

---

### Post by ronparent on 2010-12-10
Since no one is answering this post, let's stir it up a bit. 

I think that many of the user configuration files, which are hidden, are retained when a program like OpenOffice is removed. This is usually an asset because it retains user data you often want to retain. Unfortunately it also retains some features you want to be rid of or which are maybe obsolete. A possible answer is after uninstalling the program you look at the location of your user files/folders and instruct Nautilus to view hidden folders. Delete .openoffice.org. Then reinstall. If that doesn't work, you may then have to post on the openoffice site for more specific info.

---

### Post by ronti69 on 2010-12-11
Thanks for the reply. I tried that but unfortunately it didn't work. I uninstalled Ubuntu by wiping all Linux partitions (using Bootit), resized windows partition to use the whole drive. Then I re-installed Ubuntu 10.10 letting it partition the drive once again. Still have the same problem! This is so frustrating! Could any Ubuntu/OpenOffice files remain after deleting the partition? Could it be a problem of the iso file that I got?

---

### Post by Jay Car on 2010-12-11
> **ronti69 said:**
> Hello,
I just upgraded to Ubuntu 10.10. I used to run version 9.1. OpenOffice used to work great, but now it won't open ANY Microsoft Office files. It tries to import them using an ASCII filter, and the result is a bunch of garbish.
I don't have much experience with Linux at all. I tried uninstalling OOo and re-installing it - didn't work. I tried deleting all Linux partitions (it's a dual-boot laptop with Windows Vista <yuk!>) and then re-installing Ubuntu10.10 - didn't work either.

Can anybody help?

I'm curious what sorts of Office files do you need opened? I'm not an MSOffice user, but I know that Office is made up of several applications, like PowerPoint, Excel, Word, etc.  Word, by itself, can save to several types of files, like .docx or plain .doc.

I am often sent MS Office files, of one sort or another, but have always been able to find a way to open them (Google Docs is awesome at opening MS Office files).  

But I have friends who used to use MS Works and thought they were using MS Office.  When they purchased new computers, or changed to newer Office software, they found they couldn't open their old files anymore.  If they tried, everything was garbled. 

Of course, this is all just guess work on my part, but to me, rather than doing more reinstalling, maybe the key is to first figure out the specific file types they are, and what version of MS Office (or Works, maybe) they were created in. 

At worst, maybe you could try opening them in Google Docs and, if they open and are readable, resave them to a more accessable format.

---

### Post by ronti69 on 2010-12-11
Thanks for the reply. I am trying to open .doc, .ppt, .xls files created with MS Office 2007.

I just realized, also, that I cannot open any files in Ubuntu: .mp3, or .pdf, or .jpg etc.

So it looks like it is not an OpenOffice problem but rather a problem with my copy of Ubuntu. I have no clue what to do.

On the other hand, if I create a file within Ubuntu, for example a presentation using OpenOffice, I can then open it fine, both in .odt or .ppt formats.

This is so confusing. Any ideas what might be wrong?

---

### Post by Sef on 2010-12-12
> I just upgraded to Ubuntu 10.10. I used to run version 9.1.

How did you upgrade? Did you upgrade directly to 10.10 from 9.10 or did you upgrade to 10.10 from 10.04 and upgraded to that from 9.10?

---

### Post by ronti69 on 2010-12-12
I never had 10.04
The first time I upgraded from 9.1
Now I have what I think is a clean install: I formatted the linux partitions, downloaded the iso for 10.10 again, burnt a new CD (I thought I might have some corrupt files the first time around). I installed 10.10 from that new CD, but I am still having the same problem. No file will open, not only MS office files but also jpg, mp3, pdf... I tried double click on the file or opening the program first and then go File-->Open... it made no difference.
This is so weird. Can anybody suggest anything I should try? I have no clue what to do.
Thanks a lot

---

