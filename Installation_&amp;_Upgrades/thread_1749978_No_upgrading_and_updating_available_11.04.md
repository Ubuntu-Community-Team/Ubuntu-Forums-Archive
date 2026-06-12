---
title: "No upgrading and updating available 11.04"
date: 2011-05-05
forum: Installation &amp; Upgrades
---

### Post by earendil02 on 2011-05-05
I've just installed Ubuntu 11.04 from a usb flash disk, and during the installation I couldn't connect to internet, but the first time I tryed to connect and update/upgrade the system or install software I got this error message:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:L'elenco dei pacchetti o il file di stato non può essere letto o aperto.'

can you help me please?

---

### Post by lechien73 on 2011-05-05
Hi and welcome to the forums :)

This could be happening because of corrupted list files. Try deleting them using:

```
sudo rm /var/lib/apt/lists/* -vf
```

Then try the update again.

---

### Post by earendil02 on 2011-05-05
Thank You veryveryveryveryveryveryvery much!!!!! :):):):) you saved me! :)
Now it works! :)
Can you explain what I did precisely please? I'm very curious... ;)

---

### Post by lechien73 on 2011-05-05
The /var/lib/apt/lists folder contains package list files used by the package manager. Obsolete list files are usually removed whenever you run apt-get update, but this folder can grow quite large and occasionally files in here can get corrupted. The command I gave you deleted all the files in the folder, which allowed the package manger to run correctly. Necessary files will be re-created.

Please could you use the "Thread Tools" menu at the top of this page and mark this thread as [SOLVED]?

Thanks

---

### Post by earendil02 on 2011-05-05
Thank you very much! Very clear, thank you again! :)

---

### Post by orangep on 2011-05-07
yes,

sudo rm /var/lib/apt/lists/* -vf

This clears out the offending file.
Thank you. I was tearing my hair out, which is not a good idea at my age.

---

