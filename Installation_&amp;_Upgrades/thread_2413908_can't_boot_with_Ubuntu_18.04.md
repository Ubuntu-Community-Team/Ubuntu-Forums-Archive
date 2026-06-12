---
title: "can't boot with Ubuntu 18.04"
date: 2019-03-03
forum: Installation &amp; Upgrades
---

### Post by new.ubu.user.lol35 on 2019-03-03
Hi,
I installed Ubuntu 18.04 on my notebook on a hard drive next to Windows 10.
I chose the "install next to Windows" (or so) option.
However, after sucessfully installing it and restarting it, it started directly into my Windows, without ever showing Ubuntu on a boot menu or something.
I tried the Boot Repair tool, and it still didn't work.
The tool gave following output: [http://paste.ubuntu.com/p/zq6YgNWfn9/](http://paste.ubuntu.com/p/zq6YgNWfn9/)

Anyone have some insights or tips?

---

### Post by yancek on 2019-03-03
> I chose the "install next to Windows" (or so) option.]

You should have used the manual installation method which is referred to as "something else" in Ubuntu.  Also would have been a good idea to read the Ubuntu documentation at their site at the link below before beginning.  Might still be helpful to read to get a basic understanding.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Your boot repair output shows you are using something called 'grub2win' which is windows software.  You are not likely to get much help here with that software.
You have your 'grub2win' files on the EFI partition as well as the windows and Ubuntu efi files so if you can get the correct parameters in the boot options in the BIOS, you should be able to boot either/both. Boot repair will not be able to repair anything dealing with windows until you turn off fastboot and hibernation which is indicated in the output.  It won't mount a hibernated filesystem os it won't have access to the windows files.

Boot repairs shows a number of efi entries.  The Ubuntu entry is 0000 so you can use the efibootmgr software to change the settings to move it to first as below from the Ubuntu install media..

```
sudo efibootmgr -o 0000, 0003 
``` 


You can use the entries from efibootmgr output to set the order with the above command.  That is a lower case Letter O in the command.  Enter the codes separated by a comma in the order you want them.  If this succeeds and you can boot Ubuntu, immediately run:

```
sudo update-grub
```

to add entries to the boot menu.  I've never used 'grub2win' so I have no idea if that will complicate or confuse matters.  Do read the link I posted above.

---

### Post by oldfred on 2019-03-03
You show Windows is hibernated, that must be turned off.
       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Is this an Acer? I see mention of Acer and "unknown" as UEFI boot entry.
Acer has a unique requirement of setting "trust" on the Ubuntu entry or the unknown one.
And Acer needs UEFI update from Acer, if not most current version.

       
 One of several with more details on trust:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)

---

### Post by new.ubu.user.lol35 on 2019-03-04
I did a BIOS update and changed the trust settings.
It works now, thank you very much!

---

