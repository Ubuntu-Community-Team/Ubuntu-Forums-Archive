---
title: "Dos Ubantu"
date: 2006-09-27
forum: Installation &amp; Upgrades
---

### Post by TheFlamingBush on 2006-09-27
ok here goes. Ive been trying to install Ubantu 6.06.1 for 2 days now, almost non stop. 

I have tried the cd's, but nothing. I did manage to get dos prompt when i burnt the DVD iso, have i burnt things wrong?....because ive gone through about 6 dvd's now, and several cd's and the closest ive come is the dos prompt.

I tried the DVD, and it burnt fine. I have winrar on my XP, and the iso image downloaded as a winrar extention. I then extracted it to the desktop and burnt the folder. 3.something  GB's i think, nothing seemed to be missing. But when i booted the cd/dvd drive it began with dos. 

I thought it might have been me...and probably is, more likely something simple , like me!....so i tied to download my 8.1 suse professsional onto my toshiba satellite L20-300. No problems, straight into yast, and bingo....although nothing was supported of course, and no connection was possible to the net, so that was pointless as far as being useful. But it proved that it was possible. It has to be the way i burnt! the DVD's....or is there something im missing?....i used nero xpress to burn a bootable data dvd, which it duly did. Do i have to extract a particular file to get the boot to work?.....or do i need to change something in the bios to bypass the dos?


I have set aside 10 gigs in fat 32, to pop linux onto it and learn how to use the distro.....but so far i have to say im very disappointed....but im a trier!

I guess i could wait for some cd's or the DVD to be sent, but by then the snow will be on theground, and the new version will be out.....please please help me! im a newb with Linux really, moderately computor savy, but totally end user orientated at this stage....i wanted to learn a bit and then maybe move over to Linux totally, as a form of solidarity.

---

### Post by onioneater36 on 2006-09-27
When burning the DVD from the ISO you should not use any extraction program to make a folder and then burn a bootable disk.  This is why it is booting into DOS.  An ISO is a complete image.  If you have NERO there should be an option called BURN CD/DVD from ISO image.  This is what you want to select and then browse to the ubunut-xxxx-xxx-x-i386.iso file (or whichever 1 you have) an Nero will take care of the rest.  Think of an ISO as a perfect snapshot.  Although you can extract files from it, you do not want to do this.

Let me know if that helped.

---

### Post by em3raldxiii on 2006-09-27
Mmm ... it sounds like you burned it wrong.  I'll pretend for a sec that you know nothing at all about burning discs and stuff, just so we don't miss anything.

1. Okay, first up.  You keep saying DVD.  But I wasn't aware that there were DVD disc images available.  From the Ubuntu website, they're all CDs.  This might be one of your troubles.

2. Lets just do this step by step to make sure we're all doing the same thing.  You want to go to this page:  [http://www.ubuntu.com/download]("http://www.ubuntu.com/download") and pick a country to download from.  Now, not every one of those servers will "look" precisely the same, but they should all have the same files available.

3. Download the [COLOR="DarkRed"]PC (Intel x86) desktop CD[/COLOR] for your Toshiba computer.  It will be a file ending in .ISO

4.  Open your burning program (like NERO), and select "burn image to disc".  This is probably the step where you made the error.  You don't burn the ISO like a normal file, it is actually a disc "image", or an identical replica of a CD, including all the information that is "outside" the regular data area of the disc.  You DO NOT need to extract anything from the file, nor should you have to "open" the file in any way.  You open your burning program, and you choose "burn image to disc" or something like that, it will ask you which file, you pick the correct file (the ISO file), and click burn.  And remember, this is a CD, not a DVD :D

5.  When the CD is done, you are ready to go.  Shut down, put the disc in the drive, and boot.  You should get a menu.  Choose to boot Ubuntu.

6.  Ubuntu will boot "live" ... that is, it is NOT actually installed, it is running directly from the CD ... and on your computer it will likely run a little slow.  Now, on the new desktop should be an icon that you can click on to install Ubuntu.

7.  During the installation, you will be asked how you want to install Linux ... and you will likely have to muck about with partitioning the free space for Linux to use.  If you aren't sure what this is about, please post here and we will direct you :D

Good luck!

---

### Post by meng on 2006-09-27
There IS a downloadable DVD for Ubuntu/Kubuntu/Xubuntu, but the steps are the same as for burning a CD from ISO. Under no circumstances should you try to create a "bootable" disk. Burning properly from an ISO image will create an inherently bootable CD.

---

### Post by em3raldxiii on 2006-09-27
LOL look at me how retarded I am ... I never actually scrolled to the very bottom of the page.  Ugh ... sometimes I feel like a doofus ;)

---

### Post by TheFlamingBush on 2006-09-28
> **em3raldxiii said:**
> Mmm ... it sounds like you burned it wrong.  I'll pretend for a sec that you know nothing at all about burning discs and stuff, just so we don't miss anything.

1. Okay, first up.  You keep saying DVD.  But I wasn't aware that there were DVD disc images available.  From the Ubuntu website, they're all CDs.  This might be one of your troubles.

2. Lets just do this step by step to make sure we're all doing the same thing.  You want to go to this page:  [http://www.ubuntu.com/download]("http://www.ubuntu.com/download") and pick a country to download from.  Now, not every one of those servers will "look" precisely the same, but they should all have the same files available.

3. Download the [COLOR="DarkRed"]PC (Intel x86) desktop CD[/COLOR] for your Toshiba computer.  It will be a file ending in .ISO

4.  Open your burning program (like NERO), and select "burn image to disc".  This is probably the step where you made the error.  You don't burn the ISO like a normal file, it is actually a disc "image", or an identical replica of a CD, including all the information that is "outside" the regular data area of the disc.  You DO NOT need to extract anything from the file, nor should you have to "open" the file in any way.  You open your burning program, and you choose "burn image to disc" or something like that, it will ask you which file, you pick the correct file (the ISO file), and click burn.  And remember, this is a CD, not a DVD :D

5.  When the CD is done, you are ready to go.  Shut down, put the disc in the drive, and boot.  You should get a menu.  Choose to boot Ubuntu.

6.  Ubuntu will boot "live" ... that is, it is NOT actually installed, it is running directly from the CD ... and on your computer it will likely run a little slow.  Now, on the new desktop should be an icon that you can click on to install Ubuntu.

7.  During the installation, you will be asked how you want to install Linux ... and you will likely have to muck about with partitioning the free space for Linux to use.  If you aren't sure what this is about, please post here and we will direct you :D

Good luck!


you guys are fantastic! :)....thankyou for all your help....i shall give it a go!....im using a Toshiba laptop satellite L20-300, and ive read some dodgy stuff about the suse 10.1. ...

I posted a similar note on the suse site, and you guys most definately won! ;)....great help!, and i shall try burning a new image.

thankyou again emerald, meng, and onion, I may well be back for more help asap! since im a total newb when it comes to linux.

Here goes! :KS

---

### Post by TheFlamingBush on 2006-09-28
> **TheFlamingBush said:**
> you guys are fantastic! :)....thankyou for all your help....i shall give it a go!....im using a Toshiba laptop satellite L20-300, and ive read some dodgy stuff about the suse 10.1. ...

I posted a similar note on the suse site, and you guys most definately won! ;)....great help!, and i shall try burning a new image.

thankyou again emerald, meng, and onion, I may well be back for more help asap! since im a total newb when it comes to linux.

Here goes! :KS


one quick question. Once ive booted the live dvd, and have Ubantu running on my system, when i choose to install, can i choose to install it on the 3rd partition i have created before hand on my harddrive?.....i have two partitions in NFTS, with about 50 gig combined for windows. and set aside 10 gig for linux in a 3rd partition , formatting it in FAT32. 

So when i install Ubantu can i just pop it in the 3rd partition?

and if so, how do i then choose the boot priority between windows and Linux when the comp boots?

This is important as i do not want to lose any data in my windows partitions, C and E, (D being my cd/dvd drive), but want my F drive to be the 'Linux box' part of my hard drive.

I cant really afford to lose my windows stuff....Just yet! ;)

---

### Post by meng on 2006-09-28
Short answer: yes the install program will allow you to install it wherever you like, and will make space for a partition if a spare one doesn't yet exist. Consider installing onto ext3 rather than FAT32 (don't worry, the installer can reformat the partition for you). 10G is a good size for Ubuntu partition, so long as you don't plan on storing heaps of data there. GRUB will be installed to the master boot record, allowing you to select which OS to use at boot-time.

---

### Post by Lord Illidan on 2006-09-28
You also need a swap partition. My advice is to use the installation partitioning tool to resize the 10 GB partition to 9 GB, and use 1 GB for swap space.

You can use what drive you want, just make sure you don't select the Installation choice "Erase entire drive"!!

Also, don't use fat32, use ext3. Windows can read from it with a special driver.

And do take backups of windows beforehand.

I have 6 partitions...and so far Linux hasn't damaged any!

---

### Post by TheFlamingBush on 2006-09-28
ok i'll give it a crack....i have to say im a little nervous about having grub on my comp, as ive just had to reinstall my whole comp because Grub somehow managed to corrupt my boot.....oi think it was my fault being a little too gung ho deleting linux and trying to install a different flavour of it. 

The swap partition is made during instal no?.....i just have to state that i want one created inside the 10 gig drive no?......or doesnt it do this?.....i seem to recall suse and yast doing this during installation, but does grub function differently?....if so i can always use boot-it ng, a great little free prog for repartitioning doze and NFTS drives! ;)

another question if you can stand it, if i want to unistall Ubantu, is this easy?....does it unistall Grub so that i can get back to a clean drive from which to install a different flavour of Linux?.....i have a penchant to maybe try Kubantu and Suse 10.1 as well and see which one suits my requirements , but im a bit nervous about install/uninstall situations having been stung only recently.

Thanks again guys! :)

---

### Post by Lord Illidan on 2006-09-28
> **TheFlamingBush said:**
> ok i'll give it a crack....i have to say im a little nervous about having grub on my comp, as ive just had to reinstall my whole comp because Grub somehow managed to corrupt my boot.....oi think it was my fault being a little too gung ho deleting linux and trying to install a different flavour of it. 

another question if you can stand it, if i want to unistall Ubantu, is this easy?....does it unistall Grub so that i can get back to a clean drive from which to install a different flavour of Linux?.....i have a penchant to maybe try Kubantu and Suse 10.1 as well and see which one suits my requirements , but im a bit nervous about install/uninstall situations having been stung only recently.

Thanks again guys! :)

If you want to try another flavour of Linux, then all you have to do is overwrite the partition..The distro will then overwrite Grub with it's own version. And if by any chance Windows does not get included in grub, it is easy to add it in.

---

### Post by TheFlamingBush on 2006-09-28
thanks LI! :)

---

### Post by Lord Illidan on 2006-09-28
> **TheFlamingBush said:**
> thanks LI! :)

np..please do post again if it works!

---

### Post by TheFlamingBush on 2006-09-28
I certainly will, nice to hear some success stories as well as the disasters ;)

---

### Post by em3raldxiii on 2006-09-28
Just to be thorough (again, I'm probably rehashing stuff you already know, but I'd rather rehash than miss something completely).

GRUB is your boot handler, it does nothing else.  When Ubuntu (or any other Linux flavor) is installed, it will install either GRUB or LILO which is another boot loader.  If you are going to change the Linux installation on your 10GB partition, just "think" of it's partition as a blank partition and let your new version of Linux handle overwriting it.  A new version of GRUB (or LILO) will be installed with it.

SWAP:  It's a general rule of thumb to go with at least double your RAM size for this partition.  Your Linux installer can automatically configure your SWAP drive for you, or you can manually make adjustments.

Primary versus Logical:  I generally go for ALL primary partitions.  There are some good arguments for using logical partitions, but I find I have less headaches if I go with all primaries.  So my NTFS partition, my FAT32, my EXT3, and my SWAP are all independent primary partitions.

EXT3:  This is the default (and probably best) partition for you to use in your general Linux installations.  It has a number of benefits over NTFS, and Linux is very comfortable with it.  You can safely choose to use EXT2 as well, but it doesn't have journalling which is good to have in the event of crashes and for other security stuff. Another filesystem format you may look into at some time is ReiserFS.  From what I have read, it is great for handling a lot of small files because it's faster for file-in-file-out access.  Not sure about it's journalling capabilities, but I seem to remember that it does not support that feature.

If you want to go back to a purely Windows computer, that's another matter since I've never done it.  I imagine there are simple tools available to return your MBR to it's original Windowsy state.

Mmm ... I should mention that all of this was off the top of my head, so please everyone, feel free to correct me if I am wrong :D

---

### Post by Johan! on 2006-09-28
[Here]("http://www.psychocats.net/ubuntu/index.php") you can find excellent guides on how to install ubuntu.

I'm sure it will help you.

---

### Post by randell6564 on 2006-09-28
> **Lord Illidan said:**
> You also need a swap partition. My advice is to use the installation partitioning tool to resize the 10 GB partition to 9 GB, and use 1 GB for swap space.


Hi!  Ubuntu will create those partitions automatically if you tell her to just use the Fat32 space that she has recognized.

---

### Post by TheFlamingBush on 2006-09-29
well thanks to you all i now have my very first Linux distro installed on my laptop and am writing to you from my Toshiba L20-300. 

I partitioned it as you had suggested guys!....although i made a slight variation. I went with 30 gigs in my doze, as it needs it with all those security programs cluttering up the place. I stuck 14 gigs in a fat 32 second partition that is shared between the two operating systems, and then  popped 8 gigs in my third primary in an ext3 format.  I added two further partitions, one a small 3.5 gig home extended partition, and the other slightly over a gig in a logical swap partition.

Ubuntu operated in a faultless manner, during the entire install. I have tested both OS's, and have integrity in the hard drive......happy camper!!!! :)....and UBUNTU!....I am what i am, because we are whats we are!....!!!

thanks guys for al the help with the instal, and now its a steep learning curve, over the next 6 months, all around!.....im picking it wont be the last time im pickin your collective brains. Firefox works beautifully and i will be checking out thunderbird tonight...i got used to those two on windows, and the zilla machines were a good reason i decided to make a foray into the world of Linux, that and the excellent community! ;)

I still have to work out where everything goes, and things like downloads and such like arent intuitive yet....but in time im sure we can make it so.

Once again thanks guys/gals for all the help in my darkest hours....i havent slept for over 48 hours but at least its all working beautifully now! :)

any progs you think are essential, and things that i need to do initially to ensure the experience remains a positive one?

---

### Post by randell6564 on 2006-09-30
Hi FlamingBush!  Glad ya got it going!! I Love Ubuntu!  I Love Linux!  I was just sitting here surfing the net and thinking about how nice it is to not have to worry about viruses, or hackers!  

My only advice is that you update, though you probably have already done that. Play around, have fun!  You will learn fast and never look back!

The Ubuntu community will be here when you need them.  Soon YOU will be helping others!

Peace!

---

### Post by em3raldxiii on 2006-09-30
Some next steps to think about (no particular order, and no particular priority)

1.  Think about whether you want to use 3rd party repositories.  They can get you cutting edge software, and some fantastic features that you can't get elsewhere.  But they can also cause (relatively minor) complications (like having unrecognized versions of critical software packages).  Also, you may want to enable your Universe and Multiverse repositories, then surf through Synaptic Package manager to see what kindsa stuff are available.  If you don't know what something is, just ask us!

2.  Check out Compiz & XGL (or AIGLX) depending on your video performance.  I don't know how it will perform on your machine, but it is really quite impressive.  There are some videos on Youtube that should introduce you to the world of Compiz.

3.  Multimedia support.  Right now, your installation probably does not have all the possible 3rd party multimedia enabled.  This is because a lot of it comes with a hidden price-tag, or restrictions in the licensing (so it can't be distributed with Linux).  So you will probably want some codecs (MP3, DivX, that sort of thing).  You might want to check out a package called AUTOMATIX or EASYUBUNTU (you might want to use this forum or a search engine to find these resources).  They will help you get some of your multimedia applications up and running with a minimum of fuss.  One thing, though, Easyubuntu has a bug if you use it to install a certain plugin ... firefox media plugin maybe?  I dunno, but keep it in mind if you get any errors using Easyubuntu.

4.  WINE.  It's a software package that allows you to run MANY windows-only programs by "spoofing" a windows installation on your computer.  There is a lot of community support for WINE, and it's a very rapidly updated and evolving software package.  If you install it, Ubuntu will let you know when there are updates available.

That should give you some stuff to work on. :D

Some advice:  When using the console SUDO command, if you are trying to open a graphical application with it, use [COLOR="Red"]gksudo[/COLOR] instead.  It is "safer" to use than SUDO in those situations (see the link in my signature).  If you want to do a LOT of "sudo" commands in your command line, then you can do this:  [COLOR="#ff0000"]sudo su[/COLOR] which will enable "super user mode" and cut down on insane typing.  Remember to close that window when you are done though.  If you find yourself doing more and more command-line stuff, installa program called [COLOR="#ff0000"]yakuake[/COLOR] which is a customizable drop-down console like the one in Quake, Half-Life, etc etc.  It's really quite handy, and I use it all the time... and it beats clicking on icons to open terminal.

Okay enough ... LOL ... I like to see myself type ;)  Let us know if you have any questions or comments :D

---

### Post by TheFlamingBush on 2006-09-30
> **em3raldxiii said:**
> Some next steps to think about (no particular order, and no particular priority)

1.  Think about whether you want to use 3rd party repositories.  They can get you cutting edge software, and some fantastic features that you can't get elsewhere.  But they can also cause (relatively minor) complications (like having unrecognized versions of critical software packages).  Also, you may want to enable your Universe and Multiverse repositories, then surf through Synaptic Package manager to see what kindsa stuff are available.  If you don't know what something is, just ask us!

2.  Check out Compiz & XGL (or AIGLX) depending on your video performance.  I don't know how it will perform on your machine, but it is really quite impressive.  There are some videos on Youtube that should introduce you to the world of Compiz.

3.  Multimedia support.  Right now, your installation probably does not have all the possible 3rd party multimedia enabled.  This is because a lot of it comes with a hidden price-tag, or restrictions in the licensing (so it can't be distributed with Linux).  So you will probably want some codecs (MP3, DivX, that sort of thing).  You might want to check out a package called AUTOMATIX or EASYUBUNTU (you might want to use this forum or a search engine to find these resources).  They will help you get some of your multimedia applications up and running with a minimum of fuss.  One thing, though, Easyubuntu has a bug if you use it to install a certain plugin ... firefox media plugin maybe?  I dunno, but keep it in mind if you get any errors using Easyubuntu.

4.  WINE.  It's a software package that allows you to run MANY windows-only programs by "spoofing" a windows installation on your computer.  There is a lot of community support for WINE, and it's a very rapidly updated and evolving software package.  If you install it, Ubuntu will let you know when there are updates available.

That should give you some stuff to work on. :D

Some advice:  When using the console SUDO command, if you are trying to open a graphical application with it, use [COLOR="Red"]gksudo[/COLOR] instead.  It is "safer" to use than SUDO in those situations (see the link in my signature).  If you want to do a LOT of "sudo" commands in your command line, then you can do this:  [COLOR="#ff0000"]sudo su[/COLOR] which will enable "super user mode" and cut down on insane typing.  Remember to close that window when you are done though.  If you find yourself doing more and more command-line stuff, installa program called [COLOR="#ff0000"]yakuake[/COLOR] which is a customizable drop-down console like the one in Quake, Half-Life, etc etc.  It's really quite handy, and I use it all the time... and it beats clicking on icons to open terminal.

Okay enough ... LOL ... I like to see myself type ;)  Let us know if you have any questions or comments :D

Emerald that was some of the most useful information any new user could ever have wished to have read!....thankyou so very much for that dude!....:KS 

and as for everyone else!....UBUNTU!.....I am because you are!!!!8)

---

### Post by TheFlamingBush on 2006-09-30
Oh and Emerald....i thought your sig was cool! ... I shall remember that little pearl of wisdom! ;)

Thanks!.....

I used Automatix and it was awesome!....truly awesome!....taking what would have taken literally years out of the headache of updating and installing some pretty wonderous programs. 

I have a little problem with laying some commersial DVD's, but im sure there will be a fix somewhere...something about VOB's and totem not being able to recognize them...

anyway, thanks again! 

UBUNTU!

---

### Post by em3raldxiii on 2006-10-01
Totem has been unstable for me for awhile too ... try using a different player like VLC Media Player, or my personal favorite Gxine.  There is also Xine, Mplayer movie player, and my favorite audio program xmms.  Check them out when you have time to play :D

And I am very happy to hear that I helped you out.  I've only been at this for a few months too, so I know EXACTLY how you feel :D.  Keep up the good work, my friend :D

---

