---
title: "Boot failed on clean install to Acer Aspire E15 laptop"
date: 2015-08-06
forum: Installation &amp; Upgrades
---

### Post by DarkerStar on 2015-08-06
I tried installing 15.04 to a brand new Acer Aspire E15 laptop (that came with Windows 8 or 8.1) from a live USB. The installation went off without any warnings, but it won't boot to the HDD (live USB still works fine).

I tried searching for related problems, but just about every one was about trying to dual-boot Windows/Ubuntu - I did a full, clean install of Ubuntu (using the installer option to wipe the existing HDD partitions). The remainder suggested using boot-repair, so I tried that. That, too, worked without a warning, but it still won't boot from the HDD. The output is here: [http://paste.ubuntu.com/12015975/]("http://paste.ubuntu.com/12015975/")

(A couple threads also suggested manually enabling the boot flag on the boot partition, but when I checked with gparted, it was already set.)

During boot, there are a few errors flashed briefly before the "default boot device missing or boot failed" error. They flick by quickly, but they look like they say there's a missing "/EFI/Microsoft/Boot/grubx64.efi", and then another one with a similar name but that seems to have the word "manager" in it.

This is my first time installing Ubuntu on a device with UEFI, so it's entirely possible I just missed some common and obvious step that disables some security thing. For example, in the BIOS there are options to "erase all secure boot settings", "select an UEFI file as trusted", and "restore secure boot to factory default" - I didn't touch any of those. One thread led me to a video about "unlocking hidden pages" in the InsydeH20 BIOS manager, but that only seems necessary to enable virtualization.

---

### Post by oldfred on 2015-08-06
You have erased Windows, was that your intent?

Every Acer so far has had to set a password to open up additional settings & then you have to enable trust on the Ubuntu boot files.

       Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

If not booting Windows you can do another work around that some others have to use, but better to set trust.

You also have flash drive as sda, normally it is sdb or some much higher letter like sdf. That may be confusing things a bit.
Also remove flash drive before rebooting. And when you boot run this:
sudo update-grub

---

### Post by DarkerStar on 2015-08-06
Your tip did it! I had to "select an UEFI file as trusted", then choose HDD0(my main HD)/EFI/ubuntu/grubx64.efi - then it booted up fine! I'll mark this as solved.

But, just for completeness, let me answer your other questions:

> **oldfred said:**
> You have erased Windows, was that your intent?

Yes, it was. I now have a Vivid laptop with complete access to the HDD - no partitions clogged up with Windows or recovery junk.

> **oldfred said:**
> Every Acer so far has had to set a password to open up additional settings...

About this - yes, for anyone else reading this, you have to set a *supervisor* password (not a *user* password) in the BIOS, and enter it, before the boot options activate. Otherwise they're greyed out.

> **oldfred said:**
> ... & then you have to enable trust on the Ubuntu boot files.

       Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)

If not booting Windows you can do another work around that some others have to use, but better to set trust.

That was the trick! Setting the grubx64.efi file as trusted worked perfectly. (There were other .efi files available, but I only set grubx64.efi as trusted, and it booted. I suppose those are for other boot options, memtest, and stuff, right? I could make them trusted later if needed, I guess.)

> **oldfred said:**
> You also have flash drive as sda, normally it is sdb or some much higher letter like sdf. That may be confusing things a bit.

Yeah, that bugged me a bit. The first time I ran the live USB it correctly set the HDD to sda and the USB drive to sdb. The second time - after it failed to boot and I was using boot-repair - it swapped the two.

But now that it's booted correctly to the HDD, the HDD is sda. So maybe it was just because of the boot order that the live USB got priority.

> **oldfred said:**
> Also remove flash drive before rebooting. And when you boot run this:
sudo update-grub

Should I still do that?

When it booted I got a grub menu with a couple options (I didn't read them all carefully - was too happy it was booting), and a delay of a few seconds before it booted into Ubuntu proper. I *think* boot-repair set that up. From the manpage, update-grub seems to just call grub-mkconfig, which seems to just generate a grub config file. Would update-grub remove the stuff boot-repair did, and make it so there is no grub menu visible by default (because I'm not dual-booting)?

---

### Post by oldfred on 2015-08-06
Not sure if Boot-Repair changes default setting to always show grub menu or not. It shows unhide boot menu setting, but do not know if that is always. I change mine to 3 seconds, also.

The reason for the sudo update-grub is that grub menu has inside it a lot of hd1,gpt2 settings.
The hd1 is referring to install on second drive or sdb. It should be hd0.
But since system uses UUIDs it boots ok, so not a major issue.

I do not know if the pastebin you posted is before or after Boot-Repair's changes.
But this is the only difference in standard grub setting.
#GRUB_HIDDEN_TIMEOUT=0
     
You can remove # to make it like it was.
sudo nano -B /etc/default/grub    
-B is backup copy created.

After any change to any grub configuration:
sudo update-grub

---

