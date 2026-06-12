---
title: "untrusted packages?"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by madeinwales on 2011-03-06
when trying to install a download manager (i have a very slow and unreliable bb connection)such as KGET, TUCAN or FILEZILLA from the software centre (mav 10.10)i get...

"Requires installation of untrusted packages 
The action would require the installation of packages from not authenticated sources."

And then i am not able to download, what can I do to solve it ?
cheers again
nev

---

### Post by Frogs Hair on 2011-03-06
Run these in the terminal and try again.```
sudo apt-get update
``````
sudo apt-get upgrade 
```

---

### Post by madeinwales on 2011-03-06
> **Frogs Hair said:**
> Run these in the terminal and try again.```
sudo apt-get update
``````
sudo apt-get upgrade 
```

when i run sudo apt-get update i get

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

sudo apt-get upgrade
does something..

closed and reopened software centre but still the same. 
do i need to reboot?
cheers
edit - rebooted, still the same problem:(

---

### Post by Frogs Hair on 2011-03-06
No need to reboot . The invalid key should be in your software sources . Try System> Administration > Synaptic Package Manager >  Settings > Repositories > Authentication  and find out what the key is for. There may be a way to validate it.

---

### Post by madeinwales on 2011-03-06
> **Frogs Hair said:**
> No need to reboot . The invalid key should be in your software sources . Try System> Administration > Synaptic Package Manager >  Settings > Repositories > Authentication  and find out what the key is for. There may be a way to validate it.

correct, it was the first one on the list.
copied/ pasted into google and found old thread with following solution...

 June 3rd, 2010	   #9
jaygo
Gee! These Aren't Roasted!

 
Join Date: Aug 2007
Location: US
Beans: 156
Ubuntu 9.10 Karmic Koala
Re: Signature Verification Failure
Looks like this old fix still does the trick. You'll need to preface all of these with "sudo" or "sudo su" beforehand.
Code:
apt-get clean
cd /var/lib/apt
mv lists lists.old
mkdir -p lists/partial
apt-get clean
apt-get update

and i can now download for repository.
so thanks frogs hair
and thanks jaygo

---

