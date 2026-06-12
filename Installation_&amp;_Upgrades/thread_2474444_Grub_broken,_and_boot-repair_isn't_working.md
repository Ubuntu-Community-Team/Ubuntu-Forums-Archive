---
title: "Grub broken, and boot-repair isn't working"
date: 2022-04-29
forum: Installation &amp; Upgrades
---

### Post by Paddy Landau on 2022-04-29
tl;dr Grub is broken, and Boot Repair doesn't work.

[HR][/HR]
I booted from a Live USB to install Ubuntu onto an external USB hard drive. In the past, this has never been a problem, because that process doesn't touch my computer at all. It only writes to the USB hard drive.

 But not this time. Why did it touch my computer? I don't know!

Now, when I boot my computer (without the Live USB or external USB hard drive attached), I get just a Grub prompt. (I'm writing this post from the Live USB.)

I installed and ran [Boot Repair.]("https://help.ubuntu.com/community/Boot-Repair")

The option to repair the computer — "Recommended repair (repairs most frequent problems)" — isn't shown. I only get the option to create a Bootinfo summary, and Advanced options.

So, I chose Advanced options > Main options > Repair file systems > Apply

But, that didn't help.

[SIZE=3]**More information**[/SIZE]


[LIST]
[*]My computer has Ubuntu 20.04, fully up-to-date. 
[*]Here is the [Bootinfo summary]("https://paste.ubuntu.com/p/z7phXhKm5x/") as created by Repair Boot. 
[*]I have a full up-to-date backup (whew!), so the worst case is that I have to reinstall from scratch. But I'd *really* like to avoid that, if I can just fix Grub! 
[*]I had to disable Secure Boot to run the Live USB (I'm using [Ventoy]("https://www.ventoy.net/")  for the Live USB, and my computer doesn't recognise its certificate).  But my computer won't boot with Secure Boot enabled or disabled. 
[/LIST]

My computer was installed with LVM and LUKS (full disk installation; there is no other OS on this system), as follows.

[LIST]
[*]Partition 1: EFI System Partition 
[*]Partition 2: /boot 
[*]Partition 3: LUKS, containing LVM, containing root 
[/LIST]
On the Live USB, I unlocked partition 3 and activated LVM. I've checked that it can be mounted correctly, but left it unmounted because Boot Repair wants it that way.

So, everything is available for Boot Repair to do its work.

**So…**

Can I get Boot Repair to work, or is there another method to fix Grub?

Thank you

---

### Post by oldfred on 2022-04-29
Do not know ventoy nor LVM with encryption.

But for Boot-Repair to work you need to boot live installer in UEFI boot mode and decrypt your install, so it can see all the volumes. 
Your grub entry in the ESP, line 282 refers to an UUID that is not otherwise in report. But probably is in the encrypted volumes which are not shown.

Rerun report when booted in UEFI mode & decrypted install.

---

### Post by Paddy Landau on 2022-04-29
> **oldfred said:**
> Do not know ventoy…
Ventoy allows you to simply put any number of ISOs on your USB stick, and boot from whichever one you want as a Live USB. You don't have to keep replacing the distro on the USB. It's a serious time-saver!
> **oldfred said:**
> … for Boot-Repair to work you need to boot live installer in UEFI boot mode
Ah. Maybe that's the problem. I couldn't boot in Secure Mode with Ventoy.

I'll create a new Live USB the standard way, and try Boot Repair again, but with Secure Boot. I'll report back here once I have the results, whether good or bad.

---

### Post by Paddy Landau on 2022-04-29
Alas, that made no difference.

To clarify: I booted a Live USB (Ubuntu 22.04) with Secure Boot turned on. I unlocked the LUKS partition, and enabled it in LVM, and checked that I could mount it correctly.

Here is the [Bootinfo summary]("https://paste.ubuntu.com/p/9h8Kk6BDHB/").

Might it work to chroot into my computer, and repair Grub from there? If I'm correct, I can chroot in, and run update-grub.

---

### Post by ubfan1 on 2022-04-29
Sounds like it could be launchpad bugs 1396379 or (older usb only) 1173457.  Grub bootloaders get written to the first disk (internal) regardless of where you indicate. However, part of grub is on the root which is on the external disk.  So of course, without the external disk, grub falls on its face.  If this is the case, see the workarounds in the bug and do add yourself to the "Does this affect me?" list on the 1396379 bug.

---

### Post by Paddy Landau on 2022-04-29
> **ubfan1 said:**
> … could be launchpad bugs 1396379 or (older usb only) 1173457.
You're right, it does sound like it. I've voted for the bugs ("Does this affect me?").

I'm going to chroot in, and repair Grub from there. I'll report back here with the results.

---

### Post by Paddy Landau on 2022-04-29
Success! &#127881;

I fixed it with chroot. In case someone else has this problem, here are the steps.

[LIST=1]
[*]Boot from a Live CD.
[*]Find the partition of your root on your computer. For this example, I'll call it /dev/sdXN (e.g. /dev/sda3), but obviously use the correct one for you (in my case, it was the logical LVM partition after it had been unlocked).
[*]Mount the partition.
```
sudo mount /dev/sdXN /media/ubuntu/root   # Create the folder if required
```
[*]If you have a separate /boot partition, find its partition (e.g. /dev/sda2) and mount it.
```
sudo mount /dev/sdXQ /media/ubuntu/root/boot
```
[*]If you have an EFI partition, find its partition (e.g. /dev/sda1) and mount it.
```
sudo mount /dev/sdXR /media/ubuntu/root/boot/efi
```
[*]Bind the relevant virtual folders. The easiest way is the following code.
```
for M in sys proc run dev; do sudo mount --bind /${M} /mnt/${M}; done
```
[*]Chroot in.
```
sudo chroot /media/ubuntu/root
```
[*]Look at / (root), /boot and /boot/efi to check that they look OK. If not, you have to go back and fix things.
[*]Reinstall Grub. Warning: You must choose the **device**, NOT the partition. So, /dev/sdX and **not** /dev/sdXN.
```
grub-install --boot-directory=/boot /dev/sdX   # Double-check!
```
[*]Rebuild Grub.
```
update-grub
```
[/LIST]
Exit chroot and reboot.

Thank you &#128591; for your input — you guided me to the right place!

---

### Post by oldfred on 2022-04-29
You may have been able to fix it without the full chroot which did work. That may have installed the signed versions for Secure boot.

Somehow UEFI Secure Boot was back on?
Line 235 showing grub in ESP, was still looking for this UUID, which still does not exist.
[FONT=arial]10002428-2df8-48ce-a96e-bd2349727968

If you changed that to your boot partition, it should have worked, if Secure boot was off.
a4108dfb-ea01-49ed-8de0-1c92cc7042bf[/FONT]

---

### Post by Paddy Landau on 2022-04-29
> **oldfred said:**
> You may have been able to fix it without the full chroot…
I thought that my method was chroot?
> **oldfred said:**
> Somehow UEFI Secure Boot was back on?
Yes, I turned it on as you had recommended.
> **oldfred said:**
> Line 235 showing grub in ESP, was still looking for this UUID, which still does not exist.
10002428-2df8-48ce-a96e-bd2349727968
I searched, and I found that that UUID is for the external USB hard drive where I had installed Ubuntu.

So, that explains it — exactly as you said, [bug 1396379]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379") messed with the Grub on my internal hard drive instead of placing it on my external USB drive.

---

