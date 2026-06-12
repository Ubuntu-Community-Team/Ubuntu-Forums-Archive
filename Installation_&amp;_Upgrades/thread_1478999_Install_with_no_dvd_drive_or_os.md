---
title: "Install with no dvd drive or os"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by philliprobert on 2010-05-10
Hi, i have an old dell c400 with no cd drive. Has a usb drive, but wont boot off it. Windows xp is on it, but would prefer not to use wubi.
I am trying to install 10.04 on it using roundabout means! I got as far as creating a startup disk in ubuntu, pointing to an external laptop drive i had available, it creates fine.
This is where i get stuck. Swapping out the drive, ubuntu live cd boots, gives me the live os no problem. I just cant seem to install it correctly, i believe it is because of how i have it partition.
I orignally just deleted the parition, and let startdisk manager use it all. Booted fine, but gave an error that it couldnt install because /cdrom was mounted.
Any suggestions on how to do this? My normal laptop is running fine, dual boot between ubunto 10.04 and Windows 7. Any deployment method, including PXE would be useful, i just couldnt figure out pxe.
My Modem is the dhcp server normally, If i wanted pxe to work, would i do it offline, set my working laptop as dhcp server, point to local iso and away i go? If so, is there any tips anywhere?
Thanks

---

### Post by darkod on 2010-05-10
Can this help or too complicated?
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

PS. It doesn't seem to require using your newer laptop as DHCP server. In the tutorial that's how they do it, but if the modem you mentioned is actually your router which gives IP addresses to both your new and old laptop, just check those addresses in the router status pages and use them. They won't change for the duration of the install, and you don't care if they change later.

You will just need to install the TFTP on the new laptop to serve as TFTP server.

---

