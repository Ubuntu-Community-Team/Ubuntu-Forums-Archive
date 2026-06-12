---
title: "synaptic: what are &quot;packages kept back&quot;?"
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by peter360 on 2007-03-23
Just curious: when I install a package using synaptic, I was told "1 package installed, 13 packages kept back and not upgraded".  What does the second part of the message mean?  What is the relationship between those packages that are kept back and the package I am installing?

---

### Post by djdicbob on 2007-03-23
I am not sure if I know all the reasons....someone correct me please:)   

Many times the kernel is held back and will be installed when you issue the "apt-get dist-upgrade" command.  I personally have never seen anything but the kernel held back, but I think the same goes for packages updates as well...  In synaptic over time those packages will install as the distro matures.

LESS LIKELY-- This could mean package dependencies have issue.  Which would usually post an error in Synaptic.   Hope that opens the door a little.

---

### Post by mcduck on 2007-03-23
> **peter360 said:**
> Just curious: when I install a package using synaptic, I was told "1 package installed, 13 packages kept back and not upgraded".  What does the second part of the message mean?  What is the relationship between those packages that are kept back and the package I am installing?

Most likely there is no relation with what you have installed and what is kept back. Packages that are kept back have some dependencies that cannot be satisfied for some reason. Either they are not yet available in Ubuntu repositories, there is something wrong with your sources.list or you are using some unofficial extra repository that causes problems.

To get more info about the reason, look at the upgradeable packages in Synaptic, mark them for upgrade and you'll get a message why they cannot be upgraded.

---

### Post by ffxr on 2007-03-23
sorry to troll, but it is relevant i guess..

i compiled my own 2.6.20 kernel .. and cant work out how turn off the kernel 2.6.17-11 update nag.. can anyone assist?

---

### Post by Arby on 2007-03-23
There's a  good explanation of this issue here [http://www.debian-administration.org/articles/69](http://www.debian-administration.org/articles/69) Also check out man apt-get and look at the difference between upgrade and dist-upgrade. Basically, if the upgrade requires removal of any packages then apt-get upgrade will not attempt to resolve them. apt-get dist-upgrade has 'smarter' dependency resolution so it will attempt to process these issues.

It can happen with packages other than the kernel, I had it happen with Open Office a few weeks back. That's how I learned this. It occurs if the dependencies of an installed package have changed in the new version. So if the new version depends on something that the old version didn't then you will see this type of message. To cut a long story short the command below should install those packages ```
sudo apt-get dist-upgrade
```

---

### Post by az on 2007-03-23
> **mcduck said:**
>    r they are not yet available in Ubuntu repositories, there is something wrong with your sources.list or you are using some unofficial extra repository that causes problems.


You can usually get that if you mix repositories.  Like if you mix Dapper and Edgy repos.  It's never a good idea to mix repos.  Just change them all or don't.  Don't just add one extra repo without chaging everyting over.

> **ffxr said:**
> sorry to troll, but it is relevant i guess..

i compiled my own 2.6.20 kernel .. and cant work out how turn off the kernel 2.6.17-11 update nag.. can anyone assist?

You can lock the version.  Ini Synaptic, you can select the package and then tell it to keep that version.  In Dapper, you still get the message that it is available, but it will not install it and replace your hand-made one.  I'm not sure if you still get that notification in Edgy or Feisty in that case.

---

### Post by amadeov on 2007-03-29
> **Arby said:**
> There's a  good explanation of this issue here [http://www.debian-administration.org/articles/69](http://www.debian-administration.org/articles/69) Also check out man apt-get and look at the difference between upgrade and dist-upgrade. Basically, if the upgrade requires removal of any packages then apt-get upgrade will not attempt to resolve them. apt-get dist-upgrade has 'smarter' dependency resolution so it will attempt to process these issues.

It can happen with packages other than the kernel, I had it happen with Open Office a few weeks back. That's how I learned this. It occurs if the dependencies of an installed package have changed in the new version. So if the new version depends on something that the old version didn't then you will see this type of message. To cut a long story short the command below should install those packages ```
sudo apt-get dist-upgrade
```

After upgrading to edgy, I am also getting the "packages kept back" message, mainly with some python related packages. 

I have tried doing the code that you mentioned above "sudo apt-get dist-upgrade" and I am still getting the same error message:
The following packages have been kept back:
  hpijs python-adns python-clientcookie python-crypto python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
  python-gadfly python-htmlgen python-htmltmpl python-imaging
  python-imaging-sane python-jabber python-kjbuckets python-ldap
  python-mysqldb python-pam python-pexpect python-pgsql python-pylibacl
  python-pyopenssl python-pyxattr python-reportlab python-simpletal
  python-soappy python-sqlite python-syck python-xmpp
0 upgraded, 0 newly installed, 0 to remove and 29 not upgraded.

Any ideas?

---

### Post by girard on 2007-03-29
the link above mentioned something about the servers. that could be one reason. i'm actually waiting for dist-upgrade to finish right now.

is it possible to update/upgrade only python related stuff? somehwat like:

sudo aptitude upgrade python

 - i'm new to this so pardon (and correct me please) for wrong syntax (arrangement, not sure what you call it)

---

### Post by amadeov on 2007-04-03
The answer that finally worked for me was typing:

```
sudo aptitude update && sudo aptitude dist-upgrade
```

I found that in another thread here: [http://ubuntuforums.org/showthread.php?t=342960&page=2]("http://ubuntuforums.org/showthread.php?t=342960&page=2")

The person there was having a very similar problem that involved another mix of packages and many of the same python packages that were coming up as "packages kept back" for me.  

Yay solving problems! =)

---

