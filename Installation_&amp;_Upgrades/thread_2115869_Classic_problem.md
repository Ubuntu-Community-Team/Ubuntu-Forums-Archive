---
title: "Classic problem?"
date: 2013-02-14
forum: Installation &amp; Upgrades
---

### Post by giuscri on 2013-02-14
Hi everyone, I'm finding troubles in updating Ubuntu. Typing inside the terminal ```
$ sudo apt-get update
``` updating stops giving me the following message: ```
W: GPG error: http://ppa.launchpad.net quantal Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2B3F92F902D65EFF

```How could I solve this problem? I'm using Ubuntu 12.10.

Thank you in advance,
Giuseppe

---

### Post by kc1di on 2013-02-14
Hello giuscri and welcome to Ubuntu,

You have a bad PPA repository in your sources list somewhere.

do you rememeber what ppa you installed?

This is what I would try first

go to software center >edit tab >software sources.

Go to Other tab and uncheck all your ppa's for now.
the try running apt-get update again.  

good luck.

---

### Post by giuscri on 2013-02-14
> **kc1di said:**
> Hello giuscri and welcome to Ubuntu,

Thank you!  :wink:

> **kc1di said:**
> Go to Other tab and uncheck all your ppa's for now.
the try running apt-get update again.  

Ok! That works now. Unfortunately I don't know exaclty what a PPA is, but I would say: now that I've *unthick* all the ppa's repository, *sudo apt-get update* it's working but just because I've ignored the problem, not solved that at all ...

These are my two problematic ppa's resositories:

```
http://ppa.launchpad.net/linrunner/tlp/ubuntu
http://ppa.launchpad.net/linrunner/tlp/ubuntu

```where, with the second one, there's a label that says that's *source code*.

Here's a picture: [IMG]http://s17.postimage.org/ez3x05e5b/Screenshot_from_2013_02_14_12_52_25.png[/IMG]


Thanks for the attention.[IMG]http://postimage.org/image/fbvb6bwez/[/IMG]

---

### Post by kc1di on 2013-02-14
Hi again,

PPA's are personal package repositories and are allowed by Ubuntu for 3rd party software that is not checked by ubuntu developers.

you must have installed linrunner at some point. 

I'm not familar with that program but I would just leave it unchecked for now. It may be a server problem that will be fixed in a few days or they may have a bad package signature which again they would have to fix. 
Happy computing :)

---

### Post by kc1di on 2013-02-14
a little more research reveals this [page]("https://launchpad.net/~linrunner/+archive/ppa") about linrunner ppa's

it says right in the description you should not use the ppa as it's unstable.  

look at the list of programs and see if you've installed any of them?

---

### Post by Anaximander Thales on 2013-02-14
> **giuscri said:**
> Hi everyone, I'm finding troubles in updating Ubuntu. Typing inside the terminal ```
$ sudo apt-get update
``` updating stops giving me the following message: ```
W: GPG error: http://ppa.launchpad.net quantal Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2B3F92F902D65EFF

```

You may also need to grab the key.  You don't mention how long ago you put in the repository, whether it worked in the past or not nor how you added the repository.  

However, this [[COLOR=blue]THREAD[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1983220") addresses that particular error with two solutions being needed to address the OP's issue.

The OP had to add the keys for some of the repo's and then had to clean and clear the cache.  

Since you don't mention how you added the repository, I'll address that and you can verify your steps for how you added it. If you added the repository manually, i.e. added it in directly to the sources.list file, or added it in through the Other Repos tab, then you'll either need to add the signature key manually (d/l from launchpad, and import into synaptic under the Authentication tab) or delete the entry and, in a terminal, run: sudo add-apt-repository ppa:user/ppa-name.

The easiest way to add a repo from launchpad is to run the add-apt-repository ppa:user/ppa-name as it grabs the key and adds the repo into your sources list.

Hope this helps.
AT

---

### Post by oldos2er on 2013-02-14
> W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) quantal Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2B3F92F902D65EFF

Add the key: ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 2B3F92F902D65EFF

sudo apt-get update
```

---

### Post by linrunner on 2013-02-15
> **kc1di said:**
> a little more research reveals this [page]("https://launchpad.net/~linrunner/+archive/ppa") about linrunner ppa's

it says right in the description you should not use the ppa as it's unstable.
Look again, there is more than one PPA. giuscri tried to install TLP from ppa:linrunner/tlp which is just fine.

@giuscri: use oldos2er's suggestion.

---

