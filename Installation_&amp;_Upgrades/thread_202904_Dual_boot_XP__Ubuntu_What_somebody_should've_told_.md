---
title: "Dual boot XP / Ubuntu: What somebody should've told me"
date: 2006-06-24
forum: Installation &amp; Upgrades
---

### Post by Jere on 2006-06-24
I probably had my once-in-a-year Linux desktop testing eagerness period again. This time I went for Ubuntu.

First, I should probably tell you that while I'm fairly familiar with Linux servers, Debian in particular, I have never really used Linux on my desktop apart from trying Knoppix and Mandrake (a long time ago). I'm familiar with command line operating though (bash), including apt-get and all the stuff on Debian.

I've used Ubuntu for the last two-three days now, and during that time, I've had to learn a lot about how operating systems boot... This is what I started with: I had some 4 GB of free space in the beginning of my hard disk space. The rest was Windows' NTFS partition. My plan was to install Ubuntu 6.06 on that small strip and dual boot to Windows.

I burnt the installation CD and ran it. As everything seemed to be okay and all my hardware seemed to be supported including my internet connection, I started the Ubuntu installation. At the partitioning stage, I decided that I would edit the partition table manually. I added a primary ext3 partition, and then a swap partition, both in that ~4 GB space. I was a little confused when I wasn't able to create a logical partition (that option was grayed out) for the swap; when I have installed Debian, I have gotten used to having to create the swap partition as a logical one.

The next page in the installer wizard was rather undecipherable to me. There were two lines, where I was supposed to associate partitions with their functions. On the first line, there was Windows for /dev/hda2, which was ok, but on the next line, I was clueless. There were various mountpoints to choose from, with / selected, but I wasn't able to associate it with /dev/hda1, because it wasn't on the list. There was only /dev/hda3, which I thought was the swap partition I had created. There wasn't a third line either, so I wasn't able to associate the swap partition to anything, and as I tried to go forward, the installer told me I hadn't chosen a swap partition... bummer.

So I went back to the previous page, the partitioner, where the swap partition that I had just created had turned into a black "Unknown" partition. I recreated it and faced the same oddness again on the next page. This time, though, when I tried to make any sense of that page, the installer suddenly crashed. Cool. I restarted it, and this time I thought I'd just let Ubuntu find the largest continuos free space. The installation went fine, Ubuntu created the partitions in that ~4 GB space as I had wanted.

This installer weirdness isn't actually what I'm writing about. The thing nobody told me was the tiny, but yet important (now apparent) fact, that when you install Ubuntu (or probably any Linux distro) to dual boot with Windows, and you create the Ubuntu partitions *before* Windows the Windows one (i.e. the number of the Windows partition will change), *Windows will fail to boot...*

I started to fiddle around with Ubuntu, and at one point, I wanted to boot back to Windows. However, Windows threw me a cute error about HAL.DLL being corrupt or deleted. Really nice. Well, I figured that even if Ubuntu had crippled the Windows partition, most of my stuff would have to remain undamaged, as you just can't destroy gigabytes of stuff in a swift. I booted Ubuntu and started doing some research... Googling about hal.dll problems showed me, that it was most likely just an issue with the MBR. I tried reconfiguring GRUB in hope that it just had the wrong partition for Windows or something, but it didn't help.

I had to learn a bit more about booting operating systems. As I understand it (now), the first thing Windows does when it boots is that it reads boot.ini in order to locate things on the hard drive. Apparently Windows failed doing so, as it couldn't find hal.dll. Hal.dll seems to be the first thing Windows wants to load, hence that file gave the error.

The Gnome file manager failed to read my NTFS partition, even though I know modern Linux distros support read-only NTFS. It made me a bit worried, but I fixed it by fiddling around with fstab. (BTW, it bugs me how often you need to resort to the terminal. I wanted a *desktop* system...) Ubuntu was now able to read all the contents of my NTFS partition, so I knew all my stuff was safe. That was quite relieving...

I had a look at boot.ini, and I realized something. Ubuntu called the Windows partition /dev/hda2, but in boot.ini, it was obviously still called partition 1, the way it had always been. It seemed clear to me now, that I would just have to change it to partition 2 to be able to boot Windows again. Things weren't that simple though. Ubuntu can't write to NTFS... but I googled and found out that I can set up FUSE and ntfsprogs to get an unreliable, incomplete way of writing to NTFS. Better than nothing... As it was just a matter of changing one byte, I thought it was worth the risk.

Even though it turned out Ubuntu already had FUSE installed, setting up ntfsmount wasn't exactly a trivial task. It took quite a lot of frustration and googling, but these two pages saved me: [click](http://wiki.linux-ntfs.org/doku.php?id=ntfsmount) and [click](http://fuse.sourceforge.net/wiki/index.php/FAQ) (particularly, "What do I do if /dev/fuse does not exist?"). As I finally got the partition set up with write access, I changed the Windows partition in boot.ini to 2, rebooted and, oh the relief, Windows booted up normally again.

The lesson is, that the Ubuntu installer *really* should warn about fiddling with any partitions located before the Windows partition on the hard disk. If you do anything that makes the Windows partition number change, Windows will die. My workaround to restore it was irrationally complicated. Of course, if there are any easier ways to get things working again (I bet I overlooked something very simple), please post them, but this kind of situation really has to be avoided.

Regards,
Jere, back in Windows now.

---

### Post by rcarring on 2006-06-24
Windows uses arcloader to find itself. Creating a new partition before Windows, a primary partition meant that this would appear first in the list of available drives to Windows' bootloader. What you did with the boot.ini is perfectly correct, although you could also have booted to the recovery console using your XP cdrom disk and edited boot.ini from there.

---

### Post by Noahod on 2006-07-04
You can also boot windows xp bootloader from a floppy disk, this saves a lot of stuffing around with fuse and whatnot.

---

### Post by FenrisAbraxas on 2006-07-26
> **Jere said:**
> 
The lesson is, that the Ubuntu installer *really* should warn about fiddling with any partitions located before the Windows partition on the hard disk. If you do anything that makes the Windows partition number change, Windows will die. My workaround to restore it was irrationally complicated. Of course, if there are any easier ways to get things working again (I bet I overlooked something very simple), please post them, but this kind of situation really has to be avoided.

Regards,
Jere, back in Windows now.

Well first of all, every installer that mess up with partitions warns you about everything BUT none of it would tell you "im going to mess up with a windows partition because you want to install me before/after another, i can do this to solve it just because im Über Intelligent and i'm sure THIS IS WHAT YOU WANT"

Another thing, the hal.dll error is because probably you passed the wrong value to grub (yeah i know the installer should do it but ... ).

If u have installed windows in lets say D: (or hda2 or whatever) ntldr boot.ini and hal.dll will be installed in C: (or hd0,0 or hda1 or first partition). So the ubuntu and any other distro team consider that if windows is already installed in your system it will be installed in the primary partition of your system.

Another thing, Linux depends a lot on the command line and that's better than have to edit the cryptic windows registry. (also if you use ubuntu you can always launch nautilus (with sudo) and look for the file to edit in a graphical interface then use gedit or gvim or whatever to edit the file, it's just that for techincal help is easier to explain "vi /etc/foo/foo.conf" than "if you have kde open konqueror if you have gnome nautilus if you have xxx open yyy", also the power and flexibility of the terminal i think it's greater than most GUI's. 

Good Luck and don't blame the installers, most times is the user fault that probably try to do something "easy" and get different results because (no offense) the user don't know how a OS works.

---

### Post by mejohnsn on 2006-07-26
There are some things that are reasonable to expect that the user will know. There are some things that are not reasonable. Things described as "how an OS works" tend to fall into the latter category. We do not expect the user of an FM radio to know the intermediate frequencies in use by the superheterodyne stages of their FM receiver. Likewise, I find it highly doubtful that the user should have to know that Windows insists on usurping the first partition for its own use before using the automatic Install of Ubuntu. And if the install program itself cannot accomodate such cases (as the OP describes) then the documentation for it should. Progress has been made in this direction. Ubuntu documents this better than certain other distributions (which shall go un-named).

That said, I do remember seeing a warning about this usurpation somewhere, but I have spent MUCH more time than most people researching the man files, Googling, and searching the forums before I partition my HD to allow room for both XP and Ubuntu.

Finally, I think the OP did an excellent job of both describing his predicament, and documenting the solution. Now if (when?) others have similar problems, a judicious choice of keywords in a search of this forum will give the answer.

---

### Post by catlett on 2006-07-26
```
The lesson is, that the Ubuntu installer really should warn about fiddling with any partitions located before the Windows partition on the hard disk. If you do anything that makes the Windows partition number change, Windows will die. My workaround to restore it was irrationally complicated. Of course, if there are any easier ways to get things working again (I bet I overlooked something very simple), please post them, but this kind of situation really has to be avoided.
```
No disrespect but if you do not know that making a primary partition in front of another primary partition makes that the first partition 1 or C or /dev/hda1 and the second partition (which was the first until you put this other partition infront of it) is now 2 or D or /dev/hda2, you shouldn't be messing with partitions and your hard drive. 
Since you can google for fuse help, why didn't you google for ubuntu installation help? [http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)
[http://www.hezardastan.org/breezy_xp_dualboot/en/](http://www.hezardastan.org/breezy_xp_dualboot/en/) This is for the last release but still relavent if using the alternate install cd

I guess the lesson is , never assume the user knows anything. Assume every action is unknown and not understood, no matter how basic it may appear to the developer or writer.

---

### Post by confused57 on 2006-07-26
Nice links, catlett...anyone setting up a dualboot on their main computer should definitely do a little research first.  I've added the necessity to have Windows first to the Sticky "How To Help Yourself":
[http://www.ubuntuforums.org/showthread.php?t=142716&page=5](http://www.ubuntuforums.org/showthread.php?t=142716&page=5)

If you have a test computer, trial & error isn't so bad...actually learn a lot doing it that way.

---

### Post by orb9220 on 2006-07-26
I agree I see people getting into trouble because they don't want to read up on it first. (Read the Docs!) and they are generally lazy about disk maintenance. Like Backing up important Data to cd,DVD's ect... and the big one which tripped up gpart until I did it was to defrag the hard drive.

  I have to remind myself to slow down and take the time to do it right. But it seems we live in a world where people want instant gratification and instant results. Many have got away with no reading the docs in windows but I am sorry to say that will not work in the Linux world. You have to spend some time to educate and read about using linux.

---

### Post by flyvholm on 2006-08-02
I think the OP pointed out a pitfall that is not obvious (except if you are a developer, evidently), and I don't think it is unfair to suggest that the installer could be more informative, considering the massive trouble it could save end users from. 

How about making some docs with info about how to do common partitioning jobs, what to be aware of, properties of different filesystems etc. and make these available from the installer where you really need them? I would certainly have appreciated it. I'm in the process of digging up bits and pieces with Google instead, and this is how I find myself spending my time with Linux.

Maybe that's how it's supposed to be, but it's a major reason why most people use Windows, leaving Linux to experts. And I thought Ubuntu was an attempt to change this.

---

### Post by FenrisAbraxas on 2006-08-02
> **mejohnsn said:**
> There are some things that are reasonable to expect that the user will know. There are some things that are not reasonable. Things described as "how an OS works" tend to fall into the latter category. We do not expect the user of an FM radio to know the intermediate frequencies in use by the superheterodyne stages of their FM receiver. Likewise, I find it highly doubtful that the user should have to know that Windows insists on usurping the first partition for its own use before using the automatic Install of Ubuntu. And if the install program itself cannot accomodate such cases (as the OP describes) then the documentation for it should. Progress has been made in this direction. Ubuntu documents this better than certain other distributions (which shall go un-named).

What i was trying to point out is that the installer can't have options for n+k cases, it warns you like 3 times before making all the changes, and if you are lazy to read the documentation don't blame the installer itself nor the developers.

If you have a FM receiver you know that messing up with the internals could lead you to a messed up radio. So you try to read about it before blame the manufacturer for not telling you "if you put this inside it will not work".

And probably "how an OS works" is too much, but how about "how an OS boots"? if i want dual boot I (myself) will look and try to find out what i have to do. Specially if the installer tells me that the changes could lead to problems

---

### Post by Cynical on 2006-08-03
> **Jere said:**
> Ubuntu can't write to NTFS... but I googled and found out that I can set up FUSE and ntfsprogs to get an unreliable, incomplete way of writing to NTFS. Better than nothing... As it was just a matter of changing one byte, I thought it was worth the risk.


And what makes you think it is unreliable? I havent ever had a problem with it.

---

### Post by acedtect on 2006-08-29
I just finished a week and a half battling this same issue. The original post here was extremely helpful.

Want to point out that I did not do the partition myself, I let Ubuntu do it, which is how I ended up with Windows on hda2 instead of hda1 where it belongs. It's also a ThinkPad which has a wonky recovery partition of its own.  I didn't manage the partition myself as I was trying out Ubuntu as an evaluation of how easy it is for new users.  I let Ubuntu decide how to partition the drive and, of course, ran into the boot.ini issue.

Is there some sort of detection of the Windows partition or questioning that could help new users here? Granted, Windows should be smarter than it is.

If you want to know why it took me a week and a half, I couldn't boot from the Windows disk, because I was using a work machine that had an admin password only IT knows. I was unwilling to explain my experimentation so I decided to go the ntfsprogs route.  i wasn't using synaptics at first which was no end of trouble.  Once I did use Synaptics and realized that you had to add in other repositories to find all the programs, I was OK. I did have to do some searching to find out what I needed to install to make ntfsprogs work with FUSE. Once that happened, I was able to change boot.ini and it worked fine.

---

