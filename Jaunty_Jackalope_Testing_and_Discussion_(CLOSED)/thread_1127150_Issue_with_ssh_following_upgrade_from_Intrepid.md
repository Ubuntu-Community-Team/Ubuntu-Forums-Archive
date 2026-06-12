---
title: "Issue with ssh following upgrade from Intrepid"
date: 2009-04-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by twigusa on 2009-04-16
Hi,

I've been having some issues with using putty from my Windows machine at work to connect via ssh to my Jaunty box at home over the internet. This has happened since upgrading from Intrepid but it didn't happen immediately.

I've verified that ssh is open on the Jaunty machine by connecting to 127.0.0.1 and also connecting from another machine on my home lan.

This would then seem to point to my router / firewall and not the Jaunty machine. However, it has been working since the upgrade and I also had the same problem on another Jaunty machine at work (fresh install not an upgrade). This disappeared after running some updates and rebooting.

Any ideas?

Thanks,
Twig.

---

### Post by nandemonai on 2009-04-16
Use a firewall test like shields up to test your network from the outside.

A couple things spring to mind.. Are you on a NAT connection? Have you changed IP? Is the correct port forwarded?

---

### Post by twigusa on 2009-04-16
Hi,

Thanks for the reply. I am on a dynamic IP with nat but I use a dynamic dns service and have tested and it is all working fine. I also forward other traffic through the router which is working too. Also, I've verified the port and rebooted the router etc. but still no joy. 

I'll test the firewall with shields up when I get near my home machine.

Twig.

---

### Post by twigusa on 2009-04-16
Well, it seems I didn't test thoroughly enough. It was an issue with my dynamic dns not updating properly. I noticed it from the shields up website which reported a different IP from the one I was expecting. It's all working now.

Thanks for your help again.

Twig.

---

