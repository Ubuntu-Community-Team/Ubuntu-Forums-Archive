---
title: "Vista's lost it"
date: 2008-10-21
forum: Installation &amp; Upgrades
---

### Post by thedrone on 2008-10-21
Resized  and repartitioned disc on vista laptop  installed ubuntu  as dual boot system   vista loads fine but can no longer find/load certain files.
Anyone know how to help. This is probably a frequent problem!

---

### Post by Herman on 2008-10-21
:) Have you tried running CHKDSK /R from a Windows Recovery Console?
I'll bet that's all you need to do to fix it.

Regards, Herman :)

---

### Post by thedrone on 2008-10-21
Recovery console is apparently unavailable in vista should I try the same command from a console run as administrator?
Sorry this thread isn't really about ubuntu is it!

---

### Post by Dougie187 on 2008-10-21
Recovery Console is from the windows install cd, not inside the os.

---

### Post by Herman on 2008-10-21
:) Thanks to Computer Guru, of NeoSmart Technologies (the developer of [EasyBCD]("http://neosmart.net/dl.php?id=1")), you can download a Vista Recovery CD from his site, Neosmart.
I haven't tried it out because I don't use Vista, (or know anyone who does), but it probably has CHKDSK in it, (I guess). 
Here is the link for you, [Windows Vista Recovery Disc Download]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") - Neosmart.net


It is recommended in the GParted Documentation at the GParted Live CD site to run CHKDSK after resizing an NTFS partition.

Regards, Herman :)

---

### Post by Herman on 2008-10-21
> Sorry this thread isn't really about ubuntu is it!
:)  That's okay. 
We understand that most  computers are sold with Windows already in them, so therefore we need to be able to help a little with both operating systems.

Ubuntu's disk partitioner is about the safest in the world, even with NTFS partitions, but Linux doesn't have CHKDSK. We have ntfsfix, which marks the file system with a 'dirty' flag, thus inducing Windows to run an automatic CHKDSK in the file system the next time it's booting up.

Even without a 'Recovery' CD, you probably can  [run Microsoft CHKDSK from the command line ]("http://service1.symantec.com/SUPPORT/powerquest.nsf/docid/2004066687571562")- Symantec.

Regards, Herman :)

---

### Post by thedrone on 2008-10-22
Brill, thanks all of you guys   will download the cd on general principles and also give running chkdsk a go.

---

