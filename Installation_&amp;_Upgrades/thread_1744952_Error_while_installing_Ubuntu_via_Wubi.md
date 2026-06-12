---
title: "Error while installing Ubuntu via Wubi"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Tarantella on 2011-04-30
Hi,

i was trying to install ubuntu with wubi. I installed the application inside windows 7 (64). I executed the applicatation as "admin" and then it began downloading and stuff.

When it finished downloading it said i needed to reboot my pc, so i did. then in the splash screen it showed me win 7 and ubuntu, i selected ubuntu of course. After a few seconds it started to install, but then it showed me this error:

*Could not find the iso /ubuntu/install/ubuntu-11.04-desktop-amd64.iso This could happen if the file system is not clean because of an operating system crash, an interrupted boot process, an improper shutdown, or unplugging of a removable device without first unmounting or ejecting it. To fix this, simply reboot into windows, let it fully start, log in, run 'chkdsk /r', then gracefully shut down and reboot back into windows. After this you should be able to reboot again and resume installation.*

I've done what it says, the 'chkdsk /run' (took a lot of time btw) and it keeps telling me the same thing.

Someone knows what is the solution?

(sorry for my english)

---

### Post by Tarantella on 2011-04-30
I think my computer just dont like anything but windows 7 or vista hehe.

---

### Post by Tarantella on 2011-05-01
well, it seems this problem cannot be fixed?:confused:

---

### Post by Tarantella on 2011-05-02
:popcorn:

---

### Post by bcbc on 2011-05-03
This is a strange one...

Please go into windows and take a snapshot of the Disk manager showing your partitions. Also specify the drive you installed to and maybe "dir /s \ubuntu" on the drive you installed to.

Also, if you have an ubuntu cd, you could boot from it, select "Try it" (or try without installing) and then download and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net") and post the results back here.

---

