---
title: "wubi uninstall"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by trickmaster0465 on 2012-05-15
Hello all,

New to the forums and fairly new to ubuntu. I have a question I have not been able to find an answer to through various searches. I installed ubuntu within windows through wubi as dual boot on a windows vista laptop. Yesterday I uninstalled so that I could reinstall on its own partition, it did uninstall and no longer gives me the option to boot to ubuntu but it did not free up the 17 Gb which was in use by ubuntu on my hd. How do I free up this space?

Thanks all help is appreciated.

---

### Post by bcbc on 2012-05-15
The space used is mostly taken up by the root.disk (the virtual disk) stored in the \ubuntu\disks directory. This directory is deleted when you uninstall, freeing up the space.

If you didn't see the space freed up then the most likely reason is that the root.disk was corrupted, and Windows' chkdsk 'fixed it'. When chkdsk fixes a corrupt file it will sometimes move it to a \found.000 folder (probably because it couldn't determine the correct file name/location?). Whatever the reason, you'll need to look for this directory and delete the file manually. The \found.000 directory is hidden and OS protected so do it from an administrator command prompt.

e.g. (note you can have more than one found.??? folder. So first check how many there are. (Do this on the drive you installed on)
```
dir \found*
dir \found.000

```
If you see a file in \found.000 called chk0000.chk that is ~17GB then you've found the root.disk and can delete it.

If you instead see a directory, dir0000.chk then it's probably the entire \ubuntu\disks folder and within that you'll see the root.disk and swap.disk.
Again, just delete that to free up space.

Finally, if you're still having issues, you should run chkdsk /r on the drive you installed on and repeat the above.

---

### Post by trickmaster0465 on 2012-05-23
No luck with that, even after running check disk. Guess it isn't too big of a deal this is mostly just a backup computer anyway and there is plenty of space on it.

Thanks.

---

