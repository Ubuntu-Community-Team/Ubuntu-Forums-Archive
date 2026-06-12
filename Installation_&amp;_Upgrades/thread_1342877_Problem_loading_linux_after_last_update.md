---
title: "Problem loading linux after last update"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by tankefugl on 2009-12-01
I just finished an automatic system update on my Ubuntu 9.10 that was installed via Wubi. I didn't pay attention to it much as there were 60-something updates. It required a reboot.

After the reboot I get to Windows boot menu where I can choose Ubuntu. However, upon choosing Ubuntu, the screen quickly fills with some message (too fast for me to read), clears, and a GRUB shell loads.

I am at loss at how to procede from here. I poked around in it a bit, googled around, but got no immediate solution. All I know is that it seems to successfully find the root device (root is set to loop0), but perhaps it is missing the kernel image or something? Purely speculating here...

Any suggestions on what to do are most welcome!

---

### Post by darkod on 2009-12-01
This seems to be a problem with wubi if you do the update to kernel 2.6.31-15. Moral of the story: Make a proper ubuntu install. wubi is NOT an ubuntu installation. Just a quick and easy way to try ubuntu inside windows. Do NOT count on using it long and do NOT depend on it.
Sorry, I've seen other threads with this exact problem but not a solution that I have seen. If you like Ubuntu, I recommend removing wubi with add/remove programs and installing proper dual boot anyway. You can't expect linux to work fine inside windows, not an easy thing to do.

---

### Post by tankefugl on 2009-12-01
Found a temporary solution to at least get the old kernel working. When kicked to the GRUB shell:

linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sdb1 loop=/ubuntu/disks/root.disk ro quiet splash
initrd /boot/initrd-2.6.31-14-generic
boot

Then, as the system booted, do a

sudo update-grub2

This allows me to boot the -14 kernel at startup. The -15 kernel also displays why it fails: Kernel panic due to unable to mount a file system.

---

### Post by ubnoobie on 2009-12-01
just experienced the same problem. 

thank you tankefugl. your reply helped me get booted back up quickly.

> **darkod said:**
> This seems to be a problem with wubi if you do the update to kernel 2.6.31-15. Moral of the story: Make a proper ubuntu install. wubi is NOT an ubuntu installation. Just a quick and easy way to try ubuntu inside windows. Do NOT count on using it long and do NOT depend on it.
Sorry, I've seen other threads with this exact problem but not a solution that I have seen. If you like Ubuntu, I recommend removing wubi with add/remove programs and installing proper dual boot anyway. You can't expect linux to work fine inside windows, not an easy thing to do.

just the fact that you believe wubi runs ubuntu "inside" windows, shows you know nothing of how it actually works; and regardless of your own opinion regarding wubi, it IS an OFFICIAL installer for Ubuntu:  [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by darkod on 2009-12-01
We can argue about technicalities and wording used for ages, it's working just as any virtual OS (or VM). It does NOT create ext4 partitions on your drive right? Check windows disk management if there are any.
The same can be done by using Virtual PC for example, and then install any OS on that VM. I was talking about real dual boot situation, the same as many people here.
Yes, it is an official installer created by ubuntu team, I surely didn't develop it myself. And that's where they went wrong IMHO, because it's not easy to desing it working like that and every problem gives ubuntu bad name. 90% of those problems do not happen in dual boot environment.

PS. Since you seem to understand things exactly to the letter, from:
[https://help.ubuntu.com/community/Wubi](https://help.ubuntu.com/community/Wubi)

The **W**indows-based **Ub**untu **I**nstaller (Wubi) allows you to install and uninstall Ubuntu from within Microsoft Windows.** It lets a Microsoft Windows user try Ubuntu** without risking any data loss due to disk formatting or partitioning.

Select **Install inside Windows.** The Ubuntu Setup window appears.

From my post: Just a quick and easy way to try ubuntu inside windows.

Like I said, easy way to TRY but do NOT depend on wubi.

---

### Post by Holgi on 2010-01-12
Had same issue

1) Hints on this page got me started up again - thanks!
2) Using the patched wubildr fixed the problem properly: [https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210](https://bugs.launchpad.net/ubuntu/+source/lupin/+bug/477169/comments/210) 

Hope this helps,
H

p.s. Not to add fire to the flames. Wubi "installs" inside of windows as in "It places files in the Windows filesystem and adds an option to remove Ubuntu from the Windows filesystem". But unlike a Virtual Machine, it does not make Ubuntu "Run" within Windows (or another host system). It merely allows Ubuntu to run on a virtual file system (VFS) - incidentally, exactly the thing that seems to cause the issue discussed in this thread (wubi not loading the host file system properly). Since this runs Ubuntu using a filesystem (ext3 or 4) within another filesystem (Fat32, NTFS, or whatever you have windows installed on), it makes the system somewhat more fragile and slower. It should still generally be faster than running it within a Virtual Machine (as it does not have to share CPU, memory, disk access, etc.). Just my 2c's.

---

