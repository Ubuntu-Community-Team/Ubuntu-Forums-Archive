---
title: "After upgrade to Ubuntu 18.04, computer refuses to shut down"
date: 2018-05-08
forum: Installation &amp; Upgrades
---

### Post by marciomj on 2018-05-08
Hi, all.

So, I have a test computer (an old [but gold] Dell Latitude E6500) that I use as an Ubunt test bench.

Last year, I've made a clean install of Ubuntu 16.04 in it, and since them, I'm only upgrading the OS, without any hassles.

But after upgrade to Bionic, computer refuses to shut down. I need to keep power button pressed during four seconds to switch off the machine.

I've tried lots of methods to shutdown the computer, via terminal, keyboard shortcuts and so on.

Also tested it with the three different sessions (Ubuntu, Ubuntu Wayland and Unity), with no success.

Any hint?

P.S.: After the upgrade, I've cleaned all the old/unused packages and kernels.

---

### Post by dino99 on 2018-05-08
Only use a gnome on xorg session: wayland is not yet ready to be used everywhere, and unity is abandoned .
To get a visual booting/shutting down log: remove 'quiet splash' from /etc/default/grub, then run 'sudo update-grub' 
Also clean the system via 'gtkorphan' & 'bleachbit' (as root, select options carefully), then reboot.
Finally, glance at 'journalctl -b' for the booting processes, 'journalctl' will let you see the shutdown process

---

### Post by mörgæs on 2018-05-08
For an E6500 I suggest a fresh install of X/Lubuntu 18.04.

---

### Post by marciomj on 2018-05-09
> **dino99 said:**
> Only use a gnome on xorg session: wayland is not yet ready to be used everywhere, and unity is abandoned .
To get a visual booting/shutting down log: remove 'quiet splash' from /etc/default/grub, then run 'sudo update-grub' 
Also clean the system via 'gtkorphan' & 'bleachbit' (as root, select options carefully), then reboot.
Finally, glance at 'journalctl -b' for the booting processes, 'journalctl' will let you see the shutdown process

Hello, dino99.

Unfortunately, nothing worked. I've cleaned the system, updated it with few packages available, but problem persists.

The last three messages in shutdown splash are:

Reached target Unmount All Filesystems.
Reached target Final Step
Starting Power-Off...

And then computer stuck in this screeen.

But, I think I stumbled in a workaround.

If I logoff first, and after shutdown, most of times computer really power off.

I will investigate more.

Thanks for the tips!

---

### Post by marciomj on 2018-05-09
> **mörgæs said:**
> For an E6500 I suggest a fresh install of X/Lubuntu 18.04.

Thanks for the suggestion, mörgæs.

I was really considering switch this machine from Ubuntu to Xubuntu. I will try it in a VM first, but Xubuntu is nice to my eyes. :D

P.S.: But now occurred me that I can install xubuntu-desktop package over this system. I will try it!

---

### Post by mörgæs on 2018-05-11
> **marciomj said:**
> But now occurred me that I can install xubuntu-desktop package over this system. I will try it!

Good, please mark the thread solved if it works.

---

### Post by marciomj on 2018-06-06
So, Xubuntu install (only the xubuntu-desktop package, not a clean install), didn't worked.

Since I have strong doubts this hardware will last until 2021, I've decided roll back to Ubuntu 16.04. Made a clean install maintaining my original home partition and now everything is working fine.

I will try a Xubuntu clean install in a near future.

---

### Post by mörgæs on 2018-06-09
If you keep the /home partition it's not a clean install. A wrong configuration will survive in /home and be brought into the new system.

---

### Post by sugeek85 on 2019-06-01
I know this is an old post but just had this problem pop up on my old Dell Inspiron 1501 laptop running Lubuntu 18.04. Alot of people with this issue all over forums everywhere. What my problem ended up being was a setting in the bios. On my machine it's called "PoweNow" under the "Advanced" tab in the bios. It was set to "enabled", and when I disabled it, shutdown and reboot immediately worked again. Hope this helps someone else too.

---

