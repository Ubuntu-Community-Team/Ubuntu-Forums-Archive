---
title: "Don;t Trip and Fall With VirtualBox"
date: 2010-07-09
forum: Installation &amp; Upgrades
---

### Post by oldefoxx on 2010-07-09
I've said many times that Ubuntu, plus VirtualBox, create an almost ideal environemtn in which to set up nd use a Windows client.  The client is well surrounded by the other two, do you have a secure and stable envionment for the two operating systems to work with each other on a single PC,\\

Unfortunately, I now know firsthand that the letest versions of borh, in conjunction with each other create a situationh that is not desireable.  Why this suddenly happened I don,t really know,but I think it has to do
with some change in VirtualBox rather than in Ubuntu.

As far as I know, it only affects some laptops and notebooks.  Why just these?  Because it involves the fact that these may have two network adapters rather than just one, the first for wired connectivity and the second when going wireless.  It may be made more complicated if the wireless adapter actually uses a USB interface for access from the internal side.

You rarely have both wired and wireless working at the same time.  There is generally no real need to do so.  And you would expect that whichever way that the host connects up, that is the way the client will connect as well.  This is because the client' connectivity is merely a conveyance by VirtualBox between the host and the client.

But what seems to be happening now is that VirtualBox is not just conveying traffic between the two, but is asking the host for whichever adapter the client is to have the use of.  In passing this to VirtualBox, Ubuntu is releasing it from its own use,  The client must then set up a network connection tailored to that adapter.  If it is wireless, and there is no cable attachment, then only the host or the client can make use of the internet connection.  This is radicslly different than before when both could share the same connection.
, 
In my case, with the USB interface, WQindows 2000 seems unable to make an association between USB and internet functions.  The adapter can be reported as working properly, but no traffic moves back and forth.  I am forced to drop efforts to connect wirelessly and go cable only,  I might be able to connect wirelessly to Ubuntu and leave the wired connection for use by the client,  Or somehow convey messages between host and client so that only the wireless connection can serve both.

I'm not thrilled by this at all.  It is made harder by the fact that neither Ubuntu nor Windows 2000 has adequate tools provided to deal with USB devices unless they somehow get mounted first.  If the devices is already plugged in and powered up beforehand.  If this occurs, you will likely have to unplugged or powered down and up to get it recognized.

I am not thrilled by this find by any means.  I report it here because I have been such a strong advocate of VirtualBox here previously.  My first concern was where VirtualBox might go under Sun Microsystems, but it seemed to stay the same course.  Now that it is under Oracle,and this change has crept in, I might have to give serious thought to a different VM Manager.

You might have different findings, different conclusions, or specific recommendations to make.  This might be a good place to air all that.

---

### Post by rpete on 2011-01-13
Oldefoxx, I am a relative novice to Ubuntu, but was convinced to abandon Windows.  Recently I upgraded to Lucid and am very happy with it.  Since moving to Ubuntu in 2008 I have managed to find a substitute that was equal or superior to Microsoft software programs.  Until recently, when I realized the best program for qualitative data analysis is Nvivo9 by QSR made only for Windows and Mac.  I found out about Virtualbox and I was happy to think my problem was solved.  I could run Nvivo from a virtual Windows 7 system within my Linux.  I downloaded Virtualbox and started it, but realized I needed a CD with Windows on it.  However, whatever I did caused me to lose my Internet connection and  your post caused me to think it may be related.  What I don't understand is I never got Virtualbox actually working, never used the virtual Windows system.  

Any ideas on what might have happened?  I have a DSL connection and am able to pull out the connection from the 10.04 computer and plug it into my netbook with 10.l0 and the Internet connection works fine.  This computer is my backup, though.

---

### Post by oldefoxx on 2011-01-13
Well, let's see what I can add that might be of some value.  First, while many go for VirtualBox OSE, I believe it still lacks support for USB, which you get in the licensed version from Oracle.  The license version is free for individual use, and there is a version for every flavor of Ubuntu.  One thing to follow up with is make sure a vboxusers group is added often with group number 123, and that you as user are checked under properties to make use of the USB feature.  If this is new turf for you, just go to Users and Groups under System/Administration.  You want to make changes, and your password is good for this purpose.  If you are working pre-9.04, you may have to search out details on getting USB enabled at boot time for use with VirtualBox.  Several articles tell you exactly how online.

Next, you create a New client, name it and pick the right version of Windows.  This controls some particulars, like which version of the GuestAdditions is available to run.  GuestAdditions make Windows run faster and cleaner, and are a big help to hi-res graphics.  Don't expect real time game playing though, because the4e time slices are now split between the host, VM, and the client.  But it is not bad, all things considered.

You create the client's virtual hard drive or use an existing one.  If creating, you are left with the responsibility of getting Windows onto it, which can be done from an ISO image on your hard drive or via a CD Install disk.  Technically, go back far enough and you can do this from floppy disks.  The idea though is that once you create a client, you have to go to the Storage choices under Settings for it to tell VirtualBox what to make available to the Client from the Host side.  Settings are pretty much set when the client is running, although some changes are allowed through the Devices button in the VirtualBox frame.

So you don't have the Windows Install CD.  That is not uncommon now, but there are ways to address this.  First, you may have the option to order them at a fair price from the OEM that made your PC.  Actually, the Install CDs from other PCs should work as well.  But you probably need a Registration code that is valid.

Another possible choice is to get a Bart PE version of that Windows, and this can be a great option for several reasons:  One is that it can come with a host of updates already applied so you do not need to worry about where to find them now.  Second, with the right choices made, Bart PE may have embedded a valid Registration Code onto the disk, so you don't even have that as a question to deal with.  I find that everything is great with Win2k+SP4 or WinXP+SP2.  Vista and Win7 are unknowns to me, but there are reports that they also can be made clients.

A Windows client is not an empty shell.  You can then install alll manner of Windows compatible software there, such as the4 Office suites and games among other things.  This may require a prethink of how big to make the maximum size of the virtual hard disk.  For me, 60GB is usually adequate, but you really won't allocate all that at the beginning.  Go too small though, and I don't think there is a provided way to extend it later.

You can make one good image and clone it a few times.  Trouble is, each copy has the same UUID code, and that is a no go.  But there is a manual command to cause any copy to get a new UUID, and that takes care of the problem.

An install process like Windows or Ubuntu HAS to be able to access the internet at some point.  For Ubuntu, it is right away.  For Windows, it is to go online for email and updates.  If you think there is a problem getting online with Windows, just swith the another new client for Ubuntu and see if that works for you.  If that works check the settings for both clients and see if anything really stands out.  That might help.  You can always delete the added client when done.

I'm going to add something here that some will think is highly questionable, but perhaps less so under present circumstances. Your virtual drive is stored on a file type .VDI, which probably  stands for Virtual Drive Image. Since this is just a file externally, they are interchangeable, or put another way, exchangeable.  Now put that together with the notion of peer-to-peer (p2p) file sharing, and you have the world to pick from.  Even .ISO images might be locatable.  I'm not advocating piracy here, but recognition that the OEM for certain significant operating systems has or is throwing in the towel on several key versions, and there will no longer be any innovations, support, or sales of those items.  Both hardware and software can be orphaned in this manner, and I consider it only fair that we find ways to adapt and adopt as necessary to the changes made.

---

### Post by rpete on 2011-01-14
oldefoxx there is a lot to consider but it does seem ideal if I can get Virtualbox going.  I have to read the manual for VBox but I am assuming I can run a program from a virtual Windows 7 and use it to analyze Office files which are in the actual Linux OS.  Good advice about the space needed.  I envision only needing to use MS Office Suite and Nvivo9 in the virtual space.  

I ordered a CD and am waiting for it. Yes I need to register it for it to work.  In the meantime my Internet connection is not working.  I did not get Virtualbox started. I mean I initiated the wizard but couldn't complete it because I didn't have the Windows CD.  

I will refer to both your posts when I am ready to try Virtualbox again.

Thanks.

---

### Post by laven on 2011-01-22
It is a nice sharing.....

---

### Post by someusername on 2011-01-22
I have an experience to share: I was using VirtualBox from Oracle, proprietary, with the latest ubuntu, with Windows 7 x86 installed. As it happened I pressed Start > Hibernate. When powering the machine back on, its Windows was borked. MS setup repair couldn't solve it. Never had that problem with VmWare Workstation, so now I'm only using that. Thankfully I hadn't installed everything on the Windows version at that point in time, so I only lost an hour's worth of work.

Btw, how to turn off the hibernation command from the start menu: 
```
powercfg.exe /hibernate off
```

Cheers

---

### Post by oldefoxx on 2011-02-05
Yeah, VirtualBox is good, but each release changes features around as they add more to it.  Now you can work with the Linux partitions by Shared Folders as well as USB drives either by shared or USB Settings.
Since the host does all the read and writes, no problem with a Windows guest getting access to folders and files used with Linux.  There are some got-you issues though.  For instance, find the Oracle VirtualBox download page that is in bluey and a list of VirtualBox releases by the
OS that it is intended for.  Topmost right now is Ubuntu Maverick, and
you have as first choice X86, which is the 32-bit version, followed by
AMD or AMD64 which is the 64-bit version.  By breaking it down this way, you have best choice for a VirtualBox match to host and GuestAdditions that sweeten how the client behaves when fully installed.

But this page is important for another reason.  First, when you do the download, save it to a file.  The Archive Manager can't handle the DEB file properly on the fly, so just get the file for starters.

Next, you will need the terminal mode and type in sudo -s.  This will give you root powers for what comes next.  The next is go down the same page and find the entry they want you to make in
/etc/apt/sources.list.  Copy and paste the line entry they want there, as this is important for updates.  Then go down the page a bit further and use copy and paste again to get the wget line and run it in the terminal.  For terminal insert, do paste under Edit, or use shift+INS keys together.  The normal Ctrl+V doesn't work here.

Now you are ready to install VirtualBox.  To do this, go under Firefox's Tools/Download and select the download.  But rather than open it here, take the second choice, to go to the containing folder.  There you now open it with the Archive Manager and choose Install.  It takes care of the rest.  Sort of.

There are still some manual steps to take.  Go under System/Administration/Users and Groups.  You want to make changes, so follow that button first.  Then you want to Manage Groups, so pick that next.  There are at least three groups you want to check. These are lp, lpaddmin, and vboxusers.  Under properties in each of these you want a checkmark by whichever users are to use VirtualBox.  There are other groups listed that someone else might think worth enabling, but the two starting with "lp" have to do with using the host printer by the client, and the other is about using VirtualBox USB links.

All that done, one thing left:  You need to perform a restart (reboot if you prefer that term).  Now connecting to VirtualBox is easy.  Just go under Applications/System Tools, and there is the link. You are ready to go.

VirtualBox comes up with no clients.  New lets you make one, and let's do a quick rundown on what that entails:

Pick a Name for this client, but short is better.
Type the OS to be installed and do this right.  It controls which set of GuestAdditions are made available to improve client performance.
Set a minimum memory size.  I usually triple or go higher on this if my machine has the memory for two OSes at once.  For W2k, I use 768 in place of 128.  You will get warned if you go too high.
Decide on a VDI file size.  This will be the max ever used.  Dynamic is better since it won't demand it all at once, only grow as needed, and deals with Win2k and WinXP issues regarding huge drives.  I can't install W2k or XP on a large hard drive until I get into the Registry and set EnableBigLba.  Even though you go huge, the dynamic method makes only what you need to start.

The alternative is to provide an existing VDI that has an installed OS and possibly applications on it.  If you don't have one, this is where P2P may fill the bill.  Not that I'm saying this is the thing to do, but it can make a two computer environment more meaningful for once.

The Settings are important, even before trying to install your guest OS.  The Storage settings allow you to designate more than one virtual drive, meaning a second VDI can be joined.  You can also have more than one CD/DVD drive, or tag one or more ISO images to sub as a drive.  I've copied my W2k install disk to hard disk, and it dramatically speeds up my install time.

One bad thing about ordering the install disks is they come without the patches and upgrades.  With MS wiping out support for W2k and XP, you are in a bit of a hurt.  On the other hand, Ubuntu and VirtualBox make a pretty good moat and fortress for Windows which is rather hidden inside, so maybe they are not so necessary.  And more to the point, Some people have used Bart PE to merge original and updates into a single install, and people tend to hang onto those things.  Since it all is part of one CD ISO file, the opportunity to get your hands on one may be just around the corner or part of your next torrent trade.

My last tips are:  With VBOX, go under files and change your preference from having the right Ctrl key serve as host to using the Menu key right beside it.  It avoids conflictive use of Ctrl.  Also note that VBOX gives you a short taskbar when at full screen under the client.  Note the X on the right side of the bar.  Some conflict between the two OSes and VirtualBox will cause the keyboard to go dead if left idle for a short bit.  A quick way out of this is to use the mouse to get to the VBOX task bar, click on the X, then click on the Cancel button when the shutdown dialoge pops up.  These two clicks will somehow cause the keyboard to be enabled again. and you can go on with what you were doing.

---

