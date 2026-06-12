---
title: "Ubuntu 13.10 - PCManFM not able to mount USB drives"
date: 2014-02-24
forum: Installation &amp; Upgrades
---

### Post by PeterTaps on 2014-02-24
Folks,

I have built a clean Ubuntu 13.10 system. All it has is Ubuntu core + openbox + pcmanfm.

I start openbox and I run pcmanfm.

Now, when I mount an external USB FAT32 drive, I get an error "Not authorized to perform operation."

This similar setup used to work fine under 12.04. I have my own list of steps that I follow. It has been the same for 12.04 and 13.10.

Something has changed between 12.04 and 13.10.

I can manually "sudo mount" it but I prefer that pcmanfm does it for me as before, that is, creating a directory under /media and mounting the disk.

Wiki on pcmanfm at [https://wiki.archlinux.org/index.php/File_manager_functionality#Password_required_to_access_partitions_and_removable_Media](https://wiki.archlinux.org/index.php/File_manager_functionality#Password_required_to_access_partitions_and_removable_Media) suggest two things:
1. Add the current user to "storage" group. However, there is no group called "storage" on my system.
2. Create a polkit rule in /etc/polkit-1/rules.d/20-enable-unlocking-encrypted.rules following the steps in [https://wiki.archlinux.org/index.php/Polkit#Allow_mounting_a_filesystem_on_a_system_device_for_any_user](https://wiki.archlinux.org/index.php/Polkit#Allow_mounting_a_filesystem_on_a_system_device_for_any_user). However, although I have /etc/polkit-1 directory, I don't have any /etc/polkit-1/rules.d directory.

The system is as clean as it can get. There were no installation errors. Openbox and some other utilities work as expected.

I think the instructions are all outdated.

I am confused. Can someone please guide me on how I can fix this?

Thank you in advance for your help.

Regards,
Peter

---

### Post by sudodus on 2014-02-24
I think that external devices are automounted as

[SIZE=3][FONT=courier new]**/media/<username>/<devicelabel>**[/FONT][/SIZE]

if a label is found.

Maybe you have problems with the permissions of the directory [SIZE=3][FONT=courier new]**/media/<username>**[/FONT][/SIZE] where <username> is your user name.

If you don't worry about access from other users, you can change the permissions to read/write/execute for 'everybody'

```
sudo chmod ugo+rwx /media/<username>
```

You can also change ownership of that directory if you wish, for example

```
sudo chown <username>:root /media/<username>
```

---

### Post by PeterTaps on 2014-02-24
Hi Sudodus,

I have already set permissions to 777 on /media (recursively). Still, it doesn't help.

Regards,
Peter

---

### Post by Dennis N on 2014-02-24
This might help:

Install **policykit-desktop-privileges** if not already installed.

---

### Post by sudodus on 2014-02-25
> **PeterTaps said:**
> Hi Sudodus,

I have already set permissions to 777 on /media (recursively). Still, it doesn't help.

Regards,
Peter

Is udisks or udisk2 installed?

See for example [http://askubuntu.com/questions/339319/why-is-different-the-behavior-of-udisk-and-udisk2-in-xubuntu-for-automounting-us](http://askubuntu.com/questions/339319/why-is-different-the-behavior-of-udisk-and-udisk2-in-xubuntu-for-automounting-us)

---

