---
title: "Is it safe to view Windows files in Ubuntu?"
date: 2016-05-17
forum: Installation &amp; Upgrades
---

### Post by meridius2 on 2016-05-17
After so many years of waiting for Ubuntu to get better and having to tolerate Windows I think I have found an acceptable compromise. 

I have a desktop with 2 HDDs. I separated out the operating systems. Windows 7 Pro 64-bit is on the first disk and Ubuntu 16.04 LTS 64-bit is on the second disk.

I just did some updates from the software updater and Ubuntu installed grub with an option for Windows 7 loader. This has now given me access to my Windows files. I had been trying to avoid using grub altogether but as long as there is not a complete mess up this means I can now access my Windows 7 files within Ubuntu.

 Is it safe to run Windows files within Ubuntu? The last time I did this it came up with some errors in my external HDD which actually broke completely! Having said that it was with Ubuntu on an old laptop.

 From what I can see the grub interface does not appear to be on my first HDD with Windows and I'd like to keep it that way!

I am having another problem which I will put in another post but I would like to say that Ubuntu has come a long way since I first used Hardy Heron, which I nevertheless really liked.

---

### Post by yancek on 2016-05-17
>  I had been trying to avoid using grub altogether but as long as there  is not a complete mess up this means I can now access my Windows 7 files  within Ubuntu.

Did you manually edit the bcd file to boot Ubuntu?  Or were you  using EasyBCD or similar software to boot Ubuntu?  Otherwise, it's pretty hard to avoid using Grub because it has been the default bootloader for Linux for well over a decade.

Grub hasn't given you access to your windows files, it just created a menuentry which you can use to boot windows from the Ubuntu Grub menu.  If you didn't have that before, I expect it is because you did not have your windows drive attached when you installed Ubuntu.  It is the "ntfs-3g" software which allows read/write access to windows filesystems.  So when you select windows 7 from the Grub boot menu, you are booting into windows and can do whatever you want.  If you access an ntfs partition while booted to Ubuntu or any Linux system, you can read/write and change files but should only be 'data' and not 'system' files or you will likely have problems.

To get details on your boot and system files, go to the site below and get and run the boot repair software.  Select Create BootInfo Summary and you will get output on your system which you can review yourself or post here and that will tell where your Grub code is as well as many more pertinent things.

---

### Post by grahammechanical on 2016-05-17
The installer defaults to installing Grub onto the first hard drive (sda). The way to avoid that is either to re-direct the installer to put Grub on to the second hard drive (sdb). Or, to disconnect the first hard drive while installing Linux. But that means that Grub is unaware of the existence of Windows. The way to fix that is to load into Ubuntu and run this command.

```
sudo update-grub
```

It seems that Software Updater did just that. There must have been a kernel update for that to happen. Remember, Grub is installed on sdb. So, if you need to re-install Grub the command is

```
sudo grub-install /dev/sdb
```

If Windows is hibernated then Ubuntu will come up with a message saying that the file system is in an unsafe state. Microsoft uses hibernation to reduce Windows 8/10 loading times. You may upgrade to Windows 10 one day. I suggest disconnecting the Ubuntu drive when you do that. Just to be on the safe side. And update Grub afterwards. Otherwise, you may find that you need to re-install Grub.

Use Windows utilities to manage Windows partitions & Linux utilities to manage Linux partitions. I have no experience in writing to Windows partitions from Linux.

Regards.

---

### Post by Mark Phelps on 2016-05-17
You asked about "running" Windows files within Linux, and that generally means executing Windows apps -- which basically do not "run" within Linux.  There is Wine and it's companions, but that is a different story.

It's basically NOT safe to access a Windows OS partition from Linux, even if you only intend to read the files -- because it's really easy to corrupt the Windows filesystem, and if that happens, you have to boot into Windows to fix it, and if the filesystem is corrupted, you won't be able to do that.

If your goal is to share data/files between Windows and Linux, a safer alternative is to create an NTFS partition containing only the shared files and data.  Since you don't boot into a data partition, you don't have to worry about the filesystem getting corrupted because, if that happens, you can easily boot into Windows to fix it.

Good Luck

---

### Post by pfeiffep on 2016-05-17
There's good advice above to which I'll add you can add a NAS to your setup that can house backups for both OSes and be used as a common data store.

---

### Post by kurt18947 on 2016-05-17
> **Mark Phelps said:**
> You asked about "running" Windows files within Linux, and that generally means executing Windows apps -- which basically do not "run" within Linux.  There is Wine and it's companions, but that is a different story.

It's basically NOT safe to access a Windows OS partition from Linux, even if you only intend to read the files -- because it's really easy to corrupt the Windows filesystem, and if that happens, you have to boot into Windows to fix it, and if the filesystem is corrupted, you won't be able to do that.

If your goal is to share data/files between Windows and Linux, a safer alternative is to create an NTFS partition containing only the shared files and data.  Since you don't boot into a data partition, you don't have to worry about the filesystem getting corrupted because, if that happens, you can easily boot into Windows to fix it.

Good Luck

Excellent advice. Another benefit of a separate data partition is it makes backups simpler. I'd done that in Windows for many years when I was a Windows user. It has some of the same benefits as a separate /home partition in linux and simplified my life when a Windows install became unusable due to a bad data cable. The data was still fine.

---

### Post by meridius2 on 2016-05-17
Wow. I have only been away from my desk for a few hours and look at the number of responses! So bit by bit...

> Did you manually edit the bcd file to boot Ubuntu?  Or were you  using EasyBCD or similar software to boot Ubuntu?

No. I feel safer using the BIOS. I had bad experiences when I first used grub dual booting Hardy Heron and Windows XP. I used EasyBCD once but had forgotten about it until this post.

> 
If you didn't have that before, I expect it is because you did not have your windows drive attached when you installed Ubuntu.

Precisely. I did that on purpose as I didn't know what would happen if the two drives were attached to the motherboard during installation. I am quite new to desktops. My main experience has been with Toshiba laptops.

> If you access an ntfs partition while booted to Ubuntu or any Linux system, you can read/write and change files but should only be 'data' and not 'system' files or you will likely have problems.

In a sense all I really want to do is access music and film videos and the occasional file.

> You may upgrade to Windows 10 one day. I suggest disconnecting the Ubuntu drive when you do that. Just to be on the safe side. And update Grub afterwards. Otherwise, you may find that you need to re-install Grub.

Thanks for letting me know. Windows 10 is currently my no.1 enemy to avoid. Nevertheless I am completely bored and fed up with Windows 7 but have found no interesting Microsoft alternative to 'upgrade' to. It's good that Ubuntu has made enormous strides in terms of compatibility with applications that run on Windows.

> If your goal is to share data/files between Windows and Linux, a safer alternative is to create an NTFS partition containing only the shared files and data.

This is what I have done. As mentioned my main question was to know if it is safe to play music videos and films. I guess the answer is yes as it is not an os partition.

I am just double checking again to be 100% sure. If my understanding is correct the Ubuntu default file system is ext3 or ext4. Can I for example write a document in LibreOffice Writer and save it to the Windows (NTFS) Data partition safely? Also can I download a video from youtube in Ubuntu and copy it to the Data partition? Can I run a program from the Data partition and it runs in Ubuntu (i.e. would the Ubuntu software manager accept it?) Also can I just play videos and music safely and open documents without the original Microsoft Word format being altered?

Finally can I update grub from a live cd or pen drive looking into my Ubuntu partition if I cannot get in to the os and have a major problem?

---

### Post by pfeiffep on 2016-05-17
> This is what I have done. As mentioned my main question was to know if  it is safe to play music videos and films. I guess the answer is yes as  it is not an os partition.

I am just double checking again to be 100% sure. If my understanding is  correct the Ubuntu default file system is ext3 or ext4. Can I for  example write a document in LibreOffice Writer and save it to the  Windows (NTFS) Data partition safely? Also can I download a video from  youtube in Ubuntu and copy it to the Data partition? Can I run a program  from the Data partition and it runs in Ubuntu (i.e. would the Ubuntu  software manager accept it?) Also can I just play videos and music  safely and open documents without the original Microsoft Word format  being altered?

Finally can I update grub from a live cd or pen drive looking into my  Ubuntu partition if I cannot get in to the os and have a major problem?         No guess - it's safe!

Saving a Libre Office document to an NTFS partition is absolutely no problem - I do it all the time so no matter which OS is booted I have full read - write access. There is one caveat in that this is a single user system so I needn't concern myself that NTFS doesn't have the same secutiry as Linux ext3 or 4. 

You can download virtually anything using either OS and save it to an NTFS data partition so it will be accessible to the other OS.

I'm going to pass on the grub question - there are much more experienced folks here that can answer that authoritatively.

---

### Post by sudodus on 2016-05-18
I agree with the previous posts: It is a good idea to share data between linux and Windows in a **data** partition with the  NTFS file system. You can read and write from both operating systems.

I want to add one thing to consider: If Windows is hibernated, things can be messed up. Ubuntu should not use the data partition in such cases. The best way to manage it is to keep Windows from hibernating (turn it off).

---

### Post by vasa1 on 2016-05-18
> **meridius2 said:**
> Many thanks for the continuing feedback. I'll use the NTFS partition for data in both os's. I don't have a hibernate option in Windows. I normally shut down, log off or restart in Windows. I only have a minor problem with networking in Ubuntu which I will mention in a new post if necessary.

This is an unrelated question but ...

If your initial question has been answered, please do us the favor to mark this thread [SOLVED]. See [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads).

And you are correct in that additional questions will be better off in threads of their own: the network one would go in the [appropriate subforum]("http://ubuntuforums.org/forumdisplay.php?f=336").

I've moved the rest of your post to here: [http://ubuntuforums.org/showthread.php?t=2324899](http://ubuntuforums.org/showthread.php?t=2324899)

---

### Post by Impavidus on 2016-05-18
> **meridius2 said:**
> Can I run a program from the Data partition and it runs in Ubuntu (i.e. would the Ubuntu software manager accept it?)

No, unless it's in some platform-independent form like a shell script. Then you can run it, but the Ubuntu software manager won't accept it.

---

