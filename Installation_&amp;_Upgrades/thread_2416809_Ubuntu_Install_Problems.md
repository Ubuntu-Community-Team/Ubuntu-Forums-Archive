---
title: "Ubuntu Install Problems"
date: 2019-04-15
forum: Installation &amp; Upgrades
---

### Post by aceofcarnesie on 2019-04-15
[COLOR=#000000]I am trying to install Ubuntu on an Lenovo Thinkpad Edge 15 Laptop. I am using Release 18.04 LTS Desktop Install/Live DVD fro OSDisc.com.[/COLOR]

[COLOR=#000000]The system reads the cd and then begins to install . I get several purple screens and then one asking what language I would like to use . I chose english .[/COLOR]

[COLOR=#000000]The systems seems to stop and restart it self almost indefinity . Eventually after maybe a dozen or so times , I power it off.[/COLOR]

[COLOR=#000000]I repeat the process and no joy.[/COLOR]

[COLOR=#000000]Does anyone have any guidance or help or suggestions.[/COLOR]

---

### Post by oldfred on 2019-04-15
What model, it looks like Lenovo used that general name every year but updated specs.
Or better what are specs?

---

### Post by aceofcarnesie on 2019-04-15
Edge 15 Core i3-380M, 320GB HDD, 8GB RAM .
I would think this should be sufficient. 
Does this answer your question?

---

### Post by oldfred on 2019-04-15
Should be fine, early model Intel i-series.
Have you updated UEFI/BIOS to latest available?

It seems like it is at the hard drive scan.
Do you have hard drive issues.

Use live installer in live mode & post this:
sudo parted -l
sudo fdisk -lu

---

### Post by aceofcarnesie on 2019-04-16
Thank you for the response. I would like to add some data to our discussion. I am loading ubuntu on a laptop without an OS on it . The system has just the BIOS on it  and I can easily get to it and modify it . It do not have a viable windows machine to follow the steps to create a live bootable disk. I have a bootable disk , from OSDisks.   When you say run chkdsk , how is this done on a systems like mine ? Can It be done from the BIOS?

A.

---

### Post by oldfred on 2019-04-16
If you have a live installer, you can run many commands directly from it.
If  system partially boots you often can run from second grub entry the recovery mode to get to a terminal to make repairs.
If you have a broken system, sometimes you have to chroot (CHange ROOT) into your install to make complete repairs from Live installer.
You want to always have a live installer or repair flash drive for the current version of every system you have installed.

What system is on the OSdisks?
Sometimes those are old versions, often better to just download the current LTS (Long term Suport) version of Ubuntu directly.

---

### Post by slickymaster on 2019-04-18
Closed thread.

Duplicate [here]("https://ubuntuforums.org/showthread.php?t=2416575").

---

