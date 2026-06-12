---
title: "Error Messages during upgrade"
date: 2013-01-25
forum: Installation &amp; Upgrades
---

### Post by volkerbradley on 2013-01-25
When I perform sudo apt-get upgrade, I see the following error message and don't know how to correct the errors:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  libdrm2 libgl1-mesa-dri libgl1-mesa-dri:i386
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/7,939 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
(Reading database ... 367043 files and directories currently installed.)
Preparing to replace libdrm2:amd64 2.4.39-0ubuntu1 (using .../libdrm2_2.4.39-0ubuntu1_amd64.deb) ...
Unpacking replacement libdrm2:amd64 ...
dpkg: error processing /var/cache/apt/archives/libdrm2_2.4.39-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libdrm2/changelog.Debian.gz', which is different from other instances of package libdrm2:amd64
No apport report written because MaxReports is reached already
                                                              Preparing to replace libgl1-mesa-dri:amd64 9.0-0ubuntu1 (using .../libgl1-mesa-dri_9.0-0ubuntu1_amd64.deb) ...
Unpacking replacement libgl1-mesa-dri:amd64 ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa-dri_9.0-0ubuntu1_amd64.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libgl1-mesa-dri/changelog.Debian.gz', which is different from other instances of package libgl1-mesa-dri:amd64
No apport report written because MaxReports is reached already
                                                              Preparing to replace libgl1-mesa-dri:i386 9.0-0ubuntu1 (using .../libgl1-mesa-dri_9.0-0ubuntu1_i386.deb) ...
Unpacking replacement libgl1-mesa-dri:i386 ...
dpkg: error processing /var/cache/apt/archives/libgl1-mesa-dri_9.0-0ubuntu1_i386.deb (--unpack):
 trying to overwrite shared '/usr/share/doc/libgl1-mesa-dri/changelog.Debian.gz', which is different from other instances of package libgl1-mesa-dri:i386
No apport report written because MaxReports is reached already
                                                              dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libdrm2_2.4.39-0ubuntu1_amd64.deb
 /var/cache/apt/archives/libgl1-mesa-dri_9.0-0ubuntu1_amd64.deb
 /var/cache/apt/archives/libgl1-mesa-dri_9.0-0ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

How can I upgrade these three files and remove the error messages?
Thanks

---

### Post by SlugSlug on 2013-01-25
Can you post in CODE tages (the hash # button)

the output of

```
df -h
```

---

### Post by volkerbradley on 2013-01-25
Hi SlugSlug,
I'm sorry.  I do't understand:
What are CODE tages?
Where is the hash # button?
What do I do with df -h?
Thanks

---

### Post by SlugSlug on 2013-01-25
When you hit reply you can then click on the # button & post your output in between the CODE tags so its easier to read

type 
```
df -h
```

in Terminal this can be found in your menu

---

### Post by volkerbradley on 2013-01-25
Sorry that I cannot find the # button anywhere on this page.  Sure wished I did.  Don't mean to bug anyone.
df -h returns:

Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/laptop-root  139G  109G   23G  83% /
udev                     3.9G  4.0K  3.9G   1% /dev
tmpfs                    1.6G  956K  1.6G   1% /run
none                     5.0M     0  5.0M   0% /run/lock
none                     3.9G  220K  3.9G   1% /run/shm
none                     100M   28K  100M   1% /run/user
/dev/sda1                228M   96M  120M  45% /boot

---

### Post by SlugSlug on 2013-01-25
ok try

```
sudo apt-get update; sudo apt-get autoclean; sudo apt-get upgrade; sudo apt-get autoremove

```

---

### Post by harpal on 2013-01-25
Clean your apt cache and then try again. This might help.

---

### Post by volkerbradley on 2013-01-25
> **SlugSlug said:**
> ok try

```
sudo apt-get update; sudo apt-get autoclean; sudo apt-get upgrade; sudo apt-get autoremove

```

I gave all of the commands you suggested and then followed them with
```
 sudo apt-get update and sudo apt-get upgrade
```
At that point I am still seeing the error message that I posted earlier.

---

### Post by SlugSlug on 2013-01-25
```
sudo mv /usr/share/doc/libdrm2/changelog.Debian.gz /usr/share/doc/libdrm2/changelog.Debian.gz.old && sudo mv /usr/share/doc/libgl1-mesa-dri/changelog.Debian.gz /usr/share/doc/libgl1-mesa-dri/changelog.Debian.gz.old && sudo mv /usr/share/doc/libgl1-mesa-dri/changelog.Debian.gz /usr/share/doc/libgl1-mesa-dri/changelog.Debian.gz.old
```

followed by 

```
sudo apt-get upgrade
```


if (and only if!) this works 

```
sudo rm /usr/share/doc/libgl1-mesa-dri/*.old
```

---

### Post by volkerbradley on 2013-01-25
Thank you very much for your continued willingness to help.
I gave the first command that you suggested. Here is the output:
```
volker@laptop:~$ sudo mv /usr/share/doc/libdrm2/changelog.Debian.gz /usr/share/doc/libdrm2/changelog.Debian.gz.old && sudo mv /usr/share/doc/libgl1-mesa-dri/changelog.Debian.gz /usr/share/doc/libgl1-mesa-dri/changelog.Debian.gz.old && sudo mv /usr/share/doc/libgl1-mesa-dri/changelog.Debian.gz /usr/share/doc/libgl1-mesa-dri/changelog.Debian.gz.old
mv: cannot stat `/usr/share/doc/libgl1-mesa-dri/changelog.Debian.gz': No such file or directory 
```
Should I continue with the second and third commands you suggested?

---

### Post by SlugSlug on 2013-01-25
yep go ahead with others

 my bad posted same thing twice

---

### Post by volkerbradley on 2013-01-25
Yes, that worked!!  Thank you very much for helping me.
Here is the output now:
```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by SlugSlug on 2013-01-25
no prob :popcorn:

---

