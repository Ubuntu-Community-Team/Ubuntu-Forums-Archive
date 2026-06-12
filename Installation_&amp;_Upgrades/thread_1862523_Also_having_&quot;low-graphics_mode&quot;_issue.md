---
title: "Also having &quot;low-graphics mode&quot; issue"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by crisedwards on 2011-10-16
I am in a similar situation as the user [in this tread]("http://ubuntuforums.org/showthread.php?t=1861192&highlight=low-graphics+mode"). I have a Lenovo ideacentre Q150 which was running 11.04 when I tried the upgrade. Halfway through, it froze up and I rebooted, getting the "Low-Graphics Mode" error. After trying a few options there, I was able to get to a prompt and did a 

```
sudo dpkg --configure -a
```

I wasn't able to get any of this:

```
gksudo /etc/default/grub
```

without getting an error about my display.

Another reboot gets me to a screen that says:

*PulseAudio confirmed for per-user sessions      [OK]
saned disabled; edit /etc/default/saned
*enabling additional executable binary formats bin fmt-support     [OK]
apache2: Could not reliably determine the server's fully qualified domain name, using ::1 for ServerName
*Starting webserver a
pache2         [OK]
              [OK]


Now what?

---

### Post by crisedwards on 2011-10-16
OK, now I am at the "***Checking Battery State***" place as the user in the previously-mentioned thread. I am going to return to that thread and pickup there.

---

### Post by collisionystm on 2011-10-16
reboot

right after your bios, hold the shift key

you will be at the grub menu

choose system rescue

choose resume normal boot

you will be at a text login

put in your user name and password

now do the 
sudo dpkg --configure -a

---

