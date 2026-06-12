---
title: "Disk Controller Drivers for IBM x3200 ServeRAID M1015"
date: 2010-06-11
forum: Installation &amp; Upgrades
---

### Post by RedGrittyBrick on 2010-06-11
I want to install Ubuntu Server 10 (32-bit) on an IBM x3200 M3 7328K3G with the IBM ServeRaid M1015 SAS/SATA controller. The IBM configuration utilities suggest this is based on LSI MegaRaid and show a SAS 300 GBG JBOD disk in slot 0. JBOD = usable but non-RAID configuration I believe. 

Ubuntu installer can't detect the disk. I've tried the four MegaRaid driver options (megaraid, megaraid_sas, megaraid_mbx, megaraid_mm) as well as mptsas and ips. They generally just return to the driver list after a second or so.

IBM only support RedHat & SUSE but I note Ubuntu has x3200 as "validated" - but with no notes about controller or drivers.

Any suggestions?

---

### Post by blind0wl on 2010-06-24
Did you have any success with this?  I'm sort of in the same boat with a IBM x3250 M2 blade that runs the LSI 1064E Controller.  I have also tried the megaraid options with no success :(

---

### Post by gator on 2010-06-28
we have an ibm x3650 with the same sas card and can confirm that meerkat does detect it properly. The new system will not boot into grub event though it install correctly. I think it has to do with the fact that the bootable flag could not be set in the installer. It will boot from the HD if you use the dvd to bootstrap it. The LSI virtual disks are detected within meerkat.

---

### Post by RedGrittyBrick on 2010-06-30
CentOS 5.5 liveCD boots OK and can see the disks, partition & format them OK. So I'm now more sure it is a driver issue (previously I was struggling to configure the RAID controller for a single disk as JBOD and wasn't sure if I had a working disk controller configuration)

I was trying to install Ubuntu Server 10.04, the 32-bit version as I have a 32-bit app I want to use. If Meerkat works I guess I need the mfi driver (MegaRAID-SAS) from the 32-bit version of 10.10 Alpha 1 - right?

Where can I download just that driver?

Presumably I can load this from a USB memory stick at the point in the install where I am asked to choose a driver - is this correct?

---

### Post by pjamrisk on 2010-09-09
Hello there!
The easiest solution at this time, specially with MegaRAID 9240-8i which is the M1015 is to compile the driver they have at their website from source on ubuntu 10.04.
I am adding the attached 64 bit driver for your convenience so you can download it, and simply copy it over in a console via a fresh install to /lib/modules/kernelversion/kernel/drivers/scsi/megaraid
Then go ahead and do the disk detection and it should work like Magic. 
It took me several hours to get to that point, since the compiled driver they have on their website is for 9.10 only.

If you have any questions, just check the source file documentation from LSI
[http://www.lsi.com/storage_home/products_home/internal_raid/megaraid_sas/entry_line/megaraid_sas_9240-8i/index.html](http://www.lsi.com/storage_home/products_home/internal_raid/megaraid_sas/entry_line/megaraid_sas_9240-8i/index.html)

The following link I used to compile the driver
[http://www.tuxyturvy.com/blog/index.php?/archives/4-Installing-RHEL4-on-Systems-with-Legacy-Megaraid-Drivers.html](http://www.tuxyturvy.com/blog/index.php?/archives/4-Installing-RHEL4-on-Systems-with-Legacy-Megaraid-Drivers.html)

The only thing it will change is the fact you are doing in an ubuntu machine.
They have everything over there. as well for the other models people are asking around.

Now I did not try to compile the newest driver that they provide for RHLE, but is my guess that is should not give you any troubles and work just fine.
I believe this post should be Pinned or something because there was a lot of people asking the same question.

Have a great one,
Patrick Jamriska

PD: I think the driver should work on either 32 or 64 bit, but don't take my word on that, because of the architecture it was compiled on.

---

### Post by kawoel on 2010-09-26
i have an ibm x3200 m3 server raid m1015, i've been successfully installed with ubuntu server 9.10, very stable and no error message.

i'd use the package driver named 'server configuration DVD' to configure the raid controller, just follow the step, until formatting HDD step but not to install OS.

after that was done, then press exit to reboot system, insert ubuntu server 9.10 cd/dvd, let the server booting from cd/dvd rom, after that.... select check cdrom integrity to check defect, but press cancel when checking of all files (this is the way to avoid "no cd rom ...bla...bla..."), then the machine will reboot automatically.... and continue with normal installation..... .....

---

### Post by webappl on 2010-09-29
> **pjamrisk said:**
> Hello there!
The easiest solution at this time, specially with MegaRAID 9240-8i which is the M1015 is to compile the driver they have at their website from source on ubuntu 10.04.
I am adding the attached 64 bit driver for your convenience so you can download it, and simply copy it over in a console via a fresh install to /lib/modules/kernelversion/kernel/drivers/scsi/megaraid
Then go ahead and do the disk detection and it should work like Magic. 
It took me several hours to get to that point, since the compiled driver they have on their website is for 9.10 only.

If you have any questions, just check the source file documentation from LSI
[http://www.lsi.com/storage_home/products_home/internal_raid/megaraid_sas/entry_line/megaraid_sas_9240-8i/index.html](http://www.lsi.com/storage_home/products_home/internal_raid/megaraid_sas/entry_line/megaraid_sas_9240-8i/index.html)

The following link I used to compile the driver
[http://www.tuxyturvy.com/blog/index.php?/archives/4-Installing-RHEL4-on-Systems-with-Legacy-Megaraid-Drivers.html](http://www.tuxyturvy.com/blog/index.php?/archives/4-Installing-RHEL4-on-Systems-with-Legacy-Megaraid-Drivers.html)

The only thing it will change is the fact you are doing in an ubuntu machine.
They have everything over there. as well for the other models people are asking around.

Now I did not try to compile the newest driver that they provide for RHLE, but is my guess that is should not give you any troubles and work just fine.
I believe this post should be Pinned or something because there was a lot of people asking the same question.

Have a great one,
Patrick Jamriska

PD: I think the driver should work on either 32 or 64 bit, but don't take my word on that, because of the architecture it was compiled on.

I downloaded LSISAS2008 source file for RHEL5 from LSI website, unpack and compiled with the command

```
make -C /lib/modules/$(uname -r)/build M=`pwd`
```

However, I encountered the following error log

/tmp/mpt2sas/mpt2sas_scsih.c: In function ‘_scsih_change_queue_depth’:
/tmp/mpt2sas/mpt2sas_scsih.c:1318: error: ‘SCSI_QDEPTH_DEFAULT’ undeclared (first use in this function)
/tmp/mpt2sas/mpt2sas_scsih.c:1318: error: (Each undeclared identifier is reported only once
/tmp/mpt2sas/mpt2sas_scsih.c:1318: error: for each function it appears in.)
/tmp/mpt2sas/mpt2sas_scsih.c:1318: error: ‘SCSI_QDEPTH_RAMP_UP’ undeclared (first use in this function)
/tmp/mpt2sas/mpt2sas_scsih.c:1320: error: ‘SCSI_QDEPTH_QFULL’ undeclared (first use in this function)
/tmp/mpt2sas/mpt2sas_scsih.c: In function ‘_scsih_set_sdev_queue_depth’:
/tmp/mpt2sas/mpt2sas_scsih.c:1438: error: ‘SCSI_QDEPTH_DEFAULT’ undeclared (first use in this function)
/tmp/mpt2sas/mpt2sas_scsih.c: In function ‘_scsih_slave_configure’:
/tmp/mpt2sas/mpt2sas_scsih.c:2083: error: ‘SCSI_QDEPTH_DEFAULT’ undeclared (first use in this function)
/tmp/mpt2sas/mpt2sas_scsih.c: At top level:
/tmp/mpt2sas/mpt2sas_scsih.c:8496: warning: initialization from incompatible pointer type
make[1]: *** [/tmp/mpt2sas/mpt2sas_scsih.o] Error 1
make: *** [_module_/tmp/mpt2sas] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'

Does anybody know how to solve the problem?

---

### Post by webappl on 2010-09-29
I also tried compiling source file downloaded from IBM website for my ServeRAID M1015 card. Now the error log becomes:

/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c: In function &#8216;megasas_make_sgl_skinny&#8217;:
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:729: error: &#8216;struct scsi_cmnd&#8217; has no member named &#8216;request_buffer&#8217;
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:729: error: &#8216;struct scsi_cmnd&#8217; has no member named &#8216;request_bufflen&#8217;
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:732: error: &#8216;struct scsi_cmnd&#8217; has no member named &#8216;use_sg&#8217;
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:735: error: &#8216;struct scsi_cmnd&#8217; has no member named &#8216;request_buffer&#8217;
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:737: error: &#8216;struct scsi_cmnd&#8217; has no member named &#8216;request_bufflen&#8217;
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:741: error: &#8216;struct scsi_cmnd&#8217; has no member named &#8216;request_bufflen&#8217;
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:746: error: &#8216;struct scsi_cmnd&#8217; has no member named &#8216;request_buffer&#8217;
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:747: error: &#8216;struct scsi_cmnd&#8217; has no member named &#8216;use_sg&#8217;
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c: In function &#8216;megasas
_build_dcdb&#8217;:
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:872: error: &#8216;struct scsi_cmnd&#8217; has no member named &#8216;timeout_per_command&#8217;
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:875: error: &#8216;struct scsi_cmnd&#8217; has no member named &#8216;timeout_per_command&#8217;
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c: In function &#8216;megasas_build_ldio&#8217;:
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:930: error: &#8216;mfi_flag&#8217; undeclared (first use in this function)
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:930: error: (Each undeclared identifier is reported only once
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:930: error: for each function it appears in.)
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:930: error: &#8216;flag&#8217; undeclared (first use in this function)
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:933: error: &#8216;ldio&#8217; undeclared (first use in this function)
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c: In function &#8216;megasas_slave_configure&#8217;:
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:1219: error: implicit declaration of function &#8216;megasas_lookup_instance&#8217;
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:1219: warning: assignment makes pointer from integer without a cast
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:1232: error: &#8216;struct
scsi_device&#8217; has no member named &#8216;timeout&#8217;
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c: In function &#8216;megasas_service_aen&#8217;:
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:1543: warning: ISO C90 forbids mixed declarations and code
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:1549: warning: assignment from incompatible pointer type
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:1550: warning: passing argument 1 of &#8216;schedule_delayed_work&#8217; from incompatible pointer type
include/linux/workqueue.h:214: note: expected &#8216;struct delayed_work *&#8217; but argument is of type &#8216;struct work_struct *&#8217;
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c: In function &#8216;megasas_slave_alloc&#8217;:
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:1558: error: &#8216;fast_load&#8217; undeclared (first use in this function)
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:1559: warning: assignment makes pointer from integer without a cast
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c: In function &#8216;megasas_probe_one&#8217;:
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:3100: error: expected &#8216;;&#8217; before &#8216;megasas_poll_wait_aen&#8217;
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c: At top level:
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:3743: error: conflict
ing types for &#8216;megasas_lookup_instance&#8217;
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:1219: note: previous implicit declaration of &#8216;megasas_lookup_instance&#8217; was here
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:4048: error: conflicting types for &#8216;megasas_aen_polling&#8217;
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:1506: note: previous declaration of &#8216;megasas_aen_polling&#8217; was here
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c: In function &#8216;megasas_aen_polling&#8217;:
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:4227: warning: passing argument 1 of &#8216;down&#8217; from incompatible pointer type
include/linux/semaphore.h:42: note: expected &#8216;struct semaphore *&#8217; but argument is of type &#8216;struct mutex *&#8217;
/tmp/megaraid_sas-00.00.04.17/megaraid_sas.c:4232: warning: passing argument 1 of &#8216;up&#8217; from incompatible pointer type
include/linux/semaphore.h:47: note: expected &#8216;struct semaphore *&#8217; but argument is of type &#8216;struct mutex *&#8217;
make[1]: *** [/tmp/megaraid_sas-00.00.04.17/megaraid_sas.o] Error 1
make: *** [_module_/tmp/megaraid_sas-00.00.04.17] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.32-25-generic'

Does anybody know where I can find a valid source code for Ubuntu?
Thanks.

---

### Post by Rismi on 2010-09-29
Hi all,

I'm trying to install Ubuntu Server 10.04.1 64 bit on an X3650 M3 with the LSI M1015 controller without success.... :(
Following Pjamrisk suggestions I've replaced the megaraid_sas.ko module obtaining a module format error....
Than I've done some attempt with the Ubuntu 10 versions from LSI ( MegaRaid SAS 9240-8 version) with a different insuccess, like: Megaraid_sas: disagrees about version of symbol module_layout.
No way to make the controller visible to the install menu.
Please, (many please!) does anybody have a suggestion to cross the river ?

Thanks a lot in advance !!!!

---

### Post by webappl on 2010-09-29
> **Rismi said:**
> Hi all,

I'm trying to install Ubuntu Server 10.04.1 64 bit on an X3650 M3 with the LSI M1015 controller without success.... :(
Following Pjamrisk suggestions I've replaced the megaraid_sas.ko module obtaining a module format error....
Than I've done some attempt with the Ubuntu 10 versions from LSI ( MegaRaid SAS 9240-8 version) with a different insuccess, like: Megaraid_sas: disagrees about version of symbol module_layout.
No way to make the controller visible to the install menu.
Please, (many please!) does anybody have a suggestion to cross the river ?

Thanks a lot in advance !!!!

The driver file provided by pjamrisk isn't working for my IBM x3550 M3 with ServeRAID M1015 card.

---

### Post by pjamrisk on 2010-09-29
Sorry for the late reply. I went over to the LSI website and they already posted new drivers and re-compiled kernels for almost every version of linux (at least the most used ones including ubuntu 10.04lts). I downloaded the driver and tried on our server by following the included instructions in the driver and it worked out of the box.
If you guys still have problems, post a reply and i'll try to reply back ASAP and help you troubleshoot your problem

Patrick

---

### Post by Rismi on 2010-09-29
> **pjamrisk said:**
> Sorry for the late reply. I went over to the LSI website and they already posted new drivers and re-compiled kernels for almost every version of linux (at least the most used ones including ubuntu 10.04lts). I downloaded the driver and tried on our server by following the included instructions in the driver and it worked out of the box.
If you guys still have problems, post a reply and i'll try to reply back ASAP and help you troubleshoot your problem

Patrick

Hi Patrick,

I'm booting the latest Ubuntu server (64 bit) ISO and I've done a try, following LSI instuctions, with the Ubuntu 10 megaraid_sas.ko version from LSI (  MegaRaid SAS 9240-8) with another insuccess, like:  Megaraid_sas: disagrees about version of symbol module_layout. The main difference is that LSI refer its driver to the kernel 2.6.32-21 version while actual Ubuntu is 2.6.32-24.


Panic !!!!

Thanks everybody for any help .

Pino.

---

### Post by pjamrisk on 2010-09-29
Sounds like you are installing 10.04.1 LTS. That had some stuff fixed, and AFAIK the lsi drivers have not been recompiled with that kernel yet. Just download the previous LTS version of ubuntu that contains the previous Kernel and you should be good to go and do the initial installation. Now don't be doing updates on the server kernel modules if you don't have to.
The other thing you can do is use the source code on the driver, and compile it on a 64bit machine and recompile the kernel image as well, and then do the 64bit installation following the LSI steps.
I don't know what to tell you guys, but it is not that hard. We have our server running already for 4 weeks with no problems, and I did the install before they posted the recompiled kernel and driver.

I am going to search around for instructions on kernel recompilation so you guys can create a driver with the newest kernel, or I might end up doing it if I get some spare time, but no promises since I am on a project deadline right now.
Patrick

---

### Post by webappl on 2010-09-30
Strange thing occurs. 

The IBM website says ServeRAID M1015 controller uses LSI SAS2008 raid chip ([http://www.redbooks.ibm.com/abstracts/tips0740.html](http://www.redbooks.ibm.com/abstracts/tips0740.html))
However, after installing CentOS5.5 system, which is able to detect the hard disks, the raid controller is recognized as LSI MegaRaid 9240. pjamrisk's post also indicated M1015 to be MegaRAID 9240-8i chip. Unfortunately, the MegaRAID 9240-8i driver for ubuntu is not working with our M1015 controller.

---

### Post by Staffan Ericsson on 2010-10-03
> **webappl said:**
> Strange thing occurs. 

The IBM website says ServeRAID M1015 controller uses LSI SAS2008 raid chip ([http://www.redbooks.ibm.com/abstracts/tips0740.html](http://www.redbooks.ibm.com/abstracts/tips0740.html))
However, after installing CentOS5.5 system, which is able to detect the hard disks, the raid controller is recognized as LSI MegaRaid 9240. pjamrisk's post also indicated M1015 to be MegaRAID 9240-8i chip. Unfortunately, the MegaRAID 9240-8i driver for ubuntu is not working with our M1015 controller.

There is no support yet in Ubuntu for LSI 9240 series yet. LSI has released drivers for 10.04 and bug [#546091]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546091") is making progress. To my understanding the patch for providing support for LSI's SAS2 boards is about to be integrated in the 10.04 kernel package. 

There is probably some subtle differences between M1015 and the stock LSI 9240 boards. Exactly what is still to be investigated. 

.staffan

---

### Post by mtbdrew on 2010-11-09
> **Staffan Ericsson said:**
> There is no support yet in Ubuntu for LSI 9240 series yet. LSI has released drivers for 10.04 and bug [#546091]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546091") is making progress. To my understanding the patch for providing support for LSI's SAS2 boards is about to be integrated in the 10.04 kernel package. 

There is probably some subtle differences between M1015 and the stock LSI 9240 boards. Exactly what is still to be investigated. 

.staffan

Same issue with the IBM x3650T and Ubuntu 10.10, funny thing is 9.10 works fine.

---

### Post by x751 on 2010-11-19
> **mtbdrew said:**
> Same issue with the IBM x3650T and Ubuntu 10.10, funny thing is 9.10 works fine.

I tried  installing 9.10 on 3650T a couple of days back and it failed to boot. I tried even Meerkat and that too didn't work.

Is there any other Linux distro version which is as simple as "download the iso, burn it, install it" for this old machine? OR is there something that I am missing while installing Ubuntu?

---

### Post by pjamrisk on 2010-11-19
Try the SLI website and get the compiled driver and Kernel. We have the source code and recompiled the kernel with it. I find out #ubuntu on IRC is great help if you don't know how to do it. Those guys know a lot when you don't and they usually can send you to the right links as well.
But getting it to work out of the box, I have not seen it yet. I guess we could add that to launchpad as a request and hope that the new update of ubuntu will have those drivers incorporated on the kernel for these raid cards to boot normally. I might do the post of it today.

---

### Post by needhelpplease on 2010-11-28
> **webappl said:**
> Strange thing occurs. 

The IBM website says ServeRAID M1015 controller uses LSI SAS2008 raid chip ([http://www.redbooks.ibm.com/abstracts/tips0740.html](http://www.redbooks.ibm.com/abstracts/tips0740.html))
However, after installing CentOS5.5 system, which is able to detect the hard disks, the raid controller is recognized as LSI MegaRaid 9240. pjamrisk's post also indicated M1015 to be MegaRAID 9240-8i chip. Unfortunately, the MegaRAID 9240-8i driver for ubuntu is not working with our M1015 controller.

I'm having exactly the same problem.  I bought a new X3550 M3 and was excited to get Ubuntu on it.  After much scratching of my head, I finally found this thread and also Bug #546091 and the driver download on the LSI site.  I downloaded a copy of the Ubuntu 64 bit 10.04 (original, not .04.01) and went through LSI's instructions several times.  No success.  According to the BIOS I have an M1015 card, which I guess is not identical to the 9240, and LSI's driver download doesn't work and IBM doesn't seem to care.

This is really really frustrating.  I've spent several days on this.  Should I just return the whole thing, and choose some other server?  When can we expect a way to install on this machine?

Given how Linux-oriented IBM is these days, and given that Ubuntu is the #1 Linux distro, you would think this kind of thing wouldn't happen and the server would "just work".

---

### Post by needhelpplease on 2010-12-08
Any updates on this?  I've been checking the [Lucid daily builds location]("http://cdimage.ubuntu.com/ubuntu-server/lucid/daily/") and there are no updates since Nov. 24, and that ISO doesn't work.  I hope I don't have to wait until February to get this server installed....  I'm somewhat tempted to try to install Natty Narwhal alpha 1.

---

### Post by needhelpplease on 2010-12-12
Any updates?  Any word on when there will be an ISO we can use?  If I signed up for Ubuntu enterprise support, could they roll me an ISO?

---

### Post by amtzone on 2010-12-13
> **needhelpplease said:**
> Any updates on this?  I've been checking the [Lucid daily builds location]("http://cdimage.ubuntu.com/ubuntu-server/lucid/daily/") and there are no updates since Nov. 24, and that ISO doesn't work.  I hope I don't have to wait until February to get this server installed....  I'm somewhat tempted to try to install Natty Narwhal alpha 1.

hello....i also have the same problems...tried about a week until now still cannot install ubuntu server on the IBM x3650 m3 server.....i found the critical update at the IBM site....but dont really know how to execute it....they really doesnt show how to update the driver or give a driver....dont know what to say about the IBM....so frusterating....

---

### Post by needhelpplease on 2010-12-13
> **amtzone said:**
> hello....i also have the same problems...tried about a week until now still cannot install ubuntu server on the IBM x3650 m3 server.....i found the critical update at the IBM site....but dont really know how to execute it....they really doesnt show how to update the driver or give a driver....dont know what to say about the IBM....so frusterating....

It's very frustrating, I have a brand new X3550 sitting here collecting dust at the moment.

Why don't you go over to the [bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546091"), log in, and also post a comment on that.  I'm sure this thing is impacting a lot of people.

---

### Post by needhelpplease on 2010-12-15
Any updates on this?  We've had this new M3 sitting here for quite a while now.  What can we do to get it working?  I know that Centos 6 will support it and will be out in about a month.

I found another post describing a "successful" method to [get the install to work]("http://tuxteam.com/2010/11/17/1-os-2-servers-5-days/"), but it sounds painful and like it might not work reliably and will require days of messing around.  All to get one standard IBM server to boot into Ubuntu.

---

### Post by amtzone on 2010-12-16
> **needhelpplease said:**
> Any updates on this?  We've had this new M3 sitting here for quite a while now.  What can we do to get it working?  I know that Centos 6 will support it and will be out in about a month.

I found another post describing a "successful" method to [get the install to work]("http://tuxteam.com/2010/11/17/1-os-2-servers-5-days/"), but it sounds painful and like it might not work reliably and will require days of messing around.  All to get one standard IBM server to boot into Ubuntu.


I tried using the ubuntu 10.10 looks like it works....but still the company wanted to use 10.04.....so im all blurred out right now....until now about a weeks i been searching for the solution.....still no luck.....give me a headache...**[COLOR=Red]IBM[/COLOR] **make me suffers.....:roll:

---

### Post by needhelpplease on 2010-12-21
Any updates on this?  My server is sitting here collecting dust.  I have contacted my vendor and told them I want to return the whole thing.  I have blown a lot of time and effort trying to get this to work, and I'm still left without an operational server.  My vendor's comment was to "see the list of supported OSes" which include such winners as SCO Unix, Novel Netware and so on.  No thanks, I'll consider it a lesson learned, return the hardware, and choose some other vendor next time.

---

### Post by amtzone on 2010-12-22
i finally finished install the ubuntu OS, but the last step is to **[COLOR=Red]chroot[/COLOR]** i really dont understand also with the **[COLOR=Red]mkinitrd[/COLOR]** also cannot be done.....so after i finished all installation and i restarted the server it **[COLOR=Blue]blank[/COLOR]**....i think the megaraid drivers still not merge with the OS...also the boot problems....anyone know about how to change the boot from **[COLOR=SeaGreen]sda1[/COLOR]** to **[COLOR=SeaGreen]sdb1[/COLOR]**?and if someone manage to solve this puzzle let me know please....the clock is ticking.....

---

### Post by holch on 2011-03-31
Are there any news on this one?

I was thinking of buying one of those IBM x3200 M3, as the price is pretty OK, they offer 3 years of onsite warranty and the specifications look pretty good to me.

I wanted to install Ubuntu as the OS (or Zentyal - aka Ebox).

I use Ubuntu on my private desktop, but I am not a Linux crack and I rather avoid the console if I can.

Now I am a little worried that Ubuntu wouldn't run on the system. I can't afford to buy a server (IT stuff is pretty expensive here in Brazil) and than not be able to install Ubuntu and maybe even have to buy Windows Server...

Has anything changed since December? Is the newest version running? Would you recommend buying this hardware, or rather not? Alternative would only be a HP Proliant ML110, which is more or less the same price, but:
- less memory possible
- Harddiscs non-hotswap
- only one network adapter
- only 1 year of warranty

So in general you get a lot less for your money.

I need it as a file server to share documents in a small office and maybe have some applications running on it, like Asterisk/Trixbox and a webbased Groupware/CRM tool. Nothing heavy though. Maximum users at the moment 5.

---

### Post by uberDoward on 2011-05-14
I can say that CentOS 5.6 AMD64 LiveCD will see the M1015 in the x3200 we have here.

---

### Post by uberDoward on 2011-06-17
Considering this is the main link that Google comes up with, just thought I'd let you guys know I'm testing Gentoo's newest install CD, OpenSUSE 11.4, and Zentyal 2.1 Beta tonight on my overnight shift.

---

### Post by CX23882 on 2011-11-06
I have a Ubuntu 10.04.3 server up and running with a combination of a 2 port AHCI PCIe controller and a 4 port SiI PCI controller. I would like to replace these two cards with one M1015 to free up a slot.

The version of megaraid_sas included with Ubuntu is 4.01. I downloaded the 5.30 driver package from the LSI website, and then built the driver and copied it into /lib/modules/<kernel>/drivers/scsi/megaraid (overwriting the old version) and rebuilt initramfs.

'modinfo megaraid_sas' now gives:
```
filename:       /lib/modules/2.6.32-33-generic-phc/kernel/drivers/scsi/megaraid/megaraid_sas.ko
description:    LSI MegaRAID SAS Driver
author:         megaraidlinux@lsi.com
version:        00.00.05.30
license:        GPL
srcversion:     374D3479F2895D988397E92
alias:          pci:v00001000d0000005Bsv*sd*bc*sc*i*
alias:          pci:v00001028d00000015sv*sd*bc*sc*i*
alias:          pci:v00001000d00000413sv*sd*bc*sc*i*
alias:          pci:v00001000d00000071sv*sd*bc*sc*i*
alias:          pci:v00001000d00000073sv*sd*bc*sc*i*
alias:          pci:v00001000d00000079sv*sd*bc*sc*i*
alias:          pci:v00001000d00000078sv*sd*bc*sc*i*
alias:          pci:v00001000d0000007Csv*sd*bc*sc*i*
alias:          pci:v00001000d00000060sv*sd*bc*sc*i*
alias:          pci:v00001000d00000411sv*sd*bc*sc*i*
depends:        
vermagic:       2.6.32-33-generic-phc SMP mod_unload modversions 
parm:           poll_mode_io:Complete cmds from IO path, (default=0) (int)
parm:           max_sectors:Maximum number of sectors per IO command (int)
parm:           msix_disable:Disable MSI-X interrupt handling. Default: 0 (int)
```

Unfortunately, it still is not working. lspci lists the LSI card, but the controller doesn't appear in Disk Utility at all, nor do any disks attached to it appear for mounting. megaraid_sas is being loaded when the card is installed in the system.

Furthermore, the system appears to misbehave somewhat with the card installed. Upon booting, rather than starting X automatically, I am given a console login prompt. I can enter my username/pass and then type startx and the system appears to run properly, except shutdown freezes. If I take the card out, bootup and shutdown work as normal.

Any ideas guys?

Edit: Looks like in my case the issue is a motherboard compatibility issue. I don't ever get to see the M1015's POST message. Tried the card in another motherboard and it appears fine.

---

### Post by pjamrisk on 2011-11-06
Hi there,
Check what version of ubuntu the driver is made for. I remember last time I had to rebuild the server I had to deal with that, and as soon as I updated the kernel, the driver completely stopped working. Mind you, the version I had it working for was 10.4.0, the very first one.
So check on that and it might get you going. It is sad that Ubuntu has not included a base driver for LSI to have it working Directly and not have to worry about doing updates in that sense.
I know for a fact our server was never Kernel Updated, but since it is in the datacenter, and we only use it internally we do not worry much about updating it until a new full revision comes out, and we know it is fully supported.

---

### Post by netuntu on 2011-12-29
Hi there

My company just buy a xSeries 3550 M3 7944, and have the same ServerRaid M1015 installed that you have guys, this xSeries has the new uEFI v1.3 and i wanna know how can go into the BIOS of this ServerRAID controller to make a RAID 5 at hardware level!

I need to do this because i recommended this server configuration and i just want to install Ubuntu Server 11.10.

I'll appreciate any help!!

Thanks in advance

Netitux

---

### Post by zedstrange on 2012-03-28
> **kawoel said:**
> i'd use the package driver named 'server configuration DVD' to configure the raid controller, just follow the step, until formatting HDD step but not to install OS.

This sounds like a great idea, I would like to do that, but what exactly is "server configuration DVD" and where do I get that?

I have downloaded IBM Server Guide 8.50, but that only sets up for Windows OS

---

### Post by Zerocool3001 on 2012-07-09
Any updates on how to get an install working on a X3550 M3 with UEFI? Some step by step instructions for getting the RAID controllers working during the install would be great.

Edit: Added to bug: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546091](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/546091)

---

### Post by Zerocool3001 on 2012-07-10
Used the Ubuntu 11.10 source drives provided at LSI to build for 12.04. I get the following error from the kernal version:

```
Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.2.0-23-generic -C /lib/modules/3.2.0-23-generic/build SUBDIRS=/var/lib/dkms/megaraid_sas/v00.00.05.30/build modules....(bad exit status: 2)
ERROR (dkms apport): binary package for megaraid_sas: v00.00.05.30 not found
Error! Bad return status for module build on kernel: 3.2.0-23-generic (x86_64)
Consult /var/lib/dkms/megaraid_sas/v00.00.05.30/build/make.log for more information.

```

---

