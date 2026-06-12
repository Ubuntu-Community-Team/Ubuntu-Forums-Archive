---
title: "Can't install libgtk-3-dev"
date: 2023-11-08
forum: Installation &amp; Upgrades
---

### Post by demonenero84 on 2023-11-08
Hi there,
In my spare time I am learning a bit of c, I wanted to make a simple program using GTK+ library, so I followed this guide [https://www.ubuntubuzz.com/2018/11/setup-cgtk-programming-tools-on-ubuntu-for-beginners.html](https://www.ubuntubuzz.com/2018/11/setup-cgtk-programming-tools-on-ubuntu-for-beginners.html).
Now when I try to install GTK with this command```
$ sudo apt-get install libgtk-3-dev
``` I get this result ```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libicu-dev : Depends: libicu70 (= 70.1-2) but 70.1-2ubuntu1 is to be installed
E: Unable to correct problems, you have held broken packages.

```.
This is my hardware and os
OS: Kubuntu 22.04.2 LTS x86_64
CPU: Intel i5-7400 (4) @ 3.500GHz
GPU: NVIDIA GeForce GTX 1050
I tried using a vm with linux mint and everything works, right now I am using that vm to compile programs as a workaround.
Many thanks in advance
EDIT:
I enabled pre-release updates, did sudo apt update and sudo apt upgrade and that solved the issue:guitar:

---

### Post by deadflowr on 2023-11-08
what does 
```
apt policy libicu-dev libicu70
``` show


Edit:
Never mind, I see you've just enabled proposed updates.
But I am interested to know where the package version 70.1-2ubuntu1  was coming from.
Or if you had enable proposed before that.

(FTR pre-release updates = proposed)

---

### Post by demonenero84 on 2023-11-08
thanks for the reply :cool:
I am quite sure I had enabled "pre-release updates" but after some time I disabled them, now I re-set them to "Recommended updates" only

Here is the result:
```
libicu-dev:
  Installed: 70.1-2ubuntu1
  Candidate: 70.1-2ubuntu1
  Version table:
 *** 70.1-2ubuntu1 100
        100 /var/lib/dpkg/status
     70.1-2 500
        500 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages
libicu70:
  Installed: 70.1-2ubuntu1
  Candidate: 70.1-2ubuntu1
  Version table:
 *** 70.1-2ubuntu1 100
        100 /var/lib/dpkg/status
     70.1-2 500
        500 http://archive.ubuntu.com/ubuntu jammy/main amd64 Packages
```

---

### Post by deadflowr on 2023-11-08
> I am quite sure I had enabled "pre-release updates" but after some time I disabled them
Ah, I get it now.

---

