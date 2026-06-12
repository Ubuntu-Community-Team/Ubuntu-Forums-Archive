---
title: "Possible encryption issue after upgrade"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by cajunaggie on 2011-10-15
I used the GUI upgrade manager. After reboot, I got the error explored in [this thread]("http://ubuntuforums.org/showthread.php?t=1859233"). I tried the solution listed there without success.

I opened up my system with a LiveCD this morning and found that there are ***TWO*** files in my profile:Access-Your-Private-Data.desktop and README.txt

The contents of README.txt:
[INDENT]THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
"Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private[/INDENT]

Obviously if I could get into my GUI, I wouldn't be here. Running ecryptfs-mount-private yields ```
Inserted auth tok with sig [c7ff2490514cefc into the user session keyring
open: no such file or directory
Error locking counter
``` and nothing changes. So what the heck did the upgrade do to my system?

---

### Post by teluma on 2011-10-15
I had a similar problem and went down the route described here :
 [https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory#Live_CD_method_of_opening_a_encrypted_home_directory) to access the encrypted home directory. 

Once in as owner of the encrypted files through this method, I was then able to edit some system files so that the messed-up upgraded installation would boot again.

---

### Post by LukeMorrison on 2011-10-15
I had the same issue and this was my thread:

[http://ubuntuforums.org/showthread.php?t=1860483](http://ubuntuforums.org/showthread.php?t=1860483)

---

### Post by cajunaggie on 2011-10-15
Tried that. Apparently I don't have /dev/null and it's telling me "Encrypted private directory is not setup properly"

Anyone else have any suggestions? I really need to recover that data.

---

### Post by cajunaggie on 2011-10-16
SOLVED: Used a LiveCD to mount the encrypted partition and ran ecryptfs-recovery-private to decrypt to a temporary mount point. Then it's just a matter of file transfer between storage mediums.

---

