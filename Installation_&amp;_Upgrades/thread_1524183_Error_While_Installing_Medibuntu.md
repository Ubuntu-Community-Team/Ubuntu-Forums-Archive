---
title: "Error While Installing Medibuntu?"
date: 2010-07-04
forum: Installation &amp; Upgrades
---

### Post by Cason on 2010-07-04
OK, so I'm following the instructions in the Medibuntu wiki. When I run the command in the terminal to add it to the repository, it runs for a couple of minutes then gives this error:
```
W: GPG error: http://ppa.launchpad.net lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY BE1B248616AE4E77
```
What does that mean, and how can I fix it?

Obviously I'm still a noob at this stuff. Any help would be much appreciated. :)

---

### Post by oldos2er on 2010-07-04
Apt is looking for Medibuntu's gpg authentication key. Try ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys BE1B248616AE4E77
```

---

### Post by mprice on 2010-07-05
Which ppa repository are you using??

---

### Post by Cason on 2010-07-05
@oldos2er: Thanks, that did the trick!

@mprice: I don't know exactly, was just using the terminal commands found in the wiki [here]("https://help.ubuntu.com/community/Medibuntu"). I got the error when I ran this command:
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```
However, like I said, oldos2er's solution did the trick and it was able to complete the next time I ran it. Thanks to you both! :D

---

