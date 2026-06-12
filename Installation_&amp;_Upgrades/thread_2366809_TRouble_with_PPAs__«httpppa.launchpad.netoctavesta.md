---
title: "TRouble with PPAs:  «http://ppa.launchpad.net/octave/stable/ubuntu zesty Release»"
date: 2017-07-22
forum: Installation &amp; Upgrades
---

### Post by nat43 on 2017-07-22
Hello @ll,
I have moved to Ubuntu Zesty 17.04. I have encountered many issues that are discussed in other posts, but I tried what they suggest without any success, and these messages appear after:

sudo  apt  update 
 
1.) E: Repository «[http://ppa.launchpad.net/octave/stable/ubuntu](http://ppa.launchpad.net/octave/stable/ubuntu) zesty Release» ERROR 404

2.) Other problem i have is with  libgdal1-dev installation

I do not have such experiences before, and not sure if changing stuff at the source.list or include repositories.

I appreciate your guidance.

Best regards,
Nat

---

### Post by QIII on 2017-07-22
Hello!

Would you please issue the command

```
sudo apt update
```

again and post the *entirety of the results* here?

Please post the results between code tags.

1. If you are using the "Reply to Thread" button - highlight text and use the # button in the text box header.  Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

The first error appears to indicate that the PPA does not exist for Zesty.

---

