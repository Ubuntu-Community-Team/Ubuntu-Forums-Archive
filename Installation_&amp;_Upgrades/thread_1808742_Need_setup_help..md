---
title: "Need setup help."
date: 2011-07-20
forum: Installation &amp; Upgrades
---

### Post by ubantunewbie215 on 2011-07-20
Hi,

I'm looking for some help so I don't need more later.

So here is what I want to do.

1.  Reinstall Vista  from recovery partition(suck, but need to have access to it)

2.  Partition about half of my 500gig drive.  Can I do this during the installation of Vista?

3.  Install Umbutu 11.04 on the partition that I set up.

I am new at all of this and just want to make sure both OS will work right, that I don't wipe the partition containing the windows recovery.

Thank you in advance for the help.

---

### Post by MG&amp;TL on 2011-07-20
1. Reinstall Vista <shudder> :D Being microsoft, it can be quite destructive to other OS's so install that over the entire hard drive first. I don't know precisely how to do this, but microsoft is quite user friendly and it should be OK. Once Vista is up and running, move on to next steps. (reboot several times with the vista install to make sure.)

2. Change BIOS to boot from cd first. You will need to look up how to do this on your system, it may be F2, F11, <shift> or another key to access it. Find some instructions online.

3. Burn Ubuntu cd.

4. Boot from the ubuntu cd, and select 'install'

5. Select 'install side-by-side'. I believe this will partition it roughly haf'n-half, some releases have a slider on the installer which allows you to pick the partitions.

6. Run installer. 

7. When your system reboots, you will be presented with a menu that will look a little scary. Select the OS you want, (i.e ubuntu or vista, leave 'memtest' 'recovery' etc. alone)

You're done. :D

---

### Post by ubantunewbie215 on 2011-07-20
Thanks for that.

Just to clarify then....

When I reinstall Vista, allow it to use the whole hard drive?  Then partition with Umbutu?

---

### Post by ubantunewbie215 on 2011-07-20
.

---

### Post by ubantunewbie215 on 2011-07-20
Nevermind, I got it now.  Just need to finish backing things up.

---

### Post by MG&amp;TL on 2011-07-20
Sorry, got a bit distracted. Yep, let Vista use whole disk, then partition with ubuntu. Oh, and as far as I know, bumping has very little effect on where your post goes on my 'answer' list, or on the main forum. Tempting, but please don't.:D

---

### Post by ubantunewbie215 on 2011-07-20
Sorry, I was not trying to bump.  I was having brain and computer issues.  Won't happen again.  :)

---

### Post by MG&amp;TL on 2011-07-20
My apologies. See it so often. Is it sorted now?

---

### Post by ubantunewbie215 on 2011-07-20
I am just trying to finish up saving files I have and downloading the Ubuntu CD.  Then I will begin the process.  Hopefully it goes smoothly.  My biggest worry is partitioning the drive.  
The other day I put Xumbutu on my kids computer (wiped windows completely), the partition screen on there was a bit confusing and I ended up wiping the hole drive including the windows recovery partition.  No problem on that computer, but I can't have that happen on mine.

---

### Post by MG&amp;TL on 2011-07-20
The partition screen isn't anything to get worried about, although I appreciate if you're new or nervous it can be daunting. Try here for a tutorial:

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

With pictures!

Did you consider Edubuntu for the kids? Like Ubuntu, but more user friendly, less boring theme, internet filtering (I think!), with an educational theme and pre-installed programs. Will still run Ubuntu packages/apps.

[http://www.edubuntu.org/](http://www.edubuntu.org/)

---

### Post by westie457 on 2011-07-20
> **ubantunewbie215 said:**
> Thanks for that.

Just to clarify then....

When I reinstall Vista, allow it to use the whole hard drive?  Then partition with Umbutu?

After you have reinstalled Vista the best thing to do is Start-button > Right click on Computer > Select manage. In the next window in the left-hand pane Storage > Disc Management.

Depending on you PC maker you will see 1 partition may be more upto 4. If you have four partitions come back here for advice. If only one Right-click and select shrink volume to whatever size you want. Okay to all questions and wait. When it has finished leave the new space unformatted. The LiveCD will be able to make proper use of it.

Sometimes Windows can be very picky when its partitions are adjusted from another operating system.

---

### Post by MG&amp;TL on 2011-07-20
Mmmm...true. Somebody needs to sort MS out. If you want to encourage us to buy your computers and OS, that's fine, but it's a free country and you can't just go breaking other systems.

Sometimes I'll get a disk check on the first boot after an install, but I just skip it and it's fine after that. Why does the OP want to keep windows? There are usually linux alternatives...

---

### Post by ubantunewbie215 on 2011-07-20
Thanks I will check that out for the kids.  We were going to switch from Xubuntu to Ubuntu in about a week, but I may take your suggestion instead.  I will check out the tutorial you sent.  

You have been a great help.  I am very excited about getting this done.  I am new to Ubuntu but love it already and I wish I had done it earlier.

---

### Post by ubantunewbie215 on 2011-07-20
> **westie457 said:**
> After you have reinstalled Vista the best thing to do is Start-button > Right click on Computer > Select manage. In the next window in the left-hand pane Storage > Disc Management.

Depending on you PC maker you will see 1 partition may be more upto 4. If you have four partitions come back here for advice. If only one Right-click and select shrink volume to whatever size you want. Okay to all questions and wait. When it has finished leave the new space unformatted. The LiveCD will be able to make proper use of it.

Sometimes Windows can be very picky when its partitions are adjusted from another operating system.
Partition inside windows?  Ok sound good.  Tried to look at that earlier, but Vista did not seem to want to give up much of the drive.  I want at least half of the drive for Umbutu.  I am only leaving Vista on here because of college needs, and a netflix account.  Other than that after all of this installing and partitioning is done Umbutu will be my primary OS when my computer is on.

---

### Post by JASONFUSARO on 2011-07-20
> **westie457 said:**
> After you have reinstalled Vista the best thing to do is Start-button > Right click on Computer > Select manage. In the next window in the left-hand pane Storage > Disc Management.

Depending on you PC maker you will see 1 partition may be more upto 4. If you have four partitions come back here for advice. If only one Right-click and select shrink volume to whatever size you want. Okay to all questions and wait. When it has finished leave the new space unformatted. The LiveCD will be able to make proper use of it.

Sometimes Windows can be very picky when its partitions are adjusted from another operating system.



You might want to shrink the windows partition after it is installed using windows partition manager, this way windows will manage it's own partitioning scheme and you will steer clear of problems that may arise using Gparted or any that are supplied in Linux, it will be the safest route. I re-installed my windows and shrunk it to about 1oo GiB on my 500 GiB hard drive and then created the other partitions using windows partition manager and when I installed Ubuntu I just pointed to the already partitioned partition.

You may want to install all your windos software first that way you know just how much space you will need and add a bit extra, but not much as time goes on you will find your using windows less and less, so you won't be installing much more software in windows.

---

### Post by ubantunewbie215 on 2011-07-20
With the Vista I have I should only find 2 partitions after a fresh install.... The bulk of the drive, and the recovery partition (which I will need to make sure stays intact.)  I should be able to start later tonight, still performing backups.

---

### Post by JASONFUSARO on 2011-07-20
> **ubantunewbie215 said:**
> With the Vista I have I should only find 2 partitions after a fresh install.... The bulk of the drive, and the recovery partition (which I will need to make sure stays intact.)  I should be able to start later tonight, still performing backups.

Recovery partitions are usually set up by the mfg AS YOU CAN SEE I no longer have mine although it was there originally after a re-install the shadowing will be done on the single partition, you won't need the recovery if you have your installation CD.



you may want to read this
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)


you might even try installing it twice to two seperate partitions in case something goes wrong with the first, you will have a spare and later you could use that partition to install another Distro.

Just a thought, I had to re-install windows twice before I got things down, major headache, now I have 8 including Vista. One craps out for some reason I can still get up and running and fix stuff.


while your backing up

---

### Post by ubantunewbie215 on 2011-07-20
Just looked at volume shrinking before I wipe everything off here.  Can anyone break this down for me.....

Total size before shrink in MB: 462546
Size of available shrink space    49299
Amount of space to shrink.

The shrink space is the new partition or the current Vista space?

If I can do all of this right now without loosing hours I would be VERY happy.

Suggestions?

---

### Post by MG&amp;TL on 2011-07-20
Size of available shrink space is how much you can shrink Vista without losing files. You won't gain much space at the moment, though.

You could: backup your data, then delete what's on Vista, then shrink the partition at will.

Or: take your chances and use the ubuntu installer.

---

### Post by ubantunewbie215 on 2011-07-20
Let me make sure I have this right....  49299 is the space Vista and all its programs are using?

I have a lot I can delete.  Programs, and files.

---

### Post by ubantunewbie215 on 2011-07-20
I am going to revove some things and then repost the new numbers

---

### Post by JASONFUSARO on 2011-07-20
> **ubantunewbie215 said:**
> Just looked at volume shrinking before I wipe everything off here.  Can anyone break this down for me.....

Total size before shrink in MB: 462546
Size of available shrink space    49299
Amount of space to shrink.

The shrink space is the new partition or the current Vista space?

If I can do all of this right now without loosing hours I would be VERY happy.

Suggestions?





I would keep it around 100, if you make it too small growing it later will be a harder process than just shrinking it and regaining usable storage space with what is left. But then again that all depends on how much software you have to install.


Have you seen my post page 2 #15?

---

### Post by ubantunewbie215 on 2011-07-20
Sorry its been a long day and I don't want to mess up.  
I have everything on Vista I will ever use there again.  No need to install more.  My main focus is Ubuntu and using that.  Out of the numbers I posted what number would be ok to put in for:
Amount of space to shrink.

I figure I want Ubuntu to have about 60% of of the drive.

Deleting stuff now.  I will check the numbers in a few

---

### Post by JASONFUSARO on 2011-07-20
> **ubantunewbie215 said:**
> Sorry its been a long day and I don't want to mess up.  
I have everything on Vista I will ever use there again.  No need to install more.  My main focus is Ubuntu and using that.  Out of the numbers I posted what number would be ok to put in for:
Amount of space to shrink.

I figure I want Ubuntu to have about 60% of of the drive.

Deleting stuff now.  I will check the numbers in a few



Then assign 60 GiB to windows and keep the rest for Linux.

---

### Post by ubantunewbie215 on 2011-07-20
Sorry that I am just not getting this....... 

In Vista shrink window..

Total amount after shrink is what Vista keeps or what the new partition gets?

---

### Post by ubantunewbie215 on 2011-07-20
Right now it tells me size of available shrink space :68998.

Maybe I am better off just doing a fresh install.

---

### Post by MG&amp;TL on 2011-07-21
No, no, it's OK. Assumably, the shrinker is not 'live', i.e. you have to click 'apply' before it starts to do anything?

If so, just play with the numbers until you work it out. Else, usually Windows gives data about itself, so it'll be the amount that windows takes up.:)

---

### Post by westie457 on 2011-07-21
> **ubantunewbie215 said:**
> Sorry that I am just not getting this....... 

In Vista shrink window..

Total amount after shrink is what Vista keeps or what the new partition gets?

Further to my earlier reply, there was some things I forgot to mention. A clean install of Vista or one that has been in use for some time really should be defragmented before the partition is shrunk, otherwise Windows reports a larger size for itself than necessary.

While looking at the window that gives numbers the top one is the current size of that partition.
The next one is the minimum amount of space that Windows will shrink the partition by.

The third one with the highlighted numbers is where you type in the new size you want. Before you change anything here the number shown is the maximum amount of space you can shrink by.

The last one is letting you know the minimum space that Windows will need to run.

You will not be able to make that space smaller than suggested because Windows has some unmovable files in the wrong places.

So to force a smaller partition for Windows to use 'defrag' the hard drive 3 times in a row then do the re-partitioning.

Attached are some pics. The first 2 are examples of the Windows partitioning. The last one is how my hard drive looks today.

Hope this helps you through the confusion.

PS Windows can and probably will break if you try to move the whole partition from its proper start point using a LiveCD and Gparted.

---

### Post by MG&amp;TL on 2011-07-21
I'd forgotten how much rubbish Windows fills itself up with. Be pleased you are switching :D

---

### Post by MG&amp;TL on 2011-07-21
> **westie457 said:**
> 

PS Windows can and probably will break if you try to move the whole partition from its proper start point using a LiveCD and Gparted.

Not sure what you mean by this. I get a disk check on Windows 7 after partitioning, but that's it...:confused:

---

### Post by westie457 on 2011-07-21
> **MG&TL said:**
> Not sure what you mean by this. I get a disk check on Windows 7 after partitioning, but that's it...:confused:

Worst-case scenario from the days way back, caused by using a third-party partition editor inside Windows. Actually if you can leave the Windows partition in its original place no problems no matter what partition editor you use. Windows throws a hissy fit if any partition it can understand has the start point moved. The end point makes no difference as far as I know.

---

### Post by MG&amp;TL on 2011-07-21
Okay, just panicking there about what my Windows was doing to poor Ubuntu. :D. I haven't moved the start point.

---

### Post by ubantunewbie215 on 2011-07-21
Ok all.  Thanks.  Here are the results of a long day.

1.  Vista (yuck) reinstalled
2. Drive shrunk, although Vista would only give me about 130gig and kept 300gig for itself.  Greedy damn OS
3. Ubuntu 11.04 installed.  Successful install.

Now only one weird thing....Ubuntu seems to run a hair slower after giving it its own slice of the hard drive, it ran a hair faster when it was installed with the window's installer.

Any ideas....  Any tricks for the newbie to have maximum performance?

---

### Post by MG&amp;TL on 2011-07-22
I don't know, but I can tell you that Unity 2d (unity 3d with trimmed effects and 'flat' icons) Boots **five times** as fast as the normal Unity. But on the other hand, the machine I am on is only just 3d-accelerated. 

(and it looks the same too!)

Did you need to install graphics drivers for your previous install? You might need to re-install those.

---

