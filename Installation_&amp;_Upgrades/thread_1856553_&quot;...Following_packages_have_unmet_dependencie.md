---
title: "&quot;...Following packages have unmet dependencies&quot;"
date: 2011-10-08
forum: Installation &amp; Upgrades
---

### Post by Noes on 2011-10-08
I'm quite new to Ubuntu (switched from win7 about 2 weeks ago)

I'm using Ubuntu 11.04 64-bit and using the Ubuntu classic (GNOME) GUI

When running update manager I get the following error:

"Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade.

Please report this bug against the 'update-manager' package and include the following error message:
'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.' "



When I try run sudo apt-get dist-upgrade via the terminal it says:

"Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Failed
The following packages have unmet dependencies:
 libaccess-bridge-java : Depends: default-jre but it is not going to be installed or
                                  openjdk-6-jre but it is not going to be installed or
                                  sun-java6-jre but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages."


I don't have a clue what to do from there.

---

### Post by Shazaam on 2011-10-08
```
When I try run sudo apt-get dist-upgrade via the terminal it says
```

Are you trying to UPGRADE to Oneric?

---

### Post by Noes on 2011-10-12
I wasn't actually trying to upgrade. as far as I know 11.10 only releases on the 13th.
I ran the dist-upgrade just to see what would cause the problem. 
Do I have to get rid of those packages? Are they important? would not having them cause any problems? 
And If I do have to get rid of them, I don't actually know how but I'm sure I can find that with a little googling.

I'm not sure if it is relative but when running "sudo apt-get update" it updates for a while then I get the following message:
" W: GPG error: [http://ftp.de.debian.org](http://ftp.de.debian.org) lenny Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AED4B06F473041FA"

---

