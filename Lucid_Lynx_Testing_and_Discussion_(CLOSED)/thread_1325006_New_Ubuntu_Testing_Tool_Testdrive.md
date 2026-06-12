---
title: "New Ubuntu Testing Tool: Testdrive"
date: 2009-11-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-11-13
[Dustin Kirkland]("https://launchpad.net/%7Ekirkland") has created a new tool called Testdrive, which provides a simple way to run an Ubuntu (milestone) release in the virtual machine of your choosing (KVM or Virtualbox). It automates the process of setting up a virtual machine, downloading incremental updates to your testing ISO image and running the system.

Check out his blog post for details:

[LIST]
[*][Introducing Testdrive!]("http://blog.dustinkirkland.com/2009/11/introducing-testdrive.html")
[/LIST]

---

### Post by ssam on 2009-11-13
looks nice.

remember the easy way to add a ppa
```
sudo add-apt-repository ppa:testdrive/ppa
```

tried with an iso file i alread have, but get

```
sam@oberon:~$ testdrive -f /data/iso/karmic-release/ubuntu-9.10-desktop-amd64.iso
/data/iso/karmic-release/ubuntu-9.10-desktop-amd64.iso: 2: CD001LINUX: not found

Usage:
  testdrive [-f FILE] [-u URL]

  testdrive is a utility that allows you to easily download the latest Ubuntu
  development release and run it in a KVM virtual machine.

  All options to this program are handled through the global configuration
  file, /etc/testdriverc, and then the user's local configuration file,
  ~/.testdriverc.

  Users wanting to change the behavior default configuration can make a
  copy of /etc/testdriverc, and pass this as a parameter to testdrive.

```

PS: are there lucid daily CDs yet?

---

### Post by shakaran on 2009-11-14
Nice! Although, the hardware specific bugs (PCI, ethernet,  graphic cards, etc) only can be tested with real installations, but well for the other gazillion of bugs it's  a real option!

---

### Post by 23meg on 2010-02-21
Dustin Kirkland has a new post with instructions for testing Lucid with Testdrive:

[list][*][Have you taken Lucid for a testdrive yet?]("http://blog.dustinkirkland.com/2010/02/have-you-taken-lucid-for-testrive-yet.html")[/list]

---

