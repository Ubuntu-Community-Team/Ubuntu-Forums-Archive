---
title: "Unable to boot via grub2 since a RAM upgrade"
date: 2020-12-19
forum: Installation &amp; Upgrades
---

### Post by Khelair on 2020-12-19
Hi everybody.

I managed to pick up another 16GB of ram for my machine a few days ago here, and got it successfully installed, despite a few mishaps with the machine not powering up.  Unfortunately, after getting it to power up successfully, I found out that it was unable to boot via *grub2*.  I can't remember the exact message, but it was looking for a drive I believe by UUID that started with a 'd', and my sole ext4fs partition does not start with such.  I have no idea where it got this idea.  I had no rescue disk or stick at the time, but I eventually realized that I could use a boot option in my BIOS to boot to the drive manufacturer specified drive.  So my system is up right now, but any time I have to reboot I have to manually go into the BIOS again to boot it.  I have tried updating *grub2* and reinstalling it, yet the same error persists...

Can anybody help me figure out how to get my machine booting on its own again?  I really need the services that I have configured on this machine to come back up on their own when I'm not around...  Let me know if I need to reboot and write down the actual exact error message that it gave, I can do it, I'm just trying not to because I don't want to have to shut down everything and the VMs, it's a royal pain in the buttocks to bring it back up to having everything I need running again, too.

I apologize if this is a little vague, please let me know how I can be more specific.  Oh, for what it's worth I am running _Xubuntu 20.04.1 LTS_ at this time.

Thanks everybody, I really appreciate whatever you can do to point me in the right direction here.

---

### Post by oldfred on 2020-12-19
If Ubuntu is running, you can run the report from Boot-Repair to see details.
Post link to summary report.

Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by GhX6GZMB on 2020-12-19
Did you run **sudo update-grub**?

---

### Post by CatKiller on 2020-12-19
> **Khelair said:**
> got it successfully installed, despite a few mishaps with the machine not powering up.
Would those "mishaps" have included the UEFI being reset to default values?

---

### Post by Khelair on 2020-12-19
> If Ubuntu is running, you can run the report from Boot-Repair to see details.
Post link to summary report.

Alright I ran *Boot-Repair* and generated a report.  The pastebin contents can be found by clicking [this hyperlink]("https://paste.ubuntu.com/p/qrMzccR5GB/").  I will be digging through the information that you have given me, as well.  Thank you for your time and assistance on this matter.

---

### Post by Khelair on 2020-12-19
> **ml9104 said:**
> Did you run **sudo update-grub**?

I did, yes.

---

### Post by Khelair on 2020-12-19
> **CatKiller said:**
> Would those "mishaps" have included the UEFI being reset to default values?

I don't know for certain, but I suspect that this could be part of the issue.  I'm afraid I know basically less than nothing about UEFI at this point.  It did look like the BIOS had had at least a few values reset...

---

### Post by oldfred on 2020-12-19
While you have an UEFI system you have BIOS install.
You show sda as gpt with a bios_grub.
It looks like grub is installed to MBR of sda for booting.

I do not know LVM nor encryption.
But you have a different grub installed into sdb, which is a MBR(msdos) partitioned drive, but only shows the extended partition, sdb4 containing the LVM encrypted volume in sdb5.

Was sdb another install?
You seem to have a lot of space in drive before sdb4 that could have been additional partition(s)?
I might see what testdisk shows, if that is the case.

Since UEFI hardware, often better to use UEFI installs, but that now is a major change. So more for future planning. UEFI also should use gpt which you have on sda, but not sdb. But you can use gpt partitioning with BIOS installs as you have done on sda.

---

### Post by CatKiller on 2020-12-20
> **Khelair said:**
> I don't know for certain, but I suspect that this could be part of the issue.  I'm afraid I know basically less than nothing about UEFI at this point.  It did look like the BIOS had had at least a few values reset...

So the biggie is likely to be whether you're booting in UEFI mode or emulating the ancient BIOS. The control for that is generally referred to by "Legacy" or "Compatibility Support Module." There are differences between them, some of which oldfred has mentioned, but the important things to know are that UEFI is both newer and better than BIOS, and that if you installed in one and then try to boot in the other, it likely won't boot. I suspect that was your initial roadblock. Having it set to RAID rather than AHCI is another contender. The other things that you've done since may well have made things worse.

oldfred can talk you through getting everything up and running again.

---

### Post by Khelair on 2020-12-20
> **oldfred said:**
> While you have an UEFI system you have BIOS install.
You show sda as gpt with a bios_grub.
It looks like grub is installed to MBR of sda for booting.

I do not know LVM nor encryption.
But you have a different grub installed into sdb, which is a MBR(msdos) partitioned drive, but only shows the extended partition, sdb4 containing the LVM encrypted volume in sdb5.

While this makes sense to me, I'm afraid I don't know how to recover from it, and I'm kind of curious how in the hell it might have happened, as well.  Would a BIOS reset have caused this?

As far as *sdb*, it's an old archival drive for encrypted backup.  It's basically just mounted on one of *sda3*'s mount points and I back up to there or shuffle big old archives to there.  The grub installed there is probably from an ancient install from where that drive was the initial drive in the system a few years back, and has never given me issues coexisting with the one that was working on *sda*.  Again, I'm not sure what to do about this, though...

> Was sdb another install?
You seem to have a lot of space in drive before sdb4 that could have been additional partition(s)?
I might see what testdisk shows, if that is the case.

Since UEFI hardware, often better to use UEFI installs, but that now is a major change. So more for future planning. UEFI also should use gpt which you have on sda, but not sdb. But you can use gpt partitioning with BIOS installs as you have done on sda.

As I mentioned, I believe that *sdb* was another install a **long** time ago.  There was a prior boot & root partition there, at the beginning of the drive.  Not anymore, though; when I'd seen the report myself, I was reminded about that extra drive space...  I've been in desperate need of more storage lately, so I went and created an *sdb1* with all of the spare space, formatted it as ext4, and have mounted it for shuffling more archival storage to to free up some more root partition space.

---

### Post by Khelair on 2020-12-20
> **CatKiller said:**
> So the biggie is likely to be whether you're booting in UEFI mode or emulating the ancient BIOS. The control for that is generally referred to by "Legacy" or "Compatibility Support Module." There are differences between them, some of which oldfred has mentioned, but the important things to know are that UEFI is both newer and better than BIOS, and that if you installed in one and then try to boot in the other, it likely won't boot. I suspect that was your initial roadblock. Having it set to RAID rather than AHCI is another contender. The other things that you've done since may well have made things worse.

oldfred can talk you through getting everything up and running again.

I'm sure my tinkering probably has made things a little worse.  The only thing I've done that's directly worked with the MBR is that single grub update that I tried, but that was probably stupid to do before speaking to people knowing more than myself.  I do appreciate the information, though.

---

### Post by oldfred on 2020-12-20
There is a BIOS boot version of grub in MBR of sda. And it wants to load grub in sda3, so looks like it should start to boot.
Since only one install, you do not normally get grub menu.
If you hold shift key from UEFI/BIOS screen until grub appears, can you then boot in recovery mode?

---

### Post by Khelair on 2020-12-21
> **oldfred said:**
> There is a BIOS boot version of grub in MBR of sda. And it wants to load grub in sda3, so looks like it should start to boot.
Since only one install, you do not normally get grub menu.
If you hold shift key from UEFI/BIOS screen until grub appears, can you then boot in recovery mode?

I haven't had a chance to be able to reboot yet, but I should be able to tonight after work, so probably around 6-7pm CST I'll have an update for you.  Thank you so much for the assistance on this, btw.

---

### Post by Khelair on 2020-12-26
> **Khelair said:**
> I haven't had a chance to be able to reboot yet, but I should be able to tonight after work, so probably around 6-7pm CST I'll have an update for you.  Thank you so much for the assistance on this, btw.

Terribly sorry for the delay in being able to get to this.  I was unable to reboot my machine until now due to circumstances and drama...

Upon reboot, holding shift, *grub* did, indeed, boot into rescue mode (which, if I remember correctly, it was doing on its own, prior to that, when boot failed).  I didn't know any of the *grub* commands, so I was unable to produce any troubleshooting data, other than what popped up on its own (maybe that's a good thing so that I wasn't able to screw things up worse); here is the information that it provided:

```
error: no such device: d485b6db-1175-4f35-8a11-f5f701ccdbd1
```

Again I had to go into the BIOS menu by holding F12 for boot options and selecting the make & model of the drive holding /dev/sda, in order to boot.

Thank you for any assistance you may be able to provide!

-D

---

### Post by oldfred on 2020-12-26
Grub is telling you the truth.
You do not have that partition.
Are you sure you are booting from sda and not sdb? It looks like sdb has old grub that would try to boot from something that does not exist.

Have you used Boot-Repair to totally reinstall grub. But you must boot live installer in BIOS mode.

---

### Post by Khelair on 2020-12-26
> **oldfred said:**
> Grub is telling you the truth.
You do not have that partition.
Are you sure you are booting from sda and not sdb? It looks like sdb has old grub that would try to boot from something that does not exist.

Have you used Boot-Repair to totally reinstall grub. But you must boot live installer in BIOS mode.

Pretty sure I was booting from sda and not sdb, but I can't be sure now.

I used Boot-Repair's recommended repairs after booting the live installer.  It's booting up fine now, although it does seem to be taking a bit longer to boot than it did previously.  Is that because it's working in BIOS mode instead of the UEFI mode that it was using previously?

Anyway thank you very much for your assistance, I sure appreciate it.

-D

---

### Post by oldfred on 2020-12-26
You do not show an ESP - efi system partition which is required for UEFI boot.

But if UEFI set for UEFI boot and it has to try that first, then try to boot in BIOS mode, it would be slower.
What setting is UEFI default boot mode, UEFI, BIOS or "UEFI or BIOS" boot mode?

---

