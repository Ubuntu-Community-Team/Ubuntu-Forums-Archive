---
title: "Ubuntu 20.04 desktop automated install"
date: 2020-07-04
forum: Installation &amp; Upgrades
---

### Post by Tigera on 2020-07-04
I am working on setting up a repeatable desktop installation for benchmarking and I'd like to automate the installation of desktop Ubuntu 20.04 on bare metal.  I've been doing some Googling and I'm trying to figure out the best way of doing an unattended installation.  Here's what I've found so far:

[How to preseed Ubuntu 20.04 Desktop]("https://askubuntu.com/questions/1233454/how-to-preseed-ubuntu-20-04-desktop")
[Preseeding an Ubuntu 20.04 Desktop with Netboot]("https://ubuntuforums.org/showthread.php?t=2440974&highlight=preseed")
[Installing Ubuntu on a VM using PXE]("https://askubuntu.com/questions/1238070/deploy-ubuntu-20-04-on-bare-metal-or-virtualbox-vm-by-pxelinux-cloud-init-doesn")

All of these methods have their downsides.  It looks like the Desktop install is using preseeding, but the server install is using cloud-init.  If I use the cloud-init method, then is that going to be as "authentic" of a benchmark as if someone installed from the Desktop distribution?  If I use the PXE method, then how do I set up the netboot entry, since there seems to be no netboot image for Focal?  The post doesn't explain how to do it very well.

I could use Cobbler too, but again, there's no Focal netboot image.  It just takes you to a page that explains how to do the live server installation.

Anyone else doing automated installations on bare metal of 20.04?  Which method was the easiest, and where can I look to set it up?

TIA.

---

### Post by Tigera on 2020-07-05
I was able to figure out how to use preseeding in the Ubuntu installer.  The trick was to pass the option:
```
"automatic-ubiquity"
``` 
as part of the kernel command line parameters as part of the installation.  Unlike what the documentation states, "auto" alone won't work.  I was also able to create a new CD image by using [Cubic]("https://launchpad.net/cubic"), which has an easy-to-use wizard to generate a new USB/DVD image, so I can just put the image on a USB key, plug it in, and do the job.

Some other notes to those who may stumble upon this in the future...

1. In the example-preseed.txt file from the documentation, the command to avoid a reboot is: 

```
d-i finish-install/reboot_in_progress note
```

But this doesn't work.  You have to use:
```
d-i ubiquity/reboot boolean true
```

AND set the "noprompt" option on the command line to avoid the prompt that reboots the PC at the end of the installation.

2. If you're using QEMU like I am to test the automated installation, make sure you have your hard disk interface set to "SATA" or the installer won't be able to partition the disk automatically.  The example has the option "d-i partman-auto/disk string /dev/sda" which is expecting to find a SATA or SCSI disk; VirtIO disks won't be detected.

3. On first boot, the installer still asks questions about whether you want to have usage data sent to Canonical, hooking up your cloud accounts, etc.  I haven't figured out how to avoid that yet.

---

