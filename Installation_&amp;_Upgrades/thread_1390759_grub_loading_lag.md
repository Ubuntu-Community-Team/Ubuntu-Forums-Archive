---
title: "grub loading lag"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by adammw on 2010-01-26
Hi,
I recently re-installed my dead home server with Ubuntu 9.10 Server but it seems that there is a large delay loading grub, before the error  "error: no such disk"  comes up and the Ubuntu finally boots normally. I've videoed it, see what I mean at [http://www.youtube.com/watch?v=0H7hsa5QIc0](http://www.youtube.com/watch?v=0H7hsa5QIc0) .

What would be causing this error and how would I go about fixing it?

Thank you, :)

EDIT: Also, no other message or boot menu/selection appears, and I only have one hard drive installed in the machine.

---

### Post by babu38 on 2010-01-26
I too have similar problem. That is grub2 loads little late.
i have two hardisks and i installed ubuntu on slave(sdb). 
I think that the master boot record is in the master(sda)disk and i think this causes this lag. I had once made this to work ok but its little confusing. can anyone give me a easy way to correct this error.

---

### Post by darkod on 2010-01-26
> **babu38 said:**
> I too have similar problem. That is grub2 loads little late.
i have two hardisks and i installed ubuntu on slave(sdb). 
I think that the master boot record is in the master(sda)disk and i think this causes this lag. I had once made this to work ok but its little confusing. can anyone give me a easy way to correct this error.

Grub is known to take its time if it's on one disk MBR and ubuntu is on another disk. Boot your ubuntu and in terminal just execute:

sudo grub-install /dev/sdb

That will install grub2 also on the MBR of /dev/sdb. Reboot and in BIOS change the boot order of the disks so you are booting grub2 from the /dev/sdb disk.

Later if you want you can return windows MBR on /dev/sda. The easiest way is from ubuntu again. Boot it, and in terminal:

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

There will be some warnings but ignore them. This definitely works for putting windows MBR back on a hdd.

PS. Before executing any of these commands make sure you know which is /dev/sda and which /dev/sdb. :) I have used them according to what you said.

---

### Post by adammw on 2010-01-26
ok, but how about it lagging with only one hard drive... i don't get it.

---

### Post by darkod on 2010-01-26
> **adammw said:**
> ok, but how about it lagging with only one hard drive... i don't get it.

Not sure sorry. And I haven't used server at all, in fact I just started using ubuntu with the 9.10 version, rather new to it.
Surely that error has something to do with it. I haven't watched the video coz my internet is playing up, I will when I can. Maybe I'll get some idea but as I said, I'm rather new here. :)

---

### Post by meierfra. on 2010-01-26
The screens  in the first 30 seconds seems to be from your Bios. So it appears to a Bios or hardware problem.  At the very end its says "/dev/mapper". Are you using some kind of raid?

---

