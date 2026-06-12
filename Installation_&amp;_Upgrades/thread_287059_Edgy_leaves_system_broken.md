---
title: "Edgy leaves system broken"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by kitten on 2006-10-28
i was doing my Dapper updates, and a button showed up saying distribution upgrade or something, so i clicked it.

... 6 hours later ...

istall, install, install .... CRASH

complained about the /usr/X11R6/bin can't be overwritten, says fix it first with apt-get or synaptic

synaptic asks for it to be fixed first, i don't know how to do that

read, read, read, try sudo apt-get -f install

get the error again

become superuser, set 777 permissions on bin

same result

now i can't add or remove software ... still works more or less, just has broken packages

relevant log message follows:

```
33 upgraded, 17 newly installed, 9 to remove and 1056 not upgraded.
36 not fully installed or removed.
Need to get 0B/112MB of archives.
After unpacking 75.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 145174 files and directories currently installed.)
Preparing to replace x11-common 7.0.0-0ubuntu45 (using .../x11-common_1%3a7.1.1ubuntu6_i386.deb) ...
Unpacking replacement x11-common ...
Replacing files in old package xinit ...
dpkg: error processing /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb (--unpack):
trying to overwrite `/usr/X11R6/bin', which is also in package opera
Errors were encountered while processing:
/var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu6_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@canetoad:/usr/X11R6#
```

---

### Post by meng on 2006-10-28
May be time for a fresh install - have you got your data/settings on a separate partition?

---

### Post by kitten on 2006-10-28
no, i thought this linux stuff was meant to be easy and bulletproof

i just did what the machine told me to do

---

### Post by meng on 2006-10-28
Upgrading across versions is always tricky, and I would never describe it as bulletproof. But let's not waste time apportioning blame. You should be able to copy your /home data onto a separate partition. (See here for details: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome))

Then you can do a clean install of Edgy by downloading and burning the install CD and overwriting the main / partition (and keeping the data on /home intact, but designating that partition's mountpoint to be /home).

If you have backed up your data recently (which you definitely should have, especially if you were upgrading to a new version of Ubuntu) then you may not need to do this, although a separate /home partition is very advisable anyway.

Granted, this is not extremely simple, but it's not dreadfully complex either.

---

### Post by kitten on 2006-10-28
ok.  when i've had some sleep, so i don't make a mistake

i think i maybe should back up /etc as well

not sure about /var/www it's got my crude website webspinning.org

---

### Post by meng on 2006-10-28
Good thinking (on all three counts).

---

