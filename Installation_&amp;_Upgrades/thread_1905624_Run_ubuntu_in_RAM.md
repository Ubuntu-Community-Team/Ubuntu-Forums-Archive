---
title: "Run ubuntu in RAM?"
date: 2012-01-07
forum: Installation &amp; Upgrades
---

### Post by sutek89 on 2012-01-07
Hi. I was wondering if below was possibe. I think It could result in great speed improvement on newer machines with a lot of ram and fast CPUs.

Install ubuntu. /home on a different partition
Add and remove packages keeping size in mind. (Large programs could be compiled on the HDD using --prefix?)
Compress / (-/home) to a "file".

Boot system copying the compressed "file" to RAM and mounting it and running everything there.
Wrie a "Shutdown" script that will copy compressed "file" from RAM to HDD and shutdown when finished.
I understand that if the computer is not shot down properly all work will be lost, but thats not necesarily a bad thing, if harfull changes are done at least you're safe.
Write "Save your Work" script which will be identical to "shutdown" but without the shutdown.

The system would have to know that location of /home is on the harddrive.

swap would probably be on HDD as well I assume?

If anyone Has the necessary knowledge to make it happen could you please write a tutorial?

Is there anything I don't know, or am missing that would make this impossible or not worth doing minus the long boot and shutdown times?

I suppose it is a similar principle as Live CD.

---

### Post by oldfred on 2012-01-07
Not a Tutorial, Moved to Installation & Upgrades.

---

### Post by Meizirkki on 2012-07-07
I recently acquired an old server which has 26Gb of RAM installed. So I'm interested in this kind of a thing now :D

I read about the [anything sync daemon]("https://wiki.archlinux.org/index.php/Anything-sync-daemon") (asd) for Arch, a script that puts whatever files you want in tmpfs and periodically rsyncs them to HDD for permanent storage. It seems to be exactly what we need here, but I had no idea how to make it work. Arch's conf files are in different places. :-?

---

### Post by raja.genupula on 2012-07-08
> **Meizirkki said:**
> I recently acquired an old server which has 26Gb of RAM installed. So I'm interested in this kind of a thing now :D

I read about the [anything sync daemon]("https://wiki.archlinux.org/index.php/Anything-sync-daemon") (asd) for Arch, a script that puts whatever files you want in tmpfs and periodically rsyncs them to HDD for permanent storage. It seems to be exactly what we need here, but I had no idea how to make it work. Arch's conf files are in different places. :-?

Hey post your issue on your own thread , don't paste it on others .

---

### Post by Elfy on 2012-07-08
Closed.

Please don't resurrect old threads - better to create your own.

---

