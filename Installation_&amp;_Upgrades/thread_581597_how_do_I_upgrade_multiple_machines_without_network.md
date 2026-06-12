---
title: "how do I upgrade multiple machines without network?"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by wanchai on 2007-10-19
I'd like to upgrade several machines from 7.04 to 7.10, and I don't want to download the same stuff over and over again. The [[COLOR="Blue"]upgrade procedure[/COLOR]]("http://www.ubuntu.com/getubuntu/upgrading") says I should burn an alternate CD, pop that in, and the rest is automatic. Did that. Then comes a pop up asking whether I want to include the latest upgrades from the Internet. I said "no". The upgrade then grabs a few hundred files from the CD and now it starts downloading the majority of files from the Internet anyway, and the speed is very slow. I wanted to avoid this. Shouldn't it be possible to upgrade the whole system from the CD only? Since the release was only yesterday I don't expect to find that many new things in the repository, so what is it doing on the net? I may have a few extra packages here and there, but that's not three quarters of the 1228 files it wants to upgrade now.

---

### Post by bmorency on 2007-10-19
> **wanchai said:**
> I'd like to upgrade several machines from 7.04 to 7.10, and I don't want to download the same stuff over and over again. The [[COLOR="Blue"]upgrade procedure[/COLOR]]("http://www.ubuntu.com/getubuntu/upgrading") says I should burn an alternate CD, pop that in, and the rest is automatic. Did that. Then comes a pop up asking whether I want to include the latest upgrades from the Internet. I said "no". The upgrade then grabs a few hundred files from the CD and now it starts downloading the majority of files from the Internet anyway, and the speed is very slow. I wanted to avoid this. Shouldn't it be possible to upgrade the whole system from the CD only? Since the release was only yesterday I don't expect to find that many new things in the repository, so what is it doing on the net? I may have a few extra packages here and there, but that's not three quarters of the 1228 files it wants to upgrade now.

what you might need to do is download the DVD version of gutsy so it will include more packages. try to upgrade like you are doing. it might not need to go to the internet then since there is more available on the dvd.

---

### Post by timcredible on 2007-10-19
i've done this before - i made a copy of the repos onto a portable usb drive (i think it took about 35gb).  this takes a while, but then you have a repo you can use on any machine to do the upgrade and to install any new packages you want.  there's a post somewhere that has the exact rsync command to do this, and shows how to edit your synaptic so it looks at your hard drive.

---

### Post by davidjmayo on 2007-10-19
have a look at aptoncd and see what you think

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by jetpeach on 2007-10-19
here is a bug for this, kinda
[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/153843](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/153843)
this bug is for downloading packages that are even available on the CD rom.
there might be another bug for just being able to upgrade without downloading at all, i'm not sure.

---

### Post by wanchai on 2007-10-19
Thanks, I will try some of these Repo on CD or DVD ideas.
 
But it also helps to verify the md5 of the iso before burning it on CD. My download wasn't good ](*,)

---

