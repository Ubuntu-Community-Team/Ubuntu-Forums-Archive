---
title: "Windows not working after upgrade to 12.10"
date: 2012-10-28
forum: Installation &amp; Upgrades
---

### Post by TigerFr on 2012-10-28
Hello,

I have been using Ubuntu for several years with the dual boot on my computer. And today Windows 7 is not booting anymore after the upgrade to Ubuntu 12.10. It displays the "A disk read error has occured" message just after selecting it in Grub.

Boot-repair generates this report : [http://paste.ubuntu.com/1311907/](http://paste.ubuntu.com/1311907/)

Can someone help me ? Many thanks.

MM

---

### Post by Sadi58 on 2012-10-28
I have also encountered various dual-boot problems with Windows 7 and Ubuntu 12.04/12.10.
When Windows failed to boot properly, I used Windows Rescue Disk.
When Ubuntu failed to boot properly, I used the Plop Boot Manager and then simply re-installed grub.
I hope this can be helpful for you as well.

---

### Post by mag1strate on 2012-10-28
Does win7 work when chosen from the boot menu of your BIOS?

---

### Post by TigerFr on 2012-10-28
@Sadi58 : I don't have any Windows CD or DVD as I have a recovery partition.

@mag1strate : I can't boot with my BIOS as it only provides me the choice between different drives when I press F12.

Thank you anyway.

---

### Post by darkod on 2012-10-28
I don't see anything wrong in the bootinfo details, only that the win7 entry has some reference to ldm which I haven't seen before. But maybe that's how 12.10 works. I use 12.04 because it's LTS.

You can try this:
Boot the computer and at the grub menu hit 'c' for a command line. At the command prompt execute one by one:
```
insmod part_msdos
insmod ntfs
set root=(hd0,3)
chainloader +1
boot
```

See if that boots win7.

---

### Post by TigerFr on 2012-10-28
> **darkod said:**
> I don't see anything wrong in the bootinfo details, only that the win7 entry has some reference to ldm which I haven't seen before. But maybe that's how 12.10 works. I use 12.04 because it's LTS.

You can try this:
Boot the computer and at the grub menu hit 'c' for a command line. At the command prompt execute one by one:
```
insmod part_msdos
insmod ntfs
set root=(hd0,3)
chainloader +1
boot
```See if that boots win7.

Please, don't be offended but is there a risk that this operation could damaged the GRUB ? Currently I have Ubuntu and not Windows, I don't want to loose both...

---

### Post by darkod on 2012-10-28
No, it can't. I'm trying to establish whether only the entry for win7 is "bad", or it's win7 that's bad somehow.

Those commands should try to boot it directly with manual commands avoiding the entry in the grub menu.

But it doesn't change anything in grub2 or its configuration.

---

### Post by TigerFr on 2012-10-28
Ok, Win7 boots correctly !

---

### Post by darkod on 2012-10-28
OK. In that case boot ubuntu, open terminal and run:
sudo update-grub

Restart and see if the win7 on /dev/sda3 entry created can boot win7 correctly or not.

---

### Post by TigerFr on 2012-10-28
Sorry, it's not working !

---

### Post by anbessa on 2012-10-28
HI, 

I have the same problem but with Windows 8, but sudo update-grub does not add any new entry to grub.

Can I add manually a Windows 8 entry to grub2? how?

Thanks

---

### Post by darkod on 2012-10-28
> **anbessa said:**
> HI, 

I have the same problem but with Windows 8, but sudo update-grub does not add any new entry to grub.

Can I add manually a Windows 8 entry to grub2? how?

Thanks

Check on which partition you have the boot flag with:
sudo parted -l (small L)

Then use that partition in the set root= command in the manual procedure to boot windows I posted earlier. If that boots win8, OK, you can easily make a custom entry.

If it doesn't boot it, then there is probably a more complex issue and you should open a new thread since the problem will be different from this one. You should also post the bootinfo from boot-repair in that new thread so that we can see more details.

---

### Post by TigerFr on 2012-10-29
> **TigerFr said:**
> Sorry, it's not working !

I guess I will have to create a manual command...

---

### Post by darkod on 2012-10-29
> **TigerFr said:**
> I guess I will have to create a manual command...

I missed that post. OK, try this. Open the 40_custom file for editing with:
gksu gedit /etc/grub.d/40_custom

In it, create a menuentry like:
```
menuentry 'Windows 7 on /dev/sda3 MANUAL' {
   insmod part_msdos
   insmod ntfs
   set root=(hd0,3)
   chainloader +1
}
```

Basically the same manual commands except the boot at the end. Save the file and run sudo update-grub again.

Reboot and the new entry should be added at the end of the grub menu. See if it works.

If it doesn't you might need to add one line more in your custom entry, so that windows thinks it's on the first disk. Since there is only one disk I am not sure you need it, and I don't remember the exact syntax right now, have to look for it. lets see if this works first.

---

### Post by TigerFr on 2012-10-29
Ok, it is working great. Thank you very much. I guess the issue will be solved with a patch in the future directly in grub...

---

### Post by YannBuntu on 2012-10-30
Hello, and welcome among us :)

> **TigerFr said:**
> Ok, it is working great. Thank you very much. I guess the issue will be solved with a patch in the future directly in grub...

It won't if you don't report the issue. I can report it for you, but it will be more efficient if you do it:
1) Create your [Launchpad]("https://launchpad.net/") account if you haven't yet
2) Login to your Launchpad account
3) From your Ubuntu, open a terminal, and type:
```
ubuntu-bug grub2
```
Press Enter.
This will gather information, and open a new internet window.
4) Fill in the bug title, eg "invalid Windows entry in GRUB2.00"
5) Fill in the bug description, eg > "Ubuntu12.10 and Windows7 dualboot. Default Windows entry in GRUB menu fails to load Windows:
```
menuentry 'Windows 7 (loader) (sur /dev/sda3)' --class windows --class os $menuentry_id_option 'osprober-chain-CC0CC8FE0CC8E494' {
	insmod ldm
	insmod ntfs
	set root='ldm/f4f4081f-1997-11e0-809d-0022fb714c30/Volume1'
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root --hint-bios=hd0 --hint-efi=hd0 --hint-baremetal=ahci0 --hint='ldm/f4f4081f-1997-11e0-809d-0022fb714c30/Volume1'  CC0CC8FE0CC8E494
	else
	  search --no-floppy --fs-uuid --set=root CC0CC8FE0CC8E494
	fi
	chainloader +1
}
```
The following custom entry is able to boot Windows: 
```
menuentry 'Windows 7 on /dev/sda3 MANUAL' {
   insmod part_msdos
   insmod ntfs
   set root=(hd0,3)
   chainloader +1
}
```
Original thread: [http://ubuntuforums.org/showthread.php?t=2077278](http://ubuntuforums.org/showthread.php?t=2077278)
6) then finish the bug report, and indicate us (here) the link (URL) to the report so that we can follow-up.

Reporting bugs in a very efficient  way of contributing to Ubuntu and FOSS in general. Thanks for participating ;)

---

### Post by TigerFr on 2012-10-30
Here is the link : [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1073281](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1073281)

Thank you very much.

---

### Post by YannBuntu on 2012-10-30
good job. Now let's wait for an answer from the GRUB developers...

---

