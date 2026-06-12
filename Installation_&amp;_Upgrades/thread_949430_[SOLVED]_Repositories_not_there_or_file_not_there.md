---
title: "[SOLVED] Repositories not there or file not there"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by Dragonbite on 2008-10-16
For the past weeks (couple of months?) when I try and update my Ubuntu 8.04 on my Laptop through Synaptic I get the following errors:```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com hardy-updates Release: The following signatures were invalid: NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://us.archive.ubuntu.com hardy-security Release: The following signatures were invalid: NODATA 2

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.45 80]

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release  

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.

```

Also, I have tried to install Ubuntu Server and it hangs on the updating from repositories stage which leads me to suspect (but I don't know how to check for sure) that it too is receiving this error.

For the URLs I get :
[http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2]("http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/")
The folder is there, but **Translation-en_US.bz2** is not listed. Translation-en_GB.bz2 is the only other English version.

[http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/i18n/Translation-en_US.bz2]("http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted")
I get a 404 error.  [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/]("http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/") is there but the **i18n** directory is not listed.

same with.. 
[http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse/i18n/Translation-en_US.bz2]("http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/multiverse")

and
[http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/restricted/i18n/Translation-en_US.bz2]("http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/restricted")

I get to these URLs alright
[http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release]("http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release")
[http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/Release]("http://us.archive.ubuntu.com/ubuntu/dists/hardy-security/Release")

I know I can remove these repositories and such, but I want to make sure my system is up-to-date and getting all of the security patches. Plus there is the unknown Ubuntu Server issue going on in the same area.

---

### Post by Dragonbite on 2008-10-16
Quick Update:

I just tried it with an unmodified Ubuntu LiveCd on my work computer (wireless works out-of-the-box! woo hoo!) and it too comes out with these errors!

If there are any possible ways to see if it is my local network settings, please let me know.  I hope to be able to try it out at work sometime (via LiveCD) to find out if it is the network, but another installed Ubuntu in the [DACS]("http://www.dacs.org") resource center updated without any errors.

Any help is appreciated!

---

### Post by Dragonbite on 2008-10-17
Another Update:
I am running this from a LiveCD session here at work and it did not return any errors.

I also realize that this does not include any 3rd party repositories while at home I  think there are 2.

So I am suspecting
[LIST=1]
[*]My network or firewall or something is blocking the necessary sites/ports
[*]My 3rd party repositories included repositories that are either moved or no longer relevant.
[/LIST]

I am hoping that it is the 2nd one, as that would be easier to fix (after I check and see what all I installed that put it there).  I'll give it a try tonight and see what happens.

---

### Post by Dragonbite on 2008-10-19
Alright, I think I have it fixed.

Because the errors occured whether I was using a LiveCD or an installed version tells me that it isn't a setting issue with my laptop.

Because the error did NOT occur from work tells me that it is in my home network (could be the router, the firewall, or something else)

My network goes from the modem into a CPU running IPCop and content filtering. After that it goes to my Linksys wireless hub and then to the computer.

Before I started re-connecting the wires to bypass the router, or the plug directly into the modem I decided to add archive.ubuntu.com, archive.canoncial.com and security.ubuntu.com to the DansGuardian exceptions list. This allows these domains and everything on the domain to be allowed.

That did it.  

So the reason for the errors was my content filter was blocking receiving anything from those sites and the Translation_en_US is something that is still missing but doesn't raise any errors.

If this didn't work I was going to start with directly connecting the system to the modem and then add the IPCop filter or the router to determine the source.

---

### Post by miki90 on 2008-11-28
Bless you Dragon Bite. That solved a problem I had behind dansguardian as well. Had been bothering me for some time. Nicely done.

---

