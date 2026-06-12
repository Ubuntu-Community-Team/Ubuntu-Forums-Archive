---
title: "Problem installing xubuntu 10.04 on old computer"
date: 2010-08-21
forum: Installation &amp; Upgrades
---

### Post by jim1944 on 2010-08-21
I downloaded the live CD and ran it to make sure that it would run on my old computer. Then I tried to install it. It was a little weird. I selected the install option at the boot prompt but it brought up the live CD desktop. Since the live CD desktop has an install icon I pressed that and it walked me through the 7 steps and started the install. Since it was an old computer it was taking along time (although clearly making progress) so I left for a while.

When I came back there was just the live CD desktop showing so I assumed that the installation had completed and rebooted. 

Xubuntu did not appear in the grub menu. Grub was installed prior to installing Xubuntu and there was a /boot partition on the first disk. I installed Xubuntu onto my second disk (its / partition was in /dev/sdb2). I mounted /dev/sdb2 from the live CD and it appears most everything got installed but there is a /boot directory in the Xubuntu partition but /boot/grub is empty.

I'm thinking that I can boot the installed Xubuntu by simply editing /boot/grub/grub.conf on my original /boot partition but I don't know what to put into it.

Any help would be appreciated.

Thanks
Jim

---

### Post by mörgæs on 2010-08-22
Hi, welcome to the forum. 

I am not sure what the purpose is. Are you trying to install Xubuntu 10.04 next to another Ubuntu, or are you trying to wipe the drive completely and only have Xubuntu?

/boot/grub/grub.conf can not be edited under Grub2.

How much memory does the machine have?

---

### Post by jim1944 on 2010-08-22
I'm trying to install Xubuntu next to Windows 98 and Puppy. Windows 98 is on my first HD. Puppy occupies a small partition on my second HD. /boot is on my first HD. Originally I had Fedora on my second HD. When I installed Fedora I had it install /boot on the first HD and the rest on the second HD. But the second HD went bad and, by the time I replaced it, Fedora was up to F12 and I could not install it because with F12, Fedora no longer supports 586 CPUs. I installed Puppy and that installation found the existing /boot and updated grub.conf correctly so that I could boot it and still boot Windows 98. 

Fedora, at least through F13, still uses legacy Grub. I now realize that Ubuntu uses Grub2. Apparently my install of Xubunu did not result in the replacement of my existing legacy Grub, but again, I was not present when the install finished so I don't know if there were any messages that I might have missed (If there were any messages, they should have stayed around until I acknowledged them!). I don't even know for sure that the only thing wrong is the Grub issue.

I can still get to Windows 98 and Puppy through my legacy Grub. What I'd like to do is edit my grub.conf so that I can attempt to boot Xubunu. If I can do that and Xubuntu seems installed OK, then I'll think about switching to Grub2.

Thanks
Jim

---

### Post by mörgæs on 2010-08-22
Whoa, by my 1000th post I encountered a running Windows 98 for the first time in this forum. This is something...

Apart from the nostalgia I think you better wipe all drives in the machine. Support for 98 ended in 2006, so there have not been any bugfixes since then, meaning that it is very likely that your system is infected with something bad. 

I would let go of everything and only install Xubuntu, but if you want to experiment with Grub, this might help:

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

How much memory does the machine have?

---

### Post by jim1944 on 2010-08-25
I tried installing again with live CD and stayed with it to actually see what happened and it reported an error running dpkg and quit. so I down loaded alternate install CD and tried that and it worked so I've got Xubuntu successfully installed.

Oh, and I have an even older computer with Windows 95 on it. Now if I could only find that TI 99A...

Pardon my stupidity but how do I mark this thread as solved?

Thanks
Jim

---

### Post by mörgæs on 2010-08-26
It is in 'thread tools'.

If you want to experiment with the older machine, this might help:
[http://ubuntuforums.org/showpost.php?p=9758078&postcount=8](http://ubuntuforums.org/showpost.php?p=9758078&postcount=8) 

Lubuntu is as light as it gets in the Ubuntu family. 

Remember to have wired internet access while installing.


If you manage to get something running on the TI 99, by all means let us know. Would be cool to see Ubuntu in 16 colours :-)

---

