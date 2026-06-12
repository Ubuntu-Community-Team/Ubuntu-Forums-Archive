---
title: "How do I get the installer to just install?"
date: 2017-09-22
forum: Installation &amp; Upgrades
---

### Post by r_widell on 2017-09-22
OK, so upgrading from Kubuntu 14.04LTS to 16.04LTS is guaranteed not to work, and I have to do a clean install. I get that.
How do I get the 64-bit installer to do the install without mucking around with my LVM disk partitioning?

I have 3 HD, 1-1TB & 2-2TB. One of the 2TB drives has a 1GB ext4 partition that's mounted as /boot.
The remainder of that drive, as well as all of the other drives are in a single volume group (which has expanded significantly over time).

There are a total of 10 logical volumes in this volume group, all of the non-LSB volumes are mounted under /home.
All of my non-removeable media is mounted by LABEL, so each of the logical volumes, including the swap partition has a label. 

I opened a bash console and manually formatted root, /tmp, /opt, /srv, /boot& /var. I also did a mkswap on the swap LV.
Unfortunately, the installer announces that it's going to format the swap partition and my entire volume group, even though I selected "manual" for the partitioning method.

How do I get the installer to leave the drives alone and just do the install. I can handle (and expect)  warning messages about problems due to installing to partitions that it didn't format.

It takes a long time to restore 3.5 TB of data after some well-meaning but clueless script wipes it out.

Thanks,
ron

---

### Post by ajgreeny on 2017-09-22
I can not specifically help with LVM but in all situations where you wish to re-use particular partitions **you MUST use "Something Else"** at the partitioning stage, where you can then select the partitions, ask for particular mountpoints, choose partition type, and select or deselect the Format button.

I am aware that you can not use gparted, for example, to work on LVM partitioning and it may be the same for the Ubuntu installation process, in which case I will have to leave others to deal with this and tell you how to proceed..

---

### Post by r_widell on 2017-09-22
> **ajgreeny said:**
> I can not specifically help with LVM but in all situations where you wish to re-use particular partitions **you MUST use "Something Else"** at the partitioning stage, where you can then select the partitions, ask for particular mountpoints, choose partition type, and select or deselect the Format button. 


Perhaps I wasn't clear enough.
When I wrote that I opened a bash prompt and manually formatted the various logical volumes (partitions), the tools I used were ```
mkswap -L VOLUME_LABEL
``` for the swap LV and 
```
mkfs.ext4 -jL VOLUME_LABEL 
``` for the other logical volumes.

In the graphical window of the installer, I explicitly ensured that none of the partitions were to be formatted (I assigned mount points, but made sure that the ```
format
``` box was left unchecked.

The only logical button choices at that time are "back" and "install". I chose "install". After clicking through the warning that all sorts of bad things would happen if I didn't format at least the root partition, I was then faced with the announcement that it was going to format the swap partition **AND the *VOLUME_GROUP_NAME* volume group. **The only choices were "back" & "OK". I chose "back", and then closed the window. When it asked me if I wanted to abort the installation, I clicked "yes".

I believe that lvm2 is not the critical point here. I only included the description for completeness. The critical point is that the scripts behind the installer insist on formatting ***something,*** even when the user tells it not to do so.

What I want to know is how to bypass that ***"feature", ***other than installing a different distro.

Thanks,
ron

---

### Post by ajgreeny on 2017-09-22
Thanks for the extra info which always helps us answer queries.

Sorry, but as I said, I can not help with LVM as it is not something I have ever used or felt the need to use.
Wait for other users who may offer a lot more help than I can.

---

### Post by Dennis N on 2017-09-22
I prepare the LV before installing. Use the something else option to install, and continue to the partitioning screen. 

Unless you are encrypting, you only need to specify one LV as root in the partitioning screen. Select it, press change, and give / as mount point. I format a new LV in the pre-install preparation, so don't need to check format box here, but you could if it's being reused. Separate boot or other separate partitions are not necessary. Make a swap partition or LV, but not necessary if one already exists. The system's formatting of swap is normal. Newest Ubuntu does not need swap partition - it makes a swap file if no swap partition is present or created.

---

### Post by deadflowr on 2017-09-22
Doesn't the mkfs.ext4 format the volume?

---

### Post by r_widell on 2017-09-22
> **Dennis N said:**
> I prepare the LV before installing. Use the something else option to install, and continue to the partitioning screen. 

So where, exactly, is this mythical "something else" option?

Unlike the 32-bit Kubuntu 16.04.2 LTS media, the 64-bit Kubuntu 16.04.3 LTS media doesn't pause mid-boot and ask whether you want to proceed to the desktop or go directly to installation. It proceeds directly to the desktop, where you see the icon to install Kubuntu 16.04.3 LTS. At no point in the installation process before where it informs me that it's going to format my entire VG is there anything that looks remotely like a "something else" option.


I have reviewed all of the media boot options, in addition to checking the media for errors on the target machine. The media is OK and there are no boot options that look anything like "something else".

To recap: I already have the drives prepared as I want them. I just want the installer to do the install without mucking around with the partition tables on  my drives.

Thanks,
ron

---

### Post by SeijiSensei on 2017-09-22
The "something else" option appears after you run the installer.  Double-click the installer icon on the KDE desktop.  You'll get to the stage where it wants to format the drives.  You can choose "something else" there.  Whether or not it will recognize your LVM partitions, I don't know.  With current disk sizes, I haven't needed to use LVM for at least a decade, and I never use encryption.

---

### Post by ajgreeny on 2017-09-22
After double clicking the "Install Kubuntu" icon on the desktop it should get to a partitioning page offering to install to the whole disk, install alongside the current OS, or, at the bottom, the option that you have not seen, ie "Something Else".

It is certainly there as I installed Kubuntu 16.04 64bit many months ago and used it.

---

### Post by deadflowr on 2017-09-22
Is it "Something Else" or "Manual" in Kubuntu's installer?
Not that it would matter they equal the same thing.

+1 to being inside the actual installation program and not a boot option.

---

### Post by r_widell on 2017-09-22
deadflowr:

    > Re: How do I get the installer to just install?
    Is it "Something Else" or "Manual" in Kubuntu's installer?
    Not that it would matter they equal the same thing.

It's "manual".
When I get to the partitioning portion of the installer, I have 4 options:
[LIST]
[*]Guided - Use entire disk 
[*]Guided - use entire disk and set up LVM 
[*]Guided - use entire disk ans set up encrypted LVM  (followed by a couple of fields to define the decryption password) 
[*]Manual 
[/LIST]

It may have said "something else" in an older version of the installer, I don't know.
I know that I'm using the current and recommended version of the Kubuntu !6.04 installation media, and clearly stated in my first post that I was using "Manual" mode for partitioning.
I also know that the installer script can't deal with a drive with a physical partition formatted as ext4 with the remainder of the drive allocated as a physical volume in the same volume group as the other drives. The before/after graphic when the first "Guided" button is selected shows before as a 1GB ext4 partition and the remainder of the 2 TB as "unknown". The other 2 drives, which are completely dedicated to the same VG show up as LVM formatted drives.

This behavior is unique to the installer. the pvs, vgs and lvs commands at a bash prompt (as root) show exactly what I expect to see for those drives.

The other problem is that there's no way to get it to NOT use a swap partition if it exists, as the "do not use" option doesn't exist for the LV formatted as swap.

It's beginning to look like 16.04 isn't worth the hassle of dealing with a badly broken installer. I'll either re-install 14.04, or switch to a different distro.

ron

---

### Post by r_widell on 2017-09-22
OK. The installer is well and truly broken.

I formatted the swap LV as ext4, so the installer wouldn't automatically use it, and then marked it as "do not use".
Then I tried to install again.

This time I got warnings about not having a swap partition, not formatting the root partition, and that existing data on the root partition would be wiped out.
I don't care, go for it.

Well, it pretended like it was installing something somewhere and finally got to the point where it said that it was almost done, it was just saving some package information (or something along those lines).
30 minutes later, the "saving" process was still at 0%, so I opened up a bash console, found where in the /tmp directory the root partition was mounted, and did an ls -l of that directory. The only thing that was there was the lost+found directory from the mkfs command. Moreover, I found it VERY curious the none of the partitions i had specified (/boot, /tmp, /var, /opt, /srv, /home) were mounted under root.

So I rebooted the machine and when it got back up to the desktop I mounted my root partition under /mnt and did another ls -l. the only thing there is the lost+found directory.

I haven't decided yet whether I'll try it again with an older image, or just install a different distro.
In any event, don't waste your time trying to install Kubuntu to an LVM system using the 16.04.3 image. It's a colossal waste of time.

ron

---

### Post by r_widell on 2017-09-25
After numerous experiments this weekend, I finally figured out why it fails.
The installer will only allow / (root), /home and swap logical volumes as mount points.
It also allows a separate physical partition (e.g. sda1) to be mounted as /boot.
Any attempt to use a different mount point (e.g. /var, /opt, etc) for a logical volume will cause the installation to fail.

The ubuntu-desktop image shares the same flaw. Presumably, all of the graphical installers share this flaw.

The ubuntu-server image does NOT have this flaw. It works as expected.

---

