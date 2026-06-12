---
title: "[SOLVED] Only one core of dual core AMD cpu enabled"
date: 2008-09-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by vishalrao on 2008-09-06
Subscribed to [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215785](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215785) and posted dmesg etc.

I have an HP Pavilion tx1302au Tablet PC with AMD Turion64 TL-58 1.9 ghz dual core mobile CPU and only one core is enabled. GNOME System Monitor also shows one core.

This is with Intrepid Alpha 5 with the new .27-2.3 AMD64 kernel and I have to provide the "nolapic" kernel boot option to be able to boot.

Worked fine in Hardy amd64 and Intrepid Alpha 4 previous kernel so I hope this is not taken as a regression - I'd still like to see .27 in Intrepid with this issue fixed :D

---

### Post by vishalrao on 2008-09-12
Updated today after nearly a week and the problem no longer occurs for me. Also no more need to specify the nolapic kernel boot option either.

---

### Post by Megatog615 on 2008-10-28
I get this issue right now with an AMD Athlon64 X2 5600+.

**EDIT**: I found out it's because the -rt kernel does not support SMP.

---

