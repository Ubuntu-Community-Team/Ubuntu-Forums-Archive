---
title: "libgl1-mesa dependencies prevent update"
date: 2013-01-29
forum: Installation &amp; Upgrades
---

### Post by francwalter on 2013-01-29
Hello

on my Ubuntu 12.04 LTS Server (64 Bit) I have some updates in aptitude (GUI) which won't be installed because the packages are hold automatically (A):

[B]ligbl1-mesa-dri
libgl1-mesa-glx
libglapi-mesa[/B]

There are dependencies which would break if I forced updates, aptitude says, e.g.:

[B]libgl1-mesa-dri replaces libgl1-mesa-dri:i386
libgl1-mesa-glx replaces libgl1-mesa-glx:i386
libglapi-mesa replaces libglapi-mesa:i386
 [/B]
I have not installed these i386-packages on my 64-bit machine anyway!
And I don't have any GUI or X11 installed on the server.

Can I just force these updates or will I break important programs?

As well I have 13 packages which are hold back (manually I guess):

[B]dkms
isc-dhcp-client
isc-dhcp-common
libdrm-intell
libdrm-nouveau1a
libdrm-radeon1
libdrm2
libplymouth2
plymouth
plymouth-theme-ubuntu-text
ubuntu-minimal
ubuntu-standard
upstart[/B]

All these are hold on their version without any comment about breaking some other package dependencies.
Can I force these updates too?

Kind thanks for an answer, frank

---

### Post by ibjsb4 on 2013-01-29
What about trying a dist-upgrade (#3)?

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by francwalter on 2013-01-29
Yes! 
This did the trick, the updates were done successfully with this command:

**apt-get dist-upgrade**

Thank you!

frank

---

### Post by ibjsb4 on 2013-01-29
Welcome :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

