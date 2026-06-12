---
title: "I had a dualboot but Grub2 eated it - can I get a usb?"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by palgorithm on 2010-06-10
Hi everyone, 

I can see from the forum other people have also had trouble with the grub->grub2 transition. Suffice to say I had a dual boot at work with an essential windows 7 and non-essential linux install on it, and randomly upgrading the distro made windows7 unbootable. Cue a missed days work, much embarrassment and ear bashing from those who are convinced Linux is written entirely by communists and hippies :)

In the end I had to re-install windows, which cut off the ability to boot to ubuntu - although I've left the existing ubuntu partitions as they were.

Although I can get away with allocating a few partitions to ubuntu, I can't really justify fiddling with the MBR based upon this experience. I need a fast boot and persistent data for doing anything further with ubuntu at work, so I'm wondering whether a safer bet would be to setup a usb stick with enough grub to boot to the existing ubuntu install? Not a full usb distribution, just enough to boot into the existing install?

Anyone know roughly how this would be done or have any other suggestions? Is it really just a grub-install /dev/sdXX (where XX is the usb)?

Thanks,
Sam

---

### Post by darkod on 2010-06-10
1. The distro upgrade didn't make win7 unbootable, if you selected grub2 to be installed on all PARTITIONS, not just all DISKS, that would make win7 unbootable because grub2 would also install on the win7 partition.
And because of the limited way win7 can boot, having grub2 on the partitions will interfere.
For example, you can boot linux even if you make the mistake to install grub2 onto the partition.

If you read about so many people having this problem you probably noticed a link to a testdisk procedure which removed grub2 from the windows partition. In most cases no reinstall was necessary, only a 2min fix procedure.

2. Using grub2 from the MBR is not "fiddling". In fact, what you are trying to do now is much more complicated and can get you into trouble with your lack of linux experience. I'm not a linux expert myself, I'm telling you this with best of intentions. I know you're spooked now, but using grub2 as main bootloader from the MBR is THE way!

You already noticed windows bootloader can't see and boot your existing ubuntu. If it could, I have nothing against it.

Having said all this, you should be able to boot grub2 from usb stick. I know you can from usb hdd, never tried with stick.

Plug the stick, boot with the ubuntu cd in live mode, and to see your disks and partitions run:

sudo fdisk -l (small L)

Post the output for exact commands, if I write them blindly I might confuse and mess up. We don't want that right? :)

---

### Post by oldfred on 2010-06-10
I have a USB flash drive set up to boot a bunch of ISO just to have another way to boot Ubuntu and I now use it for installs as it is real quick just to copy the ISO to the stick and modify grub.

I added an entry for my new Lucid install just to see if it would work. And it did but not with the drive number I expected.

This worked on my system.
Boot most up2date Lucid kernel on sdc7
menuentry "Lucid on sdc7" {
    set root=(hd1,7)
        linux /vmlinuz root=/dev/sdc7 ro quiet splash
        initrd /initrd.img
}

Note that the hd is (hd1,7). I have three drives and the USB then becomes the fourth drive.
I normally boot Karmic on sdc and had to use (hd1) to chainboot to sda's MBR to boot lucid's grub in sda.
I expected that the USB then would be hd0 as it was the boot drive. But that did not work. Using the edit function in the grub2 menu I was able to test alternatives until it worked. I actually tried hd3 (since it is sdc), hd0, but do not know how grub sees my sdc as hd1???

I used this to create my USB. But it is a full bash script and I only selected a few commands and ran those.

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntuforums.org/showthread.php?t=1498903&highlight=usb](http://ubuntuforums.org/showthread.php?t=1498903&highlight=usb)

---

### Post by palgorithm on 2010-06-14
@darkod Thanks, but unfortunately I didn't find these posts until I'd already lost a days work and re-installed windows. 

The behaviour I'd expect of the upgrade process is that is preserves the existing grub setup (which was unmodified from the initial install) and "Just Works". It's definitely a problem if it gives me the option to obliterate my hardrive :). I always feel bad having to criticise the good efforts of open source work, particularly on Ubuntu which I'm very fond of. But I think I will avoid installing grub/grub2 again on this PC - at least until development on grub2 settles down a bit. 

@oldfred Thanks for the links. I'm fairly sure I can see how to do it now. I'll have a play around on a non-critical PC first :)

Thanks guys!

---

### Post by darkod on 2010-06-14
> **palgorithm said:**
> 
The behaviour I'd expect of the upgrade process is that is preserves the existing grub setup (which was unmodified from the initial install) and "Just Works". It's definitely a problem if it gives me the option to obliterate my hardrive :). I always feel bad having to criticise the good efforts of open source work, particularly on Ubuntu which I'm very fond of. But I think I will avoid installing grub/grub2 again on this PC - at least until development on grub2 settles down a bit. 


The bootloader has to work in different environments so it's not always easy to make it "just work" and cover all possible type of installs.

Now that you know what the mistake was, it's definitely too harsh to claim you will avoid installing it again. You are of course free to do as you like, but the only "error" of the developers was that they offered you a total choice, including installing grub2 to all partitions you select. What you did with that choice can't be their fault. If there was no choice, people would complain why choice was taken from them.

Again, you can do as you want, but what you are saying here makes no sense and can mislead other users new to ubuntu. Usually they already feel nervous enough trying a new bootloader without dramatic statements like yours.

I'm fairly new user of ubuntu too, started with Karmic, and I have used grub2 with Karmic and now Lucid without even a glitch.

---

