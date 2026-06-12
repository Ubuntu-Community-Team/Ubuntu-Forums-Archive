---
title: "Can't upgrade mariadb before kernel upgrade - repo gone"
date: 2014-04-01
forum: Installation &amp; Upgrades
---

### Post by dheianevans on 2014-04-01
Was looking to do a kernel upgrade on my Digitalocean-hosted site. Was getting ready to do the recommended update & upgrade before running their kernel upgrade process.

The only problem is that mariadb seems to have removed their repos for raring ringtail, so I can't upgrade that program.

Err [http://ftp.osuosl.org](http://ftp.osuosl.org) raring/main amd64 Packages 404  Not Found [IP: 64.50.233.100 80] 
W: Failed to fetch  [http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu/dists/raring/main/binary-amd64/Packages](http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu/dists/raring/main/binary-amd64/Packages)   404  Not Found [IP: 64.50.233.100 80]

What should my next step be? Can I run sudo apt-get upgrade and upgrade as much as I can? Will I be able to somehow upgrade mariadb after the kernel upgrade?

Thanks.

---

### Post by bapoumba on 2014-04-02
Please understand I know nothing about db and stuff.
[https://downloads.mariadb.org/mariadb/repositories/#mirror=cnrs&distro=Ubuntu&distro_release=saucy](https://downloads.mariadb.org/mariadb/repositories/#mirror=cnrs&distro=Ubuntu&distro_release=saucy)
But looks like they have versions for saucy and trusty.

So if you remove your third party repos (all of them) and run your upgrade, you should be able to upgrade it afterwards. Your particular repo has the saucy packages : [http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu/dists/](http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu/dists/)

Now if you want to upgrade the kernel only (from your OP, but I'm not quite sure this is what you actually mean), you need to check which kernel version you want to have, and if bugs are documented for your particular version of mariadb.

---

### Post by dheianevans on 2014-04-02
To be clear, you're suggesting that I remove the mariadb repo from my repo list, upgrade everything else to saucy or trusty and then readd the mariadb repos and I'll be able to upgrade mariadb?

And to clarify what I said re: the kernel. DigitalOcean, because it has their VPS system, has their own process for upgrading the kernel.

---

### Post by bapoumba on 2014-04-02
> **dheianevans said:**
> To be clear, you're suggesting that I remove the mariadb repo from my repo list, upgrade everything else to saucy or trusty and then readd the mariadb repos and I'll be able to upgrade mariadb?

And to clarify what I said re: the kernel. DigitalOcean, because it has their VPS system, has their own process for upgrading the kernel.

Yeah, but do not remove the repos, comment them out, and change them to your current release after checking they exist (the mariadb does). That is the idea. What is the process they are using for the kernel upgrade ? If you cannot upgrade the kernel at the same time you upgrade the distribution, then I'm missing something else (in addition to the db stuff :)).

---

### Post by dheianevans on 2014-04-02
They've somehow blocked upgrading the kernel via command line. Instead you select your "droplet" as they call your VPS share and then select the kernel you want to move to.

They suggest a apt-get update & apt-get upgrade before changing the kernel. Hence my problem. I can't get the latest mariadb for my current kernel because they removed the repo for raring from their site.

---

### Post by bapoumba on 2014-04-02
> **dheianevans said:**
> They've somehow blocked upgrading the kernel via command line. Instead you select your "droplet" as they call your VPS share and then select the kernel you want to move to.

They suggest a apt-get update & apt-get upgrade before changing the kernel. Hence my problem. I can't get the latest mariadb for my current kernel because they removed the repo for raring from their site.

Then you have to make sure if and how you can upgrade to a newer Ubuntu release. An update/upgrade wont bump you into saucy or trusty.

---

### Post by dheianevans on 2014-04-02
> **bapoumba said:**
> Then you have to make sure if and how you can upgrade to a newer Ubuntu release. An update/upgrade wont bump you into saucy or trusty.

Thanks, I realize that. They want us to update/upgrade and then run their kernel selector to do the saucy or trusty upgrade.

---

### Post by bapoumba on 2014-04-02
> **dheianevans said:**
> Thanks, I realize that. They want us to update/upgrade and then run their kernel selector to do the saucy or trusty upgrade.

OK, have you done it before ? I mean, on their host.
If yes, then comment out any third party repo, do the release upgrade to saucy, proceed to upgrading the kernel (I'm still not sure how they work that out), enable the mariadb repo for saucy, update/upgrade and you should be good.

---

### Post by dheianevans on 2014-04-02
Commented out the mariadb repo but noticed I'm having another update issue too:

Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/universe amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_universe_binary-amd64_Packages)

my sources.list:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates universe
# deb [http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu](http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu) raring main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse

It may be a lack of coffee, but I'm not seeing the duplicate. :-)

---

### Post by bapoumba on 2014-04-02
I was going to bed, you made me log back in after I saw the notification email :)
Bolded out the ones I think are duplicates (but sleepy here).
I think it is incomplete however, as I do not see the restricted repo, or the security for universe.
> **dheianevans said:**
> Commented out the mariadb repo but noticed I'm having another update issue too:

Duplicate sources.list entry [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) raring/universe amd64 Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_raring_universe_binary-amd64_Packages)

my sources.list:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates main
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security main
**deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring universe**
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring-updates universe
# deb [http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu](http://ftp.osuosl.org/pub/mariadb/repo/5.5/ubuntu) raring main
**deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring universe multiverse**
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) raring universe multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) raring-updates multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) raring-security multiverse

It may be a lack of coffee, but I'm not seeing the duplicate. :-)

---

