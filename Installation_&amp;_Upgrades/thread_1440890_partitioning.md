---
title: "partitioning"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by iggy pop on 2010-03-28
The wife has a computer which runs Windows 7 and i have finally managed to persuade her to let me partition the hard drive and share the computer between Windows 7 and Ubuntu 9.10. Trouble is i have never partitioned an hard drive before. So could anyone point me to a very easy to follow tutorial which covers partitioning an hard drive please.

---

### Post by derekeverett on 2010-03-28
Unless your planning on re-installing win7 the easiest way would be to shrink your win7 volume.

quick instructions... 
right click on my computer.
select "manage"
choose "disk management" in the side bar
select your c: drive and shrink it.

Remember 1024 mb in one gigabyte.

I would google for better instructions before you do it though.

That's just to give you an idea.

This way when you install Ubuntu choose "install in the largest free space"

---

### Post by garvinrick4 on 2010-03-28
> **iggy pop said:**
> The wife has a computer which runs Windows 7 and i have finally managed to persuade her to let me partition the hard drive and share the computer between Windows 7 and Ubuntu 9.10. Trouble is i have never partitioned an hard drive before. So could anyone point me to a very easy to follow tutorial which covers partitioning an hard drive please.

Start by reading this link: gparted is the software on the Ubuntu disk that you will use. It is not hard just focus.

[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by iggy pop on 2010-03-28
Thanks for the replies both

---

### Post by stlsaint on 2010-03-28
I would STRONGLY suggest using windows disk management as stated in the first reply to shrink the windows volume instead of gparted. Though gparted can do the job it is just "better practice" to use windows disk management when handling ntfs partitioning if you can. Now if you were to have a blank hdd (which is not the case with you) than gparted would do just fine.

---

### Post by oldfred on 2010-03-28
+1 on stlsaint recommendations.

gparted works fine for XP, but often moves the start of Vista or 7 partitions which then require repairs. For all systems it is better to make it two steps even though you can do it all from the ubuntu installer. The two steps are resizing windows and rebooting the resized windows to make sure it sees the new size , it may want to run chkdsk or other repairs but should work. Then you can go back and install Ubuntu in the free space.

[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Herman on 2010-03-28
[IMG]http://members.iinet.net.au/%7Eherman546/p22/012.png[/IMG]

I agree with derekeverett, garvinrick4, stlsaint, and oldfred.


[LIST]
[*]It's okay to use Windows Vista or Windows 7 partition manager, Windows XP version had a bad reputation for corrupting partition tables but that seems to be fixed with Vista and 7.
[*]It's okay to use the Ubuntu installer's inbuilt partiion editor as that does not move the start of the Windows partition.
[*]It's okay to use GParted as long as we remove the tick mark from the 'align to cylinders' checkbox.
[/LIST]
There was a problem with Windows Vista because it was the first operating system to depart from the conventional cylinder alignment and put its boot sector at the 1MiB mark. That had mostly been fixed with Windows 7 because most Windows 7 installations have a separate /boot partition.

Incidentally, if you're creating a new partition GParted can also set a boot sector at 1 MiB if you set it to in the 'free space preceding' box you can see in the illustration above.

---

### Post by Herman on 2010-03-29
[https://help.ubuntu.com/community/Re...7%20Partitions]("https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions")
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

It appears as if some people have been filling the Ubuntu Community Docs up with F.U.D. !

Whilst I don't object to people using the Windows tools if they want to, I do object to people running down Ubuntu and the Ubuntu installer if it's not true.

Here  I go again searching and reading through hundreds of bug reports in launchpad to try to find out if there's actually any factual basis behind this stuff.

I went through this process a year or so ago and spent many hours testing in my own computers here, plus others I install in belonging to freinds and relatives and I wasn't able to reproduce any problem with the Ubuntu installer.
Maybe with GParted, fair enough, (if somebody fails to remove the check mark), but even when I have done that (delberately), it has always been easy to fix.
The above links seem to be referring the the Ubuntu installer, which to the best of my knowledge does not move the start point of any partition and is perfectly capable of resizing NTFS.

Can anyone link me to one or more actual bug reports on this subject?

---

### Post by presence1960 on 2010-03-29
> **Herman said:**
> [https://help.ubuntu.com/community/Re...7%20Partitions]("https://help.ubuntu.com/community/RecoveringWindows#Resizing%20Windows%20Vista%20/%207%20Partitions")
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

It appears as if some people have been filling the Ubuntu Community Docs up with F.U.D. !

Whilst I don't object to people using the Windows tools if they want to, I do object to people running down Ubuntu and the Ubuntu installer if it's not true.

Here  I go again searching and reading through hundreds of bug reports in launchpad to try to find out if there's actually any factual basis behind this stuff.

I went through this process a year or so ago and spent many hours testing in my own computers here, plus others I install in belonging to freinds and relatives and I wasn't able to reproduce any problem with the Ubuntu installer.
Maybe with GParted, fair enough, (if somebody fails to remove the check mark), but even when I have done that (delberately), it has always been easy to fix.
The above links seem to be referring the the Ubuntu installer, which to the best of my knowledge does not move the start point of any partition and is perfectly capable of resizing NTFS.

Can anyone link me to one or more actual bug reports on this subject?

Hi Herman. I remember having this discussion with you about a year ago on a thread. Very informative indeed! I did some testing of my own with Vista and the results were mixed. With windows disk management utility and with the Ubuntu installer it worked flawlessly. For reasons I have never tried to figure out with gparted Live there seemed to be instances where the resize made Vista unable to boot. Of course the fix is very easy with the vista install DVD or the Vista Recovery CD from NeoSmart. I tried each method 10 times. The windows utility and ubuntu installer were flawless, but the gparted Live resulted in 4 out of 10 times Vista not being able to boot after the resize.

Since I do not know why this happens I prefer to err on the side of caution when helping someone new and suggest resizing Vista/7 with windows disk management utility. Even though the fix for the resulting non-boot of Windows is easy to us to someone inexperienced it may be perceived as a tragedy to them.

I have not tried it with windows 7 yet.

So yes your unchecking of the box does appear to work in most cases. But with relative newbs I prefer to recommend using windows to resize to avoid troubles.

---

### Post by Herman on 2010-03-31
I agree that it's easier to tell newcomers to just shrink their partition with the Windows Vista or Windows 7 Partition Manager. It's easier for them, (except it requires defragging first).
The good thing about that is then if things do go wrong, problems cannot be blamed on Ubuntu or open source software.
If people only say to resize with Windows own tools that would be fine, I'm okay with that.

On the other hand though, I still cannot find any evidence to condemn the Ubuntu installer's inbuilt version of GParted.
Neither can I find anyone who claims GParted Partition Editor in the Ubuntu Live CD ruined their Windows boot when the check is removed from that checkbox.

I have never had a problem myself with resizing Vista or 7 either with the Ubuntu installer or with GParted.
Maybe I'm just lucky, or maybe it's because I always run CHKDSK /R first. 
It seems to be popular to advise Windows users to defrag, which might be necessary before using the Windows resize utility, I wouldn't know for sure. I don't think defragging matters to GParted or the the Ubuntu Installer. I think running CHKDSK /R or even CHKDSK /F could be helpful though.

Once again, can anybody link me to threads or bug reports where,

[LIST]
[*]the Ubuntu Installer's partition editor has moved the start point of the Windows partition?
[*]resizing an NTFS partition with the Ubuntu installer or with GParted in Ubuntu Live CD has corrupted the NTFS MFT?
[/LIST]
All I have read so far either involve problems that were already present in Windows before the user decided to try Ubuntu, gross user incompetence, hardware faults and other circumstances that are not clearly identified.

---

### Post by Herman on 2010-03-31
It appears to me that the Ubuntu Community Docs pages,  has been edited by someone advertising a proprietary third party partition editing program.
> Unlike Windows XP, Vista and Windows 7 does not allow you to move the MFT (Master File Table) that controls the NTFS file structure. Inexplicably, Microsoft locates this near the middle (or end) of the partition, somewhat limiting the ability to resize (shrink) the partition completely. Although you will be able to gain some hard drive space from the "Shrink Volume" command, it will be limited. 
I knew of no partition software that could move the MFT to a different place on the hard drive safely, but [this tutorial]("http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/") suggested that Perfect Disk worked for this purpose. I therefore tried the trial version of Perfect Disk, and it seemed to work for me very nicely. I was able to shrink my Vista partition, using the steps in the tutorial (and Perfect Disk), from 300 Gb to 74 Gb. This was perfect for me. 

---

