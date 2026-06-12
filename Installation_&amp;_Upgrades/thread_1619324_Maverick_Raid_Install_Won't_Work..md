---
title: "Maverick Raid Install Won't Work."
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by SeattleJoe98101 on 2010-11-11
My problem is that I want to install Maverick to a Raid 1 array, but I can't do it.

I dual boot Windows 7 and Ubuntu.  I have a Gigabyte (MA 790X-UDOP4)  motherboard with  fake Raid.  The motherboard has two controllers (one AMD and the other Gigabyte), but I  used the one from  Gigabyte, which I believe is equivalent to a  jmicron386.  I presently have a Raid 1  array on two 2 TB drives.  The  motherboard runs an AMD quad core chip.  All my installs are AMD 64bit.  The bios is set so the Gigabyte controller is set to RAID and the AMD controller to IDE.  

I tried several times to install with the Maverick CD (both desktop and   alternate --AMD 64 bit), but it failed every time.  When I got to the   partitioning page it would show nothing to partition.  Finally I tried   an old Karmic 64 bit CD.  That worked perfectly, and I was able to see   my raid array.  I then partitioned the drive with qparted and installed  Windows 7, although I allowed the Win 7 installer to format the drive, which probably changed the Linux partition.  The others, however, remained as gparted originally formatted them.  The CD also allowed me to use DD to copy a raid disk partiton  to an img  file on another raid partition.  Windows sees both of these  files OK and  in fact, Windows has no problem whatsoever with the Raid  partitions.

I then installed Karmic to a partition.  I tried upgrading to lucid, but   after the upgrade, it wouldn't function properly.  I then reinstalled   Karmic and did the upgrades (but not an upgrade to Lucid).  I then  began  having problems booting the partition.  On another (non-raid)  drive I have a Maverick installation.  It boots fine, but doesn't see  the raid; rather it sees the two mirror drives as separate.  Installing  kpartx appears to let the controller see the Raid array, but I can't read from it or write to it.  An installation of dmraid results in a statement  that it is already installed and is the latest version.

The question I have is whether there is a way to install the newer   versions of unbuntu on a fake raid array.  It looks to me like they   changed something after Karmic and dropped support for my type of Fake   Raid.  So is there some way I can get it to work.  And will Natty have   support for this type of fake raid?  If not, does one of the other Linux   distros have such support?  

Alternatively, is there something that I can do with Maverick to make it   work?  I have tried using the alternate CD and also installing kpartx   before trying an install.  This appears to let the system see the Raid   Array, but doesn't permit an installation to it. When I try, I reach a partitioning screen with nothing to partition unless I have a non-raid drive attached.  I never see the Raid drives as being available.  I don't know how to   install kpartx from the alternate CD and so I haven't tried that.

If replying, please assume that I know nothing and need step by step   instructions.  I should include the obligatory I'm a noob, although I have 30 years of experience with Windows (or DOS), and probably 2 years with Linux.  Please don't tell me to use Linux software RAID.  Even if it worked, it wouldn't meet my needs since I need to dual boot with Windows and let both have access to my drives.

Thanks in advance.

---

### Post by ronparent on 2010-11-11
I've read through you post with a sense of foreboding. From my own experience I thought that 10.10 had finally handled the fakeraid problems. But apparently some setups are still plagued.

> Alternatively, is there something that I can do with Maverick to make it work? I have tried using the alternate CD and also installing kpartx before trying an install. This appears to let the system see the Raid Array, but doesn't permit an installation to it. When I try, I reach a partitioning screen with nothing to partition unless I have a non-raid drive attached. I never see the Raid drives as being available. I don't know how to install kpartx from the alternate CD and so I haven't tried that.
My own experience was that I could both install to or upgrade to Maverick without needing any workarounds. Notedly in my case I didn't need the kpartx for gparted to recognize the raid! If in your case kpartx does permit gparted to see the raid, can you use gparted at this point to create an empty ext4 partition to install to. If so, while still booted to the live cd, can you start the install from the desktop icon and still see your target partition when you get to the partitoning step and select the manual partitioning option? If so you could then try selecting 'change' for the preformatted partition and designate it as ext4, do not check format and select the '/' mount point. If you can get this far you can install to it. All the files should get copied to the partition and it should be bootable. If it is not bootable that can be fixed. 

I've describe a workaround I needed for 10.04, but, if the situation is as you described it will probably work for you with 10.10. Post how it works out.

---

### Post by SeattleJoe98101 on 2010-11-13
Ron, thanks for your input, but your suggestions don't work for me.  Even after installing kpartx, gparted won't do anything besides let me see the partitions.  They all have red exclamation points and I can't resize them, format them, or do anything else.

I do, however, have some news which may assist the community and hopefully you, or some other person more sophisticated than I, can take it further than I can.  The news is that I managed to get a Maverick installation installed on a non-Raid drive to recognize a Raid array on two mirror (Raid 1) drives.  

I presently have a system that quadruple boots.  On an IDE drive I have Maverick and 
Windows Vista.  On a Raid 1 array I have Karmic and Win 7.  Windows --both vista and 7 -- are ok with the Raid.  So is Karmic as long as I don't upgrade.  Maverick doesn't see the array without kparted.  With it, it sees it but won't let you make changes, mount drives or do anything else.

In Karmic, dmraid -ay gives this output

  	 	 	 	p { margin-bottom: 0.08in; }  RAID set "jmicron_z" already active
 RAID set "jmicron_z1" already active
 RAID set "jmicron_z2" already active
 RAID set "jmicron_z3" already active


In Maverick its this:


   	 	 	 	p { margin-bottom: 0.08in; }  RAID set "jmicron_z                      #" already active
RAID set "jmicron_z                       #1" was not activated  RAID set "jmicron_z                      #2" was not activated
RAID set "jmicron_z              #3" was not activated


Although it prints as a pound sign here, the actual symbol was like a boolean truth table for AND.  It was a box with a one in the bottom right hand corner and zeroes in the others.  The numbers, 3 for example, were inside the box.  There were several spaces between the z and the sign.  I tried cutting and pasting into a mount command but that didn't work.  The box apparently functions as a return to beginning of line character.  Somehow, I'm not sure how, I managed to mount one or two of the drives once or twice, but I couldn't do it reliably and I wasn't sure how I managed it.


Meanwhile, in Karmic, I accidentally typed install dmraid and got back an answer that it needed the Maverick CD.  That reminded me of something we already know: the new version of dmraid doesn't work -- at least for me.  I checked the version numbers and found out that Karmic uses rc 15 and Maverick uses rc16 (so apparently do the initial versions of Natty).


So then I thought why not try and install the old version of dmraid in Maverick?  I uninstalled the Maverick version in 10 seconds, but it took me several hours to find out how to install the Karmic version.  Eventually I found it at [https://launchpad.net/ubuntu/+source/dmraid/1.0.0.rc15-6ubuntu2/+build/954950](https://launchpad.net/ubuntu/+source/dmraid/1.0.0.rc15-6ubuntu2/+build/954950).  I think the file I used was 



dmraid/1.0.0.rc15-6ubuntu2


So after installing the Karmic version in Maverick, dmraid -ay gives the same results as it does in Karmic.  Also, gparted looks normal and would, I think, permit me to resize a partition (I didn't try, but I'm pretty sure it would work because it allowed me to move the slider -- something I couldn't do before--plus all the red exclamation points were gone).  



The places menu doesn't really work right, and the individual mirror drives show up separately -- that is, each partition shows up twice.  And I can't mount them by clicking on the places menu.


What I can do, though, is use sudo to mount the /dev/mapper entry in a directory.  I can then use the GUI to examine the contents of the drive.  I've read from and written to the RAID partitions.  Windows doesn't seem to have a problem with the changes and I don't get any problems from the Bios when I boot up, indicating it doesn't think I've caused any problems with the mirroring.  



So . . . this isn't a complete solution to the problem.  I still don't know how to install Maverick to a Raid array.  I also don't know how to upgrade Karmic on a raid array so that it transitions to lucid or maverick without having its functioning dmraid overwritten by a non-functioning newer version.  And I don't know how to make the places menu function properly or to eliminate the double entries.  What I have is a semi functioning system that will permit me to read and write from Raid drives.  This solution might help some people if they dual boot from two drives, but it won't help someone who has a raid array as the only drive.  For that person -- at least based on my knowledge -- the only solution is to run Karmic or find a way to incorporate the Karmic dmraid into a Maverick install.  That may well be possible, but its beyond my knowledge.



As I said at the outset, I hope this will add to the fund of knowledge.  I'm also hopiing that someone more sophisticated than I will be able to take this further and solve all these problems.  If anyone out there does know a better way to do these things, by all means please leave a reply.



And if the Natty developers should see this, would you please get your act together and fix this problem?  Either return to the Karmic dmraid program or fix the Maverick dmraid code so it works for me and others who have the same problems (judging by internet there are a lot).  Given the fact that Natty is currently using the present Maverick code I'm not too hopeful about this, but I'm hoping the right person will read this and fix the problem.


P.S.:  One further note.  I have two raid controllers, one by Gigabyte (which dmraid sees as a jmicron) and one by AMD.  If I hook the gigabyte drives to the AMD controller and set it for RAID, it seems to function the same as the Gigabyte controller, although I haven't tried it since I made the changes to Maverick.  But prior to that, dmraid gave the same results regardless of which controller was used.

---

### Post by ronparent on 2010-11-13
Your post was very informative. It appears that, in your system at least, gparted has suffered a regression or won't work properly with 2Tb drives in a raid. I would suggest a bug report though the attention it could get would probably be limited unless someone else confirms your findings - more likely as more really large drives hit the market.

My exposure to fakeraid (I hate that term) from 7.04 through 10.10 has convinced me that a every new release will introduce you to a new situation. 10.10 looked very promising from my viewpoint but your experience shoots that apart. So now it appears that some people with high end drives will have to manually mount their raid partitions.

Enough ranting. I think you can do the most good posting a bug report.

---

