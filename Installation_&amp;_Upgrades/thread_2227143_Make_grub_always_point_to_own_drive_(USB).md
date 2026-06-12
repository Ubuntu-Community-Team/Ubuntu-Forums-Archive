---
title: "Make grub always point to own drive (USB)"
date: 2014-05-30
forum: Installation &amp; Upgrades
---

### Post by thegoonden on 2014-05-30
I've got a perfectly good installation running from a USB flash drive. I just installed it to that drive as if it was a hard disc, and it works just fine.
It also works just fine on other machines.......BUT ONLY if they have a single internal hard disc like the machine that was used for the installation.
The problem being, that on a machine that has, say two, internal discs........the USB becomes /dev/sdc instead of /dev/sdb, and grub never  even loads properly.

What do I do so that grub always finds itself (or the part of itself that lives on / at any rate) in the same way that a live CD/USB grub does?

If I replace any instance of /dev style naming with UUID style in grub.conf (and update) will that do the trick? Can UUID naming work in all parts of a grub.conf?
(I want to ask first, before hosing the thing LOL).

---

### Post by oldfred on 2014-05-30
UUID should be the default in grub & fstab. 

I often add my own entries to grub in 40_custom.

 menuentry "Boot from USB Drive" {
    set root=UUID=XXXX-YYYY
    linux /vmlinuz root=UUID=XXXX-YYYY ro quiet splash
    initrd /initrd.img
}

You can also manually edit grub on those machines. The search line by UUID is supposed to override a set root command. But in grub menu you can edit the device or hdX,Y entry if it is not correct.

I have somewhat same issue as I skipped a port and my flash if plugged in is sde, but if rebooted when plugged in it is sdb and all the rest change by one letter. And I then may have to edit hdX,Y depending on what I am booting. But all entries by UUID still work. My default boot is sdd and it works whether flash is in when I boot or not.

---

### Post by thegoonden on 2014-05-31
Thanks.
I've been fiddling with it more.
I'm less inclined to blame grub.
I think it's my hardware on the other test machine.

Check THIS out for odd..........
Plug USB in, and set bios to boot from it.
Black screen.
(this is as far as previous attempts got me)
Rip USB out of socket in disgust.
Error message appears from grub "attempt to read or write outside HD0"
plug USB back in and do ctrl-alt-del
Receive grub menu in all its glory.

Bizarre or what.........and it's repeatable.........I seem to have to force the error before it will work.

It still doesn't actually BOOT............but the machine in question is mad as a badger and resists booting linux live distros with all its might (AMD64 with a certain NVidia chipset that does "something" to crash 95% of live CD/USBs tried on it).

But the grub menu works, without error, after that rather bizarre procedure.


I don't know if I should delete the thread or mark it as solved now, as grub isn't ACTUALLY broken.

---

### Post by oldfred on 2014-05-31
I have nVidia and have to use nomodeset on all boots of flash drive or first boot after install. My full installs on a flash drive I do not install the nVidia driver so I can use flash drive on my laptop which is Intel, but then I need nomodeset on desktop.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Other videos systems may need different parameters.
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by thegoonden on 2014-06-01
Thanks I'll have a poke about with those options and see what happens.
I should probably test on a couple of other systems too.

---

