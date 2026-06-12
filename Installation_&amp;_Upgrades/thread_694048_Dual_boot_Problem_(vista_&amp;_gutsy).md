---
title: "Dual boot Problem (vista &amp; gutsy)"
date: 2008-02-11
forum: Installation &amp; Upgrades
---

### Post by FatmanC on 2008-02-11
I know i shouldn't be using vista, but i would like to keep it there just in case.

So i have vista and ubuntu installed and everything is working properly, i can log in to both OS. I allocated 76 gigs to vista and 60 gigs to gutsy. Some how it says that i have used up 40 gigs in vista and has left me around 26 or so. I have not used Vista to store files whatsever except for WoW. THis is quite strange. It seems that the data that i stored under the ubuntu partition is effecting that. So i look into the disk management under vista and saw that windows is has both partitions set to primary. Is there a way i can set ubuntu to extended primary? Or is this a completely different issue? Thanks

---

### Post by mrsteveman1 on 2008-02-11
Since you only have 2 partitions they should both be primary partitions anyway.

As for the drive space, i suggest you download [windirstat]("http://windirstat.info/wds_current_setup.exe")

It will show you graphically where the space on your windows partition is being used. If when you do that you can't seem to account for the used space, then something may be wrong. As for what would cause the ubuntu partition to affect the amount of used space on the windows partition, i have no idea why that would happen, and it shouldn't.

---

### Post by Herman on 2008-02-11
:) Hello FatmanC,
That  would be a completely different issue.
There's a section of the hard disk's MBR called the 'partition table', and it has room for four entries, which contain code describing the start sectors and end sectors and other details describing up to four patritions. Those are called primary partitions.
If one of those is turned into an 'extended' partition is can contain a string of 'logical' partitions linked in a series, so we can have more than four partitions in a hard disk.
[                                       What does a Partition Table really look like?]("http://users.bigpond.net.au/hermanzone/p6.htm#What_does_an_MBR_really_look_like").

You can't just click somewhere and turn a primary partition into a logical partition.  It is possible to copy the whole partition with GParted and paste it into an extended partition though, if you have the disc space and you first make an extended partition to put it in. That would be a time consuming job though and I don't see how that would fix your problem. 

There are a couple of things I have seen that can make a Windows file system appear full when it doesn't contain very many files. One is if it has a virus. I'm not saying yours does but a friend of mine had Windows 2000 that was virus infested and we found it was full of files with strange filenames. They were invisible, system, read-only files, so we didn't see them in Windows but we did see them when we mounted Windows in a Ubuntu LiveCD. We deleted all we could find and we thought we had them all.
Then we shrank the Windows partition and installed Ubuntu.

A few months later, my friend brought back the computer, it was full again. We found more of those virus files in Windows and deleted them all. Funny thing was, it was filling up Ubuntu too, to the point of slowing Ubuntu down as well. 
There is an .Trash-username file that appears in each mounted file system, and  I discovered that was full of virus files. I had to use a sudo command to delete them.  After that the computer started working much better.
We got the computer clean again, but by then my friend had had enough with Windows. After checking with his wife first, the decision was made to delete Windows and install another Ubuntu there instead, making it a Ubuntu-Ubuntu dual boot. They're both Ubuntu users now anyway. By the way, my friend's wife is topping her class in her computer studies. She uses with Open Ofiice.org and she's amazing her instructors with what she can do.
That's another story though.

The main point is, you may need to empty your trash in Ubuntu is you have deleted stuff from your Windows partition because things can get stuck in that .trash folder. Especially if you deleted large files like music or video files.
It's something to check anyway, I'm not sure, maybe your problem is something different.

Another thing to try would be running CHKDSK in your NTFS file system, that might clear the problem up if the file system is developing a few problems. Maybe it's full of duplicated links or something, and CHKDSK will fix it.

Regards, Herman :)

---

### Post by FatmanC on 2008-02-11
I ran a virus check and ran chkdisk and this has not resolved my problem. attached is the screen shot.

---

### Post by mrsteveman1 on 2008-02-11
When you say the Ubuntu partition is affecting free space on the vista partition, what do you mean? Elaborate a bit on the problem.

Are you just confused as to why Vista is using so much space? (certainly understandable, it uses way too much anyway)

---

### Post by FatmanC on 2008-02-11
> **mrsteveman1 said:**
> When you say the Ubuntu partition is affecting free space on the vista partition, what do you mean? Elaborate a bit on the problem.

Are you just confused as to why Vista is using so much space? (certainly understandable, it uses way too much anyway)

sorry let me elaborate. anything that i save under my ubuntu partiion effects the disk space in my windows vista partion. So if i save a large file like a video file in ubuntu. i switch to vista and check the disk drive and it would show that i have even smaller free space than i did before saving the file. So in my HD there are 3 main partitions. one is ubuntu, one is vista, and the other is what HP installed on to my machine for backup purposes.

---

### Post by Herman on 2008-02-11
GParted is showing a yellow warning triangle on your NTFS partitions. Maybe you need to run CHKDSK with different options?
I don't know much about NTFS or CHKDSK, or the Windows Recovery Console, but here are a couple of links, [Microsoft DOS chkdsk command]("http://www.computerhope.com/chkdskh.htm") Computer Hope .com, and [Using Chkdsk]("http://www.deltatranslator.com/chkdsk.htm"). Maybe you need to use the /F switch?

I'm not saying your Windows Vista has a virus, but if it does, scanning with your antivirus software and not being able to find a virus does not mean your computer is safe. It might just mean you have a virus that the antivirus doesn't recognize. 

ls your Windows Vista file system automatically mounted in your /media directory in Ubuntu? 
In Linux we have the ls command. 
To show the sizes of files and try to see what directory looks suspicious you could run.
```
ls -Shal /media/hda1
```Where: /media/hda1 is the mount point for your Windows file system.

That will give you a list of your Windows Vista files in the root of drive C , sorted from largest to smallest. 
Hopefully you'll be able to easily see which one is unnecessarily large and then use the same command again to look inside that folder and so on until you find the problem.
If CHKDSK doesn't do it, try that and see what you can find out.
But I think it would be more likely a file system problem that CHKDSK should be able to fix.

Regards, Herman :)

---

### Post by Herman on 2008-02-11
```
ls -Shal /media/hda1 | less
```
Would be even better, especially for folders that contain a lot of files.

---

### Post by froy02 on 2008-02-11
Whenever you install, remove or change something in Vi$ta it makes a restore point, meaning it saves that setup.  If you add a file from Ubuntu, Window$ sees that as a change and saves another restore point when you start Window$.  
There's a way to stop that but this is a Linux forum.  Check your help section in window$.  It is not Linux fault. It is Window$.

---

### Post by FatmanC on 2008-02-11
Thanks for the help. I had remove the restore point, mounted the windows partition back in ubuntu under media path name. I went back into windows and ran chkdsk c: /r which did a full check, it is now back to normal. Thanks again.

---

