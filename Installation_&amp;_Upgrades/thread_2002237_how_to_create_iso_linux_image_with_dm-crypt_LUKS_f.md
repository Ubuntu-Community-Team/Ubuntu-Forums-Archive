---
title: "how to create iso linux image with dm-crypt LUKS for multiple hard disks?"
date: 2012-06-12
forum: Installation &amp; Upgrades
---

### Post by newbie15 on 2012-06-12
I wanted to create iso linux image, dm-crypt with LUKS enabled. I wanted to write many hard disks with that ISO created, with different passwords. When i was browsing online regarding this, got the below statement from a website.

[B]CLONING/IMAGING: If you clone or image a LUKS container, you make a copy of the LUKS header and the master key will stay the same! That means that if you distribute an image to several machines, the same master key will be used on all of them, regardless of whether you change the passphrases. Do NOT do this! If you do, a root-user on any of the machines with a mapped (decrypted) container or a passphrase on that machine can decrypt all other copies, breaking security.
[/B]

So would like to know your thoughts on the same, so that disk-encryption is maintained and the task has to be automated.

Thanks in advance...

---

### Post by 3Miro on 2012-06-12
The password is only used to unlock the real key. If you clone all the HDDs then you will end up with the same key and if someone breaks one of those keys, then they will have all the keys.

What kind of machines are you running? Encryption is only useful to protect your data when the machine is off-line. If you let a user sign into an encrypted machine, then encryption will not add any security. I always though of encryption as something person, i.e. you do it only on your personal machine.

---

### Post by newbie15 on 2012-06-12
> **3Miro said:**
> The password is only used to unlock the real key. If you clone all the HDDs then you will end up with the same key and if someone breaks one of those keys, then they will have all the keys.

What kind of machines are you running? Encryption is only useful to protect your data when the machine is off-line. If you let a user sign into an encrypted machine, then encryption will not add any security. I always though of encryption as something person, i.e. you do it only on your personal machine.
ok, if thats the case how can we protect the data once we have logged into the system. 

can you pls explain me, how will de-crypt tie the data to the hardware using device-mapper(i mean whats the basic criteria on which it will get tied to the hardware like mac address or ???)

i'm trying to set up ubuntu machines for our usage in the lab; as i wanted to automate setting up machines, i'm trying to find out the ways in doing the same.

---

### Post by 3Miro on 2012-06-12
> **newbie15 said:**
> ok, if thats the case how can we protect the data once we have logged into the system. 

You have to read about user accounts and user permissions. I am not a system administrator, so others should be able to give more help.

> 
can you pls explain me, how will de-crypt tie the data to the hardware using device-mapper(i mean whats the basic criteria on which it will get tied to the hardware like mac address or ???)


The HDD holds a bunch of ones and zeros, when they are encrypted, they look like complete garbage. The Linux kernel device mapping will create a second virtual HDD so that you read and write files to the virtual HDD and every time something is written/read to/from the virtual HDD, the ones and zeros get encrypted/decrypted on the fly according to the key. The problem is that the key is loaded into the RAM and if one gets root access into the running machine, then they can extract the key.

If someone steals my laptop when the laptop is off, they cannot get the key and they can only see the encrypted garbage data (i.e. it is useless to them). If someone gets access to my laptop when it is running and if they manage to break into the security of the running kernel, then they can get the key and access ALL of my data.

> 
i'm trying to set up ubuntu machines for our usage in the lab; as i wanted to automate setting up machines, i'm trying to find out the ways in doing the same.

If I don't let other people use my laptop, then they cannot get root access. If you are allowing other people to use your lab machines, encryption is pretty much useless. You need to look into making sure nobody can get root access.

Use encryption only if you are worried about someone physically stealing a machine from the lab or physically stealing the HDD. Or if you are worried about someone physically booting a live CD in the lab. Note that if you put encryption on your machines, then you will need to manually enter the password every time the machine reboots. Encryption cannot stop a person who has the HDD password, so you shouldn't give the password to other people.

---

### Post by newbie15 on 2012-06-13
> **3Miro said:**
> You have to read about user accounts and user permissions. I am not a system administrator, so others should be able to give more help.

The HDD holds a bunch of ones and zeros, when they are encrypted, they look like complete garbage. The Linux kernel device mapping will create a second virtual HDD so that you read and write files to the virtual HDD and every time something is written/read to/from the virtual HDD, the ones and zeros get encrypted/decrypted on the fly according to the key. The problem is that the key is loaded into the RAM and if one gets root access into the running machine, then they can extract the key.

If someone steals my laptop when the laptop is off, they cannot get the key and they can only see the encrypted garbage data (i.e. it is useless to them). If someone gets access to my laptop when it is running and if they manage to break into the security of the running kernel, then they can get the key and access ALL of my data.

If I don't let other people use my laptop, then they cannot get root access. If you are allowing other people to use your lab machines, encryption is pretty much useless. You need to look into making sure nobody can get root access.

Use encryption only if you are worried about someone physically stealing a machine from the lab or physically stealing the HDD. Or if you are worried about someone physically booting a live CD in the lab. Note that if you put encryption on your machines, then you will need to manually enter the password every time the machine reboots. Encryption cannot stop a person who has the HDD password, so you shouldn't give the password to other people.


Thanks Miro for your explanation. now i got a overview about the encryption...

I'll check about the admin and other access rights stuff...

Currently i wanted to take care of the physical security of the machine. So here are my road-blocks, so if you can help me in this regard it will be of great help.

1. Without entering the password manually at the boot time is it possible to encrypt the hard-drive? If yes where will the password be?
2. for dm-crypt how will we give a password to create a master password without giving it manually(as i want to automate this task)

---

### Post by 3Miro on 2012-06-13
To start a computer with fully encrypted HDD, you need a way to unlock the key. This is usually done with either a password or a USB drive. Look into doing this over the network, it may be possible. You can also use USB drives, but you should keep good track on them, since having the USB driver is equivalent to having the password.

The way I have seen labs work is to have one common storage server. All of the data is stored on one server and only the admin has physical access to it. The rest of the computers boot on their own and without encryption, but they don't hold any real data. One would boot the regular computer and then the computer would connect to the central storage machine to mount /home. In this fashion, anyone can log into any machine in the lab and have access to all my files. The data is physically secured on the main server and all you need to worry is unauthorized access via the network, and permissions, and buffer overflow and all the other fun stuff.

---

### Post by newbie15 on 2012-06-15
When i was browsing around, i found that McAfee has a similar encrypting tool named "endpoint encryption". There the encryption is done on the fly and it is transparent(user need not enter a pass-phrase every-time when the system boots up). So can you let me know the procedure for doing the same using dm-crypt with LUKS.

---

### Post by 3Miro on 2012-06-15
I guess you can get the key to unlock your HDD by connecting to a remote server, but I don't know how this is done. Someone else may know.

---

