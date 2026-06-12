---
title: "eth0 disappears after Intrepid dist-upgrade"
date: 2008-09-28
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by unixfanatic on 2008-09-28
I am running the Intrepid alpha right now and just finished a dist-upgrade to a new kernel (2.6.27-4-generic from 2.6.27-3-generic).  After doing so, eth0 has completely disappeared.  It is unlisted in ifconfig.  I added it to /etc/network/interfaces, but it just says "device not found" when I try to run it with /etc/init.d/networking start.  My ethernet device is an Intel 82562V-2 according to lspci.  Is there anything I can do, considering that the computer can no longer connect to the Internet?

---

### Post by Dwaine on 2008-09-28
I have a similar problem after installing ubuntu_studio from scratch. During the DVD install (version 8.0.4.1) it saw and configured the network adapter, and used it during the install. Then when it was all done, and rebooted, I logged in, and no network access. All I see in ifconfig is lo. If I do a network restart, it tries to start eth0, then says no device. Help?

---

### Post by cavendish on 2008-09-28
Take a look at this: 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555)

Got mine working again by commenting out 2.6.27-rc kernel retaining
an earlier one 2.6.22 in /boot/Grub/menu.lst

See also:
[http://ubuntuforums.org/showthread.php?t=927943](http://ubuntuforums.org/showthread.php?t=927943)

---

### Post by Dwaine on 2008-09-29
In another post, I found this suggestion:

lshw -C network

This shows you your network hardware. I ran it, and it found nothing! My mobo has a NIC built in. So I knew it wasn't gone. I saw some other messages mentioning doing this command to see what's on the PCI bus:

lspci 

This showed me lots of stuff, but no NIC. But it did point out the Sound Blaster Audigy 2 card I had added. This made me wonder if the Audigy card was messing up the NIC. I removed the Audigy card and when I powered back up, networking was there and working good. 

Now, this Audigy card was there during the initial install, and the networking was working then. Likely there was no Audigy driver loaded at that point, so it wasn't conflicting with the NIC. But after the install and reboot, it did install an Audigy driver ( I know this because it was outputting audio properly). So I guess at that point the Audigy card DID conflict with the NIC on the PCI bus somehow, and kept the NIC from being seen. 

In researching this problem, I see lots of people have eth0 disappear randomly. I would suggest that adding a new card in the system could certainly be something to watch out for if this happens. 

Now I just have to figure out if I can make the Audigy card and the NIC work happily together somehow. 

Dwaine

---

### Post by Tom--d on 2008-09-29
The driver might of corrupted your Network Card.

---

### Post by unixfanatic on 2008-09-29
Hmmm.  I've always had a lot of trouble with the dist-upgrades — sometimes the graphics don't work anymore, most notoriously the wireless won't work.  But I've never had eth0 stop functioning.  Yet this definitely does look like a driver problem.

Is there somewhere I could submit a bug report for this?  I know that the beta of Intrepid is coming out on Thursday.  Maybe the Ubuntu developers could bundle in a fix so that I could burn a CD and do a dist-upgrade from that to get everything working again?

---

### Post by tangibleorange on 2008-09-29
> **unixfanatic said:**
> Hmmm.  I've always had a lot of trouble with the dist-upgrades — sometimes the graphics don't work anymore, most notoriously the wireless won't work.  But I've never had eth0 stop functioning.  Yet this definitely does look like a driver problem.

Is there somewhere I could submit a bug report for this?  I know that the beta of Intrepid is coming out on Thursday.  Maybe the Ubuntu developers could bundle in a fix so that I could burn a CD and do a dist-upgrade from that to get everything working again?

someone already posted a link above to the existing bug. there is no need to report it again i don't think:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/263555")

---

### Post by unixfanatic on 2008-09-29
Oh OK, sorry about that.  I've never reported a bug to Ubuntu before so I'm a little new to the process...

Is there any way of knowing whether the bug will be fixable by just dist-upgrading from the CD, though?

---

