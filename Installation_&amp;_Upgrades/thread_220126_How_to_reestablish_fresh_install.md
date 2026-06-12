---
title: "How to reestablish fresh install"
date: 2006-07-21
forum: Installation &amp; Upgrades
---

### Post by shoki on 2006-07-21
Hello All,

I am not sure if this is wrong thinking or not. On my Windows set up I have a base install that I refresh whenever Windows gets freaky. I install XP and SP2 then my basic set up. Firefox, Bookmarks, Printer, CD burner, Important files etc. Then I use Norton Ghost 2003 to make a DVD copy so I can recover and start over at the drop of a hat.

Is there anyway to capture and quickly refresh a fresh install with updates and tweaks. Example: Fresh install of ubuntu, apply updates, get nvidia drivers runing, set up firefox the way I like it, Then take a snapshot that I can go back to.

Thank you,
--Shoki

---

### Post by meng on 2006-07-21
Maybe Ubuntu won't "get freaky" on you. I'd be interested to hear if there is a "snapshot" option but I must tell you that a fresh install of Ubuntu is fairly quick and painless. You can streamline it further using Automatix to configure your browser/plugins/media players, although in general I'm not a big fan of Automatix or its ilk.

---

### Post by shoki on 2006-07-21
Heh yeah that is waht I was thinking... maybe ubuntu will be cool and I can just keep updating and adding things. But I was worried that I will at some point screw it up and need to start from scratch. I was hoping there was a way to get back to a fresh install plus my prefs... so far so good... but you never know what I can break :)

---

### Post by Herman on 2006-07-21
> Is there anyway to capture and quickly refresh a fresh install with updates and tweaks. Example: Fresh install of ubuntu, apply updates, get nvidia drivers runing, set up firefox the way I like it, Then take a snapshot that I can go back to.Yes, I do that by installing, then adding all tweaks, settings, updates, firefox bookmarks and things like that.
Then, I resize the partition to as small as it will go, probably 2 GB or a little larger with [Gparted LiveCD]("http://gparted.sourceforge.net/livecd.php"). Then I use GParted LiveCD to copy the whole partition and paste it to the end of my hard drive.
If I ever need to restore it I just use GParted again to delete my Ubuntu partition and copy and paste the backup to the spot where I deleted the original.
It works great,  and is very simple to do.
Data files need to be backed up seperately of course.

Ubuntu never needs to be restored because of any malware or the like. Those things are not the threat at all. The only reason I might ever need to restore mine is because I enjoy trying out crazy ideas and testing Linux commands and software I may not be familiar with. Normally I can undo things alright, but I never know for sure.
Regards, Herman :D

---

### Post by shoki on 2006-07-30
> **Herman said:**
> 
Data files need to be backed up seperately of course.


Do you meant that any new data that I create/collect since the snapshot would need to be saved/reintroduced after the restore?

Thank you,
--Shoki

Doing my clean ubuntu install currently... on my wifes laptop pc.

---

### Post by Herman on 2006-07-30
>  Do you meant that any new data that I create/collect since the snapshot would need to be saved/reintroduced after the restore? Yes, you will need to save all your data to a seperate device like a CD, DVD or a USB drive, or another computer on your network. 
I recommend doing so before making the backup and then deleting it all so the backup will take up less disk space.
You would need to back up all your data a second time before you copy and paste the empty (except for added software, tweaks and settings) operating system back over the current one to restore.
If you don't, then when you paste the old copy of the operating system over the one currently in use, you will lose all your files saved/modified since the last back up. 
You will have all your added software, tweaks and settings, bookmarks and whatever else you left in before you made the backup copy of the operating system.

So yes, the software goes in one backup (partition), and the data goes somewhere else, (to some other media preferably).
I suppose you could move the data to another partition if you want. That would not be quite as safe, but it might be okay if you can't do anything else.
Regards, Herman :D

---

### Post by shoki on 2006-07-30
Herman and Others,  

I wanted to make a new post about my next question but I think it fit's well here.  I am using an (ubuntu 6.06 only) single / directory with a swap as suggested by Herman and as installed by default from ubuntu.   

Here's my question: I want to keep my install nice and tidy. On Windows through years of torture :) I learned to keep all my files in C:\documents and settings\shoki\my documents\my downloads\*.* if I needed to reinstall I would back up the my downloads folder, reinstall and the move the contents of my downloads back to the drive. Anyway it was not pretty but I was fairly strict about keeping things I wanted to save in the my downloads folder. 
(sorry for being long winded)  

Now I would like to do something similar for my /home/shoki directory. It was starting to get real messy so I want to add:   

/home/shoki/music (a place for music, podcasts etc)  

/home/shoki/My_Apps (like Google Earth wanted to install to /home/shoki)  

/home/My_Files (a place for files I want to keep)  

/home/shoki/My_Downloads (a place to save programs I have downloaded and the place I think I will install these programs from) example: I download tar file. Expand into My_Downloads then install from /My_downloads/NewProgramFolder.  

/home/shoki/FileOrTrash (a place for clutter refile it later if I want it trash it if it is junk)  

Is this a good way to keep things organized? Will programs install properly from a directory like this? I know I am trying to force the way I set up my Windows machine on to my ubuntu machine but I do like to keep my files organized.  

Thank you again for all your help, 
--Shoki

---

### Post by Herman on 2006-08-01
> Is this a good way to keep things organized? Will programs install properly from a directory like this? I know I am trying to force the way I set up my Windows machine on to my ubuntu machine but I do like to keep my files organized. Yes, shoki, that will be okay. 
I like to name my directories (folders) something different and more original than the boring old 'Windows style' names though. It's entirely up to you, it's your personal computer. 
I have all my most improtant ones beginning with 'a' like 'accounts', 'all_images', 'all_linux_info_here' and 'audio'. making up names that begin with 'a' make them appear first on the list where I can find them easily.
Then there's 'b' for 'backups, but inside that I have folder names that are made of dates, like 18dec05bak, and 05jan06bak and so on.

My 'all_linux_info_here' folder is an interesting one. It contians a page index made by NVU. NVU is a website making software that you can install in Ubuntu. You can make your own web-pages inside your computer and save them in various folders according to category. I have one each different type of Linux info I have am collecting. (Bootloaders, filesysems, partitioners, file rescues, Linux commands, troubleshooting, and so on.) The advantage is, when I want to look something up, all I do is start firefox. The main index is bookmarked, just like a website on the internet, and from there all my collections of information about different subjects is indexed and sub-indexed. It's just like my own private wiki. I recommend everyone install NVU and give it a try. It's great, and it's another thing we can do for free in Ubuntu that Windows users can't do or they have to pay big money for. Ubuntu is great! :D

You will find that you can install all software through your terminal by typing a command, or through  'Synaptic Package Manager' by using 'Applications'-> 'Add/Remove Programs' though.  Ubuntu is different from Windows, you cannot just keep the 'installer' for an application in your 'My Downloads' folder and expect it to install when you click on it. Linux just doesn't work that way.  
Another thing is, you need to enable 'repositories' if you want the full range of sofware that's available for Ubuntu.  (Repositories are like huge libraries full of free software that Synaptic or Add/Remove Programs can look in to show you a list of what you can get).
For more information on how to install software in Linux, I recommend aysiu's website, click on the following link, [Install Software]("http://www.psychocats.net/ubuntu/installingsoftware.php")
Here's a link to the whole site too, [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php) there's lots of help there  that aysiu has gone to a lot of work  for. It explains things  about Ubuntu in easy-to read style with some illustrations for people who are new to Linux. It's good for experienced users too. :D

Regards, Herman :D

---

