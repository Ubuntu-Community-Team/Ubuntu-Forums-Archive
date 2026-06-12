---
title: "Remove package using live CD"
date: 2010-08-01
forum: Installation &amp; Upgrades
---

### Post by ChristophB on 2010-08-01
I installed ubuntu 10.4 on a lenovo T500 yesterday. Great!

Today I am almost sure to have a problem with the fglrx package.

Today I installed the graphics card accelleration driver - I think it is the fglrx, but I am not shure, because I used the gnome fancy gimmick offering this driver.
Now the computer starts neither in normal mode nor in recovery mode. In the latter it displays very fast about two screens of the usual lines and changes then something with the display. 
Trying to use boot=/bin/bash as an additional boot parameter didn't work either.
I even tried typing blind a login and something like
"apt-get remove fglrx <return><return>".

Booting from CD works.

Here my questions:

[LIST]
[*]When I have booted from CD, can I see the synaptic history to verify that it actually is the package named above?
[*]When I have booted from CD, can I remove packages from the installed version?
[/LIST]

---

### Post by oldfred on 2010-08-01
If you cannot boot into recovery mode, you can chroot into your system from the liveCd. Did you try editing the grub entry with nomodeset or other commands that may force it to use a different video driver?

At grub menu use e for edit and replace quiet splash with nomodeset.

ATI/Radeon
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

All drivers: nomodeset - this will disable the kernel modesetting feature and drop the user back to the old X.org infrastructure and behaviour. 

Lucid 10.04 KMS
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

If you have to chroot:
kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
Neat huh?
Added sudo cp /etc/resolv.conf /mnt/etc/resolv.conf

kansasnoob's change sda5 to correct partition
sudo mount /dev/sda5 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

# new for lucid & karmic 
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl

Then run whatever commands you need to run.

---

### Post by ChristophB on 2010-08-04
Great! nomodeset did the job. However I will keep the changeroot idea safe in my very valuble wisdoms folder. Thank you!
One further question: can I set the thead myself to "solved"?

---

