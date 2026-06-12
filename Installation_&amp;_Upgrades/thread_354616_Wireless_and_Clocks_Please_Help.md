---
title: "Wireless and Clocks: Please Help"
date: 2007-02-06
forum: Installation &amp; Upgrades
---

### Post by Dylnuge on 2007-02-06
Hello,

I got Ubuntu 6.06 LTS to work on my computer and need some help:

1. My clock is always wrong in either windows or ubuntu. Windows wants to switch it to local time, so it displays the GMT, while Ubuntu wants to take the GMT and then display local time, putting it way off if windows resets. I need to make one comply with the other.

2. I need to get my wireless working. On my old computer, it worked automaticly, but I have a newer version of the system now, and the drivers are ipw3945. I need to know if I plug the system into an eth cable and install the drivers will it work instantly? Also, will the eth work automaticly (it uses Broadcom TG3 drivers).

Thanks-
Dylan

---

### Post by mikewhatever on 2007-02-06
Hi, 
I think the clock issue may be the wrong time zone you have chosen.
What is the problem with the wireless. Have you tried System->Administration->Networking? I am not sure, but it can be somewhat different in 6.06. Anyway, I have the same driver for the Intel based wireless card, and it works.

---

### Post by bapoumba on 2007-02-06
Hello,
what does return : ```
~ $ cat /etc/default/rcS | grep UTC
```
If it says yes, you should set it to **no** and reboot.
Windows reads bios time and that's it. You have to set local time directly in your bios.
With Linux, you can switch timezones easily without playing around with bios. Give your proper timezone, say that bios time is not UTC, and you should be all set.

---

