---
title: "Failed installation on Acer aspire one 110"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by acerperson on 2010-10-12
Hi I have tried and failed to install the lastest netbook version 10.10 on my Acer aspire one 110 netbook, this is the one with a 8gb ssh.
It booted fine on a usb drive and I was able to test drive the distro. The installation went all the way through without any problems but when it came to rebooting the netbook just showed a blank screen with a dash in the top left of the screen. There is no sign of the computer looking for the hard drive it just sits there!
If I reboot using the usb key I could see that all the files have been installed on the 8gb drive. I have reloaded 10.04 which works just great and during that installation the installer could see that 10.10 was installed.
Has anybody else had this problem? I was wondering is there is a problem with GRUB , however it would be nice to install the new version it's so frustrating to have failed.:(

---

### Post by hecatae on 2010-10-12
sounds like grub has installed itself on the usb drive instead of the correct drive, had the same issue on both netbooks and desktop I tried to install from live usb on.

I've already posted the fix I applied in this thread: [http://ubuntuforums.org/showthread.php?t=1594515](http://ubuntuforums.org/showthread.php?t=1594515)

---

### Post by acerperson on 2010-10-14
> **hecatae said:**
> sounds like grub has installed itself on the usb drive instead of the correct drive, had the same issue on both netbooks and desktop I tried to install from live usb on.

I've already posted the fix I applied in this thread: [http://ubuntuforums.org/showthread.php?t=1594515](http://ubuntuforums.org/showthread.php?t=1594515)
Thanks for the reply , when I have the time I'll give it a try. 10.10 works great on my desktop. I don't understand how the installation works perfectly for most people but not others. 
So if I apply the code 'sudo dpkg-reconfigure grub-pc' then I should be able to install Grub on the HD. I hope it's easy.

---

### Post by annoyingrob on 2010-10-14
You can install grub manually from your live cd too. I had to do that when I installed 10.10 on my desktop. It's really easy.

Boot into live cd,

mount your hard drive root partition somewhere,

run something like this:
```
sudo grub-install --root-directory=/mount_of_ssd /dev/sdx
```

Where /mount_of_ssd is where you mounted your root partition, and /dev/sdx is the device that corresponds to your ssd

---

