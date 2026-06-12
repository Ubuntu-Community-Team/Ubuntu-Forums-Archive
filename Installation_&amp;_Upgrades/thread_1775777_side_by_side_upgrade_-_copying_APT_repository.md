---
title: "side by side upgrade - copying APT repository?"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by bulwynkl on 2011-06-05
Hi All,

I'm wondering how much of my currently installed packages I can transfer to a new system...

what I have in mind.

I have a HDD split in two. I have 10.4 on one half (/dev/sda6) - my working system for the last year or so since my last upgrade - and I have just installed 11.04 on the other half (/dev/sda8). I wanted to check out the new version rather than upgrading.

note I have my home folder and all stored data on other drives (zfs mirrored disks) - the boot disk is mostly OS related...  I can overwrite /dev/sda8 with impunity as long as /dev/sda6 is intact....


What I want to do is capture the wide variety of packages I have installed on the old version and install them onto the new system - without using the dist-upgrade mechanism...  I've had it fail too many times leaving me with a complete rebuild being required...

is this (partially) possible or have too many core packages changed?

I was especially thinking of something like [http://www.ubuntugeek.com/clone-your-ubuntu-installation.html](http://www.ubuntugeek.com/clone-your-ubuntu-installation.html)

to obtain the list:
dpkg --get-selections | awk ‘$2 ~ /^install$/ {print $1}’ > installedpackages

to reinstall:
cat installedpackages | xargs sudo aptitude install -y


another path would be to clone the entire /dev/sda6 onto /dev/sda8, boot into the duplicate and dist-upgrade that 

any other suggestions?

I figure that if I am having this thought, someone else has probably already solved it...

---

### Post by tommcd on 2011-06-05
I would probably use the *dpkg --get-selections* method. See this also: [http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
The one issue you may face is that perhaps some packages on 10.04 may have changed on 11.04. You could always just apt-get any apps that you may still need after doing this though.

I just reinstall everything manually myself. The more you reinstall Ubuntu, the easier it becomes to reinstall it. It is really just a routine thing.

---

