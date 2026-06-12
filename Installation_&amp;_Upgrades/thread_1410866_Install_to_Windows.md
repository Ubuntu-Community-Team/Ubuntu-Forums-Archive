---
title: "Install to Windows"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by Captain_MDS on 2010-02-19
General question, I have unmovable files scattered all over my hd (xp) and not a lot of free space available, about 15gb. What are the advantages (if any) and disadvantages to
installing 9.10 to windows instead of to a separate partition? Would I be subjecting Ubuntu to possible virus/spyware since it would be located in the C: drive?
Captain_MDS

---

### Post by raymondh on 2010-02-19
> **Captain_MDS said:**
> General question, I have unmovable files scattered all over my hd (xp) and not a lot of free space available, about 15gb. What are the advantages (if any) and disadvantages to
installing 9.10 to windows instead of to a separate partition? Would I be subjecting Ubuntu to possible virus/spyware since it would be located in the C: drive?
Captain_MDS

1.  windows-based and targetted virus' are different from linux-based/targetted virus'.  However, since your linux is a file-system within windows, "if the host is infected, then the guests' will have a miserable time".

2.  if windows crashes, or is not closed/ejected properly ... well, you get the point :)

3.  Virtual space (to keep the guest) has to come from somewhere.  It will reduce your current allocation for windows.  Also, I have heard that is is best to keep the HD/partition 10-20% free for windows to move freely.

See this interview with RUSSO, the developer of WUBI installs.  Note his response to the second question.

[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)

Raymond

---

### Post by Captain_MDS on 2010-02-19
Thanks, I get the picture. Wanted to "test drive" Ubuntu before I did a proper install.
I don't have enough free space so I'll have to wait until I get a new computer. Hopefully soon.
Again, thanks
Captain_MDS

---

