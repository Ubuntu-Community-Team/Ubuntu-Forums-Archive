---
title: "(dual boot) Windows crashed and repaired itself, now I can't install GRUB"
date: 2019-08-13
forum: Installation &amp; Upgrades
---

### Post by shadetree01010100 on 2019-08-13
I was using my Windows partition (games) when it locked up and rebooted. After running chkdsk or whatever it was doing, I tried to reboot to Ubuntu (time to get back to work) but there was not the usual OS selection screen. So I followed the second method here, since I have installation media on hand: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Recommended repair was not successful, here's the pastebin: [http://paste.ubuntu.com/p/RtM5zpbCQy/](http://paste.ubuntu.com/p/RtM5zpbCQy/)

My BIOS only sees the Windows boot loader on that HDD.

Thanks in advance.

---

### Post by shadetree01010100 on 2019-08-13
OK the error reported was from bootrepair being unable to mount an additional HDD, it actually did succeed in fixing GRUB but, as the last line of the pastebin says, needed me to [COLOR=#000000]change the default boot entry of the Windows bootloader, i.e. ```
[/COLOR][COLOR=#000000]bcdedit /set [/COLOR][COLOR=#666666]{[/COLOR][COLOR=#000000]bootmgr[/COLOR][COLOR=#666666]}[/COLOR][COLOR=#000000] path [/COLOR][COLOR=#BB6622]**\E**[/COLOR][COLOR=#000000]FI[/COLOR][COLOR=#BB6622]**\u**[/COLOR][COLOR=#000000]buntu[/COLOR][COLOR=#BB6622]**\s**[/COLOR][COLOR=#000000]himx64.efi
```[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by oldfred on 2019-08-13
It says it correctly installed grub in UEFI mode correctly.

But error is related to mount of sda1 which it is just showing as unknown. 
If that was NTFS, you need to run chkdsk from Windows.
If it was ext4, you need to use live installer and run fsck on it.

Report seems to also be missing fstab? Report issue or missing fstab?
Was fstab mounting sda1 and that is what is preventing boot. Or is fstab now missing?

---

### Post by shadetree01010100 on 2019-08-13
/dev/sda I'm not really using, it's just installed in the machine. It's a very small case so I stuck the drive in while I had access. No idea what its file system is, I'll format it when I need it.

I don't know what fstab is, how do I answer if it's missing?

---

### Post by oldfred on 2019-08-13
What brand model system?
With nVidia you may need nomodeset or did it install nVidia driver?

You will need to partition & format partition(s) on new drive. Be sure to use gpt partitioning. I believe gparted still defaults to the very old MBR, and you have to first change to gpt before anything else.

Is there no entry in your UEFI boot menu?

It shows solved, so is it now working?

---

### Post by shadetree01010100 on 2019-08-14
I built this system about 6 months ago, it's an AMD Ryzen 5 2600 with an RTX2060 (nVidia driver).

My M.2 SSD ([COLOR=#000000]/dev/nvme0n1 [/COLOR])is partitioned into Ubuntu and Windows, and I have an old 1TB laptop drive (/dev/sda/) that I stuck in while the case was open (small form factor, naturally). I intended to format it so that both OS can access it, but I don't remember that I ever got around to it (network storage is just so convenient).

I now have more entries than before in my boot menu, but importantly, one of them is Ubuntu, so for all intents and purposes this is solved. I made the switch from Windows 7 to Bionic this year (and I'm only holding onto the Windows 10 partition for games) so I suspect that I've done a few things wrong in this build that caused some issues with boot repair.

Thank you for the advise on gpt, and taking the time to help. Any remaining issues I think are now unrelated to boot repair.

Thanks again!

---

