---
title: "SSDs invisible (even in BIOS)"
date: 2012-01-16
forum: Installation &amp; Upgrades
---

### Post by rwst on 2012-01-16
Hello,
I had someone assemble me a new computer with:


[LIST]
[*] AMD Phenom II X6 1055T
[*] Gigabyte MA770T-UD3 board with 6xSATA 3Gb/s
[*] 8192MB (2x4096MB) Team Elite DDR3 CL9 1333
[*] OCZ Vertex Plus 60GB (SSD)
[*] Corsair Force Series 3 240GB 2.5"(6,4cm) SATA3 (SSD)
[*] (everything else working fine: CDROM, Firewire, USB)
[/LIST]
Linux won't see the SSD drives, even in BIOS they're invisible.
BIOS: I have tried switching SATA to IDE/RAID/AHCI.
I have set IDE scan to LBA and switched off some alarm functions.
Linux: I have tried 10.03 and 11.10 AMD isos, also KNOPPIX 6.
With 11.10, I have tried noacpi and acpi=noirq, also ahci.disabled=1
(this is from memory, I will try to transfer logs later, after your suggestions)


Question: what should be visible to the PCI bus? There is no mention of any
drives in PCI output, but maybe *something* should be visible. Can you tell me
please what should always be seen in case such drives are plugged in? I want
to have a minimum of confirmation to start from.


Many thanks in advance for any ideas,
rwst
PS: I know the Vertex+ will need IDE and the Corsair AHCI but we're not even close to such a decision.
PPS: Is the mainboard too old?

---

### Post by Quackers on 2012-01-16
Welcome to UF :-)
Are you using SATA3 ports? If so, try SATA2 ports and things may improve.

---

### Post by rwst on 2012-01-16
> **Quackers said:**
> Welcome to UF :-)
Are you using SATA3 ports? If so, try SATA2 ports and things may improve.

Well, I'm a bit challenged to answer that. Assume I cannot open the case atm nor do any hardware changes. Can I see anyhow from the software side if the drives were actually plugged into SATA3, so that I can tell the person who'll open it to replug them?

---

### Post by Quackers on 2012-01-16
Not sure. Can you ask the person who built it for you?
I'm not sure on the current stage of development in this area, but certainly SATA3 (or at least some SATA3 controllers) were not compatible with Linux.
You could also wait for somebody with more direct experience of this to comment.

---

### Post by rwst on 2012-01-16
> **Quackers said:**
> Not sure. Can you ask the person who built it for you?
I'm not sure on the current stage of development in this area, but certainly SATA3 (or at least some SATA3 controllers) were not compatible with Linux.
You could also wait for somebody with more direct experience of this to comment.

I just see the board has 6x3Gb/s which is all SATA2, according to Wikipedia.

---

### Post by Quackers on 2012-01-16
It may be an idea to check that the connections are good with the motherboard. That's a sensible first step. Obviously that would mean opening the case. If you are uneasy doing that you should maybe contact the builder of the system and see what he/she recommends.

---

### Post by dino99 on 2012-01-16
[http://www.ocztechnologyforum.com/forum/showthread.php?97454-BIOS-doesn-t-recognize-Vertex-Plus-Drive](http://www.ocztechnologyforum.com/forum/showthread.php?97454-BIOS-doesn-t-recognize-Vertex-Plus-Drive)

[http://askubuntu.com/questions/19376/installing-ubuntu-on-a-ssd](http://askubuntu.com/questions/19376/installing-ubuntu-on-a-ssd)
[http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/](http://www.howtogeek.com/62761/how-to-tweak-your-ssd-in-ubuntu-for-better-performance/)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)
[http://www.overclock.net/t/873608/installing-ubuntu-10-10-on-ssd](http://www.overclock.net/t/873608/installing-ubuntu-10-10-on-ssd)

---

### Post by rwst on 2012-01-16
> **dino99 said:**
> [LINKS...]("http://www.ocztechnologyforum.com/forum/showthread.php?97454-BIOS-doesn-t-recognize-Vertex-Plus-Drive")[]("http://www.overclock.net/t/873608/installing-ubuntu-10-10-on-ssd")

Thanks, I may need this later---the seller says I should open the case and check the cables. Oh well.

---

