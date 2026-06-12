---
title: "[SOLVED] mounting partition trouble"
date: 2008-10-08
forum: Installation &amp; Upgrades
---

### Post by mickeyd1965 on 2008-10-08
Hi,
I have just created a partition and have received the following error message.

 cannot create directory `/old': File exists


can anyone please help.

mickeyd1965

---

### Post by Elfy on 2008-10-08
Not sure why partition creation would try to create a directory?

Can you give a bit more detail/information on what you'vew done and when the error occurs please.

---

### Post by mickeyd1965 on 2008-10-08
i typed in.

sudo mkdir /old
sudo mount -t ext3 /dev/sda1 /old
sudo mkdir /new
sudo mount -t ext3 /dev/sda3 /new

it came back with

lance@lance-desktop:~$ sudo mkdir /old
sudo: unable to resolve host lance-desktop
[sudo] password for lance: 

i typed in my password, then

mkdir: cannot create directory `/old': File exists
lance@lance-desktop:~$

---

### Post by vanadium on 2008-10-08
If the directory which is to be the mount point already exists, the mount command is sufficient to mount the partition. Check what is mounted using the "mount" command.

---

### Post by caljohnsmith on 2008-10-08
> **mickeyd1965 said:**
> i typed in.

sudo mkdir /old
sudo mount -t ext3 /dev/sda1 /old
sudo mkdir /new
sudo mount -t ext3 /dev/sda3 /new

it came back with

lance@lance-desktop:~$ sudo mkdir /old
[COLOR="Blue"]sudo: unable to resolve host lance-desktop[/COLOR]
[sudo] password for lance: 

i typed in my password, then

mkdir: cannot create directory `/old': File exists
lance@lance-desktop:~$
I just wanted to point out that the above error usually is the result of your computer's host name being different in /etc/hosts and /etc/hostname. I would check those to files, and if the host name for your computer doesn't exactly agree in those two files, you'll need to change one of them or you will run into problems using sudo. You can check them with:
```
cat /etc/hosts
cat /etc/hostname
```
In the hosts file, look for the line that begins with "127.0.1.1", and the host name on that line should exactly match the host name in the hostname file. If they don't, you can modify either of those files with:
```
gksudo gedit /etc/<file>
```
And replace <file> with either "hosts" or "hostname". If your host names in those files are different, most likely you won't be able to edit them with the above command because gksudo will fail. So if the above fails, let me know and we can work from there.

---

### Post by mickeyd1965 on 2008-10-09
[solved] Hi,
Before you all replied, i tried to fix it myself and the screen went totally blank. I had to re-install ubuntu and in the process managed to not only install the OS but the partitions actually worked. I thank you all for your kind replies.

mickeyd1965:)

---

