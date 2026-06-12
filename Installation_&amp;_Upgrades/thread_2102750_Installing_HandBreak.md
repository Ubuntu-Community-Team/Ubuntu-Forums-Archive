---
title: "Installing HandBreak"
date: 2013-01-08
forum: Installation &amp; Upgrades
---

### Post by bman on 2013-01-08
I am trying to install handbreak and I go to add the PPA and get this.

Cannot access PPA ([https://launchpad.net/api/1.0/~stebbins/+archive/handbreak-snapshots](https://launchpad.net/api/1.0/~stebbins/+archive/handbreak-snapshots)) to get PPA information, please check your internet connection.

I am using 

sudo add-apt-repository ppa:stebbins/handbreak-snapshots

---

### Post by bman on 2013-01-08
Sudo Apt-get update gives an error about it now as well, but clearly that's because of this not working.

E: GPG error: [http://ppa.launchpad](http://ppa.launchpad) precise Release: The following signatures were invalid: NODATA 1 NODATA 2

I get on sudo apt-get update.

And yes, I noticed my spelling mistake. That error still shows up on update, and I still can't install handbrake

**So now it's installed but because of my mistake, that error on sudo apt-get update still shows there, how do I remove that?

---

### Post by oldos2er on 2013-01-08
The handbrake-snapshots PPA doesn't exist anymore, it's now handbrake-releases ```
sudo apt-add-repository ppa:stebbins/handbrake-releases
```

---

### Post by bman on 2013-01-08
I suppose that was the cause of the main problem.

I am now asking how to remove a PPA that I added, that obviously was old/spelled wrong. It's giving errors on sudo apt-get update.

---

### Post by arpanaut on 2013-01-08
> I am now asking how to remove a PPAIn a terminal copy and paste:
```
man add-apt-repository
```gives info on removing.

---

### Post by bman on 2013-01-08
So it gives me this.

"Cannot access PPA ([https://launchpad.net/api/1.0/~stebbins/+archive/handbreak-snapshots](https://launchpad.net/api/1.0/~stebbins/+archive/handbreak-snapshots)) to get PPA information, please check your internet connection."

Same as when trying to add it, obviously it's not a real PPA.

And on sudo apt-get update I still get this.

E: GPG error: [http://ppa.launchpad](http://ppa.launchpad) precise Release: The following signatures were invalid: NODATA 1 NODATA 2


So how do I remove something that isn't a real PPA, or how do I find out what exactly is causing that error message.

---

### Post by arpanaut on 2013-01-08
go to your "Software Sources" click on the "other" tab and remove the checkmarks on the PPA in question, then add the correct PPA. refresh your repositories or close out and run update again in terminal.
see:

---

### Post by bman on 2013-01-08
Thanks that worked, should have thought of that.

---

