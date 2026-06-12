---
title: "Build Failure Nvidia + 2.6.31-1"
date: 2009-07-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2009-07-02
I keep getting build failure w/ 2.6.31.1 + nvidia 190.09

---

### Post by tad1073 on 2009-07-02
I get build failures with 2.6.31-1 + 185.18.14 and 2.6.31-1 + 190.09

bad exit status 10

---

### Post by Regenweald on 2009-07-02
Did you patch the nvidia binary ? 

[http://ubuntuforums.org/showthread.php?t=1197084&page=5](http://ubuntuforums.org/showthread.php?t=1197084&page=5)

---

### Post by tad1073 on 2009-07-02
I just install the updates that came down a little while ago, nothing else.

---

### Post by mano cazalet on 2009-07-02
then u have to patch the nvidia drivers as quoted [above]("http://ubuntuforums.org/showpost.php?p=7546000&postcount=50")

---

### Post by budluva04 on 2009-07-02
all went well here on my end... didn't have to patch anything

uname -a

Linux cabo 2.6.31-1-generic #14-Ubuntu SMP Thu Jul 2 16:02:38 UTC 2009 x86_64 GNU/Linux
billybigrigger@cabo:~$ apt-cache policy nvidia-glx-180
nvidia-glx-180:
  Installed: 185.18.14-0ubuntu2
  Candidate: 185.18.14-0ubuntu2
  Version table:
 *** 185.18.14-0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) karmic/restricted Packages
        100 /var/lib/dpkg/status

billybigrigger@cabo:/var/lib/dkms/nvidia/185.18.14/2.6.31-1-generic/x86_64/log$ pastebinit make.log

[http://pastebin.com/f496b14d7]("http://pastebin.com/f496b14d7")

---

### Post by autocrosser on 2009-07-02
> **tad1073 said:**
> I keep getting build failure w/ 2.6.31.1 + nvidia 190.09

Take a look at the 185 driver thread--Dinxter has posted a fix & I think plun modded it for 190.....

---

### Post by tad1073 on 2009-07-02
got it patched and working, thanks for the help.

---

