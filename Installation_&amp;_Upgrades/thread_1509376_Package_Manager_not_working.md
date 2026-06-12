---
title: "Package Manager not working"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by Vebea on 2010-06-14
Since yesterday I have this problem...I can't open Package Manager and install or remove anything...this is what it says:

"The error message was:'Error:Opening the cache(E:Encountered a section with no Package:header,E:Problem with MergeList/var/lib/apt/lists/repository.akirad.net_dists_akirad-karmic_main_binary-i386_Packages,E:The package lists or status file could not be parsed or opened)'This usually means that your installed packages have unmet depencies.

OK...and now?What should I do? PLease help me.

---

### Post by ankspo71 on 2010-06-15
Hi,
Hmm, I'm not sure, but try opening up konsole (terminal) and paste the following:
```
apt-get -f
```
```
sudo apt-get -f
```
That should help correct any problems with dependencies. Try it with and without **sudo** before the command. 

Then you could paste these commands:
```
sudo apt-get update
sudo apt-get upgrade
```
to reload the repository cache, then download and install any updates.

Your package manager should be working again. but if not, report back with any errors to those commands above.
hope that helps.

---

### Post by Vebea on 2010-06-15
still not working..here is what it says

'E:Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/repository.akirad.net_dists_akirad-karmic_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

---

### Post by dino99 on 2010-06-15
why are you using this outdated thing, i mean akirad ?

all you need is to use genuine ubuntu repo, no need to add crap

---

### Post by Vebea on 2010-06-15
thanks...you were right...now it works...

---

### Post by Chame_Wizard on 2010-06-15
```
sud su 
```

```
aptitude update or safe-upgade
```

---

### Post by Vebea on 2011-08-31
it worked..but lately I get this error: *"Error: Opening the cache(E:Type'<!DOCTYPE'  is not known on line 2 in source list  /etc/apt/sources.list.d/medibuntu.list,E:The list of sources could not  be read)*
I used the terminal...but it says that[I] E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
[/I]now what?

---

