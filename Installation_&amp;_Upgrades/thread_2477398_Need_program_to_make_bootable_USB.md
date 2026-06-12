---
title: "Need program to make bootable USB"
date: 2022-07-23
forum: Installation &amp; Upgrades
---

### Post by Autodave on 2022-07-23
Wanting to put 22.04 onto machine.  tried from disk, but still clunking away after 15 minutes with nothing on screen now.  mkusb said that it installed, but not in list of programs.  What else can I try?

---

### Post by TheFu on 2022-07-23
I use cp.  Simple, effective, easy to remember.  Anything that will slam bits from A ---> B unmolested can be used.  cat, cp, more, or the any other program will work.

```
$ sudo cp /path/to/ubuntu.iso  /dev/sdZ
```
Obviously, sdZ needs to be correct and should be the device file for the entire USB storage ... which should not be mounted. No pre-format is needed, since the ISO has all the formatting embedded already.

Lots of people use dd, ddrescue, etcher, mkusb, rufus,  ventoy ... there must be 20 others.  Of all those, I like ventoy because once it is setup, just dropping an ISO file into a specific directory on the USB drive will make it available to install/boot from that ISO.  I think ventoy created 3-4 different partitions, each can have a specific file system type, depending on the purpose.  Ventoy seems to have issues with TPM chips and their implementation to support it about a month ago was less than seamless.  I'd expect others to have the same issue if they are as flexible.

---

### Post by Autodave on 2022-07-23
OK....will try one of those other programs.  Let me add something here that may be creating a problem:

I currently have Win10 on one SSD and Xubuntu 20.04 on another SSD.  What I really want to do is to remove the SSD with Xubuntu on it, install a new blank SSD, boot the machine and install Linux on the blank SSD.  You see any issues that I might have in doing that?

---

### Post by TheFu on 2022-07-23
I stopped dual booking around 2009.  Just too many hassles and when MSFT updated the boot and broke Linux, I'd had enough. Sorry.
Windows is on a 13 yr old laptop that gets booked 2x a year or inside a virtual machine for weekly financial program needs.

---

### Post by deadflowr on 2022-07-23
> **Autodave said:**
> Wanting to put 22.04 onto machine.  tried from disk, but still clunking away after 15 minutes with nothing on screen now.  mkusb said that it installed, but not in list of programs.  What else can I try?

This is likely because of this on-going bug: [https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1930880]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/1930880")
Which is mentioned in the main [22.04 release notes]("https://discourse.ubuntu.com/t/jammy-jellyfish-release-notes/24668"): Under the section for known issues/ Ubuntu Desktop.
The suggested fix is to set the boot parameter option fsck.mode=skip which should allow it to boot correctly.

I do see mentions in the bug report of it affecting other flavors such as Xubuntu and Kubuntu.
So seems likely it affects you too, in this case.

---

### Post by sudodus on 2022-07-23
If you used **cloning** in mkusb, after helping you get the correct target device it is doing exactly what the other cloning programs do, copy each byte from the iso file to the device. It is a very robust process, so I am rather sure that you have another problem, either settings in the UEFI/BIOS system or a hardware problem or a compatibility problem. (The hardware problem might be that the USB pendrive is old and tired, might be improved by wiping the whole device (by writing zero-bytes to it)).

I know that you are a very experienced user, and I think it will not be easy to solve a problem that you could not solve yourself. For that reason I suggest that you help us understand your computer by running the Ubuntu Forum's [system-info](https://github.com/UbuntuForums/system-info/) script from an Ubuntu based system, that is working there, either an installed system or a live system (older than 22.04 LTS). Let it upload the result to a pastebin and post a link to it.

---

### Post by Autodave on 2022-07-24
Thank you sudodus.  I went to that link and read.  And read.  And read again.  And I still have no idea what to do.  Sigh.  Evidently, I am not near as experienced that you hoped I was! :-)  I did read the bug report that deadflower posted and that is exactly what I was getting, so I guess I will just wait for the next release and try that to see what happens.  I will also try booting from a USB rather than a DVD and see if that helps any.

---

### Post by sudodus on 2022-07-25
If you upload the result file from the **[FONT=Courier New]system-info[/FONT]** script to a pastebin it will be cleaned from sensitive information. And then there are several persons here, who might find something useful to help you solve the problem. So even if you and I can't do it, there is still a chance.

[hr][/hr]
Did you add the boot parameter option **[FONT=Courier New]fsck.mode=skip[/FONT]** to the 'linux line', when in the grub menu? If not please try it.

---

