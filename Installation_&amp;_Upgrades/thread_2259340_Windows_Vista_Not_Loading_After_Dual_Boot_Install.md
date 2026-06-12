---
title: "Windows Vista Not Loading After Dual Boot Install"
date: 2015-01-03
forum: Installation &amp; Upgrades
---

### Post by tashfeen_ekram on 2015-01-03
I  am unable to boot my old Windows Vista. This is actually an old  problem. I had given up on it but recently came across [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). It  went down sometime ago after I installed Ubuntu 10.x? Not sure exactly  when. Since though I have upgraded Ubuntu 14.04. At one time if I  remember correctly, one of my Wubi installations got corrupted an d I  just reinstalled and possibly just wrote over my previous installation?

I tried to use Ubuntu Boot Repair. My Ubuntu works perfectly fine. It would be nice to get back in to the Windows side of things. 

Here is the link:

[http://paste.ubuntu.com/9666401/](http://paste.ubuntu.com/9666401/)



Thanks,
Tashfeen

---

### Post by grahammechanical on 2015-01-03
> A broken Wubi has been detected. Please fix it this way:
[https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu)

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Regards.

---

### Post by oldfred on 2015-01-04
The grub menu shows the Vista entry, what happens when you use that?

Some are able to use f8 if they press it almost at the same time as the grub entry for Windows. Most have to temporarily reinstall the Windows boot loader to the MBR with Boot-Repairs advanced mode, as then you have a bit more time for f8. Only if you have updated Vista with service pack will you have a repair console, otherwise you need a Windows repair CD or flash drive.

Boot-Repair only can fix minor issues with Windows, you usually need a Windows repair disk.
Grub really only boots working Windows.

---

### Post by tashfeen_ekram on 2015-01-04
Thanks for the reponse. That is helpful. When I choose Windows, it just hangs, nothing happens. But let me try what you suggested and let you konw how it goes.

---

### Post by tashfeen_ekram on 2015-01-04
As a follow up question, when my original Wubi failed, I think I just installed another one rather than trying to fix it which is when I think my Vista went bad. On my working Ubuntu installation, my Gparted tells me that there is some unallocated space. Could this represent my prior Wubi installation?

---

### Post by Mark Phelps on 2015-01-04
> my Gparted tells me that there is some unallocated space. Could this represent my prior Wubi installation? 

NO -- WUBI does not have its own partition; instead, it takes space inside an existing Windows NTFS partition.

---

### Post by tashfeen_ekram on 2015-01-04
Got it. Could this have been a result of trying to partition the drive for an Ubuntu that failes?

---

### Post by tashfeen_ekram on 2015-01-04
That failed to install?

---

### Post by oldfred on 2015-01-05
What failed to install?

---

### Post by tashfeen_ekram on 2015-01-05
It was a few years ago. I recall having some issue trying to install Ubuntu but honestly I can not recall what actually happened. I think I was trying to revive my Wubi installation that had gone bad by installing a fresh Ubuntu and trying to somehow revive the data? Being an amateur then and more so even before, I was blindly following some instructions I found online and things did not go as planned. Perhaps the space I had partitioned for the Ubuntu was too small? Could any of that explain the source of the unallocated space?

---

### Post by oldfred on 2015-01-06
You show a small of amount of space after sda2, but that would not be related to wubi.

---

### Post by tashfeen_ekram on 2015-02-28
So, I made things worse. I tried to use a Vista repair CD to fix things and now when my computer loads I just get the blinking cursor. Messed up the boot record? Is there a way to restore things? I would be happy just to get access to my Ubuntu again.

---

### Post by oldfred on 2015-02-28
If you have the Ubuntu live installer, down load this and post link it gives for Summary report.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by tashfeen_ekram on 2015-02-28
I used Boot-Repair and it worked great. Ubuntu is back up and running but the Windows is still broken. Below is the report 

[http://paste.ubuntu.com/9666401/](http://paste.ubuntu.com/9666401/)

I think I am just going to leave it as is...

---

### Post by oldfred on 2015-02-28
It just looks like the NTFS partition was made smaller. And then new extended partition which has swap in it did not use all the space.

---

### Post by Mark Phelps on 2015-03-01
The Vista Repair CD most likely has to be run three times to do all the repairs needed.  The Windows boot repair program is not very smart and only fixes one of three items on each pass.  Sometimes you're lucky and it fixes the broken item of the first pass, but more often, it takes all three passes to get all the items fixed.

If you didn't run it three times, then redo it -- running it three times.

---

### Post by tashfeen_ekram on 2015-03-01
Unfortunately, the repair disc will not even recognize my Vista installation. I am actually unable to even change the size of that partition as it seems to be some how corrupted. I ran chkdsk to try to address it but perhaps need to run it a few times?

---

