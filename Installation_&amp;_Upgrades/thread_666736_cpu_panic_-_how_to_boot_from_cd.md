---
title: "cpu panic - how to boot from cd?"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by roft84 on 2008-01-13
Hi,
I'm trying to install on dell latitude d600 with vm server and get a cpu panic message when ubuntu boots. I've looked at one forum which says
"Boot the server from the CD, choose to ‘Rescue a broken system’", but I don't know how to boot from the CD when ubuntu is starting. Can someone tell me pls.

Thanks.

---

### Post by Craigus on 2008-01-13
> dell latitude d600 with vm server

So, you're running vmware server under windows and installing linux in that ?

---

### Post by roft84 on 2008-01-14
yes, D600 running XP, got vmware server installed.
Ubuntu server version has installed but when boots I get the cpu panic message.

---

### Post by Craigus on 2008-01-14
Does this fix it:

[http://eric.biven.us/2007/11/04/running-ubuntu-server-710-in-vmware-server/]("http://eric.biven.us/2007/11/04/running-ubuntu-server-710-in-vmware-server/")

Edit: oops, from your initial post, it looks like you found that. 

If you configure the virtual machine with a physical CD drive it should boot from that. Then you should be able to navigate to /boot on the installed system. The virtual drive should be mounted.

---

### Post by Craigus on 2008-01-14
Alternatively, you could use a pre-built image:

[http://www.thoughtpolice.co.uk/vmware/]("http://www.thoughtpolice.co.uk/vmware/")

---

