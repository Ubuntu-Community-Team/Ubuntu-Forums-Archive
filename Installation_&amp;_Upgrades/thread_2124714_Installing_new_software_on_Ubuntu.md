---
title: "Installing new software on Ubuntu"
date: 2013-03-11
forum: Installation &amp; Upgrades
---

### Post by galfly on 2013-03-11
Hi,

What's the best way to install new software? I mean where?

I downloaded the binary for some software, lets say dummy (I don't think there's a dummy package, I'm using it in a "you-name-it" kinda way). I verified the cheksum, unzipped and extracted it in a local directory under my home. But I want all users to be able to run this software from anywhere with a dummy alias.

So, I created a symbolic link to the executable under /usr/local/bin. And I exported path settings in an s.sh file under /etc/init.d. This didn't work.

Alternatively, I extracted the executable under /usr/local/ directly, instead of using a link. I still have the s.sh file. I still can't run the executable, and I'm not sure if this is the most "elegant" way of installing it.

Thanks

---

### Post by ManamiVixen on 2013-03-11
Ubuntu Software Center is where you can install stuff. the icon looks like a shopping bag and is on the sidebar in Unity or the main Applications menu in Gnome.

Manual install of files and programs is not reccomended as usually there could be dependancy problems.

---

### Post by cortman on 2013-03-11
Whoa, installing software in Ubuntu is a lot easier than you think, I believe. :)
You can browse the software center if you like, or use apt-get to install, and apt-cache to search for available software. See the man pages on both for more info.
Good luck!

---

### Post by fantab on 2013-03-12
Now, what do you mean by "executable"? 
Most of the Applications you need are in the Ubuntu repositories. You can 'elegantly' install them from 'Ubuntu Software Center' (available by default on any ubuntu) or with 'Synaptic Package Manager' (which you need to install first). 

However, there are certain packages that may not be available from the 'repositories', for such applications you need a .deb file (which is an executable install package file for Debian based Distros, like Ubuntu). Just double clicking the .deb file will install it via 'Software Center'. Simple.

If .deb is not available then you need .tar.gz or .tar.bz2 file for that application and we are on our own to install it.

To install .tar.gz or .tar.bz2 (which, by the way, are compressed files) follow the steps below from the terminal:

```
$ cd [I]packagefolder
[/I]$ tar xvzf *packagename*.tar.gz  (if the file is .tar.gz) OR
$ tar xvjf packagename.tar.bz2  (if the file is .tar.bz2)
$ ./configure
$ make
$ make install
```

---

### Post by Cheesemill on 2013-03-12
Take a read of this...

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

