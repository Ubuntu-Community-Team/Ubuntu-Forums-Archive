---
title: "Unable to login to 12.10 as admin user"
date: 2012-10-27
forum: Installation &amp; Upgrades
---

### Post by Robbyx on 2012-10-27
First I did an update and could not login as robins.

I have just done a clean install, reformating the root but not the seperate /home partition and still my password will not allow me to login. 

I did a groupadd admin

I have tried changing the password via subdoers and adding my name to a new line as robins ALL=ALL(ALL:ALL)ALL

I have tried to go in under Ctrl Alt F1 from guest and loging in as robins but it says fopen: permission denied. I try encryptfs-maint-private and it says encrypted private directory not properly setup.

When doing the install I am not given the chance to untick the encrypting of my home directory. The tick can not be unticked. 

I just tried a software update and was asked for the robins password from within the guest login. The robins password was accepted and the software updates proceeded without a hitch. I rebooted and was unable to login as robins.

What more can I do? At present I am accessing ubuntu as a guest not requiring a password.

---

### Post by Robbyx on 2012-10-28
I hope someone has the experience to resolve my login problem and that they will comment soon.

I recall this all started because when I was doing the upgrade from 12.04 to 12.10 I wal required to encrypt the home directory by moving my mouse. I do not recall a seperate password being supplied by the encrypting process.

Robin

---

### Post by Robbyx on 2012-10-28
I found what I thought would help at:
[http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html](http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html)

followed the advice:

[I]ubuntu@ubuntu:~$ sudo ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/media/ubuntu/1t_home/robins/.Private].
Try to recover this directory? [Y/n]: y
INFO: Found your wrapped-passphrase
Do you know your LOGIN passphrase? [Y/n] n
INFO: To recover this directory, you MUST have your original MOUNT passphrase.
INFO: When you first setup your encrypted private directory, you were told to record
INFO: your MOUNT passphrase.
INFO: It should be 32 characters long, consisting of [0-9] and [a-f].

Enter your MOUNT passphrase: 
INFO: Success!  Private data mounted read-only at [/tmp/ecryptfs.iwTBCB2q].
ubuntu@ubuntu:~$ 
[/I]

I can not find the output in the /tmp directory! So I have not been able to recover the /home data

I also tried this with the same passphrase as used above:

> ubuntu@ubuntu:~$ sudo ecryptfs-recover-private
INFO: Searching for encrypted private directories (this might take a while)...
INFO: Found [/media/ubuntu/1t_home/robins/.Private].
Try to recover this directory? [Y/n]: y
INFO: Found your wrapped-passphrase
Do you know your LOGIN passphrase? [Y/n] y
INFO: Enter your LOGIN passphrase...
Passphrase: 
Inserted auth tok with sig [fd3f7bcb740bd80c] into the user session keyring
INFO: Success!  Private data mounted read-only at [/tmp/ecryptfs.UPJCsIdS].
ubuntu@ubuntu:~$ 

Again nothing extra appears in /tmp/

Any ideas as to what to do next?

Robin

---

### Post by Robbyx on 2012-10-28
I have found the correct tmp directory. I will post if I can not retrieve the contents of the decrypted file.

---

### Post by Robbyx on 2012-10-28
I thought you might like a report but this is what happens on the first line of your usual instructions. I was runinng it from the live cd:

[I]guest-daLBba@robins-EP35-DS3L:~$ sudo apt-get install python-software-properties 
sudo: unable to change to sudoers gid: Operation not permitted
guest-daLBba@robins-EP35-DS3L:~$ 
[/I]

Robin

---

### Post by darkod on 2012-10-28
When you did the new installation:
1. Did you specify during the installation the /home partition and the mount point /home?
2. Did you use the same username and password as in the original install?

I don't use encryption but from what I read now if you reuse the /home partition and use the same password for the user, it should work.

Also, you don't need to upgrade to every version that is released, only upgrade if you really need to move to the new version. 12.04 is LTS and is supported 5 years.

Doing upgrade after upgrade you are just risking your data, especially with encrypted /home partition.

---

### Post by Robbyx on 2012-10-30
In the end Canonical helped me out by reverting me to 12.04. I have had to reinstall my programs but i have also used the old home settings. 

They suggested that initially i should set Ub up in a single directory rather than have the home else where.

---

