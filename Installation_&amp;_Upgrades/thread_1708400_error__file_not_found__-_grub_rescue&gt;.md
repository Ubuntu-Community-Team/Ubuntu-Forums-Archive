---
title: "error : file not found  - grub rescue&gt;"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by simpleblue on 2011-03-16
When booting the laptop it was saying:



```
error : file not found
 grub rescue>

```I then did an install of Ubuntu 10.10 in hopes that it would reinstall a workable grub and I get this:


```
GNU GRUB version 1.98+20100804-5ubuntu3


Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.



grub>
```Windows XP is installed on sda1 and I only need to recover XP. The linux portion does not matter. Also, I do not have the setup disks for XP.


It is very important I get this working because it's not my computer so if anyone can help I would be very happy.

---

### Post by oboedad55 on 2011-03-16
Then just boot from a Windows XP disk, go to repair, and type "fixmbr". It will restore your Windows MBR, no Linux needed. Just noticed you have no Windows disc. Google for how to repair your MBR without a disc. The info is out there.

---

### Post by simpleblue on 2011-03-16
> **oboedad55 said:**
> Then just boot from a Windows XP disk, go to repair, and type "fixmbr". It will restore your Windows MBR, no Linux needed.
I don't have the disk so that option is not available. :(

---

### Post by oboedad55 on 2011-03-16
Dude, read the rest of my post.

---

### Post by simpleblue on 2011-03-16
> **oboedad55 said:**
> Dude, read the rest of my post.
I've read it and I'm searching. Thank you.

---

### Post by oboedad55 on 2011-03-16
OK, good luck. Post back if it works, or if you need more help.

---

### Post by simpleblue on 2011-03-16
> **oboedad55 said:**
> OK, good luck. Post back if it works, or if you need more help.

I found a solution:

Boot from a Ubuntu LiveCD and type this in terminal:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

I rebooted and the issue was fixed. I hope this helps others out.

---

