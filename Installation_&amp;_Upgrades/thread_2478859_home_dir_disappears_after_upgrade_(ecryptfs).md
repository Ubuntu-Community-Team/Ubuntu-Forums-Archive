---
title: "home dir disappears after upgrade (ecryptfs)"
date: 2022-09-07
forum: Installation &amp; Upgrades
---

### Post by nader-amadeu on 2022-09-07
Hi,

I had ubuntu 20.04 installed with an encrypted home directory by using ecryptfs.

I upgraded to 22.04 and all files in my home dir disappeared. 

Instead a file named "README" appeared and it told me to execute
`[FONT=Courier New]ecryptfs-mount-private[/FONT]`

I did it and my home dir reappeared. 

However when i restart the system everything is lost again, meaning, I have to rerun that command to
obtain my data.

How do i get automatic mounting of my home dir?
Thanks a lot in advance!

PS: The home dir encryption was done using this tutorial:
[https://www.linuxuprising.com/2018/04/how-to-encrypt-home-folder-in-ubuntu.html](https://www.linuxuprising.com/2018/04/how-to-encrypt-home-folder-in-ubuntu.html)

---

### Post by TheFu on 2022-09-07
encryptfs has been deprecated since 2018.   
[https://discourse.ubuntu.com/t/security-ecryptfs/11886](https://discourse.ubuntu.com/t/security-ecryptfs/11886)
[https://www.reddit.com/r/sysadmin/comments/a7osl9/ubuntu_deprecating_ecryptfs_whats_the_new_approach/](https://www.reddit.com/r/sysadmin/comments/a7osl9/ubuntu_deprecating_ecryptfs_whats_the_new_approach/)

I bet there was a clear announcement in the release notes too.

Deprecated means it won't work at some point in the future.  Welcome to the future.

You might be able to gain access to the encryptfs data manually, assuming it wasn't deleted.  I think it is in ~/.private/, but since I only used it a few days, don't trust me.  It had already been deprecated when I first used it for a number of important security and performance reasons, in favor of using LUKs.  

Worst case, just restore from the backups you made before choosing to allow the upgrade.  They backup all the files you don't want to lose, do the upgrade, and restore those files.

If you didn't make a pre-release upgrade backup set, it will be harder, but I suspect booting from a 20.04 in "Try Ubuntu" mode will allow manual access, with some magic commands, to the encryptfs files ... again, backup all the files you don't want to lose, take them to the 22.04 system and restore.

Probably not what you wanted to hear, but it shouldn't be any surprise.

---

### Post by nader-amadeu on 2022-09-08
access to the data is not a problem. I just wanted to go back to normality, home dir automatically mounted at login.
I will give up home encryption on 20.04. Thanks!

---

### Post by yancek on 2022-09-08
>  home dir automatically mounted at login 

Check the /etc/fstab file.  If you have a separate partition for /home you should have an entry for it in this file.  Countless sites online explaining this.

---

### Post by TheFu on 2022-09-08
> **nader-amadeu said:**
> access to the data is not a problem. I just wanted to go back to normality, home dir automatically mounted at login.
I will give up home encryption on 20.04. Thanks!

While not at end-user login, you can setup LUKS encryption for a separate partition which can contain multiple advanced volumes, like a logical volume for just HOME directories.  Alas, if the system is booted and someone enters the LUKS decryption passphrase/key/challenge, then it appears like normal, decrypted, file systems for any users on the system to access, based on normal Unix permissions.

Encryption only makes data safe when it isn't mounted anyway. That applies to all encryption methods, so be certain to power off the system, not just hibernate or standby, when data security is needed.  I power off whenever I'm moving between buildings, but use standby when at home, sometimes for weeks.

---

