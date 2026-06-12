---
title: "Grub Error 17: secondary hard drive not in boot order"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by TimPy on 2008-01-31
Hi.

I recently installed Ubuntu, and was booting it up for the first time when I recieved this error: Grub ERROR 17 

My bios recognizes my G: drive where I put ubuntu, but it is not an option in the boot order.

From reading other threads, I think that my bios needs to be able to select my G: drive as the boot option, instead of C:(where Windows is).

First, is this my problem, if not, what is my problem?
and second, If it is my problem, how do I add my G: drive as an option to my boot order.

I also can't boot to xp,  although I can use the live cd.

Thanks for the help!

---

### Post by TimPy on 2008-01-31
Just had another idea...

My C: drive is my master drive, and G: is my slave... maybe if I switch those, G will appear on my boot list. I haven't tried it yet though.

---

### Post by confused57 on 2008-02-01
> **TimPy said:**
> Just had another idea...

My C: drive is my master drive, and G: is my slave... maybe if I switch those, G will appear on my boot list. I haven't tried it yet though.
Ubuntu doesn't recognize your partitions/drives as C:,D:,E:, etc, but as /dev/sda, /dev/sdb,etc...you can open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
-l is a small "L"

If your Windows doesn't boot, either from grub or Windows boot, you can reinstall Window's IPL to the mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
You can do this with a Windows install cd(not a recover disk), press "r", then enter FIXMBR or Super Grub Disk can repair your Windows boot.

You might also  try switching your drives, reinstall Ubuntu...I have Ubuntu as master and Windows as slave:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

You could also try installing grub's IPL to your Ubuntu drive's mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
for example, if "find /boot/grub/stage1" shows "root (hd1,0)", you would:
```
root (hd1,0)
setup (hd1)
```
Then switch your hard drives, if you get a grub boot menu, highlight your Ubuntu entry, press "e", then highlight the line with root, press "e" again, change root from (hd1,x) to (hd0,x), press "enter", then "b" to boot...x means leave this value as it is.  This change is temporary(if you decide to try it...you wouldn't have to reinstall Ubuntu if it does), but it's easy to make it permanent.  If you  can set your bios to boot first to your Ubuntu drive, you shouldn't need to switch your drives after installing grub to your Ubuntu drive's mbr with the live cd, then  try the "e" method to boot Ubuntu, if you get a grub boot menu.

Note:  Before attempting any of the above, read the instructions in this thread, you may just need to change a few settings in your bios:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

Description of grub error 17:
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

---

### Post by TimPy on 2008-02-01
Okay, wow, that is a TON of stuff to look at and lots of possibilities to try. BUT I think I do know the problem from the setup I have...

Sorry, but I didn't understand what code you gave me did what... I don't think I should just start entering code into the terminal without knowing what it should do.

But I'm pretty sure I know what is wrong.   My G: drive (I know it's not that in ubuntu, I haven't quite figured out how to refer to it in Ubuntu terms, so that's what I'm calling it for now.) is recognized by my bios, has ubuntu on it, is slave, but cannot be chosen in the boot order. C: is master, has windows on it, and is the only hard drive in the boot order. I can't figure out how to put G: onto my boot order. I think that if I change G: to master, and C: to slave, it might show up there.  

That wouldn't mess up anything up would it?

Okay, the real question I have is: does grub need the ubuntu drive in the boot order?

To make sure I understnad my problem...

Grub is starting up from my master drive, C:. It's looking for itself in that same drive, but it's really in G:. I either need to change where grub looks through some grub code in the posts you gave me, or make G: my first boot order hard drive, so it looks for itself in the right place.

---

### Post by adrian15 on 2008-02-01
> **confused57 said:**
> You might also  try switching your drives, reinstall Ubuntu...I have Ubuntu as master and Windows as slave:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)


Could you please explain him in a non-technical way that he need to edit groot value on menu.lst and then re-run update-grub inside a chroot from a live cd.

In my opinnion ubuntu thinks its hard disk is the third one but in fact is the second one (or something very similar to it)

So he needs something like: groot=(hd2,1) to be rewritten like this: groot=(hd1,1).

Thank you confused57.

This error 17 becomes he is trying to mount another partition from another hard disk. Probably a ntfs partition.

adrian15

---

### Post by confused57 on 2008-02-01
> **adrian15 said:**
> Could you please explain him in a non-technical way that he need to edit groot value on menu.lst and then re-run update-grub inside a chroot from a live cd.

In my opinnion ubuntu thinks its hard disk is the third one but in fact is the second one (or something very similar to it)

So he needs something like: groot=(hd2,1) to be rewritten like this: groot=(hd1,1).

Thank you confused57.

This error 17 becomes he is trying to mount another partition from another hard disk. Probably a ntfs partition.

adrian15
Thanks adrian,  good to hear from you...I'll see what I can do

TimPy,
   Let me first link you to what is probably the best guide for installing & booting Ubuntu:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
I know it's too much right now for you to start reading through this guide, but I'll try to link you to sections of it that may be helpful.

   This part of the guide explains how to set your bios boot order:
[http://www.users.bigpond.net.au/hermanzone/p1.htm](http://www.users.bigpond.net.au/hermanzone/p1.htm)
You bios may not be capable of booting first to your Ubuntu drive, similar to my Dell, which can only boot first to IDE1 master drive.  

> Grub is starting up from my master drive, C:. It's looking for itself in that same drive, but it's really in G:. I either need to change where grub looks through some grub code in the posts you gave me, or make G: my first boot order hard drive, so it looks for itself in the right place.
That's probably the case, you installed Ubuntu to your slave drive, but the IPL(initial program loader) for grub was installed to the mbr of your Windows master drive(overwriting your Windows IPL).   Are you getting a grub boot menu when you boot your pc or getting a boot menu, but get error 17 when you select Windows or Ubuntu?

If you're not getting a grub boot menu, see the thread I gave in my previous reply:
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)
it mentions setting your Ubunu drive controller to Auto and User(if available)

If you just physically switched your drives, you would probably get "Operating System not found" error, since grub's IPL isn't installed to your Ubuntu drive's mbr.  That's why I was suggesting installing grub to the Ubuntu drive's mbr(using the live cd), before you switch the location of the drives.  Then you "should" get a grub boot menu and can use the "e" method to try to boot.

> Sorry, but I didn't understand what code you gave me did what... I don't think I should just start entering code into the terminal without knowing what it should do.
That's a wise policy, but it can be beneficial to someone helping you to know the ouput of:
```
sudo fdisk -l
```
you can just copy & paste the command in a terminal, then copy & paste the output in your next reply.

Sorry, I don't have much time right now, but hopefully this will get you started and maybe someone else can chime in and assist you if I'm not around when you reply.

---

### Post by TimPy on 2008-02-01
Alright, I'll try this stuff as soon as I get a laptop to use....  Mine are currently being used by other people... I'll enter that first code and give the output...

The whole "Grub looking at the 1st, not second" hard drive, sound right, so I'll need to understand how to do that after I give you that output... but I can't get to the internet and the computer at the same time... (unless someone can tell me exactly how to install a WG111 wireless adapter, but I was going to save that for later...)

---

### Post by confused57 on 2008-02-01
> **TimPy said:**
> Alright, I'll try this stuff as soon as I get a laptop to use....  Mine are currently being used by other people... I'll enter that first code and give the output...

The whole "Grub looking at the 1st, not second" hard drive, sound right, so I'll need to understand how to do that after I give you that output... but I can't get to the internet and the computer at the same time... (unless someone can tell me exactly how to install a WG111 wireless adapter, but I was going to save that for later...)
Are you getting the error 17 and no grub boot menu or are you getting the error 17 when you try to boot Ubuntu from the boot menu?  If it's the former, have you tried checking the hard drive controller settings in bios(see one of my previous replies)?

If it were my computer, I would use another computer to burn a copy of the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

Boot up SGD & restore Windows IPL to the mbr, from the above link:
> 1. boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3.  Windows
   4. Fix Boot of Windows

Once you're able to boot Windows, then switch the physical location of your hard drives...reinstall Ubuntu, similar to this thread that I provided you earlier:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

This way, you can get your Ubuntu install configured, but you'd also be able to boot your Windows drive by connecting it as master if you're unable to get Ubuntu to boot.

I don't have wireless, but you might want to do a forum search for ndiswraper & your wireless card.

---

### Post by TimPy on 2008-02-01
Sorry I didn't answer the first two times you asked, but GRUB doesn't even load and it gives me a GRUB ERROR 17.

Although this is probably incredibly easy, I just want to make sure I'm doing this right....

1. Get Super Grub
2. Restore Windows boot. 
3. switch drives
4.reinstall ubuntu

I assume that between 3 and 4 I have to uninstall ubuntu.... or do I?

---

### Post by confused57 on 2008-02-01
> **TimPy said:**
> Sorry I didn't answer the first two times you asked, but GRUB doesn't even load and it gives me a GRUB ERROR 17.

Although this is probably incredibly easy, I just want to make sure I'm doing this right....

1. Get Super Grub
2. Restore Windows boot. 
3. switch drives
4.reinstall ubuntu

I assume that between 3 and 4 I have to uninstall ubuntu.... or do I?
You don't have to uninstall Ubuntu, just reinstall over top of your current installation...you probably already know this, but if you're using IDE drives, make sure the jumper is set to Cable Select or Master/Slave accordingly.  Still wouldn't hurt to check in your bios that the hard drive controllers are set to "Auto".

Hope you get this, all the Ubuntu sites are extremely slow for me at the moment.

---

### Post by TimPy on 2008-02-02
alright... I now completely (meaning mostly) understand what I need to do.  I need to recover the windows mbr.  I almost did it using my windows recovery disk- but then I couldn't find my admin password.  I can't get onto the internet  off live, so I can't use the one program I found that does it automatically.

Could you give me the exact commands to enter into the super grub disk to restore the windows mbr? I was having trouble finding exactly what to do, and I didn't want to mess up my computer anymore...  That way I can restore windows, and then follow a dualboot guide and overwrite the previous partition I had, making G: my master first this time before I install.

---

### Post by confused57 on 2008-02-02
> **TimPy said:**
> alright... I now completely (meaning mostly) understand what I need to do.  I need to recover the windows mbr.  I almost did it using my windows recovery disk- but then I couldn't find my admin password.  I can't get onto the internet  off live, so I can't use the one program I found that does it automatically.

Could you give me the exact commands to enter into the super grub disk to restore the windows mbr? I was having trouble finding exactly what to do, and I didn't want to mess up my computer anymore...  That way I can restore windows, and then follow a dualboot guide and overwrite the previous partition I had, making G: my master first this time before I install.
You won't be able to use the mouse in SGD, just the keyboard, but all you'll need to use are the up/down arrows and "enter"....and you don't need to enter any commands.

In the main menu when you first boot SGD, select "Super Grub Disk (No Help)"
2nd screen select "English Super Grub Disk"
3rd screen select "Windows"
4th screen select "Fix Boot of Windows"

Press "enter" after each selection above, then when you reboot your computer your Windows IPL should be restored.

---

### Post by TimPy on 2008-02-02
Okay, thanks.... I was under the impression that super grub disk's menu was... well I thought it was more of a commandline interface... thanks..
I figured that SGD would be keyboard only.

---

### Post by TimPy on 2008-02-02
Thanks again Confused57... I'm now going to follow a dual boot guide and install again....  and I know what to do if something bad happens now! I learned a lot, even though it was tough.

---

### Post by confused57 on 2008-02-02
> **TimPy said:**
> Thanks again Confused57... I'm now going to follow a dual boot guide and install again....  and I know what to do if something bad happens now! I learned a lot, even though it was tough.
Glad to help...Ubuntu & Linux are quite different from Windows, but you'll get the hang of it in no time at all.  I was just as clueless when I first started using Ubuntu, hence my username.
Good luck, enjoy using Ubuntu, & ask questions on the forum when you're having problems, people here are patient, experienced, and willing to assist new users.

---

### Post by TimPy on 2008-02-02
Alright....  I got my windows ipl back, installed ubuntu again, and only had my ubuntu drive as master drive in the system when I installed it.  I didn't have my windows as slave, but I don't think that should make a difference...  I still get the exact same error message. I took a closer look at the error message, and I saw "This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB"

When I partioned it, I may have had the wrong filesystem selected.  Which one should I be using?  Does this sound like a plausible cause of my problem? I'm pretty sure I had the filesystem as ext3   .   Thanks again Confused57.

---

### Post by confused57 on 2008-02-02
> **TimPy said:**
> Alright....  I got my windows ipl back, installed ubuntu again, and only had my ubuntu drive as master drive in the system when I installed it.  I didn't have my windows as slave, but I don't think that should make a difference...  I still get the exact same error message. I took a closer look at the error message, and I saw "This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB"

When I partioned it, I may have had the wrong filesystem selected.  Which one should I be using?  Does this sound like a plausible cause of my problem? I'm pretty sure I had the filesystem as ext3   .   Thanks again Confused57.
First thing you could try is boot up Super Grub Disk, select Linux(instead of Windows), then there should be an option to boot Linux...see if SGD can boot Ubuntu or if it gives the same error message.

Which option did you use to install Ubuntu, i.e. Use Entire Disk, guided, manual, etc?
How large is your hard drive & how old is your computer?  This may seem an unusual request, but it may be a factor...the reason I ask is that it could possible be related to grub error 18:
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by TimPy on 2008-02-03
I used the manual install from the live cd. I chose a 30(ish) (maybe  a bit larger) gigabyte partition of my 200 gigabyte hard drive.  My computer is about eight years old.  

This is starting to sound like the right solution too, because Ubuntu couldn't boot and gave me some generic error messages until I chose the manual boot, where I chose the exact partition of linux.  This gave me error 18: The selcted cylander excedes bios... or something similair.

So...  There were several solutions on the site you gave me... But I can't decide which one is right for me.  My bios boots up as "Compaq Computer Setup ... " something or other.  I might need to update like that site said. I also can't figure out how to set my hard drives to auto from user from my current bios.

Alright, thanks again. I'm not giving up on ubuntu yet.

---

### Post by confused57 on 2008-02-03
> **TimPy said:**
> I used the manual install from the live cd. I chose a 30(ish) (maybe  a bit larger) gigabyte partition of my 200 gigabyte hard drive.  My computer is about eight years old.  

This is starting to sound like the right solution too, because Ubuntu couldn't boot and gave me some generic error messages until I chose the manual boot, where I chose the exact partition of linux.  This gave me error 18: The selcted cylander excedes bios... or something similair.

So...  There were several solutions on the site you gave me... But I can't decide which one is right for me.  My bios boots up as "Compaq Computer Setup ... " something or other.  I might need to update like that site said. I also can't figure out how to set my hard drives to auto from user from my current bios.

Alright, thanks again. I'm not giving up on ubuntu yet.

I hope your bios has no less than a 137 Gb limit, as described in the thread I gave you.  What you could do is make a separate /boot partition entirely within the 137 Gb limit, you may need to resize one of your other partitions in order to do this.
You should be able to use Gnome Partition Editor(System---Administration---Gnome Partition Editor) to shrink your partition so you can make a /boot partition within the 137 Gb limit.

Select manual partitioning when you install, make a partition of approx 200-300 Mb, format as ext3, /boot as the mountpoint, primary partition...you'll also need a root partition, format as ext3, mountpoint / , not /root, logical partition(or extended) and a swap partition, format as swap, mountpoint swap, logical partition, probably no more than 1 Gb.

---

### Post by TimPy on 2008-02-03
Within the 137 GB limit?  My current partition is WAY under that... Like I said, It's around thirty, it may have broken the 33.8 GB limit, I'll have to check the size. I could try to do what you said, but like I said, my partition of linux is under 137 gig. (The other partition is the rest of the hard drive, I whouldn't need to change that, should I?)


Oh, and what's the difference between a primary and logical partition?

---

### Post by confused57 on 2008-02-03
> **TimPy said:**
> Within the 137 GB limit?  My current partition is WAY under that... Like I said, It's around thirty, it may have broken the 33.8 GB limit, I'll have to check the size. I could try to do what you said, but like I said, my partition of linux is under 137 gig. (The other partition is the rest of the hard drive, I whouldn't need to change that, should I?)


Oh, and what's the difference between a primary and logical partition?
To be on the safe side, make your /boot partition at the very beginning of your hard drive(approx 300 Mb), then you can make your root & swap  wherever you like. You shouldn't need to change anything about the other partition.
  You can only have 4 primary partitions on a hard drive, however one of them can be a primary extended partition, which can contain many logical partitions.  If you won't be needing any more than 4 partitions, then you can make all of them primary partitions.

---

### Post by TimPy on 2008-02-03
Although I have not tried what you said yet, I was just making sure that you thought the limit was the problem, even though my partition is 33.2  ....  wait, plus the 1 gig of the extended partition, just realized that, that would put it over the limit.  (My computer was purchased roughly 8 years ago.... around 2000, so it may have been produced before August 1999) 

But I was reading from the SGD link you gave me, and one person said that they changed their hard drive from user to auto   -   I don't know how to tell what my hard drive is set to, or how to change it.  Just making sure that isn't the problem.

Oh, and do you make a 'logical partition' by partioning off your primary partitions? (the 'extended' that I currently see for ubuntu now?)
 
Just making sure: The /boot shouldn't be extended off the /(root) partition, right?

and, just cause I'm curious, and learning loads I didn't know already... why should the /boot partition be at the beggining of my hard drive.

Thanks again!

---

### Post by confused57 on 2008-02-04
> **TimPy said:**
> Although I have not tried what you said yet, I was just making sure that you thought the limit was the problem, even though my partition is 33.2  ....  wait, plus the 1 gig of the extended partition, just realized that, that would put it over the limit.  (My computer was purchased roughly 8 years ago.... around 2000, so it may have been produced before August 1999) 

But I was reading from the SGD link you gave me, and one person said that they changed their hard drive from user to auto   -   I don't know how to tell what my hard drive is set to, or how to change it.  Just making sure that isn't the problem.

Oh, and do you make a 'logical partition' by partioning off your primary partitions? (the 'extended' that I currently see for ubuntu now?)
 
Just making sure: The /boot shouldn't be extended off the /(root) partition, right?

and, just cause I'm curious, and learning loads I didn't know already... why should the /boot partition be at the beggining of my hard drive.

Thanks again!
There's no need to be in a hurry to install, take your time, explore your options, make a game plan, etc.  There's always the possiblity of a bios update, which can be risky and render your computer possibly irreparably unbootable.  Have you tried going into your bios setup and exploring the settings for your IDE controllers to see if there is a way to toggle a setting to "Auto"?

Here's a couple of excellent links that explain partitioning basics:
[http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning](http://ubuntuforums.org/showthread.php?t=282018&highlight=partitioning)
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)
These links should explain primary vs extended partitions and how logical partitions relate to the extended primary partition.  The /boot partition wouldn't necessarily have to be at the very beginning of your hard drive, but within the limits of what your bios can boot.

---

### Post by TimPy on 2008-02-04
I have been looking through my bios, and tried every single option, and cannot find a way to change it to 'auto'....  I can't even figure out how to set my secondary hard drive in the boot order (I don't need to but still...) right now, the boot order has the third option as "primary hard drive (C:)" It's not refering to my old hard drive is it? It's not plugged in... But Grub boots so that wouldn't really make sense.  

I'm moving my partitions around now.  You've been lots of help, thanks.  Oh, and if it comes to updating my bios, I might have to reconcider ubuntu.

---

### Post by confused57 on 2008-02-04
> **TimPy said:**
> I have been looking through my bios, and tried every single option, and cannot find a way to change it to 'auto'....  I can't even figure out how to set my secondary hard drive in the boot order (I don't need to but still...) right now, the boot order has the third option as "primary hard drive (C:)" It's not refering to my old hard drive is it? It's not plugged in... But Grub boots so that wouldn't really make sense.  

I'm moving my partitions around now.  You've been lots of help, thanks.  Oh, and if it comes to updating my bios, I might have to reconcider ubuntu.
Good luck...the separate /boot partition "should" work, you won't have to update your bios.

---

### Post by TimPy on 2008-02-05
> Good luck...the separate /boot partition "should" work, you won't have to update your bios. 

And guess what?? It WORKED!!!! Ubuntu is now woking on my pc! ALright!  I didn't end up making a seperate /boot partition, I just made sure my entire ubuntu partition was within the 33.8 limit, and then made sure to put the files at the beggining of the partition, not the end, to ensure more stability.

Wow, okay, that was harder than I thought it would be.... Now I need to make it be able to dual boot, then I need to install my usb WG111 driver for the internet, and I'll be set on my 'ubuntuhood'!

---

### Post by confused57 on 2008-02-05
> **TimPy said:**
> And guess what?? It WORKED!!!! Ubuntu is now woking on my pc! ALright!  I didn't end up making a seperate /boot partition, I just made sure my entire ubuntu partition was within the 33.8 limit, and then made sure to put the files at the beggining of the partition, not the end, to ensure more stability.

Wow, okay, that was harder than I thought it would be.... Now I need to make it be able to dual boot, then I need to install my usb WG111 driver for the internet, and I'll be set on my 'ubuntuhood'!
Glad it worked...it shouldn't be any problem getting your dual boot setup, connect both your hard drives,open a terminal(Applications---Accessories---Terminal), enter:
```
sudo fdisk -l
```
-l is a small "L"...note which partition your Windows is on(probably the first, i.e. /dev/sdb1)

Then edit your menu.lst(menu.lst is short for menu.list):
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
in case you're unsure of the spacing, the above is:
cd..../boot/grub
sudo...cp....menu.lst....menu.lst_backup
gksudo...gedit...menu.lst

If Windows is on the first partition, add this entry to the very bottom of your menu.lst(after the line ###END DEBIAN AUTOMAGIC KERNEL LIST):
```
title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1
```
if Windows is on the 2nd partition, change root to (hd1,1)

quit & save...reboot your pc & see if you can boot into Windows.

Added:  Lowercase & uppercase matters in Ubuntu(& Linux) when entering commands.  Also, see this thread for making your grub boot menu visible & changing the timeout:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by Thecoolguru on 2008-02-05
IM HAVING MASSIVE PROBLEMS :(

I installed/semi-installed ubuntu. it didnt fully install and windows didn't show up when i booted even tho im pretty sure i installed ubuntu on my external. also, it wont do anything unless i put the ubuntu cd in. does this mean that i have to reinstall windows?

---

### Post by confused57 on 2008-02-05
> **Thecoolguru said:**
> IM HAVING MASSIVE PROBLEMS :(

I installed/semi-installed ubuntu. it didnt fully install and windows didn't show up when i booted even tho im pretty sure i installed ubuntu on my external. also, it wont do anything unless i put the ubuntu cd in. does this mean that i have to reinstall windows?
You shouldn't need to reinstall Windows, but you need to restore Windows IPL to the internal hard drive's mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)
You may want to read through this thread for how to use Super Grub Disk or a Windows install cd(not a recovery disk)..

---

