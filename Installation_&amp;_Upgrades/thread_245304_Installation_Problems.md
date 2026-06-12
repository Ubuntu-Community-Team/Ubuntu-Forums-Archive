---
title: "Installation Problems"
date: 2006-08-27
forum: Installation &amp; Upgrades
---

### Post by xjosie729 on 2006-08-27
Here is how my installation went: [LIST]
[*]I chose my language
[*]I set my time zone etc
[*]I selected my keyboard layout
[*]I entered some information about me
[/LIST]

I did not get to choose which partition to use,
Then A loading window popped up saying "starting the partitioner"
and I was asked how I want to partition the disk. The options were: [LIST]
[*]Erase entire disk: IDE 1 master (hda) - 80.0 GB ST380011A
[*]Use the largest continuous free space
[*]Manually edit partition table
[/LIST]Since none of the choices were what I intended to do (install on the 4th partition with the swap on the 3rd partition), 
[B][U]I chose to Manually edit partition table.
It started loading, but never got to the next page.[/U][/B]


Any help would be appreciated.

--------------
The first time I installed, it was successful, but after it got to about 15%, I left the computer, and when I came back just a little while later, the installation window was gone, and there wasn't prompt for restarting or keep using the live cd, so I tried installing again, and again. But I got the results above^^.

---

### Post by randell6564 on 2006-08-27
> **xjosie729 said:**
> Here is how my installation went: [LIST]
[*]I chose my language
[*]I set my time zone etc
[*]I selected my keyboard layout
[*]I entered some information about me
[/LIST]

I did not get to choose which partition to use,
Then A loading window popped up saying "starting the partitioner"
and I was asked how I want to partition the disk. The options were: [LIST]
[*]Erase entire disk: IDE 1 master (hda) - 80.0 GB ST380011A
[*]Use the largest continuous free space
[*]Manually edit partition table
[/LIST]Since none of the choices were what I intended to do (install on the 4th partition with the swap on the 3rd partition), 
[B][U]I chose to Manually edit partition table.
It started loading, but never got to the next page.[/U][/B]


Any help would be appreciated.

--------------
The first time I installed, it was successful, but after it got to about 15%, I left the computer, and when I came back just a little while later, the installation window was gone, and there wasn't prompt for restarting or keep using the live cd, so I tried installing again, and again. But I got the results above^^.

HI!

What are you running at the moment?  (What OS?) Please post a little more info about your system.

How many HD's, How they are setup, Do you have an 'Hdb', or just an Hda?
"use the largest continuous free space" is what you want if you have another OS on the same drive.  

But first, tell us more about what you are working with!

---

### Post by xjosie729 on 2006-08-27
1. I'm using Windows XP SP2
2. I don't know what Hdb and Hda is.
3. I'm pretty sure I only have one hard disk
4. I tried "use the largest continuous free space" but it gave me the warning of "unusable free space"

---

### Post by taurus on 2006-08-27
Are you using the desktop CD (LiveCD)?  Maybe you want to use the alternate CD since it gives you more control of what you want to do with your partition...

---

### Post by randell6564 on 2006-08-27
> **xjosie729 said:**
> 1. I'm using Windows XP SP2
2. I don't know what Hdb and Hda is.
3. I'm pretty sure I only have one hard disk
4. I tried "use the largest continuous free space" but it gave me the warning of "unusable free space"

OK, it sounds like this is your first experience with Linux, so I'll try and be sensative to that.  "hda" and "hdb" is how Linux (at least Ubuntu), identifies your HD's (Hard drives)

On my PC, I have a 120GB Master HD, and a 20GB slave HD.  Linux refers to my Master as Hda, and my slave as Hdb.

In your situation, you have only one HD housing Windows XP. You have "Free Space", but is it enough to house Linux?

I am a full time Linux user, so I cant remember exactly how to get there, using windows, but go into your Disk manager and tell me how much free space is there.

---

### Post by xjosie729 on 2006-09-03
> **randell6564 said:**
> OK, it sounds like this is your first experience with Linux, so I'll try and be sensative to that.  "hda" and "hdb" is how Linux (at least Ubuntu), identifies your HD's (Hard drives)

On my PC, I have a 120GB Master HD, and a 20GB slave HD.  Linux refers to my Master as Hda, and my slave as Hdb.

In your situation, you have only one HD housing Windows XP. You have "Free Space", but is it enough to house Linux?

I am a full time Linux user, so I cant remember exactly how to get there, using windows, but go into your Disk manager and tell me how much free space is there.
I have plenty of free space, and I made a 30G partition for it.

---

### Post by randell6564 on 2006-09-03
> **xjosie729 said:**
> I have plenty of free space, and I made a 30G partition for it.

So then you want to choose "choose the largest continuous free space" when you get to the partitioner.  Then ubuntu will probably offer an ext3 partition and a swap partition.  If your not familiar with partitioning then just let ubuntu install the OS onto your 30GB partition the way she does it by default.

---

### Post by glotz on 2006-09-03
I had a similar experience FWIW, an install that never finished. The only solution that worked for me was to install the older version, 5.10, and then letting it upgrade itself... Now it's working perfectly though, on the other hand.

(You'll need a FAST network connection for this however, you'll be downloading some 400(?) megs)

---

### Post by xjosie729 on 2006-09-03
> **randell6564 said:**
> So then you want to choose "choose the largest continuous free space" when you get to the partitioner.  Then ubuntu will probably offer an ext3 partition and a swap partition.  If your not familiar with partitioning then just let ubuntu install the OS onto your 30GB partition the way she does it by default.

If I choose that, I get an error message saying "unusable free space". I also manually changed the partion to ext3, but it's still unusable according to Ubuntu.

---

### Post by randell6564 on 2006-09-03
> **xjosie729 said:**
> If I choose that, I get an error message saying "unusable free space". I also manually changed the partion to ext3, but it's still unusable according to Ubuntu.
Now THATS strange!
I have installed and REinstalled, using several different drive configurations (one master, one master one slave), Several partitions on one drive, and never had this problem!

You ARE setup with just ONE 80GB Ide HD correct?  Windows is installed on the beginning of this drive as NTFS?  And You have free space (30GB) at the back end of this 80GB HD correct? 

Do you know how to get a screenshot of your HD from your windows disk manager?  Please post that.  I will go looking for a how to on taking screenshots in windows for the time being.

---

### Post by xjosie729 on 2006-09-03
> You ARE setup with just ONE 80GB Ide HD correct?I think so


> Windows is installed on the beginning of this drive as NTFS?I'm pretty sure (at least I'm sure it's installed as NTFS)


> And You have free space (30GB) at the back end of this 80GB HD correct?Yes


> Do you know how to get a screenshot of your HD from your windows disk manager?No

---

### Post by randell6564 on 2006-09-03
> **xjosie729 said:**
> I think so


I'm pretty sure (at least I'm sure it's installed as NTFS)


Yes


No

Ok.,You should know wether or not you have more than one HD. 

There IS a way to take a screenshot of your HD in Windows.  I'm stil looking for it!  Bare with me My Friend!

Are you able to 'Manually partition' your 30GB space with the Ubuntu CD?

I'm starting to wonder if you have a corrupt HD!

---

### Post by jim-campbell on 2006-09-03
I wish I new how to post a question:confused:
I know this is not the place or manner but I am truly confused..Jim

---

### Post by randell6564 on 2006-09-03
> **jim-campbell said:**
> I wish I new how to post a question:confused:
I know this is not the place or manner but I am truly confused..Jim

HELLO!  Welcome to the Linux Ubuntu forums! "confused" Is OK My Friend!

Just go to the forum that closely matches what you are needing help with.
click on it, then click 'New Thread'.  In the 'Title' enter something that gives an idea of what your problem is.  Then in the 'Message' box describe your problem!

Don't let it get you discouraged!

---

### Post by Luvis8 on 2006-09-04
Hi There,
I had the exact same problem, Ubuntu would not install, the install window simply vanished from the screen.

When I tried to reinstall Ubuntu (which I attempted several times) I noticed that only the swap drive had been formated but not the root drive (I had selected "Format" in the manual partition menu).

After numerous unsuccessfull attempts to install Ubuntu I gave up and installed Freespire in the same root directory.
Eventually I decided to try installing Ubuntu again, this time the drive had already been formated by Freespire (I told Ubuntu to reformat the drive anyway) and guess what... this time it worked.

I think there is a problem with Ubuntu not full or properly formating the root drive.  This problem could be overcome by formating the drive yourself, in the proper format, before installing Ubuntu.

I hope this helps.
Please let me know if this works for you.

---

### Post by glotz on 2006-09-04
Josie, to get the screen cap, open the windows you want included in the shot and hit print screen button. Then open some picture handling software and paste. There you go.

jim-campbell, try this link, it's the beginner talk forum new thread button [http://www.ubuntuforums.org/newthread.php?do=newthread&f=73](http://www.ubuntuforums.org/newthread.php?do=newthread&f=73)

---

### Post by randell6564 on 2006-09-04
> **glotz said:**
> Josie, to get the screen cap, open the windows you want included in the shot and hit print screen button. Then open some picture handling software and paste. There you go.

jim-campbell, try this link, it's the beginner talk forum new thread button [http://www.ubuntuforums.org/newthread.php?do=newthread&f=73](http://www.ubuntuforums.org/newthread.php?do=newthread&f=73)
"Print Screen!" (Prt Scrn) thats it! But I thought that you had to hold down another key at the same time. Like 'Alt' or something in Windows.

Another thing OP. While your in your Windows disk manager, try formatting your free space as Fat32.  Then go back and boot to your ubuntu CD and see what the partitioner gives you this time. It should identify your NTFS as something like hda1 and your 30GB as hda2

---

### Post by xjosie729 on 2006-09-04
How do I open the disk manager?

---

### Post by randell6564 on 2006-09-04
> **xjosie729 said:**
> How do I open the disk manager?

I have not used windows in quite a while, but I know you can get there through control panel. I think it's under something like 'Administrator Tools' You will know when you are there.  You will be shown a graph of your drive and it's partitions.

---

### Post by glotz on 2006-09-05
> **randell6564 said:**
> "Print Screen!" (Prt Scrn) thats it! But I thought that you had to hold down another key at the same time. Like 'Alt' or something in Windows.Holding alt (or whatever it was) down will only capture the active window, if memory serves.

---

### Post by xjosie729 on 2006-09-06
Here is the screenshot. I'm quite surprised to see that the two partitions I've made doesn't have any file systems, since I am sure that I edited the 30G one to be ext3 and the other to be something else (which I cannot remember).

---

### Post by randell6564 on 2006-09-06
> **xjosie729 said:**
> Here is the screenshot. I'm quite surprised to see that the two partitions I've made doesn't have any file systems, since I am sure that I edited the 30G one to be ext3 and the other to be something else (which I cannot remember).

You did it! That helps alot! My suggestion is that you erase all that free space, format it as one Fat32 partition, reboot into your Ubuntu CD and try the install again.  Ubuntu will recognize the fat32.  Then you can partition it the way that you want.

---

### Post by randell6564 on 2006-09-06
> **xjosie729 said:**
>  I'm quite surprised to see that the two partitions I've made doesn't have any file systems, since I am sure that I edited the 30G one to be ext3 and the other to be something else (which I cannot remember).

Windows does not like Linux.  Windows will not recognize an Ext3 FS.

They are Ext3, but that will not be shown when looking at your HD from your windows disk manager.

---

### Post by xjosie729 on 2006-09-07
You mean I should erase Windows?

---

### Post by randell6564 on 2006-09-07
> **xjosie729 said:**
> You mean I should erase Windows?

No my friend!  I mean erase your free space. The three partitions that you see that are not identified as Ext3.  Erase them so you end up with only two partitions, Windows and one unallocated space.  Then format that unallocated space to Fat32.

Then reboot to your Ubuntu CD, and you will see your Windows partition and your Fat32 partition. That way there is no confusion.  Then repartition the Vfat to how you want it.

---

### Post by xjosie729 on 2006-09-08
> **randell6564 said:**
> No my friend!  I mean erase your free space. The three partitions that you see that are not identified as Ext3.  Erase them so you end up with only two partitions, Windows and one unallocated space.  Then format that unallocated space to Fat32.

Then reboot to your Ubuntu CD, and you will see your Windows partition and your Fat32 partition. That way there is no confusion.  Then repartition the Vfat to how you want it.

I can't delete all three of them. One (D) contains some Windows files for recovery, and I really don't want to remove them.

---

### Post by Average Joe on 2006-09-08
> **xjosie729 said:**
> I can't delete all three of them. One (D) contains some Windows files for recovery, and I really don't want to remove them.

I think you should delete only the partition that you want to use for linux (the 27 GB one). As far as I can remember you can right-click on the partition and select delete. I think it will then show up as "free space" or  as "unallocated" as the 1.15 GB partition. Maybe you should explicitly delete the 1.15 GB partition too.

I am dual booting Windows XP and Ubuntu, and I had to do this to have Ubuntu recognize some free space on my hard disk.

---

