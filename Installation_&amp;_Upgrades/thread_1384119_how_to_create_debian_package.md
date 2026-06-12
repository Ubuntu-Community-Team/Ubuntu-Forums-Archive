---
title: "how to create debian package"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by nuke_fluke on 2010-01-18
every time i start with a new installation, i have to download all the useful software once again...

i think it would be simple and easy-to-use if these software could be bundled into debian packages which can be installed just by clicking (like in windows)...

Is there any website where I can find debian packages for important software? Or can I create them myself...

Plz suggest something other than aptoncd...

---

### Post by User_Program on 2010-01-18
I use [_GetDeb_]("http://www.getdeb.net/welcome/"), quick and easy.

---

### Post by sliketymo on 2010-01-18
I use The Software Center,or apt-get.

---

### Post by Lars Noodén on 2010-01-18
You can create a package that contains no programs, just a list of dependencies.  [equivs](http://packages.debian.org/etch/equivs) is probably the tool you are looking for there.  Here is one [description of using equivs](http://www.groklaw.net/comment.php?mode=display&sid=20080705225101376&title=Not+a+support+forum...&type=article&order=&hideanonymous=0&pid=710510#c710552).

A simpler way is to make a list of the packages that you have installed and put them, one per line, in a text file.  Then next time you do a reinstallation you can use that text file to restock your machine using a short shell script.  Here is one such script, there are other, probably better, ways:

```

sudo apt-get update;

# note that **`** is a 'backtick' not an apostrophe or single quote
for package in **`**cat /home/nuke_fluke/packages-i-want.txt**`**; do
  sudo apt-get install --assume-yes $package;  
done;

```

Or the text file itself could be a shell script.
```

#/bin/sh

sudo apt-get update;
sudo apt-get install --assume-yes *package1*;
sudo apt-get install --assume-yes *package2*;
# ...
sudo apt-get install --assume-yes *packagen*;

```

---

### Post by chuina on 2010-01-18
```
sudo apt-get install aptoncd
```after install go to System>Administration>APTonCD 
write a with the softs u currently installed CD.(also if u saved the "package-name.deb" packages in any folder,add that folder here,it will resolve dependencies auto) 

next time when installing any software use the CD with: System>Administration>Synaptic Software Manager> ::
Edit>Add CD-ROM
u can use it even in other online/offline Ubuntus

---

### Post by Lars Noodén on 2010-01-18
@ chuina : Thanks!  [aptoncd](http://packages.ubuntu.com/karmic/aptoncd) was new to me but looks *very* useful.

---

