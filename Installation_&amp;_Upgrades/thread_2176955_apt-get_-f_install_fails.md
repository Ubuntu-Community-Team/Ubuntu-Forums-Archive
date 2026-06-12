---
title: "apt-get -f install fails"
date: 2013-09-26
forum: Installation &amp; Upgrades
---

### Post by juan7 on 2013-09-26
I am having issues installing packages on my server. All failures are related to the fact that linux-image-3.5.0-39-generic is not installed.  I have *-37-* and I am running *-40-* in /boot, but no *-39-*


uname -a
Linux ePay 3.5.0-40-generic #62~precise1-Ubuntu SMP Fri Aug 23 17:38:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


root@ePay:/home/juang/downloads# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-32-generic linux-headers-3.5.0-27-generic linux-headers-3.5.0-30-generic linux-headers-3.5.0-28-generic
  linux-headers-3.5.0-23-generic linux-headers-3.5.0-23 linux-headers-3.5.0-30 linux-headers-3.5.0-31 linux-headers-3.5.0-32
  linux-headers-3.5.0-27 linux-headers-3.5.0-28 linux-headers-3.5.0-34 linux-headers-3.5.0-31-generic
  linux-headers-3.5.0-34-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-image-generic-lts-quantal
The following packages will be upgraded:
  linux-image-generic-lts-quantal
1 upgraded, 0 newly installed, 0 to remove and 80 not upgraded.
2 not fully installed or removed.
Need to get 0 B/2,402 B of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of linux-image-generic-lts-quantal:
 linux-image-generic-lts-quantal depends on linux-image-3.5.0-39-generic; however:
  Package linux-image-3.5.0-39-generic is not installed.
dpkg: error processing linux-image-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-generic-lts-:
 linux-generic-lts-quantal depends on linux-image-generic-lts-quantal; however:
  Package linux-image-generic-lts-quantal is not configured yet.
dpkg: error processing linux-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-generic-lts-quantal
 linux-generic-lts-quantal
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by philinux on 2013-09-26
Just run sudo dpkg -- configure -a and see what errors that brings up.

---

### Post by juan7 on 2013-09-27
# dpkg --configure -a
dpkg: dependency problems prevent configuration of linux-image-generic-lts-quantal:
 linux-image-generic-lts-quantal depends on linux-image-3.5.0-39-generic; however:
  Package linux-image-3.5.0-39-generic is not installed.
dpkg: error processing linux-image-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-lts-quantal:
 linux-generic-lts-quantal depends on linux-image-generic-lts-quantal; however:
  Package linux-image-generic-lts-quantal is not configured yet.
dpkg: error processing linux-generic-lts-quantal (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-generic-lts-quantal
 linux-generic-lts-quantal

---

### Post by varunendra on 2013-09-27
> **juan7 said:**
>                                                              Errors were encountered while processing:
 linux-image-generic-lts-quantal
 linux-generic-lts-quantal

Both the offending packages above are just metapackages, so purging them is not going to harm anything. Let's just get rid of them -
```
sudo apt-get purge linux-image-generic-lts-quantal linux-generic-lts-quantal
sudo apt-get update
sudo apt-get dist-upgrade
```
Everyone happy now?

Oh, and a warm welcome to the forums juan7 ! :)

**PS:**
For posting command outputs, please use 'Code' tags (follow the "Using Code Tags" link in my signature to see how). It preserves the formatting and makes the post look cleaner and more readable.

---

### Post by juan7 on 2013-09-27
It worked!
Thanks to both, Philinux and Varun.

Sorry about posting results using Quick Reply. Next time I'll use the Code Tags.
And thank you for your welcome! It felt good in the midst of despair. It felt great when my issue was solved this promptly!
Juan

---

### Post by varunendra on 2013-09-28
> **juan7 said:**
> It worked!
Thanks to both, Philinux and Varun.
Congrats ! And you're welcome :)
Please mark the thread as [SOLVED] using "Thread Tools" link above the top post.

> Sorry about posting results using Quick Reply. Next time I'll use the Code Tags.
No problem, I use the quick reply box all the time. Here's how you do it in quick reply box -

Add **[noparse]```
[/noparse]** in the beginning and **[noparse]
```[/noparse]** at the end of the text that you want to put into the 'Code' box. For example -

[noparse]```
[/noparse]
[COLOR="#000080"]My gibberish output code here[/COLOR]
[noparse]
```[/noparse]

After submitting the post, it will look like this -
```
[COLOR="#000080"]My gibberish output code here[/COLOR]
```

Hope you find it useful :)

....and don't forget to mark it as [SOLVED] now :P

---

