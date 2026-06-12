---
title: "Ubuntu 13.04 is NOT installing in Asus Zenbook Prime UX31A via USB"
date: 2013-05-30
forum: Installation &amp; Upgrades
---

### Post by HeyItsMoses on 2013-05-30
Hello everyone

I spent about 4 hours last night trying to Install Ubuntu 13.04 64-bit flavor on my zenbook, but I couldn't get it to work. 

I plugged in the usb stick inside, and downloaded 13.04 and pendrivelinux on my zenbook and did all the steps to get the iso in the usb. 

I restarted the zenbook and pressed esc to enter the boot mode. 

[[IMG]http://i1131.photobucket.com/albums/m552/moseskazaryan/20130530_001200_zps111dbe03.jpg[/IMG]](http://s1131.photobucket.com/user/moseskazaryan/media/20130530_001200_zps111dbe03.jpg.html)

I selected the usb drive and clicked enter, and got this screen.

[[IMG]http://i1131.photobucket.com/albums/m552/moseskazaryan/20130529_233547_zps4c629ec1.jpg[/IMG]]("http://s1131.photobucket.com/user/moseskazaryan/media/20130529_233547_zps4c629ec1.jpg.html")

From here, when selecting Try Ubuntu or Install Ubuntu, I just get a black screen. 

I tried selecting it and pressing e (on both Try and Install), and I end up here

[[IMG]http://i1131.photobucket.com/albums/m552/moseskazaryan/20130529_234516_zpsafb08dd3.jpg[/IMG][/URL[URL=http://s1131.photobucket.com/user/moseskazaryan/media/20130530_001723_zps6c8c29a0.jpg.html][IMG]http://i1131.photobucket.com/albums/m552/moseskazaryan/20130530_001723_zps6c8c29a0.jpg[/IMG]](http://s1131.photobucket.com/user/moseskazaryan/media/20130529_234516_zpsafb08dd3.jpg.html)

I have tried typing nomodeset in front of quiet splash -- (so it looked like "quiet splash -- nomodeset), but it wouldn't work. I have even replaced the word splash with nomodeset, and still wouldn't get any results.

From the boot screen, I've even selected the Enter Setup, and here are some photos of what I see

[[IMG]http://i1131.photobucket.com/albums/m552/moseskazaryan/20130530_010802_zpsd01f3eee.jpg[/IMG]](http://s1131.photobucket.com/user/moseskazaryan/media/20130530_010802_zpsd01f3eee.jpg.html)
[[IMG]http://i1131.photobucket.com/albums/m552/moseskazaryan/20130530_012137_zps49423752.jpg[/IMG]](http://s1131.photobucket.com/user/moseskazaryan/media/20130530_012137_zps49423752.jpg.html)

I've been using a mac computer since 2007, and I got my zenbook a few days ago, and I'm having a real hard time using windows8. 

When it comes to computing, everything that I do pretty much involves Google. I know I could've gotten a Chromebook, but I love viewing media, and it didn't have the build quality, screen resolution, specifications, or anything else for me to get it. I found this video

[http://www.youtube.com/watch?v=uqdqxFEfMPI](http://www.youtube.com/watch?v=uqdqxFEfMPI)

And I want my zenbook to be clean of all bloatware (I already removed the win8 recovery partition to a separate usb stick, but I'm not sure if I had to do anything else to it), and to just run Ubuntu with a couple of google icons on the bottom that I use almost everyday (Google Chrome, Google Music Manager, Google Drive, Vuze, Android File Transfer). Plus, Ubuntu comes with some free features that I think will be great, like LibreOffice, Ubuntu1, VLC player, and so much more.

So, I'm pretty much stuck with trying to install Ubuntu, and I can really use some help please. 

Whoever that can help me, please either write a comment here, or even better, add me on skype (username: moseskazaryan), and that way we can do this step by step. 

The person that was helping me last night lives in Australia, and I live in California, so you can be from anywhere in the world, and I will welcome your assistance with open arms!

I really want this to work, and I hope someone here can help me.

Thanks in advance,

Moses

---

### Post by sanderj on 2013-05-30
"windows 8" and "UEFI": that means ... Bingo! Did you read [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) ?

---

### Post by fantab on 2013-05-30
I suggest that you return your laptop to factory settings and partitions and do a 'comprehensive backup': 
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
Also back up the Windows 'EFI' partition separately.

Windows 8 uses 'fast startup' which is actually 'hibernate'. You will have to disable 'fast startup' and actually 'shutdown' your computer and then re-boot. Otherwise Ubuntu will not install as the computer is already running Win8. (Probably this is the reason why your 'Try Ubuntu' is not working).
You will also have to disable 'Fast Boot' in the BIOS.
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Check if your Zenbook uses 'Intel SRT (Smart Response Technology)", if it does then disable it as well.
Though its not a must since 12.04.2, sometimes it is necessary to disable 'Secure boot'. I suggest you keep it until it is apparent that you have to disable it.

Assuming you have only one drive (SSD or HDD), then boot Windows and use Windows Disk Management tools to SHRINK Windows Partition to make space for Ubuntu. But do NOT create any new partitions from Windows, leave the space as 'unallocated'. Reboot Windows a couple of times for it to check for any filesystem errors after 'Shrink'.
[http://www.liberiangeek.net/2012/11/shrink-resize-partitions-in-windows-8/](http://www.liberiangeek.net/2012/11/shrink-resize-partitions-in-windows-8/)
If you have a SSD and HDD and if you want to install Ubuntu on a separte Disk than Windows then above step is not required. Let us know if you want to install Ubuntu on a different disk.

Now, Boot Ubuntu install Disk, in EFI mode. It should boot. I don't think you need 'nomodeset' option. However it will be good idea to check the integrity of your downloaded ubuntu.iso with [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM"). If their is mismatich then redownload, if possible use torrent download. Try reburning the .iso to USB again, if needed.

After booting Ubuntu, "Try Ubuntu". From desktop run Gparted and partition the 'unallocated space' that you have after 'shrinking' Windows partition. And from Desktop Install Ubuntu.

If you have problems booting after installing Ubuntu run '[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")', and apply 'Recommended Repair' also note the link 'BootInfo Summary' creates. Ubuntu should Boot. If it cannot then post the link that BootInfo Summary created.

Good Luck.

---

### Post by HeyItsMoses on 2013-05-30
> **sanderj said:**
> "windows 8" and "UEFI": that means ... Bingo! Did you read [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) ?
I've already that page, but I wouldn't know how to fix it.

Like I said, I'm really new to doing all of this stuff.

---

### Post by HeyItsMoses on 2013-05-30
> **fantab said:**
> I suggest that you return your laptop to factory settings and partitions and do a 'comprehensive backup': 
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
Also back up the Windows 'EFI' partition separately.

Windows 8 uses 'fast startup' which is actually 'hibernate'. You will have to disable 'fast startup' and actually 'shutdown' your computer and then re-boot. Otherwise Ubuntu will not install as the computer is already running Win8. (Probably this is the reason why your 'Try Ubuntu' is not working).
You will also have to disable 'Fast Boot' in the BIOS.
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

Check if your Zenbook uses 'Intel SRT (Smart Response Technology)", if it does then disable it as well.
Though its not a must since 12.04.2, sometimes it is necessary to disable 'Secure boot'. I suggest you keep it until it is apparent that you have to disable it.

Assuming you have only one drive (SSD or HDD), then boot Windows and use Windows Disk Management tools to SHRINK Windows Partition to make space for Ubuntu. But do NOT create any new partitions from Windows, leave the space as 'unallocated'. Reboot Windows a couple of times for it to check for any filesystem errors after 'Shrink'.
[http://www.liberiangeek.net/2012/11/shrink-resize-partitions-in-windows-8/](http://www.liberiangeek.net/2012/11/shrink-resize-partitions-in-windows-8/)
If you have a SSD and HDD and if you want to install Ubuntu on a separte Disk than Windows then above step is not required. Let us know if you want to install Ubuntu on a different disk.

Now, Boot Ubuntu install Disk, in EFI mode. It should boot. I don't think you need 'nomodeset' option. However it will be good idea to check the integrity of your downloaded ubuntu.iso with [MD5Sum Check]("https://help.ubuntu.com/community/HowToMD5SUM"). If their is mismatich then redownload, if possible use torrent download. Try reburning the .iso to USB again, if needed.

After booting Ubuntu, "Try Ubuntu". From desktop run Gparted and partition the 'unallocated space' that you have after 'shrinking' Windows partition. And from Desktop Install Ubuntu.

If you have problems booting after installing Ubuntu run '[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")', and apply 'Recommended Repair' also note the link 'BootInfo Summary' creates. Ubuntu should Boot. If it cannot then post the link that BootInfo Summary created.

Good Luck.
I already backed up the Win8 recovery on a separate usb drive. Will I still be able to get it back to Factory settings and partitions? 

How would I do a "comprehensive backup"?

Will you be free today (it's 7pm in my location now), to help me with this step by step over skype? 

I'm just worried about damaging my laptop completely.

---

### Post by fantab on 2013-05-31
> **HeyItsMoses said:**
> I already backed up the Win8 recovery on a separate usb drive. Will I still be able to get it back to Factory settings and partitions? 

Yes you should be able to get it back. Restore the Wind8 recovery partition and run 'recovery'. If you cannot for some reason then contact the Laptop service (assuming that Win8 came pre-installed) and let them help you with the restoration and recovery. 

Did you create a Windows Repair Disc? You must. Once your laptop is restored to factory settings the first thing you will do is create a Windows 8 repair disc. Then make that back up of the entire HDD.

> How would I do a "comprehensive backup"?
Read the post by 'Mark Phelps' in the first link in my post carefully. It talks about using '[Macrium Reflect]("http://www.macrium.com/reflectfree.aspx")' to do a back up.

> I'm just worried about damaging my laptop completely.

Don't worry at the most you will mess up the Windows8 install. This is the reason why a good backup is absolutely necessary.

Just follow the instructions in my post and you will do good. The forum is here to help.

Good Luck.

---

### Post by yurahi on 2013-06-06
I have the same computer and I could only install ubuntu 12.04 and upgrade to a new vercion caused comflictos 12.04 I recommend that you install is very stable in the machines with UEFI

---

### Post by Pander on 2013-06-27
It is also not installing for me and I really need it. :( Please see [http://bugs.launchpad.net/ubuntu/+source/shim/+bug/1195483](http://bugs.launchpad.net/ubuntu/+source/shim/+bug/1195483) Can you help to get it fixed? See also [https://bugs.launchpad.net/ubuntu/+source/shim/+bug/1195483](https://bugs.launchpad.net/ubuntu/+source/shim/+bug/1195483)

---

### Post by oldfred on 2013-06-27
See also this thread.
 Asus Zenbook Prime UX31A (UEFI)  Blank screen resolved by turning secure boot off, many tests of Boot parameters
[http://ubuntuforums.org/showthread.php?t=2086054](http://ubuntuforums.org/showthread.php?t=2086054)

---

### Post by Pander on 2013-06-29
Does [http://cdimage.ubuntu.com/daily-live/current](http://cdimage.ubuntu.com/daily-live/current) work? Please let me know.

---

### Post by oldfred on 2013-06-29
I cannot recommend the daily build for any other than those that want to test and then report bugs. Generally it works but then something gets updated and you may have to wait for fixes or reinstall the new daily.

You always should have another working install when using daily for that reason, either another install on same computer or another computer with a reliable operating system.

---

