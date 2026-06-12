---
title: "install ubuntu alongside Win7 option not shown"
date: 2010-12-15
forum: Installation &amp; Upgrades
---

### Post by raac on 2010-12-15
Hi guys, I just installed Windows 7 in my computer, and I wanted to install ubuntu along with Windows 7, but for some reason during the installation process that option (install ubuntu alonside with Windows 7) is not displayed. I did a a check for errors on my disk, and also defragmented and still it does not work. Also, I check on disk management console on Windows, and there is only one partition on my Hard Disk. What should I do???

---

### Post by Dutch70 on 2010-12-16
Other than a bad burn on your cd, I don't know why it wouldn't show up. I'd try burning the cd again at the slowest speed possible. 

Also you may want to consider these alternatives. 

[_[COLOR="Red"]Virtual Box[/COLOR]_]("http://www.psychocats.net/ubuntu/virtualbox")

Or... [_[COLOR="Red"]Wubi[/COLOR]_]("https://wiki.ubuntu.com/WubiGuide")

I've seen it, but I'm not really sure what "alongside windows" actually does.

---

### Post by wilee-nilee on 2010-12-16
You might take a snippet of the W7 disk manager and post it.

You need a unallocated space most likely to install to. You make this unallocated space by using the shrink function in disk manger in W7.

We also use the bootscript in my signature to find what is where that might be a option to post as well, especially if you are planning on removing any partitions. If you post this notice the codetags description in the signature as well.

---

### Post by garvinrick4 on 2010-12-16
> **raac said:**
> Hi guys, I just installed Windows 7 in my computer, and I wanted to install ubuntu along with Windows 7, but for some reason during the installation process that option (install ubuntu alonside with Windows 7) is not displayed. I did a a check for errors on my disk, and also defragmented and still it does not work. Also, I check on disk management console on Windows, and there is only one partition on my Hard Disk. What should I do??? What is on your disk now. A system partition a 7 partition and a recovery partition. It comes with 3, do you have something else to make a 4th primary partition? That would be 4 and all you get.
# If you want to you can take your install cd and use try ubuntu and go to gparted and open and take a screenshot and post in this thread with attachments on top of Message window. We can see what to do then.
## Do either this or previous post both come to same end.

---

### Post by wilee-nilee on 2010-12-16
> **garvinrick4 said:**
> What is on your disk now. A system partition a 7 partition and a recovery partition. It comes with 3, do you have something else to make a 4th primary partition? That would be 4 and all you get.
# If you want to you can take your install cd and use try ubuntu and go to gparted and open and take a screenshot and post in this thread with attachments on top of Message window. We can see what to do then.
## Do either this or previous post both come to same end.

I prefer gparted as well it will give us da picture.

---

### Post by raac on 2010-12-16
Ok, I just attached the screenshot, this is the first time I'm doing it, so I hope I did it right. Anyway, if possible, I rather have the dual boot instead of virtual box. 
 
If it is still possible to have it dual boot, I'd appreciatte if you guys tell me exactly what to do either following the gparted route or anyother other one. I'm sort of new with all this technical issue.
 
The thing is that, I used to have it dual booted, but I formatted my disk drive with my laptop recovery Disk , I deleted all partitions (I think I had three), then Install Windows Vista in one of them, then upgraded it to Windows 7.

---

### Post by wilee-nilee on 2010-12-16
Use the disk manager in W7 to shrink that one partition it is just a right click and it will tell you how far it can be shrunk. That will leave a unallocated space.

Other users like a separate home partition you might want this so, the other poster garvirick4 is familiar with this and the whole process so we might let them get in on this.

In the unallocated space though you can do a straight install and let Ubuntu build the partitions, as well.

---

### Post by garvinrick4 on 2010-12-16
#There is a red circle next to the sda1 in gparted, I do not know what that symbol means
I have not seen it before. Something is at hand there and we have to find out before proceeding. 
# I am going to google around to see what it represents for that partition.
## If someone else knows chime in please.

---

### Post by garvinrick4 on 2010-12-16
raac,
run this in a terminal in live CD.
```
sudo fdisk -l
``` (lower case L)
post to this thread if you would.

This is a gparted manual just for you to keep.
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
#first we do have to find out what the red insignia means next to sda1

---

### Post by raac on 2010-12-16
This is the output of fdisk....
 
 
ubuntu@ubuntu:~$ sudo fdisk -l
 
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001c2a5
Device Boot Start End Blocks Id System
/dev/sda1 * 1 30402 244196352 7 HPFS/NTFS
 
ubuntu@ubuntu:~$

---

### Post by wilee-nilee on 2010-12-16
In gparted right click on sda1 then information it will probably give something on the red dot.

---

### Post by garvinrick4 on 2010-12-16
#Something is just amiss in your harddrive with the red warning sign and it shows
  no space being used in NTFS partition sda1, your Windows 7.
# I would say to go into your command line in Windows and run chkdsk to see if it helps
   your drive. Right now it is just unreadable. You do not have any type of raid setup just
   one 250 gig drive. This code to check your disk in Windows
```
  chkdsk /f /r 
```Now boot into gparted and see if red warning sign gone and shows some disk being used.
[FONT=Arial,Helvetica][SIZE=-1][B][COLOR=#FF0000]
##Below how to run chkdsk in Windows
[/COLOR][/B][/SIZE][/FONT]```

[FONT=Arial,Helvetica][SIZE=-1]**[COLOR=#FF0000]1[/COLOR]**. Click the **Start **button[/SIZE][/FONT]
[FONT=Arial,Helvetica][SIZE=-1]**[COLOR=#FF0000]2[/COLOR]**. In the **Run** window's ***Open*** box, type **[COLOR=#000099]cmd[/COLOR]** or **[COLOR=#000099]command[/COLOR]**[/SIZE][/FONT] 
[FONT=Arial,Helvetica][SIZE=-1]**[COLOR=#FF0000]3[/COLOR]**. Click **OK **and an MS-DOS-style black screen will appear in a new window[/SIZE][/FONT] 
[FONT=Arial,Helvetica][SIZE=-1]**[COLOR=#FF0000]4[/COLOR]**. Run ***chkdsk*** by typing _one_ of the the following commands where the cursor is blinking:[/SIZE][/FONT] 
[IMG]http://www.brazil-help.com/lil-nada.gif[/IMG][FONT=Arial,Helvetica][SIZE=-1]**[COLOR=#FF0000]a[/COLOR]**. **[COLOR=#000099]chkdsk c: /f /r [/COLOR]** and then press **[COLOR=#000099]<Enter>[/COLOR]** (see **[Notes]("http://www.brazil-help.com/chkdsk.htm#Notes")** below)[/SIZE][/FONT] 
[IMG]http://www.brazil-help.com/lil-nada.gif[/IMG][IMG]http://www.brazil-help.com/lil-nada.gif[/IMG][IMG]http://www.brazil-help.com/lil-nada.gif[/IMG]**[FONT=Arial,Helvetica][COLOR=#FF0000][SIZE=-1]OR[/SIZE][/COLOR][/FONT]** 
[IMG]http://www.brazil-help.com/lil-nada.gif[/IMG][FONT=Arial,Helvetica][SIZE=-1]**[COLOR=#FF0000]b[/COLOR]**. **[COLOR=#000099]chkdsk c: /f [/COLOR]** and then press **[COLOR=#000099]<Enter>[/COLOR]** (see **[Notes]("http://www.brazil-help.com/chkdsk.htm#Notes")** below)[/SIZE][/FONT] 
[FONT=Arial,Helvetica][SIZE=-1]**[COLOR=#FF0000]5[/COLOR]**. With either command, a message will appear that says: 
"chkdsk[I][COLOR=#000099] cannot run because the volume is in use by another process. 
Would you like to schedule this volume to be checked the next time the system restarts? <y/n>"[/COLOR][/I][/SIZE][/FONT] 
[FONT=Arial,Helvetica][SIZE=-1]**[COLOR=#FF0000]6[/COLOR]**. Type [COLOR=#000099]**y** [/COLOR][COLOR=#000000](for "yes") [/COLOR]and then press **[COLOR=#000099]<Enter> [/COLOR][COLOR=#FF0000]Caution[/COLOR][COLOR=#000000]: [/COLOR]**[COLOR=#000000]canceling an already scheduled ***chkdsk*** 
is a giant hassle so **be sure** you want to run ***chkdsk *_before_ **completing this step. [/COLOR]
[/SIZE][/FONT][FONT=Arial,Helvetica][SIZE=-1]**[COLOR=#FF0000]7[/COLOR]**. A message will appear that will say: *[COLOR=#000099]"This volume will be checked the next time the system restarts"[/COLOR]*[/SIZE][/FONT] 
[FONT=Arial,Helvetica][SIZE=-1]**[COLOR=#FF0000]8[/COLOR]**. Type **[COLOR=#000099]exit[/COLOR]** and then press **[COLOR=#000099]<Enter> [/COLOR]**to close the MS-DOS-style black screen window[/SIZE][/FONT] 
[FONT=Arial,Helvetica][SIZE=-1]**[COLOR=#FF0000]9[/COLOR]**. Reboot (restart) the computer as you normally would and ***chkdsk*** will automatically begin 
running _after_ your reboot (restart). While ***chkdsk*** is running, you will see a light blue window 
with a dark blue band at the top and bottom. ***Chkdsk*** will display the specific stage it is checking 
as well as the percentage of completion of the stage. You cannot do anything else on your computer 
while ***chkdsk*** is running. When ***chkdsk*** is finished, it will automatically reboot (restart) your computer.[/SIZE][/FONT] 

```

---

### Post by kansasnoob on 2010-12-16
Just out of curiosity I'd like to see the output of:

```
sudo parted /dev/sda print
```

Also, you're not this far yet, but I made some notes regarding the new live installer that might be helpful once you get that far:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

---

### Post by raac on 2010-12-16
This is the output for
 
 sudo parted /dev/sda print
 
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA Hitachi HTS54322 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Number Start End Size Type File system Flags
1 1049kB 250GB 250GB primary ntfs boot
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] 
 
 
 
I tried the chkdsk from windows, I checked everything, it took a while, I left it running and next thing I knew it was on windows already (Finished). So, I tried again and it's still showing the red dot in gparted.

---

### Post by kansasnoob on 2010-12-16
I'd hoped parted might show some info but it didn't, so in Gparted right click on /dev/sda1 and you'll see the option "Information" at the bottom of the window that opens like this:

[ATTACH]178626[/ATTACH]

And after clicking on "information" a new window will open like this:

[ATTACH]178627[/ATTACH]

I'm curious what it says?

---

### Post by kansasnoob on 2010-12-16
Aside from that I know I already linked to this:

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)

But if you spent hours reading all of that you'd see I've been working with Herman that maintains this site:

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

And we're getting very close on this:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

That guide shows how to use Gparted to create your partitions in advance and then installing to the exact partitions you've just created. The worst problem with that guide ATM is that in screenshot 034 we show /dev/sda5 as root and /dev/sda6 as SWAP, but from there forward root and SWAP "flip-flop". I'm sure Herman will get that fixed :)

But in your specific case I'd definitely use Windows own tools to resize your Windows:

[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

And then create the partitions for Ubuntu as shown here:

[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

Then if you keep track of the newly created device designations you should be fine. I just can't recommend using the "alongside" option ATM!

---

### Post by raac on 2011-01-09
Sorry for being out. Internet issues. I did chkdsk on Windows another time and still is not giving the option of install ubuntu alongside windows.
 
gparted is saying. 
 
WARNING: The disk has bad sector. This means physical damage on the disk surface caused by deterioration, manufacturing faults or other reason. The reliability of the disk may stay stable or degrade fast. We suggest making a full backup urgently by running 'ntfsclone --rescue...' then run 'chkdsk /f /r' on Windows and reboot it TWICE Then you can resize NTFS safetly by additionally using the --bad-sectors option of ntfsresize.
 
About the last part
 
am I suppose to go to the command line a type
 
ntfsresize --bad-sectors
 
??
 
Or how can I resize the disk??
 
 
Sorry for taking so long, I still haven't fixed it.

---

### Post by kansasnoob on 2011-01-09
Looks to me like a bad hard drive :(

---

