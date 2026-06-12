---
title: "KUbuntu &amp; apt problems"
date: 2006-03-20
forum: Installation &amp; Upgrades
---

### Post by BStevens on 2006-03-20
I am sure that this is not a new problem but I was unable to find the answer searching through lists and via google.

I have just installed kubuntu and I am trying to set up the apt system and because of errors have reduces sources.list to:
## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted  
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main restricted  

I have set the bash.bashrc to have export http_proxy=".." according to the proxy adress published by the company

but get the following when doing apt-get update

apt-get update
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
  Temporary failure resolving 'archive.ubuntu.com'
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Temporary failure resolving 'archive.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

The browser can find the pages, so there is some network connectivity.

Please can any one suggest what I have done wrong.

Thank you

---

### Post by gnu2tux on 2006-03-20
I've never used apt via a proxy but I would imagine it should be fairly transparent.

As an alternative way around this, first ensure that your KDE settings for internet access thru your proxy are ok in the control centre (eg, you can access the internet ok with Konqueror).

Once you have done that, try using the tool 'adept' to download your packages, rather than straight apt. If you don't have adept then try synaptic.

---

### Post by BStevens on 2006-03-20
Thanks,

I have checked with Konqerer and can get out to the web, including the update site.

I have also looked at adept as a package manager and the update part, but they seem to give little feed back, and the package manager, does not list emacs or kile that I want.

I was starting with update as a simple command that should make sure my base distribution is upto date, before moving on to get other packages.

---

### Post by trejo23 on 2006-03-20
i have the exact problem as you mate i still have tried alot of things i am running through the networks proxy i can use browser and go to these archives but i cant use synaptic or apt-get to get the packages for breezy i have tried modifying the sources.list file as another way and still no luck i hope we can find a solution soon.

---

### Post by jude254 on 2006-05-11
I have the same problem as you guys. What I have tried to do was

1) change my source list
2) update either thru therminal or fetch updates
3) configure proxy thru the terminal

still not getting any result.
I can easily connect to the internet, and browse the net, but cannot find all the packages I want in Adept  nor use any apt-get functions in the terminal

If I get to know what it is that's wrong, Ill remember to post it here...

---

### Post by jude254 on 2006-05-11
This has solved my problem for now...though I dont know if I have to do it everytime I want to update:

"set an environment variable in your root terminal window prior to running apt-get. Here's the syntax:
[B]
export http_proxy=http://my.proxy.server:port/[/B]

Hope this helps

---

### Post by jude254 on 2006-05-11
the smilie is  server : port#

---

