---
title: "boot repair failed due to 'Locked-NVram detected'"
date: 2023-08-21
forum: Installation &amp; Upgrades
---

### Post by hansljy on 2023-08-21
I cannot log into ubuntu on my dual-boot laptop after it was fixed by Lenovo. So I tried boot-repair using a live USB disk. However it shows 'Locked-NVram detected'.
The log can be seen here [https://paste.ubuntu.com/p/qk8WQcKHb6/](https://paste.ubuntu.com/p/qk8WQcKHb6/)
Any advice?

---

### Post by tea for one on 2023-08-22
I wonder if the UEFI settings were returned to default while Lenovo were repairing your PC.
Can you access the UEFI settings and check the security options:-

Disable Secure Boot
Disable TPM
Disable PTT (Platform Trust Technology or similar descriptions)

There doesn't seem to be an EFI entry for Ubuntu at the moment so we may have to run boot-repair again or install Grub manually via a live session.

---

### Post by MAFoElffen on 2023-08-22
Have you looked for similarities in these?

RE: [https://ubuntuforums.org/search.php?searchid=29165735](https://ubuntuforums.org/search.php?searchid=29165735)

That is a search on the search terms "locked-nvram lenovo"... If you do that on Google, quite a few more.

If you posted more information about what your hardware actually is, it might be a bit easier to narrow that down for you, for things to try.

I am still a certified Onsite Warranty Service Tech for Lenovo, HP and Dell. I am familiar with the hardware and their default BIOS settings.

This happens on Lenovo's for a few reasons. One similarity is that most of these are laptops where Windows was installed. Usually long ago as Windows 7, then upgraded to newer releases. A lot of them were installed originally as BIOS Legacy/CSM boot. They had installed the bootloader as MBR in sector 0 of the disk... And later created an EFI partition to boot from. A lot of Lenovo's also had a BIOS setting that was hybrid, where it would allow both CSM & UEFI boot. That sort of "multiple choice" situation confuses Grub. the next is a Windows setting for hibernation, that sets the Windows filesystem in an open-suspended state, which also locks the NVRAM so that it can wake up... Those varied things setup sort of a perfect storm kind of thing.

Some of the things you can check on your own, in Windows (if installed) and in the BIOS Settings that affect Grub, is that turn off Windows Hibernation "fastboot". Next is to go into the UEFI BIOS settings to turn both SecureBoot off and set the BIOS Boot Mode to UEFI. Not hybrid, not legacy.

Depending how Windows is installed, that may break your Windows install. Yours looks like it will be fine. (from the report)

But see this in lines 68 through 72?
```

chroot /mnt/boot-sav/nvme0n1p5 grub-install --efi-directory=/boot/efi --target=x86_64-efi
Installing for x86_64-efi platform.
grub-install: warning: EFI variables cannot be set on this system.
grub-install: warning: You will have to complete the GRUB setup manually.
Installation finished. No error reported

```
There is that perfect storm... It should be able to see those efi variables in sysfs.

One way around that is to ensure you create an Installer LiveUSB as GPT/UEFI boot. Ceck the boot mode on your own:
```

ls /sys/firmware/efi/efivars

```
If you have output, it booted in UEFI mode.

Mount the installed filesystem...
```

sudo su -
modprobe efivars
mount /dev/nvme0np5 /mnt
mount /dev/nvme0np1 /mnt/boot/efi
mount -t efivarfs none /sys/firmware/efi/efivars
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run /mnt/run
chroot /mnt /usr/bin/env bash --login

## This is your test:
ls /sys/firmware/efi/efivars
## If it has ouput, go on. If not stop here.

apt install --yes grub-efi-amd64 grub-efi-amd64-signed linux-image-generic shim-signed
grub-probe /boot
## ^^^ If this goes with no errors, go on

grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy
## If no errors, go on
exit
reboot

```

---

### Post by hansljy on 2023-08-22
I use ThinkPad X1C gen 9 and I cannot find where to change my setting to uefi boot

---

### Post by oldfred on 2023-08-22
Are you sure its not new enough to be UEFI only?
Lenovo announced all 2020 products will be UEFI only (UEFI Class 3 or no CSM).
[https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products](https://support.lenovo.com/us/en/solutions/ht510878-legacy-bios-boot-support-removed-in-lenovo-2020-products)

---

### Post by hansljy on 2023-08-22
Maybe it is. But I have done all the things except this one in MAFo's answer and still not working

---

### Post by hansljy on 2023-08-22
When running the 'grub-probe' command, I came across the error of '[grub-probe: error: failed to get canonical path of /cow]("https://unix.stackexchange.com/questions/96977/grub-probe-error-failed-to-get-canonical-path-of-cow")'

---

### Post by MAFoElffen on 2023-08-23
> **hansljy said:**
> When running the 'grub-probe' command, I came across the error of '[grub-probe: error: failed to get canonical path of /cow]("https://unix.stackexchange.com/questions/96977/grub-probe-error-failed-to-get-canonical-path-of-cow")'
It may sound odd, but the workaround to that is to do
```

sudo touch /cow

```
Yes, the release date for his Lenovo Thinkpad X1 Carbon Gen 9 laptop was in 2021. Should be less than 2 years old...

The X1 gen 9 actually has more than one option you need to set... In the BIOS Setup, first go to Config > USB > USB BIOS Support for UEFI > Set to "Enabled" Next, go to Config > USB > USB always on > Enabled. Next go to Config > Storage > Controller Mode > AHCI. 

Next go to Security > Security Chip > TPM... Check if enabled or not. I "enable" and have no problems. Some say to disable it. For now, just take note of where it si lacated ad what it is set to.

Next go to Security > Secure Boot > Secure Boot > Disabled. Note that if you wantr or need to set SecureBoot to "enabled" on this laptop, then Boot mode needs to be set to "UEFI Only", and "CSM Support: No" If for some reason you want to the boot mode as "Legacy", then Secure boot must be set to diabled.

Next go to Startup > Boot Mode > "UEFI Only"

Save and exit...

---

### Post by oldfred on 2023-08-23
/cow is the live installer or USB flash drive. That cannot be updated.
You want to run commands on your install, not the live installer.

---

### Post by MAFoElffen on 2023-08-23
Dang... Forgot where it was in. Then at that point, do this to check if chroot was successful or not
```

sudo systemd-detect-virt -r
exit_code=$?

if [ $exit_code -eq 0 ]
then
    echo -e "Inside of chroot environment."
else 
    echo -e "Not inside of a chroot."
fi

```

---

