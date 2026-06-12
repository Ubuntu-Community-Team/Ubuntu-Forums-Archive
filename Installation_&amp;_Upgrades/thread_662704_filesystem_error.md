---
title: "filesystem error?"
date: 2008-01-09
forum: Installation &amp; Upgrades
---

### Post by Embiggens on 2008-01-09
I've installed Gutsy pretty recently and I am trying to install the movie player codecs.  So I'm installing the ubuntu-restricted-extras package.  In the unpacking process, I run into the following problem.

```
Get:13 http://us.archive.ubuntu.com gutsy/main libaudio2 1.9-2 [77.5kB]         
Fetched 2798kB in 6s (407kB/s)                                                  
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... dpkg: error processing /var/cache/apt/archives/java-common_0.26ubuntu1_all.deb (--unpack):
 unable to open files list file for package `bsh': Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/java-common_0.26ubuntu1_all.deb
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
```

which I think is kinda bad (particularlyl the "Input/output" line)? I'd be slightly surprised if my filesystem was corrupt, since I've only recently installed and all I've really done is gotten my wireless card working (granted, I installed and uninstalled ndiswrapper about 5 times in the process). Maybe I shouldn't be surprised?

Anyway, does anyone have any thoughts on what my problem is here and how I might fix it without reinstalling, which is the only solution I've seen for an "Input/output" error?  Thanks.

---

### Post by Embiggens on 2008-01-11
Well, I don't really know what I'm doing, so I tried a few simple things like reinstalling the package 'bsh' and even manually deleting then reinstalling the package.  Unsuccessful as expected, so I reformatted and reinstalled.

---

