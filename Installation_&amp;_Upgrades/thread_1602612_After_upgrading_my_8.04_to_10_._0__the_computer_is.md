---
title: "After upgrading my 8.04 to 10 . 0  the computer is dead"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by Gins on 2010-10-21
[B]

I have been using Ubuntu 8.04 for more than 2 years. It asked me to upgrade. I obliged and upgraded.

It took about 2 hours. I had the patience and responded to the questions such as keeping the old 'menu.lst ' file.

Now it doesn't come to the screen due to an error in mounting file system.

The following is the message:[/B]
.................................................................................................................................................
init: ureadhead main process (2618) terminated with status 5

libudev: udev_monitor_new_from_netlink : error getting  socket : Invalid argument

mountall : mountall .c :3204: Assertion failed in main: udev_monitor = udev_monitor_new_from_netlink (udev , &#8220; udev &#8220;)

init: mountall main process (2621) killed by ABRT signal

General error mounting file system.

A maintenance shell will now be  started.

CONTROL &#8211; D will terminate this shell and reboot the system.

Give root password for maintenance ( or type Control -D to continue )

........................................................................................................................................
[COLOR="Red"]I gave  the root password and ran the command ' fsck ' too.

It worked.

I reboot the computer several times. I am getting the same above message.

So my Ubuntu doesn't work.
Please help me.

Control -D command reboot the computer.[/COLOR]

 [COLOR="Red"]I didn't run any command like ' sudo apt-get upgrade '.[/COLOR]
[COLOR="Blue"]
There was a message to upgrade the system. I just accept and sat in front of the computer for about 2 hours until the process completed.
[/COLOR]
I have a 64 bit computer so it is very likely I ran 64 bit version of the Desktop version of Ubuntu. It is not Kubuntu. It is just Ubuntu.

[COLOR="Red"][ I wrote the command ' exit ' pressed enter. Then the computer rebooted.
The words 'exit' didn't appear on the screen. In other words when I wrote something it is not visible.
[/COLOR]

---

### Post by jerrrys on 2010-10-21
i did the 8o4 to 10o4 dance.  first time i tried i made it all the way to 910 before i crashed and burned.  second time i made it to 10o4 without problem.  so in my opinion this sort of upgrade is a roll of the dice and better off with a fresh install. which i ended up doing, just didn't like the mix of old and new.  after all, we only got to do it every two years...

---

### Post by Gins on 2010-10-22
Thanks Jerrys

I can't do the upgrade process as you suggested.
I run several operating systems using GRUB.
It will be a problem with MBR and the  'menu.lst' file.

I know the problem. It is in the /etc/fstab file.

In the fstab file, you will find the following items.

(file system) , (mount point) , (type) , (options) , (dump) and (pass).

[COLOR="Blue"]The relevant partition is /dev/sdb3

I wrote the command 'cat fstab ' and got the following results.[/COLOR]

UUID=c5fb4ab5-6767-44e8-b89a-6383b6e2bad  
 
 /   ext3  realtime,error s=remount-ro   0  1


I think the mount point is / .(This means the root.)

I think 'ext3' is the file type.

I think dump is 0.

I think pass is 1.

I think options is 'realtime,errors=remount -ro'.
[COLOR="Red"]
Could you please post your fstab file contents?[/COLOR]

---

### Post by jerrrys on 2010-10-22
sorry, can't help. im out of town and on windows.  but i hear you when it comes to grub.  i run 6 hdd and its easy to screw the pooch.  maybe **supergrub** could help out.

---

### Post by Gins on 2010-10-24
[COLOR="Red"]
I badly need help to solve the problem.
[/COLOR]
I tried in vain to edit the fstab file.

The fault lies in the following line:
[B]realtime,error s=remount-ro
[/B]
I tried all the tricks to insert the following line.

**defaults,errors=remount-ro,noatime**
[COLOR="Red"]
It insists the file  is a read-only one.
[/COLOR]


I wrote the following  command to find out the version number.

lsb_release  -a

It says 10.04.

.................................................................

I downloaded the CD to install. 

The installation process worked fine.
[COLOR="Blue"]
It will erase entire hard drive. It doesn't give me a chance to install on 'sdb3' partition.
[/COLOR]
It says I will lose everything on 'sdb' hard drive. I gave it up. I don't want to lose my Mandriva and Windows resides on the 'sdb' drive.
[COLOR="Green"]
I am writing to you using Mandriva.

Please help me.[/COLOR]

---

