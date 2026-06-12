---
title: "Cannot boot into windows8 after installing lubuntu next to it"
date: 2016-10-02
forum: Installation &amp; Upgrades
---

### Post by mineralwouter on 2016-10-02
Hi,

installing lubuntu for school work next to my windows8 (which I believe is an OEM installation) on my laptop. Used the regular installation steps for dual boat.

Afterwards couldn't see Windows8 in the GRUB menu so followed some tutorial using *grub-update. *This way I managed to get windows8 in the GRUB menu but when I tried to boot it it just restarted the GRUB menu.

I tried Boot-Repair. Which gave me this paste:
[http://paste.ubuntu.com/23264579/](http://paste.ubuntu.com/23264579/)

It also told me to repair bootsector of sda1. So I used TestDisk and copied backup boot to original one. Didn't fix the problem neither.

I can still see the windows system partition fine and doesn't seem anything wrong with it.

While writing this I'm preparing a windows RepairCD to see it that can help in any way.

So here I am to ask for help. Not an experienced Linux user at all so any help is appreciated.

Thanks in advance!

---

### Post by Mark Phelps on 2016-10-02
> Used the regular installation steps for dual boat.

By this, can I presume that you used the AlongSide option to shrink Win8?

If so, you probably corrupted the Windows filesystem in the process, as that is known to be a typical problem when using Linux utilities to modify Windows filesystems.

What generally is needed to fix that is repairing the Windows filesystem using CHKDSK -- but there is no Linux equivalent for this.

The Windows Repair CD generally repairs only the boot loader files, but it might work -- so continue to prepare it.

---

### Post by mineralwouter on 2016-10-02
> **Mark Phelps said:**
> By this, can I presume that you used the AlongSide option to shrink Win8?
Yes indeed. I think tutorials also recommended this method for dual boot?

> **Mark Phelps said:**
> If so, you probably corrupted the Windows filesystem in the process, as that is known to be a typical problem when using Linux utilities to modify Windows filesystems.

What generally is needed to fix that is repairing the Windows filesystem using CHKDSK -- but there is no Linux equivalent for this.

The Windows Repair CD generally repairs only the boot loader files, but it might work -- so continue to prepare it.

I used the repairdisk to *chkdsk.* While it didn't find any bad sectors it seems, it did seemingly fix the problem as after running it, using *update-grub* again it managed to get windows to boot again :)

Thanks for the help.

---

### Post by ajgreeny on 2016-10-02
Great! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

