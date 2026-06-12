---
title: "installing gcc3.4, g++3.4, g773.4 on Ubuntu 10.10"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by LMHmedchem on 2011-03-28
I really need to install gcc 3.4, along with g++ 3.4 and g77 3.4 on my Ubuntu 10.10 x86_64 distro. It is astonishing that gcc 3 is no longer available in Ubuntu, when most other distros have a compatibility package at least. I have downloaded the necessary .deb files from the hardy repository, but they cannot be installed individually because there is no installation order that will solve the dependencies. I have tried adding the downloaded packages to the package manager with file > add downloaded packages, but all of the files are greyed out. I added the hardy repository to the list of software sources, but that doesn't make gcc3 available anywhere, unless I did it wrong. I cannot install with apt, since there is no g77 package in the repository.

It appears as if I have managed to get gcc3 installed, but I cannot get g++3 or g77 installed and I really could use some assistance.

[COLOR=Navy]**LMHmedchem**[/COLOR]

---

### Post by LMHmedchem on 2011-03-30
No suggestions on this one? I can't be the only Ubuntu 10* user who needs gcc3. Can I just download and install the packages from gnu, or would that cause conflicts? My basic understanding of Liunx is that, in theory, you can have as many of whatever installed wherever you want it. Your software just has to point to what it needs. It's a bit unsettling to see so many things finding there way into Ubuntu that can't be un-installed. There are many apps that are install in the default config, but I find if I get rid of them, I loose gnome, or something else I can't do without. It looked to me that I couldn't uninstall wireless support without uninstalling the kernel, which makes no sense at all. What ever happened to linux being the OS you can configure just the way you want it???

**[COLOR=Navy]LMHmedchem[/COLOR]**

---

### Post by SISheetov on 2011-04-04
I used on my system (Ubuntu 11.04) a simple advice from here:
[http://ubuntuforums.org/showpost.php?p=6160836&postcount=14](http://ubuntuforums.org/showpost.php?p=6160836&postcount=14)
--begin citation:

I just added the following lines to the source.list after the lines of universe repositories for intrepid:

     ```

deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hardy universe  
deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hardy universe  
deb [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hardy-updates universe  
deb-src [http://hu.archive.ubuntu.com/ubuntu/](http://hu.archive.ubuntu.com/ubuntu/) hardy-updates universe 

```(Note: *hu* should be changed to your country code i.e. *us*, *gb*, *de*, *ru*, etc.)

after that in the terminal:

 ```

sudo aptitude update 
sudo aptitude install g77 

```-- end citation.

The compilation g77 with -c flag started working, but I was getting

```

/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status

```while building an executable.

For me everything started working OK after I have done (as a root):

```

ln -s /lib/x86_64-linux-gnu/libgcc_s.so.1 /lib/libgcc_s.so

```The last operation would put libgcc_s where ld expects it to find.

---

### Post by oh6eh on 2011-11-22
This was suggested by my user, I am bit wary... Did this break other compilers or libraries. What about during an upgrade?

---

### Post by jalirious on 2012-03-27
Catch 22.

---

### Post by raja.genupula on 2012-03-27
ok look for that dependencies  package in synaptic and install it from there  and then try again .

---

