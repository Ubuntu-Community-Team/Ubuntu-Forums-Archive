---
title: "Mega-weirdness and partial failure upgrading to 11.10 (Oneiric)"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by spamless on 2011-10-16
I intended to keep this short, but with so many baffling things happening I did not succeed. Please bear with me.

GF's machine (which I adminsiter) is an AMD Sempron(tm) 2400+. No proprietary graphics or drivers in use. Background: I started long ago with Lucid. Last month I upgraded it in stages to Maverick and then Natty. Mostly trouble-free upgrades, though I had lots of trouble getting the Plymouth splash to work. (It all works now.)

The onboard graphics card is nothing special, so only the basic graphics capabilities ever would work. So when I got to Natty, the new Gnome look didn't work and it reverted to the classic layout.

From another machine I downloaded the Torrent "alternative" Oneiric ISO for i386. Put it on a USB stick. It would not boot this system. The menu came up, but the efforts to select Oneiric to try or to install did not work. So I burned a CD from the ISO. It would not boot this system. It gave an error message that I was trying to load a 64-bit kernel. Well, gee, I was sure I'd burned the i386 image to the CD (though I also had downloaded the x64 ISO for my own machine). But I decided I must have burned the wrong image, so I burned a second CD. Same thing!

So now I was pretty annoyed and I started the standard update to 11.10 from the Natty Update Manager.  Three hours later, it seemed to have worked (I did see dozens of ssh-cert errors flash across the screen, but didn't get too worried at those). Update Manager proclaimed success at the end, so I rebooted.

Grub2 failed! I have several other bootable partitions on this machine, by the way. I knew I would eventually get something booted, but this failure was a huge surprise. I was at the grub-rescue> prompt, but no commands I could think of to try produced anything useful.

I found an old grub-boot rescue CD I'd burned 1.5 years ago and ran it. (It runs old grub, but that's just a side-note.) Many of the things I tried from the boot menu didn't work, but eventually I got into an Oneiric rescue shell. I ran update-grub and grub-install and tried again, but grub (new) still would not load.

I re-loaded the grub-boot CD and eventually got into another bootable Linux partition and installed grub. That worked, and now I found out the next crazy oddity.

Now I had a normal grub2 menu, but Oneiric would not boot. It said "missing license" or something! On further inspection, the 3.0.0-12 kernel was nowhere to be found, although I thought I had watched the Oneiric update put it on the hard drive. Just completely gone! MIA.

So I booted to the previous kernel, i.e., Natty, and everything looked entirely normal -- except the message about Oneiric's having been released and don't I want to upgrade immediately? came up. WTF?

So anyway, I re-ran update-grub and so on. Everything seemed fine, so I rebooted. Grub still worked (whew!), but the Oneiric kernel was definitely MIA.

So now I went back to my other computer and burned one more i386-alternate CD from my ISO. I put it in this (GF's) machine, but it would not boot. It didn't give the old error message about a 64-bit kernel, though. But I could not make it boot.

So I rebooted to grub again, went to the previous version (Natty) from the menu again, started the boot, and walked away from the computer. Well, when I came back, I was looking at the Oneiric login screen! My jaw actually dropped.

I logged in to Oneiric, opened a terminal, and ran uname -a. It was running the Natty kernel. But it said it was Oneiric. It looked like Oneiric (I have it on two other machines). Another thing: the Dash stuff worked. Remember how I said Natty wouldn't load the new GUI and reverted to Classic? But Oneiric loaded Dash fine with this cheap old onboard graphics card.

Okay, I looked in /boot and saw there really was no 3.0.0-12 kernel to be seen. I opened Synaptic and installed the "pae" set, since it was recommending itself in the description text. I re-ran update-grub and it listed the 3.0 kernel and also the 3.0-pae kernel.

Now I took out the CD and rebooted. Can you guess what? It said the 3.0 kernels weren't found. I went back to the "previous version" again, but this time Natty booted. Natty, with the old, classic user interface. Oneiric was not to be found. The kernels I had installed were there in /boot, though.

So I put the Oneiric CD back in and rebooted. (Again, the CD won't load directly.) At the grub menu I still could not get into Oneiric with the 3.0 kernel: neither 3.0.0-12 nor 3.0.0.12-pae. Again I went to "previous version" (i.e., Natty), but now the Oneiric CD was in the bay again. It booted to Oneiric again, but still with the 2.6.38-11-generic kernel from Natty.

And that's where I'm typing this from. Everything works, but if I take the CD out of the bay and reboot I'll be back in Natty again, not Oneiric. (And the grub menu items pointing to Oneiric won't work, and GF will be flummoxed.)

Help?

---

### Post by spamless on 2011-10-16
Heh. I know what happened now. And I fixed it.

Are you curious?

Before I began the upgrade, I saved a copy of the active Natty partition to a free area on the drive (using gparted), as a safe backup in case things did not go well. I neglected to change the UUID. The two identical UUIDs confuse grub and various other things, such as gparted. (When it's run subsequently, it locks the same-UUID partitions that are not mounted and calls them mounted.)

The upgrade routine apparently failed for this reason also, leaving the new kernel in Bit Heaven instead of copying it. In any case, even after I manually put a kernel there grub reported the kernel as missing, because it was looking on /dev/sda9 instead of /dev/sda5.

Somehow leaving a CD in the drive changed the constellation enough to let grub see the now-existing kernel in /dev/sda5 when I tried to boot /dev/sda5, but then it read (I surmise) boot files from /dev/sda9 anyway and so booted /dev/sda5 to the old kernel.

Naturally, I should have changed the UUID after cloning a partition. But it is a stupid and exasperating security flaw in Ubuntu that it can't handle two completely different bootable partitions correctly just because the user left two UUIDs the same.

Maverick and Natty both handled this situation with no problem. Lucid, or was it Karmic before it, did have a problem. So it got fixed two or three releases ago, only to get unfixed again now. (But gparted has been broken all along as to this.)

Another thing: if you use tune2fs to change the UUID on a different partition than the one currently active and booted, and you update grub, part of the grub menu statements for booting that domain will have the right, new UUID and part of them will have the old UUID still. (Yes, it's so even if you did remember to edit /etc/fstab first, too. I did.) So the partition you changed the UUID of still won't boot right without editing grub manually. Once you manage to get into that partition (by hand-editing the grub entry before executing the line), you can run grub-update again and fix that.

Then you still have to boot into the first (new) partition again and update grub one more time. Now the menu entries will be consistent and correct with regard to the fixed UUIDs.

---

