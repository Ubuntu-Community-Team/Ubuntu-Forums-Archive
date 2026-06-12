---
title: "Installing Ubuntu on Sandisk Exstream IV CF (using IDE to CF converter)"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by lwh on 2007-06-28
Hi all, 

I have started to play a bit with installing Ubuntu on a 8G Sandisk Exstream IV card, but I have differnt installation issues, I like some help getting solved.

The hardware i'm installing onto is a Thinkcenter desktop that has successfully worked as an workgroup / vmware server with Debian and latest Ubuntu the last 4 Years and I'm sure that it's it not defect, the CF card is mounted on the motherboard using a IDE to CF converter.

Until now I have tried different installation ways but all have more or less failed.

Ordinary I PXE install all computers, but durring the loding of initrd.gz the installation it fails,
I have tried PXE netboot installation for Dapper, edgy and feisty and it's the same issue everytime, but the installation reaches different number of dots on the screen durring the load of initrd.gz, I dont know if that means anything)

NEXT I have tried to install using a good oldfasion CD, where I'm able to get into the Installation guide and start the installation, but the install steps are running sloooow.
The best CD installation I have tried until now is using an Ubuntu Alternate  7.04 desktop install cd with the boot parm ide=nodma, the installation guide loades fast, but it also installes all the desktop packages which I dont need, aborted the installation since it's gonna become a server once again, Is there any-how possible to byparse the installation of the desktop applications?

Since the ide=nodma seams to have an effect on the CD installation did I tried to add it to the PXE installation, but it does not have any effect here, why / How-come that ?
It seams that the ide=nodma does not have an effect when i'm using the Ubuntu 7.04 Server installation CD and the server installation fails when it whats to install the driver for the CF "disk",  that driver to use?

When i'm booting without the nodma option, and removes the quiet boot option, I see some dma_timer_expiry   dma status == 0x41 errors, which in the first place was the reason why I tried the nodma option....

Does any one know where to start debugging this installation or have any clue where to look

Best Regard LWH
DENMARK

---

### Post by vta on 2007-07-03
I am interested in running Ubuntu on a laptop from a CF card to IDE card (to fit in Hard Drive Slot).  I am also interested in the above info.

Thx.

Adam
Portland, OR

---

### Post by lwh on 2007-07-06
Small Update...
Hmm. seams that the DMA stuff is a big part of the issue.

Yesterday I order a new ide-to-cf conterter, which should support DMA, and I'll have a go with this one.
I have been able to install SLES10 on the CF card using a USB Cart reader.

---

