---
title: "Upgrade freezes on - Unpacking replacement linux-image-2.6.32-33-generic"
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by i 6Shot on 2011-08-11
Hello,

As the title says, when I try to upgrade it freezes at:

Unpacking replacement linux-image-2.6.32-33-generic ...

I'm at a loss as to why? I have tried many things to sort this with no success. I have tried updating via Ubuntu Tweak, Terminal as well as Update Manager. All stop at the same place. I have even left it on over night to see if that may help. 

I'm currently booting Windows 7, Kubuntu 10.04 and Ubuntu 10.04. The problem is with Ubuntu.

I should point out that over the last few weeks I have had problems with Ubuntu booting. On occasions it would just boot to a command line screen. I'm not sure what to do with it. Once it wouldn't even let me choose my OS to boot. If I get these problems it sorts it's self out in a few hours and then everything boots fine until I get the same problem again.

I don't know much about linux kernels but to me this seems to be where the problem is?

I have been searching the web for over a week now for a solution with no results. 

I have uploaded a picture (I hope it works) to help paint the image of my problems.

Thanks in advance for any help.

---

### Post by i 6Shot on 2011-08-12
No need to worry anymore (at least I don't think so).

I was impatient and decided to do a fresh install just over /. It seems to have sorted my problem. 
Still not sure what the problem was or what caused it. I guess it's another one of life's mysteries now.

---

### Post by Blasphemist on 2011-08-13
Here's my guess on the issue. When you install multiple distros or distro versions, you end up with one partition that has the controlling grub/grub2. Your list of boot options only gets updated when that distros grub-update is run. Kernel updates run grub-update but if that happened on the partition that isn't controlling grub/grub2 no new kernel entry is shown to you. So you reboot and think you are now running a new kernel and your not actually. If you watch an update that includes a kernel update closely you'll see the new kernel number and could notice the old kernel at boot but most people don't catch that. 

Solution, whenever you have an update that includes a kernel update you must run update-grub for the partition with the "controlling grub". Again, this happens automatically to the controlling grub partition but not the other(s). 

Or the much better solution, you use the 40_custom script and boot using symlinks that don't use a specific kernel number. This works for ubuntu based and some other distros but not all as follows.
```
menuentry "Natty main on sda5" {
set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 ro quiet splash
initrd /initrd.img
}
```
The above shows Natty main on sda5 as a boot menu choice on my grub2 and natty is on my first hard disk, partition sda5. You can learn more about this in grub2 documentation and symlink documentation.

---

### Post by NigO on 2011-09-09
> **i 6Shot said:**
> No need to worry anymore (at least I don't think so).

I was impatient and decided to do a fresh install just over /. It seems to have sorted my problem. 


I'm having the same problem, without the luxury of being able to reinstall... and not the only one from a quick google search.

As [http://blog.joegillotti.com/2011/08/18/fixing-a-dpkg-io-error/]("http://blog.joegillotti.com/2011/08/18/fixing-a-dpkg-io-error/") suggested, 
```
sudo killall dpkg
sudo killall synaptic
sudo rm /var/lib/dpkg/lock
sudo reboot
sudo apt-get clean
sudo dpkg --configure -a
sudo apt-get dist-upgrade
``` cleared out an apparent corrupted deb file, and reinstall worked.  I guess it was corrupted in the repo's, from the number of reports of this issue.

The killalls were because the underlying dpkg processes from initial install attempts using the update manager were still hanging around, and didn't remove the lock file when they were force killed.

I tried without reboot but couldn't get rid of the dpkg processes with any amount of killing, presumably as they were all in a disc wait state, so had to reboot to get a lock on the apt database

Nigel

---

### Post by i 6Shot on 2011-09-09
Hi NigO,

I followed this youtube video to re-install:

[http://www.youtube.com/watch?v=QGnsYuWS0xY&list=FLqlT-iNph1yFFD_CWhCPImw&index=3]("http://www.youtube.com/watch?v=QGnsYuWS0xY&list=FLqlT-iNph1yFFD_CWhCPImw&index=3")

By doing so I retained most if not all of my settings. The only things I had to re-install were some apps.

---

