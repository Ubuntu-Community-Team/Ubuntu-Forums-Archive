---
title: "Install Issues - Infinite Pause"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by ehidle on 2011-09-21
I'm trying to install Ubuntu Server 11.04 as a guest in VMWare ESXi 5.0 with a passed-through PCI device (Marvell 88SE9123 SATA Controller). Whenever the PCI device is present in the guest configuration, the installer infinite-pauses at (won't say hang, because I can still get around and do stuff, and the VM is not locked up):

update-initramfs: Generating /boot/initrd.img-2.6.38-8-server

in the console log. 

There is also a Kernel oops during boot having to do with the ahci modules, so I feel this is probably related. 

lspci shows the Marvell controller present, and lsmod shows both the ahci and the libahci modules loaded. There are also messages in the syslog about not being able to initialize the ahci controller at the PCI address where the Marvell controller resides. 

I am certain this boils down to VMWare not doing passthrough properly for the Marvell controller, but what I am uncertain of is why the installer hangs where it does. The kernel gets through the oops just fine, and it isn't until much later in the install process that the hang occurs, so I'm just curious what might be going on at this point during the installation that is causing everything to just stop. 

I've attached images of logs: 

The end of the syslog:

[IMG]https://lh3.googleusercontent.com/-hce3Y904Sow/TnnIYy2q1hI/AAAAAAAANPc/YGtpBk5fFdY/s720/Ubuntu_Install_Hang_PCI_Passthrough_VMWare.png[/IMG]

And here's the train of ahci init failures and the kernel oops:

[IMG]https://lh5.googleusercontent.com/-6vTdPl5Al8I/TnnIY_Tsz4I/AAAAAAAANPg/1RL8sbQ53hg/s720/Ubuntu_Install_Hang_PCI_Passthrough_VMWare_2.png[/IMG]

[IMG]https://lh4.googleusercontent.com/-AtS8JRfqqI0/TnnIZhE48GI/AAAAAAAANPo/EUfgA_4AcVw/s720/Ubuntu_Install_Hang_PCI_Passthrough_VMWare_3.png[/IMG]

[IMG]https://lh6.googleusercontent.com/-IJaBGDeF2Qs/TnnIZjgmOGI/AAAAAAAANPk/R_1mg4KehlE/s720/Ubuntu_Install_Hang_PCI_Passthrough_VMWare_4.png[/IMG]

[IMG]https://lh5.googleusercontent.com/-dXjuLJOqo6s/TnnIaPyHwdI/AAAAAAAANPs/JmGu1mWvoe0/s720/Ubuntu_Install_Hang_PCI_Passthrough_VMWare_5.png[/IMG]

---

### Post by nxmehta on 2011-12-08
VMware definitely hates this controller.  I added a card after installing all my VMs that contains this Marvell 88SE9123 chip, and if I pass it through to any VM it will fail to start with a very generic message ("A general system error occurred").

If you google around you'll see that other people seem to have lots of problems with this controller.  I would try to find another card.  I hope it's not integrated into your motherboard!

---

