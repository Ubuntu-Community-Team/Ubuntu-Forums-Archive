---
title: "Advice needed on 10.04 LTS to 12.04 LTS upgrade."
date: 2013-05-06
forum: Installation &amp; Upgrades
---

### Post by gencon on 2013-05-06
I need some advice on upgrading from 10.04 LTS Lucid Lynx to 12.04 LTS Precise Pangolin. Lucid support ends in 3 days on 2013-05-09, so I've kind of left it to the last minute.

Many people seem to have had problems upgrading directly from 10.04 to 12.04 using a "dist-upgrade", so I was thinking of burning a Precise install DVD and doing a clean install. However I do not want to overwrite my '/home/' directory tree and lose all my application settings. Can I keep '/home/' and just install the 12.04 LTS Precise Pangolin OS? Can I have advise on how best to do this please?

I will, of course, backup the whole of '/home/user/' but within my home directory tree I have >750 GB of data - restoring this via my USB external HDD would take days! - so I don't want to overwrite '/home/user/' when doing the 12.04 OS install.

Many thanks.

---

### Post by darkod on 2013-05-06
If /home is not a separate partition, you can't save it. Because best is to format the / partition when installing the new version, and if home is only a folder in / it will get formatted too.
If /home is a separate partition, you can format / but not format /home and reuse it as /home again.

Also, I don't think you upgrade to a new release with dist-upgrade, that it only to upgrade all packages to the most recent version. To upgrade the ubuntu release you use do-release-upgrade.

In any case it's best to have a full backup, which ever choice you make.

---

### Post by grahammechanical on 2013-05-06
Just for the record and because you are not the first person to get this wrong, "dist-upgrade" does not upgrade to the next release of Ubuntu. It is a way of upgrading the existing install of Ubuntu. It is similar to "upgrade."

In my opinion a sensible way of upgrading from 10.04 to 12.04 is to use Update Manager. Run

```
update-manager -d -c
```

That should prompt the Update Manager to give a button inviting you to upgrade to 12.04. At least it did as far as I can remember from a year ago when I was testing upgrades from 10.04 to 12.04. Revert your 10.04 to as basic an install as possible. Remove PPAs.

Official advice

[https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

---

### Post by gencon on 2013-05-16
Thanks for the advice. Sorry to take a week to get back to you I had to unexpectedly go abroad for this last week.

"/home" is in fact in a separate partition, so I'll do a 12.04 LTS Precise Pangolin clean install of "/" but not of "/home".

Cheers.

---

### Post by C.S.Cameron on 2013-05-16
You may need change permissions to get access to the home partition.

---

### Post by gencon on 2013-05-16
> **C.S.Cameron said:**
> You may need change permissions to get access to the home partition.

Can you say when this would need to be done, what would need to be changed, and why this would be necessary?

Thanks.

---

### Post by darkod on 2013-05-16
If you want to keep using your /home partition, which you do, you need to "use it" during the install, just not to format it.

So, you reuse the root partition as ext4 with mount point / and tick the format box. You reuse /home as ext4 (or different filesystem if you had a different one, it has to match the existing filesystem, that's very important), with mount point /home and NOT ticking the format box.
When the partitions list shows, make sure /home does NOT have the format column selected.

If you use the same first user as in the previous installation, all should be well and you don't need to change any ownership or permissions. You should always create the same first user when using existing /home.

You can create other users later.

---

### Post by gencon on 2013-05-17
Okay got it. Thanks very much.

All clear and ready to go for the big move from Lucid to Precise this weekend. Kinda exciting. :)

---

### Post by lisati on 2013-05-17
> **darkod said:**
>  To upgrade the ubuntu release you use do-release-upgrade.

In any case it's best to have a full backup, which ever choice you make.

^^^ This.

+1 to Backup: there is always a risk of breakage when going down this path, so having a backup of important stuff.

---

### Post by gencon on 2013-05-17
Okay got it. Thanks very much.

All clear and ready to go for the big move from Lucid to Precise this weekend. Kinda exciting. :)

---

### Post by gencon on 2013-05-17
Backups all done, ran it using rsync overnight. Took 9 hours over USB to an external HDD, hope I don't need to restore it. :)

---

