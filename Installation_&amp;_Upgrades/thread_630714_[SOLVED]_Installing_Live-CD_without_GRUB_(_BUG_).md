---
title: "[SOLVED] Installing Live-CD without GRUB ( BUG )?"
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by perixx on 2007-12-03
Hello...

I want to install Xubuntu Feisty from the Live-CD, but **without ** installing Grub! I believe it contains a BUG, since I tried to install it to the superblock twice and it terminated the installation 'Grub was not installed, that is a serious failiure' during the process, at the point Grub began to install, leaving me with an unbootable system. 
Btw., I've also tried it with Xubuntu AMD64 Gutsy - same effect...

I managed to fix that meanwhile, but I want to prevent Ubuntu from messing up everthing (I'm using the Grub in that partition for chainloading other distros!).

My setup can be reviewed here:

[http://ubuntuforums.org/showthread.php?t=621827]("http://ubuntuforums.org/showthread.php?t=621827")

So, how can I install without installing the Grub as well, specifying the boot parameters in the menu.lst manually afterwards?


perixx

---

### Post by perixx on 2007-12-04
*bump*

---

### Post by logos34 on 2007-12-04
If I understand you correctly, then what you want to do during installation is tell it to install grub to the bootsector of the new xubuntu root partition, NOT the MBR.  So at step 7 ('Ready to install'), hit 'Advanced' button lower right, and replace the default '(hd0)' with '**(hd0,x)**', where x=xubuntu root partition. (so if for example it's hda5, you would enter '(hd0,4)' because grub starts counting from 0.  Or else type '**/dev/hda5**').  The result is that you won't overwrite the current grub stage1 on the mbr, and it will be bootable from the other menu.lst as soon as you add an entry.  (whereas if you do not install grub you get a 'fatal error' message and have to fix it by running 'grub-install'  from the live cd to generate the boot files in /boot/grub.)

Then add a xubuntu entry (use [configfile]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") format) to the existing grub menu.lst.  

Hopefully that will work for you.

---

### Post by perixx on 2007-12-04
logos34, sorry but you seem to have been mislead by my words.
I want to install Linux **WITHOUT installing Grub AT ALL**, since I've already installed it on another partition and want to run Linux directly from the Grub in that partition.


perixx

---

### Post by jken146 on 2007-12-04
Why don't you just overwrite the GRUB you had originally on the MBR?  Other distros should be detected.

logos34 is right though, you can install a new GRUB to a location that won't be booted.

---

### Post by maybeway36 on 2007-12-04
Choose Advanced... on the last screen and uncheck the boot loader or change it to (fd0) if you have a flopy disk.

---

### Post by perixx on 2007-12-04
I have reasons... in this case, because Grub-install will always terminate during the Ubuntu setup, leaving me with an unusable system. Since installing Grub over and over again seems superflous to me, that'd be a simple solution, wouldn't it?

perixx

---

### Post by logos34 on 2007-12-05
then just uncheck the grub option at the end...it will complain as mentioned above...reboot into your other ubuntu and add a regular entry (can't use configfile) to menu.lst to directly boot the kernel on the xubuntu install:

> title		Xubuntu 7.04, kernel 2.6.20-16-generic
root		(hd0,?)
kernel		/boot/vmlinuz-2.6.20-16-generic root=/dev/hda? ro splash
initrd		/boot/initrd.img-2.6.20-16-generic

You can use the 'root=/dev/...' or 'root=UUID-...' format. (to find the uuid of the new xubuntu install run 'blkid' or 'ls -l /dev/disk/by-uuid')

However, you may have problems during the next kernel update because grub-install will not know what root device ('groot') to update.  Maybe it will just deposit the new kernel in /boot and allow you to add it manually to your other menu.lst. Hopefully it won't cause any problems.  I'm not sure because although I've installed a few times using the live cd and left the grub dialog box blank (resulting in the above-mentioned fatal error), I've never left it that way long enough to find out what happens with a kernel update.

([this pag]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location")e discusses the it from the point of view of the alternate cd install, but does not exactly address your issue)

---

### Post by perixx on 2007-12-05
> just uncheck the grub option at the end 
oh... I seems to have missed the checkmark-box? :)

Oh, well seems easy enough then. Except for that 'groot' problem... isn't there a way to specify the 'groot' entry in the menu.lst? I think I've read somewhere about it... but to be perfectly honest, I didn't quite get it what 'groot' does.

Did I understand you correctly, that, with each kernel-update, the Grub-manager has to be updated too - and that it's a problem if I have, say, a 'master-Grub' in the MBR, but no chainloaded Grub's in the respective partitions because the separate kernels have no idea where they were booted from (and that's what the groot-command is telling them)??

perixx

---

### Post by logos34 on 2007-12-05
checkbox --> step 7 "Ready to install' --> click 'Advanced' button lower right and take out '(hd0)' and or uncheck grub option in the popup dialog box

the problem is that when an update comes along the grub-install program will run after you download the new kernel.  Normally it checks the menu.lst and adds an entry for the new kernel at the top of the 'automagic' section.  (the 'groot' line is mainly there for cases where /boot is on a dedicated partition, separate from /root).  But since you won't have a grub folder or menu.lst grub-install will automatically generate a new one (along with all the other files) and add entries for all the kernels in /boot. Hopefully it won't try to reinstall grub to the mbr (but that's what running 'grub-install /dev/hda' does) or cause a problem.  You'll do any kernel updates in each of your (x)ubuntu partitions independantly, so all you have to do is manually add the new kernel entry to the 'master' grub.  

If it does overwrite the mbr simply reinstall grub from the live cd pointing the correct root partition.

---

### Post by perixx on 2007-12-06
thank you logos, for pointing out those facts!
Auto-installing Grub into the MBR would be a big bad, as hda1 is dedicated to XP, thus, it would render Windows unusable.

Isn't there an option I can set somewhere (in the menu.lst or somewhere else) that can tell the kernel to skip grub-updates in any case?


perixx

---

### Post by logos34 on 2007-12-06
correction: after a new kernel is installed it's specifically /sbin/update-grub that runs, and which adds it to the existing menu.lst (or if absent creates one anew listing all the vmlinuz- and initrd,img- in /boot).  So hopefully that's all that will happen.  

Not sure about the option to skip updates...don't see one in menu.lst specifically for that, although there may be something you could add the /etc/kernel-img.conf file.  

You could just go Synaptic pkg mgr>Packages>'Lock version' on your linux-image-2.6.xxx-generic kernel...that's the easiest way I believe

---

### Post by perixx on 2007-12-06
isn't a new kernel only installed when doing a system-upgrade - speaks: Feisty 2 Gutsy? 

perixx

---

### Post by MQMike on 2007-12-06
I know what you are saying.  I do stuff like this all the time.

There is NO harm done installing GRUB to the same partition as you installed the root files of your OS during the OS installation procedure (choosing “Manual”—GRUB is specified in Step 6, behind the Advanced button;  or use the Alternate installer).  GRUB is just a bunch of files – they will just safely sit there unless/until you wish to use them.  Or, overwrite them later from another /grub.  Whatever.  However, do NOT install GRUB to *any* MBR unless that is specifically what you want to do, as it will overwrite any other bootloader already installed to the MBR (of the drive in question).  Etc.

Then, do whatever you wish later:
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

### Post by perixx on 2007-12-06
Thx Mike.

The reason I'm worried about installing Grub during the installation is, that I've had trouble with Grub-setups breaking up with an 'serious' error on an already existing (alternative) /boot/grub folder on another partition. I then had a non-functioning boot menu (formerly working) - this happened twice.

So I thought, why change a running system when all I need to do is manually adding the new OS to the menu.lst?

> You can use the 'root=/dev/...' or 'root=UUID-...' format. (to find the uuid of the new xubuntu install run 'blkid' or 'ls -l /dev/disk/by-uuid')
Merci beacoup, logos34! Very useful little helper for fixing my fstab again! Only proper NTFS print-outs are missing, but I don't need to auto-mount these anyway.


perixx

---

### Post by perixx on 2007-12-08
```
/dev/hda9: UUID="994800a4-cd6d-40b0-b74c-3c99db04311c" SEC_TYPE="ext2" TYPE="ext3" 

```

despite the fact that I've manually edited my fstab file, these added partition(s) aren't automatically added and accessible with Thunar - also not via CLI... why?

perixx

---

### Post by IeU on 2007-12-08
> **logos34 said:**
> If I understand you correctly, then what you want to do during installation is tell it to install grub to the bootsector of the new xubuntu root partition, NOT the MBR.  So at step 7 ('Ready to install'), hit 'Advanced' button lower right, and replace the default '(hd0)' with '**(hd0,x)**', where x=xubuntu root partition. (so if for example it's hda5, you would enter '(hd0,4)' because grub starts counting from 0.  Or else type '**/dev/hda5**').  The result is that you won't overwrite the current grub stage1 on the mbr, and it will be bootable from the other menu.lst as soon as you add an entry.  (whereas if you do not install grub you get a 'fatal error' message and have to fix it by running 'grub-install'  from the live cd to generate the boot files in /boot/grub.)

Then add a xubuntu entry (use [configfile]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile") format) to the existing grub menu.lst.  

Hopefully that will work for you.

hum nice,

my problem is that ubuntu installation does not right grub on mbr, so ive dual boot with xp and while booting i never get prompted asking me what i want to boot, i get directly on xp

so the mbr would be hd0 ?

---

### Post by logos34 on 2007-12-08
> **IeU said:**
> so the mbr would be hd0 ?

Yes.

You might check[ this]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect").  Or maybe grub did write to the MBR but your /boot/grub/menu.lst is defaulting for some reason  to windows instead of ubuntu

try [reinstalling grub]("http://ubuntuforums.org/showthread.php?t=224351").

If you have more than one drive maybe grub is there instead

---

### Post by logos34 on 2007-12-08
> **perixx said:**
> ```
/dev/hda9: UUID="994800a4-cd6d-40b0-b74c-3c99db04311c" SEC_TYPE="ext2" TYPE="ext3" 

```

despite the fact that I've manually edited my fstab file, these added partition(s) aren't automatically added and accessible with Thunar - also not via CLI... why?

pardon me if i've forgotten the details...did you [create a mountpoint]("http://www.psychocats.net/ubuntu/mountlinux")?

sudo mkdir /media/hda9

---

### Post by perixx on 2007-12-08
Yep. These are my entries:

> # /dev/hda8
UUID=7cfeea25-e1a5-4ad1-8f07-2dc31038f61b /media/hda8	ext3	defaults	0	2
# /dev/hda9
UUID=994800a4-cd6d-40b0-b74c-3c99db04311c /media/hda9	ext3	defaults	0	2

perixx

---

### Post by perixx on 2007-12-20
*bump*
logos34 ?

---

