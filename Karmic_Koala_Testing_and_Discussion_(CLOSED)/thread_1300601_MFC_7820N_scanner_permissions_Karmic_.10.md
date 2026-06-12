---
title: "MFC 7820N scanner permissions Karmic .10"
date: 2009-10-25
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by linyanam on 2009-10-25
Hi
I have Brother MFC 7820N scanner which I use with usb connection.
After upgrading from Jaunty to Karmic, regular user does not have access to it. root has access.
"sudo xsane" works. How to give permissions to regular user. [Brother website]("http://solutions.brother.com/linux/en_us/instruction_scn1c.html") does not yet give details about karmic.
Editing "/lib/udev/rules.d/50-udev-default.rules" as in 9.04 Jaunty did not help.
Thanks in advance
Cheers,
Linyanam

---

### Post by linyanam on 2009-10-25
Found the answer [here]("https://bugs.launchpad.net/ubuntu/+source/sane-backends/+bug/217571/comments/12")

---

