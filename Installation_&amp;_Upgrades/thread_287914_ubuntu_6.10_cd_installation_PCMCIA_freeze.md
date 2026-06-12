---
title: "ubuntu 6.10 cd installation PCMCIA freeze"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by b1tnut on 2006-10-29
Hello Community!

I'm trying to install Ubuntu 6.10 dapper on my no-name laptop. After googling and searching various forums i can't still find a solution to my problem:

Installation from cd-rom from CD seems to run smooth till loading the pcmcia-drivers in the hardware-initalizion phase which freezes the machine and forces me to reboot.

I had the same problems with breezy-bager at least i could solve it using the no-pcmcia boot parameter. Now if i use start_pcmcia=false as add. parameter it still crashes the laptop (i tried it as first parameter, after the "--" etc.).

Is there any way of how i could make a clean 6.10 install without first installing breezy and then upgrade????

Thanks so much to everybody.
I'm willing to post any file, more specific info etc. just to get it running asap.

regards, markus aka b1tnut

---

### Post by John.Michael.Kane on 2006-10-29
Ubuntu 6.10=Edgy
Ubuntu 6.06.1=Dapper

Also we need more info
Complete hardware specs videocard type/make.

Also need to know if your trying to install from the live/cd or alternate text mode cd or using the dist-upgrade command.

---

### Post by b1tnut on 2006-10-30
> **SD-Plissken said:**
> Ubuntu 6.10=Edgy
Ubuntu 6.06.1=Dapper

Also we need more info
Complete hardware specs videocard type/make.

Also need to know if your trying to install from the live/cd or alternate text mode cd or using the dist-upgrade command.

Thanks for your quick response and sorry about mixing up distro-titels.

I tried the edgy live/cd and the alternate text mode with the same result.

(PCMCIA) yenta socket
(Graphics) ATI RV350 [Mobility Radeon 9600 M10]

Attached you will find the output of the hwinfo-tool for further information. Please let me know if there is also a betther tool to get hw info in the shell.

regards, markus

---

### Post by John.Michael.Kane on 2006-11-02
You can try passing this command at the boot prompt ```
noapic nolapic hw-detect/start_pcmcia=false
```

---

