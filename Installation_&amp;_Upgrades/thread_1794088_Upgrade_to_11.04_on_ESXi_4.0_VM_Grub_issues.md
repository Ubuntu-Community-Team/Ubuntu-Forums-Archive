---
title: "Upgrade to 11.04 on ESXi 4.0 VM Grub issues"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by m3_del on 2011-06-30
Hi,

Recently I decided it was time to go ahead and upgrade a couple headless servers of mine from 10.04 to 11.04. I upgraded first to 10.10 and then to 11.04. (Just in case it matters I am using the VMXnet3 NIC)

The upgrade to 10.10 went great. All services were still functioning etc. I then began the path to 11.04. Once the server reboot, grub started to scream. Basically it is unable to find the boot partition. "No Such Disk" error followed by an invalid mode: auto message

I was up quite late last night searching for answers and decided to wait until morning to post for help.

Below is my fdisk -l and contents of /dev/sda5 output. When I mount /dev/sda5 I see all the normal files. At the grub menu, however, when I input
```

root (hd0,4)
setup (hd0)

```

I get a stage1 not found message! Any help would be appreciated!

/dev/sda5
[IMG]http://i54.tinypic.com/ape2vb.png[/IMG]

fdisk -l
[IMG]http://i52.tinypic.com/15zgnds.png[/IMG]

From the Grub Menu ls
[IMG]http://i52.tinypic.com/sm5z0l.png[/IMG]

---

### Post by m3_del on 2011-06-30
Solved part of my problem by purging (not uninstalling) and installing grub2. I used the Server Disk in rescue mode. I select the /dev/[servername]/root partition. Then execute a shell. No need to chroot. I then mounted the boot partition (In my case /dev/sda5) to /boot and then ran

```
apt-get purge grub grub-pc grub-common
apt-get install grub-common grub-pc
update-grub
```

And walla I can get past grub, but now I am at a blinking cursor!! Funny thing is, all services start up I just can not interact with the console. Any thoughts? Again this is a headless server.

---

