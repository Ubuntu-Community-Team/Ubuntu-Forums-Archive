---
title: "Failure to download certain packages during update"
date: 2013-05-31
forum: Installation &amp; Upgrades
---

### Post by jorritTyb on 2013-05-31
I just tried to update using Synaptic Package Manager. This worked fine for a lot of files but I got this error near the end:

```
W: Failed to fetch http://ppa.launchpad.net/irie/blender/ubuntu/pool/main/b/blender/blender_2.67.a+svn56948-0irie1~precise1_amd64.deb  404  Not Found




W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_3.2.0.43.51_amd64.deb
  404  Not Found [IP: 91.189.92.190 80]




W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.2.0.43.51_amd64.deb
  404  Not Found [IP: 91.189.92.190 80]




W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.2.0.43.51_amd64.deb
  404  Not Found [IP: 91.189.92.190 80]




W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.2.0-43.68_amd64.deb
  404  Not Found [IP: 91.189.92.190 80]





```


What can I do about this?

Thanks!

---

### Post by sanderj on 2013-05-31
First run:

```
sudo apt-get update
```

then

```
sudo apt-get upgrade
```

HTH

---

### Post by ibjsb4 on 2013-05-31
Im not finding "blender_2.67.a+svn56948"

[http://ppa.launchpad.net/irie/blender/ubuntu/pool/main/b/blender/](http://ppa.launchpad.net/irie/blender/ubuntu/pool/main/b/blender/)

---

### Post by jorritTyb on 2013-05-31
Thanks a lot! That helped. I wonder how one is supposed to know that if you're not used to the commandline tools.

---

### Post by sanderj on 2013-05-31
> **jorritTyb said:**
> Thanks a lot! That helped. I wonder how one is supposed to know that if you're not used to the commandline tools.

If you only use the GUI, you should not get that problem.

So: how did you get the errors ... via the CLI or via the GUI ... ?

And: read [http://eva-quirinius.blogspot.com/2013/03/enrich-your-ubuntu-by-creating-short.html](http://eva-quirinius.blogspot.com/2013/03/enrich-your-ubuntu-by-creating-short.html) ... it will give you a handy command "sagusagu" that will take care of it ... :-)

---

### Post by ibjsb4 on 2013-05-31
> **sanderj said:**
> If you only use the GUI, you should not get that problem.

So: how did you get the errors ... via the CLI or via the GUI ... ?

Its a PPA, there is no GUI for ppa's.

---

### Post by ibjsb4 on 2013-05-31
> **jorritTyb said:**
> Thanks a lot! That helped. I wonder how one is supposed to know that if you're not used to the commandline tools.

Didn't use the command line for this one :)  Just start with:

[http://ppa.launchpad.net/irie/blender/](http://ppa.launchpad.net/irie/blender/)

And keep going down a level until you hit oil :)

---

### Post by sanderj on 2013-05-31
> **ibjsb4 said:**
> Its a PPA, there is no GUI for ppa's.


No GUI for PPA's? Software & Sources -> tab Other Software.

---

### Post by ibjsb4 on 2013-05-31
Your half way there, that won't add a key :)

sudo add-apt-repository ppa:<repository-name>  is the way to go.


[https://launchpad.net/+help-soyuz/ppa-sources-list.html](https://launchpad.net/+help-soyuz/ppa-sources-list.html)

---

### Post by jorritTyb on 2013-06-03
I got that error with the GUI.

---

