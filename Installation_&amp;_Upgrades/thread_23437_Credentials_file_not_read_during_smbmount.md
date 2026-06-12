---
title: "Credentials file not read during smbmount"
date: 2005-04-01
forum: Installation &amp; Upgrades
---

### Post by rotorwash on 2005-04-01
I am trying to mount some shares upon boot. If I specify the username and password options in the mount command on the command line **or**  in fstab the shares mount fine. If I use the credentials option I get prompted for a password. I am trying to avoid passwords in the fstab file. My credentials file permission is 600 and is  of the format:
username = username
password = password

My fstab entry:
//192.168.0.233/share  /mnt/share  smbfs  credentials=/etc/credential  0  0

My cmdline:
smbmount //192.168.0.233/share /mnt/share -o credentials=/etc/credential

I also see these messages in syslog:
smbfs: mount_data version 1684370019 is not supported 
Am I fighting a buggy smbmount cmd or doing something wrong?

---

### Post by tgs on 2005-04-06
Hi i dont know if you found a fix for this yet, 

but i had the same problem and i noticed that smbfs isnt installed by defualt, so if you do a "sudo apt-get install smbfs" then it should work,

Cheers
tgs

---

### Post by rotorwash on 2005-04-07
[QUOTE=tgs]Hi i dont know if you found a fix for this yet, 

but i had the same problem and i noticed that smbfs isnt installed by defualt, so if you do a "sudo apt-get install smbfs" then it should work,

Cheers
tgs[/QUOTE]
Yes, I found that out when I tried to mount the share. But this is not the problem. Smbfs is installed.

---

### Post by toothpaste on 2005-04-09
I had the same problem but it disappeared once I installed the smbfs package.

---

### Post by rotorwash on 2005-04-28
The problem went away with hoary.

---

