---
title: "Unable to Boot from Encrypted LVM after Upgrading to Ubuntu 21.04"
date: 2021-09-08
forum: Installation &amp; Upgrades
---

### Post by moonsquad on 2021-09-08
Greetings everyone,

Regrettably, my first post to this forum is a frustrating issue. Please bare with me though, as I am relatively new to the world of Ubuntu/Linux.

I have daily driven Ubuntu 20.04 on my work laptop for the last several months, but a week ago I had the wonderful inspiration to upgrade to Ubuntu 21.04. This upgrade resulted in my no longer being able to boot from my encrypted drive. 

My first troubleshooting steps involved booting up a live USB and launching the boot repair tool, but the options to do anything with GRUB or MBR are disabled/greyed out. Here is a [link]("https://paste.ubuntu.com/p/hJFs5Cqfzz/") to the pastebin output file.

[IMG]https://cloud.visipraxis.com/apps/files_sharing/publicpreview/jyTY69R7eJpP2WB?x=1920&y=626&a=true&file=Boot%2520Repair%2520Options.png&scalingup=0[/IMG]

I have also attempted to reinstall GRUB after decrypting and mounting the drive/partitions, but the system still refused to boot.

Here is an "lsblk" output for the drive:
> 
nvme0n1               259:0    0 465.8G  0 disk  
&#9500;&#9472;nvme0n1p1           259:1    0   512M  0 part  /mnt/boot-sav/nvme0n1p1
&#9500;&#9472;nvme0n1p2           259:2    0   732M  0 part  /boot
&#9492;&#9472;nvme0n1p3           259:3    0 464.5G  0 part  
  &#9492;&#9472;nvme0n1p3_crypt   253:0    0 464.5G  0 crypt 
    &#9500;&#9472;vgubuntu-root   253:1    0 463.6G  0 lvm   /
    &#9492;&#9472;vgubuntu-swap_1 253:2    0   980M  0 lvm   [SWAP]


Currently, the only way I can get the option to boot is by having the Ubuntu 21.04 live USB connected to the laptop as the primary boot option, and then selecting "Boot from next volume" from the GRUB menu to boot into my system.

At this point, I honestly have no idea what else I can try to get out of this predicament...

Any assistance with regards to this issue would be much appreciated.[IMG]https://cloud.visipraxis.com/s/jyTY69R7eJpP2WB[/IMG]

---

### Post by moonsquad on 2021-09-10
Does anyone perhaps have some suggestions as to the next course of action?

---

### Post by moonsquad on 2021-09-14
Bump.

---

### Post by tea for one on 2021-09-14
> **moonsquad said:**
> My first troubleshooting steps involved booting up a live USB and launching the boot repair tool, but the options to do anything with GRUB or MBR are disabled/greyed out. Here is a [link]("https://paste.ubuntu.com/p/hJFs5Cqfzz/") to the pastebin output file.

According to the boot-repair report, you are using your installed system to run the repair.

[COLOR="#0000FF"]Line 44[/COLOR] - OS#1:   The OS now in use - Ubuntu 21.04 CurrentSession on mapper/vgubuntu-root
[COLOR="#0000FF"]Line 59[/COLOR] - BootCurrent: 0004
[COLOR="#0000FF"]Line 62[/COLOR] - Boot0004* ubuntu	HD(1,GPT,99aae03a-413a-4d38-b45a-43ba36540445,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)

Possibly this is why boot-repair is having a difficulty?
Or something to do with encryption?

Anyway, after 6 days without a solution, I would bite the bullet and re-install 20.04 and restore your backups?

It's certainly frustrating that a working solution has not been forthcoming but one of the distinct advantages of Ubuntu is that a re-install of OS and data generally takes 60-90 minutes.

---

### Post by moonsquad on 2021-09-20
> **tea for one said:**
> According to the boot-repair report, you are using your installed system to run the repair.

[COLOR=#0000FF]Line 44[/COLOR] - OS#1:   The OS now in use - Ubuntu 21.04 CurrentSession on mapper/vgubuntu-root
[COLOR=#0000FF]Line 59[/COLOR] - BootCurrent: 0004
[COLOR=#0000FF]Line 62[/COLOR] - Boot0004* ubuntu    HD(1,GPT,99aae03a-413a-4d38-b45a-43ba36540445,0x800,0x100000)/File(\EFI\UBUNTU\SHIMX64.EFI)

Possibly this is why boot-repair is having a difficulty?
Or something to do with encryption?

Anyway, after 6 days without a solution, I would bite the bullet and re-install 20.04 and restore your backups?

It's certainly frustrating that a working solution has not been forthcoming but one of the distinct advantages of Ubuntu is that a re-install of OS and data generally takes 60-90 minutes.

Thank you for the response. Much appreciated.

I believe I posted the incorrect pastebin report originally. I since ran the repair tool on the live USB again, but the options were still greyed out after mounting and decrypting the drive. My guess is that the tool itself doesn't like encrypted drives for its repair process.

However, it certainly is frustrating that I have been unable to address this issue so far, and it would seem that a complete reinstall is calling...

I will need to set some time aside over a weekend to go through everything that will need to be reinstalled and configured before pulling the plug.

---

### Post by dogservant on 2021-09-21
What does your /etc/fstab files have? (specifically for "/", "/boot", and "/boot/efi" but the whole thing is fine)
Contents of /etc/crypttab (probably a single line)
Also include the value of GRUB_CMDLINE_LINUX from /etc/default/grub

If you haven't added any, there is unlikely to be any sensitive info in them, but do check and sanitize.

If you can boot into the installed system, have you tried running update-grub?

---

### Post by TheFu on 2021-09-21
> **dogservant said:**
> What does your /etc/fstab files have? (specifically for "/", "/boot", and "/boot/efi" but the whole thing is fine)
Contents of /etc/crypttab (probably a single line)
Also include the value of GRUB_CMDLINE_LINUX from /etc/default/grub

If you haven't added any, there is unlikely to be any sensitive info in them, but do check and sanitize.

If you can boot into the installed system, have you tried running update-grub?

The boot-info link above, contains all that information.
I doubt boot-repair can do anything with encrypted storage.

The easy answer is to backup all the data and settings, then do a fresh install of the OS you want to keep.  Depending on the data amount and how good the backups are (not just the files, but the owner, group, ACLs, xattrs, etc... are needed too), then the new install should be 15 minutes. Restoring the settings and up to 20G of personal data is another 15 min, then feeding the list of programs previously manually installed should be 5-15 minutes.  So ... in less than 45 minutes, with good backups, the system can be restored.  And with really good backups, you can move the entire system to a new computer in that same time, typically.

Once you have backups automatic and restores practiced 4-10 times, you'll know exactly how to do this stuff well and if any problem takes more than 1 hr to fix, you'll wipe the system and restore from the backup version just prior to the time when the issue started.  There are lots of other uses for versioned backups too.  They aren't really hard to create. 
[Https://ubuntuforums.org/showthread.php?t=2465713&p=14052751#post14052751](Https://ubuntuforums.org/showthread.php?t=2465713&p=14052751#post14052751)

If you just want your HOME directory, the backup is even easier, but without the list of installed programs and the settings for those programs, the restore process will be hours, not minutes.

---

### Post by moonsquad on 2021-10-15
Well, the strangest of things happened...

I was gearing up for a re-install and backup this weekend, when I neglected to insert the bootable flash into the laptop on first boot upon arriving at the office. Lo and behold, the system miraculously booted without issue, allowing me to decrypt the drive prior to system boot. Since I assumed this was an anomaly at first, I proceeded to reboot and shutdown the system several times to confirm consistency. Well, the problem seems to have miraculously resolved itself...

Thanks for all of the helpful insight gentlemen! Much appreciated. I will proceed to close this thread as resolved.

---

