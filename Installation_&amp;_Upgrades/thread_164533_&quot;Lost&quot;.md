---
title: "&quot;Lost&quot;"
date: 2006-04-22
forum: Installation &amp; Upgrades
---

### Post by general_error on 2006-04-22
I'm new to the world of Ubuntu and I feel completely lost.

I come from the world of Slackware, then Mandrake, then RedHat/Fedora Core so I'm not new to the Linux world at all.  I keep wanting to run RPM commands because I don't know the deb equivalents.  

Is there a site that shows you the apt-get version of rpm commands?

For example, I want to know what I have installed on my box.  I want to run "rpm -qa"... no dice.

I know I need a package to provide package foo.  What's the command to LOCATE what package provides file foo when the package is not installed.  In rpm I'd use the rpmdb for that.

The only way I ever figure out what to install in Ubuntu via apt-get is by googling around and looking at forums.  There has to be a better way.

---

### Post by jazzmuzik on 2006-04-22
Use Synaptic to see what's on your system and what's available for install. Otherwise try:

dpkg -l
dpkg --get-selections

yum is analogous to apt-get and rpm is analogous to dpkg.

If you want to download and install something:

apt-get install programName

If you already have the deb package on your hard drive you install that with 

dpkg -i programName.deb

apt-get is better than yum/rpm at getting all the dependencies you need.

There's a package called apt-show-versions. It is like an "rpm -qa". You could install it with this:

apt-get install apt-show-versions

What provides:

dpkg -S

rpmbuild == dpkg-buildpackage

---

### Post by Sef on 2006-04-26
Check out this by psychocats on installing and converting .rpm to .deb.

[http://www.psychocats.net/ubuntu/installingsoftware.php]("http://www.psychocats.net/ubuntu/installingsoftware.php")

---

