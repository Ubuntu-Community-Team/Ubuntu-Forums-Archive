---
title: "Mangled grub2: another dead UEFI  (but I can boot manually)"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by erupter on 2012-10-20
Ubuntu 12.04 x64
So the other day some auto-update crashed my boot config.

[http://paste.ubuntu.com/1292248/](http://paste.ubuntu.com/1292248/)
here is my setup: SDC is where linux is, I manually choose the boot device.
Meaning I don't want GRUB to interfere with windows or anything.
I had it installed on SDC and stop. And so it must remain: as if SDC were the only drive in the system. Apart from any other pieces UEFI may need to properly boot.

Now if I try to boot sdc in uefi mode I have the
"invalid arch independent ELF magic” error and subsequent grub recovery cli.

If instead I boot the hardrive itself (which is to say legacy mode... I think) I get to a standard grub cli, where I can do the following
```

set root=(hd0,msdos6)
chainloader +1
boot

```and everything is fine: I'm greeted with the usual boot menu (linux, linux recovery, memtest, etc) and I can go on just fine.

Now since it's pretty uncomfortable to type all that each time I boot, I'd really like to fix my configuration.
I found numerous pages citing the kind of error I'm having, and I tried
```

sudo grub-install --root-directory=/  /dev/sdc

```it went through without errors, but still no boot.

So the partition is there, I can manually mount it but I can't get grub to automatically do that.
Can anyone point me in the right direction please?

---

### Post by erupter on 2012-10-20
Ok I must admit I cried too soon :)

All manual attempts failed.

Then some site recommended trying boot repair (from a custom repo).
I did and now everything is fine, including my UEFI boot!!! yeah :guitar:

---

### Post by darkod on 2012-10-20
You have a very weird mix of legacy boot and uefi. And in fact you shouldn't be using uefi at all. win7 is not installed in uefi.

You notice how the fdisk results in the boot info say you have GUID (gpt) table not used on sdb. It seems the disk was gpt and you converted it to msdos with windows but windows doesn't delete the backup gpt table and later creates confusion.

So, here is what I would do:
1. Boot the computer and go into bios immediately. Find the option mentioning uefi boot and disable it. You should be using legacy mode only.

2. Boot the ubuntu manually with the commands that already work. Install fixparts and run it on sdb like this:
```
sudo fixparts /dev/sdb
```

The fixparts link is:
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Fixparts should detect the unused gpt backup table on sdb and offer to remove it. Do that.

3. After that is done you need to purge grub2 completely since it tried to install in uefi mode. So, in terminal do:
```
sudo apt-get remove --purge grub-pc grub-efi grub-common
sudo apt-get install grub-pc
sudo grub-mkconfig
sudo update-grub
sudo grub-install /dev/sdc
```

That will install grub2 on sdc as you want, not touching the windows bootloader on sdb. Reboot and in bios set to boot from sdc as first option (because that's hwere grub2 will be).

If anything happens, don't panic right away, even if things get complicated it should be easily fixable from live mode. Just make sure you have ubuntu cd at hand to use in live mode if necessary.

---

### Post by erupter on 2012-10-20
> **darkod said:**
> You have a very weird mix of legacy boot and uefi. And in fact you shouldn't be using uefi at all. win7 is not installed in uefi.

You notice how the fdisk results in the boot info say you have GUID (gpt) table not used on sdb. It seems the disk was gpt and you converted it to msdos with windows but windows doesn't delete the backup gpt table and later creates confusion.

[...]

3. After that is done you need to purge grub2 completely since it tried to install in uefi mode. So, in terminal do:

sdb is an ssd that was partitoned by Windows 7 during installation. I didn't do anything else, so I suppose the number and kinds of partitions are what Windows thought necessary to function on my system.
sdc is a removable and has linux on it.

Btw as I wrote above I solved (at least for linux, now I have to see if I didn't screw anything else): it boots automatically in uefi as before.

---

### Post by darkod on 2012-10-20
> **erupter said:**
> sdb is an ssd that was partitoned by Windows 7 during installation. I didn't do anything else, so I suppose the number and kinds of partitions are what Windows thought necessary to function on my system.
sdc is a removable and has linux on it.

Btw as I wrote above I solved (at least for linux, now I have to see if I didn't screw anything else): it boots automatically in uefi as before.

What you are saying sounds technically impossible. It might be booting, but not in uefi as you think. Or, you ended up with a hybrid boot process where it boots win7 in legacy, and ubuntu in uefi.

The reason is that sdb has msdos partition table and win7 can work with uefi only on gpt table. That's why is technically impossible that you have full uefi boot.

Further more, uefi boot works with a FAT32 EFI System partition which should be the first partition on the disk. Such a partition doesn't exist on any of your disks.

---

### Post by erupter on 2012-10-20
> **darkod said:**
> What you are saying sounds technically impossible. It might be booting, but not in uefi as you think. Or, you ended up with a hybrid boot process where it boots win7 in legacy, and ubuntu in uefi.

The reason is that sdb has msdos partition table and win7 can work with uefi only on gpt table. That's why is technically impossible that you have full uefi boot.

Further more, uefi boot works with a FAT32 EFI System partition which should be the first partition on the disk. Such a partition doesn't exist on any of your disks.

sdc has ha FAT32 as the first partition, I can see it from Windows.
sdb has a 100mb NTFS partition as the first.
sda has just a 1TB NTFS partition.

I don't know how my setup came to be in terms of booting, I know what I did.
Connect an sdd on the second sata channel, an hdd on the first sata channel.
Install win7 on the sdd, format the hdd as ntfs.

A lot later I added a removable 500GB hdd on sata3, set that as first boot device (legacy) and installed ubuntu.

This is how my configuration came out.
From what I know Ubuntu boots in UEFI (boot menu options show: "uefi: ubuntu") and now that you point that out Win7 probably doesn't.

---

### Post by darkod on 2012-10-20
Yeap, correct. sdc1 is FAT32 but as you can see it is marked as standard fat32 partition, not EFI System (the partition code for EFI System is different).

Personally, I would clear up the mess and make ubuntu boot in legacy too. But it's your computer and you can use it how ever you want. :) If you are happy with the currect setup, no problem.

---

