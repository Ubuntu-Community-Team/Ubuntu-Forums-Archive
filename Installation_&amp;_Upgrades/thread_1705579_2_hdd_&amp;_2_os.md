---
title: "2 hdd &amp; 2 os"
date: 2011-03-12
forum: Installation &amp; Upgrades
---

### Post by colt247365 on 2011-03-12
Hi! I have probably a simple question, but I need some help. I have 2 Western Digital Hard Drives. First I installed Ubuntu Lucid Lynx 64 on the first hard drive, and installed Windows 7 Ultimate Edition 64 on the second hard drive. After I installed Windows, everytime I turn on my computer, it automatically boots into Windows. How do I select my operating system at start up? On another computer I partitioned a single hard drive and dual booted, which gave me the GRUB loader, but with 2 hard drives I don't have a prompt where I can select my operating system. Any help? Thanks a bunch in advance.

---

### Post by ericrichards420 on 2011-03-12
Try installing ubuntu on the same drive as the windows os and use the second drive as drive space. just use gparted in ubuntu to partition the drives after you get it installed. or I geuss you could go into your bois and select it to start from hdd1 to start ubuntu.
are you sure you have the second drive set to slave and the first jumper set to master. make sure the slave drive is hooked to the first slot on the ide cable and it should work

---

### Post by colt247365 on 2011-03-12
I thought about that and it is an option, but I thought I would just keep things neater by using one OS per hard drive. If all else fails I could do this, but I don't really want to.

---

### Post by Hakunka-Matata on 2011-03-12
Welcome to Ubuntuforums:

You need to reinstall Grub, the bootloader to the MBR of your 'first hard drive' , probably defined as /dev/sda.
> Let me restate that: You **may need** to reinstall Grub (thanks oldfred)

Post the output of these two commands so we can see your drive configuration:

```
sudo fdisk -lu
sudo parted -l
```

---

### Post by colt247365 on 2011-03-12
Alright we'll see where that gets me.

---

### Post by oldfred on 2011-03-12
Are these SATA drives? You may just have to in BIOS change boot order or try using one time boot key to select other drive to boot. If older IDE drives then you may only be able to boot primary master in IDE chain.

To see entire configuration.

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by Hakunka-Matata on 2011-03-12
Post # 4 edited - H-K

---

### Post by colt247365 on 2011-03-12
> **oldfred said:**
> Are these SATA drives? You may just have to in BIOS 


Yup, Sata drives, makes sense I might have to play around in Bios config. Here's the RESULTS.TXT

---

### Post by oldfred on 2011-03-12
Have you been able to boot windows after installing Ubuntu?

Boot script does not show normally hidden windows boot partition. It looks like when you installed windows to the second drive it put its boot files on the first which were then overwritten. You can repair the windows install with a windows repair disk.

But windows and drive number and grub & drive number often get confused. Most have windows on the first drive and that works. Some have posted with issues with windows on drive 1 and only some have seemed to make it work. Probably a BIOS issue on how it reports drive number to grub/windows.

---

### Post by colt247365 on 2011-03-12
After installing Ubuntu, I have not been able to boot into Windows 7. I do not have a GRUB loader menu pop up after it flashes my processor, and bios configuration.

---

### Post by oldfred on 2011-03-12
See my posts in this thread.

oldfred's Windows Vista/Win7 repair links posts #7 & #9:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

Make sure boot flag is set for any partition you try to repair, otherwise the windows repair will not see the partition.
You can use gparted, click on partition and manage flags, or in Disk Utility, click on partition and edit to change boot flag.

Not sure with it as sdb how window will see it.

---

### Post by YesWeCan on 2011-03-12
It is a wise plan to have the two OSes on separate drives.

Your RESULTS.TXT looks ok to me.

Just to state the obvious...your bios will be set to boot off a particular drive first. At the moment it seems it boots your Windows drive. If you select boot options during the POST you should be able to choose to boot the Ubuntu drive. What happens when you do this?

If that boots Ubuntu ok, then you need to add your Windows install to your Grub2 menu. It won't be there yet because Grub2 does not synamically scan for OSes and because Windows wasn't yet installed when you installed Grub2. You simple run 'sudo update-grub'.

You may also choose to add Ubuntu to your Windows boot menu. From Windows, download EasyBCD (free) and use it to automatically locate your linux/Grub2 and add a link to your Windows menu.

[edit] I just read your post #10. I'm confused because in post #1 you could only boot Windows.

---

### Post by colt247365 on 2011-03-12
Yea, I reinstalled Ubuntu just to see if that had any effect on boot order, and now it boots into Ubuntu by default. I added boot flags to the hard drives in Gparted, to no avail.

---

### Post by YesWeCan on 2011-03-12
The acid test is to disconnect each drive in turn and see when it boots and when it doesn't. If each drive boots on its own then it is a simple step to make a dual-boot menu.

BTW this is the way I recommend to people to set up dual boots on separate drives. Have only 1 drive connected at a time and do a separate install on each. Only then connect both up and set up the dual-boot menu. This guarantees each OS is properly installed and all its components are only installed on its own drive. Also avoids having to make decisions in the Ubuntu installer.

---

### Post by kagerato on 2011-03-12
> **colt247365 said:**
> Yea, I reinstalled Ubuntu just to see if that had any effect on boot order, and now it boots into Ubuntu by default. I added boot flags to the hard drives in Gparted, to no avail.

What's confusing here is this: do you have separate boot records on each drive?  For example, a Grub master boot record on one and the typical Windows master boot record on the other?  Or is there only one functional MBR which is being overwritten every time you reinstall an OS?

I think it's the latter, but I'm not certain.  If you're keeping the BIOS drive boot order fixed on one drive, and installing OSes with the default options, it's very likely you have only one active boot record.  That's fine, and typically expected.

In order to get the effect you want, you need to configure grub to chainload the Windows 7 bootloader.  If you're booting automatically into Ubuntu, you have grub installed on the active MBR.  It's merely that the grub menu is being hidden by default.  This is configurable (and I would recommend changing it).

There's a long Ubuntu community article on Grub 2 configuration:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

However, to summarize some of the things you can learn from it:

(1) The Grub 2 configuration scripts are stored in /etc/grub.d/  .
(2) These files are interpreted, and then the result is concatenated together to form the effective grub configuration file, which will be written to /boot/grub/grub.cfg  .
(3) The command 'update-grub' is used in Ubuntu to apply changes made to the config scripts, rebuilding /boot/grub/grub.cfg in the process.
(4) When you run 'update-grub', that script will typically find any new operating systems for you.  Though in the rare case it doesn't, it's possible to add them manually.

Configuring grub may seem scary at first, but it's reasonably straightforward once you've read (and understood) the docs.

It may help to see what a final Grub 2 configuration looks like.  This is mine, simplied a bit:

```

set menu_color_normal=yellow/black
set menu_color_highlight=red/black

menuentry "Xubuntu Core" --class ubuntu --class gnu-linux
{
  insmod ext2
  set root='(hd0,2)'
  linux /boot/vmlinuz-2.6.35.5-ouga root=/dev/sda2 ro quiet
}

menuentry "Xubuntu Development" --class ubuntu --class gnu-linux
{
  insmod ext2
  set root='(hd0,5)'
  linux /boot/vmlinuz-2.6.35.5-ouga root=/dev/sda5 ro quiet
}


menuentry "Windows 7"
{
  insmod ntfs
  set root='(hd0,1)'
  chainloader +1
}

```Note that I left out the initialization segment which loads certain modules and fonts, sets the graphics mode, and some other options.  All of that is typically generated for you automatically with 'update-grub', using the settings in /etc/default/grub (and a few other source locations).

In case it's not clear, my setup above has one Xubuntu installation on /dev/sda2 , another on /dev/sda5 , and Windows 7 on /dev/sda1 .  Each system's root (hdX,Y) entries need to match the actual partition layout of that system.  As I mentioned, typically the update-grub script figures out what is what automatically.

---

### Post by XsheepX on 2011-03-12
Open your BIOS by pressing F12 (or whatever button it may be, depending on your computer) and change the boot sequence to boot your other hard drive first, or simply select to boot from that hard drive for that time only.

---

### Post by oldfred on 2011-03-12
Because you have two drives and they are SATA you can have two MBR's one with windows and one with Ubuntu's grub.

 I think to repair windows you have to set the windows drive as the boot drive before repair or it may install its boot loader on the sda Ubuntu drive. The way to be sure is to physically disconnect Ubuntu and repair windows.

Once windows is repaired the osprober will find it.
```

sudo update-grub
```

---

### Post by XsheepX on 2011-03-12
> **oldfred said:**
> Because you have two drives and they are SATA you can have two MBR's one with windows and one with Ubuntu's grub.

 I think to repair windows **you have to set the windows drive as the boot drive** before repair or it may install its boot loader on the sda Ubuntu drive. The way to be sure is to** physically disconnect Ubuntu** and repair windows.

Once windows is repaired the osprober will find it.
```

sudo update-grub
```
Yes, exactly. OP, try booting from the other HDD in the BIOS first, and see if it will boot Windoze. If not, try this.

---

### Post by colt247365 on 2011-03-13
> **kagerato said:**
> .

In order to get the effect you want, you need to configure grub to chainload the Windows 7 bootloader.  If you're booting automatically into Ubuntu, you have grub installed on the active MBR.  It's merely that the grub menu is being hidden by default.  This is configurable (and I would recommend changing it).

Hey, you got my GRUB Loader back, thanks! I still boot into Ubuntu fine, but underneath Windows it says

BOOTMGR is missing
Press Ctrl+Alt+Del to restart
_

Do you think if I repair Windows from the disk it should work? EDIT: No dice. FYI I have Windows on my second hard drive as my only partition, so I put
> menuentry "Windows 7"
{
  insmod ntfs
  set root='(hd1,1)'
  chainloader +1
}

---

### Post by oldfred on 2011-03-13
If you have not run the windows repairs, it will continue to say bootmgr missing. Typical boot/recovery hidden windows partition has these two files that are missing. Repairs will add them back.

/bootmgr /Boot/BCD 

You can run boot script to see if they are in your windows partition. If not you need the repairs. Post #11.

---

