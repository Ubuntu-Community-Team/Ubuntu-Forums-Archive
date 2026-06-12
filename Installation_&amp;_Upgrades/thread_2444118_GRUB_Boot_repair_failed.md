---
title: "GRUB Boot repair failed"
date: 2020-05-25
forum: Installation &amp; Upgrades
---

### Post by nickinem on 2020-05-25
Hey guys
1. I have installed GRUB with 2 OS Ubuntu Bionic and Windows 10. Everything was working fine for a while with booting to different OS
2. I have moved Windows up to be the first. Still was working
3. I have reinstalled Windows 10 and GRUB disappeared. I heard about that and was ready to (I supposed)
4. I tried to repair GRUB using [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) and attempt has failed.
5. Here is the report [http://paste.ubuntu.com/p/SF2szj9NWB/](http://paste.ubuntu.com/p/SF2szj9NWB/). 

Can anybody, please, help with that?

---

### Post by yancek on 2020-05-25
> I have reinstalled Windows 10 and GRUB disappeared.  

Yes, expected behavior with windows.  You did a lot more than try to repair Grub, see line 174 of boot repair.  sda1 and sda2 are your windows partitions so don't do anything with them.  sda3 and sda11 appear to be at least partial installs of Ubuntu.  What if anything do you have on the other partitions (sda4-sda10)?  When trying to do this repair, boot repair needs to be connected to the internet (line 38) and it's not.  You might try connecting to the internet and running boot repair again.  You don't seem to have a grub.cfg file on any partition which is a major problem.  What are you able to boot now?

---

### Post by oldfred on 2020-05-25
Boot-Repair will not fix your install.
It works fine with standard installs with / (root) or even if you also have a /boot. 
But when you start creating partitions for every system folder, it does not mount them. So then the reinstall of grub will not work.

You need to use chroot & mount all or most of your system partitions. Not really sure which are absolutely needed as only a few with servers use that configuration in the long time ago. 

I think all the examples of chroot I have only show mount of / and maybe /boot. But you also need to mount in similar fashion all your partitions.
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

You may want to think about not having all the extra system partitions to manage. And now those with servers and extra partitions use LVM to make it easier to resize. Even /boot used to be required with LVM, but is not. Maybe with encryption.
Standard desktop Ubuntu now uses just / (root). Swap is now a file.
Many like to add either /home or data partition(s).

---

### Post by nickinem on 2021-05-24
I know it has been for a while. Thank you guys for your time and help. Everything was a bit too complicated so I ended up reformatting disk space to single volume, mount root "/" to it, and reinstalling ubuntu there.

---

