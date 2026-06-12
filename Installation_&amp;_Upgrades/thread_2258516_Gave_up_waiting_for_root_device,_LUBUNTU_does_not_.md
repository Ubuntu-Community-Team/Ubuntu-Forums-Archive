---
title: "Gave up waiting for root device, LUBUNTU does not boot..."
date: 2014-12-28
forum: Installation &amp; Upgrades
---

### Post by xxleopoldxxx on 2014-12-28
Hey Guys, saw my mistake posting in german

Please help me with the following problem: 
After failing to install Linux mint (or better getting the drivers for my graphic card running) i decided to give Lubuntu a try. I installed everything. Then i tried to boot the system and this message came:

"Gave up waiting for root device Common problems

  -Boot args (cat(proc/cmdline)
  -check rootdialog
  -check root
  Missing modules (Cat/proc/modules; ls/dev)
  Alert /dev/disk/by-uuid/bb1c03ad-6cb4-43f6-804f-d7561865a5db   ...  doesnt not exist dropping to a shell"

And a busy-box opened.
Typing "exit" or setting the boot mode to IDE from AHCI didnt work. 
So i reinstalled Lubuntu but it is still not working.

I cant give you further information about my system because i deleted Windows with the installation of Linux mint.
Please give me a hint how i can solve this problem, i really would love to have Lubuntu running on my Laptop.

Sorry btw for the earlier post in german, was a bit confused....

---

### Post by yancek on 2014-12-28
> Alert /dev/disk/by-uuid/bb1c03ad-6cb4-43f6-804f-d7561865a5db   ...  doesnt not exist dropping to a shell"

The above message indicates it is looking for a specific partition with that UUID which doesn't exist.  Could be a number of reasons.  Use the Lubuntu or Mint medium and go to the site below and get bootrepair.  When you get it, just run the "Create Bootinfo Summary" and don't try to repair.  Post that output here.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by xxleopoldxxx on 2014-12-28
I tried installing that program before... The terminal shows me the message
[B]Website: [https://launchpad.net/boot-repair](https://launchpad.net/boot-repair)
 More info: [https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair](https://launchpad.net/~yannubuntu/+archive/ubuntu/boot-repair)
Press [ENTER] to continue or ctrl-c to cancel adding it
sudo apt-get update
gpg: keyring `/tmp/tmpaqqhgyik/secring.gpg' created
gpg: keyring `/tmp/tmpaqqhgyik/pubring.gpg' created
gpg: requesting key 60D8DA0B from hkp server keyserver.ubuntu.com
gpg: /tmp/tmpaqqhgyik/trustdb.gpg: trustdb created
gpg: key 60D8DA0B: public key "Launchpad PPA for YannUbuntu" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)
OK
lubuntu@lubuntu:~$ sudo apt-get install -y boot-repair && (boot-repair &)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package boot-repair

[/B]So I am not able to install this program... 

**EDIT**
reloaded the synaptic manager.. now it is working, will show the results in the next answer

---

### Post by xxleopoldxxx on 2014-12-28
Boot repair:

[http://paste.ubuntu.com/9639139/]("http://paste.ubuntu.com/9636418/")

Thank you in advance for reading through that text... Karma will be on your side for quite a time ;D

---

### Post by xxleopoldxxx on 2014-12-29
Solved the problem by myself xD
I changed the advanced settings in bootr-repair to install the latest version of Grub and to purge it before, now it is working \\:D/

---

### Post by yancek on 2014-12-29
In your initial post, you show this error:

> Alert /dev/disk/by-uuid/bb1c03ad-6cb4-43f6-804f-d7561865a5db   ...  doesnt not exist dropping to a shell"


The bootloader is looking for its boot files which in your case (according to the bootrepair script) is on sda5 and the UUID is not the one shown in the message above but rather:

> 20fa5b23-1d20-43f6-9611-cfad70991c71

The entries in the boot menu, the grub.cfg file shown in your output have the correct UUID number so it should boot.  The only thing I can think of that might be a problem is that you did not install Grub to the MBR with the Lubuntu install.  If you look at the suggested repair in the bootrepair script, it indiates it would reinstall grub of sda5 (Lubuntu) to the mbr.  You might try that.

---

