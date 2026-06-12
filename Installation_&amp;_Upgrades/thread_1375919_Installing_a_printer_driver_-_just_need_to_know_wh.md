---
title: "Installing a printer driver - just need to know what to do"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by simpleblue on 2010-01-08
It'll likely work, I'm just new here and need some baby steps to learn how to walk again. ;)

I'm installing the driver on [this]("http://www.samsung.com/us/support/detail/supportPrdDetail.do?menu=SP01&prd_mdl_cd=&prd_mdl_name=CLP-310N&prd_ia_sub_class_cd=P") link. It would be the 'unified driver for linux.'

Here is what the terminal says: andre@andre-desktop:~$

If anyone could help with a step by step I would really really appreciate it. Plus I'll have learned for next time so I won't have to keep asking! :P


Here are the instructions:

[Ubuntu OS Installation]
[I]
1. Download and extract the driver. 

2. Open ''Root Terminal'' 

3. Execute installation program. 
   $ sudo cdroot/autorun

4. After install, PPD path is set again.
   $ sudo ln -s /usr/share/cups/model/samsung /usr/share/ppd/custom/samsung

5. Execute Configurator, and Add your printer model name by Add Printer.[/I]


I don't know how to change directories or where to extract the tar.gz file to. I also don't know what 'Root Terminal' is.


Thanx

---

### Post by mk1w86 on 2010-01-08
Chances are the driver is already included with Ubuntu.  Try installing the printer from

System>>Administration>>Printing

and click new printer and follow the instructions.

If your printer is not listed or you would still like to install the driver from the Samsung website then let us know and I am sure we can help. :)

---

### Post by kansasnoob on 2010-01-08
See if this is helpful:

[https://bugs.launchpad.net/ubuntu/+bug/306004](https://bugs.launchpad.net/ubuntu/+bug/306004)

Specifically:

> It works with Karmic (but the printer is detected as CLP-310, so it doesn't work, I have to manually select CLP-315 driver and it works).

---

### Post by simpleblue on 2010-01-08
> **mk1w86 said:**
> Chances are the driver is already included with Ubuntu.  Try installing the printer from

System>>Administration>>Printing

and click new printer and follow the instructions.

If your printer is not listed or you would still like to install the driver from the Samsung website then let us know and I am sure we can help. :)
Thank you.

I found my printer driver and installed it. I was prompted to print a test page and I selected 'yes'. The printer printed a sheet saying to install the proper driver. I tried many different time installing it.

I noticed that when I unplug and plug the printer in the status changes to offline/online. So it's reading the printer. And the printer worked fine this the other OS.

Any ideas?

---

### Post by simpleblue on 2010-01-08
> **kansasnoob said:**
> See if this is helpful:

[https://bugs.launchpad.net/ubuntu/+bug/306004](https://bugs.launchpad.net/ubuntu/+bug/306004)

Specifically:
This link had a person saying that they installed the CLP-315 instead of 310 and it solved the problem... At first somehow I had an option to pick which printer I wanted (which included the 315) and now either it's gone or I cannot find it.

How can a draw up a list of drivers to install?

Thank you all!

---

### Post by simpleblue on 2010-01-08
Got it working!!!! :P:P

I changed the printer from a CLP-310 to a CLP-315 and it worked. So if anyone has the same Samsung printer this is what to do.

Once again, thanx!

---

### Post by RINKO on 2010-01-15
> **kansasnoob said:**
> See if this is helpful:

[https://bugs.launchpad.net/ubuntu/+bug/306004](https://bugs.launchpad.net/ubuntu/+bug/306004)

Specifically:

perfect.  Thank you

---

