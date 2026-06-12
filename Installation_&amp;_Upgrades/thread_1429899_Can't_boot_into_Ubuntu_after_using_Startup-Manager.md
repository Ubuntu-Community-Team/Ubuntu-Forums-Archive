---
title: "Can't boot into Ubuntu after using Startup-Manager!"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by tareksobh on 2010-03-14
I downloaded **StartUpManager** from the Synaptic Package Manager. I started the application and changed some parameters like Display Resolution to "800x600" and color depth to "24bits". All values were set to minimum before that. Later, Ubuntu wouldn't start after I restarted the system to see the changes!
How can I restore my boot setting to the original settings to be able to boot into Ubuntu?

**More info.**
After I choose "Ubuntu 9.10 kernel...generic" from the bootloader menu, I receive the following text

>    [Linux-bzImage, setup=0x3400, size=0x3b4660]
vga=789 is deprecated. Use set gfxpayload=800x600x24, 800x600 before linux command instead.
[Initrd, addr=0x171db000, size=0x78c329]
[   1.718926] kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,1)

I tried choosing different entries from the bootloader menu, but I still get the same error.

I'm typing this from Windows xp now, and it seems like it's downloading tons of updates (without even asking my permission!) Please help me, I can't look at Windows anymore!

If it matters, I used the Wubi installation method for installing Ubuntu.

---

### Post by Bullwinkle_Moose on 2010-03-15
StartUp Manager changes the file /etc/default/grub and in particular the following:

GRUB_CMDLINE_LINUX=" vga=769"

if you change that back to:

GRUB_CMDLINE_LINUX=""

and then run

sudo update-grub

It should get rid of the error message.  Don't know if that will fix your issue, though, and of course that assumes you can somehow at least boot to the command prompt.

They should either update StartUp Manager or stop offering it in the Ubuntu Software Center, IMHO. I see it's already been reported as a bug:

[https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/495436](https://bugs.launchpad.net/ubuntu/+source/startupmanager/+bug/495436)

See also [https://bugs.launchpad.net/startup-manager/+bug/483262](https://bugs.launchpad.net/startup-manager/+bug/483262)

---

### Post by tareksobh on 2010-03-15
Thank you very much Bullwinkle_Moose. I'll try and do that...
All I really want to do is to boot into Ubuntu, I think if I could, I might be able to run Startup-Manager and change it back to the way it was. If I couldn't, I think that I'll just have to reinstall Ubuntu. I won't be losing many files since I only was introduced to Ubuntu and installed it last Thursday (And I'm already playing with the system files!)

I reinstalled Ubuntu... Works perfectly now...
Thanks to Bullwinkle_Moose for the help :D

---

