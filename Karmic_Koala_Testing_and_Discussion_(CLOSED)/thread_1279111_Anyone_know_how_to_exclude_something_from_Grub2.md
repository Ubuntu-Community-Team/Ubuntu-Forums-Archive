---
title: "Anyone know how to exclude something from Grub2?"
date: 2009-09-30
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Rallg on 2009-09-30
Using current Karmic, with Grub2 bootloader, Ubuntu:

My hard drive has several operating systems. One of them is a Windows "restore" partition that I do NOT want Grub2 to list. If someone chooses that one from the Grub menu, it will be a disaster.

Is there a way I can direct Grub2 to omit one or more of the OS it finds? Unlike old Grub, it is not even obvious which file to edit for immediate relief. I'd also like the exclusion to apply whenever rub2 updates.

---

### Post by drs305 on 2009-09-30
One way would be to build a custom menu which includes your Windows OS, and then disable the 30_os-prober file in /etc/grub.d (remove the executable bit). This would prevent Grub2 from trying to import any non-linux OS's.

This guide discusses the file structure of Grub 2:
[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by Rallg on 2009-09-30
Thanks. I'll have a look. It wasn't obvious what to do within /etc/grub.d/ due to the executable codes.

Grub2 may be great for the informed, but it isn't as obvious as the good old menu.lst was, for the rest of us.

UPDATE: OK, the advice worked. Here is what I did:

1. Made backup copies of /etc/grub.d/30_os-prober and /etc/grub.d/30_otheros.

2. Hashed out the existing other OS listed within 30_otheros.

3. Remove all from within 30_os-prober (that is, saved it as a blank file).

4. In Terminal, sudo update-grub.

5. Reboot, and now only the choices related to Karmic are shown.

Understand that I have another way to get to my other OSes on this machine, since I arrive at Karmic's Grub2 by first going through the Windows XP bootloader. Those of you who use only Grub2 will have to manually add your other OSes (probably just don't hash out whatever is already in 30_otheros).

---

### Post by drs305 on 2009-09-30
Rallg,

In the guide's "Custom User Entry" section there is an example of a 40_custom Windows entry. All you would need to do is change the "set root" entry to point to your Windows partition and change the UUID. Don't forget that Grub 2 starts counting drives from 0 but partitions from 1.

Make sure 40_custom (or whatever you name it) is executable and that 30_os-prober is not. You can do it with the following command:
```

sudo chmod -x /etc/grub.d/30_os-prober && sudo chmod +x /etc/grub.d/40_custom

```

---

### Post by ranch hand on 2009-09-30
> **Rallg said:**
> Thanks. I'll have a look. It wasn't obvious what to do within /etc/grub.d/ due to the executable codes.

Grub2 may be great for the informed, but it isn't as obvious as the good old menu.lst was, for the rest of us.

UPDATE: OK, the advice worked. Here is what I did:

1. Made backup copies of /etc/grub.d/30_os-prober and /etc/grub.d/30_otheros.

2. Hashed out the existing other OS listed within 30_otheros.

3. Remove all from within 30_os-prober (that is, saved it as a blank file).

4. In Terminal, sudo update-grub.

5. Reboot, and now only the choices related to Karmic are shown.

Understand that I have another way to get to my other OSes on this machine, since I arrive at Karmic's Grub2 by first going through the Windows XP bootloader. Those of you who use only Grub2 will have to manually add your other OSes (probably just don't hash out whatever is already in 30_otheros).
It would have been better, and easier, to simply change the permissions on the scripts in grub.d that you did not want to function so that they were not executable.

---

### Post by seamuso on 2009-09-30
This is my custom to boot xp on my netbook ..


```
#! /bin/sh -e

prefix=/usr
exec_prefix=${prefix}
libdir=${exec_prefix}/lib
. ${libdir}/grub/grub-mkconfig_lib
echo "Adding Windows" >&2
cat << EOF
menuentry "Windows XP" {
EOF
save_default_entry | sed -e "s/^/\t/"

cat << EOF
       insmod ntfs
       set root=(hd0,1)
       search --no-floppy --fs-uuid --set a2f48f73f48f490d
       drivemap -s (hd0) \${root}
       chainloader +1
}
```

keep 30_os-prober executable, run update-grub .. you need some if that it's going to generate into /boot/grub/grub.cfg

Look at your grub.cfg file and get the uuid, root=(x,x), drivemap ..

create a new file, call it 20_load-xp (for example), copy the code from above, change the uuid to match yours, etc. chmod -x 30_os-prober .. chmod +x 20_load-xp and run update-grub so it rewrites your grub.cfg

---

