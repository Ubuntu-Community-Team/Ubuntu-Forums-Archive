---
title: "dual booting from windows boot manager"
date: 2012-12-13
forum: Installation &amp; Upgrades
---

### Post by xana40 on 2012-12-13
I have watched tutorials and read tons of articles on this subject. I narrowed it down to the essential fact that if I want both on a single hdd, I'll need to let windows manage or else it will eventually update and kill off the grub. So I now have these partitions: 1)system (mbr) 2)c drive (ntfs/windows7) 3)d drive (ntfs/file storage) 4)boot(ext4/grub/recognized as sda5) 4)root (ext4 ubuntu 12.04/sda6) 5)swap. Since I chose this configuration, Ubuntu did not just magically appear in windows boot selection. I've also read this can be resolved with easybcd. Apparently there are some comments that say this program is invasive and is similar to adware. So I tried the manual approach to bcdedit and  got an error message \ubuntu.pbr ...application is missing or corrupt. Any suggestions?  thanks, xana40
btw...my first attempt landed grub in the mbr sector and ubuntu loaded but the grub menu couldn't display on my monitor

---

### Post by oldfred on 2012-12-13
Welcome to the forums.

Some do like to use EasyBCD to use Windows boot loader, but we prefer grub. Grub is designed to multi-boot. Windows is only designed to boot Windows.

Even if Windows overwrites grub, it is easy to reinstall.

In the beginning there were issues with flexnet and some other DRM rights management software. Grub created a work around for flexnet. Some HP or Dell utilities also created issues, but virtually everyone uninstalled those as they said they were worthless. So now there are rarely issues.

If you use EasyBCD you have to force grub2 into the PBR - partition boot sector. Grub does not like that and does not really fit. It has to use blocklists or hard coded address of the next grub file to use to boot. Normally it has enough code to do a search.  If grub is updated or even an aggressive filecheck that changes a file's address  and then you have to reinstall grub.

 [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling](https://help.ubuntu.com/community/Grub2#Reinstalling) GRUB2

---

### Post by xana40 on 2012-12-14
[LEFT]Thank you, oldfred, for a prompt reply. I have reviewed the links in your post and still would like to find an answer to the mystery of booting through windows mbr. 

 Since yesterday when I asked the question, I connected my older ide hard drive and formatted with ubuntu. This way I can still use this one while experimenting with the other one :D.
The instructions that I used  stated
1. Copy file/boot/grub/boot.img to c: (windows root folder)

I found the file "boot.img" , did a right click, copy, went to c drive and did paste. This was only possible with the ext2fsd driver and mounting the boot partition of ubuntu so windows could see it.
Somehow I don't think that created a path to the core.img which would have been able to load ubuntu. Maybe I'm missing something.  I'll post if I figure it out.
[/LEFT]

---

### Post by oldfred on 2012-12-14
I do not know EasyBCD.

       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

    
But I think you have to install grub2 to the partition so Easy can chainload to the grub install in the partition.

---

### Post by debodas on 2012-12-14
If you want to use the windows boot manager, install grub on the partition you give the / mount point. Looking at you post I think you plan on giving /dev/sda6 the / mount point? If so, install grub to /dev/sda/6.

---

### Post by xana40 on 2012-12-29
I have spent the last 2 weeks learning my way around linux/ubuntu and I have found what I believe is the answer. Only after getting scolded by my terminal with the message "bad idea" lol. Yeah, it probably is a bad idea to want to take away some of the automation. This is an extra computer that came along and gives me a lot of latitude to learn even it gets messed up. 
If I wanted everything decided for me, I would have stuck with windows!

I get it, Grub2 does not do well outside of the master boot area on a harddrive. But it can, if you set  it up right. It needs a physical area away from day to day activities. So a separate boot partition will help.

A copy and paste of the boot.img into your  C drive on windows does work. I had to go to windows7 recovery and command line prompt to enter the path to the boot.img file. Telling it to call the bootloader Ubuntu.

Now I have a windows and Ubuntu dual boot selection at start up. The Ubuntu (because of the boot.img) takes me to a Grub rescue prompt. I finally figured out that the ls command shows what _**it**_ sees as my partitions.  So, set root=(hd0,5) and the set prefix=(hd0,5)/grub .  Then, miraculously , the Ubuntu os loaded.

That's when my terminal would not save my mod in Grub. Most all of the instructions are based on Grub being installed in the master boot sector of the harddrive. I just didn't want to give up. So this evening I tried another search and voila! 

I haven't tried this yet but it looks promising!

[https://wiki.archlinux.org/index.php/GRUB2](https://wiki.archlinux.org/index.php/GRUB2)
**  Install to Partition or Partitionless Disk **

 ** Note: **grub-bios  (any version - including upstream Bazaar repo) does not encourage  installation to a partition boot sector or a partitionless disk like  GRUB Legacy or Syslinux does. This kind of setup is prone to breakage,  especially during updates, and is not supported by Arch devs.
 To set up grub-bios to a partition boot sector, to a partitionless disk (also called superfloppy) or to a floppy disk, run (using for example /dev/sdaX as the /boot partition): 
 # modprobe dm-mod  # chattr -i /boot/grub/i386-pc/core.img # grub-install --target=i386-pc --recheck --debug --force /dev/sdaX # mkdir -p /boot/grub/locale # cp /usr/share/locale/en@quot/LC_MESSAGES/grub.mo /boot/grub/locale/en.mo # chattr +i /boot/grub/i386-pc/core.img  You need to use the --force option to allow usage of blocklists and should not use --grub-setup=/bin/true (which is similar to simply generating core.img). 
grub-install will give out warnings like which should give you the idea of what might go wrong with this approach: 
 /sbin/grub-setup: warn: Attempting to install GRUB to a partitionless disk or to a partition. This is a BAD idea. /sbin/grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists.                          However, blocklists are UNRELIABLE and their use is discouraged.  Without --force you may get the below error and grub-setup will not setup its boot code in the partition boot sector: 
 /sbin/grub-setup: error: will not proceed with blocklists  With --force you should get: 
 Installation finished. No error reported.  The reason why grub-setup does not by default allow this is because in case of partition or a partitionless disk is that grub-bios relies on embedded blocklists in the partition bootsector to locate the /boot/grub/i386-pc/core.img file and the prefix dir /boot/grub. The sector locations of core.img may change whenever the filesystem in the partition is being altered (files copied, deleted etc.). For more info see [https://bugzilla.redhat.com/show_bug.cgi?id=728742](https://bugzilla.redhat.com/show_bug.cgi?id=728742) and [https://bugzilla.redhat.com/show_bug.cgi?id=730915](https://bugzilla.redhat.com/show_bug.cgi?id=730915). 
The workaround for this is to set the immutable flag on /boot/grub/i386-pc/core.img (using chattr command as mentioned above) so that the sector locations of the core.img file in the disk is not altered. The immutable flag on /boot/grub/i386-pc/core.img needs to be set only if grub-bios is installed to a partition boot sector or a partitionless disk, not in case of installation to MBR or simple generation of core.img without embedding any bootsector (mentioned above). 
 **  Generate core.img alone **

 To populate the /boot/grub directory and generate a /boot/grub/i386-pc/core.img file **without** embedding any grub-bios bootsector code in the MBR, post-MBR region, or the partition bootsector, add --grub-setup=/bin/true to grub-install: 
 # modprobe dm-mod # grub-install --target=i386-pc --grub-setup=/bin/true --recheck --debug /dev/sda # mkdir -p /boot/grub/locale # cp /usr/share/locale/en@quot/LC_MESSAGES/grub.mo /boot/grub/locale/en.mo  You can then chainload GRUB2's core.img from GRUB Legacy or syslinux as a Linux kernel or a multiboot kernel.

---

