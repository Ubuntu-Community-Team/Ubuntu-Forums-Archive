---
title: "Unable to install the selected kernel Ubuntu 14.04 from local mirror"
date: 2016-09-15
forum: Installation &amp; Upgrades
---

### Post by azranjith on 2016-09-15
Hi,

We have setup ubuntu local mirror in our environment to do the ubuntu  unattended installation, We have setup the local mirror from: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)

  (We have post this issue in: [https://askubuntu.com/questions/822816/unable-to-install-the-selected-kernel-ubuntu-14-04-from-local-mirror](https://askubuntu.com/questions/822816/unable-to-install-the-selected-kernel-ubuntu-14-04-from-local-mirror) too, still we are facing the same issue, INSTEAD OF LOCAL MIRROR WE HAVE TRIED WITH ONLINE MEDIA: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) STILL THE MENTIONED ERROR PERSIST)

Now we are facing the error: Unable to install the selected kernel,  kindly check the attached image and assist me to rectify the issue.


  Unable to install the selected kernel:


[IMG]http://i.stack.imgur.com/kd69U.jpg[/IMG]

Regards,
Ranjithkumar.T

---

### Post by ian-weisser on 2016-09-15
Let's see....

```
$ rmadison linux-generic linux-generic | 3.2.0.23.25   | precise          | amd64, i386
 linux-generic | 3.2.0.109.125 | precise-security | amd64, i386
 linux-generic | 3.2.0.109.125 | precise-updates  | amd64, i386
 linux-generic | 3.2.0.110.126 | precise-proposed | amd64, i386
 linux-generic | 3.13.0.24.28  | trusty           | amd64, arm64, armhf, i386, ppc64el
** linux-generic | 3.13.0.95.103 | trusty-security  | amd64, arm64, armhf, i386, ppc64el**
** linux-generic | 3.13.0.95.103 | trusty-updates   | amd64, arm64, armhf, i386, ppc64el**
 linux-generic | 3.13.0.96.104 | trusty-proposed  | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.19.0.15.14  | vivid            | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.19.0.68.66  | vivid-security   | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.19.0.68.66  | vivid-updates    | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.19.0.69.67  | vivid-proposed   | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 4.2.0.16.18   | wily             | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 4.2.0.42.45   | wily-security    | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 4.2.0.42.45   | wily-updates     | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 4.4.0.21.22   | xenial           | amd64, arm64, armhf, i386, ppc64el, s390x
 linux-generic | 4.4.0.36.38   | xenial-security  | amd64, arm64, armhf, i386, ppc64el, s390x
 linux-generic | 4.4.0.36.38   | xenial-updates   | amd64, arm64, armhf, i386, ppc64el, s390x
 linux-generic | 4.4.0.38.40   | xenial-proposed  | amd64, arm64, armhf, i386, ppc64el, s390x
 linux-generic | 4.4.0.9136.37 | yakkety          | amd64, arm64, armhf, i386, ppc64el, s390x
```

Do you have the trusty-security and/or trusty-updates repositories on your local mirror?

---

### Post by azranjith on 2016-09-20
Hi,

Thank you for your response, we were setup the local mirror on path: /ubuntu-mirror/archive.ubuntu.com/ubuntu. as your update i have perform the command 'rmadison', kindly check the below output and let me know whether i generate the output in correct way or share the steps to rectify the issue. 

```
[EMAIL="root@ubuntu:/ubuntu-mirror/archive.ubuntu.com"]root@ubuntu:/ubuntu-mirror/archive.ubuntu.com[/EMAIL]/ubuntu# du -sch *
19G     dists
1.4G    indices
16M     ls-lR.gz
323G    pool
576K    project
0       ubuntu
343G    total
```
```
[EMAIL="root@ubuntu:/ubuntu-mirror/archive.ubuntu.com"]root@ubuntu:/ubuntu-mirror/archive.ubuntu.com[/EMAIL]/ubuntu# du -sch dists/*
1.5G    dists/trusty
1.5M    dists/trusty-backports
8.4G    dists/trusty-proposed
445M    dists/trusty-security
8.5G    dists/trusty-updates
19G     total
```
```
[EMAIL="root@ubuntu:/ubuntu-mirror/archive.ubuntu.com"]root@ubuntu:/ubuntu-mirror/archive.ubuntu.com[/EMAIL]/ubuntu# rmadison linux-generic linux-generic
 linux-generic | 3.2.0.23.25   | precise          | amd64, i386
 linux-generic | 3.2.0.110.126 | precise-security | amd64, i386
 linux-generic | 3.2.0.110.126 | precise-proposed | amd64, i386
 linux-generic | 3.2.0.110.126 | precise-updates  | amd64, i386
 linux-generic | 3.13.0.24.28  | trusty           | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.13.0.96.104 | trusty-security  | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.13.0.96.104 | trusty-proposed  | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.13.0.96.104 | trusty-updates   | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.19.0.15.14  | vivid            | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.19.0.69.67  | vivid-security   | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.19.0.69.67  | vivid-proposed   | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.19.0.69.67  | vivid-updates    | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 4.2.0.16.18   | wily             | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 4.2.0.42.45   | wily-security    | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 4.2.0.42.45   | wily-updates     | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 4.4.0.21.22   | xenial           | amd64, arm64, armhf, i386, ppc64el, s390x
 linux-generic | 4.4.0.38.40   | xenial-security  | amd64, arm64, armhf, i386, ppc64el, s390x
 linux-generic | 4.4.0.38.40   | xenial-proposed  | amd64, arm64, armhf, i386, ppc64el, s390x
 linux-generic | 4.4.0.38.40   | xenial-updates   | amd64, arm64, armhf, i386, ppc64el, s390x
 linux-generic | 4.4.0.9136.37 | yakkety          | amd64, arm64, armhf, i386, ppc64el, s390x
 linux-generic | 4.8.0.11.20   | yakkety-proposed | amd64, arm64, armhf, i386, powerpc, ppc64el, s390x
 linux-generic | 3.2.0.23.25   | precise          | amd64, i386
 linux-generic | 3.2.0.110.126 | precise-security | amd64, i386
 linux-generic | 3.2.0.110.126 | precise-proposed | amd64, i386
 linux-generic | 3.2.0.110.126 | precise-updates  | amd64, i386
 linux-generic | 3.13.0.24.28  | trusty           | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.13.0.96.104 | trusty-security  | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.13.0.96.104 | trusty-proposed  | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.13.0.96.104 | trusty-updates   | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.19.0.15.14  | vivid            | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.19.0.69.67  | vivid-security   | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.19.0.69.67  | vivid-proposed   | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 3.19.0.69.67  | vivid-updates    | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 4.2.0.16.18   | wily             | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 4.2.0.42.45   | wily-security    | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 4.2.0.42.45   | wily-updates     | amd64, arm64, armhf, i386, ppc64el
 linux-generic | 4.4.0.21.22   | xenial           | amd64, arm64, armhf, i386, ppc64el, s390x
 linux-generic | 4.4.0.38.40   | xenial-security  | amd64, arm64, armhf, i386, ppc64el, s390x
 linux-generic | 4.4.0.38.40   | xenial-proposed  | amd64, arm64, armhf, i386, ppc64el, s390x
 linux-generic | 4.4.0.38.40   | xenial-updates   | amd64, arm64, armhf, i386, ppc64el, s390x
 linux-generic | 4.4.0.9136.37 | yakkety          | amd64, arm64, armhf, i386, ppc64el, s390x
 linux-generic | 4.8.0.11.20   | yakkety-proposed | amd64, arm64, armhf, i386, powerpc, ppc64el, s390x
[EMAIL="root@ubuntu:/ubuntu-mirror/archive.ubuntu.com"]root@ubuntu:/ubuntu-mirror/archive.ubuntu.com[/EMAIL]/ubuntu#
```

---

### Post by ian-weisser on 2016-09-20
Please answer the question in Post #2.

---

### Post by azranjith on 2016-09-26
Hi Ian-weisser,

yes, i have the trusty-security and trusty-updates on my local repository. I have already updated with their size on my #2 post.

[email]root@ubuntu:/ubuntu-mirror/archive.ubuntu.com[/email]/ubuntu# du -sch dists/*
1.5G dists/trusty
1.5M dists/trusty-backports
8.4G dists/trusty-proposed
445M dists/trusty-security
8.5G dists/trusty-updates
19G total
 
Thanks.

---

### Post by ian-weisser on 2016-09-26
It is unwise to blindly run mysterious commands (like rmadison).
That practice can cause a lot of damage very quickly. Avoid it.

Compare the output of 'apt policy' on the affected machine vs. a good machine for the following packages: linux-image, linux-image-generic

---

### Post by azranjith on 2016-09-28
Hi,

Okay.

Shall i know more details about the good / affected machine, because i have 3 machines

machine1 to initiate unattended installation, machine2 for Ubuntu local-mirror setup from [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) (which am facing the pkg issue) and the machine3 have no OS installed.

As per your update i just checked the packages: linux-image, linux-image-generic and found: linux-image-generic (/ubuntu-mirror/archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.13.0.95.103_amd64.deb), Let me know how to proceed further.

Regards,
Ranjithkumar.T

---

### Post by ian-weisser on 2016-09-28
linux-image-generic should be at 3.13.0.96 on all machines.
If it's not, the delete the local version on the affected machine and reinstall from your mirror:
```
sudo apt update
sudo apt-cache clean linux-image-generic
sudo apt install --reinstall linux-image-generic
sudo apt upgrade
```

If your mirror has not updated to .96, then that's a different problem.

---

### Post by azranjith on 2016-10-08
Thanks for the update, 

As i mentioned there is no affected machines "because i have 3 machines, machine1 to initiate unattended installation, machine2 for Ubuntu local-mirror setup from [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) (which am facing the pkg issue) and the machine3 have no OS installed."

kindly let me know how to proceed with this setup or Do i need to add the package manually and need to regenerate the repo to short our this issue.

---

