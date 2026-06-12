---
title: "Installing old version of mono"
date: 2021-07-02
forum: Installation &amp; Upgrades
---

### Post by tom-dean on 2021-07-02
I'm trying t[SIZE=2]o get protocol fuzzer ce (the community edition of what use to be peach fuzz) installed. So far everything seems to have worked in the build except for the components that require mono. The default version of mono installed in 20.04 appears to be 6.X. The build system for protocol fuzzer insists on a mono version prior to 4.4. 

I've tried apt-install mono-complete=4.0, but it doesn't know that version. How do I find out what the versions numbers for ubuntu are?

based on: [/SIZE]https://stackoverflow.com/questions/33763177/install-older-version-of-mono[SIZE=2]

I added a file[/SIZE]mono-official.list in /etc/apt/sources.list.d that contains

deb [https://download.mono-project.com/repo/ubuntu](https://download.mono-project.com/repo/ubuntu) wheezy/snapshots/4.2 wheezy main


Since that seems to be the only distribution on mono-project that has a 4.x vision. However, when I do an  apt update
I get the Messages:

```
W: Conflicting distribution: https://download.mono-project.com/repo/ubuntu wheezy/snapshots/4.2 InRelease (expected wheezy/snapshots/4.2 but got wheezy)
W: Skipping acquire of configured file 'wheezy/binary-i386/Packages' as repository 'https://download.mono-project.com/repo/ubuntu wheezy/snapshots/4.2 InRelease' doesn't have the component 'wheezy' (component misspelt in sources.list?)

```
And 8 more variants of the second message with different file names.

Thanks for any help.

---

### Post by CatKiller on 2021-07-02
Adding Debian repositories to Ubuntu is a Bad Plan. Particularly ancient ones. Be thankful that it didn't work.

[That project currently has build issues](https://gitlab.com/gitlab-org/security-products/protocol-fuzzer-ce/-/issues/2) as a result of it only being built with Visual Studio on Windows before it got open sourced. They appear to be working on it.

---

### Post by tom-dean on 2021-07-02
Thanks for the info.

---

