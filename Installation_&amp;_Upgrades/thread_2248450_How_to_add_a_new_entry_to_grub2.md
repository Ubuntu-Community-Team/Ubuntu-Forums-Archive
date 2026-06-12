---
title: "How to add a new entry to grub2 ?"
date: 2014-10-14
forum: Installation &amp; Upgrades
---

### Post by luca-dgh on 2014-10-14
Hi to all!
I found out of many threads, but I didn't find anything related with my question.
I have Ubuntu 12.04 working, I have no real problems but some little things that are not working because the kernel is 3.2.0 or other system software that is not recent. I red that many people has successfully done an automatic upgrade, so I wish to try it, but not on my real installation.

My linux box is like th¡s:
sda1 = /boot
sda2 = /      (root 12.04)
sda3 = raw partition
sda4 = logical
sda5 = /home
sda... / sdb... / sdc... more partitions with personal data.

So I cloned sda2 on sda3 and I edited fstab to adapt it to the new partitions, but now I have a little problem: How can I insert the new partition in the grub2 start menu? (with the old grub that was very easy).
Remember that the two installation share the same kernel 3.2.0-70, so in the boot partition there are file like vmlinuz / system map / config and so on, that will be used form both installations until I do the upgrade.

I tried ```
sudo update-grub
``` but (obviously) nothing changed.

Somebody can help me?

---

### Post by grahammechanical on 2014-10-15
update-grub runs os-prober which detects operating systems and in your case it found Linux kernels in sda1 the /boot partition and nowhere else.

If you did not have a separate /home partition the kernels would be in the /boot folder on / partition. That might have worked but I doubt it. Each partition is given a Universally Unique Identifier (UUID). A combination of alpha- numeric characters unique to that partition. When you clone a partition you keep the same UUID (me thinnks). So, Grub would have two partitions with the same UUID and who knows which one it would choose to load.

Why not create a 20GB partition and install 12.04 into it and giving it sda5 as its /home partition? Then you have a standby OS in case the upgrade fails in some way.

I have several installs of Ubuntu and its flavours. I have all my data on a separate data partition that I can access from any installation. I am running the development versions which sometimes break. So, I keep one installation as a standby OS. It used to be 12.04 and now it is 14.04. I never mess with my standby Ubuntu. It is there in case an installation I am testing breaks and then I can use the standby Ubuntu to carry on with my daily work.

You can find the main Grub file at /boot/grub/grub.cfg. But do not try to edit it as you will do what you are trying to avoid doing and that is break the OS. Or its loading. There other ways to make changes to the Grub menu. I do not think what you want to do will work because Grub will still be reading grub.cfg on sda1 and loading the kernels on sda1.

Do not forget that any upgrade, whether it is 12.04 to 12.04.1 to 12.04.5 or to 14.04.1, the kernels will also be upgraded. And that will cause os-prober to run and it will detect the new kernels which will be compatible with the upgraded Ubuntu but not the cloned Ubuntu. This especially applies to proprietary video drivers.

Regards.

---

### Post by oldfred on 2014-10-15
I would only share /home if you have another copy of the same version of Ubuntu. If upgrading one install then I prefer separate /home or my preference but a bit more work to configure, the separate data partition for all folders like Music, Video, Documents etc.

I do not recommend /boot for most Desktop installs. You do need regular maintenance to make sure /boot does not fill up. When just the boot folder inside / (root) it is not quite as critical as most installs have more room. But you still should regularly house clean old kernels.

I am sure you have duplicate UUID and may boot into one partition one time and the other the next time and can get things out of sync quickly.

Post this 
       sudo blkid -c /dev/null -o list

      Change UUID see also man pages:
uuidgen
sudo tune2fs /dev/sdaX -U numbergeneratedbyuuidgen
or:
sudo tune2fs -U random /dev/sdaX
if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid
Then you have to update fstab and reinstall grub for the second partition.
Do not use same /boot either for both installs as that will still get out of sync. Comment out the entry for /boot in fstab in second install.

If in Boot-Repair you the full uninstall and reinstall of grub in your second install and leave /boot partition unchecked it will download new grub and the newest kernel into your /boot folder. That may be the easiest way to reconfigure to not have separate /boot in second install.

---

### Post by luca-dgh on 2014-10-15
1) First of all I apologize, I improperly said > I cloned sda2 on sda3 actually I made a copy of 12.04 root with the command ```
sudo cp -ax input output
``` so I have an exact copy of the content of sda2 partition in the sda3 partition, but I didn't touch UUIDs.

2) My 12.04 installation is higly customized so I wish to make a try with the upgrade in order to preserve my customization.

3) I have /home separated from the root (/home is in sda5) and /boot is a 1 GB partition, I made the choice to separate /boot some years ago when I was used to install every ubuntu release, but I only had 2 partitions to make that (small disk) so every 6 months I installed the new release and, when everything was ok, I cleaned-up the old one to make space to the new release. In this case was useful to have the boot partition separated.

4) I wouldn't touch the OS that is working now, many things are working with it at my house (wife job, son school, telephones, printers, windows lan, etc.), so I wouldn't like to touch /boot partition. With the old grub was so easy to add a line to the cfg file with the partition or the UUID address, so I wonder if there is a trick that permits to do the same in grub2. I understand that to share the same kernel may be a problem when the upgrade starts, but I think that would be enough to use a previous version of kernel to separate the jobs in /boot and/or in grub cfg.

Thank you for your patience.

---

### Post by yancek on 2014-10-15
The file in Grub2 which is comparable to the Grub Legacy menu.lst/grub.conf is /boot/grub/grub.cfg.  If you open that file it tells you that you should not modify it directly and also explains why, that if you add anything to it and run update-grub your manual change will not be save.  What you should do is put the new menuentry for sda3 in /etc/grub.d/40_custom file on the base system (sda2) modified to point to sda3, save the change and run sudo update-grub from that system.  Should give you an entry for the sda3 Ubuntu if the entry is correct, correct uuid or /dev.

---

### Post by luca-dgh on 2014-10-15
Thanks a lot **yancek**, it was a little tricky to find the correct syntax, but now I can boot my second partition.

---

### Post by yancek on 2014-10-15
I think the simplest way to do that would be to take a known working entry and copy it to the 40_custom file on the new partition.  Most of the entry won't need to be change in a case where it is the same OS and filesystem type.  Usually only the /dev partition (hd0, msdos1 as an example) and the uuid.

---

