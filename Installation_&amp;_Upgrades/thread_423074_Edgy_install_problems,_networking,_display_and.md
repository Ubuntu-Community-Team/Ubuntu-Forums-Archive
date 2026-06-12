---
title: "Edgy install problems, networking, display and ?"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by RonKZ on 2007-04-25
I have installed (sucessfully) several times, first Dapper Drake and now Edgy, in both PC and x64 versions.  Edgy is far my favorite, but every prior installation has "come apart", invariably trying to configure my little eth0 LAN.  Whenever it "comes apart" I wipe the partitions and reinstall, whether Edgy or any of several other major distros, but Edgy is far my favorite, so if I can manage a stable configured installation that should be all over.

I have rechecked all the hardware, all okay in XP.  Athlon64 3200+ on a Gigabyte GA-K8U MB, 512mb just kicked up to 1gb; Hitachi 160gb SATA (bah humbug but it works), Actiontec PCI serial dialup modem, all USB plugs are connected -- mb-rear, std front, plus card-reader.  <?Possible problem?> with linux & "Realtec RTL8139/810x Family Fast Ethernet NIC" but it's ok on XP.  Dual-boot with XPhome, which I intend to escape SAP.  Sheez! when I booted up just now after changing my videocard, it's reactivate again!  M$, the master spy.

So this last install (twice 2 days ago, again last nite) v.6.10 PC DVD, disc verified.  

Both times installation finished w/display at 800x600 and change-option only to 640x480.  This has never occurred in the past.  A fairly new Radeon 9250 was replaced with a Radeon 9600XT, but didn't fix the issue, the 9250 works in other boxes.

Both these last (now 3) installations, Networking comes up without Activate buttons for modem and ethernet.  Only dialup is available, I use only hardmodems which are known to work always, but with these installations I can't even dial the modem - seems to be no connection between Networking/Modem and wvdial.  When I say that Ubuntu "comes apart", invariably it's during trying to set up networking, which has been my nemisis for 22 years now.  I have a router/switch, want only a LAN, essentially peer-to-peer but using this box as Server of modem and files for other computers which I built or rebuilt for sale.

My password doesn't log me into root as in earlier installations, and (default pass?) ubuntu doesn't work either, so much commandline stuff is impossible.  Maybe(?) sudo works but definitely not su (don't remember for sure)

I am sure there are plenty more problems, but I really wasn't able to get further, or didn't bother.  Because this hasn't happened with earlier installations, I know it's gotta be something wrong with the installation.  I am not exactly a newbie anymore, altho I'm not very good with commandline stuff yet.  That's a matter of knowing all sorts of useful commands and apps, of which I know only a few. 
 
And last night reading a Madriva book, I noticed it uses /swap, /, and /boot partitions, that makes some sense but I have never gone that route.  Only the kernel installs to /boot, I guess.  Comments?

My one other setup question is...  I have all my data on a fat32 partition and want to continue working with and adding to that data in Ubuntu, in a direct and convenient fashion.  It seems SO frigging irritating that Ubuntu gives control of that (and my XP NTFS) partition) to Root, and I don't know how to wrest it away, and feel I shouldn't have to, but maybe future installers will be a little kinder in such regards.  

Some good advice would be so welcome!  I expect to reinstall anyway (rather than mess around trying to fix it) but hopefully next time it'll be right.

---

### Post by RonKZ on 2007-04-30
Well gee, no help out there?

One thing, still checking, but my ATI 9250 may have been partially fried.  The change to 9600 may make a difference, but frankly it's doubtful that would have been the entire cause.  Meanwhile I'm trying Mandriva 10.1 (Spring), but it's also messed up.  I don't remember if that was before or after I changed the vCard.  Will be checking that soon and report.  I can say that Mandriva installed beautifully on another box, a P4 on a cheapie Epox mb.

---

