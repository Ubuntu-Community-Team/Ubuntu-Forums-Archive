---
title: "I Just Can't Get this ntfsfix thing compiled"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by CadMasterAdam on 2007-04-09
okay so i got the CVS from linux-ntfs

i've done the ./configure in the directory
now i understand that i need to do:

make
sudo make install

before i can "run ntfsfix ..."

but when i type make, it says "command not found"

help?

---

### Post by ajgreeny on 2007-04-09
Perhaps you need *build-essential* package installed.  Try:-
sudo apt-get install build-essential

---

### Post by CadMasterAdam on 2007-04-09
genious.

well that makes it easy.. okay thanks.

now can someone answer me this question?

why isn't this kinda thing preloaded with ubuntu and other distros. i also had to get gcc and something else i can't remember..?

it should would make it easier for noobs like me

---

### Post by ajgreeny on 2007-04-09
I think it's not included in the default iso because of the space limitation on the one CD (think about fedora with its 5 CDs) and the likelyhood of few people wanting to compile programs in ubuntu.  There is plenty of advice around for those who do want to do it for themselves which you will find if you do a search.

---

### Post by CadMasterAdam on 2007-04-09
10-4 thanks for the info. i'll have to keep things liek this in mind.

---

