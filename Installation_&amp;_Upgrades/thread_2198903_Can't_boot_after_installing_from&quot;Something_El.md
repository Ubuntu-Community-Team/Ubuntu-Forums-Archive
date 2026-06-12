---
title: "Can't boot after installing from&quot;Something Else&quot; option"
date: 2014-01-11
forum: Installation &amp; Upgrades
---

### Post by antsco on 2014-01-11
Hi
ok, this is somewhat the continuation of [this solved post]("http://ubuntuforums.org/showthread.php?t=2198724") (for those who followed it)

I reinstalled ubuntu using the third option available where I can state in which partition to install the OS.
Windows 7 is in a 100 Gb partition at the beginning of the hard disk, which only had 25% of space occupancy (plus other some 190 Gb of unused disk space at the end), so I 
shrinked this partition in order to make room for ubuntu near the beginning of the HD and left it with some 55 GB and a partition for ubuntu was left with more than 40Gb. (I did this because of some problems that my old laptop has in finding hard disk areas beyond 137 Gb)
I defined this partition as ext4 (but I am not sure if this was the correct choice since there were many other possibilities)
Then the partition manager asked me to define an intermediate area that could function as a swap area, so I put apart some 100Mb
(even though I am not sure if this is enough) and told the partition manager to define this ext4 partition as "/"  as the installation point

After this the installation ensued which was successful

Upon reboot though the following error message appears: [COLOR=#ff0000]error: no such partition[/COLOR] 

Evidently something has gone wrong.
I run boot-repair and the report that I got is the following: [http://paste.ubuntu.com/6732020/](http://paste.ubuntu.com/6732020/)
Any help would be appreciated
Antonio

---

### Post by grahammechanical on 2014-01-11
> [COLOR=#000000]and told the partition manager to define this ext4 partition as "/" as the installation point[/COLOR]

Did you do what I think you have done? The partition that we give a mount of / is the partition into which the installer puts Ubuntu or tries to. Did you tell the installer to install Ubuntu into a 100MB partition or am I misunderstanding you?

Ext4 is the default file system type for Ubuntu. So, that choice was correct. It is customary for the swap partition to be twice the size of RAM otherwise there will be problems with resuming from hibernation and suspension. We do not format the swap partition as Ext4. The installer will take care of setting up the assigned partition as swap.

Ubuntu can be installed in a partition size between 6GB - 10GB but it leaves not so much space for adding applications and data. 40GB is more than enough for Ubuntu and it is that 40GB partition that should be Ext4 and with a mount point of /. Just tell the installer which partition is for swap. There is no need to do anything else for setting up a swap partition. Oh, if we re-install (which you may have to do) the installer will identify an existing swap partition and use that without us needing to tell it where the swap partition is. Just make sure it is big enough.

Regards.

---

### Post by oldfred on 2014-01-11
Install looks normal.
If you look at line 337, all the boot files are within the first 100GB.

Your UUID looks correct.

Some also have issues with search line in boot stanza. Or even using UUID which is preferred but some find the old device designation works.

You can try manual booting if you can get to grub comment line. If not we can try editing the file we are not supposed to ever edit. Any update to grub will undo edit, so it is only temporary.

Add # to make it a comment to the line shown in pastebin as line 245 or the search line. You may have to mount from liveCD and edit it from there. It may also be write protected.

 #Normally we do not directly edit grub.cfg. Edit from live-CD/DVD/USB.
mount /dev/sda7 /mnt
gksu gedit /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg

Some also are able to boot with Supergrub which by-passes the regular grub. Then you can edit or update files from inside your install which is a bit easier.

       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by antsco on 2014-01-11
Hi
well, after the error message, I get a "grub rescue", prompt is it this that you are referring to
for the manual booting, where to write the commands you suggest?
Thanks
Antonio

---

### Post by oldfred on 2014-01-11
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)


 See post #10 by drs305 
[http://ubuntuforums.org/showthread.php?t=1916698](http://ubuntuforums.org/showthread.php?t=1916698)
grub rescue:
ls # Do you see (hd0), (hd0,7) ? If so, run the next command. If you see (hd0,7), use that instead of (hd0,7) in the next command.
configfile (hd0,7)/boot/grub/grub.cfg

If that does not work try these:

   set prefix=(hd0,7)/boot/grub
set root=(hd0,7)
linux (hd0,7)/vmlinuz root=/dev/sda7 ro
initrd (hd0,7)/initrd.img
boot

---

### Post by antsco on 2014-01-12
I followed instructions in the links  1 & 2 but didn't work
Also tried to use the commands you suggest but the 'linux' command (also used by drs305) is not recognized by grub rescue

When I do 'ls' I can see (hd0) but not (hd0,7)

Also in the line:

> If you see (hd0,7), use that instead of (hd0,7) in the next command. is this what you really meant?

Best regards
Antonio

---

### Post by oldfred on 2014-01-12
It totally depends on what the ls command says. 
But I thought your install was in (hd0,7) or sda7.

---

### Post by antsco on 2014-01-13
well my 'ls' command says (after doing the manipulations in the provided links)

(hd0) (hd0,msdos5) (hd0, msdos4) (hd0, msdos2) (hd0, msdos1) (hd1) (hd1,msdos2) (hd1,msdos1)

that doesn't sound right, does it?
Cheers
Antonio

---

### Post by oldfred on 2014-01-13
I don not know why the ls command is not showing it, so there is something wrong that Boot-Repair is not seeing.

Try Supergrub. Link in post #3.

---

### Post by antsco on 2014-01-14
Hi
ok, right now I am giving up...it is taking too long to sort this out and I need my laptop to work.
So just thanks a lot for all the suggetions you gave me. I hope to have more time in the near future and try to reinstall ubuntu in my laptop
Best regards,
Antonio

---

