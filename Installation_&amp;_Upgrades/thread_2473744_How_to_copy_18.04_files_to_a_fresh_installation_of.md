---
title: "How to copy 18.04 files to a fresh installation of 18.04"
date: 2022-04-12
forum: Installation &amp; Upgrades
---

### Post by robertcull1 on 2022-04-12
I am having trouble with my old installation of 18.04. I am opting to reinstall the operating system.

After I have the fresh install, can I just delete the contents of the home directory and they copy in everything in my account directory of the old installation?

If there is a better way to get your old files installed onto a fresh installation, would you tell me how? Or point me in the right direction?

Thanks.

---

### Post by deadflowr on 2022-04-12
Why no backups already?

---

### Post by robertcull1 on 2022-04-12
I have the entire drive backed up. But it seems to have something wrong with it.

The files in the home director seem to be okay.

---

### Post by robertcull1 on 2022-04-12
I made a goof! I remembered that the home directory contains data for personal accounts.

What I meant to say is that I have everything in my personal account backed up.

If I copy what was in my personal account to the new personal account in the new installation, will that be okay?

---

### Post by grahammechanical on 2022-04-12
If Ubuntu is installed in only one partition it is possible to re-install Ubuntu without formatting the partition  and then everything in the Home directory is preserved. It is also possible to install Ubuntu as two partitions, One partition with the mount point of / and the other with the mount point of /home. Then we can re-install Ubuntu and reformat the / partition but not formatting the /home partition. And again everything in /home will be saved.

An alternative would be to put in a fresh install of 18.04 as a dual boot with the same user name and password and then transfer data over.

Regards

---

### Post by vanadium on 2022-04-13
Make sure that the trouble you had with your old installation was related to the system files. If it was caused by user configuration, you will just copy the problem back in your new installation.

---

### Post by robertcull1 on 2022-04-14
I made use of your suggestion to make a separate home partition. Seems to be working. Thanks!

---

