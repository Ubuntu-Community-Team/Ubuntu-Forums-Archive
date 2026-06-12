---
title: "Upgrading a 9.04 Jaunty virtual machine"
date: 2020-02-09
forum: Installation &amp; Upgrades
---

### Post by svennils on 2020-02-09
Hi,
I have a Ubuntu 9.04 Jaunty VM, containing a Arcemu World of Warcraft server for personal use. (I occasionally go exploring for a few hours, or create items & modify stuff after i quit gaming in 2012). Both were installed in 2010 by the file dates, and i no longer have the installer for arcemu, nor the howto. I just remember it being quite a job setting up. Reinstalling on a newer version ubuntu  is not an option. It works, but for one flaw:

Recently, after upgrading the host server hardware, os(18.04 server), and vmware, mouse pointer integration stopped working properly, probably due to age difference between vmware tools in the guest os and the vmware player. The mouse pointer is all over the place, making anything more then starting the 4 terminal windows required for the WoW server a royal pita.  Sql editor is right out. 

Upgrading vmware tools is a no go, because it requires ubu 10.x or newer

That leaves me with upgrading the os itself. 
I made a copy of the VM folder, and set about the usual stuff found on google, like changing the repositories, command line updating etc. 
So far i have got it to update packages, and suggest i have a newer version (12.04.5 LTS ) available. When i click upgrade, and authenticate, the updater window closes after downloading two files.
I tried apt-get dist-upgrade, got a nice error message after it downloaded 2 files, now unable to reproduce since it just says 0 upgraded, 0 installed, etc. 

Found a suggestion of upgrading via cd image, mounted ubu 9.10, 12.10, 14.10 via vmware an no matter if i boot them directly or just let them mount, upgrading is not an option. Only reinstall alongside.

So, how can i go about upgrading my ageing os a few versions to make it work better in vmware? 
Any tips would be greatly appreciated. Since i have several full backups, anything can be tried.

---

### Post by oldfred on 2020-02-09
Do not know vmware, but you need to upgrade to a current version of Ubuntu.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by svennils on 2020-02-09
Vmware is just like any other computer, except it runs virtualized. All i need is to upgrade the 9.04 jaunty to something more recent, like 14.04. Actually anything beyond 9.04 worked with mouse pointer integration as i tried booting mounted images in the same VM. 
So it just boils down to: how do i upgrade a 11 year old os?

---

### Post by TheFu on 2020-02-09
I think your plans are screwed.

ubu 9.10, 12.10, 14.10 have all been out of support over 5 yrs (well, 12.10 was a special case).

Lesson 1: If you want supported OSes for more than 9 months, always select an LTS release.  Those are {even year}.04 releases.  20.04 is coming up.  16.04 support ends in about a year, for example.  Then there will be paid support for that release for 5 more years, if you like. [https://itsfoss.com/ubuntu-18-04-ten-year-support/](https://itsfoss.com/ubuntu-18-04-ten-year-support/) explains the announcement.

VMware has different priorities than making old software work.  BTW, VMware produces 6 different virtual machine products, so you'll need to be much more specific to get any meaningful help.

Really, the best answer today is:
a) load up 18.04.x onto hardware, setup KVM, bridge-utils, ssh-server, fail2ban, libvirt and virt-manager on that machine.
b) Create VMs using 18.04 or 20.04 (when released) and re-do all the WoW work using modern versions.  Gaming is probably 100x easier on Ubuntu today than it was in 2009.  There  are lots of tools that make many game setups almost 1-click.  [https://lutris.net/games/world-of-warcraft/](https://lutris.net/games/world-of-warcraft/) is one of those "make gaming easier" tools.  Don't know if that applied to just client games or servers. Sorry.

---

### Post by QIII on 2020-02-09
Trying to upgrade from just one old EOL release to a newer release is, at best, a gamble.  It is more likely to end in a significant negative emotional event than in success.  In your case, upgrading through a succession of EOL releases is not even something to bother considering.

I suggest, as has already be suggested, that you upgrade your server to a recent LTS release and then a new LTS VM.  I'd also recommend KVM as your virtualization platform, as it is already part of the Linux kernel and is dead easy to use if you use Virtual Machine Manager.

Asking the community to help you with your proposed course of action would be asking them to help with something that will ultimately be a waste of time.  Please don't ask them to do that.

---

