---
title: "Installing Karmic on a Windows 7 laptop"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by jfl on 2010-04-02
I am getting a laptop Lenovo G530 with Windoze 7 installed.
Since I am not the sole user of the machine, W7 has to stay.
I want to install Karmic on the laptop with dual boot, what is the proper procedure ?
I understand I could screw up very easily ;)
I did install Dapper (a long time ago) on a Win2000, not easily, but not traumatic either, and the setup has taken all the upgrades to Karmic without bothering Win2000. Problem is, I cannot remember, even remotely, what I did, and anyways,it probably doesn't apply to W7.

I am sure there are threads that would answer the question, but I am not good with the search utility on this forum.

In short, I need a **how-to** **install Karmic on a Windows 7 laptop**

Thanks !!!

---

### Post by NightwishFan on 2010-04-02
Simple!

[LIST=1]
[*]**Defragment** and check the drives for errors.
[*]Right click on 'My Computer' and hit manage. Go to the Windows Disk Utility (Partitioner thing). Shrink Windows enough to give free space for Ubuntu at the **end**. Windows needs to be first. 20+ GB should be good.
[*]Download and burn an Ubuntu CD, check it for errors before you install. Run the live session see how your hardware works.
[*]If you are satisfied, run the installer and choose to install Ubuntu in the 'free space'. It should partition automatically.
[*]Boot and enjoy.
[/LIST]

---

### Post by Bluesan on 2010-04-02
Adding...

[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)

---

### Post by Mark Phelps on 2010-04-02
Just be sure to note that both NightwishFan and the linked guide mention using only the Win7 Disk Management utility to shrink the Win7 OS partition.  

If that doesn't shrink enough for your satisfaction, do NOT resort to using the Ubuntu installer or GParted to shrink the partition.  Doing so runs the risk of corrupting your Win7 OS so it won't boot anymore.

And before you do ANYTHING, you should boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD.  That will come in handy later if you ever need to repair your Win7 boot.

---

### Post by jfl on 2010-04-02
**[FONT="Comic Sans MS"][SIZE="5"]Thanks !!!!!!![/SIZE][/FONT]**

---

### Post by NightwishFan on 2010-04-02
I assume you got it working. Have fun!

---

### Post by Herman on 2010-04-02
> If that doesn't shrink enough for your satisfaction, do NOT resort to using the Ubuntu installer or GParted to shrink the partition. Doing so runs the risk of corrupting your Win7 OS so it won't boot anymore.It doesn't hurt to recommend shrinking Winodws with its own disk management solution, then if something goes wrong it has nothing to do with Ubuntu.
You should also recommend people reboot once or twice to make sure Windows is still okay and hasn't corrupted itself, as most resizing failures are actually due to hardware problems or gross user incompetence rather than faults in the software itself.

I have tried out the Windows 'Disk Management' utility and it worked for me, but I usually use the inbuilt partitioner in the Ubuntu installer or GParted and I have not yet experienced any problems. 
I have yet to see any links to bug reports against either the inbuilt partitioner or GParted, (when used properly), in which Ubuntu or GParted has actually corrupted an NTFS partition.

It's a wonder that anybody is still brave enough, (or foolish enough), to install Ubuntu with Windows at all if they are told the software will be faulty and dangerous before they even get a chance to try it. 
Mind you, warnings against the partitioner, whether justified or not, don't necessarily reflect on the entire operating system. 
However, if I was told to avoid a certain product in a bakery or a butcher shop for an analogy, as the shop sold a product that was known to contain poison, I would probably avoid the whole shop completely and get my meat or bread from somewhere else.
So by implication, warnings against software that's used by Ubuntu can turn people away from the operating system itself.

Therefore I feel that people should be careful about how they convey information in a web forum which is after all, dedicated to open source and free software and particularly to Ubuntu. 

It's really not fair when it's so easy to negate the good, hard work of so many people who spend hours trying to make this operating system the best when someone can undo all that hard work with only a few words.
It's a lot easier to destroy something than it is to create something.

---

### Post by NightwishFan on 2010-04-02
True, however Microsoft makes it's system picky on purpose. Any third party tool runs a high risk of causing it to fail.

---

### Post by Herman on 2010-04-02
So, you think ntfsprogs is a waste of time then? Or even, dangerous?

---

### Post by NightwishFan on 2010-04-02
No I do not think so. However the user can understand the risks and 'no warranty' attitude of what they are doing. Any software, even Microsoft's own tools can cause problems. I am honor bound to keep the user aware of such. Also to give them a path that is in their power I feel is likely to succeed.

---

### Post by Herman on 2010-04-03
> **Defragment** and check the drives for errors.
Right click on 'My Computer' and hit manage. Go to the Windows Disk Utility (Partitioner thing). Shrink Windows enough to give free space for Ubuntu at the **end**. Windows needs to be first. 20+ GB should be good.
Download and burn an Ubuntu CD, check it for errors before you install. Run the live session see how your hardware works.
If you are satisfied, run the installer and choose to install Ubuntu in the 'free space'. It should partition automatically.
Boot and enjoy.

I don't see too much to object about in your post, and in fact I applaud you for suggesting 'check the drive for errors'.
It's possible that the reason why I have such phenomenal good luck with our Ubuntu partition editors could partially be attributed to the fact that I make it a habit to run CHKDSK /R first. I think that's probably a good idea before Windows utilities as well.

It was your sidekick's follow-up post with the uppercase letters that attracted my attention more than anything. It's okay to warn people about possible risks, but we shouldn't need to scare the heck out of poor Windows users, they're scared enough already, poor things.

---

### Post by TheNerdAL on 2010-04-03
Mark [SOLVED] if solved. :)

---

### Post by Mark Phelps on 2010-04-03
> **Herman said:**
> It was your sidekick's follow-up post with the uppercase letters that attracted my attention more than anything. It's okay to warn people about possible risks, but we shouldn't need to scare the heck out of poor Windows users, they're scared enough already, poor things.

If you're referring to ME, my use of uppercase letters was intentional.  We get post after post her from folks who trashed their Win7 setups -- without even knowing that in 5 minutes or less, they could have easily made a recovery CD.

If my use of uppercase letters pauses them to take that five minutes and burn a Recovery CD, it's better for them to have that CD and not need it, than to make some simple mistake and be left with an expensive machine which won't boot.

It's no different than other folks telling people to make a backup before they try something risky -- and I don't see you going after them.

---

### Post by NightwishFan on 2010-04-03
If anything **I** am the sidekick. ;)

---

### Post by Herman on 2010-04-03
Originally posted by Mark Phelps
> Just be sure to note that both NightwishFan and the linked guide mention using only the Win7 Disk Management utility to shrink the Win7 OS partition. 

If that doesn't shrink enough for your satisfaction, do NOT resort to using the Ubuntu installer or GParted to shrink the partition. Doing so runs the risk of corrupting your Win7 OS so it won't boot anymore.

And before you do ANYTHING, you should boot into Win7 and use the Backup feature to create and burn a Win7 Repair CD. That will come in handy later if you ever need to repair your Win7 boot.Apparently the Windows Vista Disk Management utility suffers from two limitations, it can't resize the NTFS partition when the file system is fragmented and it doesn't seem to be able to move the Windows 'page file'.

I agree with your suggestion about making a backup,  but as for the warnings against using open source software to work on it, you know as well as I do that what you are saying is not the whole truth.
Windows will boot just fine after resizing with the Ubuntu installer's partitioner because that one doesn't move the start of the Windows partition and it will also boot just fine after resizing with GParted as long as the user doesn't allow GParted to move the partition to align it with cylinder boundaries.

We went through all of this almost exactly one year ago in thei thread,       [[COLOR=#980101][ubuntu][/COLOR] Is Partition Magic Reliable?]("http://ubuntuforums.org/showthread.php?t=1107391&highlight=partition+magic+reliable")  and nobody could link me to any valid bug reports then and I still think that a year later you would be doing some scratching to find one that's clearly attributable to GParted and not user error or hardware problems. 

Your Windows Disk Management tools are subject to hardware problems too, although maybe they're designed a little more with stupid users in mind. Unfortunately we don't get to see bug reports against the Windows Disk Manager because it's a proprietary operating system and Windows Tech support wouldn't be likely to publish them, so it's hard to know if Windows Disk Management is any more reliable or not. I doubt it.
If the truth could be know, there is probably at least an equal risk using the Windows resizer.

While I was searching for that other thread I linked to (above), I chanced across another one you starred in, here, [Re: Can't resize ntfs partition]("http://ubuntuforums.org/showthread.php?t=871687&highlight=partition+magic+reliable&page=2"), and I wonder how many similar threads you have around here.
In that thread you admitted you've never even tested the open source resizer yourself.

Well I have and still do spend a lot of my time testing partition editors and installers and I haven't found any problems with Ubuntu or GParted.

If you could just tell the truth and say you *don't know for sure if open source software is safe* with resizing NTFS, that would be okay and probably wouldn't upset anybody, but you're going around implying the open source software is dangerous, and that's simply not the truth.

---

### Post by NightwishFan on 2010-04-04
We did not say it was dangerous, I merely stressed it was my personal recommendation that the poster use his the tools available for Windows. He has a license for this tool. **From experience** I have had problems using the Linux partitioning tools that resulted in an unbootable Windows. It was a great embarrassment for me. I do not blame the software I blame my lack of foresight on that particular issue. However, especially on a newer Windows I would think using a built in tool would be more reliable. Philosophically? No! Practically? Yes.

In either case, when modifying an operating system that we do not know the code for it honestly seems safe to use their built-in tools to do so. I will not advise a user to try something that I have not done myself (Shrink Windows 7 from Linux) or has proven to be unreliable in the past (Shink NTFS leads to Windows Disk Error)

I have faith in open source software but when it is not my neck on the line I will go with the route I know will have the least amount of variables.

---

