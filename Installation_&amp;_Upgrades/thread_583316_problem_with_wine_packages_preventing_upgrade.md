---
title: "problem with wine packages preventing upgrade"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by redheffer on 2007-10-20
I tried running the update manager to upgrade to gutsy.  I get an error during update message:

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'

I removed wine some time ago completely.  Anyone have any ideas?  Thanks in advance!

---

### Post by haydnsimon on 2007-10-20
I am having exactly the same problem.

---

### Post by lasers22 on 2007-10-20
i thought at first it was my o/s but i am having the same problem
so it could be a bug on the website,or a file that needs to be updated.

---

### Post by haydnsimon on 2007-10-20
There is an answer to this problem in an earlier thread (you can find it by searching for wine and gutsy). Basically you have to remove the wine repository from the third party repositories that Ubuntu searches for upgrades. Use the Synaptic package manager to do this.

---

### Post by Strfie89 on 2007-10-20
Can you post specific instructions?

---

### Post by haydnsimon on 2007-10-20
I would like to but unfortunately I cannot open the Synaptic package manager at the moment to check the details as I am in the middle of the Gutsy update process !!

As I remember go to system -> administration -> synaptic package manager. Now the bit I don't remember is how to find the repositories but it must have been trivial otherwise I would have remembered. In any case what you want is to open the tabbed dialog box that lists all the repositories that Ubuntu searches for. Select the third party tab and look for the line that says Wine. Now delete that and press confirm. Close the Synaptic package manager before you repeat the update procedure.

Good luck.

Shimon

---

### Post by Strfie89 on 2007-10-20
In a way, I have already done that, but I still get this message after trying to upgrade:

Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl'


Can these be obained and resolved manually from somewhere else? Can you perhaps give an alternate method of checking/ deleting Wine?

(Note: I used [Automatix]("http://www.getautomatix.com") to download Wine. I also used it to get *VirtualBox*.)

---

