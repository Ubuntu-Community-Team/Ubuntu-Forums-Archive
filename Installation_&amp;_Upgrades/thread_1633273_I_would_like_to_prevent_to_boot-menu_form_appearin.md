---
title: "I would like to prevent to boot-menu form appearing after update"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by Rinusch on 2010-11-29
Hello,

I'm using an unattended installation of Xubuntu. I think this question is general to Unbuntu, that's the reason of using 'Ubuntu' in this thread's name.

I have a system that's running unattended. I use it to log-on to remotely. It's running Xubuntu 10.04. Every now and then, I update my distribution by applying all security updates. Often, a new kernel is being applied then. When I give the system its required reboot after de update, it sometimes hangs in the Grub boot menu because it wants me to be able to select the kernel to boot.

Can I somehow prevent this from happening and just let the system boot the newly installed kernel? Now, I need to go to my basement, hook up a keyboard and monitor to the system and press <enter> to boot the highlighted kernel. It's very impractical so I really hope for a simple solution (or workaround)!

Kind regards,
Rinusch.

---

### Post by Rinusch on 2010-12-07
Kick..

---

### Post by Old_Grey_Wolf on 2010-12-07
Try installing the "Startup-Manager" from the Ubuntu Software Center. It may do what you want. You can select the default OS to boot. For me it always selects the latest Kernel I downloaded. You can also set the default timeout in seconds before it boots the Kernel so you can hit the Esc key to select a different Kernel.

---

### Post by drs305 on 2010-12-07
You could set up an /etc/grub.d/40_custom menu. For the "linux" and "initrd" lines of the menuentry, instead of listing a specific kernel you could write that portion as 
> linux /vmlinuz root=/dev/sd**XY** ro
initrd /initrd.img
These entries point to the kernel and initrd shortcuts in / and always use the latest kernel. If a kernel is updated, it would use the most current one.

Of course, you could also use a specific kernel in 40_custom - just copy a menuentry from grub.cfg and put it in 40_custom. Make 10_linux unexecutable and you would be set if you have put the kernel you want in t 40_custom.

If you never wanted Grub2 updated, which could also trigger a menu waiting for input, you could lock/pin grub-pc and grub-common so those files would not be updated unless you changed the settings.

It would be up to you to manually update the contents of 40_custom entries when you wish.

Added: Forum member *Cavsfan* wrote up a very nice guide on how to create a 'maintenance-free' menu which might give you some more ideas:
[http://ubuntuforums.org/showthread.php?t=1542338]("http://ubuntuforums.org/showthread.php?t=1542338&highlight=maintenance+free")

---

