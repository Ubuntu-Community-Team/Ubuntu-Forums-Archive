---
title: "software install/remove failures"
date: 2011-06-06
forum: Installation &amp; Upgrades
---

### Post by Rgibbons on 2011-06-06
I have been having problems with OpenOffice and wanted to try uninstalling and re-installing it to correct the problem, but when running the uninstall or re-install I get the error below. Any idea what is causing it?
[IMG]http://www.creativeartsphotography.com/public/Screenshot.png[/IMG]

---

### Post by Rubi1200 on 2011-06-06
First thing to check is whether the package mentioned in the error message is the only thing causing problems.

Post the output of this command please:

```
sudo dpkg --audit
```

---

### Post by Rgibbons on 2011-06-06
Sorry, I received no output at all.

---

### Post by Rgibbons on 2011-06-06
Now. I am getting the same error on upgrades or anything else I try to upgrade, remove or install. 

Do I need to reinstall the system software from scratch?

---

### Post by Rubi1200 on 2011-06-06
No, what you can try is the solution from here:
[http://ubuntuforums.org/showthread.php?t=1232143](http://ubuntuforums.org/showthread.php?t=1232143)

post # 7 seems to have figured it out.

Let me know if this works for you.

---

### Post by Rgibbons on 2011-06-06
Sorry, it didn't work. Below is the output after removing OpenOffice from the status list:

rodney@rodney-inspiron:/var/lib/dpkg$ sudo dpkg --configure -a
rodney@rodney-inspiron:/var/lib/dpkg$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ure
Suggested packages:
  cli-uno-bridge
The following NEW packages will be installed:
  ure
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 1,222kB of archives.
After this operation, 4,952kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main ure 1.6.0+OOo3.2.0-7ubuntu4.2 [1,222kB]
Fetched 1,222kB in 4s (263kB/s)
Preconfiguring packages ...
Selecting previously deselected package ure.
(Reading database ... 95%dpkg: unrecoverable fatal error, aborting:
 failed in buffer_read(fd): files list for package `pulseaudio-module-gconf': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
rodney@rodney-inspiron:/var/lib/dpkg$

---

### Post by Rgibbons on 2011-06-06
SMART is reporting a few bad sectors. Could that be causing the problem?

---

### Post by Rgibbons on 2011-06-06
Well, I have a real mess now. Synaptic Package manager is reporting 14 broken packages - all unfixable with the same error as before.

---

### Post by Rubi1200 on 2011-06-06
If SMART is reporting bad sectors that is never a good thing.

I think you need to try the procedure again and remove those packages from the status list and then try again.

But as a precaution save all important data now in the event you need to reinstall and/or the drive is failing.

---

### Post by Rgibbons on 2011-06-06
I tried again and even took all the packages out of the status file. Still same error. I have ordered a new hard drive, I just hate having to install and configure everything again.

---

