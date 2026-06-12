---
title: "Skype has unresolvable dependencies"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by neocortex on 2007-06-22
Hello!
I am trying to install Skype but with no success. I have tried via Automatix, Synaptic, with the repository:
<[http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free>, but nothing. Constantly, I receive following error-message:

```

skype:
  Depends: libasound2 (>1.0.12) but 1.0.10-2ubuntu4 is to be installed
  Depends: libc6 (>=2.3.6-6) but 2.3.6-0ubuntu20.4 is to be installed
  Depends: libgcc1 (>=1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed
  Depends: libqt4-core but it is not going to be installed
  Depends: libqt4-gui but it is not going to be installed
  Depends: libstdc++6 (>=4.1.1-12) but 4.0.3-1ubuntu5 is to be installed

```

Can anyone help me? What should I do to get Skype?

Best,
PM

---

### Post by tux821 on 2007-06-22
In the past I had some Skype problems too.
As a work-around for those times I used the 'static' version:

[http://www.skype.com/go/getskype-linux-static](http://www.skype.com/go/getskype-linux-static)

Download it and extract it with:

tar  jxf  skype-1.4.0.74-static.tar.bz2

Then start Skype with:

cd  skype_static-1.4.0.74
./skype

---

Hmm just see that you tried to install the 'Debian' Skype version
'<[http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free>'

If you are running Ubuntu .. try the Ubuntu Skype version:

[http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)

Good luck ;)

---

### Post by merlinus on 2007-06-22
> 
If you are running Ubuntu .. try the Ubuntu Skype version:

[http://www.skype.com/go/getskype-linux-ubuntu](http://www.skype.com/go/getskype-linux-ubuntu)
This worked perfectly for me.  Clicking on the downloaded .deb file opened package installer, and it went out, got and installed the needed dependencies.

The only think I had to change was Options/Sound Devices.

-merlin

---

### Post by neocortex on 2007-06-23
Well, yes: problem might be the Debian repo, but as I saw, you both use Feisty while I am still under Dapper. I shall go for the static and report where it took me.

Best,
PM

---

### Post by arnieboy on 2007-06-23
> **neocortex said:**
> Well, yes: problem might be the Debian repo, but as I saw, you both use Feisty while I am still under Dapper. I shall go for the static and report where it took me.

Best,
PM
we have recently made an update to the automatix repositories with regard to skype.. That should pretty much fix it.
Try this
```
sudo apt-get update
```
and then install skype from automatix. You should not get any error this time.

---

### Post by neocortex on 2007-06-25
Too late for the Automatix :sad: I already did it with static tarball, and it went smooth. Just follow the instructions in README.

Best,
PM

---

