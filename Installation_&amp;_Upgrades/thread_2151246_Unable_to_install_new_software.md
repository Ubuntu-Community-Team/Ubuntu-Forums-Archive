---
title: "Unable to install new software"
date: 2013-06-03
forum: Installation &amp; Upgrades
---

### Post by sideburns on 2013-06-03
My sister uses Ubuntu (I'm not sure which version, and it shouldn't matter.) and needs to be able to upload files to her website.  We've tried using the Ubuntu Software Center to install gFTP and got an error that this requires installing software from untrusted sites.  Clicking OK gets rid of the warning, but doesn't help and telling it to Repair the issue fails.  I had her try to work around this by installing Filezilla, with the same results.  What is our next step?

---

### Post by Shrek01 on 2013-06-04
I would say that the version does matter since it might not be supported anymore.
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions]("https://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions")

To find what version she has, have her open a console and report back on:
```
cat /etc/issue
```
And as for the next step to find what the problem is, we can get a clue with the anwser of the following in a console
```
sudo apt-get install
```

---

### Post by sideburns on 2013-06-04
She's using Ubuntu 13.0.2 LTS

As far as the second suggestion, she'd probably have gotten a meaningless error message for not having specified what to install.  I'll have her try it properly, with gftp.

---

### Post by sideburns on 2013-06-04
OK, she was able to install gftp from the command line.  It still complained about not being able to authenticate the sources, but when she told it to install anyway, it did.  Now, the only question is, why didn't the Software Center continue when she told it to?

---

### Post by Softa on 2013-06-04
Hi Shrek01,
Thank you for your help.  And like Sideburns said: "Why didn't the Software Center continue when I told it to?"

---

### Post by oldos2er on 2013-06-05
Software Center is working the way it was designed; you'd need to ask the developers themselves for further explanation. As noted, *apt-get install whatever* will give you a warning, but still work.

---

