---
title: "Triple dual boot Ubuntu 11.10 and two Windows on different disks"
date: 2012-08-22
forum: Installation &amp; Upgrades
---

### Post by xdbhk on 2012-08-22
I have had Windows XP and Windows 7 installed on a hard drive. I want to install Ubuntu 11.10 on another hard drive. The two Windows can boot dually well.

When I installed Ubuntu, I couldn't start Windows XP anymore. I opened Windows 7 System Startup in Control Panel and saw that Windows XP boot line disappeared. I couldn't run bcdedit.exe to modify the bootmgr either. But if I erased Ubuntu, the two Windows works well again, and the XP boot line appeared again.

Why was that, and how to fix it? Please help me!
Thanks

---

### Post by oldfred on 2012-08-22
Post link to BootInfo from this.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

Which drive was set as boot drive in BIOS? Windows sometimes installs its boot files to the other drive.

Info on Windows dual booting. Discusses Vista but 7 is the same.

To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by xdbhk on 2012-08-23
I read the multi-boot process webpage. It 's very informative. Thanks!

I tried the Boot Repair and it recorded the information at:
[http://paste.ubuntu.com/1162996/](http://paste.ubuntu.com/1162996/)

I don't understand much of the information, so I couldn't guess what trouble is. Would you please take a look at it and give me your advice?

Thank you very much!

---

### Post by YannBuntu on 2012-08-23
@xdbhk: If I were you, I would:
1) try to move /bootmgr file and /Boot folder from sdb1 to sdb2, then open a terminal in Ubuntu and type "sudo update-grub".
2) if still not good, try the fix described by oldfred's link (ubuntuforums.org/showthread.php?t=1271600&page=1 ): reinstall XP, then remove the bootflag, then install Seven, then recover GRUB.

---

### Post by Cavsfan on 2012-08-23
I have a custom grub that never has to be changed.

Just copy this

```
#!/bin/sh
echo 1>&2 "Adding Ubuntu Oneiric Ocelot 11.10, Windows XP and Windows 7"
exec tail -n +4 $0 
# This file provides an easy way to add custom menu entries.  Simply type the 
# menu entries you want to add after this comment.  Be careful not to change 
# the 'exec tail' line above (unless on Natty or later then change +3 to +4).
menuentry "Oneiric Ocelot 11.10" {     
    set root=(hd0,1)         
    linux /vmlinuz root=/dev/sda1 ro quiet splash         
    initrd /initrd.img 
} 
menuentry "Oneiric Ocelot 11.10 (Recovery Mode)" {     
    set root=(hd0,1)         
    linux /vmlinuz root=/dev/sda1 ro single         
    initrd /initrd.img 
}
menuentry "Windows XP" {
    insmod ntfs     
    set root='(hd1,1)'     
    search --no-floppy --fs-uuid --set 28E826DCE826A7D0     
    chainloader +1
}
menuentry "Windows 7" {
    insmod ntfs     
    set root='(hd1,2)'     
    search --no-floppy --fs-uuid --set 8CF87442F8742C98     
    chainloader +1
}
``` into a gedit notepad record and save it as **06_custom** in your home directory.
Then in terminal enter **ls -l** to make sure 06_custom is there.
Then enter **sudo mv 06_custom /etc/grub.d/** 
Then in terminal enter **sudo chmod +x /etc/grub.d/06_custom** 
Then  **sudo update-grub**
Then reboot and you have access to all three and they should display at the top

Windows 7 and XP might be backwards and if so, just edit the above file with 
**gksu gedit /etc/grub.d/06_custom**
and cut and paste the lines between menuentry and } to switch them around.
If you want to change the default enter **gksu gedit /etc/default/grub**

The line **GRUB_DEFAULT=0** means default is the first thing. It starts 0,1,2,3 etc. If you want it to default on the 4th one XP you would put 3 there.
Also the default timeout is there too. **GRUB_TIMEOUT=60** 
I have mine set to 60 seconds but, you can change that to whatever you want.

Just remember any time you change grub to enter **sudo update-grub**

Edit: when you select either Windows 7 or XP, you will probably see an error "no arument exists, press enter to continue".
Just ignore that. If you wait or press any key it will go into Windows.
It is just a bogus error message.

---

### Post by Cavsfan on 2012-08-23
If that doesn't get you there **xdbhk**, that will get you close and we'll go from there.

---

### Post by Cavsfan on 2012-08-24
I didn't mean to step on any toes here. Just thought I'd throw in my 2 cents. :)
Just thought that would be a quick workable solution.

---

### Post by xdbhk on 2012-08-24
YannBuntu, I can't open the /Boot folder in Windows although I can see it from Ubuntu, so I it can't be moved either. 

I'll reinstall Windows again, XP and 7, on HD 500gb. Then I'll reinstall Ubuntu on HD 80gb. My question is: 
1. Which HD should boot first, the Ubuntu or Windows HD?
2. How can I do that? Modify BIOS or switch the cables?

Cavsfan, thanks for the guidance of grub. I think it's very useful when I install Ubuntu.

---

### Post by oldfred on 2012-08-24
Do you want two boot entries in grub2's menu or the standard one?

Windows second install will move its boot files to the primary NTFS partition with the boot flag, so grub2's os-prober will only find one install. Then from Windows you should get a menu to boot either Windows. But if you want to split the boots so you can boot both directly from grub then you ;have to move boot flag before second install of Windows.

If you use the auto install options in Ubuntu it will probably install grub2's boot loader in the MBR of sda or your Windows. You should make sure to install the grub2 boot loader to the MBR of sdb, the Ubuntu drive and set BIOS to boot it.

But the only way you get a choice on where to install the boot loader during install is with Something Else or manual install. You can with Boot-Repair update after the fact but best to install correctly first.

Installer has not really changed so these are still correct instructions.
Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png]("http://members.iinet.net.au/%7Eherman546/p24/041.png")

---

### Post by Cavsfan on 2012-08-24
> **xdbhk said:**
> Cavsfan, thanks for the guidance of grub. I think it's very useful when I install Ubuntu.

You are welcome. You're in better hands with **oldfred** as he knows more about what you are trying to do.

But, once you get all three installed the above should work. You will have to enter **sudo blkid** in terminal to get the UUID to put here in red
```
search --no-floppy --fs-uuid --set [COLOR=Red]8CF87442F8742C98[/COLOR]
```For Windows 7 and the one for XP and you should be good to go.
If you like that (just the 4 entries), you can make the other stuff unexecutable like memtest, etc.
Just look in the how to in my signature towards the bottom of the first entry. There is my current grub screen on the last post.
I change it up from time to time as I get bored.

---

### Post by YannBuntu on 2012-08-27
**@Oldfred:** FYI [https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/1042177](https://bugs.launchpad.net/ubuntu/+source/os-prober/+bug/1042177)

> **xdbhk said:**
> YannBuntu, I can't open the /Boot folder in Windows although I can see it from Ubuntu, so I it can't be moved either.

You can try via a root browser ("gksudo nautilus"). If still not good, just reinstall everything as described by Oldfred.

---

### Post by oldfred on 2012-08-27
@Yann,
It is not a bug in grub2's os-prober, but the way Windows installs. Windows only installs boot files to the boot flagged partition. A second install of Windows literally moves all the boot files to the first install. Some then delete the first install and cannot boot. Second installs can be to logical partitions but still only boot thru primary. If primary boot partition is deleted then an install in a logical will not boot. (Some exceptions for XP with lilo and maybe syslinux, but not Windows in MBR).

To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

### Post by YannBuntu on 2012-08-27
As XP boot files (boot.ini/ntldr) are still present in the partition, why os-prober wouldn't be able to create any entry for XP?

---

### Post by oldfred on 2012-08-27
It only creates one boot entry per partition, but I think that is because the PBR - partition boot sector only says to boot either ntldr or bootmgr. 

When I ran a Windows 7 chkdsk on my XP partition it also wrote a new PBR with Windows 7. In testdisk I could see the plain text bootmgr not ntldr. I ued testdisks side by side compare of boot sector and backkup BS. I then reinstalled the XP PBR and it went back to ntldr. 

The grub chain entry is actually to the partition's PBR to use that code to boot, so only one system file will be used tp boot (ntldr or bootmgr), but then boot.ini or BCD may list more than one  Windows install.

---

### Post by xdbhk on 2012-08-31
Sorry that I was so busy to return here.

I tried both ways of YannBuntu and Cavsfan, but they didn't work. I decide to re-install the three OSes again, but I don't know how to remove the flag after installing Windows XP on the first partition. Please show me in detail since I am not an experienced one in these issues.

I have the two HDs: 80gb (first boot in BIOS) and 500gb (second boot).
I want to install Ubuntu 11.10 on the first HD, and XP and Windows 7 on the second.

My steps should be as follows:

1. Unplug the HD 80gb.
2. Plug the HD 500gb, prepare 3 partitions: 2 primary and 1 logical
3. Install XP on the first partition, and remove the flag
4. Put the flag on the second partition and install Windows 7 on it
5. Plug the 80gb HD and install Ubuntu on it (but put grub on MBR or just Ubuntu partition?)
6. Put grub on MBR of 500gb HD too?
7. Any needed steps ....

Please adjust those steps above in detail with guidelines.
Thanks!

---

### Post by oldfred on 2012-08-31
That basically should work. Install grub to the MBR of the Ubuntu drive and let Windows install its boot loader to the MBR of the Windows drive. Only the partition with the boot flag will directly boot on the Windows drive, but grub should add entries for either one. Set BIOS to boot Ubuntu drive.

Windows prefers to be the first drive and when XP is installed to one drive only boot.ini is hard coded to rdisk(0) or first drive. 
I think Windows 7 is more like Ubuntu in using something like UUIDs so it finds the correct partition to boot.
So after the Ubuntu install make it the second drive in BIOS. 

You can use gparted to change boot flag. Click on partition and right click manage flags. In Windows you use the make active command.

---

### Post by xdbhk on 2012-09-01
I did as above, just remove the flag on partition 1 of Windows XP, and run sudo update-grub after plugging the Ubuntu disk. The system works well now. The two Windows appear on grub at startup. So now I understand that the only problem was the flag on XP partition.

Thank you very much!

---

### Post by Cavsfan on 2012-09-03
> **xdbhk said:**
> I did as above, just remove the flag on partition 1 of Windows XP, and run sudo update-grub after plugging the Ubuntu disk. The system works well now. The two Windows appear on grub at startup. So now I understand that the only problem was the flag on XP partition.

Thank you very much!

Just a thought. This is probably not worth much but, I removed the boot flag on my windows 7 partition by mistake and it would not go to sleep until I put the boot flag back.
Not sure if XP works the same or not.

---

