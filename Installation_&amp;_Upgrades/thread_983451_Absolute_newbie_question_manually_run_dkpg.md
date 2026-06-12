---
title: "Absolute newbie question: manually run dkpg ?"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by Brat Child on 2008-11-15
I tried to install google earth using the instructions from [http://ubuntu-tutorials.com/2008/06/24/install-google-earth-on-ubuntu-804/]("http://ubuntu-tutorials.com/2008/06/24/install-google-earth-on-ubuntu-804/")  Things went well until the user acceptance screen appeared. Then the install stopped working, and did not complete. Tried to rerun it, and got this message:

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 


I have no idea how to do that. This same error also appears when trying to install any updates.  

This is a new install of Hardy Heron (8.04), so there hasn't been much time to mess things up yet .

How do I either run that dpkg, or prevent the error, or both?

---

### Post by oldos2er on 2008-11-15
In a terminal, run "sudo dpkg --configure -a".

---

### Post by cdtech on 2008-11-15
I was going to say the same with an addition:
```
sudo dpkg --configure -a && sudo apt-get -f install
```

---

### Post by Brat Child on 2008-11-15
Thank you oldos2er and cdtech:)

I tried running the longer command first, and the google earth gave a "serious error" that couldn't be read before the screen went by. Something about missing file list. So that explains why that wouldn't install correctly. 

The install updates still gave the same instruction to manually run the dkpg. So I tried the shorter command. It tried to install google earth (again), gave the same error, and then the updates started working \0/

So it appears things are happy once more :guitar:

Thank you, both!

---

