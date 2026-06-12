---
title: "Create archive, install on non-networked host"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by sampsont on 2012-11-14
I want to use apt-get to do the following with (host A, ON internet) and (host B, NO network)

[LIST]
[*]On host A, get some apps, ie: sudo apt-get download xinetd tftpd tftp
[*]Put the .deb files on a thumb drive
[*]On host B, plug in the thumb drive and install the apps.
[/LIST]

The apt-get download command puts these files in the current directory:

[INDENT]tftp_0.17-18ubuntu2_i386.deb
tftpd_0.17-18ubuntu2_i386.deb
xinetd_2.3.14-7ubuntu4_i386.deb[/INDENT]

This is great! I can now put them on my thumb drive and put them on my non-networked hostB.

**My question is: What do I type on hostB to install these .deb files?**

Thanks,
Todd

---

### Post by ibjsb4 on 2012-11-14
I don't think your going to get the dependencies.  Example:

 [http://packages.ubuntu.com/zh-tw/precise/i386/xinetd](http://packages.ubuntu.com/zh-tw/precise/i386/xinetd)

Click on the packages that make up xinetd and you find they have dependencies.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=download+install+packages+without+internet&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=download+install+packages+without+internet&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by pkadeel on 2012-11-15
You need to setup a trivial repository.
[http://www.debian.org/doc/manuals/repository-howto/repository-howto](http://www.debian.org/doc/manuals/repository-howto/repository-howto)

It sounds good to avoid multiple downloads of same files if you have to upgrade multiple computers at the same time i.e. for admins. However for single PC users, these trivial repositories are not much effective because when you need to re-use that local repository, the packages on the actual repositories have been further upgraded and eventually you endup downloading new packages.

---

### Post by varunendra on 2012-11-15
Todd,
Answer to your question first -
```
sudo dpkg -i* <package-name>*
```For example - [I]sudo dpkg -i tftp_0.17-18ubuntu2_i386.deb
[/I]
However, there is a very nice tool - AptOnCD, which does what you want very efficiently and elegantly. It is in the default repositories. From its description -
> APTonCD  is  a complete solution to manage/backup/restore your packages
       downloaded via apt-get, aptitude and synaptic.   APTonCD  also  is  the
       best choice to download an entire repository and/or specific section of
       selected mirror, by an pretty GUI.
By default it picks all the (relevant) packages from **/var/cache/apt/archives** directory *(that's the place where the packages are downloaded and stored for future use before being installed)*. You can also include manually downloaded packages. It then creates one or more cd/dvd iso(s) (as you choose) depending on the size of the selected packages.

These ISOs can then be used to either burn CD/DVDs [COLOR=DarkSlateGray]*(which would automatically be recognized as "Software-Sources" by your package manager as soon as inserted)*[/COLOR], or you can use AptOnCD again (besides other methods) to restore/install all or selected packages directly from the iso - without burning them to cd/dvd.
[COLOR=DarkRed]*[The "Restore" button function is somewhat broken in latest Ubuntu versions. You need to manually install "**hal**" package to make it work.]*[/COLOR]

The best part is - it takes care of dependencies - just like apt-get does, and it can create a 'meta-package' (selected by default) which can install all the included packages (if supported) in one-click !

Hope it helps.

---

