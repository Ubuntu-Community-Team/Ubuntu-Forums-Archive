---
title: "incomplete upgrade"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hsartoris on 2010-03-26
i'm trying to install the beta of lucid, and i keep getting this error:

hayden@Haydens-Computer:~$ update-manager -d
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg' 
Traceback (most recent call last):  File "/tmp/tmpqK2k7K/lucid", line 3, in <module>
    from DistUpgradeMain import main
  File "/tmp/tmpqK2k7K/DistUpgradeMain.py", line 25, in <module>
    from DistUpgradeController import DistUpgradeController
  File "/tmp/tmpqK2k7K/DistUpgradeController.py", line 50, in <module>
    from sourceslist import SourcesList, SourceEntry, is_mirror
  File "/tmp/tmpqK2k7K/sourceslist.py", line 36, in <module>
    from apt.deprecation import function_deprecated_by
ImportError: No module named deprecation

before this, in update manager, it just says 'downloading file 2 of 2', never 1 of 2, and it just zips right through the download. sometimes i get this response:

hayden@Haydens-Computer:~$ update-manager -d
extracting 'lucid.tar.gz'
authenticate 'lucid.tar.gz' against 'lucid.tar.gz.gpg' 

and i authenticate, and nothing happens. it just opens another prompt to enter code. I would burn a cd, but i'm using a netbook running UNR, and i don't have a cd drive.

---

### Post by Neds Moar Salt on 2010-03-26
I got this same problem.  Driving me nuts.

---

### Post by whoop on 2010-03-26
hhm, maybe wait a while, reboot, make sure /tmp is empty and try again...

---

### Post by Neds Moar Salt on 2010-03-26
Well, I tried this already and no cigar.  Same error as hsartoris too.

---

### Post by Yofel on 2010-03-26
from apt.deprecation import function_deprecated_by
 ImportError: No module named deprecation

Seems like a missing python module. But apt indeed doesn't have a  deprecation module here in lucid (at least I can't find it).

---

### Post by mccashin on 2010-03-27
Same for me. Both on 9.10 PPC and 9.10 Intel. 
Has anybody done a successful upgrade?

---

### Post by Neds Moar Salt on 2010-03-27
> **Yofel said:**
> from apt.deprecation import function_deprecated_by
 ImportError: No module named deprecation

Seems like a missing python module. But apt indeed doesn't have a  deprecation module here in lucid (at least I can't find it).

I have updated before to lucid, but my hard drive got cooked.  Could it be my ext2 filesystem?  Usually I use ext3, but I am running mac and macfuse-ext2.  Anything on fixing, or would a clean install be my best bet, like almost everything else in the linux world?

---

### Post by raccaman on 2010-03-27
I have the same problem... with ext4 

i thik this is a bug

---

### Post by raccaman on 2010-03-27
> I managed to solve this by installing the Lucid version of python-apt from [https://launchpad.net/ubuntu/lucid/+source/python-apt](https://launchpad.net/ubuntu/lucid/+source/python-apt)

I used [http://launchpadlibrarian.net/41937819/python-apt_0.7.94.2ubuntu3_amd64.deb](http://launchpadlibrarian.net/41937819/python-apt_0.7.94.2ubuntu3_amd64.deb)

this is the solution, but i haven't try yet

---

### Post by gang65 on 2010-03-27
I have sumbitted bug to launchpad:

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/549402](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/549402)

I'm using ext3 filesystem

---

### Post by Yofel on 2010-03-27
Can someone still confirm this?

a recent update manager update might have fixed this:
[https://edge.launchpad.net/ubuntu/+source/update-manager/1:0.133.8](https://edge.launchpad.net/ubuntu/+source/update-manager/1:0.133.8)

---

### Post by Neds Moar Salt on 2010-03-27
> **raccaman said:**
> this is the solution, but i haven't try yet

Thanks, that worked beautifully.  Now to figure out how to get live linux running on my usb.  For some reason, grub on my mac won't recognize my flash drive, and refit is a failure.

---

### Post by hsartoris on 2010-03-27
thanks for the help. i tried the python solution, and that got me as far as the installer. unfortunately, the installer kept crashing, and now i have to use a live usb to get my files off, then wipe the whole partition. a well. it was worth a shot.

---

