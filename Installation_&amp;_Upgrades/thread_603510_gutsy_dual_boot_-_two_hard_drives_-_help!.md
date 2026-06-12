---
title: "gutsy dual boot - two hard drives - help!"
date: 2007-11-05
forum: Installation &amp; Upgrades
---

### Post by george56 on 2007-11-05
I've upgraded my own machines to gutsy without a problem, but when I helped a friend, oh boy....

He purchased a new 500 GB Maxtor.  Following the instructions to install dual drive dual boot system [http://users.bigpond.net.au/hermanzone/]("http://users.bigpond.net.au/hermanzone/"),
 I disconnected the win xp master (only hard drive) and plugged in the new maxtor and treated it like the master drive (which it was).

When the Gutsy install was finished, I tried rebooting Gutsy.  Got the Grub error 2.

I tried to boot off the alternate CD and access the menu.lst but it won't start gedit (no "display".)

If I plug the Win XP disk back in as master and move Gutsy to secondary, Windows boots up with the maxtor Gutsy showing as removable drive and is inaccessible.

I know I'm almost there.  I have successfully installed Gutsy and it's sitting on the 500GB maxtor as a secondary master.  XP is primary master and it boots.

Is there something I should have done with the Maxtor install CD?  Or in the bios setup?  Or is it just an edit of a boot file somewhere?

I can't get past the grub error to do anything to the maxtor holding gutsy.  And I'm weak on booting Ubuntu off the CD to edit the installation.

Please help!!  I don't want this guy thinking my inexperience with Ubuntu is related to the product.

George :(

---

### Post by bulldog on 2007-11-05
Your error means```
2 : Bad file or directory type
    This error is returned if a file requested is not a regular file, but something like a symbolic link, directory, or FIFO. 
```
So the next question would be,which filesystem did you use to install ubuntu.
Can you give me a ```
sudo fdisk -l
``` from the live cd?
If not try to install it again,use manual partition,create a / partition 10GB file system ext3
create a swap 2GB file system swap
create a /home as big as you want file system ext3
Mount the partitions on the proper place and continue the install.

Remember though,when you install with the windows hdd dis connected,you won't get a windows entry in the menu.lst,you should do this manually.
Also GRUB will be installed to the maxtor hdd,so when you want to see grub,you have to boot from this hdd!!!

---

### Post by FreakTech on 2007-11-05
Why did you unhook the XP drive.  I have the exact same setup on my machine at home except I dual boot vista.  Gusty's installer has the option to set up the dual boot for you.  All you have to do is pick the secondary 500GB drive as the install destination.  This way you can leave you XP as primary drive and Gusty will install the Grub into the master boot record of the primary drive.

My experience with grub error 2 is that you need to reinstall grub.

1. Pop in the Live CD, boot from it until you reach the desktop.
2. Open a terminal window or switch to a tty.
3. Type "grub"
4. Type "root (hd0,0)" or whatever your drive config is.
5. Type "setup (hd0)", ot whatever your harddisk nr is.
6. Quit grub by typing "quit".
7. Reboot.

---

### Post by george56 on 2007-11-05
When I boot from the alternate CD, there's no option to run off CD, is there?  Will it go to a CD-based environment?  Or do I have to download the live cd of Gutsy?

I do have a 6.06 live cd. Should I boot from it and fix the file?

Or should I just install 6.06 and update to 6.10 and then 7.0 then 7.1?

Win XP is now the master.  Should I leave it that way?

---

### Post by FreakTech on 2007-11-05
Leave XP where it is at.  You can fix grub from the cd you have.  Boot into the CD enviroment and do the commands from terminal.  You may have to edit the menu.lst to include the xp boot since it wasn't in at time of install.

---

### Post by bulldog on 2007-11-05
> **george56 said:**
> When I boot from the alternate CD, there's no option to run off CD, is there?  Will it go to a CD-based environment?  Or do I have to download the live cd of Gutsy?

I do have a 6.06 live cd. Should I boot from it and fix the file?

Or should I just install 6.06 and update to 6.10 and then 7.0 then 7.1?

Win XP is now the master.  Should I leave it that way?
Run the dapper live cd,it make no difference :)
Copy the output of the fdisk command to the forum please,so we can have a look.
You can use the 6.06 live cd to reinstall GRUB as well.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```
Grub will be installed to the mbr of the hdd which contains Ubuntu.

---

### Post by george56 on 2007-11-05
i feel so stupid.  Which option do I pick to boot into CD?

they are:

1. install in text mode
2. oem install
3. install a command line system
4. check cd for defects
5. rescue a broken system
6. memory test
7. boot from first hard drive

---

### Post by bulldog on 2007-11-05
> **george56 said:**
> i feel so stupid.  Which option do I pick to boot into CD?

they are:

1. install in text mode
2. oem install
3. install a command line system
4. check cd for defects
5. rescue a broken system
6. memory test
7. boot from first hard drive

The first one will do :) oeps this isn't a live cd but an alternate cd

---

### Post by george56 on 2007-11-05
Here's the output of fdisk -l:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/hdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       60708   487636978+  83  Linux
/dev/hdb2           60709       60801      747022+   5  Extended
/dev/hdb5           60709       60801      746991   82  Linux swap / Solaris

---

### Post by george56 on 2007-11-05
i've got the live 6.06 running.

what should I do?

I ran the fdisk and grub gave me this:

grub> find /boot/grub/stage1
 (hd1,0)


xp is the master.

should I reinstall grub on the ubuntu disk?  do i have to change it to master?

what about menu.lst?

thanks.

---

### Post by george56 on 2007-11-05
I did the grub changes.  I rebooted and I'm back to getting the Error 2

---

### Post by bulldog on 2007-11-05
Well there seems to be a linux install on the second hdd,that's a good thing.
Reinstalling GRUB is something you can try,the hdd to reinstall is another problem.
If you reinstall GRUB to hdd 1,0 it will be installed on the ubuntu hdd,to see grub you have to boot from this hdd,otherwise it would boot into XP.
The boot order can be changed in the BIOS so that's no problem.
If you do so,and ubuntu will run,you have to make an entry for the windows in your menu.lst,no big deal to do,I can help with all of that.

If you install GRUB onto the first hdd 0,0 [windows] you won't have to change anything in the BIOS,but when you reinstall windows for some reason,you will lose your GRUB so you have to reinstall it again.

So the choice is yours,personally I would go for the first option,but it's your computer so you make the choice.

---

### Post by george56 on 2007-11-05
OK.  I'd like to try option 1.  Exactly what do I do?

---

### Post by bulldog on 2007-11-05
> **george56 said:**
> OK.  I'd like to try option 1.  Exactly what do I do?

Look into my previous post on how to reinstall GRUB.
This will reinstall GRUB on hd 1,0 [ubuntu] 
If done and if ubuntu will boot, we have to make an entry for windows in the menu.lst.

Some other thing,can you boot windows without any error?
Just curious

---

### Post by george56 on 2007-11-05
I did the grub commands and after typing setup (hd0) I got:

grub> find /boot/grub/stage1
 (hd1,0)

grub> root (hd1,0)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 d (hd0) (hd0)1+17 p (hd1,0)/boot/grub/stage
2 /boot/grub/menu.lst"... succeeded
Done.

I quit grub and am rebooting. I'll let you know what happens.

---

### Post by george56 on 2007-11-05
please see the output of grub as followed in your instructions.

I rebooted and immediately went into Grub error 2.

If xp is on first hdd, is that where grub is to give this message?

---

### Post by bulldog on 2007-11-05
I suppose you have both hdd's connected?
The find command stated (hd1,0) and you did the setup command setup (hd0)?
If so GRUB is installed on the windows disk.
No problem but if you reinstall windows in the future,you need to reinstall GRUB as you did now.
So copy and paste the commands to a text file for future reference.

The error two is something I can't understand,grub find a linux partition and find the boot files,but gives the same error.
Maybe do a fresh reinstall on the same partitions and let the windows hdd connected.
Or maybe you can find something here,

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

To reinstall your windows MBR,popin the windows cd and go into recovery console.
When you're logged in in your windows type fixmbr and after that fixboot
This will let you boot windows again.

---

### Post by george56 on 2007-11-05
OK.

The grub on hd(0) was the command as it read in the instructions. I will do a Ubuntu reinstall on the second drive.

What about the grub on the xp drive?  How do I remove it?  Isn't it going to prevent me from booting anything?  

And that link was the place that started the mess about disconnecting the xp drive.

---

### Post by logos34 on 2007-11-05
The 40gb and 500gb are your primary master and primary slave, hda and hdb.  Did you remember to set the jumper on the back of thje maxtor for 'slave' after you reconnected windows?  Or are both drives set for 'cable select'?

---

### Post by george56 on 2007-11-05
cable select

---

### Post by Herman on 2007-11-05
Hello george56              :)
>  What about the grub on the xp drive?  How do I remove it?  Isn't it going to prevent me from booting anything?  
 It is quite okay to have GRUB installed in both hard drives, because it only means there is a little code installed in the MBR, which is not part of the Windows file system, so it does not affect Windows. Windows only needs its boot sector, it doesn't really care about the MBR at all.

>  And that link was the place that started the mess about disconnecting the xp drive.:confused:
Please tell me where in my website I have told anyone they need to unplug any hard drives to install Ubuntu?
Perhaps there is something else there somewhere I have written that is confusing or ambiguous or not explained well, but I don't think there is anywhere where I have ever recommended unplugging hard drives.
If you can tell me where this error is then I will correct it so no-one else will make the same mistake too. Thanks in advance.

I think that logos34 is on the right track looking for a problem with the way your hard dirves are plugged in and jumpered.
Please check that you have a 'cable select' IDE cable.
A 'cable select' IDE cable should have the blue plug plugged in to the motherboard, the black plug goes to the master hard disk and the grey plug should go to the slave hard drive.
Please recheck you jumpers and make sure thy are set to 'cable select' if you have a 'cable select' IDE cable.
Also, please check the condition of the cable too. :)

If you have an IDE cable with black plugs then it is an non-cable-select IDE cable and you should set your jumpers to master and slave positions.
If you have an old 40 conductor IDE cable throw it away and but a new 80 conductor IDE cable, they are very cheap and 40 conductor cables are not recommended anymore.

Finally, recheck the way your hard drives are detected in your BIOS and make sure that all looks okay. :)

FreakTech, bulldog and logos34 were already giving you good instructions. :)

Regards, Herman :)

---

### Post by Herman on 2007-11-05
Just another thought, 500 GB is quite a large hard drive. I wonder if there's any problem with your BIOS being able to cope with such a large hard drive?


Installing in a smaller partition might help, (like less than 137 GB), and making a data partition in the remainder of the drive.
Or maybe try making a separate /boot partion, that might even be a better suggestion.

Regards, Herman :)

---

### Post by PhatKat on 2008-05-06
Hi there! I ama very new Ubuntu user - just build me a buntu box last week and am using gutsy. Now i have read some threads here but my questions are:

1) Can i dual boot with 2 x SATA HDDs with 
a) gutsy already installed
b) XP Home already installed

2) Before editing anything: i should disconnect the windows HDD right? Or all connected? 

3) All/any editing should be done via booting with the buntu live cd and then in terminal - am i correct to say this?

4)What would be different if i wish to dual boot with 2 HDDs, one with gutsy and the other with hardy? (just for info)

Thanks and i am using less of windows since my buntu box powered up hehe

---

### Post by Herman on 2008-05-06
:) Hello PhatKat,
> just build me a buntu box last week and am using gutsy.
 Good! :)
> 1) Can i dual boot with 2 x SATA HDDs with 
a) gutsy already installed
b) XP Home already installed
Hmmm, You just said you already have Gutsy installed.  I guess you mean you want to add another hard drive with Windows XP already installed in it? Yes, certainly you an dual boot. 
Here are two links about that I like, ,[**Dualboot Two Hard Drives**]("http://www.ubuntuforums.org/showthread.php?t=179902"), and,[CENTER][LEFT][**Trying to Dual Boot, using two HD's**]("http://www.ubuntuforums.org/showthread.php?t=120994")
                                                                                                                                                                                                  [/LEFT]
[/CENTER]
[RIGHT][LEFT]Particularly note post #6.[/LEFT]
[/RIGHT]
> 2) Before editing anything: i should disconnect the windows HDD right? Or all connected? 
It would be easier to just leave both of your hard drives connected.
> 3) All/any editing should be done via booting with the buntu live cd and then in terminal - am i correct to say this?
Not necessarily. If you want to edit  your /boot/grub/menu.lst you can do that easier with Ubuntu booted. 
If you can't boot Ubuntu then you might need to use the Live CD to fix Ubuntu's menu.lst so you can boot.
> 4)What would be different if i wish to dual boot with 2 HDDs, one with gutsy and the other with hardy? (just for info)
 Well, I like to do that, I think that's a great way to do things. That's how I do it, I even have a few Feisty installs in a few of my computers. If everyone did that there would be a lot fewer problems and complaints here in Ubuntu Web Forums about failed upgrades and installations gone wrong.
That's a more cautious approach, because that way I can try Hardy Heron out for a while to make sure it will do everything I need it to be able to do.
For example, when Gutsy Gibbon first came out and most people upgraded from Feisty to Gutsy, I found that I couldn't make a presentation CD in Gutsy that will automatically open in a Windows PC . They had changed some things in the CD writing commands.
Even though everything else about Gutsy is better, I still need Feisty for making these special CDs I make which certain people at my work really like. 
Normally though, the latest version will be the one you'll probably use the most. I think Hardy Heron has a lot of great improvements over Gutsy Gibbon. Some day when I'm ready I'll install Interpid Ibis and start testing that out too. In computers with lots of hard disk space, I'll keep Feisty, Gutsy and Hardy and install Interpid Ibis after those, but I won't transfer much data into it until it has been released in another six months or so.
In computers without so much spare hard disk space, I'll keep Gutsy and Feisty, and when Interpid Ibis is almost ready, I'll overwrite Gutsy with Interpid Ibis, but keep using Hardy as my main operating system.
My wife likes having her computer set up with two Ubuntus too. That way if she gets in any trouble with one system while I'm away she can simply boot into another Ubuntu and keep on doing whatever work it is she's trying to get done. I can fix her other system when I get home. Actually, it's been a long time since she's had any problems at all, but it's nice to know she can do that if anything ever does go wrong.
Another thing about having two Ubuntus, if you're a new user, is you can use one system as a 'sandbox', for learning Linux in and trying out commands or software in that you're not familiar with. You can learn Linux a lot faster without worrying about harming your 'good' installation. If you try out some idea and if it does something to the operating system you don't know how to undo yet, it only takes half an hour to re-install. For some people that would be a good reason why it would be nice to have two Ubuntu installs. 
I think Hardy Heron is great though, and I don't often boot back into my old Gutsy installation these days. 

I hope I have done an okay job of answering your questions, if not, feel free to rephrase a question and ask again, or ask new questions if you like.
Regards, Herman :)

---

### Post by PhatKat on 2008-05-08
Sweet and thanks for your reply! I am going to try this but just some final clarifications first :P  I had read the 2nd thread you linked to and in particular post #6 so in summary i should:

Go into terminal and do a:
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst

Text file pops up and i should copy and paste:
title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

save, close and reboot? Can i do all this via booting with the live cd and both HDDs connected? Did i get this right? Hmm as for my last question: eventually i want to ditch Windows entirely but for now until i learn to be more adept with buntu, i have it as an fall back option :P I have tried Hardy and the wifi is working more stably than gutsy and i wish to ditch Windows for hardy. Also been  exploring Xubuntu/Kubuntu hehe So how would terminal/text differ if i wish to dual boot Gutsy/Hardy then? Oh ya i also intend to assemble some low cost buntu rigs for my nephews/nieces but how does one make the wired connection with an ADSL2 modem work? Drivers and all? Or does it come packed with the OS and all one has to do is to enter the ISP details yada yada?

P.S oh ya my humble 1st buntu box
AMD x2 4000+ brisbane
Biostar K8M800 
1GB DDR2 667 Kingston 
Samsung 80GB (Gutsy)
Seagate 80GB (XP)
Sony DVD-RW

---

### Post by Herman on 2008-05-08
> Can i do all this via booting with the live cd and both HDDs connected?
:) Yes you can!
Here is a link to explain to you how to mount your Ubuntu partition in a Live CD and gain access to your /boot/grub/menu.lst (and other important files too), for editing, [Mount a Ubuntu ext3 or reiserfs filesystem.]("http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD")

> Did i get this right? Hmm as for my last question: eventually i want to ditch Windows entirely but for now until i learn to be more adept with buntu, i have it as an fall back option :P I have tried Hardy and the wifi is working more stably than gutsy and i wish to ditch Windows for hardy. Also been exploring Xubuntu/Kubuntu hehe So how would terminal/text differ if i wish to dual boot Gutsy/Hardy then? Yes, I think that looks right at a quick glance.

You won't need to worry if you install another *buntu as it will automatically set itself up to boot your existing Ubuntu installation.
Then later, optionally when you feel like it, you can edit your new installation's /boot/grub/menu.lst with an [Operating System Entries for Multiple Booting More Linux Systems]("http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems"). This is just so the other *buntus or Debian or other Linux can have a kernel update without you needing to manually update any GRUB menus.
> Oh ya i also intend to assemble some low cost buntu rigs for my nephews/nieces but how does one make the wired connection with an ADSL2 modem work? Drivers and all? Or does it come packed with the OS and all one has to do is to enter the ISP details yada yada?
It will just work, all you have to do is plug in your ethernet cable to your motherboard's ethernet port.
If the ADSL modem is connected and configured to your ISP then it will just instantly and automatically connect to the internet.
Whenever I travel with my laptop I can just plug it in to anyone's internet connection after I have the owner's permission and download my own email if I want or go anywhere on the internet.
Once you have [Configured Evolution Email]("http://users.bigpond.net.au/hermanzone/p5.htm#Configure_Evolution_Email") once it will work from anywhere in the world.

---

### Post by PhatKat on 2008-05-09
Hi Herman! Wow it was a sucess so thanks a mil ^^ Ok in the end this is how i did it:

1) Disconnect sata HDD with Windows
2) Boot into sata HDD with gutsy
3) Go into terminal and do a:
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
4)Text file pops up and i copy and paste:
title Windows XP
root (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

save, close and reboot
5) You get a Windows OS prompt error (HDD disconnected)
6) Shutdown and connect the Windows HDD up
7) Restart and this iss what i got:
Grub loading....
Press esc to enter menu
Menu shows up with Windows, buntu, buntu with some memtest yada yada

My only concern is: i havee like 3 secs to press esc failing which i auto boot into windows :P Is there a way for the menu to show up w/o having to press esc? Also can i make buntu the default OS to boot into if the user does not press anything? Thanks again!

---

### Post by Herman on 2008-05-09
:) You just need to delete the '#' (hash symbol or 'comment', from before the command 'hiddenmenu', in your /boor/grub/menu.lst file. 

[menu.lst example file with links]("http://users.bigpond.net.au/hermanzone/p15.htm#Fiesty_Fawns_new_menu.lst")

Also, Ubuntu should already be the default operating system that gets booted if the user doesn't press any key during boot-up. If you still want to leanr how to customize which operating system boots by default, see this link, [default        0]("http://users.bigpond.net.au/hermanzone/p15.htm#osprefernc")

Regards, Herman :)

---

### Post by PhatKat on 2008-05-11
Whoa those 2 links were outstanding and my desire to boot up to buntu by default is fulfilled so thanks again ^^ On my way to ditching windows soon and at the very least have one rig in my pace dedicated to linux hehe Oh ya one last question: how should i edit my /boor/grub/menu.lst file when the day comes i wanna ditch windows from my 2nd HDD and dual boot Hardy or even Fedora 8?

---

### Post by Herman on 2008-05-11
> one last question: how should i edit my /boor/grub/menu.lst file when the day comes i wanna ditch windows from my 2nd HDD and dual boot Hardy or even Fedora 8?:) Sure, you can edit your /boot/grub/menu.lst file anytime you like.
You can even do it just for fun and try out some of the tricks you can do with it like adding your own colors to the menu or making your own beautiful splashimage for your GRUB menu. There are lots of ways you can personalize and customize your GRUB by editing your /boot/grub/menu.lst file. Just read [GRUB Page]("http://users.bigpond.net.au/hermanzone/p15.htm") and have fun.

It's a good idea to get yourself a copy of [Super Grub Disk Official]("http://www.supergrubdisk.org/") first though, in case you make a mistake and have trouble booting. Super Grub Disk will help you boot again so you won't be stuck.

---

