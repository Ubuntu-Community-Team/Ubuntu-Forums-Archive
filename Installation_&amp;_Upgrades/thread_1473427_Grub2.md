---
title: "Grub2"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by swudee on 2010-05-05
A long story,
but basicly when I was upgrading 9.10 to 10.04, I had an after hours call from one of our clients (work) which meant I had to switch over to the windows computer with the KVM switch in the middle of it, in order to log into their Linux server, yeah some damn fool made the web interface ie only!!! When I switched back I had no mouse or keyboard function. This was OK until it stopped for some input for configuring grub. Even plugging in a usb mouse had no effect, so I had no option but to hold the power switch in until it shut down. Of course there was no boot partition. So I found the instructions to chroot and install grub, however this came back with an error. I rebooted and this time had a grub prompt, well it's progress.
I was able to boot with instructions from here.
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
I then tried to reinstall grub, this came back with an empty config line I was supposed to confirm, and when I continued came back with an error 128.
I found a post in the dev forums and added a few lines to a file, /etc/default/grub if I remember rightly.

Refound the page here

[http://www.archivum.info/linux.debian.bugs.dist/2009-09/09255/Bug-547649:-grub-pc-postinst-exit-status-128.html](http://www.archivum.info/linux.debian.bugs.dist/2009-09/09255/Bug-547649:-grub-pc-postinst-exit-status-128.html)

Now it comes back with an error 2

When I go through the boot procedure, 

set root=hd0,1
insmod /boot/grub/linux.mod    

 This line comes back,  the symbol 'grub-getxy' not found

If I continue, 

linux /vmlinuz root=/dev/sda1 ro 
initrd /initrd.img
boot

It boots up

I can make it boot. I think I am getting close.
Has anyone got any ideas how to fix this?

Thanks

---

