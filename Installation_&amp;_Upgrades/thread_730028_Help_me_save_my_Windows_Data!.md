---
title: "Help me save my Windows Data!"
date: 2008-03-20
forum: Installation &amp; Upgrades
---

### Post by theaceoffire on 2008-03-20
Ok, here is a quick rundown:

Installed Wubi, installed Ubuntu 7.04 to the C Partition, tried to upgrade to 7.10 from inside it, destroyed windows. 

We are now booting from the live ubuntu cd, and trying to backup her data, but we can't get into the hidden windows file "Documents and Settings"...

Can someone tell me how to see hidden Window's folders from inside ubuntu's live cd? I can do the rest from there. Turning on Ubuntu's "View hidden folders" doesn't make it show, so if there is a special mount we have to do or something let me know.

---

### Post by PmDematagoda on 2008-03-20
Actually, the only way I know that you could hide a file/folder on Linux is by putting a "." in front of the name.

So unless the folder has been deleted, you should be able to see it.

Edit:- Did you check the path? The path has to be the exact path where the folder is found since Windows links may not be understood by Linux.

---

### Post by theaceoffire on 2008-03-20
No, this problem has occured before in Ubuntu. For example, if you look at a WoW installation disc, the "setup.exe" file does not appear in the window, but if you boot into XP you can see it "hidden" in windows.

This is very important to my GF, could someone who dual boots open their C: partition in Linux and tell me if they can see their 'Documents and settings" folder?

***************EDIT****************
I haven't tried this yet, but I found this tutorial: [http://ubuntuforums.org/showthread.php?t=270609](http://ubuntuforums.org/showthread.php?t=270609)

Is there some setting I can use mounting the hard drive that would unhide windows hidden files?

---

### Post by Herman on 2008-03-20
:) Hello theaceoffire

> This is very important to my GF, could someone who dual boots open their C: partition in Linux and tell me if they can see their 'Documents and settings" folder?Here is a link to a screencap of what you should see in the root of a typical Windows XP file system when you have it mounted in Ubuntu, [A Birds's eye view of Windows XP]("http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP") .
As you will see, you can see 'Documents and Settings', and it is not a hidden folder, I have looked at lots of Windows systems when I'm fixing computers for friends and they all look quite similar to this.

As far as I know, Windows 'hidden' files are only hidden to Windows users, and we can see everything when they are viewed from Ubuntu. I will check up on that shorty and make sure that's right, but I'm fairly certain we should be able to see them if they're there and if they're accessible to the file system.

Ubuntu gives you access to a great number of free and excellent programs for testing your hard disk drive to make sure it is in good shape and is not failing, and if the hard drive is okay, we have some of the best data recovery utilities, also for free.
If the hard disk is beginning to fail, then it will be important to rescue your data immediately, or you might lose it for good.

The instructions in the link you posted would describe the right procedure for an ordinary file rescue when the file system (and hard disk) containing the files is okay.

Regards, Herman :)

---

### Post by theaceoffire on 2008-03-20
Thank you very much Herman.

However, using Ubuntu 7.10 as my main OS on my home computer for several months now (Since release as a mater of fact, using a fresh instillation), I have observed SOME hidden files being missing. 

Not the "Documents and Settings" that my GF is experiencing now (Since I am Ubuntu Only), but more specifically the World of Warcraft disk, which has hidden the exe in the windows OS and does not show up when viewing it in Ubuntu (Does show up in XP in a virtual computer however). 

My only guess is that something must have been altered in 7.10 so that hidden files in windows are not shown in Ubuntu. 

I am willing to try remounting the offending partition if that will help, please let me know if you have any ideas...

************EDIT**************
I had her go on her computer, and type in a terminal 
> cd /media/Disk1/ 
cd ./Documen (Tried to press tab here)

And it would not auto-complete, which implies that the folder is not seen... yes? It doesn't show up when you type "ls" either.
I also tried typing in "cd ./Documents\ and\ Settings/", but it didn't work. I am willing to try this, or anything else again.

************EDIT 2 *************
I found this page about other people who are having a problem sort of similar to mine: [http://www.astahost.com/info.php/ubuntu-livecd_t15859.html](http://www.astahost.com/info.php/ubuntu-livecd_t15859.html)
But I can't seem to find anyone else with this issue.

---

### Post by Herman on 2008-03-20
Alright, I don't know very much about wubi, but I know what it should be like (normally) to mount a Windows system in a hard disk installed Ubuntu or in a Ubuntu LiveCD.
I know that we should, (normally) be able to see all the files and folders, even the ones that are 'hidden', 'system', 'read-only' files to Windows users and even virus files which Windows users can't see.
I use the FAT32 file system in Windows XP (not the I ever boot it anymore, I just keep it for testing purposes when I want to help someone here in the Ubuntu Web Forums with a dual boot question). Maybe you use the NTFS file system and there's something about that I haven't noticed when I'm fixing other people's computers here.

For example, referring to my [WinGRUB Page]("http://users.bigpond.net.au/hermanzone/p9.html") , you will see that Windows users need to run[COLOR=DimGray] '[/COLOR][COLOR=#ffffff][COLOR=DimGray]attrib -s -h -r boot.ini' [/COLOR][/COLOR]from their command line in order to 'see' and access boot.ini, but Ubuntu users can see it right away. We can't write to it (as far as I know), until the security attributes have been relaxed from within Windows.

So you are saying you think your problem is within your Ubuntu?
Or maybe there is a new way Windows might have invented for hiding files maybe?

This seems like quite an interesting problem and now I'd be interested to try to find out what's going on too, I have never heard of this before.

I think would we start with the simplest things first, how about booting up Windows and running a file system check?
 You go 'Start', --> 'My Computer', and right-click on 'Drive (C:).
Open the 'Tools' tab, and in the 'Error Checking' box, hit the button for 'Check Now'.
Another window will open, place a check mark in both 'automatically fix file system errors', and 'Scan for and attempt recovery of bad sectors'.
Then click 'Start', and Windows will say it can't do it right now, you'll have to reboot. 
So reboot, and it'll blue-screen halfway through the boot-up and run CHKDSK for you.
Maybe that will fix it or maybe not, but it won't hurt and probably will do some good. A file system check is always good.

> I am willing to try remounting the offending partition if that will help, please let me know if you have any ideas...Yes, it might help. Let's see what options you're using to mount the file system.
Is it  NTFS or FAT32?
```
cat /etc/fstab
```Regards, Herman :)

---

### Post by theaceoffire on 2008-03-20
Normally I let ubuntu auto-mount everything, however I tested this just now on my Dad's PC (The problem PC is my GF, and on her computer XP will not boot in normal or safe mode, which is why we are backing everything up).

I found that if I followed the following two commands:
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xeb275b50

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           8       64228+  de  Dell Utility
/dev/sda2   *           9        9119    73184107+   7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo mkdir /media/recovery
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/sda2 /media/recovery -o nls=utf8,umask=0222

```
This allowed me to see the hidden folder just fine! I will ask my GF to try the same thing, and we will see if it works.

So I figgure this was a wierd effect of Wubi being updated. The ntfs drive works on this comp, so I will get her to do the same steps and let you guys know if it fixes it. 

Also, when I get home to my computer,  I will do the same steps to see if I can see the WoW setup executable on the cd disk. 

^_^ Thanks for your help guys!

---

### Post by Herman on 2008-03-20
:) Okay, cool, be sure to keep us posted. It's interesting.

Regards, Herman :)

---

### Post by theaceoffire on 2008-03-21
IT WORKED!

We created by hand a folder in /media/ called recovery, unmounted the "disc" that ubuntu's live cd had automounted, and then mounted it by hand like it said above! 

She could see it! She is copying the whole folder to another partition now.

I have no clue why we can't see it in Ubuntu 7.10, but if anyone else has this issue, this is how to fix it!

---

### Post by gpilkay on 2008-03-21
Actually, Wubi has had this problem and there's an easier way to fix it, I think.  Check out the Wubi forum, it's under third party projects, the creators are very active on the board.

Edit:  Here it is:

Quote:
run chkdsk /r from a windows CD or a rescue CD (recovery console)

And here's the forum link:
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

---

