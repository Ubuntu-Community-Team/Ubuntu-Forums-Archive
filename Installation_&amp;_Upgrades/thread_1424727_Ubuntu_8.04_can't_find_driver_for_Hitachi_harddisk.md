---
title: "Ubuntu 8.04 can't find driver for Hitachi harddisk"
date: 2010-03-08
forum: Installation &amp; Upgrades
---

### Post by pungki on 2010-03-08
I am trying to install [Ebox 1.4]("http://www.ebox-technologies.com/") on Lenovo 3000 G430 laptop. I am trying to install it as a Virtual Drive using Virtual Box. As host, I am using Ubuntu 9.10 Desktop Edition.

But the installation stuck in detect harddisk stage (Ebox 1.4 use Ubuntu 8.04). It said that Ubuntu can't recognize the harddisk and ask me to load the driver if I know the driver (but the problem is I don't know :) )

This is information from lshw command :

*-disk
                description: ATA Disk
                product: Hitachi HTS54322
                vendor: Hitachi
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: FBEO
                serial: 081107FB2F00LLHYZ1LB
                size: 232GiB (250GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=0d9c45eb

I've search on Google, and the harddisk is [Hitachi HTS543225L9A300]("http://www.buy.com/prod/hitachi-travelstar-5k320-hts543225l9a300-hard-drive-250gb-5400rpm-plug/q/loc/101/208292222.html").

Does anyone know what is the driver for this harddisk? Or where I can download the driver.

Thanks in advance.


-Pungki

---

