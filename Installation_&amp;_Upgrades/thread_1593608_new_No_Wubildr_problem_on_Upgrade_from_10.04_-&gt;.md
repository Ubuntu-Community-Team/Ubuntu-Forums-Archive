---
title: "new No Wubildr problem on Upgrade from 10.04 -&gt; 10.10?!"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by marley07 on 2010-10-11
This is just ridiculous.

I upgraded my Wubi installation from 10.04 to 10.10 beta a few nights ago and everything was fine. Then I got an update last night (one which I can only assume contained 10.10's official release). I installed it and was asked to reboot (which I did). Upon rebooting it, I was able to reach the normal GRUB screen where it asks if I want to boot my Ubuntu or my Windows 7 OS. When I click Ubuntu's partition, it says something along the lines of this:

Try(hd0,0) NTFS5: No wubildr
Try(hd0,1):

Then it instantly automatically restarts...no other messages or anything and I'm back to the Grub screen again...

I can boot to Windows 7 just fine (Go figure).

I've looked at a ton of forums and most people get the grub command line screen after having this problem. I don't. Most people also are able to hit insert to see more information. I can't.

Could it be an outdated wubildr or that my grub file got updated somewhere so it's pointing to an old wubildr?

Any information would be amazing! :confused:

---

### Post by bcbc on 2010-10-11
[http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

---

### Post by marley07 on 2010-10-11
Alright so first off, Thank you so much! That definitely worked.

Could you tell me why exactly though? I don't understand why it worked and if it was as simple as that, then why can't I just fix something in the grub.cfg file to make it work?

---

### Post by bcbc on 2010-10-11
I'd love to be able to explain this to you but getting information out of the developers is like extracting teeth.

What's happened is that grub2 has introduced some new commands/functionality and this is supported by new modules that need to go in the wubildr. Up to a few days before 10.10's release the command to refresh the wubildr during the upgrade was missing 3 modules. 

In addition, wubildr wasn't being updated at all in some cases. The devs have explained that they don't know how to update wubildr when the wubi install is on a different partition than windows. But even on installs on the same partition, the wubildr didn't get updated (at least not in the tests I ran).

When I manually updated my test wubi's wubildr, I just got a different error: 'no suitable mode found'. 

When you delete all those lines from grub.cfg it removes the new unsupported code along with probably a lot that will work, but really doesn't add anything that I've noticed. 

There was another problem introduced with 10.10. The \ubuntu\winboot\wubildr.cfg file was also not supported by the rescue grub module, and so a new wubildr-bootstrap.cfg was introduced to load that up. I haven't seen that being created for upgrades either so that is probably also an issue. (Again, I don't really have a deep understanding of this so take it with a grain of salt).

NOTE: whenever you run update-grub or install a new kernel or remove an old one it will regenerate grub.cfg and you'll have to reapply the workaround unless a fix has been provided by then.

---

### Post by Kelvin K on 2010-10-12
OK I've just been told to post anew as I too have this problem which several people are having too and this seemed to be appropriate place to repost.

I saw your recommendation **bcbc** but I'm just a simple point and click computer user and am not sure how to follow your instructions :(

I have an Acer Aspire Laptop which came with Windows Vista Installed. I have been using Ubuntu on desktops and I like it and wanted to use Ubuntu on my laptop. I went to the Ubuntu website and got the then latest release 10.4.

I was unaware that the installer would install Ubuntu INSIDE windows using Wubi. All I knew was that my new laptop now ran both Windows Vista and Ubuntu. I was pretty happy 

However along comes 10.10 telling me to upgrade and I blissfully follow the upgrade as I have made sure I update Ubuntu each day. 

Now I can't boot into Ubuntu (I get a very quick DOS like screen reporting some error or something and then the laptop goes back round to the start asking me which OS to boot up). The Windows boot up works fine but the Ubuntu option just puts me in this loop  I believe that this is Wubi asking me what I want to boot. Till now I really hadn't any idea what Wubi was and was unaware I had it, it was just how my laptop booted up I always chose Ubuntu and just got on with replying to emails etc

I need to get my Ubuntu working with the files I have on the machine already. There's lots of data that I really really really do NOT want to lose. How do I get my Ubuntu working again Please help me.

---

### Post by bcbc on 2010-10-12
> **Kelvin K said:**
> OK I've just been told to post anew as I too have this problem which several people are having too and this seemed to be appropriate place to repost.

I saw your recommendation **bcbc** but I'm just a simple point and click computer user and am not sure how to follow your instructions :(

I have an Acer Aspire Laptop which came with Windows Vista Installed. I have been using Ubuntu on desktops and I like it and wanted to use Ubuntu on my laptop. I went to the Ubuntu website and got the then latest release 10.4.

I was unaware that the installer would install Ubuntu INSIDE windows using Wubi. All I knew was that my new laptop now ran both Windows Vista and Ubuntu. I was pretty happy 

However along comes 10.10 telling me to upgrade and I blissfully follow the upgrade as I have made sure I update Ubuntu each day. 

Now I can't boot into Ubuntu (I get a very quick DOS like screen reporting some error or something and then the laptop goes back round to the start asking me which OS to boot up). The Windows boot up works fine but the Ubuntu option just puts me in this loop  I believe that this is Wubi asking me what I want to boot. Till now I really hadn't any idea what Wubi was and was unaware I had it, it was just how my laptop booted up I always chose Ubuntu and just got on with replying to emails etc

I need to get my Ubuntu working with the files I have on the machine already. There's lots of data that I really really really do NOT want to lose. How do I get my Ubuntu working again Please help me.

If you just want to get your data out of wubi the simplest way is to install ext2read 2.2 from [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) - I tried it once and apart from making my display a bit wonky allowed me to view and copy files from the wubi virtual disk (c:\ubuntu\disks\root.disk). It's a "read-only" view though so you can't update files.

If you want to get wubi booting again, you need to download and burn an Ubuntu CD or USB and then boot it in Live CD mode (Select "Try without installing"). Then run [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results and I'll give you specific commands to get it booting. But note that the 'fix' is just a workaround and may need to be repeated. If you can retrieve all your data first, a reinstall is better. (PS Don't uninstall Ubuntu from Windows until you're sure you've got everything or it will all be deleted).

---

### Post by marley07 on 2010-10-12
Kelvin K - If you go on your windows partition and go to where the ubuntu folder is, you can actually go into that folder and go to disks. Your root.disk (i think that's what it is called) file actually has all of your data (files, etc) from Ubuntu on it. I have made it a habit of periodically making a backup of this file. 

As for how to fix the boot problem (if it is indeed like mine), you have to boot Ubuntu from a CD. Just put the CD in, restart your computer and boot from the CD instead of your hard drive (You should get a screen the second you turn your computer on that says the name of the manufacturer and somewhere on that screen it should say to press a function key to go to drive selection menu. Mine was F12). After you select to Boot from the CD to and select run Ubuntu as is (no install, just straight from the disk) go to that link bcbc provided and do exactly as it says to do when you click the [loopmount]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?") link. 

I had to mess around a few times with the "sda1" thing in the instructions (I think mine was actually sda2) but if you just put in "sd" where the instructions say it and hit tab, it'll give you the options you can choose. You'll know it's the right partition number and disk letter when you can successfully go to the root.disk file in the following steps. Once this is "mounted" (which just means it's accessible from your current setup...CD in this case), you can enter the command "cd /" and "ls" and you should see that you can "cd vdisk" so that you can enter into the files that you are trying to access. (cd just means change directory and ls just lists the accessible folders/files from your present location. "/" is the root directory) Then you can type in what bcbc said (I had to use a different command to find the grub.cfg file and manipulate it because it was giving me a read only error... I used "vi" if you know how to use it. It doesn't matter how you go about changing the file as long as you find that grub.cfg file and are able to save your changes).

PS, all of this is done in terminal. :)

bcbc - That information helped, thank you. If you hear any more news about them fixing it, can you please post a reply on this forum? That would be amazing. 

Also, is there not a way to just manually update the wubildr? I know that I had to download a separate wubildr when I upgraded to 10.04 because UbuntuOS had some problems finding it because it wasn't in the first 4gb on my computer (or some bs like that...all I know is downloading wubildr and putting it where the instructions said fixed my problem). Shouldn't there be another workaround like that?

---

### Post by bcbc on 2010-10-12
> **marley07 said:**
> bcbc - That information helped, thank you. If you hear any more news about them fixing it, can you please post a reply on this forum? That would be amazing. 

Also, is there not a way to just manually update the wubildr? I know that I had to download a separate wubildr when I upgraded to 10.04 because UbuntuOS had some problems finding it because it wasn't in the first 4gb on my computer (or some bs like that...all I know is downloading wubildr and putting it where the instructions said fixed my problem). Shouldn't there be another workaround like that?

I'll update as soon as I know what the fix is. I believe that we will need a fix to the lupin package (required for wubi) before it will work. Lupin gives a special override to the grub-install command that will update wubildr on the /host partition. I think this functionality was added after that 9.10 issue when they realized they had to be able to update wubildr on the fly. 

I think you're probably right that copying a wubildr from a good 10.10 install will work - but I haven't got around to testing it. It will probably have to be supplemented by the new wubildr-bootstrap.cfg.

Here's the bug report [https://bugs.launchpad.net/wubi/+bug/653134](https://bugs.launchpad.net/wubi/+bug/653134)

---

### Post by Kelvin K on 2010-10-12
Pheeewwww!  :D

Thank you for the help. I'm currently making sure I get copies of all important photos that you can never repeat using the Ext2Read

*Excellent piece of software I'd definitely recommend anyone else get a copy of this for just such a rescue and I'm sure there will be thousands of people out there now with this problem*

I'll have a go at the booting Wubi via the CD option though the CDs I have are generally pretty old versions of Ubuntu but I'll try and get something more recent. Then I'll get the bootinfoscript working following your recommendations. I'm not into command line stuff so I hope I can do it as I haven't a clue what the commands are.

Thank you **bcbc** and **Marley07** both so much for your help so far it's very much appreciated and I'm certain there are many others out there with just the same problem.

Once I've got the data and if I manage to get into ubuntu again via Wubi I'll definitely be making moves to get Ubuntu on a completely separate partition. It seems to me that this Wubi thing is nothing more than a liability :(

---

### Post by Kelvin K on 2010-10-12
OK thanks to ext2read I've run in Windows I've copied the files I needed to onto another hard drive I've connected via USB. I've now booted up from a CD with Ubuntu 9.10 I found and grabbed a copy of bootinfoscript to the desktop.

I've just run bootinfoscript like this....
ubuntu@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda2/Wubi for information... 
Searching sdb1 for information... 
Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Desktop
ubuntu@ubuntu:~$ 

and the results are ....
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda2/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x475adfff

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,482,047    20,480,000  27 Hidden HPFS/NTFS
/dev/sda2    *     20,482,048   625,139,711   604,657,664   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98599660

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   625,137,344   625,137,282   c W95 FAT32 (LBA)


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       e41d5166-bf44-4439-bc62-abf014edeaae   ext4                                     
/dev/sda1        EAEE-EB49                              vfat       PQSERVICE                     
/dev/sda2        144044F24044DBDC                       ntfs       ACER                          
/dev/sdb1        6853-5BA9                              vfat       LaCie                         

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/LaCie             vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


Obviously I haven't much idea what to do with this info so I'd be really grateful if you can guide me through what to do next. Ideally I'd like to get Ubuntu up and running again from the laptop installation as I'd like to get all my emails, bookmarks, tomboynotes etc. Then when the dust has settled I'll put a separate partition in for Ubuntu. I will ditch Windows eventually but for the time being it's handy to have and it was already on the laptop anyway, it's better to have a planned migration of data rather than a forced one where you lose those bits you take for granted and forget about till you need them next.

Thanks for helping!

---

### Post by bcbc on 2010-10-12
Kelvin K: From a terminal (CTRL-ALT-t) enter:
```
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu gedit /mnt/boot/grub/grub.cfg
```

Look for the lines
> ###BEGIN /etc/grub.d/10_lupin
menuentry 'Ubuntu...

Delete everything above that menuentry to the beginning of the file. Save it. Exit. Reboot.

Don't install a new kernel or grub-pc update until you hear that it will fix the problem. You'll be looking for a lupin update when the fix arrives.

---

### Post by Kelvin K on 2010-10-12
YES ! ! ! ! \\:D/


**bcbc** You are such a STAR!

Thank you so so so much, yes I think you might have guessed it.... It works :D

Now I'll make sure I've got all my emails and calendars backed up.

Where do I look out for this lupin update?

Will it be all right to fresh install 10.10 on a separate partition if I partition my drive properly rather than this Wubi method? or do I need to wait for this lupin update first?

---

### Post by bcbc on 2010-10-12
> **marley07 said:**
> bcbc - That information helped, thank you. If you hear any more news about them fixing it, can you please post a reply on this forum? That would be amazing. 

Also, is there not a way to just manually update the wubildr? I know that I had to download a separate wubildr when I upgraded to 10.04 because UbuntuOS had some problems finding it because it wasn't in the first 4gb on my computer (or some bs like that...all I know is downloading wubildr and putting it where the instructions said fixed my problem). Shouldn't there be another workaround like that?
Just an update - I installed a fresh wubi 10.10 and copied all the boot files over to my computer with bad wubi upgrade. Didn't help. I had a slightly different version of the same problem: "No suitable mode found" and then reboot. Previous attempts to rebuild wubildr gave "no suitable mode" and a hangup. So not much better. 

I might try and purge/reinstall grub next. When I have time.

---

### Post by Kelvin K on 2010-10-13
> **bcbc said:**
> 
Don't install a new kernel or grub-pc update until you hear that it will fix the problem. You'll be looking for a lupin update when the fix arrives.

I don't know if this is a stupid question or not but the Update Manager has notified me that there are some security updates for 'Linux kernel image and headers' already this morning.

Is it safe to install these updates ? Or when you say "don't install a new kernel or grub-pc update" do you mean the next release e.g 11.4?

---

### Post by bcbc on 2010-10-13
> **Kelvin K said:**
> I don't know if this is a stupid question or not but the Update Manager has notified me that there are some security updates for 'Linux kernel image and headers' already this morning.

Is it safe to install these updates ? Or when you say "don't install a new kernel or grub-pc update" do you mean the next release e.g 11.4?

It will regenerate grub.cfg. You can install the update, but before you reboot, just go and edit the /boot/grub/grub.cfg, the same as before. Otherwise you'll end up in the same situation.

---

### Post by Lhademmor on 2010-10-13
Hi guys, I'm not trying to hijack the thread or anything, but I'm having the exact same problem, and I can't solve it with a LiveCD because my CD-ROM drive is completely ****ed, and spits out all sorts of errors with almost any CD. That's the reason why I went with Wubi in the first place.

Is there any other way of getting through this? Is there any chance that we'll get a 10.10 Wubi update? I have nothing of value on the Wubi installation so in that case I could just uninstall Wubi and install a new version.

Do anyone know of an ETA on a proper, non-rebooting, 10.10-installing Wubi?

---

### Post by bcbc on 2010-10-13
> **Lhademmor said:**
> Hi guys, I'm not trying to hijack the thread or anything, but I'm having the exact same problem, and I can't solve it with a LiveCD because my CD-ROM drive is completely ****ed, and spits out all sorts of errors with almost any CD. That's the reason why I went with Wubi in the first place.

Is there any other way of getting through this? Is there any chance that we'll get a 10.10 Wubi update? I have nothing of value on the Wubi installation so in that case I could just uninstall Wubi and install a new version.

Do anyone know of an ETA on a proper, non-rebooting, 10.10-installing Wubi?
This should only impact upgrades. If you have nothing of value then just reinstall. Right now you are advised to install on C: (main windows partition)

---

### Post by Kelvin K on 2010-10-13
OK thank you **bcbc** I'm glad I checked with you, it wasn't a stupid question after all

---

### Post by Lhademmor on 2010-10-14
> **bcbc said:**
> This should only impact upgrades. If you have nothing of value then just reinstall. Right now you are advised to install on C: (main windows partition)

I would if I could find a Wubi installer that installed 10.10. The current Wubi - linked to from the 10.10 download page - still installs 10.04.

Also, I'm already installing on C:

---

### Post by bcbc on 2010-10-14
> **Lhademmor said:**
> I would if I could find a Wubi installer that installed 10.10. The current Wubi - linked to from the 10.10 download page - still installs 10.04.

Also, I'm already installing on C:
You can get wubi.exe 10.10 here...
[http://mirror.csclub.uwaterloo.ca/ubuntu-releases/maverick/](http://mirror.csclub.uwaterloo.ca/ubuntu-releases/maverick/)

---

### Post by Lhademmor on 2010-10-15
> **bcbc said:**
> You can get wubi.exe 10.10 here...
[http://mirror.csclub.uwaterloo.ca/ubuntu-releases/maverick/](http://mirror.csclub.uwaterloo.ca/ubuntu-releases/maverick/)

Hey, thanks mate! I'll get right on that :D

---

### Post by santana007 on 2010-10-15
Thanks to all that posted here. Got my system working again as per:  [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5). Think I will repartition and make a permanent install of 10.10.

---

### Post by bcbc on 2010-10-15
> **santana007 said:**
> Thanks to all that posted here. Got my system working again as per:  [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5). Think I will repartition and make a permanent install of 10.10.

Or migrate your wubi: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by santana007 on 2010-10-15
> **bcbc said:**
> Or migrate your wubi: [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Yes, I think I read something similar in the WubiGuide

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

I will investigate further. Thanks for the info.

---

### Post by bcbc on 2010-10-15
> **santana007 said:**
> Yes, I think I read something similar in the WubiGuide

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20migrate%20to%20a%20real%20partition,%20and/or%20get%20rid%20of%20Windows%20entirely?)

I will investigate further. Thanks for the info.

The one in the wubi guide worked on older versions of Ubuntu. Also LVPM hasn't been updated since 8.04. The script in that link is based on the wubi guide script but updated for grub2 and some other deprecated commands etc.

---

### Post by capput on 2010-12-03
Thanks bcbc.  The information in the links were a lot of help.

---

### Post by dg_hosey on 2010-12-04
Can I also get help please? Here is the boot info

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Acer 3 is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /ubuntu/winboot/wubildr.mbr /wubildr 
                       /ubuntu/winboot/wubildr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb47bb8fc

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    24,578,047    24,576,000  27 Hidden HPFS/NTFS
/dev/sda2    *     24,578,048    24,782,847       204,800   7 HPFS/NTFS
/dev/sda3          24,782,848   976,771,071   951,988,224   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       30696f47-26f5-4838-b95e-7315d73315a2   ext4                                     
/dev/sda1        0A5AB7A25AB78949                       ntfs       PQSERVICE                     
/dev/sda2        60FCBA69FCBA395C                       ntfs       SYSTEM RESERVED               
/dev/sda3        7AC2BCE9C2BCAB31                       ntfs       Gateway                       

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


======================== sda3/Wubi/boot/grub/grub.cfg: ========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ntfs
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 7ac2bce9c2bcab31
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ntfs
set root='(hd0,3)'
search --no-floppy --fs-uuid --set 7ac2bce9c2bcab31
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/10_lupin ###
menuentry "Ubuntu, Linux 2.6.32-26-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 7ac2bce9c2bcab31
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-26-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 7ac2bce9c2bcab31
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-26-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-26-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 7ac2bce9c2bcab31
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-25-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 7ac2bce9c2bcab31
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-25-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-25-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 7ac2bce9c2bcab31
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro   quiet splash
    initrd /boot/initrd.img-2.6.32-24-generic
}
menuentry "Ubuntu, Linux 2.6.32-24-generic (recovery mode)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 7ac2bce9c2bcab31
    loopback loop0 /ubuntu/disks/root.disk
    set root=(loop0)
    linux /boot/vmlinuz-2.6.32-24-generic root=/dev/sda3 loop=/ubuntu/disks/root.disk ro single 
    initrd /boot/initrd.img-2.6.32-24-generic
}
### END /etc/grub.d/10_lupin ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows Vista (loader) (on /dev/sda1)" {
    insmod ntfs
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 0a5ab7a25ab78949
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda2)" {
    insmod ntfs
    set root='(hd0,2)'
    search --no-floppy --fs-uuid --set 60fcba69fcba395c
    chainloader +1
}
menuentry "Windows 7 (loader) (on /dev/sda3)" {
    insmod ntfs
    set root='(hd0,3)'
    search --no-floppy --fs-uuid --set 7ac2bce9c2bcab31
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

============================= sda3/Wubi/etc/fstab: =============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

================= sda3/Wubi: Location of files loaded by Grub: =================


  13.3GB: boot/grub/grub.cfg
  12.2GB: boot/initrd.img-2.6.32-24-generic
   8.4GB: boot/initrd.img-2.6.32-25-generic
   5.7GB: boot/initrd.img-2.6.32-26-generic
  15.5GB: boot/vmlinuz-2.6.32-24-generic
  12.8GB: boot/vmlinuz-2.6.32-25-generic
  15.6GB: boot/vmlinuz-2.6.32-26-generic
   5.7GB: initrd.img
   8.4GB: initrd.img.old
  15.6GB: vmlinuz
  12.8GB: vmlinuz.old

---

### Post by bcbc on 2010-12-05
> **dg_hosey said:**
> Can I also get help please? 

You root.disk is on /dev/sda3, so boot the live CD, go to a terminal (CTRL+ALT+t):
```
sudo mkdir /media/win
sudo mount /dev/sda3 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu gedit /mnt/boot/grub/grub.cfg
```
Delete all lines up to but NOT INCLUDING the first line starting with "menuentry". Save exit, unmount and reboot.
```
sudo umount /mnt
sudo umount /media/win

```

Then Wubi should boot normally. There is now a permanent fix described here (that you can only do after you get wubi booting):
[http://ubuntuforums.org/showpost.php?p=10180520&postcount=78](http://ubuntuforums.org/showpost.php?p=10180520&postcount=78)

---

### Post by dg_hosey on 2010-12-20
Thanks so much

---

### Post by tmcmulli on 2010-12-28
Worked great, thanks guys.  Been running wubi on my work laptop for years... so disappointed that Ubuntu seems to be headed down the wrong path... Here's to hoping the next LTS is better than 10.10 in a bunch of ways.

---

