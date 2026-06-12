---
title: "Need help fixing boot."
date: 2021-05-29
forum: Installation &amp; Upgrades
---

### Post by samkingmisc on 2021-05-29
I am a novice. I installed ubuntu 21.04 on a SuperMicro 1U server . However, the system does not boot on reboot and cannot find the OS.

I used the boot repair disk to fix the issue. However, it did not fix this issue. Here is the ubuntu pastebin url from the boot repair. [http://paste.ubuntu.com/p/HQ6hWmYpvr/](http://paste.ubuntu.com/p/HQ6hWmYpvr/)

I would appreciate if your support in resolving this issue.

Regards 

Subhash.

---

### Post by TheFu on 2021-05-31
Novice users should use the LTS releases, not the intermediate, short-term-support releases.
The last LTS is 20.04.  Google "LTS Ubuntu" for more information.

Using server hardware implies that you are trying to install the Server version of Ubuntu. Yes or no?
Desktop installers are different from server installers.

I skimmed the information.

In general, don't attempt to use RAID of any type on your first install.  Don't.  Just don't. There are many complexities that a novice will likely miss.

In general, it is best to install with just 1 HDD connected during the installation.  If you select an LVM install, you can add another HDD post-install and setup a RAID1 mirror later, if you like.

It appears that the system should boot from sda, but grub is installed on sdb.  If you only have 1 disk connected during the installation, this cannot happen.

Try doing the install with 20.04 Server. See how that goes.  When 22.04 is released, it will be the next LTS and you can move to that a few months later.  Many businesses delay moving to an LTS for 6 months after the initial release to give the team time to address early failures.  Non-LTS releases have such short support periods that for servers, it just isn't worth our time to bother.  I look at non-LTS releases just to play, never for any serious use.  Generally, non-LTS releases only get used for 1-2 weeks before I wipe them.
[https://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release](https://blog.jdpfu.com/2013/07/19/why-ubuntu-users-should-run-an-lts-release) is why I use LTS releases.

---

