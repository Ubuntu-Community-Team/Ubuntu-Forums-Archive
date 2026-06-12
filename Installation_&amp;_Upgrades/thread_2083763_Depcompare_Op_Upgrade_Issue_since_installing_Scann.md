---
title: "Depcompare Op Upgrade Issue since installing Scanner"
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by Andavane on 2012-11-13
I've got a

Canon LIDE 110

scanner working well on Ubuntu 12.04 64-bit. It was a bit tricky getting it to work and I tried sevral things. Unfortunately I lost track of what I did, although there must be a record.

Trouble is, when I went to update latetr via terminal I persistently get:

> W: Ignoring Provides line with DepCompareOp for package iscan-interpreter
W: You may want to run apt-get update to correct these problems

Naturally I want to get this sorted, but fear that I may not have my scanner working any more if I do.

I have googled it a lot but as I don't understand what it's about.

Advice as usual much appreciated, and hoping this went into the right board.

Regards

John

---

### Post by bastubis on 2012-11-19
Same problem here, Ubuntu 12.04 64-bit and Epson Perfection V37 scanner with these drivers installed:

iscan-data_1.19.0-1_all.deb
iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb
esci-interpreter-gt-f720_0.0.0-1_amd64.deb
iscan-plugin-perfection-v370_1.0.0-2_amd64.deb

Took quite a lot of fiddling to get it going, the scanner is now working fine but I have this error when I update apt:

W: Ignoring Provides line with DepCompareOp for package iscan-interpreter
W: You may want to run apt-get update to correct these problems

Think my problem is to do with this: [https://bugs.launchpad.net/ubuntu/+bug/208405](https://bugs.launchpad.net/ubuntu/+bug/208405) - an issue with the packaging of the deb that still hasn't been solved. I still haven't figured out how to get rid of the error message though, short of purging and compiling the drivers from scratch - and I'm too fed up with the saga of getting it working to start again from scratch and compile the binaries - so will tolerate the error which seems harmless, if annoying. Well, I hope it's harmless . . .

---

### Post by Andavane on 2012-11-21
> **bastubis said:**
> Same problem here, Ubuntu 12.04 64-bit and Epson Perfection V37 scanner with these drivers installed:

iscan-data_1.19.0-1_all.deb
iscan_2.29.1-5~usb0.1.ltdl7_amd64.deb
esci-interpreter-gt-f720_0.0.0-1_amd64.deb
iscan-plugin-perfection-v370_1.0.0-2_amd64.deb

Took quite a lot of fiddling to get it going, the scanner is now working fine but I have this error when I update apt:

W: Ignoring Provides line with DepCompareOp for package iscan-interpreter
W: You may want to run apt-get update to correct these problems

Think my problem is to do with this: [https://bugs.launchpad.net/ubuntu/+bug/208405](https://bugs.launchpad.net/ubuntu/+bug/208405) - an issue with the packaging of the deb that still hasn't been solved. I still haven't figured out how to get rid of the error message though, short of purging and compiling the drivers from scratch - and I'm too fed up with the saga of getting it working to start again from scratch and compile the binaries - so will tolerate the error which seems harmless, if annoying. Well, I hope it's harmless . . .

Well good to meet someone in the same boat: Perhaps by hollering and waving we can get some help :) Well I feel like you that it's not that serious, probably a bug.

I tried this:, after typing 
"sudo apt-get update && sudo apt-get dist-upgrade"
I now get ;
> Fetched 2,625 kB in 10s (258 kB/s)                                             
W: Failed to fetch [http://ppa.launchpad.net/plaxx/random-fixes/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/plaxx/random-fixes/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/plaxx/random-fixes/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/plaxx/random-fixes/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/plaxx/random-fixes/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/plaxx/random-fixes/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.
andavane@Cedilla:~$ 

which is now a bit diffferent as the i-scanner thing has gone.
Even if not solved, perhaps someone will help by telling a bit more about this kind of issue. To repeat: I wonder and hope it went into the right forum.
Let's see... john

---

