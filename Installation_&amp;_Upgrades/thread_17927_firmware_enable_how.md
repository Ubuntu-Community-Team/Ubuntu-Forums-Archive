---
title: "firmware enable how?"
date: 2005-03-03
forum: Installation &amp; Upgrades
---

### Post by Dotrig on 2005-03-03
i will get my harddrive lacie 500GB work any Know how i mount That i know how i mount nfts

---

### Post by az on 2005-03-03
What kind of device is it?

---

### Post by Dotrig on 2005-03-04
Harddrive :D

---

### Post by dewey on 2005-03-05
Is it primary master, primary slave, sata, ide?

Do you know what the partition number is?

---

### Post by Dotrig on 2005-03-05
firmware  wtf..

---

### Post by Dotrig on 2005-03-05
Wtf can any help me

---

### Post by alastair on 2005-03-05
"firmware wtf.."
"Wtf can any help me"

Do you know what "wtf" stands for? Is it polite?

No one can help you because you give NO INFORMATION that is useful to diagnose the problem. What has "firmware" got to do with anything?

You have a lacie disk you want to use on Ubuntu? I use a lacie disk on Ubuntu - no problem.

Answer some question and perhaps I can help :

Is it USB? Firewire?

When you plug it in, do any messages appear in the system log i.e.  have a shell open running "sudo tail -f /var/log/syslog" - then plug it in. Messages?

Does it have data on it already? Or can you format it with a Linux filesystem?

If you see a device (e.g. /dev/sda etc.) mentioned in the /var/log/syslog messages above, you can list partitions on it using :

fdisk -l /dev/sda  (example!)

---

