---
title: "network-manager 0.7 is coming"
date: 2009-01-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ShirishAg75 on 2009-01-12
Hi all, 
 This may be good (or not good) but a big change, network-manager 0.7 is coming. 

[https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002941.html](https://lists.ubuntu.com/archives/jaunty-changes/2009-January/002941.html)

> 
network-manager (0.7-0ubuntu1) jaunty; urgency=low

  * (merge) new upstream release NetworkManager 0.7 final
    - rev 3802 lp:~vcs-imports/network-manager/main/
    + fix LP: #288963 Network Manager fails to connect to a system stored
      network with "set_network_cb(): Couldn't set network config: Did not receive
      correct message.." in intrepid
    + fix LP: #288703 Routes lost on DHCP lease renewal (breaks VPN)

  * drop probe v250 modem patch; this should be done in udev-extras; until
    that happens we rely on accurate hal-info
    - delete debian/patches/add_probe_for_v250_modems.patch
    - update debian/patches/series
  * drop upstreamed patches
    - delete debian/patches/50_gcc43.patch
    - delete debian/patches/lp282207_set_apn_at_syntax.patch
    - delete debian/patches/lp268667_more_ppp_default_options.patch
    - delete debian/patches/lp278631-initscript-polishing.patch
    - update debian/patches/series
  * drop unused patch
    - delete debian/patches/41o_completely_deactivate_stage1.patch
  * make manual regristration timeout patch out of automatic one (which
    was applied upstream)
    - rename debian/patches/lp303142_more_time_for_automatic_registration.patch
      => debian/patches/lp303142_more_time_for_manual_registration.patch
  * add patch to fix ftbfs
    - add debian/patches/ftbfs_nm_netlink_monitor.patch
    - update debian/patches/series
  * [libnm-util-dev] dont try to install nm-setting-ip6-config.h - which is
    supposed to be hidden in 0.7 final
    - update debian/libnm-util-dev.install
  * prepatch upstream soname version bump for libnm-util
    - add debian/patches/04-ltversioning.patch
    - update debian/patches/series
    ship the libs in libnm-util1
    - update debian/control
    - rename debian/libnm-util0.install => debian/libnm-util1.install
    and bump so shlibs control file info for libnm-util1
    - update debian/rules
  * add easy bzr builddeb support with proper upstream-revision (--show-ids)
    - add .bzr-builddeb/default.conf
  * install plugin in ppp 2.4.4 and 2.4.5 directory
    - update debian/network-manager.install

Let's see how this one goes, this would be interesting. 
All related packages are also getting updated at the same time too.

Comments, suggesetions, experiences all welcome :)

---

### Post by secret_force on 2009-01-12
Huh???
Is NetworkManager 0.7 not in intrepid already?

---

### Post by JohnJackson on 2009-01-12
> **secret_force said:**
> Huh???
Is NetworkManager 0.7 not in intrepid already?

I believe Intrepid uses SVN snapshots, 0.7 final was released in November. Hopefully the final release fixes some connectivity problems I have sometimes when reconnecting to wireless networks.

---

### Post by Starks on 2009-01-12
i want 3g cdma over bluetooth support!

---

### Post by theDaveTheRave on 2009-01-12
It would be good if you could change network locations without requiring a root login to the network manager.

for instance.

I have a static IP for work, but at home I run on DHCP, as I do when I am "visiting" other places (airports, conferences etc).

It is a pain no to be able to switch easily from my "office" location to another without having to mess around using the root login. There also seems to be an issue with needing to bring down the interface first then changing the location then bringing the network back up, although this works inconsistently, and often I need to re-boot to sort out the change in network location.

I can of course have wireless on DHCP and Ethernet on static, I guess I just need 2 Ethernet ports and then switch between, but I don't know of any laptops that have 2 ethernet ports... unless you use the pci slot!

Anyway that is my pennies worth.

David

---

### Post by zekopeko on 2009-01-12
> **Starks said:**
> i want 3g cdma over bluetooth support!

probably in 0.7.1 or 0.7.5.

---

### Post by scaine on 2009-01-12
> **Starks said:**
> i want 3g cdma over bluetooth support!

You can do this now by installing Blueman, which replaces Bluez-utils and hooks into network manager 0.7 (intrepid) nicely.  This thread explains how :
[http://ubuntuforums.org/showthread.php?t=982074](http://ubuntuforums.org/showthread.php?t=982074)

EDIT -  whoops, I see you later posted on that very thread claiming that CDMA 3G doesn't work with Blueman.  I have no idea what you mean right enough, but sorry for the double post.  I've used Blueman/Network Manager with about 4 phones now flawlessly, a mixture of UK T-Mobile and UK Vodafone networks.

Perhaps if you go into more detail about what you mean by "CDMA 3G", I can help?  Specifically, what phone/network are you trying to use and what is the error that's preventing you from using Blueman/Network Manager in intrepid?

---

### Post by jfernyhough on 2009-01-12
Last time I tried blueman and pairing it with my Nokia 6120c over bluetooth it worked fine as a modem - and that was with Intrepid when it was in development with NM0.6. Though I think it used Gnome-PPP as well.

I'll have to try it with Jaunty and NM0.7. /runs off to test :D

---

### Post by ShirishAg75 on 2009-01-13
Any info./update on network-manager as have people updated to it and what has been its performance?

Curious about 0.7 final.

---

### Post by jpeddicord on 2009-01-13
I don't see what the fuss is all about, we've had 0.7 since Intrepid, it just wasn't final. I'm on Jaunty with latest NM and it's no different. The final release just clears up a few bugs that were in the checkouts.

---

### Post by ShirishAg75 on 2009-01-13
> **jacobmp92 said:**
> I don't see what the fuss is all about, we've had 0.7 since Intrepid, it just wasn't final. I'm on Jaunty with latest NM and it's no different. The final release just clears up a few bugs that were in the checkouts.

jacobmp92, 
 The problem is simply this, after update, if for some reason it doesn't work (any reason) then downgrading is not so easy. You have to remember exact version and the package should be in the archive (no autoclean).

I've been burned couple of times by updates of network-manageer hence asking for feedback is good.

---

### Post by oygle on 2009-01-13
Let's hope this release solves MANY bugs. I can't use ppp0 and eth0 concurrently with NM 0.7 (svn version), and there are connection problems,my syslogs are showing it falling over and disconnecting at times.

What I would like to see in NM is some stats, just like [UMTSmon]("http://umtsmon.sourceforge.net/") displays. Whenever there are connection problems (mobile broadband using a USB dongle) with my ISP, I cannot provide them with signal strength and connection type, etc.

---

### Post by ayates on 2009-01-13
> **ShirishAg75 said:**
> Any info./update on network-manager as have people updated to it and what has been its performance?

Curious about 0.7 final.

It will not let you edit or delete 'auto'  connections.

---

### Post by rykel on 2009-04-12
Hey all,

I want to report that I am using Blueman (from the ppa) with Jaunty... it can browse my Nokia 6121 Classic phone just fine... but getting Network Manager to detect the phone as a modem is No Go. sigh... I hope this gets sorted out soon!

---

### Post by jfernyhough on 2009-04-12
> **rykel said:**
> Hey all,

I want to report that I am using Blueman (from the ppa) with Jaunty... it can browse my Nokia 6121 Classic phone just fine... but getting Network Manager to detect the phone as a modem is No Go. sigh... I hope this gets sorted out soon!It will pick up my 6120c no problem over USB - I don't think using BT works properly yet with NM. You can still use the Blueman and GnomePPP combination to get it working over BT.

---

