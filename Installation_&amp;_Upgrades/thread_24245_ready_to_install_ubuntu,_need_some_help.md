---
title: "ready to install ubuntu, need some help"
date: 2005-04-06
forum: Installation &amp; Upgrades
---

### Post by Kassandra on 2005-04-06
Okay, I've seen this in some other threads but no one ever gets an answer.

Anways, I have Win XP Home installed on my main HD (40gb), and my second drive is used for all essencial things (Music, documents, pictures, apps, and games when I need to install them, as the second drive is faster) and is 60GB, currently with less than 200MB free over all 3 partitions. Anyways, I just used PartitionMagic to resize the C:\ windows main partition down to 5GB, it's basicly a clean install, with my core things installed and updates. Anyways, I'm still within the 1024 cylinder limit (Don't know if that matters at all for me, the system drive is from 2002, along with the rest of the machine, the second drive was added later) and I want to install Ubuntu. If I stay within the 1024 cylinder limit I have about 2.5GB to work with for Ubuntu, I figure that will be enough, afaik I can go over that anyways as long as the linux root is within the 1024, if that even matters. Anyways, A few months ago I installed Mandrake, when I realized I never really used it, I removed it, and the bootloader, and resized my XP partition to again take up the rest of the drive. Mandrake wasn't installed within the 1024 cylinder limit, it was installed in the last 5GB or so of the drive. Anyways, my problem is the bootloader. I want to use the windows bootloader and have found some tutorials to do so, but I'm not sure how I should partition the space for Ubuntu. I don't intend to give it any more then 5GB at the very most. Grub messed up my MBR before and it still isn't fixed. I never had any problems exvept I can't boot from my windows disc, setup crashes when it finishes loaded with a stop error saying it stopped to prevent dammage to the machine, I'm guessing this has something to do with the MBR still being messed up from Mandrake. I know about fixmbr but I don't want to have to format the drive again, and I can't get to the XP recovery console because I can't load the windows disc when I boot from it, like I said, it errors. Anyways, so I want to install Ubuntu, but I want to ensure I can use the windows bootloader, and that nothing will get messed up. I won't install unless I can use the windows bootloader.

Anyways, the last part of my questions/problems is partitioning. Since I resized the XP partition down to 5GB, I was intending to format the rest as NTFS and use it for storage and app installation. If I were to choose to have Ubuntu install to free space on this newly created partition, would it be bootable? Or should I resize the XP partition back to the full size of the drive and have Ubuntu resize it and create it's partitions for me? And then with the rest of the free space, still for windows, I could split it and fence off windows from the rest of the free space, for data storage.


Any thoughts/answers are appreciated. I will NOT USE GRUB.

Thanks in advance.

Oh, and just as a note, I'm no linux pro, so try to keep away from shell commands and such if possible, those things scare me! :cry:

---

### Post by ming0 on 2005-04-06
No GRUB eh? Will you use Lilo? ;)

I'm being a bit facetious, but I think that the people on these forums are much more knowledgable when it comes to GRUB. As far as I know, the Windows bootloader is inflexible and difficult to configure. Conversely GRUB isn't too bad, and if you get into a jam, people here can definitely help unjam you.

Furthermore, I can personally vouch for the coolness of Ubuntu's installer--it automagically knew I had a Windows install, and created a boot entry for it (I think you can easily put Windows on the top of the list, so that it is booted to by default).

Also, if you stick around, we can teach you to stop worrying and love the command line :)

Good Luck!

---

### Post by Shaggy on 2005-04-06
Well you would be able to to it yes and it would be bootable, although you would be in for more of a headache by using the windows bootloader IMO, but whatever floats your boat.

Personal recommendation though is to have a small partition (only a few hundred megs) formated as fat32 to use as a midway incase you ever have to move a file from windows to linux.  Have that be the second to last partition on the drive.

Also I'm kind of old hat but I still use a swap space partition as the last partition on the drive it should be about the size of your RAM.

---

### Post by WMCoolmon on 2005-04-06
If I read your post correctly, you've got two partitions on your first drive, one with 5 GB and WinXP, and the other is ~55 GB and NTFS. And now Windows setup won't run an closes with an error, after GRUB was installed.

I *just* installed Hoary today, but I've installed LILO, GRUB, LILO, and now back to GRUB for the distros I've tried, on this computer. On another computer, I tried to do what you were saying with the WinXP bootloader - and couldn't get it to work at all.

AFAIK when the bootloader is installed it completely overwrites the first 512 bytes of the disc. So, I'm a little hesitant to agree with you that GRUB is the problem, because otherwise the system wouldn't be bootable at all. Hoary has the option of choosing LILO or GRUB; I had to choose GRUB, IIRC, because it's not supported on AMD64, but it worked flawlessly on my system. It even autodetected my Windows 2000 install without any questions.

I suspect that MS has rigged their loaders to not work with Linux, and honestly, the Linux ones are just better; they've got more features and are better supported for multiple OSes. Not to mention that Mandrake may have used an older version of GRUB.

So; I'd suggest trying to install LILO, then GRUB; LILO is easier to configure, but you shouldn't be mucking around with either of the bootloader's configurations unless you're recompiling the kernel.

On the partition thing, I'd say it'd be better to set up the drive as you want it in PartitionMagic, since it's got a GUI and you're probably more familiar with it than the Ubuntu install. Remember that you should also have a swap partition; I think the recommended size is equivelant to your current memory size.

By the time it's all said and done, you should probably have three or four partitions on your drive:

Windows XP (System)
Windows XP (Applications)
Ubuntu (Ubuntu?)
Linux Swap partition

Edit: I'd suggest reading up on bootloaders in general; once you know what they do, they seem a lot less scary than they do at first. Even if you completely screw up your MBR, unless you damage the disk, you should be able to boot from a livecd and make a LILO config file to get you off the ground (Although it will involve console commands)

---

### Post by Hinko on 2005-04-06
I think installing GRUB again might solve your problem instead of worsening it. Did your computer come with a rescue partition? ie. a partition which had windows and a bunch of software installed as an image and was made unbootable? 

Anyway, usually you just install GRUB automatically, and everything works fine. I'd suggest leaving all your data on the 60GB disc. I'd say 5GB would work, but take 10GB if you can, gives you some more space to fiddle around with Openoffice and some nice other applications, as well as exploring both KDE and Gnome

Also, I'd use Swap as well. just take 500 MB, never hurt anyone, and the Ubuntu (Kubuntu) setup proces is userfriendly enough to guide you through the partitioning process.

---

### Post by Kassandra on 2005-04-06
*sigh* maybe ill install grub, but i'd really much rather use the windows bootloader, i prefer it by far and have used it for a thing or two in the past. Anyways, I've now split up the system disc (40gig master) into 2 partitions, 5GB for windows (about 850megs free on it right now, 1.5GB or so once i get rid of the ubuntu ISO on my desktop:p ) and the rest I partitioned into NTFS with the windows disc management utilities. I'd have used P-Magic but didn't want to go through it's confusing wizard. 

Anyways, could I just like, install ubuntu to the new partition I created, and it will still detect windows and all and configure the bootloader? 
-(If I use Grub, otherwise, afaik, I'd need to create a linux boot disc at the end of the setup process if I skip the bootloader install, or I install it to the linux root, and then I need to get the bootfile over to windows with another floppy or copy to another partition (I'd be creating one for linux/windows to share of course aswell) and move it to C:\ in windows, and add it's info the windows bootloader. As far as I understand it, that linux bootfile, in the windows bootloader, would sort of redirect the system to the linux root so it can start booting)-

Also, I noticed something when I was using the live cd's, Ubuntu live wouldn't mount my NTFS partitions on the other drive. In past live cd's I've used (Mandrake, Knoppix) it will mount them in read-only mode so I can atleast open up an mp3 or image or something. Is it just the Ubuntu live cd that's limited to this? Or will Ubuntu installed not mount them read-only either? I'm pretty limited if I can't atleast mount them read only, and I'll need to make a bigger partition for linux/windows to share in that case. I do have a FAT32 formatted partition that's 10GB on the second drive, but I use that for games and storage of non-critical things (movies, ISO's, things from the desktop when I formatted), as well as the windows pagefile (1792MB). I don't have a problem with giving linux about 5GB total (install, swap, share) but I don't want to give it anymore then that because it won't be my main OS. I plan to use it to learn linux and get used to it, and to have a faster experience when I need it (windows is good at using up resources and becomming slow), as KDE and Gnome are much faster and responsive (in my experience) than windows explorer (gosh I wish the KDE or Gnome people would do a windows port).

Anyways, another thing, could I setup the linux partitions now with partitionmagic, and then select them in the ubuntu install?

Thanks again.

[Edit] oh and about rescue partition, no, thank god, manufacturers that put those on systems usually don't even give you a standard OEM windows disc. This is a Gateway machine, good thing I didn't get a compaq, my friend has one and messed it up several times because of that stupid rescue partition[/edit]

---

### Post by Shaggy on 2005-04-06
During the installation if you use grub it will automatically detect your windows partition, and ask you if you want it in the boot list.  I'm pretty sure you can set it up to be mounted at boot time during the install but if it doesn't just ask here and we'll tell you how to get it mounted pretty quickly, and make it mount everytime ubuntu loads up.  Or look at one of the other posts people made regarding this as it has been asked before most likely.

When you turn on your computer after the install you will see a couple options, your Ubuntu boot ones, a memTest and lastly your windows partition.

By editing the menu.lst file in the /boot/grub folder you can change how grub works.  Do things like make the time out for it longer, and change the order that shows up on the screen.  Maybe you'll want to make windows your first option.

As far as using the windows boot loader goes, you've got the process down for it.

---

### Post by Kassandra on 2005-04-06
Yeah, cool, though so (about the windows bootloader) :)

Can I access the boot directory with the linux bootfile I'll need to bring over to windows if I go the windows bootloader rout? By that I mean can I get to it within gnome or kde logged in as root? Then I could just copy it to a partition or floppy. The ways I've read of doing it requires console commands lol, so if I can do it through the gui then all the better ;)

---

### Post by Shaggy on 2005-04-07
since there is not root user in Ubuntu I wouldn't advise being all about the GUI.  Use the console, its better for you.  Think of the console as you're veggies, you'll be a better man the more you use them.

---

### Post by ming0 on 2005-04-07
[QUOTE=Shaggy]you'll be a better man the more you use them.[/QUOTE]
Are we sure that [Kassandra]("member.php?u=13575") is a man?

---

### Post by Shaggy on 2005-04-07
Lets look at the numbers.

There are very few women computer geeks, out of those few even less of them are linux geeks.  Now take that small number and what are the chances that one of them is interested in a smaller distrobution, although the distro is very good quality.

Nil, and even if it is a woman, she will now be considered man for all time  :p

---

### Post by Kassandra on 2005-04-08
don't push it lol, i'm a girl, i'm a geek, and damn prowed of it lol. If nothing else it empowers me even more >:D 

Anyways yeah, again, i don't want to use the command line if at all possible. Believe me, I'll get used to it eventually, but for now, I just want it as simple as possible.

---

### Post by kassetra on 2005-04-08
[QUOTE=Shaggy]Lets look at the numbers.

There are very few women computer geeks, out of those few even less of them are linux geeks. Now take that small number and what are the chances that one of them is interested in a smaller distrobution, although the distro is very good quality.

Nil, and even if it is a woman, she will now be considered man for all time  :p[/QUOTE]

Just hold your thinking there...
I'm a girl, and not only am I a female computer geek - that's a Linux geek that's a super moderator on the Ubuntu forums... 

Ya might want to re-think that statement.  heh.  ;)

---

### Post by Ozitraveller on 2005-04-08
Lets just help Kassandra first, and you guys can fight it out!!!

Just joking!!

There are a couple of dual boot threads on this forum that might be worth checking on, and I think Machiner wrote a HowTo that is worth a read.

Here is a couple to start with:
How do you easily install Ubuntu for dual-boot with Windows?
[http://ubuntuforums.org/showthread.php?t=16287](http://ubuntuforums.org/showthread.php?t=16287)

Try my links below too!

---

### Post by Shaggy on 2005-04-08
Once again math has failed me, oh well nothing new. Before any other females come in correcting me, what I said earlier was meant in jest, hope no one took it seriously and if they did I'm sorry.

The thread traveler has some very good information though.

---

### Post by ming0 on 2005-04-08
[QUOTE=Kassandra]i don't want to use the command line if at all possible. Believe me, I'll get used to it eventually, but for now, I just want it as simple as possible.[/QUOTE]

don't worry too much--generally if people know that you don't have experience with the CLI, they will give you explicit instructions (for example, type **this** word for word on the prompt, and press enter). Once you start learning the basics, you won't be as scared :)

good luck!

---

### Post by Kassandra on 2005-04-08
=\ well, i better dive in soon then, i need to start getting windows back into full operational order (installing my non-main apps / games) which means moving alot of stuff to that new partition on the system drive.

---

### Post by WMCoolmon on 2005-04-09
[QUOTE=Shaggy]since there is not root user in Ubuntu I wouldn't advise being all about the GUI.  Use the console, its better for you.  Think of the console as you're veggies, you'll be a better man the more you use them.[/QUOTE]

AFAIK all you need to do to get the root user working is to assign it a password. But yeah, knowing how to use the console is very handy and you get used to it fast. Once you get used to ls, cd, mv, rm, and cp you may find yourself reaching for the console before Nautilus. ;)

---

