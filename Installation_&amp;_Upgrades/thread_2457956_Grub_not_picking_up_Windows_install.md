---
title: "Grub not picking up Windows install"
date: 2021-02-13
forum: Installation &amp; Upgrades
---

### Post by Lee_Nowell on 2021-02-13
Hi All,

I have an old Windows 7 PC which I upgraded to Windows 10 had issues and used the Windows 10 feature to restore it back to my Windows 7 build.  This seems to have resulted in a small Windows 10 partition followed by my Windows 7 partition on the disk.  I then installed Ubuntu 20.04 on final partition and the build picked up the dodgy Windows 10 partition rather than the Windows 7 one.

I tried running boot-repair as suggested in the documentation and it added a second entry for the dodgy Windows 10 install and still nothing for Windows 7.  The url for the boot-repair is

[https://paste.ubuntu.com/p/23Chkszzjm/](https://paste.ubuntu.com/p/23Chkszzjm/)

Thanks in advance for your help

Lee.

---

### Post by yancek on 2021-02-13
>  I have an old Windows 7 PC which I upgraded to Windows 10 had issues and  used the Windows 10 feature to restore it back to my Windows 7 build.

After doing this and rebooting, were you able to successfully boot into windows 7?  A newer version of windows will generally overwrite the boot files of an older windows. 

What does the menuentry in the /boot/grub/grub.cfg file for windows 7 (/dev/sda2) look like?  Post it here.  It should look like the entry below.  You can test this on boot without making changes to the grub.cfg file.  When you see the grub menu, hit the c key on the keyboard and enter the lines consecutively, hit the Enter key after each line and you should then see the grub prompt (grub>) where you enter the next line.  Don't use the first line below beginning with menuentry.

> menuentry "Windows 7" {
insmod part_msdos
insmod ntfs
set root='(hd0,msdos2)'
chainloader +1
}

---

### Post by Lee_Nowell on 2021-02-13
Hi Yancek,

Yes once I went back to Windows 7 it booted fine straight into Win 7 as before.  TBH I didn't know anything about the Win 10 partition until Ubuntu showed it in gparted

Unfortunately there isn't a menuentry for Windows 7 but there are 2 for Windows 10 (both boot up to the Win 10 partition).  The entries are

```

### BEGIN /etc/grub.d/30_os-prober ###
menuentry 'Windows 10 (on /dev/sda1)' --class windows --class os $menuentry_id_option 'osprober-chain-421A892D1A891ED3' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos1'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos1 --hint-efi=hd0,msdos1 --hint-baremetal=ahci0,msdos1  421A892D1A891ED3
    else
      search --no-floppy --fs-uuid --set=root 421A892D1A891ED3
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}
menuentry 'Windows 10 (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-AC1E8BDB1E8B9CC8' {
    insmod part_msdos
    insmod ntfs
    set root='hd0,msdos2'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  AC1E8BDB1E8B9CC8
    else
      search --no-floppy --fs-uuid --set=root AC1E8BDB1E8B9CC8
    fi
    parttool ${root} hidden-
    drivemap -s (hd0) ${root}
    chainloader +1
}

```

Looking in disks, I believe the Win 10 partition is /dev/sda1 and the Win 7 is /dev/sda2.  Between the 2 partitions in disks, there appears to be an area of free space if that matters too?

EDIT - sorry.... I tried entering the grub commands you suggested (without the first line and {'s and it just left me at the command line.  No errors reported from any of the lines.  Is that what you expected?

Thanks

Lee.

---

### Post by oldfred on 2021-02-13
Windows typically has a small boot partition and then main install. It boots from a primary NTFS partition with the boot flag that must have its boot files.
When you installed Windows 10, it overwrote the Windows 7 boot loader with the Windows 10 boot loader and added Windows 7 into the BCD in the boot partition. 

If you ran Boot-Repair it copied the essential boot files into the main install partition also. 
So many users did not know Windows has a boot partition and in housecleaning delete it. Then they cannot boot at all and only if you did a backup would have have the boot files. 
Windows does not have to have separate boot partition as upgrades from Vista (which was only in one partition) would work. But you still have primary NTFS partition with boot files.

Vista/7/8/10 BIOS (with 7, 8 or 10 the [COLOR=#ff0000]first two files[/COLOR] are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe

---

### Post by Lee_Nowell on 2021-02-13
Thanks oldfred.  yes I have /bootmgr and /Boot/BCD files in the 105mb partition (/dev/sda1). /Windows/System32/winload.exe is in the other partition /dev/sda2.  Does this imply the partitions are ok it is just that grub is not detecting the Win 7 partition?

---

### Post by oldfred on 2021-02-13
Because Windows 10 installed, grub is seeing something that makes it Windows 10 still.
You may be able to run Windows 7 repairs, but since Windows 7 not supported by Microsoft, not sure if those would work.
Best not to use Windows 7 and do not use it to connect to Internet.

---

### Post by Lee_Nowell on 2021-02-13
Thanks oldfred. It booted fine into Windows 7 before I installed Ubuntu. Won't this imply the Windows bit is fine and we "just" need grub to understand it and boot from the win7 partition?

---

### Post by oldfred on 2021-02-13
Even though grub may say Windows 10, is it not booting Windows 7?

---

### Post by Lee_Nowell on 2021-02-13
No it doesn't boot into Windows 7.  It comes up with a back screen saying Windows failed to start and a recent hardware or software change may have caused it.  It is saying I should use my installation disk to "repair your computer" The status is 0xc0000225.  This happens for both the Windows 10 entries in grub.  I have just noticed that the Windows 10 entries are different one says /dev/sda1 and the other /dev/sda2.  So seems like booting from the 105mb one or the "normal" one results in the same.

---

### Post by oldfred on 2021-02-13
Grub only boots working Windows.
So you may need to run Windows repairs.
I thought the Windows boot files between Windows 10 & 7 were essentially the same as 10 will boot 7. The differnce is the BCD entry.

Google says that error is related to corrupted BCD, and that can only be repaired using Windows.

---

### Post by Lee_Nowell on 2021-02-13
Thanks Oldfred will do some searching to see how to do that do the windows repair.  Odd how the Ubuntu install did this unless the resizing of the original partition to make space for the Ubuntu install was the culprit?

---

### Post by oldfred on 2021-02-13
Windows always need chkdsk after any NTFS resize. You only resize NTFS from inside Windows or with Windows tools to avoid issues & immediately boot Windows directly so it can run chkdsk. Grub will not boot Windows if it needs chkdsk.

Old BIOS installs, especially with Windows 10 often need directly boot of Windows to try to make repairs or use of your Windows repair/recovery Windows flash drive. Or the Windows installer with repair console.
Since grub only boots working Windows & you only have one MBR with BIOS systems and one drive, you often have to temporarily install Windows boot loader, fix Windows & then restore grub from Ubuntu live installer, either manually or with Boot-Repair.

With newer UEFI systems, you can always directly boot Windows from UEFI or Ubuntu from UEFI boot menu. So no installing of boot loaders required.

---

### Post by Lee_Nowell on 2021-02-14
Thanks again for your help.

I followed this guide ([https://neosmart.net/wiki/fix-mbr/](https://neosmart.net/wiki/fix-mbr/)) and was able to get Windows 7 back up and running.  It did a chkdsk and then booted ok.  I then run boot-repair from an Ubuntu boot disk and it rebuilt grub to where I was before.  I have 2 windows 10 entries 
- sda1 (the small partition) boots fine into Windows 7
- sda2 starts with the previous error code of 0xc0000225.

So ideally I would like to 
1. rename the sda1 to say Windows 7 rather than Windows 10
2. remove the sda2 entry

Is this possible?  My boot-repair log is as follows which says an error occurred during the repair

[https://paste.ubuntu.com/p/4zJ8rnwJ5j/](https://paste.ubuntu.com/p/4zJ8rnwJ5j/)

thanks

Lee.

---

### Post by yancek on 2021-02-14
> error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.

If the error you are referring to is the one above, that is in reference to the flash drive you are using and is unrelated to your hard drive with windows and Ubuntu.

You can rename the entry for windows 7 and remove the 2nd entry for windows 10 by editing the /boot/grub/grub.cfg file with root privileges (using sudo).  Any time you update Grub which includes the installation of a new kernel, the entry for windows 10 will reappear.

---

### Post by Lee_Nowell on 2021-02-14
Thanks yancek.  The error I get when loading the /dev/sda2 entry for Windows 10 (sda2 is the partition that Windows 7 is actually installed on) is

> Windows failed to start.  A recent hardware or software change might be the cause.

It then says to fix it using the Windows disc and says error code was 0xc0000225

In terms of changing grub.cfg  just wanted to check I am doing the right thing in case I screw it all up!.  At the top of the file is says

> #
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#


Am I still safe to edit it or do I need to edit something else and get it to regenerate this file?  If I am safe to edit the file directly, is the following correct?

1. Remove all of the following

> 
menuentry 'Windows 10 (on /dev/sda2)' --class windows --class os $menuentry_id_option 'osprober-chain-AC1E8BDB1E8B9CC8' {
        insmod part_msdos
        insmod ntfs
        set root='hd0,msdos2'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos2 --hint-efi=hd0,msdos2 --hint-baremetal=ahci0,msdos2  AC1E8>
        else
          search --no-floppy --fs-uuid --set=root AC1E8BDB1E8B9CC8
        fi
        parttool ${root} hidden-
        drivemap -s (hd0) ${root}
        chainloader +1
}



2. Change 
> menuentry 'Windows 10 (on /dev/sda1)'

to

> menuentry 'Windows 7 (on /dev/sda1)'

thanks for your help

Lee.

---

### Post by oldfred on 2021-02-14
You can do what I do.
I turn off os-prober, so grub does not find any entries.
Then I copy the entries I want into 40_custom. 

sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
sudo nano /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or 
sudo sed -i '$a GRUB_DISABLE_OS_PROBER=true' /etc/default/grub
or turn off executable bit, so not run when grub updates.
sudo chmod a-x /etc/grub.d/30_os-prober

Copy the  entries from this do this before you update-grub with os-prober off, so you have a copy of the Windows entries:
sudo cp -a /boot/grub/grub.cfg /boot/grub/grub.cfg.backup
gedit /boot/grub/grub.cfg
Copy them to and edit to have only entries you want:
sudo nano -B /etc/grub.d/40_custom
Then do:
sudo update-grub

How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config](https://www.gnu.org/software/grub/manual/grub/grub.html#Multi_002dboot-manual-config)
[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

