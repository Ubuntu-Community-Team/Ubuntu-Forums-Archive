---
title: "Weird grub (?) failing problem."
date: 2020-04-25
forum: Installation &amp; Upgrades
---

### Post by 2912pwil on 2020-04-25
Weird grub (?) failing problem.

I’ve used Ubuntu since 2007.  Never particularly had really difficult  issues.  My 5-yr old Dell 15 was creaking and started getting unreliable so bought a new one, Dell Inspiron 15 3593, with Uefi – UEFI being new to me - as with the lockdown have the time to transfer everything.  Came with Windoze 10 & planned to run it dual-boot.
[https://www.dell.com/en-uk/shop/laptops-notebooks-and-2-in-1-laptops/inspiron-15-3000/spd/inspiron-15-3593-laptop/cn33504](https://www.dell.com/en-uk/shop/laptops-notebooks-and-2-in-1-laptops/inspiron-15-3000/spd/inspiron-15-3593-laptop/cn33504)

I’ve now installed 20.04 (official LTS version, 1st installed 24th) at least 6 times, weird problem. 
- Partitioned disk, Windows about 100Gb, various bits that came with the box, spare 100Gb, Ubuntu ext4 100gb, the rest a data partition 
- Comes up with grub options ..
- Ubuntu
- advanced options Ubuntu
- Windows Boot manager
- Uefi

But oddly.. sometimes trying booting into Ubuntu works, ditto Windoze, sometimes (usually) it doesn’t.  And seems to usually fail thus…
- error: command failed (x several..) then…
- error: you need to load the kernel first…
 behaviour seems random. 

As mentioned, re-installed Ubuntu wiping Ubuntu partition, several times.

I’ve also set Secure boot off..

When Ubuntu works it then runs fine, although the boot times are way way longer than my 5-yr old dell.  20.04 seems pretty good!

Any suggestions please?  I’m stuck!  Let me know if there's any further info that would help. Any advice gratefully received, best wishes everyone & stay safe!

2912pwil

---

### Post by oldfred on 2020-04-25
Have you updated UEFI?
Dell now also updates from Linux.

Fwupd 1.4 brings with it many improvements  April 20, 2020
[https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-1.4-Released](https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-1.4-Released)

It is strange that it works sometimes. Usually error is related to older info being used to try to boot that then does not work.

This shows boot configuration, may show something.
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
fwupx64.efi
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

---

### Post by 2912pwil on 2020-05-07
(Belated) thanks Fred!.  My father, born 1903, was a Freddie: A PoW during WW2, (captured after Dunkirk - along with 50000 others) spent the rest of the war in what is now Poland.  Eventually liberated by US forces, thanks guys!  He was always keen on Americans for the rest of his 94-years, genuine many thanks for that, USofA services!

Tried various things including Boot repair, same symptoms.  In the end decided to reset through UEFI/BIOS all I could - factory default settings, BIOS settings - then fresh re-install of Windows 10 (Dell downloadable USB system, very thorough) 
[https://www.dell.com/support/article/en-us/sln130027/factory-reset-restore-or-reinstall-microsoft-windows-on-a-dell-computer?lang=en](https://www.dell.com/support/article/en-us/sln130027/factory-reset-restore-or-reinstall-microsoft-windows-on-a-dell-computer?lang=en)

and then fresh 20.04 UBU install.  Nice...I thought it would all be OK....
- but same symptoms.  Fails re-boot from time2time, Grub timing changes from 10 to 30 secs countdown (I THINK from either re-booting Windows or UEFI settings ..). 

- and really long boot times...

Secure boot is switched off, sleep also as far as I can tell in both Windows & Ubuntu

I'll get grub-repair done again & post info.

Best wishes to all forum members..

---

### Post by oldfred on 2020-05-07
Is it a failed to boot or extremely slow boot?

We have seen where an entry in fstab, if invalid takes a long time to time out before it completes boot.
Examples were where second install reformatted swap and changed UUID. Or mount of NTFS and Windows turned fast start up back on with an update, so normal mount would not work.

And sometimes other processes take more time. I have seen where connecting to Internet is a repeated entry in my log files, sometimes just a few tries and other times many, but my system has NVMe drive & fast Internet, so I rarely notice any real change in boot time.

You can look in /var/log/syslog  and other log files.
Typically warnings can be ignored although checking to see if major issue may have a suggestion.

I added to this bug as my system repeatly shows this error. But it still boots quickly.
[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1799213](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/1799213)

---

### Post by xandey on 2020-05-19
@2912pwil did you solve this issue? I'm seeing what seems to be exactly the same thing. I get stuck in grub sometimes during reboots. It's pretty tricky to figure out why.

@oldfred. For me it completely blocks booting. You type "sudo reboot" then when it gest to grub it has a bunch of:
- error: command failed (x several..) then&#8230;
- error: you need to load the kernel first&#8230;
shown on the monitor and the only way to get it to work is power off then back on and it comes back up.

edit: Oh and I have already updated the bios to latest 1.8 via a usb method. I also tried disabling secure boot (although I installed with it on).

---

### Post by oldfred on 2020-05-19
@xandey
Please start your own thread. 
Although boot issue may seem similar, hardware & issues are often unique.
Run Boot-Repair & post link your new post.
What brand/model system?
What video card/chip?
What flavor of Ubuntu?

---

### Post by boatman1900 on 2020-05-19
i am going thru similar problems at the moment, I have an acer aspire e14 which had windows 10 on and i installed Kubuntu 18.04 as a dual boot worked for 18mths no problem the last windows update crapped the system totally. I am fairly used to grub problems with windows updates etc.. Am a linux user for 15+ years. My current laptop appears to have an imbeded windows bootloader which seems to be overriding all attempts to adjust efi boot files. I get no boot device all the time, having done a complete new install just for Kubuntu (3 times) whole disk for Kubuntu IT won't boot... Using live Kubuntu usb boot...

Cant even get windows 10 1909 on usb to boot..., Uefi problem....(yes) am trying to figure out how to change boot loader not grub2 but the (windows, efi) boot loader that has no boot options...
have tried most i can find on the web, all failed....

Will update when i get there.

---

### Post by oldfred on 2020-05-19
@boatman1900
Please see post #6, and start your own thread with same info. Also put Acer model as first part of title.
Acer often has issues with "trust" setting in UEFI addition to some other typical issues.
I mention trust in link in my signature for Acer, but now have some newer links on users who set trust.

---

### Post by xandey on 2020-05-20
@oldfred thanks for the recommendation. The problem may have stopped at this point. Google sent me to this thread so I figured adding might help someone.

I did muck with the uefi defaults from the BIOS. The bios had two uefi targets and I told it to use one of them maybe there was some race condition as to which one it chose.

I had the same laptop as the OP Dell Inspiron 15 3593, did a minimal clean install of 20.04 desktop.
* cold boot worked every time
* reboot sometimes would get stuck in the same.

Anyway, if it comes back I'll post a new thread and try boot-repair.

---

