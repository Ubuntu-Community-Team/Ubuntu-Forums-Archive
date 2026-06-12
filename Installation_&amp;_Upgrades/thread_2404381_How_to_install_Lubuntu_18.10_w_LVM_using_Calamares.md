---
title: "How to install Lubuntu 18.10 w/ LVM using Calamares installer?"
date: 2018-10-23
forum: Installation &amp; Upgrades
---

### Post by thatrandomguy+ on 2018-10-23
Hello,

I am working with one disk and I am simply trying to encrypt my Linux partitions. I do have non-Linux partitions on this disk for which I cannot remove for provisional reasons (not dual-boot).

I initially installed Lubuntu with distinct partitions for /, home, and swap. What I didn't realize at the time was that I would then only be able to encrypt my home and swap with *ecryptfs* (after the install).

I wanted to apply FDE as far as I could with Linux and after some Googling, I was led to LUKS. I remembered seeing that option during the install and so I researched what was needed and went ahead with the install again.

My process during **manual partition **creation via the installer was as such:

1) Created boot partition w/ appropriate mount point and flag(s)
2) Created LVM2 PV partition w/ encryption (including passphrase)
3) Attempted to create volume group where previously "created" PV was recognized but once OK was clicked, nothing happened.

That's as far as I could get and I'm not sure if it's simply because Calamares has a limitation or if I'm doing something wrong.

As I understand it, in order to achieve the LUKS partition with LVM, I need to a create a PV&#8212;which itself has a volume group&#8212;which then stores the distinct LV.

[IMG]https://i.imgur.com/G5JYbhm.png[/IMG][IMG]https://www.howtogeek.com/wp-content/uploads/2011/02/xbanner-1.png.pagespeed.gp+jp+jw+pj+ws+js+rj+rp+rw+ri+cp+md.ic.VGSxDeVS9P.png[/IMG]

_Forewarning_:
I have never worked with LVM and I used Ubuntu resources as well as other sources on github to verify what it is I wasn't getting.

_TL;DR_:
I am 90% sure that calamares simply won't do what I'm going for on its own and I might need to do stuff via terminal. I don't want to do that 'cause I'm lazy. Should it be the case that calamares can't do what I'm seeking to do, is anyone aware of a GUI tool that can?

Additional Info:
*PC is a Sony Vaio laptop
*Machine is running in UEFI mode
*Partition table is GUID
*Lubuntu 18.10 is currently installed on target PC with distinct partitions and only home, swap are encrypted via ecryptfs.

TIA

EDIT: **See post #5 for answer/result.**

---

### Post by Dennis N on 2018-10-23
Just a couple of comments:

Calamares can install to an LVM logical volume, but I always set up the LV before using the installer. You may have to bite the bullet and do it that way. Also I don't use encryption, so have no comment on that aspect. Sorry.

My own recent experience on installing Lubuntu 18.10 with Calamares: it would only install on my BIOS computer (this was done using an LVM setup). On my UEFI machine, the install failed. I ended up installing as a VM on that machine. 

Calamares can do UEFI - I have done it with other OS that use this installer, but something seems amiss with the current Lubuntu Calamares installer and UEFI.

---

### Post by thatrandomguy+ on 2018-10-23
@Dennis N
Thanks for the feedback!

Incidentally, the PC in question is a Sony VAIO laptop. I don't know how Sony works their BIOS nor if I can even switch it to legacy (<> UEFI).

I currently have Lubuntu installed with UEFI, it just isn't a LVM setup.

I wasn't aware that LVM and UEFI had a conflict within Calamares&#8212;so thank you for bringing that to my attention.

I will investigate some more and eventually provide my results here. Let's hope this thread doesn't close before then. :lol:

---

### Post by Dennis N on 2018-10-23
> I currently have Lubuntu installed with UEFI, it just isn't a LVM setup.

Well, that's interesting. I didn't try the UEFI install on a regular partition - just LVM. I may try UEFI without LVM since another disk in that UEFI computer has regular GPT partitions, and it could go there.

---

### Post by thatrandomguy+ on 2018-10-23
UPDATE:
It turns out that one does in fact need to setup a preliminary PV and VG before running the Calamares installer. This can be done via terminal or a GUI tool, KPVM. KPVM might just only work on this instance 'cause LXQt borrows from KDE.

Once the appropriate partition is created and the LVM is preliminarily setup, you can start the installer.

My mistake was not noticing that you had to change the disk view within the installer to get into the volume group. Objectively, having to manually select that from the drop down menu isn't nearly as intuitive as the installer automatically changing the view into the volume once it's been created. In the end, it wouldn't matter if once did create a volume group or not because the installer will not actually write those changes to the disk&#8212;hence why I said preliminary LVM setup is needed. Once that's out of the way, you can simply start creating the desired partitions on the volume and that's it.

[IMG]https://i.imgur.com/DKYaP3U.png[/IMG]

---

