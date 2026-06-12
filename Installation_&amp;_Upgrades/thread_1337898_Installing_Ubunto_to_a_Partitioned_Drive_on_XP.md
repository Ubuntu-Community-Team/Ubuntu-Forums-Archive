---
title: "Installing Ubunto to a Partitioned Drive on XP"
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by ScarieXS on 2009-11-25
My friend told me to try out ubunto, however I do not have a computer with a blank hard drive, or one I am willing to remove all the data from to install Ubunto on.

What I want to do is partition my current drive so that I can have both Windows XP Home Edition and Ubunto on the same harddrive, but in separate partitions. (Known as Dual Booting)

I have been searching the internet to try and find out how to partition my drive  on Windows XP, however I can not find anything that doesn't require me installing a new hard drive or reformatting my current one. (Neither I want to do)

I have a few questions, which are..


[LIST=1]
[*]Is it possible to partition my current drive so that I can have both Windows XP Home and Ubunto on the same physical hard drive?
[*]If it is possible, how would I go about partitioning and installing Ubunto, so that I may use it?
[*]If it is not possible, would it be possible to purchase an external harddrive to install Ubunto to, and run it from there? (If so, how exactly would I run it? Dual Booting gives you the option on load, would running from an external drive also do this?)
[*]Will all physical components remain compatible? (Such as my Epson Stylus NX105 printer, Insignia HD Monitor, and my nVidia GeForce 6100 graphic card.)
[/LIST]
Thanks, and sorry if what I am trying to do is not possible.

Any help is appreciated, thanks :)

---

### Post by audiomick on 2009-11-25
Hallo.
None of this is a problem.
I have heard that there are some reasons to use a windows tool to shrink the windows partition, and that it is a good idea to start windows once afterwards.

Be that as it may, read this first:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by ScarieXS on 2009-11-26
Alright, installation went fine computerwise, however I did have a powersurge while it was doing step 5/6. (I selected the Install Side-by-Side and choose which one on start up option)
 
When I was sure there wouldn't be another powersurge, I started the installation again, and got to step 5...however, the option to install side-by-side was no longer there. I was given the option to erase my harddrive and install just ubuntu, manually partition my drives, or quit.
 
I decided to manually partition, I had printed instructions on how to do so, however when I got into the manual partition page, the program had changed my whole Windows partion into Ubuntu's partition, the only other partition was the recovery partition, and I could not re-size any of the partitions.
 
I can still load Windows when I start up my computer the regular way, however I am getting error alerts, such as "mpfservices.exe is corrupted, please run chkdsk.exe", and Java no longer runs for Internet Explorer (However, it does run to an extent on FireFox)
 
I made a backup of important data before I started this, and I have the system restoration disk right beside me, however what I couldn't find were the drivers for my wireless card, so reformatting is an option I wouldn't like to do unless its the only way.
 
New questions:
[LIST=1]
[*]Is there a way I can get the side-by-side option back so that I can finish the install?
[*]If not, how can I go about undoing the changes that Ubuntu made?
[*]If I do get Ubuntu working, how can I get my wireless card to work on both windows and ubuntu to connect to the internet? I am using a Netgear WG311v3 802.11g wireless PCI adapter.
[/LIST]While typing this message I got the same alert given above for mpfservices, only it said for Drive C. Should I run a system restore to before I tried the Ubuntu install, or run the check disk application?

---

### Post by darkod on 2009-11-26
Ubuntu shouldn't have done any changes at all. Are you sure this was ubuntu and not the power surge?
You select the install options in steps 1-7 and only at step 7 you have the Install button to start the installation. If you click Quit on that screen nothing happens.
Only after clicking Install the process starts and partitions are created/formatted.
Sort out your XP first, if it still complains about disk checks, do them. Boot it few times to see if it's OK. XP can be problematic if something got corrupted during the shrink or the power surge. It's useless to install ubuntu if you find out you have corrupted XP later on. Well, not useless, but you know what I mean.
Sort out XP and only then proceed.
In case there really is something like partition created by the interrupted install, then you can just delete them and use that free space to create manual partitions. BUT BE SURE which one is your XP partition, not to delete that.
Another option is to boot with ubuntu CD and select Try Ubuntu. When it loads you can start Gparted in System -> Administration. That will show you partitions, and you can manage them there, including ntfs. If some of them are mounted (swap would be), just right click on the partition in the list and select Unmount to be able to make changes on it (for swap use swapoff).

---

### Post by ScarieXS on 2009-11-26
The computer said that it was setting up the partitions, and had been running for about 10 minutes, at which point the power surge occured.
 
I don't think its the Ubuntu install itself, I think the powersurge stopped it in the middle of the partitioning process and corrupted some files, and now Ubuntu doesn't recognize that I have a Windows partition since the partitioning process apparantly changed it all to a Ubuntu partition.
 
To better explain myself, when I first ran the installation, there was a bar at the bottom of the screen showing partitions, and how they would be changed. It showed a small blue bar (My recovery drive), a large green bar (My windows partition) and a small white bar (Ubuntu partition). However, after the powersurge it shows the small blue bar and the rest is orange. When the mouse is hovered over the orange bars it says that its a Ubuntu partition, however there is no longer a windows partition.
 
I'm going to run the checkdisk application now, which can take awhile from my experience. When its done, I will check back here.
 
Thanks for the help so far.

---

### Post by ScarieXS on 2009-11-26
Update: Upon rebooting my computer, it would not load past the recovery option. (Normally it gives me the option to run recovery, waits 3 seconds, and then loads the OS, however now after the 3 seconds it just froze.) I rebooted several times, all with the same effect. I ended up using my recovery disk that came with my computer to fix my computer, lost everything. (I had all my pictures, documents, music, ect backed up, so I'm not that upset...)

By doing this, however, it did fix the partitions on my computer. I figured that since I have nothing to lose, I might as well try the install again. When I left my house it was at 67%, and it should be up and running when I get home. Thanks :smile:

Now, my only remaining question is how can I get my wireless adapter to connect.

I use a WG311v3 Netgear Adapter. Any tips?

---

