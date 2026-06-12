---
title: "I seem to have screwed up installing VMWare Server. Need a bit of help."
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by Rockerone on 2007-09-05
I downloaded VMWare Server today and got a key. The install file is a .pl file. I ran it in the terminal. After selecting a few options it froze, apparently. So I killed the process. Now whenever I try to run the installer again it keeps saying that the installation has already been run. But when I try to start VMWare Server nothing happens. Can anyone help me on this?

---

### Post by tuxcantfly on 2007-09-05
Use the feisty-commercial repository to install VMWare, not their downloadable version. See here: [http://ubuntuforums.org/showthread.php?t=473627](http://ubuntuforums.org/showthread.php?t=473627)

---

### Post by Rootong on 2007-09-06
[http://archive.canonical.com/ubuntu/pool/main/v/vmware-server/vmware-server_1.0.3-1_i386.deb](http://archive.canonical.com/ubuntu/pool/main/v/vmware-server/vmware-server_1.0.3-1_i386.deb)

You can download the file here by using the download tool.:)faster only. And then put the package to
/var/cache/apt/archives

Then, install vmware server by using package manager.

Hope this helps.

---

