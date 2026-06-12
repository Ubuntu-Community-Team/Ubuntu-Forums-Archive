---
title: "Upgrading to 7.10 from 7.04"
date: 2007-10-07
forum: Installation &amp; Upgrades
---

### Post by malel on 2007-10-07
when I tried to run $ gksu "update-manager -c" it tells me "warning: could not initiate dbus
current dist not found in meta-release file".
Have I done something wrong to get this reply.
Is this the correct method to upgrade from Ubuntu 7.04 to Ubuntu 7.10 ?

---

### Post by smartboyathome on 2007-10-07
You need to run update-manager -d

---

### Post by malel on 2007-10-07
Thank you I will give that a try . I see in some post's it say's  update-manager -c and some say -d .    Rgds

---

### Post by malel on 2007-10-07
Hello again.
Tried upgrading using  -d but it comes back with .....gksu "update-manager -d"
warning: could not initiate dbus
current dist not found in meta-release file

Is there something funny going on here ?

---

### Post by mindtrick on 2007-10-07
[http://ubuntuforums.org/showthread.php?p=3425955](http://ubuntuforums.org/showthread.php?p=3425955)

---

### Post by malel on 2007-10-07
Tried that thread but it came back this time with 

sudo update-manager -c -d
warning: could not initiate dbus


Well at least it has got one thing done but what about the 'dbus' thingy .

Thanks your help !

---

### Post by jmusso on 2007-10-07
Hi,

trying to update from Feisty to Gutsy, and I'm getting and error message that reads

Could not install "ubuntu-desktop"

followed by another message that says it can't 'calculate the update' or something, then update manager restores my old version and closes itself. Any ideas? Should I boot into normal Gnome or something, i'm currently in XGL using Beryl. I installed all the updates, including the Beryl ones from the repos that I'm "not supposed to install" hoping those would let the update to Gutsy go well, but no luck. Any help would be great! Thanks!

- Joe

---

### Post by mindtrick on 2007-10-08
> **malel said:**
> Tried that thread but it came back this time with 

sudo update-manager -c -d
warning: could not initiate dbus


Well at least it has got one thing done but what about the 'dbus' thingy .

Thanks your help !
Check this out 
[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

### Post by mindtrick on 2007-10-08
> **jmusso said:**
> Hi,

trying to update from Feisty to Gutsy, and I'm getting and error message that reads

Could not install "ubuntu-desktop"

followed by another message that says it can't 'calculate the update' or something, then update manager restores my old version and closes itself. Any ideas? Should I boot into normal Gnome or something, i'm currently in XGL using Beryl. I installed all the updates, including the Beryl ones from the repos that I'm "not supposed to install" hoping those would let the update to Gutsy go well, but no luck. Any help would be great! Thanks!

- Joe
Do you have the ubuntu-desktop metapackage installed? 
It's highly recommended to have one of the desktop packages installed (ubuntu-desktop, kubuntu-desktop or xubuntu-desktop) for a successful upgrade. Otherwise you can check the [help page]("https://help.ubuntu.com/community/GutsyUpgrades") as well.

---

### Post by malel on 2007-10-08
Thank you "mindtrick" I have tried out that but this is what I get....

 gksudo "update-manager -c -d"
warning: could not initiate dbus
extracting '/tmp/tmpjqZuw2/gutsy.tar.gz'
authenticate '/tmp/tmpjqZuw2/gutsy.tar.gz' against '/tmp/tmpjqZuw2/gutsy.tar.gz.gpg' 
could not send the dbus Inhibit signal: global name 'dbus' is not defined


although it starts to install I get an error msg as follows:

Failed to fetch [http://nz.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.bz2](http://nz.archive.ubuntu.com/ubuntu/dists/gutsy/universe/source/Sources.bz2) MD5Sum mismatch


So maybe I will just have to wait untill the 18/10/07 as nothing is working at this time

---

### Post by nraney on 2007-10-10
I hope that is the trouble. mine does the same thing except it hangs up on wine.

Post again if you got it to work without having to wait.. im impatient.

---

