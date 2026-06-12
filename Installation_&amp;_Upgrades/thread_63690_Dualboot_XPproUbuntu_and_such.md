---
title: "Dualboot XPpro/Ubuntu and such"
date: 2005-09-08
forum: Installation &amp; Upgrades
---

### Post by BoomShake007 on 2005-09-08
Welly well then.  I've had some experience with Windows machines, using the cmd prompt slightly, troubleshooting, etc.  I have realized it's high time for me to install Linux and start learning.  I've never used it before, but I've heard good things.  I've done some searching and chatting and landed on Ubuntu.  After trying out the LiveCD and finding it nifty enough to go further, I decided I want to install.  However, I'm not ready to give up my lovely XP yet (games!), so I'd like to do a dual boot.  I therefore have a couple questions on the process and would like some reassurance to calm my nerves.

To start, I've got one 120GB hard drive partitioned accordingly:
C: - 20GB - System (XP Pro installed here) - NTFS
D: - 10GB - Personal files (Word docs, etc) - NTFS
E: - 90GB - Media (Movies, music, etc.) - NTFS

Now, I've used Partition Magic, playing Russian Rulette, and unallocated some space from the end of the 90GB partition, making around a 75GB media NTFS one and leaving like 10-15GB unallocated space (not entirely sure where the extra space went, but w/e).  I this sufficient?

I'm getting blank media for the install cd tomorrow, so the rest is just a few questions (for now).

When I run the CD and it asks me to format the unallocated space, I read on linux.org that i should make a swap (512MBram => 1GB partition), / (boot), /usr (isntall programs), and /home (personal files).  Now, few questions here.  How shuld i divvy up the space amoung these things?  Can I use Partition Magic to change the D and E partitions to FAT32, eliminating the need for the /home directory?  If so, how much do i need for / (boot) and /user?

Furthermore, I'm very nervous about this dual boot thing.  I've heard it can screw up and render it unbootable to anything.  Will the install automatically install and configure GRUB or whatever properly?  Will I then just be prompted when I power on which OS i want, then boot to my selection smoothly?

And finally (for now), with the LiveCD, my wireless card Netgear WG311v1 does not work.  It recognizes it, i can configure it, but it doesn't find the network or anything.  It's atheos chipset or whatever.  Is this what I need [http://ubuntuforums.org/showthread.php?t=38972&highlight=madwifi](http://ubuntuforums.org/showthread.php?t=38972&highlight=madwifi) ?

Thanks in advance for any help you can give me.  If you have any tips or tricks for complete beginners, those would be appreciated too.

BoomShake007

---

### Post by dave9191 on 2005-09-08
[QUOTE=BoomShake007]
Now, I've used Partition Magic, playing Russian Rulette, and unallocated some space from the end of the 90GB partition, making around a 75GB media NTFS one and leaving like 10-15GB unallocated space (not entirely sure where the extra space went, but w/e).  I this sufficient?[/QUOTE]

That should be pleanty to start of :) 

> 
When I run the CD and it asks me to format the unallocated space, I read on linux.org that i should make a swap (512MBram => 1GB partition), / (boot), /usr (isntall programs), and /home (personal files).  Now, few questions here.  How shuld i divvy up the space amoung these things?  Can I use Partition Magic to change the D and E partitions to FAT32, eliminating the need for the /home directory?  If so, how much do i need for / (boot) and /user?

/swap should equal the amount of RAM you have. 
/boot will do with a 100mb 
/ can be the rest of the space. 

If you dont make a /usr /home it will all be under /. I have a /boot, /home, / and swap. You can't eliminate a /home directory. Its either a seperate partion or under /. Files that go in your home directory can't always be saved to a FAT32 partion. 

> 
Furthermore, I'm very nervous about this dual boot thing.  I've heard it can screw up and render it unbootable to anything.  Will the install automatically install and configure GRUB or whatever properly?  Will I then just be prompted when I power on which OS i want, then boot to my selection smoothly?

There is always a risk that something can go wrong and you should have backups of all your important files. If the installer screws up the system, you can insert the windows cd, go into the recovery console and type 'fixmbr'. But the installer will detect windows and create a boot menu that will let you choose the OS. 

Hope this helps. 

Dave

---

### Post by BoomShake007 on 2005-09-08
> 
If you dont make a /usr /home it will all be under /. I have a /boot, /home, / and swap. You can't eliminate a /home directory. Its either a seperate partion or under /. Files that go in your home directory can't always be saved to a FAT32 partion.
On the linux.org site it said that by using the /usr and /home partitions that it will preserve your files and programs when upgrading.  Is this true?  It also says this about the /swap partition:
> First, you should see how much RAM you have. From this figure, you create what's known as a SWAP partition. This is simply a way that Linux uses to get an extra memory boost. Custom dictates that your swap partition be double your ram memory. So if you've got 256 megabytes of RAM, the feel free to make a 500 megabyte swap partition.
So should it be the same, or double my RAM?
[Linux.org Lesson2c](http://www.linux.org/lessons/beginner/l2/lesson2c.html)
Looking at that, it seems that the drive they installed to was just plain /  .  Do I name it / or /boot?  They also allocated considerably more size to the boot partition.  Is this necessary?

Also, one other thing.  When I ran the LiveCD, aside from the wireless not working, none of my NTFS partitions were seen.  Do I have to mount these manually (and how do I do that)?  And once I install Linux, do I need to mount them every time I start up?

---

### Post by dave9191 on 2005-09-09
[QUOTE=BoomShake007]On the linux.org site it said that by using the /usr and /home partitions that it will preserve your files and programs when upgrading.  Is this true?  [/QUOTE]

Most programs installed on your computer will be stored under /usr (sort of like the Program Files dir in windows) and all your user files / personal settings go under /home. So you can format / and install another Linux without loosing your files. Ive had limited success with that. And with Ubuntu you can do a dist-upgrade (look it up when you are upgrading) and it will upgrade to a new version leaving all your files and programs intact. So yes you can preserve you files during upgrades, but you need to know how much space you want to allocate to those dir's now. 

> It also says this about the /swap partition:

So should it be the same, or double my RAM?
[Linux.org Lesson2c](http://www.linux.org/lessons/beginner/l2/lesson2c.html)
Looking at that, it seems that the drive they installed to was just plain /  .  Do I name it / or /boot?  They also allocated considerably more size to the boot partition.  Is this necessary?

It should be the same size or more then your RAM. Making it bigger wont hurt. I always set it the same size as my RAM, unless I plan to upgrade my RAM soon. 

They havent got a seperate boot partion there. Just a / which then contains the boot dir. I have a 100mb /boot partion and currently Im using 13 mb of it. 

/ is the root of the files system. Everything else is somewhere below that. Any mounted partion (cdrom, hard disk, mem stick) will be somewhere under /. So you can have one giant partion where everything under that is a directory (apart from swap which needs a seperate partion). Or you can created partions and mount them under / somewhere. So /home can be a directory on the / partion, or it can be a seperate partion mounted under /home. My windows D drive is mounted under /home/dave/media. 

> 
Also, one other thing.  When I ran the LiveCD, aside from the wireless not working, none of my NTFS partitions were seen.  Do I have to mount these manually (and how do I do that)?  And once I install Linux, do I need to mount them every time I start up?

You need to mount them yourself. You will only be able to read from them, not write to them. And you can configure Linux to automount them at boot. You can find instructions on how to do that as well as most of the other common questions at [www.ubuntuguide.org](www.ubuntuguide.org) . 

Dave

---

### Post by BoomShake007 on 2005-09-09
ok, i think i'll use your method with swap = 512MB (same as ram), /boot =100MB, and the rest as / with /usr and /home directories and mounted stuff under the main / for now.  Thanks for the help.  I'm going to be installing either later today or tomorrow, so I'll let you know with my results.

---

### Post by BoomShake007 on 2005-09-09
Well, hmm.  I tried this [Install Ubuntu without a CD](http://ubuntuforums.org/showthread.php?t=28948) since my friend forgot to bring the blank cd.  The GRUB thing works, I can get into the installer thing, however, I encounter a problem that I expected.
[quote=computer]No network interfaces were found.  The installation system was unable to find a network device[/quote]It went on to say something about a module, and I was confused.

I'm using a Netgear WG311v1 wireless card, atheos chipset (something like that).  I have no ethernet ports on this computer.  Is there any way I can get around this, or should I just wait and do it from the cd? (I assume to wait for the cd).

Then comes the real question.  Once I get this installed, how the heck do I get wireless working? I read [Wlan with Ndswrapper](http://www.ubuntuforums.org/showthread.php?t=31926), but am slightly confused by it.  

First off, can I download whatever I need with Windows and see it in Ubuntu?  What do I need to get?  And how do I "install" it or whatever (that whole header thing confuses me in particular)?

---

### Post by dave9191 on 2005-09-09
[QUOTE=BoomShake007]I'm using a Netgear WG311v1 wireless card, atheos chipset (something like that).  I have no ethernet ports on this computer.  Is there any way I can get around this, or should I just wait and do it from the cd? (I assume to wait for the cd).> 

Now I'm not an expert on wireless cards and linux (hence I didnt mention anything before). But the  atheros chipset rings a bell, and not a good one. Its not a well supported chipset under linux - I think anyway. Don't quote me on any of this. You wont be able to do the network install, but fight with the card later. 

[QUOTE]Then comes the real question.  Once I get this installed, how the heck do I get wireless working? I read [Wlan with Ndswrapper](http://www.ubuntuforums.org/showthread.php?t=31926), but am slightly confused by it.  

Now when you install ubuntu you'll have a fun learning experince to try and get it working. Ive not done this so I can really help. Ndiswrapper takes the windows driver and lets you use it under linux. Thats about all I know. You get the windows driver, compile it or combine it with ndiswrapper and load it as a module into the kernel. You'll have to find a guide or someone else to help. 

Another possiblity would be [Linuxant](http://www.linuxant.com/driverloader/), but its not a free solution. I bought a modem driver from them and it works like a charm. They have a 30 day free trial. Maybe you could use the free trail to use the net on ubuntu till you can find another solution :)

> First off, can I download whatever I need with Windows and see it in Ubuntu?  What do I need to get?  And how do I "install" it or whatever (that whole header thing confuses me in particular)?

You should be able to download everything you need in windows and hopefully get it to work in linux. What you need is another matter. Im not quite sure. Installing also depends on what it is, and when you find out what you need, then you should be able to find instructions for it. 

Dave

---

### Post by BoomShake007 on 2005-09-10
Huzzah!  Install went just swimmingly off the cd.  Dual-boot works just like it should.  I figured out how to mount my other partitions, although it didn't recognize the unmount command...I probably was typing it wrong :P

I now realize I have a buttload of stuff to install like mp3 codecs and such after I get the wireless working.  Hehehe.

Thanks for all of your help and support with my n00bishness.  I'll let ya know when I get wireless working.

If you have anything you recommend or think I should get or tweak in general, I'm open to suggestions :)

---

### Post by amohanty on 2005-09-10
>  it didn't recognize the unmount command. 

I think what you want is umount.

AM

---

### Post by dave9191 on 2005-09-10
[QUOTE=BoomShake007]Huzzah!  Install went just swimmingly off the cd.  Dual-boot works just like it should.  I figured out how to mount my other partitions, although it didn't recognize the unmount command...I probably was typing it wrong :P[/QUOTE]

Like amohanty siad its umount. I trip up on that every time. And if the drive is busy and you want to unmount it (mem stick, external hdd, etc) then do a lazy umount (umount -l /dev/...)

> I now realize I have a buttload of stuff to install like mp3 codecs and such after I get the wireless working.  Hehehe.

Thanks for all of your help and support with my n00bishness.  I'll let ya know when I get wireless working.

If you have anything you recommend or think I should get or tweak in general, I'm open to suggestions :)

If you have any other questions just ask. And good luck on your wifi stuff. Hope you get it to work. And dont forget to browse the ubuntuguide and the ubuntu wiki. Its got loads of cool tips in there. 

Dave

---

### Post by BoomShake007 on 2005-09-10
[QUOTE=dave9191]Like amohanty siad its umount. I trip up on that every time. And if the drive is busy and you want to unmount it (mem stick, external hdd, etc) then do a lazy umount (umount -l /dev/...)



If you have any other questions just ask. And good luck on your wifi stuff. Hope you get it to work. And dont forget to browse the ubuntuguide and the ubuntu wiki. Its got loads of cool tips in there. 

Dave[/QUOTE]
 Thanks SO much for all of your help.  I'm usually one to try out new software and such, but this is the first time I've gone riding without my Windows training wheels.

And I finally got the wireless to work, using Madwifi.  Took a little bit of tweaking and fiddling, but now I'm posting this from Firefox within Ubuntu.  :)

Ah, umount....stupid n not being there.  Where's the logic in that? lol

I think i'm gunna just play around for a while, fiddle with settings and such, and see where I get.  I'll remember to look you up, dave9191, if I have any problems.  Thanks again.

---

### Post by dave9191 on 2005-09-10
[QUOTE=BoomShake007]Thanks SO much for all of your help.  I'm usually one to try out new software and such, but this is the first time I've gone riding without my Windows training wheels.

And I finally got the wireless to work, using Madwifi.  Took a little bit of tweaking and fiddling, but now I'm posting this from Firefox within Ubuntu.  :)

Ah, umount....stupid n not being there.  Where's the logic in that? lol

I think i'm gunna just play around for a while, fiddle with settings and such, and see where I get.  I'll remember to look you up, dave9191, if I have any problems.  Thanks again.[/QUOTE]


Congrats on the wifi. Ill need to take a note of Madwifi in case other people need help :) 

As for the missing n... I guess its less typing ;)

Good luck and enjoy.

Dave

---

