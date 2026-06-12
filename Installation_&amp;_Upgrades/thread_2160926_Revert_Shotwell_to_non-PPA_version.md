---
title: "Revert Shotwell to non-PPA version"
date: 2013-07-08
forum: Installation &amp; Upgrades
---

### Post by Dragonbite on 2013-07-08
I wanted to try out a newer Shotwell and so I added the yorba PPA to my Ubuntu Precise (12.04) ```
http://ppa.launchpad.net/yorba/ppa/ubuntu precise main
http://ppa.launchpad.net/yorba/ppa/ubuntu precise main (Source Code)
```

Some of it doesn't work or doesn't work very well and since this system is on an LTS schedule I want to remove the yorba PPA and return to the official packages in the Ubuntu repositories.

My initial thought is to [LIST=1]
[*]Remove the PPAs from the source list
[*]Remove Shotwell
[*]Install Shotwell (which would use the official repositories as the PPA would be removed)
[/LIST]

Before I run this, I want to ask if this is the preferred or best method or is there another way to do the same thing?

I am assuming that all of my configuration and picture database information should remain intact and accessible afterwards.

---

### Post by Frogs Hair on 2013-07-08
You may want to run the following after removing the ppa version of shotwell .```
sudo apt-get autoremove

``` This is also handy and there is a version in the repository.   [http://www.webupd8.org/2012/11/install-ppa-purge-with-multi-arch.html](http://www.webupd8.org/2012/11/install-ppa-purge-with-multi-arch.html)

---

### Post by eric-yorba on 2013-07-08
One thing to keep in mind: Like most apps, Shotwell cannot be downgraded to an earlier version.

---

### Post by Dragonbite on 2013-07-09
> **Frogs Hair said:**
> You may want to run the following after removing the ppa version of shotwell .```
sudo apt-get autoremove

``` This is also handy and there is a version in the repository.   [http://www.webupd8.org/2012/11/install-ppa-purge-with-multi-arch.html](http://www.webupd8.org/2012/11/install-ppa-purge-with-multi-arch.html)

That looks like a helpful tool in this instance. Ultimately, though, is it much more than just automating the "remove(ppa)->remove(application)->install(different source)" process?

> **eric-yorba said:**
> One thing to keep in mind: Like most apps, Shotwell cannot be downgraded to an earlier version.

Thanks.

---

### Post by Dragonbite on 2013-07-09
Darn. I removed the Yorba PPAs, removed Shotwell, updated and installed Shortwell and now I am getting ```

$ shortwell
shotwell: error while loading shared libraries: libgexiv2.so.1: cannot open shared object file: No such file or directory 
$ sudo apt-get install libgexiv2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libgexiv2

```

 Is this a hold-over from the previous version?  How do I clear it?

---

### Post by Dragonbite on 2013-07-09
Ok, so  I did a search, and tried to add the reference libraries ```
$ sudo apt-get install libgexiv2-1-dbg libgexiv2-dev libgexiv2-1
[sudo] password for drew: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgexiv2-1 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgexiv2-1-dbg : Depends: libgexiv2-1 (= 0.4.1-1build1) but 0.6.1-0precise1 is to be installed
 libgexiv2-dev : Depends: libgexiv2-1 (= 0.4.1-1build1) but 0.6.1-0precise1 is to be installed
E: Unable to correct problems, you have held broken packages.

```


Ahh.. just figured it out. Ran ```
sudo apt-get remove libgexiv2-1-dbg libgexiv2-dev libgexiv2-1

``` to clear it out and then ```
sudo apt-get install shotwell
``` and it pulled in the currently available requirements.

---

### Post by stinkeye on 2013-07-10
Normally you would just use ppa-purge to downgrade to official packages.
eg
```
sudo ppa-purge ppa:yorba/ppa
```

With shotwell, though, the library database used in the ppa version  is incompatible with the downgraded version and shotwell failed to start.
Had to delete ~/.shotwell and ~/.local/share/shotwell and in the process do what you didn't want.....
and lose "my configuration and picture database information"

---

### Post by Dragonbite on 2013-07-10
I did do a "clean" or "purge" to make sure I got the Shotwell configuration files and database before I manually removed and reinstalled the missing library.

It took a few hours for Shotwell to update the database but it seems to work now and display properly.

---

