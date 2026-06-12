---
title: "Can KXstudio repos be installed into Lubuntu?"
date: 2015-02-25
forum: Installation &amp; Upgrades
---

### Post by yoshii on 2015-02-25
Hello,

I had good results with UbuntuStudio in the past.  But then I got a chance to try Lubuntu and I liked the feel of it better than UbuntuStudio.  For a future project I am considering turning a Lubuntu install into a Digital Audio Workstation.  

So my question is, "Can Lubuntu be safely upgraded for digital audio using the KXstudio repos?"  And, "Will I need to use a low-latency kernel?".  

I saw some good stuff within the Ubuntu Wiki on sound settings and at a LinuxAudio website.  So I'm rather hopeful.  

Any replies would be appreciated.

---

### Post by deadflowr on 2015-02-25
They should be installable, at least that is what kxstudio says
From here
[http://kxstudio.sourceforge.net/Repositories](http://kxstudio.sourceforge.net/Repositories)
> Ubuntu users can also install deb files for the repositories, but different files are needed for each version.
As such, we recommend you to enable the repositories using the command-line instead. Just follow these steps:
# Cleanup previous installations if needed
sudo rm -f /var/kxstudio/*
sudo apt-get purge kxstudio-repos


# Install needed tools
sudo apt-get install software-properties-common wget


# Enable KXStudio repo (press 'Enter' once asked)
sudo add-apt-repository ppa:kxstudio-debian/kxstudio


# Update software sources
sudo apt-get update


# Install kxstudio-repos
sudo apt-get install kxstudio-repos


# Update software sources again
sudo apt-get update

If they can be installed on Ubuntu they can be installed on Lubuntu.

---

