---
title: "Observations on problem &quot;kdm_greet memory corruption, /dev/null permission denied&quot;"
date: 2006-08-05
forum: Installation &amp; Upgrades
---

### Post by ruedihofer on 2006-08-05
Hi

After an updating my Dapper Drake to the latest packages (kde 3.5.4, kernel vmlinuz-2.6.15-26-k7) I can't start kde anymore (AMD K7 with Nvidia Geforce2 MX400). In my syslog I see the following error messages: 
[SIZE="2"]Aug  4 21:05:05 localhost kdm_greet[8949]: Can't open default user face
Aug  4 21:05:25 localhost kdm_greet[8949]: Internal error: memory corruption detected[/SIZE]

Since I thought the problem was kdm related, I renamed /etc/kde3/kdm to something else and restarted kdm. I logged in and kde started up but showed only a xterm with error messages:
[SIZE="2"]/dev/null permission denied[/SIZE]

I chmod /dev/null to 777 and tried again. (Who had changed the permission of /dev/null to 400?) Anyway, I restarted kdm again and a xterm without decoration started up. From there I was able to start kicker, konqueror, kate... but all without decoration.

What I definitely can't start is the 'Appearance' part of the Kontrol Center. (There I was looking on how to enable the decorations.)

Has someone observed the same behaviour? I need further help on how to start the Windows Manager so that it shows the decorations!

Thank you!

---

### Post by r00tzz on 2006-10-11
Having this with latest Edgy also, don't know what is happening.

/etc/udev/rules.d/40-permissions.rules shows:

KERNEL=="null",                         MODE="0666"

anyone??

---

### Post by ruedihofer on 2006-10-24
My problem was completely solved when i upgraded my ubuntu to the very latest packages. I did that after i read that the nvidia driver had caused problems. ...but several packages were upgraded, so i don't know which one actually solved the problem.

---

### Post by m0nstermind on 2006-10-31
I had the same /dev/null permission problem after upgrading from dapper to edgy. After some investigation, i found, that /lib/udev/devices/null has wrong permissions (600). So, chmod 666 /lib/udev/devices/null solves this problem permanently.
Hope this will help to you too.

---

