---
title: "Broken package problem"
date: 2007-11-28
forum: Installation &amp; Upgrades
---

### Post by ethang on 2007-11-28
I started to download and install the java package with adept manager.  However, my internet went down part way through.  It stopped downloading and was broken.  I have tried to uninstall, reinstall, and even purging.  None of it works, and I still have the broken package.

---

### Post by PmDematagoda on 2007-11-28
Do:-

```
sudo dpkg --configure -a
```

To try and fix the broken packages.

---

### Post by qpieus on 2007-11-28
try```
sudo apt-get install -f
```
this should fix broken packages. it's worked a few times for me.

---

### Post by ethang on 2007-12-05
thanks for your help

---

### Post by Jumpmasterrt on 2007-12-06
I just found a Perl update that has done the same to me. I've used
```
sudo apt-get install -f
``` but it didn't fix it.

Here's the output
```
me@my-machine:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  samba-doc
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  perl-modules
The following packages will be upgraded:
  perl-modules
1 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B/2310kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 106472 files and directories currently installed.)
Preparing to replace perl-modules 5.8.8-7build1 (using .../perl-modules_5.8.8-7ubuntu0.1_all.deb) ...
Unpacking replacement perl-modules ...
dpkg: error processing /var/cache/apt/archives/perl-modules_5.8.8-7ubuntu0.1_all.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/perl-modules_5.8.8-7ubuntu0.1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Jumpmasterrt on 2007-12-06
My whole package list is jacked up. It won't let me do anything.

---

### Post by Don Gatto on 2007-12-06
Hello everybody!

Jumpmasterrt, I have a similar problem as you. I needed some Perl packages, but mine were old. I downloaded the new one, tried to install, seems OK, got an error message in the end. (Forgot to check the version numbers. (I don't have internet at home, have to check the dependencies manually.)) Now my perl-base is broken, if I'd want to remove it (and then install again) I have to uninstall about half of the system as well.
So now we just sit here and wait someone to help us, don't we? :)

[A lame problem was here, solved.]

Thanks anyone who helps in anticipation.

---

### Post by PmDematagoda on 2007-12-06
Don Gatto, in order to fix your problem here is what you must do:-

1) Get the proper perl-base package from [Ubuntu packages]("http://packages.ubuntu.com/"), **make sure** that you get the right package version for the right version of Ubuntu.

2) After you download it, open up a terminal and do:-

```
sudo dpkg -i --force-downgrade nameofdeb.deb
```

That should fix your problem.

To Jumpmasterrt, try:-
```

sudo rm /var/cache/apt/archives/perl-modules_5.8.8-7ubuntu0.1_all.deb
```

and then do:-

```
sudo apt-get update
```

That could solve your problem.

---

### Post by Jumpmasterrt on 2007-12-06
PMD,

I tried fixing the broken packages but when I did it erased my whole Gnome Gui. That sucked. 

It's the Perl Packages "Larry Wall's Practical Extraction and Report Language" and "Pathalogically Eclectic Rubish Lister"

Those names seem like malicious packages to me..... but I'm too new to know.

---

### Post by PmDematagoda on 2007-12-06
Yes, I know that when you try and solve those dependencies manually you do face that problem. I faced it myself. So in your case, use the solution I gave to Don Gatto, it should work for you as well.

---

### Post by Don Gatto on 2007-12-07
PmDematagoda, thank you. (I will *do* try this at home. :) )

[A lame question was asked here again. Sorry.]

---

