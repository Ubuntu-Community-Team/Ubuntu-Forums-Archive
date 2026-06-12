---
title: "Can not get unattended setup run commands at the end."
date: 2016-03-10
forum: Installation &amp; Upgrades
---

### Post by mint1mint on 2016-03-10
Hi. I try to make an unattended setup that will configure proxy, install programs and make some settings of Gnome.
But this "success_command" do not work. Files are not created. Is here some mistake?
```

ubiquity ubiquity/success_command string \
in-target echo 'Acquire::http::Proxy "http://proxy.domain.com:3128/";'>/etc/apt/apt.conf.d/95proxies; \
in-target echo 'Acquire::https::Proxy "http://proxy.domain.com:3128/";'>>/etc/apt/apt.conf.d/95proxies; \
in-target echo 'Acquire::ftp::Proxy "http://proxy.domain.com:3128/";'>>/etc/apt/apt.conf.d/95proxies; \
in-target echo export http_proxy="http://proxy.domain.com:3128/">/etc/profile.d/proxy.sh; \
in-target echo export https_proxy="http://proxy.domain.com:3128/">>/etc/profile.d/proxy.sh; \
in-target echo export ftp_proxy="http://proxy.domain.com:3128/">>/etc/profile.d/proxy.sh; \
in-target echo export no_proxy="localhost,127.0.0.1,localaddress,.localdomain.com">>/etc/profile.d/proxy.sh; \
in-target echo export HTTP_PROXY="http://proxy.domain.com:3128/">>/etc/profile.d/proxy.sh; \
in-target echo export HTTPS_PROXY="http://proxy.domain.com:3128/">>/etc/profile.d/proxy.sh; \
in-target echo export FTP_PROXY="http://proxy.domain.com:3128/">>/etc/profile.d/proxy.sh; \
in-target echo export NO_PROXY="localhost,127.0.0.1,localaddress,.localdomain.com">>/etc/profile.d/proxy.sh

```

---

### Post by TheFu on 2016-03-10
I've never touched anything related to ubiquity and don't know **anything** about it.
However, I do build and configure servers using automatic processes all the time ... with ansible.  Is that something worth considering?  It is cross-platform and handles this sort of stuff easily.  

Plus the whole "devops" thing looks good on a resume.

---

### Post by mint1mint on 2016-03-11
Well usualy I work with Windows. I make an image using Ghost and load it to workstations. It is very very easy basic task. I hoped that Linux won't be a pain in this. May be Ubuntu was a bad choice and I should turn to Suse...

---

### Post by sudodus on 2016-03-11
Maybe you should use the [Ubuntu OEM Installation](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)

---

### Post by mint1mint on 2016-03-11
Looks like what I need. Thx.

I've read about OEM installation. But does it mean I have to install it every time manualy and manualy setup everything? I want to insert a bootable flash in the desktop and let it do everything automaticaly. Because I can't use individual approach to every of several hundreds workstations.

---

### Post by sudodus on 2016-03-11
The idea with OEM install is that you set it up once. You install the extra program packages that you want to add, and create global settings.

But the user's own environment will be set up the end user. (Is this what you want, or do you want to set up the user's own environment too?)

When you have a system that you think is good, you can make a compressed cloned image of it, for example with ***Clonezilla***. After that you can create systems from the image into drives of the same size or larger. Cloning will be easier, if you make the installation in BIOS mode. It is possible also in UEFI mode, but it can be complicated if the drive size is different.

An alternative is to create a tarball, a compressed tar archive, with the ***One Button Installer***. After that you can create systems from the tarball also into smaller drives than the original one. This method works only in BIOS mode.

If you intend to install into identical workstations, or at least machines with the same graphics and wifi hardware, you can install proprietary drivers. Otherwise you should keep the free drivers in order to make it work with different brands and models of graphics and wifi chips/cards.

---

### Post by sudodus on 2016-03-11
I should add a comment about Ghost - and Clonezilla.

Many years ago I used Ghost to clone installed Windows systems. I would say that Clonezilla is a free tool, that can do something similar to Ghost. Clonezilla can actually clone also Windows (and dual boot systems with Windows and linux installed alongside).

There is a simple 'end user' version of Clonezilla, 'Clonezilla Live', but also a 'pro' version of it. Both are free software. Maybe you are professional enough to use the 'pro' version, 'Clonezilla SE'. See more details at

[http://clonezilla.org/](http://clonezilla.org/)

---

### Post by mint1mint on 2016-03-11
Does it clone good to different hardware? And I need to add some shortcuts to user desktops, language settings etc. Is there something like "default profile" that is copied to new user profile? 
I thought those post-install commands in ubiquity could help with everything i need.

---

### Post by sudodus on 2016-03-11
Clonezilla clones (makes cloned copies). If the cloned copy works in different hardware, fine :-)

Linux is free, so there are no obstacles created to make you pay for each copy. It also makes it possible with systems that are portable, but there are limits, as described in post #7. Of course, the computer architecture must match, but within Intel and AMD 32-bit and 64-bit PC systems, things are rather portable.

Make a system in an external box, that you can connect via USB or eSATA, and try to run it in the computers, that you intend to use, and you will find out what works, and what does not work. See this link:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)


It will be a manual hack, but you can edit the directory **/etc/skel** which contains the default settings for creating new user accounts.

-o-

I have not used those post-install commands in ubiquity (except via the OEM cloak). Maybe they *can* do what you want. It is worth trying ...

But I have been using Clonezilla for years, and I have made the One Button Installer. Both work for me.

---

### Post by TheFu on 2016-03-11
a) sudodus is correct.  Cloning (bit-for-bit) almost always works well on Linux desktops.  Only the specific ways that the systems are different matter at all and most of those don't matter.  Linux looks at the hardware after every reboot and loads what is needed.  Only really strange HW might get in the way or proprietary drivers (say the systems have different GPUs).

b) The only thing most people will want to "fix" is to clean up the 70-persistent-net.rules in /etc/udev/rules.d/.   Just remove the non-comment lines so that eth0 will be the default ethernet device used at the next reboot.  Besides that, Linux sorta just works.  It is extremely common to pull a HDD from 1 system and plug it into another and boot, then be happy since everything is exactly the same (except the ethernet card MAC).  HW upgrades are pretty trivial because of this.  Pull a drive from a 1st-gen C2D and drop it into a 4th-gen Core i7 - no problem.

c) if you are working with hundreds of systems, you'll want to automate this stuff.  I wouldn't use cloning. Too much hands-on work.  I'd use cobbler and ansible. cobbler is a PXE boot systems loader and ansible is a systems management tool. Both were written by the same guy.  It is much easier to let the PXE boot handle the base install (via cobbler), then do any fine tuning with Ansible.  Single companies manage thousands of linux systems across many different locations with ansible.  There are 10s of thousands of Ansible users - perhaps you've heard of Chef or Puppet or Salt or Rexify or CFEngine?  Ansible is the much easier-to-use tool that does similar things.  All free.  I know of a few universities and government organizations who use Cobbler for their systems installations and I've been using Ansible for my systems management for a few years. I don't need cobbler, but if I did, wouldn't hesitate to use it.

[https://help.ubuntu.com/community/Cobbler](https://help.ubuntu.com/community/Cobbler)

[https://docs.ansible.com/ansible/intro_installation.html](https://docs.ansible.com/ansible/intro_installation.html)

---

### Post by mint1mint on 2016-03-11
Ok thx a lot for advices. I go to read about these Cobler things.

I need to configure proxy for apt on first start after installation and apt-update/upgrade.
One of the steps is to write "Defaults env_keep..." to sudoers file.
This command works in normal session but I have to reboot after it to get it aplied:
awk '/env_reset/{print;print "Defaults env_keep = \"http_proxy https_proxy ftp_proxy\"";next}1' /etc/sudoers>tmp && mv tmp /etc/sudoers
When I add it to rc.local it does not change the file at all.
Is there working way to edit sodoers file in rc.local or configure proxy for apt on first run?

---

### Post by TheFu on 2016-03-15
Use the easier "include" directories for local overrides. Files with appropriate names in these directories are picked up automatically:
/etc/apt/apt.conf.d/
  and
/etc/sudoers.d/

Do not touch the main config files (sudoers) and using rc.local is NOT the best practice.

Please use **code tags** for any posted code.

An example proxy file:
```
/etc/apt/apt.conf.d# more 02proxy

# Ansible managed: /home/thefu/.ansible//templates/etc_apt_02proxy.j2 modified on 2015-08-18 14:13:39 by thefu on mngmt

Acquire::http { Proxy "http://istar:3142"; };

```
istar is our local apt-cach-ng system, not a generic proxy. I've don't remember setting up a system-wide proxy on any systems.  Have used PAC files in browsers, however. Sorry.

---

