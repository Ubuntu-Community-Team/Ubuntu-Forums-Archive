---
title: "clonezilla uuid grub"
date: 2013-12-07
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2013-12-07
say I have three partititions with ubuntu
sda7 10.04
sda9 12.04
sda12 xxxx

I created an image of sda7 and saved it out to exthd.
Now I want to test this image of sda7.

So I place it on partition sda12 (sizing is fine) using clonezilla again, correct?
Now, when I boot up, what will grub do? What will the menu present?
Could I boot to sda9 and run grub update or something?
I am trying not to manually edit any grub files, "scary"... but if need be np.

---

### Post by Bashing-om on 2013-12-07
pjmlmas; Hi !

Welp, there is no way to avoid editing , at the very least, "/etc/fstab"

Version 10.04 that was on device sda7 had a UUID set for sda7; clonzilla did it's thing, and on sda12 is the UUID of sda7.
What you need to do now to boot 10.04 on sda12 is to find the UUID of sda12:
```

sudo blkid

```
Using the info from "blkid" uuid ->sda12, edit "etc/fstab" and replace the UUIDs to that of sda12.
```

sudo cp /etc/fstab /etc/fstab-orig
gksudo gedit /etc/fstab

```
Makes a backup of "/etc/fstab" and the next opens the file in the text editor "gedit" with admin authority. Make the change and save the file !

Now, you need to update the boot code,. If you have made no changes to grub's config files. this should suffice:
Boot up your primary operating system and "update" grub:
```

sudo update-grub

```
Boot each of your installs - from grub's menu,to  make sure grub works to boot as desired.
Else: run "update-grub" in each install, and 
once more boot into the primary OS and (re-)install grub -only if problems still exist -
```

sudo grub-install /dev/sda

``` as you are booting a single hard drive with all OSs installed on that single hard drive the boot code is to be installed to the MBR of that drive.

It really is 
[INDENT][INDENT]a piece of cake
[/INDENT][/INDENT]

---

### Post by pjmlmas on 2013-12-08
> What you need to do now to boot 10.04 on sda12 is to find the UUID of sda12:
Will the MBR grub find sda12 to boot into at that stage? I though boot to either sda7 or sda9 and change sda12 from there?

---

### Post by Bashing-om on 2013-12-08
pjmlmas; Hey,

Once you are certain the UUIDs are straight then for grub, you have one primary booting operating system controlling what operating system is to be booted.
Bios is going to hand off to the boot code located at the boot sector of the sda drive and a boot menu is displayed. From this menu you choose which version (and kernel) you want to boot. I have as my primary version 13.04 installed onto the first partitions of the 1st hard drive - 1st entry on my boot menu. Each time I have major grub changes I must "update" grub from within each of my installs, and finally from the primary install (re-)install grub to the MBR of sda and then all is good.

The command "sudo update-grub" will find all instance of the operating systems, IF you have not disabled os-prober, and do all the configuring, as the final step - if required - is to "install grub" to /dev/sda in the event that the grub boot menu is not displayed. 

I must do that last step from my primary operating system for grub to display/act properly. Be aware I have 4 installs on this box and my grub is indeed customized.

As to editing  (/etc/fstab) files on sda12; one can mount that partition from either of the installs, or from the liveDVD and effect any required changes. This "fstab" == File System TABle and controls what is mounted when the operating system starts up. UUID's are the most reliable method of identification.

If you desire confirmation of what "/etc/fstab" should look like; post back - between code tags - the output of terminal codes:
Mount the partition for editing:
```

sudo mkdir /mnt/work
sudo mount /dev/sda12 /mnt/work
sudo blkid
cat /mnt/work/etc/fstab

```
 

[INDENT][INDENT]hope this does help
[/INDENT][/INDENT]

---

### Post by pjmlmas on 2013-12-22
sda9 
less /boot/grub/grub.cfg

        search --no-floppy --fs-uuid --set=root 2xxx
        linux /boot/vmlinuz-3.2.0-37-generic root=UUID=9xxx

sudo update-grub
sudo grub-install ***did not run yet
They are not matching, so the boot menu, even though it looks ok, boots to old partition. I know I could manually change ...but  should I run different command instead.

---

### Post by Bashing-om on 2013-12-22
pjmlmas; Hello,

All that I expect is required is to make sure that the UUIDs are correct in /etc/fstab control file;
AND
make sure your /etc/grub.d/30_os-prober is enabled, that it's permissions look like this:
"-rwxr-xr-x  1 root root 11531 Oct 23 15:44 30_os-prober"
from;
```

ls -la /etc/grub.d/30_os-prober

```
Then run:
```

sudo update-grub

```
from the primary booting 'buntu operating system. "os-prober" will pick up all operating systems installed and update the grub menu.

Should be all there is to it.
[INDENT][INDENT]my regards
[/INDENT][/INDENT]

---

### Post by pjmlmas on 2013-12-22
**from sda9**

-rwxr-xr-x 1 root root 7603 Jul 19 19:32 /etc/grub.d/30_os-prober
*mounted* restored partiton etc/fstab appears correct

sudo grub-mkconfig  generating incorrect uuid as well.
sudo blkid is _correct_.

---

### Post by Bashing-om on 2013-12-22
pjmlmas; Humm,

Let's take a look at what is driving "grub-mkconfig" ;
```

ls -la /etc/grub.d

```
see if we can come up with a reason why.

[INDENT][INDENT]it is a process
[/INDENT][/INDENT]

---

### Post by pjmlmas on 2013-12-22
Will sudo grub-install ignore any exisiting grub cfg files. I have not run this command yet on sda9...but want to...any harm

> grub2-mkconfig will create a new configuration based on the currently running system, what is found in /boot, what is set in /etc/default/grub, and the customizable scripts in /etc/grub.d/ . A new configuration file is created with: 

> grub2-install will install the bootloader - usually in the MBR, in free unpartioned space, and as files in /boot. The bootloader is installed with something like: 

---

### Post by oldfred on 2013-12-23
I think os-prober copies grub.cfg entries. So if both installs still have grub.cfg with same UUID, an update-grub from your working system will not find the new install or will not find it correctly.

I think the only fix is to edit the file we are told to never edit or directly edit grub.cfg. You only have to update the first boot stanza with new UUID. Once booted into that install then from inside it you run the sudo update-grub and everything then will be updated.

You also may be able to manually boot from grub command line or just edit your grub boot stanza to the new UUID to boot once. Select version that is original install on sda7, then use e on grub and change UUIDs to correct ones for sda12. You also can change to use device instead of UUID.

Something like this may work as a manual boot using device instead of UUID. Uses link in / that links to the newest kernel installed in /boot.

 set prefix=(hd0,12)/boot/grub
set root=(hd0,12)
linux (hd0,12)/vmlinuz root=/dev/sda12 ro
initrd (hd0,12)/initrd.img
boot

---

### Post by Bashing-om on 2013-12-23
pjmlmas; Hey,
+10 ^ oldfred's advisement .

[INDENT][INDENT]it's all in the process
[/INDENT][/INDENT]

---

### Post by pjmlmas on 2013-12-23
The grub.cfg on the restored partition is what is causing this problem. I suppose os-loader is looking at this and picking up bad information. I base this on the fact that I moved the grub.cfg on the restored partion out to home directory. grub-mkconfig now works (sda#) is being used instead of uuid. 

	search --no-floppy --fs-uuid --set=root **UUIDOK!**
	linux /boot/vmlinuz **SDA#OK**!

I move it back
	search --no-floppy --fs-uuid --set=root **UUIDOK!**
	linux /boot/vmlinuz **UUIDBAD**!

I am going to move the grub.cfg out on **restoredpartition**.
 Execute grub-mkconfig on **sda9**.
Hopefully, be able to boot to **restoredpartition**.
Than run sudo update-grub from **restoredpartition**.

This seem reasonable?

---

### Post by pjmlmas on 2013-12-24
This worked. Partition successfully cloned and installed to new partition.
summary. When installing a cloned partition to different partition, move out/backup original grub.cfg on **cloned** partition after install. Then use update-grub to generate new grub.cfg on cloned partition.
This is due to "feature" of os-prober that uses a partitions existing grub.cfg for information.

---

