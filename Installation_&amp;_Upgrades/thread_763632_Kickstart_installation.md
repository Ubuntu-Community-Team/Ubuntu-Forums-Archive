---
title: "Kickstart installation"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by Sundlin on 2008-04-23
Hi all
To start with i'm useing Ubuntu 7.10 Desktop Edition
I need some help sorting out how to make unattended installation properly with kickstart
I got the kickstart file like it should (i think), I used the system-config-kickstart package to create it

The problem is that my installer ignores the kickstart file
when the installer-boot starts I hit F6 to get the command line and type:
ks=cdrom:/ks/ks.cfg file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet &#8211; 
or
ks=http://10.0.0.169/ubuntu/ks.cfg file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet &#8211; 

non of them works, it just starts the live CD

I would love some help with this matter, how to write the boot commands or if it&#8217;s something else I may have done wrong.

*edit* some typos

Regards
Mikael

---

### Post by Sundlin on 2008-04-25
I have not found any solution yet, anyone that can help me?

---

### Post by Sundlin on 2008-05-14
bump :popcorn:

---

### Post by Partyboi2 on 2008-05-14
reading the help file its says:
      > After saving the file, create a boot diskette from       boot.img for CD-ROM installations or       bootnet.img for network installations. Copy the       kickstart file (ks.cfg) on the boot diskette. Boot       from the diskette and type **linux ks=floppy** to       start the kickstart installation.     

---

### Post by jasoncusick on 2008-05-28
> **Sundlin said:**
> Hi all
To start with i'm useing Ubuntu 7.10 Desktop Edition
I need some help sorting out how to make unattended installation properly with kickstart
I got the kickstart file like it should (i think), I used the system-config-kickstart package to create it

The problem is that my installer ignores the kickstart file
when the installer-boot starts I hit F6 to get the command line and type:
ks=cdrom:/ks/ks.cfg file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet – 
or
ks=http://10.0.0.169/ubuntu/ks.cfg file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet – 

non of them works, it just starts the live CD

I would love some help with this matter, how to write the boot commands or if it’s something else I may have done wrong.

*edit* some typos

Regards
Mikael


You can't use the Desktop Edition to kickstart you need to use the alternate image.  

Use the following for guidance:


[http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/](http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/)

---

### Post by brucewagner on 2010-04-18
@Sundlin Did you ever get this to work?

---

