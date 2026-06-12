---
title: "multi boot laptop install - Missing modules (cat /proc/modules; ls /dev)"
date: 2014-11-25
forum: Installation &amp; Upgrades
---

### Post by parker-hugh on 2014-11-25
Hi, I have my old laptop hp Compaq nx6125 setup with dual boot. and it's  running both nicely even with only 1.38GB RAM and the original AMD  Turion 64 1.8GHz processor. I bought it in 2005 and it's still going strong.

First I installed Linux Mint 17 xfce, then I  installed Debian 7.7 lxde. As I said it's running very well.

I have just added Lubuntu 14.04.1 as a third OS. When I finished the install and reboot laptop, the grub does show all three OS, Mint, Debian and Lubuntu (default).

But when I try to log into Lubuntu, the screen goes blank for about a minute or so, then some text is displayed, but I can't get into the OS, here is the text as displayed on screen....

```
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/94f3be........ does not exist. Dropping to a shell!

BusyBox v1.21.1 (Ubuntu 1:1.21.0-lubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) _
```

this is what my partitions look like using Gparted live cd ...

```
Partition        File System    Label          Size     Used    Unused    
/dev/hda1        extended                      57.13GB                
  /dev/hda5      ext4            MINT          11.42GB                
  /dev/hda6      swap                          1.00GB                
  /dev/hda7      ext4            DEBIAN        11.42GB                
  unallocated    unallocated                   33.29GB
  /dev/hda2      ext4            SHARE         17.40GB
```

Both the other two OS are working ok, not Lubuntu. The laptop is otherwise working very well.

Any idea what might have went wrong? I am fairly new to Linux but have been able to install multiple OS on other laptops before, so not sure what is going wrong here.

Thanks for any help or guidance.

regards, Hugh

---

### Post by oldfred on 2014-11-25
Best to see all the details:
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Current version ppa now available.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you wait a few seconds and then press enter does it then boot?


Some old BIOS will not boot if boot files are beyond 137GB on drive.

---

### Post by parker-hugh on 2014-11-25
Hi, thanks for reply to my post. I tried waiting a few seconds and pressed enter again, but nothing happened. 

I tried the install again, this time using another live usb in case the one I used was faulty, I tied Xubuntu this time. But same result. 

When I did the install, I chose partition /dev/sda8, and the install finished ok and asked me to re boot laptop.

I downloaded BootRepair and booted from that and managed to get a BootInfo summary [http://paste.ubuntu.com/9238954](http://paste.ubuntu.com/9238954)

I looked for /dev/sda8 in the summary and saw it mentioned about 8 times, e.g. ...

```
=================== os-prober:
/dev/sda5:Linux Mint 17 Qiana (17):LinuxMint:linux
/dev/sda7:Debian GNU/Linux (7.7):Debian:linux
/dev/sda8:Ubuntu 14.04.1 LTS (14.04):Ubuntu:linux

=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda2: LABEL="SHARE" UUID="f06a8c0f-9af3-4702-b90a-db2e3caed3b6" TYPE="ext4"
/dev/sda5: UUID="5b9e7d5e-070c-4db4-99dc-81ffe98099d8" TYPE="ext4"
/dev/sda6: UUID="83f588fb-fcb2-4b77-84be-726cb9df4cb7" TYPE="swap"
/dev/sda7: LABEL="DEBIAN-LXDE" UUID="7db40bc1-7d1c-472b-8ed4-b85291c4766a" TYPE="ext4"
/dev/sda8: UUID="ed6344b1-6244-4e75-ad8d-29c1be6e00b6" TYPE="ext4"
/dev/sdb1: LABEL="UUI" UUID="1CF4-186C" TYPE="vfat"
```

there are a few other instances where /dev/sda8 is mentioned but not sure what it all means as I am fairly new to linux. Any idea what has gone wrong?

Thanks and Regards, Hugh

EDIT

Also noticed sda8 in the summary here ...

============================= Boot Info Summary: ===============================

sda8: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 14.04.1 LTS 
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

---

### Post by oldfred on 2014-11-25
I do not see anything wrong with install.
Drive is smaller, so kernels beyond 137GB is not an issue.

What mode is drive set in BIOS, if you have AHCI that should be used not IDE nor RAID.

You have the same kernel in Mint, Debian is older.
Are you able to boot Mint & Debian from the Xubuntu install's grub menu?

At grub menu try this, changing from UUID back to the old device setting:
[http://ubuntuforums.org/showthread.php?t=1611213&p=10058668#post10058668](http://ubuntuforums.org/showthread.php?t=1611213&p=10058668#post10058668)
Yours should be something like:
			 				linux	/vmlinuz **root=/dev/sda8** ro quiet splash

---

### Post by parker-hugh on 2014-11-25
> I do not see anything wrong with install.
Drive is smaller, so kernels beyond 137GB is not an issue.

What mode is drive set in BIOS, if you have AHCI that should be used not IDE nor RAID.

You have the same kernel in Mint, Debian is older.
Are you able to boot Mint & Debian from the Xubuntu install's grub menu?

thanks again for your reply.

I looked in the BIOS and couldn't find any mention of AHCI or IDE nor RAID.

I am able to log into both Debian and Mint ok from the Xubuntu install's grub menu. it's just Xubuntu that is the problem.

This is the second time I tried the install, Lubuntu first, then Xubuntu second, and it's the same problem each time. 

After the first install when I couldn't log into Xubuntu, I logged into Debian and ran the following command as root...

```
sudo grub-install /dev/sda
```

.. the terminal output looked successful.... 

```
root@hp-compaq-nx6125-debian-7:/home/hugh# grub-install /dev/sda
Installation finished. No error reported.
root@hp-compaq-nx6125-debian-7:/home/hugh#
```

This changed the default OS to Debian, which is what I wanted to do, but the grub only displayed Debian and Mint, the Lubuntu option was not there, so it didn't pick up the third oS. Not sure if this is significant or just adds to the mystery.

> At grub menu try this, changing from UUID back to the old device setting:
[http://ubuntuforums.org/showthread.p...8#post10058668]("http://ubuntuforums.org/showthread.php?t=1611213&p=10058668#post10058668")
Yours should be something like:
                             linux    /vmlinuz **root=/dev/sda8** ro quiet splash

I will now boot the grub menu and try what you have suggested above (changing from UUID back to the old device setting) I've never done this before but I'll have a go and and will get back to you shortly with results. Thanks again for your help.

EDIT.

the instructions on the link   ....  says "Cursor to the start of the "search" line. Hold down the DEL key and remove the entire line".

I can see two lines that start with search

[B]if .... then
   search .....
else
   search ......[/B]

Should I delete both lines?

---

### Post by oldfred on 2014-11-25
If you now have changed to Debian, those instructions do not apply.

And you have to scroll down to the Linux line.

In Debian did you also run this?

sudo update-grub

---

### Post by parker-hugh on 2014-11-25
Once again, thanks for taking the time to respond.

> If you now have changed to Debian, those instructions do not apply.

Although I changed grub default to Debian, that was for the first attempt at the install. Then I deleted the partition and started again, so I'm still at the point where I can see the Xubuntu grub menu but can't log into Xubuntu, although the oher two (Mint and Debian) are both ok.

> And you have to scroll down to the Linux line.

before I change the linux line....

I can see two lines that start with search ....

```
if .... then
   search .....
else
   search ......
```

Should I delete both lines?

> In Debian did you also run this?

sudo update-grub

No, I ony ran ...

```
sudo grub-install /dev/sda
```

I'm only learning Linux this past few months, I didn't know this need to be run as well, what additional function does **sudo update-grub** have on the system?

Thanks for your help, it's much appreciated.

Hugh

EDIT

I tried deleting both search lines but system came back saying systax error... press any key to continue

so I also deleted these lines...

[B]if [ x$feature-platform .... etc....
   search
else
  search[/B]

and tried again but system came back saying systax error... press any key to continue

not sure what to do next, any ideas?

---

### Post by oldfred on 2014-11-25
I donot think instructions said to delete anything other than the linux line and the search by UUID lines above it. The newer grub has lots of added logic.
But the idea is to convert boot to the very simple device boot. That used to be the standard but devices often changed. So it was updated to search by UUID and UUID almost never change.

You want all the references to UUID to be removed.
```
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-ed6344b1-6244-4e75-ad8d-29c1be6e00b6' {
    recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='hd0,msdos8'
[COLOR=#ff0000]    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,msdos8 --hint-efi=hd0,msdos8 --hint-baremetal=ahci0,msdos8  ed6344b1-6244-4e75-ad8d-29c1be6e00b6
    else
      search --no-floppy --fs-uuid --set=root ed6344b1-6244-4e75-ad8d-29c1be6e00b6
    fi
 [/COLOR]   linux    /boot/vmlinuz-3.13.0-32-generic [COLOR=#ff0000]root=UUID=ed6344b1-6244-4e75-ad8d-29c1be6e00b6[/COLOR] ro  quiet splash $vt_handoff
    initrd    /boot/initrd.img-3.13.0-32-generic


```

This is all you need:
      ```
 menuentry "Install on sda8" {
    set root=(hd0,8)
        linux /vmlinuz root=/dev/sda8 ro quiet splash
        initrd /initrd.img
}

    
```

---

### Post by parker-hugh on 2014-11-26
Hi, thanks for the feedback again, I tried to edit the lines but didn't work. this is what I ended up with after deleting the unwanted text...

```
 menuentry "Install on sda8" {
    set root=(hd0,8)
        linux /vmlinuz root=/dev/sda8 ro quiet splash
        initrd /initrd.img
}
```

This didn't acept my entry when I hit Ctrl + X

So I tried this text which I saw from the fourth reply on this page you had referred me to earlier [http://ubuntuforums.org/showthread.php?t=1611213&p=10058668#post10058668](http://ubuntuforums.org/showthread.php?t=1611213&p=10058668#post10058668)

> recordfail
insmod ext2
set root='(hd0,8)'
linux /vmlinuz root=/dev/sda8 ro quiet splash
initrd /initrd.img 

When I hit Ctrl + X the screen went black and the curser was blinking but didn't boot into the os.

Could you look at the text I uesed above, to see if I made an error somewhere?

Thanks,
Hugh

---

### Post by oldfred on 2014-11-26
Lets leave out quiet splash and/or replace with nomodeset.

Often black screen is a video issue. Without the quiet splash you should see all the boot process and where it may fail. Or if just a video issue nomodeset may let it boot.

---

### Post by parker-hugh on 2014-11-26
thanks for response once again, I appreciate your help on this, I tried following text...

```
recordfail
insmod ext2
set root='(hd0,8)'
linux /vmlinuz root=/dev/sda8
initrd /initrd.img
```

this was same as previous except I omitted "ro quiet splash" as you suggested...

lots of text run up screen (mainly about devices found etc) then halts for about half minute then displays following 

message which is slightly different from before....

```
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda8 does not exist. Dropping to a shell!

BusyBox v1.21.1 (Ubuntu 1:1.21.0-lubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) 
```

what's different from before is 

"/dev/sda8 does not exist" 

previously it said ....

"/dev/disk/by-uuid/94f3be... etc........ does not exist"

does this help to identify the problem in any way?

next I tried same text with "nomodeset" added as you suggested...

```
recordfail
insmod ext2
set root='(hd0,8)'
linux /vmlinuz root=/dev/sda8 nomodeset
initrd /initrd.img 
```

same result as above, lots of text run up screen (mainly about devices found etc) then halts for about half minute then displays same text..

```
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda8 does not exist. Dropping to a shell!

BusyBox v1.21.1 (Ubuntu 1:1.21.0-lubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) 
```

does this help in finding cause of the problem?

regards,

EDIT,

I was wondering if my install process caused the problem, I mean that I used a USB rather than a DVD, do you think that might be the cause of the problem?

Hugh

---

### Post by oldfred on 2014-11-26
How you install should make no difference. DVD or flash is really the same.

Did install complete normally?
Sometimes if install did not complete then the initrd.img is not created or created correctly.

This thread, now old, says add rootdelay. You can add that manually
[http://ubuntuforums.org/showthread.php?t=1531999&highlight=rootdelay](http://ubuntuforums.org/showthread.php?t=1531999&highlight=rootdelay)
rootdelay=90

insmod ext2
set root='(hd0,8)'
linux /vmlinuz root=/dev/sda8 ro nomodeset rootdelay=90
initrd /initrd.img

Have you typed exit at busybox before rebooting?
[http://ubuntuforums.org/showthread.php?t=1561652&highlight=rootdelay](http://ubuntuforums.org/showthread.php?t=1561652&highlight=rootdelay)

And if rebooting be sure to remember the elephants. 
 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

### Post by parker-hugh on 2014-11-26
> Did install complete normally?
Sometimes if install did not complete then the initrd.img is not created or created correctly.

The install did complete and usual message says restart pc, so I click ok and wait for pc to reboot. For some reason sometimes the pc doesn't actually restart, but it just sits there and nothing happens. So I have to press the power button for 10 seconds to switch it off and then restart.  Do you think this may have something to do with the problem? That was the reason I asked about installing with USB, because I don't think I have encountered this reboot problem when using a DVD.

> This thread, now old, says add rootdelay. You can add that manually

thanks for the suggestion above, I will try this and give an update.

> Have you typed exit at busybox before rebooting?
[http://ubuntuforums.org/showthread.p...ight=rootdelay]("http://ubuntuforums.org/showthread.php?t=1561652&highlight=rootdelay")

do you mean rebooting when the install is finished? 

regards, hugh

---

### Post by oldfred on 2014-11-26
With flash drive installs, or even DVD, you often had to press enter one more time.
It is more like it is missing a message on press enter to remove DVD, even if flash drive.
But that should not have made any real difference unless it still was writing data and forcing shutdown caused file corruption. Then an e2fsck may be needed.

At busybox error type exit.

---

### Post by parker-hugh on 2014-11-26
thanks again.

I tried entering ...

```
insmod ext2
set root='(hd0,8)'
linux /vmlinuz root=/dev/sda8 ro nomodeset rootdelay=90
initrd /initrd.img
```

but same result as before

```
Gave up waiting for root device. Common problems:
 - Boot args (cat /proc/cmdline)
   - check rootdelay= (did the system wait long enough?)
   - Check root= (did the system wait for the right device?)
 - Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/sda8 does not exist. Dropping to a shell!

BusyBox v1.21.1 (Ubuntu 1:1.21.0-lubuntu1) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs
```)

I think I might try reinstalling again using a DVD to see if that solves the problem, I will let you know how I get on.

Thanks so much for your help on this.

regards, hugh

---

### Post by parker-hugh on 2014-11-26
I re-installed Xubuntu. Then tried to shut down but like before, Xubuntu didn't shut down, so I followed your instructions and pressed following keys...
Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown. 

Laptop still didn't shut down so typed exit and hit enter, and it shut down ok.

When I restart and selected Xubunt, it worked ok. So I think the problem was not shutting down properly in the first place, I wasn't aware or the REISUB and exit method.

So thanks for all your help, with your patience we got there in the end, so I'm happy about that.

Take care, Hugh

**EDIT**

If I wanted to make one of the other OS, e.g. Debian to be the default grub, I understood that all I need to do is log into Debian and run following command as root ...

**grub-install /dev/sda**

This worked for me before, because when I reboot I can see Debian has been changed to default in grub, and I can login ok. The reason I ask is, in one of your earlier questions you asked did I also run **"sudo update-grub"**.  Is it necessary to run this command, would it be instead of or in addition to **"grub-install /dev/sda"**, also what does it do?

Thanks for all your help.

regards, hugh

---

### Post by oldfred on 2014-11-26
This installs grub to MBR of device sda from inside a working install.
sudo grub-install /dev/sda

This updates grub menu. It also runs os-prober which searches all drives for bootable systems and adds those to your menu.
sudo update-grub

With multiple installs, it can be difficult to keep track of which is in charge and which is current.
You have to update system that is not in charge, and then boot into main system and run its update to find the new kernels in the other install.

And major updates in your other installs may automatically run a grub install to the MBR, switching which system boots.
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    
You may be able to unselect all options in your second installs.
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

I prefer to turn off os-prober, and add my own boot stanza to 40_custom to boot partition. Debian based installs add links to most current kernel into /, so you can create a boot stanza to boot using link. 
Examples & details:
      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

---

### Post by parker-hugh on 2014-11-27
Thanks for your really thorough explanation, some of it is a bit over my head right now, but it gives me something to research using the links you kindly included. so that will keep me quiet for a while :) 

Cheers,

Hugh

---

### Post by parker-hugh on 2014-11-27
Sorry I have a couple of questions after reading your great feedback and tips...
>  [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711") said. You may be able to unselect all options in your second installs.
#to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

Q1.
Since I only have one physical drive with multiple partitions, wouldn I need to run "sudo dpkg-reconfigure grub-pc" ?  i.e. this would only be useful where there are more than one physical drive where you wanted to force MBR to one or the other?
................
>  [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711") said. This installs grub to MBR of device sda from inside a working install.
**sudo grub-install /dev/sda**

This updates grub menu. It also runs os-prober which searches all drives for bootable systems and adds those to your menu.
**sudo update-grub**

Q2.
Currently my default grub is still Xubuntu (since it was the last one I installed) If I want to change this, would I need to run two commands ... 

**sudo update-grub**

and then...

**sudo grub-install /dev/sda**

My question is, is it necessary to run both since perviously I only ran "sudo grub-install /dev/sda" and this looked as if it changed the grub successfully. I'm still a bit unsure on this.
.................
Q3.
If at a later date, one of the other OS (Mint or Xubuntu) get an upgrade to the kernel, which updates their grub to make it the default, would I just need to login to Debian again and run the sudo update to bring it back default grub?
.....................
>  [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711") wrote. I prefer to turn off os-prober, and add my own boot stanza to 40_custom  to boot partition. Debian based installs add links to most current  kernel into /, so you can create a boot stanza to boot using link. 
Examples & details:
      
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/Ma...tomGrub2Screen]("https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen")
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)

Both the links you gave above look really interesting, the second one especially. It will be my next learning experience, as it is a bit more advanced than I am currently.

Thanks for all your help. Hugh.

---

### Post by oldfred on 2014-11-27
Yes you should have all 3 systems in all 3 boot menus. So if the one that you do not normally boot first, then installs its grub you can choose to boot into your main install reinstall its grub. You need to run the update so it finds the new kernels in the 2nd or 3rd install.

That is where it can get confusing on which system's grub is in charge, which is currently updated and all all the others also updated to boot the most current kernel in all the other versions.

The dpkg reconfig is like the way a new install works. But it seems to also let you un-choose everything so grub is not installed to the MBR on updates. You still need grub installed to system, to run updates so most current kernel is seen and in menu, as other installs read menu first to find correct kernel to boot.

---

### Post by parker-hugh on 2014-11-27
so right now if I want to change Xubuntu default grub to Debian, do I log into Debian and run both "**sudo grub-install /dev/sda**" and "**sudo update-grub**"? or just one.

Then later if one of the other OS (Mint or Xubuntu) has a kernel change which changes grub, should I log back into Debian and run "**sudo dpkg-reconfigure grub-pc**" followed by both "**sudo grub-install /dev/sda**" and "**sudo update-grub**"?

regards, Hugh

---

### Post by oldfred on 2014-11-27
I think the dpkg reconfigure does the equivalent of both other commands. And you should only have to run that once to make sure that the grub internal setting to reinstall is either correct or empty.

The sudo update-grub does not install grub to the MBR, but runs updates to the menu. Any setting change, like adding entry to 40_custom, changes to /etc/default/grub or installing new systems need the update so settings & new installs are reflected in the grub menu.

And the install to the MBR is just putting the boot loader from which every install you have booted into, in the MBR specified. You can install a different installs grub into the MBR, just like from a live installer, by mounting the partition (and /boot if you have one) and then running the install command.

You have to run the sudo update-grub in every install, if there are changes. Normally a new kernel automatically runs it in the install you update, but then you have to boot into all other installs and run the update so then have the new info in their menu. That is why the simplification of booting partition or link works much better. 

Best to run Boot-Repair's summary report or what really is the first part of the summary report which is the bootinfoscript. Then you know what is where and have some documentation of how system is configured for booting. I run a new bootinfoscript with every rsync backup even though there may not be changes.

---

### Post by parker-hugh on 2014-11-28
Thanks again for the feedback, I am much clearer now on Grub than I was a couple of days ago.

Cheers, Hugh

---

