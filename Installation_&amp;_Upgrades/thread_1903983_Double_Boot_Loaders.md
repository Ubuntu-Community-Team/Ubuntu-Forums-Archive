---
title: "Double Boot Loaders"
date: 2012-01-03
forum: Installation &amp; Upgrades
---

### Post by nipunshakya on 2012-01-03
Hi guys. I have been using ubuntu 11.10 for a while along with win 7. I use ubuntu for learning the terminal thing, and still a noob at it. so i decided to get the windows boot loader instead of ubuntu's grub2 to switch between my OS. 
For this, i used the EasyBCD, edited stuffs there, and then restarted my machine while on win 7. Seems like my procedure to load the windows boot loader was fine, unless one strange thing happened ; both loaders load. 
i. e. **when i start my machine, i first get the GRUB2 loader from ubuntu (selecting ubuntu would start the os too.). But then when i select windows 7 from the list of GRUB2, the windows boot loader loads, and then allows me to choose between windows 7 and ubuntu. when choosen ubuntu, i again get the GRUB and have to choose between the OS...**

what i want is, i want to remove the ubuntu's grub loader, so that i can have a clean windows boot loader on startup....
sorry if this type of thread has already been in this forum

Any kind of help would really be appreciated.

Thanks in advance.
Regards, WinuxUser

---

### Post by fantab on 2012-01-04
From Ubuntu remove GRUB.

*sudo apt-get --purge grub*

---

### Post by darkod on 2012-01-04
I would recommend to just keep using grub2 on your MBR.

If you want to chainload from windows bootloader to grub2, grub2 needs to be installed on the PBR, not MBR (in your case it seems to be on the MBR). You added an entry in EasyBCD from the MBR, that's why it looks like going in circles.

If you insist using windows bootloader and EasyBCD, you have to boot ubuntu, install grub2 to the PBR of your root partition, install the windows bootloader on the MBR and create a new entry in EasyBCD for ubuntu.

Personally I see no benefit using windows bootloader when you have to do all of the above to make it work, when right now it's working fine.

---

### Post by ottosykora on 2012-01-04
while there are certainly reasons for using other boot manager then grub, still a bootloader has to be then in the partition where linux has to be booted from.
As we have nothing much reasonable for that except full size grub today it needs to go into the partition where linux boots from.

However I made experince, that the grub2 is not very much useful for that, as it seems to have files too big and does often not survive upgrades or similar bigger changes to the partition, parts seems to get damaged or moved etc.
In such case I found it is good idea to replace the grub2 by the grub legacy. It has no special function here so it is ok, but it survives very well in the PBR and the actual boot partition. All gets very reliable then.

---

### Post by ottosykora on 2012-01-04
> **fantab said:**
> From Ubuntu remove GRUB.

*sudo apt-get --purge grub*

I would not do that just stright this way. This will make the linux partition unbootable completely. There must be something installed and left *in the partition linux should boot from* , this can be the old lilo or grub legacy or even some syslinux construct.

---

### Post by darkod on 2012-01-04
> **ottosykora said:**
> 
In such case I found it is good idea to replace the grub2 by the grub legacy. It has no special function here so it is ok, but it survives very well in the PBR and the actual boot partition. All gets very reliable then.

Isn't grub1 unable to boot/recognize ext4?

I remember seeing something like that earlier. Maybe it's resolved today.

---

### Post by ottosykora on 2012-01-04
>Isn't grub1 unable to boot/recognize ext4?
<

I have some old fedora on ext4 and booting with grub1, seems not to be a real problem.
Other distros I have mostly on ext3 thought, it gets more compatible with lot of tools that way.

But have replaced all bootloaders where in partition, with grub1, this looks much more stable then.

---

### Post by Mark Phelps on 2012-01-04
It appears that you have modified BOTH boot loaders to allow selection of Either OS -- a redundancy you don't need.

If you've installed GRUB to your MBR (presuming you only have one actual drive), then using EasyBCD is adding a repetition layer (as far as Ubuntu is concerned).

I would remove the Ubuntu entry from the Win7 BCD (using EasyBCD) and just use the GRUB2 menu to do selection.

---

### Post by nipunshakya on 2012-01-04
> **darkod said:**
> I would recommend to just keep using grub2 on your MBR.

If you want to chainload from windows bootloader to grub2, grub2 needs to be installed on the PBR, not MBR (in your case it seems to be on the MBR). You added an entry in EasyBCD from the MBR, that's why it looks like going in circles.

Sir, i think that my grub2 is on the MBR as u said and so, i previously had problem while trying to remove my guest session and reboot wouldn't give any changes too..but i solved it with a shut down for time being.But i don't want to chainload from windows bootloader to grub2,[B] i totally want to remove the grub2 so i can use the windows bootloader only. 
[/B] 
> **darkod said:**
> If you insist using windows bootloader and EasyBCD, you have to boot ubuntu, install grub2 to the PBR of your root partition, install the windows bootloader on the MBR and create a new entry in EasyBCD for ubuntu.

Actually i technically dont know how to install grub2 to the PBR of my root partition and install windows loader to MBR. I just know to add new entry to EasyBCD. If you could, please assist me through this process to **remove grub2 totally **and guide me **to use the windows boot loader. **

> **darkod said:**
> Personally I see no benefit using windows bootloader when you have to do all of the above to make it work, when right now it's working fine.
 
I know everything is fine now, but actually i want other users of my machine to use windows rather than ubuntu. its not that i hate grub2 loader, its just that i dont want anyone to load to ubuntu without knowing what to select at the grub2 loader list. Its just to avoid panic among my little brothers here....no hard feelings for grub2.

If my partition table is needed in case, i have attached the file alongside this post

---

### Post by nipunshakya on 2012-01-04
> **Mark Phelps said:**
> It appears that you have modified BOTH boot loaders to allow selection of Either OS -- a redundancy you don't need.

If you've installed GRUB to your MBR (presuming you only have one actual drive), then using EasyBCD is adding a repetition layer (as far as Ubuntu is concerned).

Sir, i have only one partition for my ubuntu i.e. / and another is a  swap memory. Rest is a NTFS and another partition is for Win 7. (You  could see my attachment in previous comment :) ). 
Now, the thing is, i read a bit about MBR and PBR on wiki, but i really  don't know what they actually mean and neither do i know where are the  GRUB2 and win bootloader installed on my machine.

> **Mark Phelps said:**
> I would remove the Ubuntu entry from the Win7 BCD (using EasyBCD) and just use the GRUB2 menu to do selection.

Well, removing the ubuntu entry would totally disable the windows bootloader and just the grub2 will load, which i totally don't want sir. Doing that would take me to the state where i wanted to use windows bootloader but didnt add any ubuntu entry to easyBCD, isn't it? [B]I actually want to totally remove the GRUB2 on my startup and use just the simple windows boot loader.

[/B]Thanks for your help.
Regards, WinuxUser

---

### Post by nipunshakya on 2012-01-04
> **fantab said:**
> From Ubuntu remove GRUB.

*sudo apt-get --purge grub*

Sir, if i do that, i think i wouldn't be able to boot the ubuntu on first hand coz reading the replies of other Gurus, i think that simply removing GRUB2 won't solve my problem. Instead, i think i have to load windows boot loader to the MBR first then use EasyBCD, isn't it?

---

### Post by nipunshakya on 2012-01-04
> **ottosykora said:**
> while there are certainly reasons for using other boot manager then grub, still a bootloader has to be then in the partition where linux has to be booted from.
As we have nothing much reasonable for that except full size grub today it needs to go into the partition where linux boots from.

However I made experince, that the grub2 is not very much useful for that, as it seems to have files too big and does often not survive upgrades or similar bigger changes to the partition, parts seems to get damaged or moved etc.
In such case I found it is good idea to replace the grub2 by the grub legacy. It has no special function here so it is ok, but it survives very well in the PBR and the actual boot partition. All gets very reliable then.

Sir, that was a good piece of info about grub legacy, but my partition is an ext4. i dont think grub legacy will be able to boot that....please correct me if otherwise.

Regards, WinuxUser

---

### Post by ElanCompaq on 2012-01-04
I read some where to make the boot loader timeout to zero for grub so that you just get the windows boot loader, but I don't know how well that would turn out, so you could try it out if you don't care about your partitions which you probably do. I am also interested in using the windows boot loader instead of grub as well.

---

### Post by nipunshakya on 2012-01-04
> **ElanCompaq said:**
> I read some where to make the boot loader timeout to zero for grub so that you just get the windows boot loader, but I don't know how well that would turn out, so you could try it out if you don't care about your partitions which you probably do. I am also interested in using the windows boot loader instead of grub as well.

Friend, if i make the boot loader timeout to zero for grub, still, i think that the primary selection on the grub would be Ubuntu itself. So, my question is **how can i get inside my windows 7 if the primary selection is Ububtu on the grub2 with timeout ==0 sec.?** any ideas ?

**Regards, WinuxUser**

---

### Post by ottosykora on 2012-01-05
>Actually i technically dont know how to install grub2 to the PBR of my root partition and install windows loader to MBR. I just know to add new entry to EasyBCD. If you could, please assist me through this process to remove grub2 totally and guide me to use the windows boot loader. <

you can not do that.
You have to have something in the linux partition to boot it. You have to have something there what can be picked by the bcd.
If you have no bootloader in the partition, bcd is not able to start linux.

It does not need to be grub, it can be also lilo or some syslinux etc.
But it has to be there.


If you have the grub in MBR, then you can simply set the bcd to windows only and by this it will not show any menu any more and start windows stright away.
Just remove the ubuntu entry in the bcd, that is all.

---

### Post by ottosykora on 2012-01-05
To have only bcd as bootmanager, you need 
1.restore windows MBR so it points first to the bcd files and windows
2.set the bcd to have menu which contains w7 and linux, pointing the linux entry to the partition with the bootloader
3.install some bootloader into the partition with linux
this can be grub (it can be set to zero time if you like then), it can be lilo (careful after kernel updates, it has to be updated as well) or syslinux.

I have one of my installs running win mbr->bcd and from there ubuntu with grub in the partition as bootloader.

---

### Post by ottosykora on 2012-01-05
>but my partition is an ext4. i dont think grub legacy will be able to boot that...<

the current version of grub legacy does support ext4 as well

---

### Post by darkod on 2012-01-05
I think we should not give you any commands or procedures to run until you decide what you want to do.

1. If your idea is to completely remove grub2 like you said, you can't do that because windows bootloader can't boot linux. It can just continue with booting grub2, and this is called chainloading.

That's why I said you might as well leave grub2 on the MBR as main bootloader, because you can't completely remove it. It's not worth the complication installing grub2 or grub1 to the PBR, and then windows bootloader on the MBR.

2. If you are worried someone else might select wrong OS to boot, you will always have this "problem". Regardless what bootloader you use when you have dual boot you will always have two options, so anyone using the computer might select one or the other.

If your idea is just to change the default OS in grub2, this can be done easily. You don't remove grub2 just because you don't like the default OS option.

---

### Post by ottosykora on 2012-01-05
+1 darkod

the use of grub2 in this config, installed in MBR is far more safe then going through all those rather complex chnages to place in the PBR etc.

Just leave it as it is and remove the entry from the bcd for linux.

---

### Post by nipunshakya on 2012-01-05
Now i finally came up with something:

Grub2 cannot be uninstalled in a dual boot unless one wants to have 2 OS in harddrive but make only 1 functional :D
Removing the  entry of Linux in EasyBCD is an easy thing. That would only remove a chainload from grub2 to win7 boot loader, but not completely the grub2.

However, somewhere i had learnt this:
When we install win7 after first installing ubuntu on the same machine, there is a requirement to repair the grub loader for ubuntu. And for that we use live cd of the ubuntu and mess some stuffs on the terminal to update the grub.( correct me if i am wrong)

So just a question arose in my mind: [B]
What if we go from the windows side, not use easyBCD, but use the win7 installation cd to do something with the startup ? 
When i had installed win7 a couple of years back, i remember that there was an option of "Startup Repair" at the installation process. Can this option be used instead to do something to update windows boot loader to fix it to the MBR and then use EasyBCD to add new entry of UBUNTU ? Will that remove grub2  but still add ubuntu to the boot menu and boot from it?

[/B]I just don't want to go to the windows7 forums begging for help coz the helpers there might ask for money...lol. Someday, when ubuntu community can be able to develop a similar project to visual studio, then i shall say [B]WINDOWS, U ARE FIRED ! ! !

Regards, WinuxUser
[/B]

---

### Post by darkod on 2012-01-05
How many times do we need to say it? :)

YOU CAN'T BOOT LINUX ONLY WITH WINDOWS BOOTLOADER, WITHOUT GRUB!!!

No matter what you do, you can't. Yes, you can use the win7 dvd and install the windows bootloader to the MBR. That will overwrite grub2. And then you will have no way to boot ubuntu.

EasyBCD is not a bootloader, only a program helping you to create an entry in the windows bootloader. But that entry, when you select to boot ubuntu, is simply calling grub2 to continue booting ubuntu. You would need to have it on the PBR so it can work.

In this situation doing all of this is pointless, but if you really want to, there are plenty of guides on google. You know what you need to do.

---

### Post by oldfred on 2012-01-05
The way you describe booting, it almost sounds like you have both a full install and wubi which is an install inside the NTFS windows partition. you can in Ubuntu/grub set a default of Windows to boot first if you want.

The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

If you want to repair booting:
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

If you want to understand how BIOS/MBR systems particularly Windows boot - you really just have to look at the pictures unless you really want to understand it in detail:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

I know nothing about EasyBCD, but some report it works for them with Windows 7 or Vista.
[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by nipunshakya on 2012-01-05
> **darkod said:**
> How many times do we need to say it? :)

YOU CAN'T BOOT LINUX ONLY WITH WINDOWS BOOTLOADER, WITHOUT GRUB!!!

SIR, I HAD ALREADY CAME UP TO THAT CONCLUSION. SORRY IF I STARTED TO QUESTION ALTERNATE METHODS TO SOLVE MY PROBLEM.

> **darkod said:**
> No matter what you do, you can't. Yes, you can use the win7 dvd and install the windows bootloader to the MBR. That will overwrite grub2. And then you will have no way to boot ubuntu.

Seems like now im getting a clear vision of grub2's importance for ubuntu and so i guess i will spend some time reading the threads **oldfred** prescribed in his comments.
Thanks for your help.

> **darkod said:**
> EasyBCD is not a bootloader, only a program helping you to create an entry in the windows bootloader. But that entry, when you select to boot ubuntu, is simply calling grub2 to continue booting ubuntu. You would need to have it on the PBR so it can work.

And this additional piece of information was overwritten to my brain too. I was just wondering to get grub to my PBR or whatever...but it looks like i need to stick with **oldfred's **help for a while and then post my findings. :)

Thank You.):P
Regards, WinuxUser

---

### Post by nipunshakya on 2012-01-05
> **oldfred said:**
> The way you describe booting, it almost sounds like you have both a full install and wubi which is an install inside the NTFS windows partition. you can in Ubuntu/grub set a default of Windows to boot first if you want.

Sir, i don't have any wubi install inside the NTFS. I just have a full installation of Ububtu on an ext4 partition, a windows 7 on NTFS and another NTFS to share data between ubuntu/win7. Keeping that aside, i would first try out your prescribed thread and then see what i can do with your help. 
If i won't be able to do what i actually wanted, i would surely prefer to have windows boot first via my grub2.

> **oldfred said:**
> If you want to understand how BIOS/MBR systems particularly Windows boot - you really just have to look at the pictures unless you really want to understand it in detail:
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

I would like to try out with that. I will post after i do something with my findings.):P

Thank You.
Regards,WinuxUser

---

### Post by oldfred on 2012-01-06
So we can see your full configuration. Run boot info script and post results.txt in code tags.

This is a new test version that should work.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Current version:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install gawk
sudo apt-get install xz-utils

---

### Post by nipunshakya on 2012-01-07
So sorry for late reply. I did as u suggested and here is the output.

```

                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for  on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   125,835,096   125,835,034   7 NTFS / exFAT / HPFS
/dev/sda2         125,837,145   495,307,848   369,470,704  83 Linux
/dev/sda3         499,308,544   625,137,663   125,829,120   7 NTFS / exFAT / HPFS
/dev/sda4         495,308,798   499,308,543     3,999,746   5 Extended
/dev/sda5         495,308,800   499,308,543     3,999,744  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        02E62A90E62A83CF                       ntfs       
/dev/sda2        8d95df9a-413e-464d-958e-d65c202b5957   ext4       
/dev/sda3        B81CE0301CDFE800                       ntfs       REPOSITORY
/dev/sda5        600d7422-6d14-4e99-91c4-14dc27c779a5   swap       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda2        /                        ext4       (rw,errors=remount-ro,commit=0)


=========================== sda2/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
  insmod video_bochs
  insmod video_cirrus
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos2)'
search --no-floppy --fs-uuid --set=root 8d95df9a-413e-464d-958e-d65c202b5957
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  insmod part_msdos
  insmod ext2
  set root='(hd0,msdos2)'
  search --no-floppy --fs-uuid --set=root 8d95df9a-413e-464d-958e-d65c202b5957
  set locale_dir=($root)/boot/grub/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=30
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, with Linux 3.0.0-14-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 8d95df9a-413e-464d-958e-d65c202b5957
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=8d95df9a-413e-464d-958e-d65c202b5957 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-14-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-14-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 8d95df9a-413e-464d-958e-d65c202b5957
    echo    'Loading Linux 3.0.0-14-generic ...'
    linux    /boot/vmlinuz-3.0.0-14-generic root=UUID=8d95df9a-413e-464d-958e-d65c202b5957 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-14-generic
}
submenu "Previous Linux versions" {
menuentry 'Ubuntu, with Linux 3.0.0-13-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 8d95df9a-413e-464d-958e-d65c202b5957
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=8d95df9a-413e-464d-958e-d65c202b5957 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-13-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 8d95df9a-413e-464d-958e-d65c202b5957
    echo    'Loading Linux 3.0.0-13-generic ...'
    linux    /boot/vmlinuz-3.0.0-13-generic root=UUID=8d95df9a-413e-464d-958e-d65c202b5957 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-13-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 8d95df9a-413e-464d-958e-d65c202b5957
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=8d95df9a-413e-464d-958e-d65c202b5957 ro   quiet splash vt.handoff=7
    initrd    /boot/initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, with Linux 3.0.0-12-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 8d95df9a-413e-464d-958e-d65c202b5957
    echo    'Loading Linux 3.0.0-12-generic ...'
    linux    /boot/vmlinuz-3.0.0-12-generic root=UUID=8d95df9a-413e-464d-958e-d65c202b5957 ro recovery nomodeset 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-3.0.0-12-generic
}
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 8d95df9a-413e-464d-958e-d65c202b5957
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos2)'
    search --no-floppy --fs-uuid --set=root 8d95df9a-413e-464d-958e-d65c202b5957
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 02E62A90E62A83CF
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
--------------------------------------------------------------------------------

=============================== sda2/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda2       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=600d7422-6d14-4e99-91c4-14dc27c779a5 none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda2: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1
               =                boot/grub/grub.cfg                             1
               =                boot/initrd.img-3.0.0-12-generic               2
               =                boot/initrd.img-3.0.0-13-generic               1
               =                boot/initrd.img-3.0.0-14-generic               2
               =                boot/vmlinuz-3.0.0-12-generic                  1
               =                boot/vmlinuz-3.0.0-13-generic                  1
               =                boot/vmlinuz-3.0.0-14-generic                  1
               =                initrd.img                                     2
               =                initrd.img.old                                 1
               =                vmlinuz                                        1
               =                vmlinuz.old                                    1

======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda4

00000000  5f b7 eb eb b0 b7 9b 25  e2 14 67 85 5f 06 2c 6b  |_......%..g._.,k|
00000010  d7 9a b4 5a 48 dd d8 bd  82 9d b4 9e c5 f1 b3 e5  |...ZH...........|
00000020  e5 3e 06 d4 bb 98 8d eb  79 96 37 79 b4 b3 3a bd  |.>......y.7y..:.|
00000030  e7 56 43 c9 3b 4f 93 fe  82 07 fd 2f 15 58 1c 5d  |.VC.;O...../.X.]|
00000040  e5 8b 05 23 cc 56 a9 a6  a7 b8 c2 cd ee cd e5 ff  |...#.V..........|
00000050  d4 6f 39 ea b4 35 d2 32  d8 69 8d f7 77 b1 f6 99  |.o9..5.2.i..w...|
00000060  0a 63 f7 20 c5 e0 80 3f  a2 4f 80 f0 42 2f f4 04  |.c. ...?.O..B/..|
00000070  29 24 f2 b1 f2 8b 7c c7  e2 f2 e5 46 6c 1e 03 fc  |)$....|....Fl...|
00000080  30 3c 08 20 c0 a7 54 80  54 0c 3e 80 1e 3f 56 25  |0<. ..T.T.>..?V%|
00000090  fa 04 25 7f 2e b9 96 fa  0f 3f ff 4d fd f7 2d 38  |..%......?.M..-8|
000000a0  0d 07 e0 f0 3f ed ab c9  e8 10 61 74 9c 80 7d 0f  |....?.....at..}.|
000000b0  c4 73 2a fe d8 1c 34 e0  a6 1f db 83 c0 7f 63 00  |.s*...4.......c.|
000000c0  31 5a b9 80 c3 d2 f0 8c  1e 03 fb b8 10 07 f2 83  |1Z..............|
000000d0  c1 ff de 0c f0 61 2a 09  00 c1 0d 71 25 18 97 45  |.....a*....q%..E|
000000e0  a0 c2 55 00 c0 61 2e b6  08 68 c4 91 58 31 b6 89  |..U..a...h..X1..|
000000f0  c2 98 38 38 07 80 fe 95  50 94 24 83 e2 ff e2 0f  |..88....P.$.....|
00000100  01 fd 0f cb 87 e5 c0 f0  9f f8 f6 b5 0f 03 0f 81  |................|
00000110  e0 60 1b 06 12 d7 56 8c  21 d1 68 30 42 07 81 80  |.`....V.!.h0B...|
00000120  6c 19 5d 67 e8 c4 9a 2d  06 36 d1 38 53 05 41 c0  |l.]g...-.6.8S.A.|
00000130  3c 07 f7 20 c3 c0 83 41  f1 3f f1 07 80 fe ec 19  |<.. ...A.?......|
00000140  40 43 07 85 ff c4 64 0c  3e 07 81 80 74 18 bd 38  |@C....d.>...t..8|
00000150  3c 4f fe 34 5a 0c 3e 07  81 80 7c 18 bc 0c 83 c5  |<O.4Z.>...|.....|
00000160  7f e2 2b 37 38 4e 14 c1  18 38 07 80 ff 04 19 40  |..+78N...8.....@|
00000170  92 0f 8b ff 88 3c 07 f8  60 a0 08 60 f0 bf f8 8c  |.....<..`..`....|
00000180  81 87 c0 f0 30 0e 83 2b  03 20 f1 5f f8 bc 18 4a  |....0..+. ._...J|
00000190  07 81 80 7c 10 59 1f c8  94 7e 19 d1 d9 37 b8 4e  |...|.Y...~...7.N|
000001a0  14 c0 f8 38 07 80 ff 1c  19 40 92 0f 8b ff 88 3c  |...8.....@.....<|
000001b0  07 f8 a0 84 25 83 c2 ff  df 06 40 c3 e0 78 00 fe  |....%.....@..x..|
000001c0  ff ff 82 fe ff ff 02 00  00 00 00 08 3d 00 00 00  |............=...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=============================== StdErr Messages: ===============================

unlzma: Decoder error
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in
awk: cmd. line:36: Math support is not compiled in


```

---

### Post by darkod on 2012-01-08
@oldfred,
To help you out a little bit. He has created a loop but doesn't understand it. I don't know what more to say so I have given up.

He has grub2 on the MBR and it works fine, no issues. But then decided with EasyBCD to add an ubuntu entry in the windows bootloader. But for that procedure you need to install grub2 to the PBR of the root partition and leave windows bootloader on the MBR. It is not the case here.
The entry for ubuntu created with EasyBCD jumps you back to the grub2 MBR.

So:
You boot.
In grub2 menu if you select ubuntu it loads.
If you select windows it continues with windows booloader.
Once you are there if you select windows it loads.
But when you select ubuntu (made by easybcd), it jumps you to grub menu again, and you can play like that whole day.

I said at least 5 times.
Option A: Very simple. Remove the easybcd entry for ubuntu, keep booting the pc with grub2 on the MBR, everything works, no complications.
Option B: If you really want to do it the hard way, install grub2 to the PBR, delete the current easybcd entry and create a new one for PBR grub2, install windows bootloader on the MBR.

If you leave it like it is, the loop remains.

---

### Post by nipunshakya on 2012-01-08
> **darkod said:**
> 
The entry for ubuntu created with EasyBCD jumps you back to the grub2 MBR.

Option A: Very simple. Remove the easybcd entry for ubuntu, keep booting the pc with grub2 on the MBR, everything works, no complications.
Option B: If you really want to do it the hard way, install grub2 to the PBR, delete the current easybcd entry and create a new one for PBR grub2, install windows bootloader on the MBR.

Sir, being aware of your help, i went on with Option A. 
Pointless to say, but i carried out the boot_info_script.sh to get the result.txt **after i had removed Ubuntu entry from the EasyBCD. **
I understood well that the Grub2 is in the MBR. 


> **darkod said:**
> If you leave it like it is, the loop remains.

I got a bit confused here... u said "If you leave it like it is..." , am i doing something wrong here even after removing the ubuntu entry from EasyBCD???:confused:

---

### Post by darkod on 2012-01-08
> **WinuxUser said:**
> Sir, being aware of your help, i went on with Option A. 
Pointless to say, but i carried out the boot_info_script.sh to get the result.txt **after i had removed Ubuntu entry from the EasyBCD. **
I understood well that the Grub2 is in the MBR. 




I got a bit confused here... u said "If you leave it like it is..." , am i doing something wrong here even after removing the ubuntu entry from EasyBCD???:confused:

I didn't see you mention that you removed the easybcd entry for ubuntu.

If you did that, you are the one who needs to tell us if it works fine or not.
Can you boot ubuntu from grub2?
Can you boot windows from grub2 without getting another menu? Does it boot directly when you select windows or not?

---

### Post by nipunshakya on 2012-01-08
Oh yes , Ubuntu boots from grub2 directly and so does the win 7(without getting win7 boot loader).
im sorry for not mentioning that before my previous comment but my concern was still going on to give a try to Option B if possible, maybe i need to google some stuffs here for detailed methods to do that.Till then, i shall assume this thread as solved. Thanks everyone
Anyways, thanks for your help and quick response.

Regards, WinuxUser

---

### Post by oldfred on 2012-01-08
It comes down to preferences. I do not have Windows 7 and prefer to have a different operating system on each hard drive. But I do dual boot XP and Ubuntu on my portable with one drive.

Some who primarily use Windows 7 have used EasyBCD. But realize that installing grub2 to the PBR is not recommended and on grub updates you may have to reinstall grub to the PBR. It has to compress its install and use hard coded addresses to find the rest of its boot code. On an update that address may change.

A few use some very proprietary software in Windows 7 that uses DRM and writes that hidden data in the same area that grub2 uses for booting. For those EasyBCD may be a better choice. 
Some Dell & HP software does the same, but most just uninstall that, if they really want to use Ubuntu a lot. 

I like grub2, but if you want some info on EasyBCD.
[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by nipunshakya on 2012-01-08
> **oldfred said:**
> But realize that installing grub2 to the PBR is not recommended and on grub updates you may have to reinstall grub to the PBR. It has to compress its install and use hard coded addresses to find the rest of its boot code. On an update that address may change.


With that little warning sign, i would take it as a disadvantage for trying to install grub2 on the PBR.
 
So instead of trying to use windows boot loader, i would now stick to the GRUB2.

Seems like this is really a solution to the problem. 
The only thing to learn now is changing the boot sequence in the grub.


Thanks everyone for your kind support.

Regards, WinuxUser.

---

### Post by oldfred on 2012-01-08
You can manual edit  grub or use customizer.

  Changenumber used as default, count starts at 0.
gksudo gedit /etc/default/grub
After any change to grub:
sudo update-grub

Grub 2 Title Tweaks-drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by nipunshakya on 2012-01-08
^^ Im on it.

Thanks for quick response.

Regards, WinuxUser

---

