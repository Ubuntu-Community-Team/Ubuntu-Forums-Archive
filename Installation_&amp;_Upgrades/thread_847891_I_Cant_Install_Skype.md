---
title: "I Cant Install Skype???"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by goforlinux on 2008-07-03
Hey I just updated 8.04 and now when i downloaded skype it said under the package installer STATUS: Error wrong architecture 'i386'


although on skypes website it did say Ubuntu 7.04 so how do i get it to work on 8.04

---

### Post by dominiquec on 2008-07-03
I'll bet your running the 64-bit version of Ubuntu.  Am I right? :)

Have a look at this: [http://ubuntuforums.org/showthread.php?t=432295&highlight=skype](http://ubuntuforums.org/showthread.php?t=432295&highlight=skype)

---

### Post by iaculallad on 2008-07-03
Are you using 64-bit Ubuntu version? You can force 32-bit packages to install by:

```
sudo dpkg -i --force-architecture your_skype_package.deb
```

---

### Post by goforlinux on 2008-07-03
can you kind of tell me how to do that im kind of new and yes its the 64 bit edition thanks

---

### Post by goforlinux on 2008-07-03
it works thanks so so much guys so helpful thanks :)

---

### Post by iaculallad on 2008-07-03
> **goforlinux said:**
> can you kind of tell me how to do that im kind of new and yes its the 64 bit edition thanks

Click on this [link]("http://www.skype.com/go/getskype-linux-ubuntu") to download the Skype Ubuntu version and save it on your Desktop.

Assuming you had successfully downloaded the file linked above, perform the following steps below using your terminal:

Change Directory to your Desktop:

```
cd ~/Desktop
```

Force install the skype pakcage:

```
sudo dpkg -i --force-architecture skype-debian_2.0.0.72-1_i386.deb
```

That should do it.

EDIT: Just ignore this post, late reply.

---

### Post by sonofusion82 on 2008-07-03
anyway...  a better way to install Skype is to add skype's repo into apt.
This way, we will also get updates automatically. See [https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

