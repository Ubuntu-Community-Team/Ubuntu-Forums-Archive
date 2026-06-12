---
title: "Live USB on ThinkPad X41 Tablet: Boot option suggestions?"
date: 2008-07-02
forum: Installation &amp; Upgrades
---

### Post by wingsrule on 2008-07-02
Hey all,

First post! :)

I'm thinking about switching from Win XP to Linux on my laptop. I've been using Fedora on my desktop (made that decision b/c of the number of servers/daemons I'm running and the peace of mind that comes with a working SELinux).

But on my laptop, I wanted to go for ease-of-use and also learn a new distro, so I decided to go with ubuntu 8.04.

I set up a Live USB from my Fedora machine (ext2 partition, bootable, extlinux as the bootloader), plugged the drive into my IBM ThinkPad X41, and booted from the drive.

I got to the boot: prompt fine but when I tried to boot with the default options ("live" + ENTER or just ENTER), I got thrown out to the initramfs screen. No errors, just the typical busyBox header.

From what I've gathered on these forums, the default options don't jive with something on my X41, but before I start all permutations of these:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

I figured maybe someone has had experience with my notebook (or some IBM/Lenovo X-class ThinkPad), and can suggest which options should work.

If you haven't used an IBM ThinkPad X41 but have a good method of figuring these things out non-randomly, please do share! Here's some technical info on the computer:

[http://www.thinkwiki.org/wiki/Category:X41](http://www.thinkwiki.org/wiki/Category:X41)

Thanks in advance for all your help, folks. This community is one of the key reasons I decided to go with ubuntu!

(I'm a somewhat experienced Linux user, but I kinda draw my current line at recompiling the kernel. Never had to do it, and am kind of scared of the idea. Just letting you know the relative technical level when/if you respond).

---

### Post by wingsrule on 2008-07-07
Hey all.

I figured this one out, so if you are having similar issues, this may help you out.

First off, the problem was not hardware-dependent. It didn't work on another computer, and the fix isn't in running the Live USB with various boot options.

Instead, IF you have root access to a Linux machine, follow this guide exactly to create the Live USB:

[http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/](http://www.ryancloke.com/ubuntu-804-hardy-heron-live-usb-how-to/)

If you don't have access to a Linux machine, perhaps using something like Citrix would work. Unetbootin didn't work for me.

---

