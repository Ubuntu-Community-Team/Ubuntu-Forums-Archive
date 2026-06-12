---
title: "moved my swap partition and now i can't hibernate"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by v1nsai on 2009-12-22
I resized my swap partition so i could borrow some space from it, and now my system won't hibernate.  I updated the UUID in /etc/fstab, and it goes into hibernation no problem, but when it comes out it flashes some text on the screen that I don't have time to read, then it does a fresh reboot instead of restoring from hibernation.

Here's some info about my system:

sudo blkid
```
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat"
/dev/sda3: LABEL="/home" UUID="52adbd99-82b5-4976-8eb8-2e91fcfa5f86" TYPE="ext4"
/dev/sda5: UUID="86EE22B6EE229E85" LABEL="Win7" TYPE="ntfs"
/dev/sda6: LABEL="Ubuntu" UUID="5ab69ff7-468c-4736-b535-e5416c2a6562" TYPE="ext4"
/dev/sda7: LABEL="Fedora" UUID="693e59f9-9ad8-4f18-aed3-10ae0694499c" TYPE="ext4"
/dev/sda8: UUID="74172575-e3b7-4be8-b9aa-881f1c667111" TYPE="ext4"
/dev/sda9: LABEL="boot" UUID="fa455150-7cd5-40ed-b4e4-c45614144539" TYPE="ext4"
/dev/sda10: LABEL="Debian" UUID="6b1baabb-6d6a-4ad6-8b86-76b6a95ee317" TYPE="ext4"
/dev/sda11: UUID="c6eca809-d069-4f74-adf2-f63d20306d12" TYPE="swap"
```

my /etc/fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=5ab69ff7-468c-4736-b535-e5416c2a6562 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=52adbd99-82b5-4976-8eb8-2e91fcfa5f86 /home           ext4    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=c6eca809-d069-4f74-adf2-f63d20306d12 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

I can't figure out why it won't work now, it's really making me mad, would really appreciate any input.

---

### Post by buellman on 2009-12-22
If i remember correctly to hibernate your Swap has to be at least the same size as you have RAM. 2GB RAM = min 2GB Swap because the RAM will be written to Swap.

Greets. Buellman

---

### Post by v1nsai on 2009-12-22
lol I was just coming back to add that I've got 4 GB of RAM and my swap is still over 8 GB

Which log file would I need to look in to find the error messages that I'm getting when I try to thaw after hibernating?

---

### Post by phillw on 2009-12-22
I had an issue with swap a while back, when I did some disk 'house-keeping'.

I disabled swap & then re-enabled it to point where it was (and always had been)

That worked for me.

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Has the instructions - You're doing them 'back to front'
i.e. Removing the entries for swap & turning it off (Under 'undoing your chages') Then 
turning it back on.

Should get you up & running.
/edit - just read that FAQ --- An easier way is at the bottom of it -Duh !!!!!

> **Enabling a swap partition**

 In case you do have a swap partition, there are several ways of enabling it. 

[LIST]
[*]Use the following command 
[/LIST]

cat /etc/fstab
[LIST]
[*]Ensure that there is a line link below.  This enables swap on boot. 
[/LIST]

/dev/hda8       none            swap    sw              0       0
[LIST]
[*]Then disable all swap, recreate it, then re-enable it with the following commands. 
[/LIST]

sudo swapoff -a
sudo /sbin/mkswap /dev/hda8
sudo swapon -a 

Regards,

Phill.

---

### Post by buellman on 2009-12-22
> **v1nsai said:**
> Which log file would I need to look in to find the error messages that I'm getting when I try to thaw after hibernating?
If phillw tip does not help you maybe could look in
/var/log/pm-suspend.log
or any other log in /var/log
But it is just a guess.

Greets. Buellman

---

### Post by plucky on 2009-12-22
Also look at ```
cat /etc/initramfs-tools/conf.d/resume
``` and make sure the UUID is the same as your swap partition.


Good Luck

---

### Post by v1nsai on 2009-12-22
Thanks for the suggestions, I followed phill's instructions and nothing changed.  I notice that it changes the UUID every time you run mkswap, so now the UUID of the swap doesn't match /etc/initramfs-tools/conf.d/resume.  Even when I copied and pasted to make them match, I still can't resume.

fstab now looks like this:
```
# / was on /dev/sda7 during installation
UUID=5ab69ff7-468c-4736-b535-e5416c2a6562 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=52adbd99-82b5-4976-8eb8-2e91fcfa5f86 /home           ext4    defaults        0       2
# swap was on /dev/sda10 during installation
UUID=7f41b71d-c370-49ee-87a3-d36af2d12d92  none  swap  sw  0 0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

blkid:
```
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat"
/dev/sda3: LABEL="/home" UUID="52adbd99-82b5-4976-8eb8-2e91fcfa5f86" TYPE="ext4"
/dev/sda5: UUID="86EE22B6EE229E85" LABEL="Win7" TYPE="ntfs"
/dev/sda6: LABEL="Ubuntu" UUID="5ab69ff7-468c-4736-b535-e5416c2a6562" TYPE="ext4"
/dev/sda7: LABEL="Fedora" UUID="693e59f9-9ad8-4f18-aed3-10ae0694499c" TYPE="ext4"
/dev/sda8: UUID="74172575-e3b7-4be8-b9aa-881f1c667111" TYPE="ext4"
/dev/sda9: LABEL="boot" UUID="fa455150-7cd5-40ed-b4e4-c45614144539" TYPE="ext4"
/dev/sda10: LABEL="Debian" UUID="6b1baabb-6d6a-4ad6-8b86-76b6a95ee317" TYPE="ext4"
/dev/sda11: UUID="7f41b71d-c370-49ee-87a3-d36af2d12d92" TYPE="swap"

```

and /etc/initramfs-tools/conf.d/resume:
```
RESUME=UUID=7f41b71d-c370-49ee-87a3-d36af2d12d92

```

---

### Post by v1nsai on 2009-12-23
Bumping because this is pretty urgent, I'm on a laptop and now I can't hibernate and I think it's damaging my filesystem.  Even when I do a normal restart, there is a new message in the startup, it scrolls by too fast to see but it says something about fsck and re-writing the swap signature (is there a log that I can look in for all these startup messages?) and something about waiting for filesystems listed in fstab.

I double checked my other fstab entries against blkid and they seem to be fine, and my separate /home partition gets mounted just fine with my normal filesystem.

I noticed in the suspend log that my system isn't even trying to thaw.  I changed the swap partition Monday night, and before that there are logs of hibernation and thawing, but after Monday night there are normal logs of hibernation, but I see nothing about the system even attempting to thaw.  It seems to just skip the process altogether.

I read through the swapfaq and using the 'free' command I can confirm that my swap partition is on and being used while the system is booted.

I'm still digging, any help appreciated.

---

### Post by v1nsai on 2009-12-23
Solved it!  Added 'resume=/dev/sda8' to the kernel line in GRUB.

I shouldn't have had to do it, but that solved it.  I just successfully re-hibernated.

If anyone can shed some light on this situation it'd be great, this whole thing just doesn't make sense and I don't like the feeling of 'don't touch it it might fall down'.  The whole reason we use Linux is customization and control, right?

---

### Post by felichas on 2009-12-29
I just read this post that may apply:
[http://ubuntuforums.org/showthread.php?t=1316747](http://ubuntuforums.org/showthread.php?t=1316747)

Try running "update-initramfs -u" see if it helps.

---

### Post by v1nsai on 2010-01-03
Success!

I guess now I need to figure out what an initramfs image is, I never would have guessed that had anything to do with it.  Thanks a bunch for reposting that over here, I never found that thread when I was searching.

---

