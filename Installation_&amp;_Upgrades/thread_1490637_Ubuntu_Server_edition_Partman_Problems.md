---
title: "Ubuntu Server edition Partman Problems"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by Theory5 on 2010-05-22
I have been trying to install Ubuntu Server Edition from a USB drive for a long time. I finally get it working at it freezes at 43% when launching the partitioning service. I read that If I type in 
tail /var/log/partman 

it would show me what was going on.
It came out with this:
Parted Server: Read Command: Open
Parted Server: Command_Open()
Parted Server: request to open =dev=sdb
Parted Server: opening outfifo
Parted Server: OUT : Ok

Parted Server: OUT : Ok

What does this mean? IS there a problem and can it be fixed? Also, What command sends me back to the installer GUI?

I also found out that if I remove the USB stick it will go to 47% if I run partman again. Help?

---

