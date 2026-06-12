---
title: "No login console after upgrade ubuntu server from 9.10&gt;10.04&gt;10.10&gt;11.04"
date: 2011-07-13
forum: Installation &amp; Upgrades
---

### Post by chakhedik on 2011-07-13
Hi,

I just did "do-release-upgrade" from ubuntu 9.10 > 10.04 > 10.10 > 11.04 which successful but after a restart, no login console just a blinking underscore. However I still able to login to server using ssh. During the boot I saw this failure "Starting system V runlevel compatibility [fail]".

How do I fix this?Please help...

---

### Post by billschu on 2011-08-19
same issue but fresh 11.04-64bit install, not upgrade - worked fine as usual when setup - possibly related to later install of webmin with requisite changing of root password?
goes through grub menu normally, a while later signal to monitor goes dead, trying to login blind doesn't wake monitor up, reboot does

ssh access always works, 11.04-32bit install on same machine works

no joy from update-grub or grub-mkconfig nothing obvious in dmesg or syslog - changing root back to no logins allowed also didn't fix

---

### Post by LurPak on 2011-09-27
Hi,

I encountered the same problem as you did with no login console just a blinking underscore. And all the configured services (SMB, SSH, NTP, Apache, etc) were working too. However it showed up that I was using terminal session 7 :)

On my machine, as I know, there are seven terminal sessions.  The first six terminal sessions are text console sessions. You can toggle between them hitting <Cntrl><Alt><F1>, <Cntrl><Alt><F2>, etc up to <Cntrl><Alt><F6>

But when hitting <Cntrl><Alt><F7> there is just a blinking cursor at the upper left corner. Not sure of the purpose of this session.

The rest of the function keys do nothing.

---

### Post by MAFoElffen on 2011-09-28
> **chakhedik said:**
> Hi,

I just did "do-release-upgrade" from ubuntu 9.10 > 10.04 > 10.10 > 11.04 which successful but after a restart, no login console just a blinking underscore. However I still able to login to server using ssh. During the boot I saw this failure "Starting system V runlevel compatibility [fail]".

How do I fix this?Please help...
And to the other 2 with the same...

Server Edition used to be totally tty text based console display.  Starting back 11.04 it went to using KMS and do VGA graphics.  That added the capability to start adding themes such as the aubergine theming.

Most server boards have basic VGA GPU graphics... If you install on a box that has better graphic GPU's such as NVidia or ATI, you might have to turn off KMS with a nomodeset or radeon.mode=0 kernel boot switch.

---

### Post by LurPak on 2011-09-28
> **MAFoElffen said:**
> And to the other 2 with the same...

Server Edition used to be totally tty text based console display.  Starting back 11.04 it went to using KMS and do VGA graphics.  That added the capability to start adding themes such as the aubergine theming.

Most server boards have basic VGA GPU graphics... If you install on a box that has better graphic GPU's such as NVidia or ATI, you might have to turn off KMS with a nomodeset or radeon.mode=0 kernel boot switch.


[LIST]
[*]Does this mean that the Server Edition now has graphic capabilities active by default? Maybe there are some settings needed to get the graphics working?
[*]Is the terminal session 7 supposed to show that graphics?
[/LIST]

I'm running the 32-bit Server Edition (which was installed on version 9.10 and upgraded to 11.04), on this Intel desktop board which has built in graphics (i.e. no Nvidia or AMD graphic GPUs):
[http://www.intel.com/Products/Desktop/Motherboards/D945GSEJT/D945GSEJT-overview.htm](http://www.intel.com/Products/Desktop/Motherboards/D945GSEJT/D945GSEJT-overview.htm)


[LIST]
[*]Shouldn't this setup show graphics now then?
[/LIST]

Thanks.
BR,
LurPak

---

