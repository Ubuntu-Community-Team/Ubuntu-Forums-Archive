---
title: "The package system is broken"
date: 2012-06-29
forum: Installation &amp; Upgrades
---

### Post by Evocashious on 2012-06-29
I'm completely new to Linux. I have just installed 11.10 If I'm correct. I would have liked to have my 10.10 because my friend said it was good, but it kept crashing for some reason. Anyways, I just got it installed and most things run okay. But when I tried to install updates and what not I get a popup saying 

The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f The following packages have unmet dependencies:

libc6-dev: Depends: libc6 (= 2.13-20ubuntu5) but 2.13-20ubuntu5 is installed
           Depends: libc-dev-bin (= 2.13-20ubuntu5) but 2.13-20ubuntu5.1 is installed

I tried the Terminal command and got this.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc-bin libc6 libc6-dev
Suggested packages:
  glibc-doc
The following packages will be upgraded:
  libc-bin libc6 libc6-dev
3 upgraded, 0 newly installed, 0 to remove and 125 not upgraded.
Need to get 0 B/9,771 kB of archives.
After this operation, 28.7 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
(Reading database ... 125595 files and directories currently installed.)
Preparing to replace libc6-dev 2.13-20ubuntu5 (using .../libc6-dev_2.13-20ubuntu5.1_i386.deb) ...
Unpacking replacement libc6-dev ...
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error
dpkg-deb: error: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libc6-dev_2.13-20ubuntu5.1_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/include/i386-linux-gnu/bits/confname.h'
Preparing to replace libc-bin 2.13-20ubuntu5 (using .../libc-bin_2.13-20ubuntu5.1_i386.deb) ...
Unpacking replacement libc-bin ...
dpkg-deb (subprocess): failed to read on buffer copy for failed to write to pipe in copy: Input/output error
dpkg-deb: error: subprocess paste returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libc-bin_2.13-20ubuntu5.1_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/bin/tzselect'
Errors were encountered while processing:
 /var/cache/apt/archives/libc6-dev_2.13-20ubuntu5.1_i386.deb
 /var/cache/apt/archives/libc-bin_2.13-20ubuntu5.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I'm really hoping someone can help me out.

---

### Post by drmrgd on 2012-06-29
Try running:

```
sudo apt-get clean
```

and then try running the install  / upgrade again.

Also, out of curiosity, your root partition on the hard drive is not full, is it?

---

### Post by Evocashious on 2012-06-29
So far it seems to be working. I restricted the downloads to important ones just in case it tried to mess up again. Also on your question about the root. I don't think so. How should I go about checking.

---

### Post by drmrgd on 2012-06-29
> **Evocashious said:**
> So far it seems to be working. I restricted the downloads to important ones just in case it tried to mess up again. Also on your question about the root. I don't think so. How should I go about checking.

From the terminal, you can run:

```
df -h
```

That will break down your partitions, their sizes, and how much space is used on them.

It sounds like clearing the apt cache was good enough to fix it though.

---

### Post by Evocashious on 2012-06-29
I was able to install all but 1 update. The software center is still saying it wont work.. I'll post results to your command in a second sorry for taking so long.

---

### Post by Evocashious on 2012-06-29
Okay ran the apt-get clean thing again. Was able to get the last major update. I'm going to try installing all the smaller updates and hope I get to use the software center. I'm currently using another computer so I can't copy and paste those results yet. However based on how fast the memory is gone I'd say I've got very little space there. I had to reboot cause it froze. Then it shut off the wifi so I had to remove the softblock on it. Back to installations.

---

