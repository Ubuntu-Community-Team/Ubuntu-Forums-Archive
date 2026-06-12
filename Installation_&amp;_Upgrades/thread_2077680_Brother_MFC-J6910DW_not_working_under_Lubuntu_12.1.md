---
title: "Brother MFC-J6910DW not working under Lubuntu 12.10"
date: 2012-10-29
forum: Installation &amp; Upgrades
---

### Post by Askel on 2012-10-29
Edit: Solved now. I checked the printerdisplay for ip-adress. wich was 192.168.001.066
The real ip-adress was 192.168.1.66
No zeros. Now it's working like a charm (printing atleast. Havn't tried scanning yet.

Hello

I've had Ubuntu 12.04 before and installed the drivers to my printer without much hassle. But now I reinstalled the computer with Lubuntu 12.10 (plus the drivers on Brothers website has been updated). Anyways, I can't get it to work. I've followed the instructions and the printer is installed. When I go to: [http://localhost:631/printers/](http://localhost:631/printers/) I see my printer there. 

The IP is: 192.168.001.066 wich I set with this command: sudo brsaneconfig4  -a  name=MFC-J6910DW  model=MFC-J6910DW  ip=192.168.001.066

But when I use this command: sudo brscan-skey  -l

I get the following response:

 Brother           : brother4:net1;dev1  : 192.168.1.54         Not responded

If I press the printbutton the work comes up in [http://localhost:631/printers/](http://localhost:631/printers/) but it only says that the printer is unreacheble at the time.

I don't know what I'm doing wrong. I really can't get it to work.

---

