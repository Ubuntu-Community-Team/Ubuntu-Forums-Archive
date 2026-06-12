---
title: "Grub2 rescue after repartitioning"
date: 2013-05-08
forum: Installation &amp; Upgrades
---

### Post by John_Rose1 on 2013-05-08
Hello,
 

 I am running Ubuntu 10.04 Lucid Lynx and Windows XP in GRUB2 based double boot on a Dell Vostro notebook.
 

 For historical reasons I had two separate NTFS data partitions:
      /dev/sda1         fat16         DellUtility    39MB
      /dev/sda2         ntfs           XP                 24GB     boot
      /dev/sda4         ntfs           data-1            22GB
      /dev/sda3         extended                       421GB
                /dev/sda5    ntfs           data-2           395GB

                /dev/sda6    ext3          /home               8GB

                /dev/sda7    ext3          /                      13GB

                /dev/sda8    linux-swap                        4GB

 

 In preparation for updating to 13.04 (for another 3 years) I wanted to put all my data in a single primary partition. So I backed up all my data and deleted  /dev/sda5, but the partition names changed as follows:
 /dev/sda1         fat16         DellUtility    39MB
      /dev/sda2         ntfs           XP                 24GB     boot
      /dev/sda4         ntfs           data-1            22GB
      /dev/sda3         extended                       421GB
                unallocated                                      395GB

                /dev/sda5    ext3          /home               8GB

                /dev/sda6    ext3          /                      13GB

                /dev/sda7    linux-swap                        4GB

 

 My idea had been to decrease the size of the extended partition to hold only the Ubuntu files, increase the data-1 primary partition according, and copy in the data which had been in data-2. [I guess I should have decreased to the smallest possible size without deleting it, but now I can't get back to the original configuration, when I create a new logical partition in the unallocated space it is called /dev/sda8.]

 

 When booting failed with this new configuration, I modified fstab to use the right device names for mounting the Ubuntu files (/dev/sda5 instead of /dev/sda6, etc.), but I still can't boot: no GRUB menu, just "Error : unknown file system. Grub rescue>".
 

 I tried the Boot Repair disk, no help, what should I do? Thanks and best regards, John

---

### Post by fantab on 2013-05-08
13.04 is not LTS and is supported for only 9 months. You must consider 12.04 LTS which is supported until 2017. The next LTS will be 14.04. 

Since your DATA is all backed up. I suggest you delete all the partitions after /dev/sda2.
Then make /dev/sda3 NTFS 
/dev/sda4 Extended... and so on.

Instead of resolving the grub issue just install 12.04 LTS and carry on. By the way, "Boot Repair" should have fixed your grub issue. Try again, perhaps you missed something.

my two cents...

EDIT: if you have to save data from /home then boot Ubuntu LiveCD/USB and rescue data.

---

### Post by John_Rose1 on 2013-05-08
Thanks fantab,

I loaded boot-repair from the net while on LiveCD and it worked fine, fixed the grub problem (but was complicated to find boot-repair, had to change the respository releative to the instructions because LiveCD was old - hard to find this on the web). Not sure what the problem was with the boot-repair CD (title of iso file was 32 bits, but when booted it said 64 bits, in any case I could not get it to provide the user interface).

I will now upgrade to 12.04 (strange that the original 3-year sequence was not followed for 10.04) and get back to the forum if further problem. I understand that this procedure will enable me to keep my applications, whereas with clean 12.04 install I would have to reinstall them (please correct if I am wrong).

I really appreciate your help, John

---

### Post by darkod on 2013-05-08
The 3 year period was for the support length, not how many years you have to wait for the new LTS. The LTS comes out every 2 years, at least for now. The LTS support is longer than 2 years on purpose, so you don't need to upgrade to the next LTS right away after it comes out, you can wait for the main problems to be sorted out while still having support for your previous LTS. In most cases you should wait for the so called first point release, like 12.04.1 which comes out approx 6 months after the main release. In fact, if upgrading from the previous LTS the option will not be shown until the .1 comes out. This is also on purpose because they sort out most urgent problems in the .1 so it's nest to install a new LTS only after the .1 is out.

Now with 12.04 they enlarged the support perios to 5 years, while the next LTS is still planned as 14.04 as far as I know.

If you look closely in your partition layout after you deleted the ntfs data partition, your root partition is actually sda6, not sda5. And the /home partition is sda5. You needed to change both entries in fstab. You can also use UUIDs in fstab which helps in cases like this, moving disks and partitions around, since fstab mounts the partitions by their UUID which doesn't change unless they are formatted, and not by their partition number.

Upgrading will keep your applications but it can also create issues, smaller or bigger. You can give it a shot if you want to. Just make a full backup first. And try 12.04 live cd to see how live mode runds and whether it shows some issues with your hardware.

Clean install is always best, most of your config will be in your Home folder anyway, and you can keep /home because it's separate partition.

But it's your choice. If you really think it will take you long time to reconfigure the new install, try with upgrade.

---

### Post by oldfred on 2013-05-08
I would still make a list of installed apps, just in case. Your backup of /home will have all your user settings, but unless you have a list of apps you have to remember what you installed. I include a new list of apps as part of my rsync backup.

       from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)
From old install
dpkg --get-selections > ~/my-packages

If concerned about 12.04.2, you can install in another 10 to 25GB / (root) to test or convert to?

Just released:
      
 LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

