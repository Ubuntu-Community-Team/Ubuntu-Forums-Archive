---
title: "Error - apt-get update after using apt-mirror to create local repository on USB HD"
date: 2018-10-11
forum: Installation &amp; Upgrades
---

### Post by john3j on 2018-10-11
Greetings!

I have some Ubuntu 16.04 LTS workstations that cannot be connected to a network and the only way I can update them is by use of a USB hard drive.  I have created a local repository on my USB hard drive using apt-mirror, as outlined in the following:

[https://popey.com/blog/posts/2006/10/24/creating_an_ubuntu_repository_mirror_with_apt-mirror.html](https://popey.com/blog/posts/2006/10/24/creating_an_ubuntu_repository_mirror_with_apt-mirror.html)

I have updated my sources.list and mirror.list files as described in the previous link, however, I have changed my mount point and from edgy to xenial.  After going through all of this, I receive errors related to a release file and files that I have verified as existent in the folder structure.  I am not sure why I am being told that these files could not be found.  If anyone could take a look at the instructions I followed, the attached .txt files for output from running sudo apt-get update, as well as sources.list and mirror.list to help me figure out what is going on, it would be greatly appreciated.  I am stumped and the fixes I found online don't seem to help, such as adding [arch=amd64] to my sources.list file.

-John

---

