---
title: "Ubuntu 11.10 won't boot after install"
date: 2012-02-25
forum: Installation &amp; Upgrades
---

### Post by tylergard702 on 2012-02-25
Hello ubuntu formus,
I have just installed ubuntu 11.10 and upon first time boot there is only a black screen with a flashing text cursor, as if waiting for input. Also the USB I installed from is constantly being accessed (light on USB stick is constantly on)
All help is Appreciated
Thanks in advance

---

### Post by darkod on 2012-02-25
Does it run in live mode successfully?

---

### Post by MAFoElffen on 2012-02-25
> **tylergard702 said:**
> Hello ubuntu formus,
I have just installed ubuntu 11.10 and upon first time boot there is only a black screen with a flashing text cursor, as if waiting for input. Also the USB I installed from is constantly being accessed (light on USB stick is constantly on)
All help is Appreciated
Thanks in advance
??? You installed from USB to an HDD, right?  When it reboots after the install, it asks you to remove the media you installed from... So it can boot from the Install.

Otherwise, it's going to try to boot from the USB.

---

### Post by tylergard702 on 2012-02-25
Thank you for your replies :),
I presume by 'live mode' is when you 'try ubuntu without making changes to your computer', in which case yes; live mode works :).

And i tried booting with and without memory stick inserted, so unfortunately this is not the solution :(

Thank you anyway though :D

---

### Post by darkod on 2012-02-25
Sometimes grub2 fails to install correctly. Maybe it's not installed on the MBR, or both on the MBR and inside the installation.

It would show more info if you run the boot info script from the link in my signature and post the results as explained.

Since live mode runs fine, this usually excludes video driver issues, that's why I asked if it loads fine.

---

### Post by tylergard702 on 2012-02-27
Due to the large amount of text i have posted 'results.txt' as an attachment.
Sorry it took a while, had to get a live cd off a friend as my live USB stick was corrupted after install and scratches on my live CD prevented me from using live mode
Thanks for the help :)

---

### Post by darkod on 2012-02-27
As it says right at the top of the results, no bootloader installed. Don't know why though.

Not sure if it's installed OK inside ubuntu, it seems OK. The easiest thing to try is just adding it to the MBR. Boot in live mode again, in terminal try:

```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Restart and keep fingers crossed. :)

If that doesn't work, there is a more complex set of commands to run. Lets try the above first.

---

### Post by tylergard702 on 2012-02-27
It works :)
Thank you all for all your help, I am now one step closer to independence from Microsoft products. :)
Hopefully installation of Ubuntu on my desktop will be more successful, but i shall wait until July - September until I Reinstall that (I need it for work)

I thank you all again for your help and effort! :D
And thank you darkod for finding and providing the solution.

---

