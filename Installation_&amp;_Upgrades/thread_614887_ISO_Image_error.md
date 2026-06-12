---
title: "ISO Image error"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by greatgoo on 2007-11-16
Attempting to burn a CDRom from the 7.10 ISO image I get this error ..

Foreign Image File

The entered block size does not correspond to the image length
The block size may be wrong.  Do you want to correct the 
problem or ignore it.


This came up using Nero in Windows XP.  Ignoring the problem makes a CD that will boot but cycles back to the boot, continuous boot.  

I assumed I had a bad download and downloaded the image again, twice now, on two different machines from two different respositories.  The only common feature is both repositories are in the US.  I guess I could try one from another country.

David Davis
Toledo, OR US

---

### Post by Herman on 2007-11-16
A good way to check if the .iso file you have downloaded is either good or if it's corrupted is to run an md5sum integrity check.

Don't bother wasting your time burning it to a CD unless the md5sum from testing the .iso file matches the md5sum found at the site you downloaded the file from.

If you have Linux installed already it's very very simple to run an md5sum test on any file, just open a terminal and run the command 'md5sum ubuntu (and press your TAB to auto-complete the rest of the file name and then press 'enter', and wait a few minutes.
For example, here's what an md5sum check looks like in my computer when it's finished, 
```
herman@amdxz:~$ md5sum ubuntu-7.10-desktop-amd64.iso 
61c87943a92bc7bf519da4e2555d6e86  ubuntu-7.10-desktop-amd64.iso

```Otherwise, if you have any kind of Linux LiveCD, you will still be able to run an MD5sum check if you know how to mount your partition that has the file it it first.  I can explain to you exactly how to do that if you want, just let me know. :)

I presume you only have Windows at the moment though. :(

Well, if so, you're still in luck if you can install '[MD5summer]("http://www.md5summer.org/")' because I have a how-to on using that, here:[ Checking the integrity of your .iso in Windows]("http://www.users.bigpond.net.au/hermanzone/p17.htm#Checking_the_integrity_of_your_.iso_in_Windows"). :)

If it passes the md5sum test and Nero still won't burn it then something is wrong with Nero and you'll have to check what settings you're using in Nero or try some other CD burning program maybe.

Regards, Herman :)

---

