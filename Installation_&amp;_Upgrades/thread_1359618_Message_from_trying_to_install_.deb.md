---
title: "Message from trying to install .deb"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by spursncowboys on 2009-12-19
I'm trying to install sopcast and when I tried I got this message when I tried to open it with gdebi package installer.
```
/tmp/sp-auth_3.2.6_all-2.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences.
```
When I tried to install it with ```
sudo apt-get install sp-auth_3.2.6_all-2.deb
```
and ```
sudo dpkg -i sp-auth_3.2.6_all.deb 

``` It says that cannot access. Any ideas what the problem is and what I can do to fix it. Also is there a better program than gdebi?

---

### Post by RedSingularity on 2009-12-19
You need to change to the directory of the file before using dpkg.  Did you do that?

---

### Post by USB_NL on 2009-12-19
hello


Not the correct folder could be the problem.
here are some commandline options:

use 
ls 
to show folders and files

use
cd foldername
to go down the tree into in that folder

use
cd ..
to move up one folder in the treepath

use cd\
to go up to "main" folder or the root of the tree


  I hope this wil solve the problem you have.

---

### Post by spursncowboys on 2009-12-20
Thanks for both replies. The first one I went to the website and just clinked on the download link. Because it was a .deb it went straight to the 'open(with gdebi) open with other app or save' window. When I clicked to open with gdebi, I got the "/tmp/sp-auth_3.2.6_all-2.deb could not be opened, because the associated helper application does not exist. Change the association in your preferences." window pop up.
Then I did the cd Downloads file, where it was located and when I tried apt-get install and dpkg I got nothing. 

I'm going to try and download a .deb file from a different place.

---

### Post by howefield on 2009-12-20
> **spursncowboys said:**
> I'm going to try and download a .deb file from a different place.

Try adding the ppa, and install with Synaptic, and get all the updates.

There is an update version to the one you are trying to install.

I'll get the url for you.

There you go...

[https://launchpad.net/~jason-scheunemann/+archive/ppa](https://launchpad.net/~jason-scheunemann/+archive/ppa)

---

