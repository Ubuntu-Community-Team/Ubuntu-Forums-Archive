---
title: "Slow update process 12.04"
date: 2017-04-06
forum: Installation &amp; Upgrades
---

### Post by Otto-C on 2017-04-06
Had not used my laptop with Ubuntu 12.04 for about 19 days.
To begin I went to Update Manager and check for updates.
My download speed is about 3.84Mbps. As the check was in progress it
appeared to be slow. It took just over 5 minutes to complete the process.
Now I got called away just after I started the install so length of time
that it took is unknown.
Now I went to command line and did:
```

sudo apt-get update
Hit http://ppa.launchpad.net precise Release.gpg
Hit http://ppa.launchpad.net precise Release                                  
Hit http://ppa.launchpad.net precise/main Sources                             
Hit http://ppa.launchpad.net precise/main i386 Packages                       
Hit http://ppa.launchpad.net precise/main TranslationIndex                    
Hit http://ppa.launchpad.net precise/main Translation-en                      
100% [Connecting to us.archive.ubuntu.com (2001:67c:1562::19)] [Connecting to s

```
What is going on. I have found something similar on Linux Mint.
What to do?

tia
otto-c

---

### Post by TheFu on 2017-04-06
Ubuntu 12.04 support ends in a few weeks (4/28 according to the Ubuntu release website). It is passed time to move to a newer LTS release.  BTW, you are not alone on this. I have 1 box to move ASAP.  Guess I've put it off as long as possible too. ;)

As for slowness, check for normal slow network issues - slow DNS, slow ISP, or a VPN left running that you forgot about with an exit in some Asian country, perhaps?

Does speedtest show a slowdown?

Are any other sites being impacted? Is it just ubuntu repos?  BTW, it appears you are using IPv6 - I've disabled that across all my systems. There have been reports of IPv6 causing issues.

I have a server in the USA running 12.04. Ran an update ... 
```
$ time sudo apt-get  update
....
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Fetched 5,686 kB in 25s (225 kB/s)                                             
Reading package lists... Done

real    0m30.852s
user    0m8.517s
sys     0m12.869s

$ date
Thu Apr  6 16:37:41 EDT 2017
```
So whatever it is, it isn't system-wide. It is just you. ;(  Provided a timestamp so you'd know when I did it.

---

