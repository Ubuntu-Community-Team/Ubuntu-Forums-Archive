---
title: "Ubuntu &amp; Edubuntu Sharing Same Home Folder"
date: 2013-12-21
forum: Installation &amp; Upgrades
---

### Post by arnold.pietersen on 2013-12-21
Hi

I have Ubuntu 13.10 installed on my netbook with the home folder in a separate partition.

I then installed Edubuntu 12.04 with it's own home folder. However, I want the Edubuntu installation to share or access the Ubuntu 13.10 home folder.

Is it possible? If so, how would one go about it?

Any guidance will be appreciated.

Kind Regards

ARNOLD

---

### Post by vanadium on 2013-12-21
I only would support this if both your Edubuntu and Ubuntu were version 13.10. They are not, and thus, there is no guarantee that config data have kept the same format between the different versions of the applications that come with your installed operating systems.

If it is a matter of just accessing the home folder of one OS from within the other OS, then the most convenient way is to make sure that partition is mounted in the other OS (though *not* as /home), and use symlinks to access it from for example your home folder.

---

### Post by grahammechanical on 2013-12-21
If your Ubuntu 13.10 home folder is on its own partition you can access it in Edubuntu by loading the File Manager and opening/mounting the partition. In fact that partition should appear in the Edubuntu Launcher. Perhaps Edubuntu 12.04 did not at that time run Unity.

I have several installs of Ubuntu, including Edubuntu. I keep my data on a separate partition that I have labelled DATA and I can access the documents on that partition from any install of Ubuntu that I have simply by using File Manager to open/mount the partition. Once I have done that then Libreoffice Recent Documents will load a recently accessed file and Rhythmbox will use its play list to play music files on the DATA partition.

Regards.

---

