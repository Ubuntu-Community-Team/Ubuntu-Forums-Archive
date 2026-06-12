---
title: "Ubuntu Server install freezes on IBM x3850 8864"
date: 2012-01-26
forum: Installation &amp; Upgrades
---

### Post by Kyc on 2012-01-26
Hi All,

I'm trying to install Ubuntu Server 11.10 on my IBM x3850 server but I am experiencing freezing issues.

I've attempted to boot the system with kernel option "acpi=off"; it worked and I don't experience any freezing but automatic module loading doesn't work.

When booting with no boot options all appears fine for a few moments then the system eventually freezes.  By pressing escape at the Language screen, after booting, I've gone to the terminal option and done a "tail -f /var/log/syslog" but no errors are presented before or after the system freezes.

I though it might be a firmware/bios issue, so I loaded up a Gentoo boot disk, was able to finish the gentoo build and flashed my bios, raid array and sas drives with no crashing/freezing issues.

I attempted to load the Ubuntu 11.10 server disk again and still experienced the freezing mentioned above.

The is a 4 socket with Intel Xeon 7150N (16 logical processors) and 16GB of ram.  I have two of them, both experiencing the same issue.

---

### Post by MAFoElffen on 2012-01-27
> **Kyc said:**
> Hi All,

I'm trying to install Ubuntu Server 11.10 on my IBM x3850 server but I am experiencing freezing issues.

I've attempted to boot the system with kernel option "acpi=off"; it worked and I don't experience any freezing but automatic module loading doesn't work.

When booting with no boot options all appears fine for a few moments then the system eventually freezes.  By pressing escape at the Language screen, after booting, I've gone to the terminal option and done a "tail -f /var/log/syslog" but no errors are presented before or after the system freezes.

I though it might be a firmware/bios issue, so I loaded up a Gentoo boot disk, was able to finish the gentoo build and flashed my bios, raid array and sas drives with no crashing/freezing issues.

I attempted to load the Ubuntu 11.10 server disk again and still experienced the freezing mentioned above.

The is a 4 socket with Intel Xeon 7150N (16 logical processors) and 16GB of ram.  I have two of them, both experiencing the same issue.
Okay, so yours has an LSI 1078 SA as a disk controller or an Adaptec AIC9410 SAS? Just looking at the variants on that server. Thinking it's probably the previous.  

Usually if it needs firmware, such as for something nonfree, it pops up dialog box saying that, giving you a chance to load that. Again--> Usually.

What drives are you using? Are you doing RAID? Where does it freeze?

---

### Post by Kyc on 2012-01-27
Thanks for the reply MAFoElffen,

During the 11.10 install it freezes on any screen, usually after a few moments.  For example if I rush and try to process the install screens as fast as possible I can get to the network configuration.  

If I just let the system boot and leave the system alone for a few minutes it will eventually freeze at the language selection screen (during the install, does not freeze in grub).

During the install I am not prompted to provide a firmware, and my NICs and raid array seem to be working fine - until the freeze.  The raid card is a ServeRAID 8i, but I don't know the controller chip off hand and I won't be back at the server for another hour.

Again, thanks for the reply.

---

### Post by Kyc on 2012-01-27
lspci provides the following details for the raid card:
Adaptec AAC-RAID (rev 02)


I've tried to do a 10.04 LTS install and it lasts longer before a freeze, but it still freezes up and at different points in the install (same as 11.10).

---

### Post by MAFoElffen on 2012-01-28
> **Kyc said:**
> lspci provides the following details for the raid card:
Adaptec AAC-RAID (rev 02)


I've tried to do a 10.04 LTS install and it lasts longer before a freeze, but it still freezes up and at different points in the install (same as 11.10).
Here's where I think I need to throw in a disclaimer- Even though I've done almost a thousand installs of Ubuntu Desktop and hundreds of installs of Ubuntu Server; for customers, my own and my own test boxes on Dev Versions...

Of my 6 servers here (all with respective server boards), 5 are running Ubuntu Server without problems... One is challenged and acts similar to yours.  It is an HP TC2120 (rebranded ASUS NRL-LS mobo).  I thought my Intel Server Board was finicky- No match on that one.

On install, it will fail at different steps/didn't think it was consistent, nor any pattern.  After 50 installs in one week, on this same box, I did notice some things... First, that it had Broadcom NetXtreme gigabit onboard eth ports that need non-free firmware, that it wasn't being asked for. Second, If I hard-set the vesa video mode at the start of the install, the prompt for that the non-free firmware then started coming up.

Next, even though the prompt came up asking for where the linux-nonfree-firmware and it said it found it and continued on- It then (if it got passed loading the base system) it had apt or other errors.

Sometimes it would crash during the initial bootstrap handler and base system load.... Other times during The package processing using bzip...

I tried Server versions 12.04 alpha, 11.10, 11.04, 10.10, 10.04, 9.10; thinking if it would just install, that I would do a release upgrade.  All had problems, until- I dropped an vanilla IBM NIC in it.  10.04 then installed without hickup nor complaint (I thought).

For me is that this is not the end of the adventure for me on that one.  It gets apt-cache corruption and will not upgrade to a newer version...  So, at least on that one, I'm going to file a launchpad bug-- [https://bugs.launchpad.net/ubuntu/+source/debootstrap/+bug/923594](https://bugs.launchpad.net/ubuntu/+source/debootstrap/+bug/923594)

But- 1. I know where you're coming from on yours. 2. Sometimes something simple can hold things back in the installer.  The hard part is too track down what that thing is.  Mine didn't show errors in the syslog either...

How I tracked things down in the installer was to- at the initial "Install Menu", press F6, press esc, then edit the boot line. I usually delete "quiet", change the "vga=791" switch to "vga=264" (Which is invalid/get to later), and add "--verbose". The invalid vga switch will bring up a text menu saying unrecognised mode, select one of these modes...

It will display all the boot and hardware probe messages. Next to know and do is that the installer displays in tty1 and the consoles display in tty4.  On a problematic install, I keep an eye on tty4 and look for problems there.  You can use <Shift><PageUp> and <Shift><PageDown> to scroll back and forth in the console to reread stuff that scrolled by too fast. One note- the display buffer is a set size. Anything (old) will be pushed from that buffer as the buffer is full and newer stuff is added. (Meaning you can only read so far back.)

---

