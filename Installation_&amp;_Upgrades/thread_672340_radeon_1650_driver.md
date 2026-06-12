---
title: "radeon 1650 driver"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by Pap3rbag on 2008-01-19
how do i install this driver? im  new to linux and when i put the cd nothing happens

---

### Post by Liam-Gorham on 2008-01-22
Yes i can help you with your driver problem i have had the same thing with my ati 9550 but i have fixed problem.

You will need 2 programs:
Wine (allows you to install exe files on ubuntu) heres the link
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

and your ati graphics card driver heres the link for that to:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/gamesite/8-1_xp32_dd_ccc_wdm_enu_57717.exe](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/gamesite/8-1_xp32_dd_ccc_wdm_enu_57717.exe)

this is only the link for Catalyst Software Suite other drivers for 1650 can be found at: 
[http://game.amd.com/us-en/drivers_catalyst.aspx?p=xp/radeonx-xp](http://game.amd.com/us-en/drivers_catalyst.aspx?p=xp/radeonx-xp)

Ok here goes:

1.) install wine 
2.) run the Catalyst Software Suite.exe though wine
3.) once it as installed go to system, admistrator and then restriced drivers manager. A driver should be on the list for your ati card. enable it and reboot your machine and it should work.


Hope this helps

If you have any problems with this just PM me and i will be happy to help.

---

### Post by kellemes on 2008-01-22
> **Liam-Gorham said:**
> Yes i can help you with your driver problem i have had the same thing with my ati 9550 but i have fixed problem.

You will need 2 programs:
Wine (allows you to install exe files on ubuntu) heres the link
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

and your ati graphics card driver heres the link for that to:
[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/gamesite/8-1_xp32_dd_ccc_wdm_enu_57717.exe](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/gamesite/8-1_xp32_dd_ccc_wdm_enu_57717.exe)

this is only the link for Catalyst Software Suite other drivers for 1650 can be found at: 
[http://game.amd.com/us-en/drivers_catalyst.aspx?p=xp/radeonx-xp](http://game.amd.com/us-en/drivers_catalyst.aspx?p=xp/radeonx-xp)

Ok here goes:

1.) install wine 
2.) run the Catalyst Software Suite.exe though wine
3.) once it as installed go to system, admistrator and then restriced drivers manager. A driver should be on the list for your ati card. enable it and reboot your machine and it should work.


Hope this helps

If you have any problems with this just PM me and i will be happy to help.


You just need a working driver right? Why catalyst through Wine?
The fglrx-driver is in the list of the restricted drivers manager to begin with as far as I know..

Man, I learn something everyday. ;-)

---

### Post by Liam-Gorham on 2008-01-22
Not with the 1650 as the driver(s) only come in windows format and that range ubuntu has to have the drivers from the ati webite.

---

### Post by kellemes on 2008-01-22
> **Liam-Gorham said:**
> Not with the 1650 as the driver(s) only come in windows format and that range ubuntu has to have the drivers from the ati webite.


I have the same card and simply installed the hole thing using the GNU/Linux-installer.
Here are the GNU/Linux drivers, I use version 8.42.3
[http://ati.amd.com/support/drivers/linux/radeonprevious-linux.html](http://ati.amd.com/support/drivers/linux/radeonprevious-linux.html)

Anyway, if it's works, that's fine ;-)

---

