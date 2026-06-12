---
title: "Can't do a dual-boot with Windows 7 and Ubuntu 12.4 LTS x 64"
date: 2012-10-08
forum: Installation &amp; Upgrades
---

### Post by Tobaloide on 2012-10-08
Hi, this is the thing. I have two HDD I have Windows 7 in "sdb" and I install Ubuntu in "sda" but its only boot windows. :confused::confused::confused:

And I have the right order to boot in the BIOS.

Thanks!

---

### Post by oldfred on 2012-10-08
Welcome to the forums.

Normally Windows is in sda & Ubuntu in sdb?

Post the link that running the BootInfo report creates:

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by varunendra on 2012-10-08
Hi oldfred!

I know what your presence means, but was too curious to keep quite :) (besides, it's very long since I learned any lessons from you..:)).

If it is actually the case as the OP mentioned, isn't it possible that Ubuntu and GRUB are in sda (from Ubuntu's point-of-view), while the BIOS is set to boot from sdb (and the OP did'n even try to change the boot order)?

If so, wouldn't it be easier to just set the BIOS to boot from the second HDD, then do an 'update-grub' from Ubuntu?

[PS:
Obviously what you asked for is no doubt the much better, elegant and sure-shot way of figuring out and also fixing it. I think what I'm just suggesting is a blind but quick shot.. :).]

---

### Post by oldfred on 2012-10-08
@varunendra
The OP says he has boot order correct. But some of the old timers here taught me that often users do not know the details of their system, so a run of the bootinfoscript was often best. 

Now with BootInfo we get a bit more info and the user can use the same tool to repair his system in many cases.

Often I posted the quick answers and sometimes still do, but meierfra. (creator of bootscript) and others quickly taught me that more info was good. :)

---

