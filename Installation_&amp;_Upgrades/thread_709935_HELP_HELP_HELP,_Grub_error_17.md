---
title: "HELP HELP HELP, Grub error 17"
date: 2008-02-27
forum: Installation &amp; Upgrades
---

### Post by hchanman on 2008-02-27
I recently installed Ubuntu 7.04. Then I got my Kubuntu disk so I installed Kubuntu 7.10. In the process of doing this, I deleted the swap and Ubuntu partition along with a partition of 2.24mb size. During the install, the grub install failed. Now I keep getting grub error 17 when I boot up. 

I can't get to my Vista OS. I need my Vista access back. This is on a Compaq F572US. If someone knows how to reinstall the Windows boot loader, please tell me so I can. Currently I have no OS accessible. I can't get to Vista because of Grub ERROR 17. I can't get Kubuntu installed right because of Grub. And I'm trying Ubuntu again, but am unsure how it will work. What I really want to do is wipe my Ubuntu install and go back to my Windows stuff so I can start over. (Windows boot loader too.) If someone knows what to do please help me. If more details are needed, ask. 

But I need [SIZE="7"]HELP[/SIZE]

---

### Post by bazzawill on 2008-02-27
I'm not sure how to reinstate the windows boot loader but you should be able to reinstall ubuntu or just grub to give you access to windows I would suggest if you do reinstall ubuntu do so with a 50mb /boot partitions which should always give you access to windows if an install fails

---

### Post by hchanman on 2008-02-28
huh? I'm a bit of a noob, so you say when I reinstall Ubunt to create a 50mb /boot partition. IF yes, then where, before the Linux partition, after it, before the Windows partition, or after that?

I tried to reinstall Ubuntu. That failed, it wouldn't install. I tried Kubuntu. That failed too. Nothing will install. 

And the grub error changed, now it's giving me Error 15.

---

### Post by Partyboi2 on 2008-02-28
try using [super grub]("http://supergrub.forjamari.linex.org/") to restore windows mbr and here is more info on [grub 15]("http://users.bigpond.net.au/hermanzone/p15.htm#15")

---

### Post by hchanman on 2008-02-28
Ok, i succesfully reinstalled kubuntu, but now when i boot up, i only get grub command line.

anybody know how to use grub command line to boot into windows

my windows paritition is /dev/sda1, the kubuntu partition is /dev/sda2

---

### Post by froy02 on 2008-02-28
From grub enter the following commands:

root (hd0,0)
makeactive
chainloader +1
boot

That shouild boot window$.

---

### Post by hchanman on 2008-02-28
OK, I'll try that, but my root drive is (hd0,1) not (hd0,0) so I should use that instead right?

I got root from command:

find /boot/grub/stage1

---

### Post by froy02 on 2008-02-28
What grub returned is the location of your stage1 file which is your linux installation.  Post the output of 'sudo fdisk -l' and we'll be able to help you better.  From your posts I only assumed that Vista was installed before linux.

---

