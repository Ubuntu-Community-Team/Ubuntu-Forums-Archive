---
title: "Encryrpted Ubuntu doesn't boot anymore (vgubuntu not found)"
date: 2022-11-11
forum: Installation &amp; Upgrades
---

### Post by alexpezet on 2022-11-11
Hello @all,
(excuse if my English is not the best)

I already googled about the problem, but didn't find a solution. I am no pro, but I can use the terminal somehow.
What I did before: I tried to install some software and did some updates in the paket manager when I was there to find software. Perhaps this was the problem.
Suddenly my Harddrive wasn't shown any more. I couldn't access my files any more. Did a restart and then the following message after password (decryption):

Can not process volume group vgubuntu
vgubuntu not found
(And perhaps this was also there: vgubuntu-root cear/n <-- sadly I am not sure if I wrote down correctly)

After google about that problem, I didn't find a solution yet. Even if there wouldn't be chance to repair the installation, is there a chance of accessing my data from another ubuntu and decrypt it?

Thank you!

---

### Post by TheFu on 2022-11-11
A) when ever using encryption, excellent backups are mandatory.  Any tiny hardware issue can break access to the encrypted areas, making all the data inaccessible.  So, assuming you have excellent backups that can be restored, if this isn't solved in 45 minutes, is the first assumption.  A restore from backups should take less than 1 hr.

B) Troubleshooting any system that doesn't boot begins with booting from a "Try Ubuntu" ISO off installation media from the same OS release installed.  If the installed OS that won't boot is running 20.04, then you need a 20.04 installation ISO to boot from .

C) After getting booted into the "Try Ubuntu" environment, you'll want to install a few helper programs if they don't exist.  I think they should be in the environment, but you'll need lvm and cryptsetup.  If your "Try Ubuntu" is Ubuntu-Mate, I know that the file manager will let you point-n-click on storage and prompt to unlock any encrypted containers, then use the 'vgchange -ay' command to activate the LVM storage throughout the system.

D) In theory, the LUKS encrypted container is open and the different logical volumes are showing up. Run these commands to prove it:
```
lsblk -e 7 -o name,size,type,fstype,mountpoint
df -hT -x squashfs -x tmpfs -x devtmpfs
sudo pvs
sudo vgs
sudo lvs

```
Post both the command and the results back here. Please, please, please, use forum "code tags" around the output so things line up in columns correctly. Without that, it is impossible to read.

Now would be a good time to run the Ubuntu Forums System Information script, while everything is unlocked and available.  Get it here and follow the instructions to run it and have the results posted:  [https://github.com/UbuntuForums/system-info](https://github.com/UbuntuForums/system-info)
Without that requested information, we really can't help.  You may see posts about using  "Boot-Repair" - don't.  With encryption and LVM, I don't think it does what you want. It will likely make things much worse.

If you can't unlock the LUKS and see the LVM objects, best to wipe the system and do a fresh install, followed by restoring your data/setting backups.

If access to the drive doesn't happen, you'll want to use smartctl to run a test, then after the test finishes, use smartctl to get a test report.  That's 2 separate commands.  SMART data is provided by all storage makers to provide hardware status reports.  It can show were a drive has failed or is failing or has just begun to fail.  It is very useful, but best to see how the data changes over time, not just when a failure is suspected.  I run SMART tests on all storage each week, so that any changes can be seen.  Look for the parameters with "errors" and  "relocated" and "pending".   Or just post the output here, using code-tags.

---

### Post by alexpezet on 2022-11-12
Thank you very much! I will be back when I have done it. (Yes I have backups, but it is 1-2 month ago- better than nothing, but bad enough)

---

