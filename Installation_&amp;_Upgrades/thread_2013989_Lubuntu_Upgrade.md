---
title: "Lubuntu Upgrade"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by suttonseven on 2012-07-01
Been using Lubuntu 10.10 on an ageing Dell laptop since February 2011 with no issues. Way better than it was with XP. Decided its time to upgrade to 12.04 but I have a problem. Reformatted disk to carry out a new install but when I start using the live CD it fails to get very far into the set up, after about a minute I get a blinking curser in the top LH corner and thats it. The ISO I downloaded is fine as far as the MD5 is concerned. I have also tried Xubuntu 12.04, exactly the same result and out of desperation 11.10 with exactly the same again. Even tried Mint 12 with the Lubuntu type desktop, same again.

Stuck in the old Lubuntu 10.10 disk I used originally, came free with Linux magazine and all is OK.

Any ideas, I guess its a hardware or driver issue that the old version copes with and the newer versions fail on but is there a way to fix it. If not I will carry on using 10.10, its not the end of the world.

---

### Post by ajgreeny on 2012-07-01
When you boot the live CD try using each of the boot options one at a time by pressing F6 and starting with **nomodeset**.  If that does not help go through the other options and you may get a chance to get further and reach the desktop.

If so you will then need to edit the **/etc/default/grub** file of the new installation which you can do from the live CD system before you reboot, by adding the option that worked to the line ```
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet **your-option**"
```

If that does not work I am afraid I don't know where else to go for ideas, but let's go one step at a time.

---

### Post by suttonseven on 2012-07-03
Thanks for your reply. Tried "nomodeset" as suggested, no help. Tried the other F6 options, all the same except for "acpi=off" which allowed the laptop to carry on booting into live mode. Did a Google and discovered that using acpi=off can be a bad thing for temps etc and a suggestion for "acpi=osi=", tried it, computer no worky. Used "acpi=off" again but the processor temps went over 60 just idling and when I tried using Chromium or AbiWord it was very clunky. OK, its in live mode but it did not appear right. Processor was also spiking whilst it was idling but the mem usage was OK.
 
Booted up on my old 10.10 DVD, selected Lubuntu, loaded with no issues. Chromium fine, AbiWord fine, not at all clunky. Processor temp was 52 degrees iding, no spiking but mem usage was about 10mb higher.
 
Looks like I will be putting 10.10 back on unless someone has a better suggestion.

---

### Post by dino99 on 2012-07-03
you should use the latest kernel which have solved lot of issues about acpi. Add this ppa and update, then install linux-lts-quantal

[https://launchpad.net/~ubuntu-x-swat/+archive/q-lts-backport](https://launchpad.net/~ubuntu-x-swat/+archive/q-lts-backport)

[https://launchpad.net/~ubuntu-x-swat/+archive/q-lts-backport/+packages](https://launchpad.net/~ubuntu-x-swat/+archive/q-lts-backport/+packages)

---

### Post by suttonseven on 2012-07-04
Sorry but you have completely lost me now.

---

### Post by msammels on 2012-07-04
Sorry about the above spammer Sutton,

Have you tried downloading an ISO of Lubuntu and installing it in the traditional way, or are you set on upgrading?

---

### Post by Elfy on 2012-07-04
> **suttonseven said:**
> So I post a serious question about Lubuntu and the b'stard ereowuosmith SPAMS  a reply about fekin holiday deals.


There is a Report Abuse button by the side of posts - use it and we will see it and do something about it ;)

---

### Post by msammels on 2012-07-04
> **Elfy said:**
> There is a Report Abuse button by the side of posts - use it and we will see it and do something about it ;)

Aww, now I can't report it again :( :P

---

### Post by suttonseven on 2012-07-04
Lubuntu 10.10 is off the machine. Iso of 12.04 burned to CD but unless I use the "acpi=off" option I cannot get the machine to run off the CD. This is not unique to Lubuntu 12.04, Xubuntu 12.04 is exactly the same as is Mint 12 and Bodhi 1.4.0 (and thats based on Ubuntu 10.04!!!!). All the disks work perfectly in live mode on a newer laptop. Original Linux magazine Lubuntu 10.10 CD will work fine.
 
Puppy 5.2.8 works perfectly except the wireless will not find my hub, finds next doors perfectly but I don't know their password.
 
Might try Crunchbang, heard good things about its resource usage but have heard it can be a sod to set up.
 
Could the Linux magazine CD have a different set up to avoid any issues with ACPI, just a thought?

---

### Post by msammels on 2012-07-04
I don't think it will. Are you able to test USB booting at all?

---

### Post by suttonseven on 2012-07-05
Only have USB 1.1 on this old laptop thus booting is a waste of effort.

Did some more testing last evening, does this make any sense to anyone. Printed off some more ACPI info from Ubuntu.com. As I said previously acpi=off allows the laptop to boot from the CD but tried acpi=oldboot, according to the info this allows the ACPI components for the boot process to be used disabling the remainder, guess what, did not boot. Does this mean (as it appears to me) that the ACPI boot component is the problem, if so is there a command to simply disable this and test the theory.

The good news appears to be even with acpi=off the temperatures stabilised a little when I allowed the laptop to stay on a while plus the fans appeared to operate normally, bit more relaxed about possibly trying the ACPI off more permanently if necessary.

Now this is an interesting one. I burned a new copy of Lubuntu 10.10 from a downloaded iso file and burned it to a CD. The Linux mag Lubuntu disc works with no boot up problems but the one based on the new iso download has exactly the same issues as the 12.04 CD. As I suggested earlier there must be something different with the Linux mag CD to make it more compatible with all hardware.

Finally did a DELL diagnostic of the laptop which it passed with no issues, not bad for a 10 year old with the original battery. Wonder if I should try a BIOS update if there is one available.

---

