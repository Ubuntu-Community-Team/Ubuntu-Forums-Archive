---
title: "Could not Initialize package information"
date: 2011-05-09
forum: Installation &amp; Upgrades
---

### Post by pavlovgg on 2011-05-09
Greetings. 

Today, on Ubuntu 11.04, when attempting to update, this error message appeared in update-manager:


```
An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.
```


The same appears in Terminal upon sudo apt-get update/upgrade:

```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```


Would anyone please suggest what the solution to this issue may be?

---

### Post by mörgæs on 2011-05-09
What exactly did you enter into the terminal? Have you tried booting the machine and running

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```?

---

### Post by pavlovgg on 2011-05-10
> **mörgæs said:**
> What exactly did you enter into the terminal? Have you tried booting the machine and running

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```?


Greetings. Thank you for the reply. Here is what I get

```
georgi@Georgi:~$ sudo apt-get clean
[sudo] password for georgi: 
georgi@Georgi:~$ sudo apt-get update
Ign http://extras.ubuntu.com natty InRelease
Ign http://archive.ubuntu.com natty InRelease
Ign http://archive.ubuntu.com natty-security InRelease
Ign http://archive.ubuntu.com natty-updates InRelease
Get:1 http://extras.ubuntu.com natty Release.gpg [72 B]
Ign http://archive.ubuntu.com natty-proposed InRelease
Hit http://archive.ubuntu.com natty Release.gpg
Hit http://extras.ubuntu.com natty Release
Hit http://archive.ubuntu.com natty-security Release.gpg
Get:2 http://archive.ubuntu.com natty-updates Release.gpg [198 B]
Get:3 http://archive.ubuntu.com natty-proposed Release.gpg [198 B]
Hit http://extras.ubuntu.com natty/main Sources
Hit http://archive.ubuntu.com natty Release    
Hit http://archive.ubuntu.com natty-security Release
Hit http://extras.ubuntu.com natty/main i386 Packages                 
Ign http://extras.ubuntu.com natty/main TranslationIndex
Get:4 http://archive.ubuntu.com natty-updates Release [27.2 kB]
Get:5 http://archive.ubuntu.com natty-proposed Release [27.2 kB]
Hit http://archive.ubuntu.com natty/main Sources                               
Hit http://archive.ubuntu.com natty/restricted Sources
Hit http://archive.ubuntu.com natty/universe Sources
Hit http://archive.ubuntu.com natty/multiverse Sources
Hit http://archive.ubuntu.com natty/main i386 Packages
Hit http://archive.ubuntu.com natty/restricted i386 Packages
Hit http://archive.ubuntu.com natty/universe i386 Packages
Hit http://archive.ubuntu.com natty/multiverse i386 Packages
Ign http://extras.ubuntu.com natty/main Translation-en_US
Ign http://extras.ubuntu.com natty/main Translation-en
Ign http://archive.ubuntu.com natty/main TranslationIndex
Ign http://archive.ubuntu.com natty/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty/restricted TranslationIndex
Ign http://archive.ubuntu.com natty/universe TranslationIndex
Hit http://archive.ubuntu.com natty-security/main Sources
Hit http://archive.ubuntu.com natty-security/restricted Sources
Hit http://archive.ubuntu.com natty-security/universe Sources
Hit http://archive.ubuntu.com natty-security/multiverse Sources
Hit http://archive.ubuntu.com natty-security/main i386 Packages
Hit http://archive.ubuntu.com natty-security/restricted i386 Packages
Hit http://archive.ubuntu.com natty-security/universe i386 Packages
Hit http://archive.ubuntu.com natty-security/multiverse i386 Packages
Ign http://archive.ubuntu.com natty-security/main TranslationIndex
Ign http://archive.ubuntu.com natty-security/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty-security/restricted TranslationIndex
Ign http://archive.ubuntu.com natty-security/universe TranslationIndex
Get:6 http://archive.ubuntu.com natty-updates/restricted i386 Packages [14 B]
Get:7 http://archive.ubuntu.com natty-updates/main i386 Packages [73.5 kB]
Get:8 http://archive.ubuntu.com natty-updates/multiverse i386 Packages [14 B]
Get:9 http://archive.ubuntu.com natty-updates/universe i386 Packages [26.9 kB]
Ign http://archive.ubuntu.com natty-updates/main TranslationIndex
Ign http://archive.ubuntu.com natty-updates/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty-updates/restricted TranslationIndex
Ign http://archive.ubuntu.com natty-updates/universe TranslationIndex
Get:10 http://archive.ubuntu.com natty-proposed/restricted i386 Packages [14 B]
Get:11 http://archive.ubuntu.com natty-proposed/main i386 Packages [60.3 kB]
Get:12 http://archive.ubuntu.com natty-proposed/multiverse i386 Packages [2,217 B]
Get:13 http://archive.ubuntu.com natty-proposed/universe i386 Packages [22.0 kB]
Ign http://archive.ubuntu.com natty-proposed/main TranslationIndex
Ign http://archive.ubuntu.com natty-proposed/multiverse TranslationIndex
Ign http://archive.ubuntu.com natty-proposed/restricted TranslationIndex
Ign http://archive.ubuntu.com natty-proposed/universe TranslationIndex
Ign http://archive.ubuntu.com natty/main Translation-en_US
Ign http://archive.ubuntu.com natty/main Translation-en
Ign http://archive.ubuntu.com natty/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty/multiverse Translation-en
Ign http://archive.ubuntu.com natty/restricted Translation-en_US
Ign http://archive.ubuntu.com natty/restricted Translation-en
Ign http://archive.ubuntu.com natty/universe Translation-en_US
Ign http://archive.ubuntu.com natty/universe Translation-en
Ign http://archive.ubuntu.com natty-security/main Translation-en_US
Ign http://archive.ubuntu.com natty-security/main Translation-en
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-security/multiverse Translation-en
Ign http://archive.ubuntu.com natty-security/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-security/restricted Translation-en
Ign http://archive.ubuntu.com natty-security/universe Translation-en_US
Ign http://archive.ubuntu.com natty-security/universe Translation-en
Ign http://archive.ubuntu.com natty-updates/main Translation-en_US
Ign http://archive.ubuntu.com natty-updates/main Translation-en
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-updates/multiverse Translation-en
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-updates/restricted Translation-en
Ign http://archive.ubuntu.com natty-updates/universe Translation-en_US
Ign http://archive.ubuntu.com natty-updates/universe Translation-en
Ign http://archive.ubuntu.com natty-proposed/main Translation-en_US
Ign http://archive.ubuntu.com natty-proposed/main Translation-en
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-en_US
Ign http://archive.ubuntu.com natty-proposed/multiverse Translation-en
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-en_US
Ign http://archive.ubuntu.com natty-proposed/restricted Translation-en
Ign http://archive.ubuntu.com natty-proposed/universe Translation-en_US
Ign http://archive.ubuntu.com natty-proposed/universe Translation-en
Fetched 240 kB in 5s (44.1 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
georgi@Georgi:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
georgi@Georgi:~$ 
```

---

### Post by mörgæs on 2011-05-10
Try this:

```
sudo rm /var/lib/apt/lists/* -vf
```

followed by the three commands above.

---

### Post by pavlovgg on 2011-05-10
Thank you sir. It all seems to be working now. 
Thank you.

---

### Post by mörgæs on 2011-05-10
You are welcome. Please mark the thread 'solved'.

---

### Post by monkeybanana on 2011-05-28
I love the forums thank you!

---

### Post by kiwibunt on 2011-06-28
I only needed to run sudo rm /var/lib/apt/lists/* -vf in the terminal to get updates working, thanks heaps

---

### Post by ajay.cse.nitjsr on 2011-11-05
> **kiwibunt said:**
> I only needed to run sudo rm /var/lib/apt/lists/* -vf in the terminal to get updates working, thanks heaps

thanks man it worked for me too......  :):popcorn:

---

### Post by bfb on 2012-01-18
Does not work for me...I get 
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory

---

### Post by mörgæs on 2012-01-18
What exactly does not work?

---

### Post by omjaijagdish on 2012-10-13
[LEFT]thanks a lot..... it worked 4 me too....:P
[/LEFT]

---

