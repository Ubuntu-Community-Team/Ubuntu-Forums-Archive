---
title: "daul booted ubuntu with vista"
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by gordie69 on 2012-04-02
I installed Ubuntu 12.04 on a hard drive and I unplugged the drive when I was finished I put Windows on my second drive and plugged them both in and I'm trying to get the boot menu so I can choose to go either Ubuntu or Windows what did do wrong.

---

### Post by 2F4U on 2012-04-02
And what exactly do you get now? As far as I understand is that now you have two hard drives each with its own boot loader, so neither system nows of the other. It might be worth to read a bit about dual booting:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by oldfred on 2012-04-02
When you installed Windows it is the first drive, it may not like being the second drive. Ubuntu does not usually care as it uses UUID not device like /dev/sda anymore. Newer versions of Windows are also more tolerant of drive change.

In Ubuntu run this:

sudo update-grub

That should find your Windows install, but it may need repairs if not still the first drive.

---

