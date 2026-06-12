---
title: "Can't install 12.04 on machine without Internet connection"
date: 2013-06-24
forum: Installation &amp; Upgrades
---

### Post by dbclinton on 2013-06-24
Hi,
I'm trying to install 12.04 on a machine without a direct connection to a router or dsl. An Internet-connected dhcp server does give it an ip address and I can ping the server, but I can't set a gateway - sudo route add default gw 192.168.0.254 appears to work, but ifconfig reports no gateway on eth0 and there is no outside access.
So, if I can't get connectivity, I could always just install direct from my usb, right? Nope. the "download updates while installing" option is checked "on" and grayed out...so I can't uncheck it. That means that the install routine will report "retrieving files" indefinitely and the install will fail.
Any ideas?
Thanks

---

### Post by dbclinton on 2013-06-26
Update: I've now had the same problem with 13.04...this time, "download updates while installing" is NOT checked, but it still gets stuck trying to retrieve files.
Does anyone know why Ubuntu gives such trouble installing without an Internet connection?

---

### Post by nathanservicesinc on 2013-06-26
> **dbclinton said:**
> Hi,
I'm trying to install 12.04 on a machine without a direct connection to a router or dsl. An Internet-connected dhcp server does give it an ip address and I can ping the server, but I can't set a gateway - sudo route add default gw 192.168.0.254 appears to work, but ifconfig reports no gateway on eth0 and there is no outside access.
So, if I can't get connectivity, I could always just install direct from my usb, right? Nope. the "download updates while installing" option is checked "on" and grayed out...so I can't uncheck it. That means that the install routine will report "retrieving files" indefinitely and the install will fail.
Any ideas?
Thanks
You may not be able to go online ; however an option may be to use a DVD instead of a USB installation device.  I tried downloading UBUNTU 12.04 and 13.04 for my HP pavilion Windows 7 system and only got a dash line.   The DVD has more storage and can carry larger downloads.  If that doesn't work there is a source that takes about two weeks to have the disk mailed to you at home.  The disk DVD other UBUNTU programs the whole works and it's still free.

---

### Post by dbclinton on 2013-06-26
> **nathanservicesinc said:**
> You may not be able to go online ; however an option may be to use a DVD instead of a USB installation device.  I tried downloading UBUNTU 12.04 and 13.04 for my HP pavilion Windows 7 system and only got a dash line.   The DVD has more storage and can carry larger downloads.  If that doesn't work there is a source that takes about two weeks to have the disk mailed to you at home.  The disk DVD other UBUNTU programs the whole works and it's still free.

Thanks. But this machine hasn't got a DVD player. And, besides that, the iso for burning a DVD is the same as for USB.
Regards,
David

---

### Post by nathanservicesinc on 2013-07-16
I struggled with getting my Windows 7 HP pavilion to accept UBUNTU as an operating system working in its own partition on the same disk. But I had to go to a DVD instead of using the USB.  I wonder if you may have an option to add an external drive to your laptop or an external dvd.??  If not you have to make absolutely sure that the version of the ISO on your USB drive is 32-bit instead of 64-bit for the newer machines.  This is important and will make a big difference when trying to get the system to operate.

---

### Post by nathanservicesinc on 2013-07-16
If you've go the right 32-bit ISO Ubuntu operating system then also make sure your're using a*** UTILITY*** USB drive: I don't have time to explain but this can make a difference as well... a 16 Gig utility usb drive will be necessary...

---

### Post by dbclinton on 2013-07-16
Thanks, I'll keep that in mind. In the meantime, though, I gave up and installed Fedora.

---

