---
title: "boot-repair recommended repair - attempt to read or write outside hd0"
date: 2022-12-25
forum: Installation &amp; Upgrades
---

### Post by soundscience on 2022-12-25
Hi, boot-repair is unable to successfully repair my grub it seems. I'm not sure what the issue is, but here's the pastebin I received after running it initially: [https://paste.ubuntu.com/p/RGm5sHZt4h/](https://paste.ubuntu.com/p/RGm5sHZt4h/)

It fails with a message saying "attempt to read or write outside hd0"

---

### Post by ajgreeny on 2022-12-25
Your boot-info shows nothing at the end which should give us information we need so perhaps try running it again.

Usually at the end it has a section titled "Recommended Repair" with details  of the suggested repair; yours shows nothing of that to give us any clues.

---

### Post by tea for one on 2022-12-25
[COLOR="#0000FF"]Line 119[/COLOR] - sda:4398GB:scsi:512:512:gpt:QEMU QEMU HARDDISK

It looks like you are trying to repair Grub in a Virtual Machine?
If so, you have to boot the live repair session in the same way i.e. as if you were beginning the process of creating a new VM.

---

### Post by ajgreeny on 2022-12-26
Good catch TFO, which I missed completely; I blame Christmas festivities!

You may have to add the iso file again to your virtual system's virtual CC drive in the QEMU settings window as it often disappears after installation.
However, your report does end unusually with no recommended repair suggestion so I still believe something is missing.

---

### Post by soundscience on 2022-12-26
Hi all, sorry, I'm not sure how to mark this as solved but what I ended up doing was using the boot repair tool to purge and install the newest kernel. I was receiving a different error when trying to boot into an older kernel which lead me down this path

---

### Post by ajgreeny on 2022-12-27
Please mark as SOLVED from the Thread Tools menu at the top of the thread.

---

