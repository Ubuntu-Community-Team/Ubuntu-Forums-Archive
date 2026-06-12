---
title: "[SOLVED] linux headers 2.6.24-18 ?"
date: 2008-06-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Oldsoldier2003 on 2008-06-05
Im installing Intrepid in a VM (VirtualBox) and everything is working just fine until I attempt to install the guest additions. Apparently the headers are not available for 2.6.24-18-generic do I need to enable any special repos or is this just a "wait and see if the get uploaded" situation?

---

### Post by Joeb454 on 2008-06-05
I'm guessing it's a wait and see game :)

Did you check hardy-proposed?

---

### Post by Eclipse. on 2008-06-06
.24-18 wont appear in intrepid, it wont be uploaded.Infact .24-17 isnt in either.Devel versions use the kernel the previous distro ships with untill a build of the kernel thats going to be used in that version is available.(.26)

If you want the current .26 kernel avilable then have a look at the kernel teams ppa:

[https://launchpad.net/~kernel-ppa/+archive]("https://launchpad.net/%7Ekernel-ppa/+archive")

I expect a .26 kernel to appear soon in the repos.

Also you could have a look at the kernel teams git repo, to clone the repo then type that into a kernel:

```
git-clone git://kernel.ubuntu.com/ubuntu/ubuntu-intrepid.git
```

---

### Post by ShirishAg75 on 2008-06-06
looking forward for the .26 kernel as well.

---

