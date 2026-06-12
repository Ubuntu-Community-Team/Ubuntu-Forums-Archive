---
title: "unable to correct problems, you have broken packages"
date: 2012-07-17
forum: Installation &amp; Upgrades
---

### Post by davidwillis on 2012-07-17
I am trying to install handbrake-gtk in 12.04 with gnome3 shell 

This is what I did: 
sudo add-apt-repository ppa:stebbins/handbrake-releases
sudo apt-get update
sudo apt-get install handbrake-gtk

But I get: 

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 handbrake-gtk:i386 : Depends: libwebkitgtk-1.0-0:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


I have tried:
sudo apt-get install -f
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


sudo dpkg --configure -a
doesn't do anything

synaptic shows 38418 packages listed, 1811 installed, 0 broken, 0 to install/upgrade, 0 to remove

sudo apt-get update gives me:

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D6B6DB186A68F637

I also tried: 
echo foreign-architecture i386 | sudo tee /etc/dpkg/dpkg.cfg.d/multiarch

then updating, and installing, but it didn't do anything.

And I tried booting into safe mode and selecting fix packages (or something like that).

I am not sure what else to try.  That is all I could find when searching for it.

---

### Post by jmfal on 2012-07-17
Open the Update Manager >>settings >> authentication >> highlight the ppa for launchpad.net . >>click on import key file >> Other Software tab >> put check in front of both entries foe that ppa.

Then run
```
  sudo apt-get install -f    
```

---

### Post by davidwillis on 2012-07-17
Thanks, but I can't see the ppa for launchpad.net.

I attached a screenshot of my authentication tab.

---

### Post by davidwillis on 2012-07-17
looking in the other software tab, I see several ppa.launchpad.net entries.

---

### Post by drpjkurian on 2012-07-18
Post the output of ```
ls /etc/apt/sources.list.d
```

---

### Post by StevePai on 2012-07-18
Google it and check on discussions so you will be able to see what the other with similar problem have done before you.

---

### Post by davidwillis on 2012-07-18
> **drpjkurian said:**
> Post the output of ```
ls /etc/apt/sources.list.d
```

ls /etc/apt/sources.list.d
conky-companions-ppa-precise.list         
ravefinity-project-ppa-precise.list
conky-companions-ppa-precise.list.save    
ravefinity-project-ppa-precise.list.save
deluge-team-ppa-precise.list              
stebbins-handbrake-releases-precise.list
deluge-team-ppa-precise.list.save         
tikhonov-misc-precise.list
ferramroberto-gnome3-precise.list         
tikhonov-misc-precise.list.save
ferramroberto-gnome3-precise.list.save    
tualatrix-ppa-precise.list
gnome3-team-gnome3-precise.list           
tualatrix-ppa-precise.list.save
gnome3-team-gnome3-precise.list.save      
virtualbox.list
jonoomph-openshot-edge-precise.list       
virtualbox.list.save
jonoomph-openshot-edge-precise.list.save

---

### Post by davidwillis on 2012-07-18
> **StevePai said:**
> Google it and check on discussions so you will be able to see what the other with similar problem have done before you.

Thanks.  That was the first thing I did, but I have tried everything I could find other people used, and none of it worked mor me (see post #1 for the things I tried).

---

### Post by drmrgd on 2012-07-18
Out of curiosity, are you still getting that signing key error from the Stebbins PPA?  If so, what happens if you purge it, update (do you get an error), and then add that PPA again, and try updating?  

I tried adding that PPA and updating, and go no signing key errors just now.

---

### Post by watermark on 2012-07-18
I have the same problem on 12.04 x86_64.  No signing errors, just package errors.  Removing the source and signing key and re-adding didn't help.

"handbrake-gtk:i386 : Depends: libwebkitgtk-1.0-0:i386 but it is not going to be installed"

---

### Post by laserator on 2012-07-18
Ive had the same problem and basically all I did was install all the packages down the line that it said were necessary.

---

### Post by davidwillis on 2012-07-18
> **drmrgd said:**
> Out of curiosity, are you still getting that signing key error from the Stebbins PPA?  If so, what happens if you purge it, update (do you get an error), and then add that PPA again, and try updating?  

I tried adding that PPA and updating, and go no signing key errors just now.

I am getting the same errors as I posted on the first post.  However I don't think it is the Stebbins PPA, becuase I got that error before I tried to install the Stebbins PPA.  I am not sure which one is causing the error.

---

### Post by davidwillis on 2012-07-18
> **laserator said:**
> Ive had the same problem and basically all I did was install all the packages down the line that it said were necessary.

I tried that as well, but when I tried to install the first one, I got a list of several others that couldn't install.

However I just tried installing handbrake again to get the file to install, and I thought I would try all on the list.  But for some reason handbrake installed.  I don't think it was anything I did, I have no idea why it just worked.

I still wish I could get rid of this error though. 

> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) precise Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY D6B6DB186A68F637

---

