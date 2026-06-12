---
title: "Upgrading from 7.10 beta to 7.10 final"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by tucano on 2007-10-23
Hi there... I installed 7.10 beta on my laptop and there were no problems..

now I'd like to update to final version... How to do that?

I heard that with simple updates it upgrades to final, but how to check if it has really happened?

Fina question: why can't I reach archive.canonical.ubuntu.com while I verify for upgrades?

Thanks for support!

---

### Post by tucano on 2007-10-23
nobody got my same problem while upgrading?

---

### Post by whistl on 2007-10-23
you should only need to run

sudo apt-get update

followed by

sudo apt-get dist-upgrade

---

### Post by tucano on 2007-10-23
I did it many times, but it says that's nothing to install...

I'doubtful about having 7.10 beta or 7.10 final because in /etc/apt/sources.list the CD image searched for packets is still 7.10 i386 BETA!

how to be sure of the version installed?

---

### Post by ssam on 2007-10-23
you can remove the cd line from the sources. it will always reference the cd you installed with (unless you changed it).

if you have the right repos, and apt says you are up to date then you will have the same packages as the final gutsy. the repos do not change from developement to release, so this is most likely true. have a look in the software sources control panel.

it is possible that a upgraded development version will not be the same as a clean install of the final version, even if the packages are the same. for example an installer bug may right a bad config file, if the installer bug is fixed, you would need to reinstall to get the benifit.

---

### Post by tucano on 2007-10-23
Perfect!

And for the problem of the repos?

1)  I'm not able to reach archive.canonical.ubuntu.com
2) The other sources addresses can be reached only if I ping them, or if I navigate them into mozilla.....

My internet line is wireless...

 I'd like to wiev the content of /etc/apt/sources.list   from someone which doesn't have this problem and has final release...

Thanks for help!):P

---

