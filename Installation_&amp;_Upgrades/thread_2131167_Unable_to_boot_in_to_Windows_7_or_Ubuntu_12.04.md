---
title: "Unable to boot in to Windows 7 or Ubuntu 12.04"
date: 2013-03-31
forum: Installation &amp; Upgrades
---

### Post by sepulphuric on 2013-03-31
Hello all!


I installed Ubuntu 12.04 on my windows 7 hp pavillion dm4 computer with WUBI a few months ago. 
My W7 U12.04 dual boot worked perfectly until I started running low on memory in my ubuntu install and tried to add space to my recovery partion in windows with a partition manager (completely dumb I know, I learned after the fact that a wubi install works with a virtual partion). Idid that since it was similar in size to my wubi partition. After the fact I tried booting back in to ubuntu to recieve the message

ERROR: NO SUCH DEVICE: long string of characters. 

After that happened I booted back in to ubuntu with a bootable USB and attempted to use the reccomended repair for the *boot repair tool*
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

This only worsened my situation as my computer now stops on the screen where I used to choose my OS in dual boot and tells me that it can no longer boot into windows, with no options for either OS and reccomending I use a windows 7 install cd which didn't come with my computer when I purchased it. "darn you Craigslist!". :(

please help! I'm a college student and I really need my computer running asap!



PC SPECS: hp pavillion dm4 laptop 
memory: 3.7 GB
processor: Intel Core i5 CPU M 460@ 2.53Ghz times 4
integrated graphics

I'm currently using a bootable usb with Ubuntu 12.04 64-bit.

I'm a super newb and really need your help!

Thanks to all!

---

### Post by José Serra on 2013-03-31
You can't boot from your recovery partition?

---

### Post by sepulphuric on 2013-03-31
I'll try that right now....

---

### Post by sepulphuric on 2013-03-31
Alright Mr. Jose, 
I was unable to to use system recovery.
 An attempt to use it brought me to the the the same message in the WIndows boot manager that I talked about before. Which is exactly this:

Windows failed to start. A recent hardware or software change might be the cause. To fix the problem:

1. Insert your Windows installation disk and restart your computer.
2. Choose language setting and click next.
3. Click "Repair your computer."

Status: 0xce000000f
Info:The boot selection failed because a required device is inaccessible.

---

### Post by José Serra on 2013-04-01
When you booted from usb, could you see your drive and check if the partitions were alright, I mean that you could read your OS files.

---

### Post by José Serra on 2013-04-01
Have you seen this: [http://ubuntuforums.org/showthread.php?t=2131165](http://ubuntuforums.org/showthread.php?t=2131165)

---

### Post by oldfred on 2013-04-01
You can post the link to BootInfo report from Boot-Repair. But Boot-Repair does not really fix Window issues, it can add a Windows boot loader or some other minor things, but most Windows fixes need a Windows repairCD or Flash drive.
Do you have a Windows repairCd?

If you have a friend with either 32bit or 64bit to match yours, you can make a repairCd or flash drive.
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

---

### Post by sepulphuric on 2013-04-08
Fred and Jose!

I can't expreuss how grateful I am for the both of you..
I must admit though, that after a day or two of beng out of a computer, I decided I couldn't wait
and hastily performed a fresh install of ubuntu Precise.
I should've been patient, but after using Ubuntu, Windows just irks me straight to heck!

Either way, I sincerely appreciate all the help that was given! :)

Hopefully one day I'll be able to aid newbies out with techy things like you two gentlemen. 

God Bless! ):P

---

