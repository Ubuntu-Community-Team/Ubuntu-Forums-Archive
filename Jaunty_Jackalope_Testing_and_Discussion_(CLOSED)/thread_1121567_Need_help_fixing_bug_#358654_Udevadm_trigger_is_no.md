---
title: "Need help fixing bug #358654 Udevadm trigger is not permitted while udev is unconfigu"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Quift on 2009-04-10
Hi all,

I've been having some problems since yesterdays upgrade. Ubuntu refuses to start for me, This seems to be a known bug, but I'm to much of a newb to fix this myself. I have now booted from a linux mint live cd, and some of the proposed fixes does not seem to work.

mint ~ # chroot /mnt/target
root@mint:/# dpkg --confgure -a
dpkg: unknown option --confgure
root@mint:/# mount /dev/sda8 /mnt/target
mount: you must specify the filesystem type
root@mint:/# mount /dev/sda9 /mnt/target
mount: you must specify the filesystem type
root@mint:/# 


Also, I have never used chroot, or done anything like this before, @ie, mounting and working from the live cd. any help is really appreciated. if a solution involving mounting /home and moving it to external storage, followed by reinstall is the simplest I might have to do that. also, this is an ubuntu only lap/top, no other fix operating system, and I can only play with live/cd that have native support for mobile broadband. 

Thank you for your time.
Quift

---

### Post by Quift on 2009-04-10
ok, I now have access to the filesystem on the computer, Is there a graphical way to proceed?

I don't mind using the cli, but I don't ge twhat I'm supposed to be doing now?

---

### Post by iponeverything on 2009-04-10
> dpkg --confgure -a

I see one problem. 

--configure not --confgure

---

### Post by Polygon on 2009-04-10
in today's updates i think this was fixed, as i remember seeing something about udevadm in the release notes.

---

### Post by Quift on 2009-04-10
Eh, I still need to et this to work. I spelled configure correcntly and rebooted, but that didn't help. Now I'm trying to remount my harddrive again, but the name that i'm sure worked the last time (hda1) doesn't work.

So nom I;m even more lost. could someone please try to explain what the actual problem is_ and what is supposed to be done to rectify it, cause I don't even now that, which given that I have troubles mounting the harddrive from a live-cd is a cruel indication of my noob skillz.

Thanks for all the help.

---

### Post by Claus7 on 2009-04-11
Hello,

I had exactly the same problem with the updates I made today:
Alert :/dev/disk/by-uuid/ad3f494c-59d5-4dfc-8eld-dbfcalb62194 does not exist

udevadm ...

it drops to bash shell with initramfs in front. I booted from restricted kernel...

Any ideas?

Regards!

---

### Post by nebajoth on 2009-04-11
same problem here, with a different uuid.

---

### Post by Claus7 on 2009-04-11
Hello, 

this seems to be a known bug as the thread starter posted, yet it is supposed to be solved.
[https://bugs.launchpad.net/ubuntu/+source/dkms/+bug/320200](https://bugs.launchpad.net/ubuntu/+source/dkms/+bug/320200)

Someone is supposed to execute the commands:
```
dkms remove -m MODULE -v VERSION --all
/etc/init.d/dkms_autoinstaller start
```

yet since I do not get a descent command prompt, where am I supposed to run this commands? I have booted from linux kernel 2.6.28-3-rt and executed this command. It went ok, I rebooted, yet the generic kernel refuses to work. Even from the ubuntu cd I cannot figure out what am I supposed to do.

I see that other people are facing the same too. Even if there are some updates, how is someone supposed to triger them without command line? From rt kernel maybe?

Regards!

---

### Post by Claus7 on 2009-04-13
Hello,

I was fed up and I reinstalled. Everything is back to normal now. This problem, as those who faced it are pretty aware, is really very tricky because it drops you to a shell with more or less 20 commands at one's disposal. If someone finds a solution, this is good news. I would suggest avoid it at all cost.
edit: I chose ext4 and up to now is working nicely. Trying to put ext4 only the / partion didn't work.

Regards!

---

