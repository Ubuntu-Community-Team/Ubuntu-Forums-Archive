---
title: "dpkg was interrupted, not fixed using --configure -a"
date: 2007-07-21
forum: Installation &amp; Upgrades
---

### Post by skewer on 2007-07-21
Hi

An installation was interrupted by a power outage - well actually it was a laptop overheating and cutting out to prevent damage, but the result is the same :)

I have seen plenty of people recommending that an interrupted dpkg can be resolved using 
```
dpkg --configure -a
```

...BUT this isn't working here. It results in an error: 
```
dpkg: parse error, in file '/var/lib/dpkg/updates/0001' near line 1:
 field name `nded' must be followed by colon
```

I have looked in that file with gedit and it looks somehow "wrong". I don't know how it *should* look, but it says...
```
nded that
 it not be removed

Package: gnome-panel
Priority: optional
(...continues with dependencies...)
```

I get the feeling this file has been corrupted but I am reluctant to delete or manually edit it in case it will mess things up further. 

Any advice greatly welcomed, to reiterate I have tried [FONT="Courier New"]sudo dpkg --configure -a && apt-get -f install[/FONT] and it did NOT work.

Many thanks, forever in debt etc....!
SQR

---

### Post by jocko on 2007-07-21
Have you tried removing that file?
I don't have any files at all in /var/lib/dpkg/updates/ and I don't have any problem.
Just move it somewhere else:
```
sudo mv /var/lib/dpkg/updates/0001 ~/0001
```
That will move the file to your home directory.
Then try running ```
sudo dpkg --configure -a
``` and see what happens.
If it works, delete the file from your home directory, otherwise move it back to where it was.

---

### Post by skewer on 2007-07-21
Thanks for the tip, I was wondering if that directory was meant to be full of files or not :)

However, it has got so much worse!!! Now refusing to boot, failing on fsck, dropping to a root command line and saying "apt-get is not installed, install by typing apt-get install apt"

Can anyone else see the problem with that one? Reminds me of the old MS boot error "Keyboard error or no keyboard detected. Press any key to continue".

Currently re-burning the feisty desktop install CD under Windows to start over, will back up a few things via USB and sacrifice the rest!

---

