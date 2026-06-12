---
title: "Ubunto Server 6.10 installs but does not boot - how do I debug/diagnose?"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by r-senior on 2007-05-02
Hi,

I've had an old headless box running RedHat 6.2 for several years and would like to upgrade.

In short, it's a Pentium II 120MHz with Award Modular Bios v4.51PG and a couple of Seagate IDE/ATA ST34321A 4GB drives, one of which is a replacement for a 425MB Samsung drive that still has RedHat on it. I can't remember the motherboard manufacturer and can't see a name on the board.

I've installed Ubuntu Server 6.10 with DNS and LAMP. No problems reported during install.

When it boots off the hard drive, I get a couple of GRUB messages, the press escape for boot options message, the screen clears and I briefly get "Starting up ..." before it reboots.

How can I diagnose the problem? I've tried pressing escape for boot options, removing "quiet splash" from the loading of the kernel, then press "b" to boot but still get the same behaviour.

I don't really want the risk of flashing the BIOS because I want to be able to put the RedHat drive back in as a fall-back option.

Any ideas?

Regards,

Richard

---

### Post by r-senior on 2007-05-02
I've been grubbing around with GRUB command line interface, so to speak, and I've discovered that typing root (hd0,0) returns no response. According to the page on GRUB I've just been reading, it should. I can use other GRUB commands to confirm that (hd0,0) contains a kernel image and the file structure I expect.

What does this mean? GRUB doesn't recognise my drive?

Richard

---

### Post by WiNET on 2007-05-02
I have a very similar problem with a server install i just did on an old Compaq Ipaq

motherboard intel 810e
PIII 733 proc
128 MB NEC Ram
10 gb seagate Hd (master)
LG cd/rw (slave)

I went thru the install everything went normally for me. Since this is my 3rd install of this kind i didn't expect any problems. Both were on older dell machines (older than this ipaq as well) and all worked fine. It seems impossible to diagnose beings you can't even boot. 

the difference i have than from the post above is that my machine doesn't reboot it just hangs at "starting up ..." for as long as i let it. I have tried different arrangements of the IDE configeration (no cdrom, cable select, etc) and nothing seems to make any difference. Only once that it actually passed this point but then it locked just before the bash prompt

HELP Please!

---

### Post by r-senior on 2007-05-02
OK, I've made some progress:

The issue seems to be with loading the kernel image. [This]("https://launchpad.net/ubuntu/+bug/48284") gave me a clue. It may be that the server install cannot detect that older processors don't support [PAE]("http://en.wikipedia.org/wiki/Physical_Address_Extension"), the PAE kernel is installed and won't boot. Can someone confirm this?

I have a working system of sorts, achieved as follows:

1. Booted from the install CD, selecting the recovery option
2. Followed the options through to get a shell against the root filesystem on my hard drive
3. Use apt-cdrom add to add the CD as a source of packages for apt-get
4. Run apt-get install linux-image-2.6.17-10-386 to install a basic 386 kernel image
5. Booted this image in recovery mode to watch progress, some fsck fixes required
6. Rebooted without recovery mode

So, I have a working system. It's getting late now - may investigate other kernel packages I could have installed tomorrow but at least it's booted.

Richard

---

### Post by ixus_123 on 2007-05-09
brilliant!

I was just having this problem.  I thought maybe my burns were corrupt as that has happened in the past.

I just apt-get'd the latest kernel 2.6.15-28

downloading now - I hope it works

---

### Post by ixus_123 on 2007-05-09
okay, that didn't work :(

I used the server version.

Just redone it as the poster above and it's worked fine. Got a log in prompt!  Hooray :)

---

