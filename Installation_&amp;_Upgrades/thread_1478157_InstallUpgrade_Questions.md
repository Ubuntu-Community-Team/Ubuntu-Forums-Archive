---
title: "Install/Upgrade Questions"
date: 2010-05-09
forum: Installation &amp; Upgrades
---

### Post by AZinOH on 2010-05-09
Have a 3 year old Dell currently dual-booting XP SP3/8.04. What I need to achieve is a seamless replacement of 8.04 with 10.04. First question-can I upgrade directly from 8.04 to 10.04? There is no "upgrade button" in the Update Manager to do this. Is there a way using Terminal? If no-second question. I am currently using what I guess is now called grub-legacy and ext3. If I install using the cd, what is going to happen to these? Will either or both get updated? If I install using the cd, I do not want to save anything from the 8.04 install nor do I want to save the /home partition. I just want to replace the old with the new while making ABSOLUTELY CERTAIN THAT THE EXISTING DUAL-BOOT WITH XP IS NOT DAMAGED IN ANY WAY. What's the best way to go about this? I have already run the 10.04 live cd and do not see any conflicts with it. Thanks for any assistance.

---

### Post by darkod on 2010-05-09
I don't think you can upgrade directly from 8.04 to 10.04. And if you don't need to keep anything from 8.04 a fresh install of 10.04 is much better anyway.

If you are happy with the current sizes of your partitions, you could start the 10.04 installer and select Manual partitioning. It will show you a list of your partitions (and disks).

Just click on the 8.04 root partition and the button Change on bottom. Change from "do not use" to ext4 (or ext3 if you want to use that). Tick the format box. Set mount point as /.

The swap partition will get reused automatically.

If you have separate /home partition do as above for / and don't format it if you want to keep the data.

That's it.

Another way is to boot the 10.04 live desktop, use Gparted to delete all 8.04 partitions and leave that space as unallocated.
Boot the 10.04 installer and just select Use Largest Available Free space. That will install it inside the unallocated space you left.

If you have one disk no need to worry about grub going to the wrong disk. With multiple disks, at the last screen of the installer click on Advanced and make sure the bootloader is installed on the disk where you want it.

---

### Post by DougieFresh4U on 2010-05-09
In the 'Software Sources' under 'Updates' what do you have selected? You should have 'Long Term Releases' and it should offer upgrade, as you can go from 'LTS' to 'LTS'

---

### Post by darkod on 2010-05-09
> **DougieFresh4U said:**
> In the 'Software Sources' under 'Updates' what do you have selected? You should have 'Long Term Releases' and it should offer upgrade, as you can go from 'LTS' to 'LTS'

I stand corrected. :)

---

### Post by AZinOH on 2010-05-09
Under software Sources/Updates, long term support releases was already checked. Under Ubuntu updates, my four choices are: important security updates (hardy-security), recommended updates (hardy-updates), prereleased updates (hardy-proposed), and unsupported updates(hardy-backports). The first two were enabled, the other two were not. After checking those boxes and running Update Manager, I got this:


GPG error: [http://repository.cairo-dock.org](http://repository.cairo-dock.org) hardy Release: The following signatures were invalid: NODATA 1 NODATA 2GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513Failed to fetch [http://repository.cairo-dock.org/ubuntu/dists/hardy/cairo-dock/binary-i386/Packages.bz2](http://repository.cairo-dock.org/ubuntu/dists/hardy/cairo-dock/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

Some index files failed to download, they have been ignored, or old ones used instead.

After doing this, I rec'd 57 updates that seemed not to be important but I installed them anyway. However, I still do not get a button in Update Manager to upgrade to 10.04.

---

### Post by darkod on 2010-05-09
> **AZinOH said:**
> Under software Sources/Updates, long term support releases was already checked. Under Ubuntu updates, my four choices are: important security updates (hardy-security), recommended updates (hardy-updates), prereleased updates (hardy-proposed), and unsupported updates(hardy-backports). The first two were enabled, the other two were not. After checking those boxes and running Update Manager, I got this:


GPG error: [http://repository.cairo-dock.org](http://repository.cairo-dock.org) hardy Release: The following signatures were invalid: NODATA 1 NODATA 2GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513Failed to fetch [http://repository.cairo-dock.org/ubuntu/dists/hardy/cairo-dock/binary-i386/Packages.bz2](http://repository.cairo-dock.org/ubuntu/dists/hardy/cairo-dock/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

Some index files failed to download, they have been ignored, or old ones used instead.

After doing this, I rec'd 57 updates that seemed not to be important but I installed them anyway. However, I still do not get a button in Update Manager to upgrade to 10.04.

You can always do the clean install since you said you don't need anything from the current system. As mentioned, a clean install is always preferred. Upgrade could leave you with issues even when 10.04 is running well in live mode.

---

### Post by AZinOH on 2010-05-09
I appreciate the reply and will probably end up doing the clean install. I was just hoping to understand why the upgrade path wasn't available. sometimes things like this are good to know later on.

---

### Post by fabounet on 2010-05-10
cairo-dock.org has changed to glx-dock.org
so you just need to replace it in your sources.list

---

