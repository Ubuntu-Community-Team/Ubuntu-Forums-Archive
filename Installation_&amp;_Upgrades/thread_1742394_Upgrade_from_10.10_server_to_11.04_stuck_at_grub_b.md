---
title: "Upgrade from 10.10 server to 11.04 stuck at grub boot screen"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by mil77 on 2011-04-28
I've upgraded two servers from 10.10 to 11.04. No error or problem during upgrade. After the upgrade both servers stuck at grub boot screen no boot choice, nothing, just grub screen with minimal bash like editing. Both servers have LVM2 encryption on / and they are running inside the vsphere.

HELP!!! :confused:

---

### Post by rkillcrazy on 2011-04-29
> **mil77 said:**
> I've upgraded two servers from 10.10 to 11.04. No error or problem during upgrade. After the upgrade both servers stuck at grub boot screen no boot choice, nothing, just grub screen with minimal bash like editing. Both servers have LVM2 encryption on / and they are running inside the vsphere.

HELP!!! :confused:

I have the same issue.  Went from 10.04.02 to 10.10 and then 11.04.  10.10 worked fine.  11.04 gets through POST and then stop at a grub prompt. :confused:

---

### Post by davrosuk on 2011-04-29
I know this isn't exactly very helpful... but why would you 'upgrade' a server to non LTS? On the desktop, I can see why people would want to upgrade... but server? really? I know I'll be sticking with 10.04 LTS until I'm compelled to move away from it. Its stable and gives me exactly what I need.

As I say, not too helpful, but food for thought :-)

---

### Post by rkillcrazy on 2011-04-29
> **davrosuk said:**
> I know this isn't exactly very helpful... but why would you 'upgrade' a server to non LTS? On the desktop, I can see why people would want to upgrade... but server? really? I know I'll be sticking with 10.04 LTS until I'm compelled to move away from it. Its stable and gives me exactly what I need.

As I say, not too helpful, but food for thought :-)

I'm merely testing the upgrade path in a non-production environment.

---

### Post by mil77 on 2011-04-29
It seems that upgrade breaks grub, which then defaults to grub rescue menu. I've upgraded the same servers from version 9 to version 10 without problem. Upgrading them from 10 to 11 seems to break grub and who knows what else. I've saved the data on the servers by loading ubuntu live disk and then manually mounting lvm2 encrypted partitions. I don't have time to play with grub or troubleshoot something that shouldn't been happening in the first place. Just moving everything onto debian squeeze servers and saying buy, buy to ubuntu server. Next time ubuntu development should play a bit more with different setups and upgrade paths before releasing something that breaks server systems into wild. About upgrading the server systems. Why not upgrade? New kernel, new functionality, more responsive system, etc.

---

### Post by davrosuk on 2011-04-30
> **mil77 said:**
> It seems that upgrade breaks grub, which then defaults to grub rescue menu. I've upgraded the same servers from version 9 to version 10 without problem. Upgrading them from 10 to 11 seems to break grub and who knows what else. I've saved the data on the servers by loading ubuntu live disk and then manually mounting lvm2 encrypted partitions. I don't have time to play with grub or troubleshoot something that shouldn't been happening in the first place. Just moving everything onto debian squeeze servers and saying buy, buy to ubuntu server. Next time ubuntu development should play a bit more with different setups and upgrade paths before releasing something that breaks server systems into wild. About upgrading the server systems. Why not upgrade? New kernel, new functionality, more responsive system, etc.

I totally agree on the testing front - although its quite difficult to cover every test case, so I appreciate what the team does.

Each to his own - but when it comes to a server system, stability is key. I might be looking at this from a different angle because in general I'm dealing with production systems that need five nines of uptime - So for me, a bump in kernel and extra flashing lights isn't a reason to upgrade. If its a home system and you're happy to have long periods of downtime, well, thats a different story.

---

### Post by rkillcrazy on 2011-04-30
**The topic at hand:**
Well, like I said, it's a non-production server.  Moreover, the issue is still there, regardless of one's opinion of whether or not an upgrade is warranted.

**The side conversation:**
There's still the issue of an upgrade path.  Say you waited for the next LTS.  If you didn't want to do a complete reinstall, you'd follow the upgrade path - 10.04 > 10.10 > 11.04 > 11.10 > 12.04...  So, the issue would still more than likely show up.  While my server will remain an LTS, I still like to test upgrade paths as timed goes by.  That way, when the next LTS comes out, I can upgrade with confidence.  This looks like I might not easily be able to do that next time....

---

### Post by mamlouk on 2011-05-02
Same scenario, different setup.

Setup: Ubuntu server 10.10 64-bit installed as a VM under a CentOS KVM host. Default installation, no encryption of / or /home. Drive size 5GB, memory is 256MB.

Maverick ran smoothly on 3 VMs (including this one), and I decided to test the upgrade.

I ran ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo do-release-upgrade
```

Upgrade went fine, and when rebooted, stuck @ a grub menu "GNU GRUB version 1.97~beta4" with a grub prompt.

---

### Post by mamlouk on 2011-05-02
I was able to boot temporarily, but problem persists when rebooted. I used```
sh:grub> linux (hd0,5)/vmlinux-2.6.38-8-server root=/dev/mapper/ubuntu-root
sh:grub> initrd (hd0,5)/initrd.img-2.6.38-8-server
sh:grub> boot
```
Not to mention that I have a separate /boot partition, and my / partition is LVM. Guessing the encrypted / partition will work normally once the kernel is loaded.

Now I can login, but will have to find a way for a persistent normal reboot.

--Edit: Typo

---

### Post by mamlouk on 2011-05-02
Reinstalled Grub2 using procedures from [this]("http://ubuntuforums.org/showthread.php?t=1195275") link.
```
sudo cp /etc/default/grub /etc/default/grub.old
sudo cp -R /etc/grub.d /etc/grub.d.old
sudo cp -R /boot/grub /boot/grub.old
sudo apt-get purge grub-common grub-pc
sudo apt-get install grub-common grub-pc
sudo update-grub
```
Now 11.04 boots normally, but I lost terminal access although I can ssh into it.

Right now, I'm checking the differences between the backed-up version, and the newly-installed version. Configuration files are identical, but I found differences in the /boot/grub and /boot/grub.old folders.

---

