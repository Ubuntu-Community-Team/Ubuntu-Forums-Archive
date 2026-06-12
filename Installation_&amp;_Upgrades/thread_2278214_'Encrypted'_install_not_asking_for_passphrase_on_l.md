---
title: "'Encrypted' install not asking for passphrase on login?"
date: 2015-05-14
forum: Installation &amp; Upgrades
---

### Post by nav_infin on 2015-05-14
I just installed Lubuntu 15.04 on my desktop, and during installation, it said that I had a 'dangerous swap area' that needed to be deleted or encrypted? I'm still learning how to set up partitions, but I followed a tutorial, and successfully created new partitions, and completed the install with everything working the way it should, except for one thing; When I log in, I am not asked for an encryption pass phrase, as I have been with previous installations of Lubuntu using full disk encryption. It only asks me for my root password. I thought that it should be the other way around, as I selected to log in automatically. I thought I would have to enter my pass phrase for encryption, but not my root password. My question is: Have I installed with full disk encryption, or did it fail somehow? I did receive a randomly generated encryption key, which I believe has to do with my Home folder? I'm still confused by all this. How do I know if the disk encryption worked, if I am not asked for a pass phrase on login?

---

### Post by sudodus on 2015-05-14
I have installed Lubuntu 15.04 according to the following links - test cases for iso testing before releasing it. I works for me.

(for 32-bit systems, but the instructions are the same for 64-bit systems, except that another iso file is used)

[Alternate Install (Encryption)]("http://iso.qa.ubuntu.com/qatracker/milestones/338/builds/92394/testcases/1439/results")

[Alternate Install (Unencrypted home)]("http://iso.qa.ubuntu.com/qatracker/milestones/338/builds/92394/testcases/1660/results") (which means 'only' encrypted disk)

Maybe the best way to solve your problem is to re-install.

Please ask again (for more details) if  there are still problems :-)

---

### Post by nav_infin on 2015-05-14
Would you say if it's not asking for a pass phrase at login, that the encryption didn't work? Is that an obvious answer, idk? I have done the automatic install process many times with success; the only thing giving me trouble on this, was the message about a bad swap area, and the fact that I had to setup my partitions manually. I have a feeling I will do another install, or just give up on the whole encryption thing. Thanks for the help.

---

### Post by sudodus on 2015-05-14
'Encrypted disk' will ask for a passphrase. Inside that system there is 'normal swap' (not cryptswap).

'Encrypted home' does not ask for a passprase at login. 'Encrypted home comes with cryptswap and needs it, or no swap. 'Normal swap' is a security leak except if there is 'Encrypted disk'. 'Encrypted home' does not work in 14.04.2 LTS.

A combination of both may seem unnecessary, but would add security in certain situations, for example between users of the same system.

---

