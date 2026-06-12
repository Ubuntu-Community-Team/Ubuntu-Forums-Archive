---
title: "Ubuntu Install Version Lockdown"
date: 2011-09-22
forum: Installation &amp; Upgrades
---

### Post by jsarma on 2011-09-22
Hi everyone. I have a question about automating Ubuntu builds which I'd really appreciate the advice of a guru on. I can't seem to find any specific references to it on the web.

I'm trying to create a validated web server using Ubuntu 10.04 LTS. I want to be able to run a build script which looks something like this whenever I need to install the system on a new server:

apt-get -y update
apt-get -y install package1
apt-get -y install package2
etc...

The problem is this script will pick up new updates to packages, which could require re-validation. So I need to lock this script to specific versions of each package. 

One method I've tried is adding =<version> to each package to make sure it installs the correct version. The problem is this method doesn't always create the same softlinks that would be create otherwise. For instance, apt-get -y install ruby is not the same as apt-get -y install ruby1.8=<version>, because the former creates a softlink from ruby to ruby1.8. So this method isn't great.

I'm wondering, is there some command like:

apt-get -y update=<ubuntu version>

which will tie all my future apt-get install commands to specific versions that can't be changed by subsequent package updates on future installs? If so, that would be super-awesome, because I wouldn't have to worry about specifying every version of every package I install. Instead, I could just validate a specific version of ubuntu's package. 

If not, is there some other approach  that is recommended for achieving version lockdown?

I'd really appreciate any suggestions.

Thanks

---

### Post by garvinrick4 on 2011-09-22
aptitude hold pkgname: Fix a package at its current version  and don't upgrade it automatically (formerly an obscure echo-to-file  command).  unhold to remove the hold.

Is this what you are looking for.
install aptitude:
sudo apt-get install aptitude

---

### Post by jsarma on 2011-09-22
Thank you very much for the quick reply, Garvin. This is definitely helpful, but I don't think it's exactly what I'm looking for. If I understand correctly, if I do aptitude hold <pkgname>, then later when I do a aptitude update later, it will not try to update <pkgname>, right? But what if I try to install on another system a year later, and pkgname has a more recent version. It seems I would need to tell it the specific version number I want to install during each install, or I'll end up with a different system the second time around.

What I'm looking for is global versioning of the source list repository that gets updated when you run apt-get update, or aptitude update. For instance, if I could type apt-get update=<ubuntu v10.04.12345>, and install a whole bunch of packages without specifying a version for each. Then come back two years later, and type the same commands, and have an identical installation, with no versions updated, that would be ideal.

In order for this to work, ubuntu v10.04.12345, would have to be linked to a source repository that knows the version of each package that can be installed, and will not allow those versions to change without incrementing the 12345 part. 

Maybe I'm asking for something that just doesn't exist. I will give aptitude and hold pkgname a try though. So thanks for the tip.

---

