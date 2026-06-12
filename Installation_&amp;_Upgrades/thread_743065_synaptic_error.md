---
title: "synaptic error"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by geokar on 2008-04-02
Hi guys i need some help here i keeep getting this error evry tym am installing thru the sysnaptic package manager "E: /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb: files list file for package `language-pack-en' contains empty filename"
can anyone help in debugging this problem 
thanx

---

### Post by erginemr on 2008-04-02
I suggest you to delete the offending file first:
```
sudo rm -i /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb
```
and retry.

---

### Post by geokar on 2008-04-03
Thanks for the help but still not working even after running th command "sudo rm -i /var/cache/apt/archives/libgtkglext1_1.2.0-0ubuntu1_i386.deb
"  this is what the error looks like when i try installin via command line

georgeyonni@georgeyonni-laptop:~$ sudo apt-get install ices2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  pcsx-bin libboost-regex1.34.1 python-pychart python-quixote1 libxcb-xv0
  psemu-drive-cdrmooby psemu-sound-alsa psemu-sound-oss psemu-input-padjoy
  libxcb1 libfltk1.1 libxcb-shape0 python-pysqlite2 libzrtpcpp-0.9-0
  python-medusa libccrtp1-1.5-1 libadns1 libxcb-shm0 libxine1
Use 'apt-get autoremove' to remove them.
Suggested packages:
  icecast2
The following NEW packages will be installed:
  ices2
0 upgraded, 1 newly installed, 0 to remove and 238 not upgraded.
Need to get 56.0kB of archives.
After unpacking 254kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe ices2 2.0.1-5 [56.0kB]
Fetched 56.0kB in 1m47s (521B/s)                                               
Selecting previously deselected package ices2.
(Reading database ... dpkg: error processing /var/cache/apt/archives/ices2_2.0.1-5_i386.deb (--unpack):
 files list file for package `language-pack-en' contains empty filename
Errors were encountered while processing:
 /var/cache/apt/archives/ices2_2.0.1-5_i386.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
georgeyonni@georgeyonni-laptop:~$ 
please help these error keep recurring every time am installing a software rendering my Synaptic Package Manager unusable

---

### Post by erginemr on 2008-04-03
The heart of the dpkg software system is the file "/var/lib/dpkg/status", which can be regarded as the main database for all installed packages in your system. I guess there is something wrong in the listing for the package "language-pack-en". 

In this context, can you please issue this command from the terminal:
```
cat /var/lib/dpkg/status | grep -A 20 -i "Package: language-pack-en" > output.txt
```

This will create a file "output.txt" in your home folder, which should contain the relevant lines (i.e. package details, dependencies, etc.) for two packages, "language-pack-en" and "language-back-en-base". Please attach this "output.txt" file to your next post. I want to compare them with the lines in my system.

---

### Post by geokar on 2008-04-07
here is the fikle you saked for

---

### Post by erginemr on 2008-04-07
Unfortunately, we are not looking at the right direction, because the relevant parts in my **/var/lib/dpkg/status** file are identical, except I have leter versions of the same software list, which is because you cannot update your system.

There is another file to which this problem might be related: **/var/lib/dpkg/info/language-pack-en.list**

Can you please post what is inside this file as well?
```
cat /var/lib/dpkg/info/language-pack-en.list > output.txt
```

---

### Post by geokar on 2008-04-09
here is the othe file you wanted

---

### Post by erginemr on 2008-04-09
Strange output you've got there...

Here is the same file in my system:
```
/.
/usr
/usr/share
/usr/share/locale-langpack
/usr/share/locale-langpack/en_GB
/usr/share/locale-langpack/en_GB/LC_MESSAGES
/usr/share/locale-langpack/en_GB/LC_MESSAGES/hello.mo
/usr/share/doc
/usr/share/doc/language-pack-en
/usr/share/doc/language-pack-en/copyright
/usr/share/doc/language-pack-en/changelog.gz
```

So, I suggest you to take a copy of that file with:
```
cp /var/lib/dpkg/info/language-pack-en.list ~/language-pack-en.list
```
(which will create a backup file with the same name in your home folder). And edit the file:
```
gksudo gedit /var/lib/dpkg/info/language-pack-en.list
```
delete everything inside and copy and paste the text I gave above into the file. Save the file and exit. 

Then issue:
```
sudo dpkg --configure -a
sudo apt-get install -f
```
to put everything back in order.

And finally:
```
sudo apt-get update
sudo apt-get upgrade
```
to -hopefully- update your system.

---

### Post by geokar on 2008-04-14
same problem persist i donno whatehr to wait for Ubuntu 8.04 to upgrade coz it aint going aways

---

### Post by erginemr on 2008-04-14
Alas... :( 

OK, then. But I believe, you should still solve this problem for a proper distro upgrade, or do a clean install of Hardy...

---

