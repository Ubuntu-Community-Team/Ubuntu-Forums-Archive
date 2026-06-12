---
title: "Unable to install anything..."
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by hopefulcd on 2010-11-17
Hi. Recently I've been receiving an error whenever I try to install any new program. I've searched for some time now and I'm not sure how to fix it. When installing a program, I immediately greeted with this error...

> installArchives() failed: dpkg: parse error, in file '/var/lib/dpkg/available' near line 17237 package 'openoffice.org-core': 
 `Breaks' field, missing package name, or garbage where package name expected 

This error is actually slightly different from another one that I was previously receiving involving 'var/lib/dpkg/status'  and the "Breaks" field issue. If anyone knows how to fix this it would be greatly appreciated!

---

### Post by Rubi1200 on 2010-11-17
Hi and welcome to the forums :)

Go to Applications > Accessories > Terminal and copy/paste the following commands in and run them (separately).

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

Let us know if there are any errors reported (copy/paste from the terminal and post back here).

Thanks.

---

### Post by hopefulcd on 2010-11-17
here's the results:

hopefulcd@hopefulcd-cpu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
hopefulcd@hopefulcd-cpu:~$ sudo dpkg --configure -a
dpkg: parse error, in file '/var/lib/dpkg/available' near line 17237 package 'openoffice.org-core':
 `Breaks' field, missing package name, or garbage where package name expected

---

### Post by Rubi1200 on 2010-11-17
Okay,

then try this please:

```
sudo dpkg --clear-avail && sudo apt-get update
```

---

### Post by hopefulcd on 2010-11-17
Wow! It works again! I just installed a program through the package manager without any errors. Thanks a lot for your help!

---

### Post by Rubi1200 on 2010-11-17
You are more than welcome :)

Please mark this thread Solved using the Thread Tools near the top of the page.

Marking this solved means that other users with similar errors can find a working solution.

Thanks and enjoy!

---

### Post by sikander3786 on 2010-11-17
> Marking this solved means that other users with similar errors can find a working solution.


And also volunteers looking to help others don't spend time reading this whole post ;-)

Regards.

---

