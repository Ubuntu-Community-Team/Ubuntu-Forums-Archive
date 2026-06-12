---
title: "Ubuntu Server 14.04 LTSP Client login failure"
date: 2014-05-31
forum: Installation &amp; Upgrades
---

### Post by kasper219 on 2014-05-31
I just set up a new LTSP server and all is well except for the fact that when i log in through the gui it gives "no response from server, restarting", the dmesg output gives "nbd9: unknown partition table" and "block nbd9: NBD_DISCONNECT"

If i use tty1 to log in it allows me to login through the account that i created for the thin clients by chrooting into the ltsp image on the server and adding the client admin account. I have internet access and can ping the server so i am at a slight loss... I am using a dual nic setup (clients on 1 and internet on the other)

Any and all help would be greatly appreciated.

Regards,
kasper219

---

### Post by kasper219 on 2014-06-04
I did manage to get an LTSP server up and running, but i had to use the normal Ubuntu Desktop installation CD to do so. Once i got that done it was a matter of dumping all of the configuration files over for the dual nic setup to allow the clients to boot.

---

