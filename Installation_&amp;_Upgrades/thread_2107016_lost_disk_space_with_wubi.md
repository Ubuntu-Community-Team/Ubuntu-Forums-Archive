---
title: "lost disk space with wubi"
date: 2013-01-20
forum: Installation &amp; Upgrades
---

### Post by mavericksn on 2013-01-20
Hi Everyone,
   Need help recovering some disk space I lost. Listed below is the sequence of actions that led to the final state of my laptop.

(1)Made a windows backup .(windows 7)
(2) Installed Ubuntu under windows using wubi.
(3)Ubuntu worked fine under dual boot.
(4) Then When I was under Windows, Said yes to windows update.
(5)The update tried to install, and at some point rolled back saying it failed.
(6) Now when I try to boot into windows, it gave an error mentioning it could not load some user profile. When I try to boot into ubuntu, it did not take me to the usual graphic environment, but took me to command promt based.
(7) So I decided to restore and did restore only system files from my restore point. Did not help.
(8) Did a full system restore.
(9) Now I dont see the ubuntu directory as I did not have it when I made the backup, but that space of 30 GB which I allocated for ubuntu is lost. As in , windows says 90 GB used in C drive, but the files/folders only account for 60 GB.
(10) I tried some disk recovery/defrag softwares to figure out. They show an unknown space of 30 GB as a chunk, but do not let me take any action on it..like delete the file. But the other files the softwares show they typically let you delete them if needed.

So that is the state of my 30 GB so far.

Also I am holding off on installing a proper linux installation by making a partition and installing, with concerns that if I do that without resolving this, I might lose that space forever. Let me know your opinion regarding that as well.

Thanks a lot for your help.

---

### Post by ttbek on 2013-01-20
I think this is what you want: [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide) the most relevant portion is copy pasted here for everyone's convenience: 
**How do I manually uninstall Wubi?**

 Remove C:\ubuntu and C:\wubildr*  
In  Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi  line. Alternatively you can modify the boot menu via Control Panel >  System > Advanced > Startup and Recovery and pressing "Edit". For  Windows 98 you have to edit C:\config.sys and remove the Wubi block. For  Windows Vista/7, you can use the built-in *bcdedit* command or install [EasyBCD]("http://neosmart.net/EasyBCD/") to edit the boot menu. To use *bcdedit*, run *cmd.exe* as an administrator, then enter *bcdedit* to show all boot entries, note the {GUID} specified for the Ubuntu entry, and then remove it: *bcdedit /delete {GUID}* 
To remove Wubi from the add/remove list, delete the registry key: HKLM\Software\Microsoft\Windows\[CurrentVersion]("https://wiki.ubuntu.com/CurrentVersion")\Uninstall\Wubi 
An  easy method of removing this registry key is to paste the following  text into a plain editor such as Notepad, close and save the file as  something like removeWubiKey.reg (you may wish to go to Folder Options  > View and disable the "Hide file extensions for known file types"  option to check that the .reg extension has been applied correctly).  Then you can perform the rest automatically by opening the file in the  normal Windows manner, or choosing the "Merge" option from the right  click context menu. Note: The formatting is rather strict, so copy the  text exactly for best results. *You may need to be logged in as the  administrator to delete the key, depending on the version of Windows you  are using. User Account Control in Vista may also ask for permission,  in the typical fashion.* 

REGEDIT4  [-HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall\Wubi]After  deleting the registry key, Ubuntu may still appear in the program list.  If this is the case, you may be asked if you would like to remove the  item from the list. 

But... there shouldn't be any lost disk space, the WUBI installer does not make a partition.  Even if it did, you would not permanently lose disk space, gparted is a very good partition editor that could fix that even if it was the case, which it is not.  Read the above link for more info, as well as this: [http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29](http://en.wikipedia.org/wiki/Wubi_%28Ubuntu_installer%29) and this: [http://en.wikipedia.org/wiki/Loop_device](http://en.wikipedia.org/wiki/Loop_device)  Also, I don't know what disk recovery/defrag software you're using... but most of the windows ones are complete nonsense/sketchy warez.  Only one I can think of that you should use for defragging is the one that comes with windows, besides we're not trying to do disk recovery or defragging, By that I mean, we're not dealing with a disk that has lost it's partition table or something like that, and defragging is only for efficiency (regroups files that have been scattered by fragmentation in NTFS for faster disk access).  If you were to end up having to mess with partitions, the way to do it is to use gparted on the Ubuntu liveCD.

---

### Post by mavericksn on 2013-01-20
Hi ttpek,
    Thanks for the response.
Just some clarifications.
I could not uninstall ubuntu. I wasnt able to log into windows, so I restored to a backup which was done before I installed ubuntu.
After restoring to that backup, I dont see the ubuntu directory or wbuild directory, guessing as expected, because that backup was created before I installed ubuntu. Then I would expect that 30 gb to be given back except that, it wasn't.

The defragging software, I did not mean to defrag, but some other guys had this lost disk space problem and they resolved it by using a defrag software to identify that chunk of data and delete that and basically recover that missing disk space. If you know of any other tools as well which could identify the disk space and recover it..please let me know. I would try them.

Thanks a lot for looking into this.

---

