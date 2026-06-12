---
title: "upgrading w/out net connection"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by Techmobowl on 2007-12-04
My PC has no internet connection but I've been able to DL some ubuntu packages at another location and manually transfer and install the ".deb" files (Xubuntu 7.04).

I've read that some of my audio problems (crackling, etc...) might be related to the libsdl package I'm using.

[COLOR="Blue"]My question[/COLOR] - (Should I ?) and how would I uninstall the current "libsdl-alsa" and install the "libsdl-all" ?  This is all with no internet connection, I've downloaded the "libsdl-all.deb".

Thanks

---

### Post by barney_1 on 2007-12-04
You should be able to use apt-get to uninstall the old package:
```
sudo apt-get remove libsdl-alsa
```

If that fails to work open up Synaptic and search for libsdl-alsa and choose to remove that.

You can install .deb files as follows:
```
sudo dpkg -i nameoffile.deb
```

---

### Post by ruibernardo on 2007-12-04
I was going to try to help you, Tecmobowl, but I can't find the packages you are talking about.

You could use my website ([nonetdebs]("http://nonetdebs.homeip.net")) to list the package files (and all the dependencies you still don't have installed) you want to install a package.

You could use it also to upgrade all the packages you have installed on the offline computer - it's a loooong list of packages, don't do it if you don't need to.

To just upgrade one package and their dependencies (if they need to be upgraded too - they often do), lets say for example "perl" - got a new update today - you would do the following:[INDENT] - First, create an account.

- Setup your account [as described here]("http://ubuntuforums.org/showpost.php?p=3742162&postcount=11"). You will need to upload 1 file from the offline computer: /var/lib/dpkg/status

- To upgrade just "perl", proceed as you where going to install it (described on the previous link), but add the option "--show-upgraded" after the name of the package:
> perl --show-upgraded(type "man apt-get" and then search for "--show-upgraded" to know a little more). If you don't add the "--show-upgraded" option, you will not get any package to download because it is already installed.

- Click the link "New packages" on the left and wait 1 minute. You will get a list the package files (*.deb) you need to download to upgrade the package you typed. NOTE: the "Upgrade" link is to upgrade all the packages as in "sudo apt-get upgrade", it's not what you want.

- Then download and copy the .deb files to the offline computer and install them with:
```
sudo dpkg -i *.deb
sudo apt-get install -f
```For example, to upgrade just "perl" to the latest package version, from a fresh install of Ubuntu 7.10 Desktop on a i386 (generic kernel), you would need to download the following packages:
[/INDENT][http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.8.8-7ubuntu3.1_all.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-modules_5.8.8-7ubuntu3.1_all.deb)
[http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-suid_5.8.8-7ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-suid_5.8.8-7ubuntu3.1_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.8-7ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/libperl5.8_5.8.8-7ubuntu3.1_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.8-7ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl_5.8.8-7ubuntu3.1_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-base_5.8.8-7ubuntu3.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/perl/perl-base_5.8.8-7ubuntu3.1_i386.deb)

Good luck.

---

