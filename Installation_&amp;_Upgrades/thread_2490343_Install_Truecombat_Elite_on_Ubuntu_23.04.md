---
title: "Install Truecombat Elite on Ubuntu 23.04"
date: 2023-08-30
forum: Installation &amp; Upgrades
---

### Post by nador2 on 2023-08-30
Hi, I was searching on internet but I found just only manuals from year 2010 and older. It looks not safe to use the same steps for me - so much things changed from these years.

So my simple question - How to install Truecombat Elite (and Wolfenstein: Enemy Territory) with Punkbuster in these days on current versions of Ubuntu (and for me Kubuntu)?[FONT=monospace]

Thank you for your advices how to install it as easy as possible (I am not too much programming-skilled :smile:)... ). For example - is there some Snap version or some repository or something to make it more easy?[/FONT]

I found sympatic project for easy instalation: [https://github.com/fabiang/true-combat](https://github.com/fabiang/true-combat)

But in step "run ./install" I got error:

[FONT=monospace][COLOR=#000000] ```
./install
```[/COLOR]```

Installing files to /home/lenovo 
panic: Get http://etkey.org/distpb.php: dial tcp 62.75.254.167:80: i/o timeout 

goroutine 16 [running]: 
runtime.panic(0x6379a0, 0xc208024cc0) 
        /usr/lib/go/src/pkg/runtime/panic.c:279 +0xf5 
main.check(0x7fa92f78b8b8, 0xc208024cc0) 
        /vagrant/install.go:88 +0x4f 
main.main() 
        /vagrant/install.go:130 +0x735 

goroutine 19 [finalizer wait]: 
runtime.park(0x414560, 0x7f6500, 0x7f4769) 
        /usr/lib/go/src/pkg/runtime/proc.c:1369 +0x89 
runtime.parkunlock(0x7f6500, 0x7f4769) 
        /usr/lib/go/src/pkg/runtime/proc.c:1385 +0x3b 
runfinq() 
        /usr/lib/go/src/pkg/runtime/mgc0.c:2644 +0xcf 
runtime.goexit() 
        /usr/lib/go/src/pkg/runtime/proc.c:1445 

goroutine 17 [syscall]: 
runtime.goexit() 
        /usr/lib/go/src/pkg/runtime/proc.c:1445

```
[/FONT]

---

### Post by TheFu on 2023-08-30
Running a non-LTS release for someone new to Linux is a terrible idea.  The most recent LTS is 22.04.  You'll want to learn which releases are LTS and which are not, since support for non-LTS is about 6 months of real use before they are dropped.  Also, non-LTS releases are where new ideas are tried. This can be fantastic, but often it is way, way, way, too early for some of the included projects.

As for Truecombat Elite ... I don't know anything special, but I can do a websearch.  There's only 1 result.

> Can I play MWTC on Mac and/or Linux?
The official platforms for CoD4 include Windows/Mac OS X. However, due to lack of resources and the early phase of the alpha, we have only been able to test on Windows.

This is where Mac users come in - we will need your help during this alpha test to see if you will be able to run the alpha properly. Please post your findings on the MWTC Forum.

Linux users, Google searches show that it is possible to run CoD4, so like the Mac testers, please report if you are able to play the alpha properly as well.

They only test on MS-Windows, so it is expected that Linux users will need to bring some OS skills to get it working, if that is even possible.
It does appear there are instructions for running a Linux Server here: [http://www.truecombatelite.com/forums/viewtopic.php?f=51&t=2443&p=30291#p30291](http://www.truecombatelite.com/forums/viewtopic.php?f=51&t=2443&p=30291#p30291) Those instructions are from 2013, but I don't see anything that wouldn't work in any later Linux release ... assuming the libraries and binaries work.  There have been many libc changes in the last 10 yrs, but libc is fairly stable and the devs try to maintain forward compatibility unless they have to break calling order for functions.  Very few, if any old functions would have that. As for other dependent libraries, the entire graphics subsystem in Linux has been replaced a few times in the last 10 yrs.

> Is TC:E Open Source? How about moving to the Q3 GPL engine or its forks? Can I contribute?
TCE is closed source. The engine subject has been discussed already, and the developement team has stated several times that they intend to continue in the W:ET engine as a closed source project. TCE is not currently in a state of active development, so we are not looking for contributors :( 

And list last FAQ really clarifies things. The spelling mistakes are theirs, not mine.

I suspect the only way for someone new to get TC working is by having them step you through every entry, as you do it.  Anyone who hasn't done it wouldn't be in a position to attempt this.

---

