---
title: "Reinstall Ubuntu"
date: 2005-12-02
forum: Installation &amp; Upgrades
---

### Post by GabrielWolff on 2005-12-02
I've got Ubuntu on my machine, and wanna add WINXP. Being quite a newbie to all this, the whole GRUB thing is a bit hard for me.

I there a possibility of saving my Ubuntu settings (like: What programs I've got installed, and my users and passes), installing XP (and thereby erasing Linux), and then adding Ubuntu?

Seems easier to me. Is it possible?

Thanx

Gabriel

---

### Post by Robgould on 2005-12-02
You don't necessarily have to kill ubuntu. You can install windows and keep your whole linux in tact. You need hard drive space fro XP is all. When you install XP it will not kill linux if you install in free space. It will wrote a new mbr and that will kill grub. After you install windows, boot back to ubuntu by using the install cd and rescue mode. Then go here:
 
[http://doc.gwos.org/index.php/Restore_Grub]("http://doc.gwos.org/index.php/Restore_Grub")
 
or here
 
[http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253]("http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253")
 
I hope this helps you.

---

### Post by aysiu on 2005-12-02
Possible? Yes.

Worth it? Probably not, especially if you don't really know what you're doing.

It'd be a lot easier to back up your settings and files (upload to a website, get an external hard drive, burn CDs, buy floppy disks--whatever you have to do), reinstall Windows and then reinstall Ubuntu.

---

### Post by Herman on 2005-12-02
Hello GabrielWolff, here's a link to the serious way of doing it:
[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

Here's a simple way I use, it does not back up all of everything, but does back up just the main things I like.
(a) open your home folder.
(b) make a new folder with a name like 'dec05_bkp' or similar.
(c) copy or move all the folders into it that are to be saved.
(d) On the 'view' menu, click 'show hidden files'.
(e) open the one called .evolution and copy whatever is in there you want, such as calendar, addressbook, mail. Copy those to 'dec_bkp'.
(f) find the .mozilla folder and copy the items in there to 'dec_bkp'.
(g) copy any other items you can think of that you might want that I haven't mentioned.
(h)move you 'dec_bkp' folder to wherever you want to save it like another partition or another computer or better still a CD or DVD disk and burn it.

When it's time to restore just paste what you need back into your new system from your storeage media (CD or other disk). For firefox if all you want is your bookmarks, just open your firefox folder and then the one inside that called 4jwlg215.default (well that's what mine's called), and there's a file inside called 'bookmarks.html'. Just copy that off your CD and navigate to your same location in your new installation and paste it there. You might get a sign asking if you want to overwrite the existing file that already has the same name, choose 'replace'. You can do similar with you email too.

An advantage of doing things in such a simple way is you can make one backup per month or whatever timespan you choose and always will be able to go back in time to that month's backup and find something like a particular e-mail you remember and want to look up, back up your current mail folder somewhere, re-install your old mail folder off your CD an open evolution to read your old mail from months ago. Then delete it and restore your current mail folder.
If it has been compressed you loose the flexibility to be be able to just restore one item at a time like that so easily.
I hope this is helpful. :D  (Herman)

Those are two ways to back up and restore, the method described in the link will be better for a complete re-install with all your programs, like you asked about. That way might be better for this situation. However, I'd have to agree with aysiu, it could be a little bit too hard if you are a beginner, it depends how brave you are. Sorry for the simultaneous post, aysiu, your post says the same thing already but much more concisely.

---

### Post by GabrielWolff on 2005-12-03
Thanx Herman,

I've read through your link ([http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311))
and I got some additional questions:
1) In that case, the backup is hopefully not be needed, right? Should everything go straight, I'd install WIN without having to damage Linux, or did I get it wrong? Wouldn't it be easier to backup, erase, install WIN, and the extract the tar file?
2) How do I make room for Ubuntu (or win, whatever's gonna be added on)? Do I just look if there's enough? DO I have to split my hd? What program should I use for that?

Thanx

Gabriel

---

### Post by GabrielWolff on 2005-12-03
I tried to create the backup file explained in your first link, but ny machine decided to commit suicide in the middle. No I can't find any tar file named backup. Is it somewhere, named differently, occupying much of my hd.

My hd space worries me anyway. gParted says 97% of my 40GB hd are used. How bad is that? I can think of 6 or 7 GB I could get rid of, but everything else seems like the system. Weird, ah?

Any clues?

Gabriel

---

### Post by Herman on 2005-12-03
Wow, that sounds pretty bad! :confused: I'm sorry to hear things have gone wrong for you. Will it still boot? Do you need to try and recover any of that data? Have you got a live CD you can use? I don't yet have a Ubuntu live CD, but I can tell you how to recover data to another computer on your LAN if you have a Knoppix CD.
(Herman).

---

### Post by GabrielWolff on 2005-12-03
Maybe I should start writing clear posts, instead of trying to be funny ;) 

My machine simply crashed, but I switched it on again, and it looks all fine. All of my data is (supposedly) where it belongs to.

Only funny thing's I can't find that darn archive I was trying to create. Looking at gParted I guess it hides somewhere in my machine, otherwise I have no explanation for 34.4GB stuffed with data. I got 5GB of mp3s plus maybe another 6GB of amule temps, but still... I don't know, maybe it's all fine.

Got no LAN, just a single machine (was that a stupid sentence? I think not)

Still the questions posted here earlier seem relevant. Do you know the answers?

Thanx

Gabriel

---

### Post by Herman on 2005-12-03
Oh, what a relief! I'm glad it still boots okay!
Now, for the questions you raised earlier;
> 1) In that case, the backup is hopefully not be needed, right? Should everything go straight, I'd install WIN without having to damage Linux, or did I get it wrong? Wouldn't it be easier to backup, erase, install WIN, and the extract the tar file?
I think you should always make a back-up if you care about the data you have saved on your hard drive. It is work and time to get it there and it will be work and time and maybe internet costs to replace it, so it is probably worth the time to back it up if you can. It's up to you, but if you don't and you lose it you only have yourself to blame. I'd think you should make a simple back-up like I explained in an earlier post, do that first, at least your most important data. Then after that clear out whatever mess is in your computer from the command in the link going wrong.
> 2) How do I make room for Ubuntu (or win, whatever's gonna be added on)? Do I just look if there's enough? DO I have to split my hd? What program should I use for that?
If you click on my signature link on the bottom of my post you will see illustrated examples of how to use the partitioner in the Ubuntu install CD to partition your drive to install Ubuntu. That's for when someone has Windows in already, but no Ubuntu yet. To do it the other way around, the easiest way I know is to use a knoppix CD with Qtparted to take away some space from Ubuntu, then install Windows. But I agree with you. For me it's easier to erase everything and install Windows first, then Ubuntu. I think I know how to do it the other way around, but I haven;t tried that myself. You just have to re-install the GRUB boot loader. it shouldn't be too hard. You decide.:D

---

### Post by GabrielWolff on 2005-12-03
Sounds good, I think I got it, I might read it a couple of more times, and then try it out. (and f**k up my mom's machine, probably. As done before)

What would be a good size for windows on a 40GB hd? I need to run a couple of heavy programs on it, but I can remove almost anything else (office and all that crap I don't wanna have on our anti-corporate machine;) )

Thanx

Gabriel

---

### Post by Herman on 2005-12-03
> What would be a good size for windows on a 40GB hd? I need to run a couple of heavy programs on it, but I can remove almost anything else (office and all that crap I don't wanna have on our anti-corporate machine
Well, Gabriel, it's pretty near impossible to advise anyone on the size for their partitions. it's really something that depends on how many large files you'd like to store in either operating system. Music files are the largest files by a long way. Oh- except if you want to store a movie, that would be even bigger. (Or a football game or the like). In my household, my wife has all that in her PC. Those kinds of files are massive! She keeps those in Windows, so she needs a large Windows partition.
Programs take up hardly any room at all, so don't ditch any programs, that won't save very much space and you'll lose a lot of functionality.
Image files like photos and drawings take up the next most amount of space, and e-mails do too. It depends which operating system you'd like to use for e-mail. I strongly recommend Ubuntu for all your e-mail and internet work because Ubuntu is very tough against adware, spyware, viruses etc. 
If you have a FAT32 filesystem in Windows it might not matter as much because you can easily read and write to both file systems from Ubuntu. If you have an NTFS file system in Windows, you might want to also decide how large to make any FAT32 logical file system for sharing files between the two systems.
See, it's a complicated question! :D  If you have used Ubuntu already and you like it, maybe give it 20.0 GB (half), if you haven't tried Ubuntu out all that much yet and are not sure, even 5.0 GB is enough. 10.0 GB would be average. Remember Ubuntu can access files in Windows, but not the other way around, and you can also easily shave some more space off Windows by re-installing Ubuntu more easily than the other way around.  hope that helps :smile: (Herman)

---

### Post by GabrielWolff on 2005-12-04
What's the minimum for a win installation? 20GB seems much to me. Is that needed? I don't really wanna store anything on my windows partition. I don't want to use it for anything other than a few notation programs, and a program to check out music to a MiniDisc.
And my last qustion before daring the big step: What happens if I wanna remove win later on. Does Ubuntu automatically reclaim the free space? Is it lost untill I reinstall the OS?

Thanx

Gabriel

---

### Post by bwog on 2005-12-04
This link was given to you earlier: [http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2521253) . 

WinXP needs a lot of space, you said you wanted to run some heavy programs on it. I would say 20GB or a minimum of 10GB if you want to use XP comfortably. However, it depends on what you do, 3 modern games would fill 10GB.

There wont be a problem when you remove XP, you will have an empty partition for use with ubuntu if you format it to ext3.

---

### Post by GabrielWolff on 2005-12-19
How do I know if I got win running with a FAT32 file system or a NTFS file system?

Thanx

Gabriel

---

### Post by Herman on 2005-12-19
Hello, Gabriel, You can tell if Windows XP is FAT32 or NTFS by clicking 'Start', then 'My Computer', then you right-click on your 'Drive C:' icon. On the bottom of the right-click menu, there should be an item called 'properties', click that.
 A sign should come up then with lots of information about drive C:, and on that sign you will see something to tell you if it's FAT32 or NTFS.  :D  (Herman)

---

### Post by GabrielWolff on 2005-12-21
[QUOTE=Herman]Hello, Gabriel, You can tell if Windows XP is FAT32 or NTFS by clicking 'Start', then 'My Computer', then you right-click on your 'Drive C:' icon. On the bottom of the right-click menu, there should be an item called 'properties', click that.
 A sign should come up then with lots of information about drive C:, and on that sign you will see something to tell you if it's FAT32 or NTFS.  :D  (Herman)[/QUOTE]

So there's no possibility of knowing which of your info pages I have to read 40 times BEFORE I install XP in my machine?

The thing is: I don't yet have win installed.

Gabriel

---

### Post by Herman on 2005-12-21
>  So there's no possibility of knowing which of your info pages I have to read 40 times BEFORE I install XP in my machine? The thing is: I don't yet have win installed. 
No, I guess not, you'll just have to wait until you install Windows first, and see what you get then. Depending on what kind of Windows XP you get, you may be offered a chance to decide for yourself, or maybe not. I think with 'Home Edition' like I have, you can choose, but with 'Professional Edition' you might get NTFS without being asked, but I don't know, I have only got 'Home Edition' myself. My choice is FAT32 for making a better dual boot computer, but that's only my opinion. :D (Herman).

---

