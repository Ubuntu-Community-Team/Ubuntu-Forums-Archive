---
title: "GRUB2 Testing Question"
date: 2009-07-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cheesypoof on 2009-07-26
I want to chainload grub2 to test how it works with my system before switching over to it permanently. When I try to install grub-pc, it says I must remove the grub package first.

The wiki at [https://wiki.ubuntu.com/KernelTeam/Grub2Testing](https://wiki.ubuntu.com/KernelTeam/Grub2Testing) did not mention anything about removing grub...

> If you are running Jaunty Jackalope or later, grub2 can be installed in parallel with, and as a chainloaded sub-bootloader of, your existing grub installation. This allows you to boot actually with grub and then select grub2 from the menu. Then you can confirm grub2 works correctly before electing to switch to it formally.

Even if you are only able to test in chainloaded mode that would give us some information as to the viability of grub2.

> sudo apt-get install grub-pc

At the first prompt, select OK. Next, at the "Chainload from menu.lst" prompt answer "Yes". And at the "Linux command line:" prompt just press the Enter key.

This will install grub2 and modify the existing grub boot loader menu allow one to chain load grub2 to allow one to test to see if grub2 works on your machine. At this stage, the original grub is still the main boot loader and keeps the original boot menu items. 

My question is, how do I proceed? Will removing grub ruin my boot setup?

---

### Post by Slug71 on 2009-07-26
Dont chainload. Theres always issues with it. Just do the full upgrade. Grub2 is default in Karmic now anyways Since Alpha 2 IRC.

---

### Post by randiroo76073 on 2009-07-26
Chainloading does not work with grub2 so far(alpha-3), everytime I have tried it I get:
"error 13 invalid or unsupported format"
So as far as I can see grub2 is useless for chainloading. Has anyone come up with a work around ?

---

### Post by Herman on 2009-07-26
GRUB2 prefers to be installed to the MBR of any disk. If we want to try to install it (or the boot.img for it) to a partition boot sector it works but we need to add the '--force' option to the [grub-setup]("http://members.iinet.net/%7Eherman546/p20/GRUB2m%20Bash%20Commands.html#grub-setup") command.

The syntax for chainloader command has changed a little bit too, (compared with GRUB Legacy), it likes to have a '+1' at the end now,
```
chainloader (hd0)+1
```For booting a partition boot sector, you probably need to insert the -f option in the chainloader command. [chainloader]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_chainloader").

I don't really think it's necessary to chainload from GRUB2 like we used to need to do with GRUB Legacy anyway. GRUB2 detects all of my operating systems when I run [grub -mkconfig]("http://members.iinet.net/%7Eherman546/p20/GRUB2m%20Bash%20Commands.html#grub-mkconfig") and sets up direct kernel booting, try running [grub -mkconfig]("http://members.iinet.net/%7Eherman546/p20/GRUB2m%20Bash%20Commands.html#grub-mkconfig") or [update-grub]("http://members.iinet.net/%7Eherman546/p20/GRUB2m%20Bash%20Commands.html#update-grub")  instead.

---

### Post by randiroo76073 on 2009-07-26
Well, thats all fine, but I'm trying to chainload into grub2 from grub-legacy and get error:

"error 13 invalid or unsupported format"

I don't care for grub2, Point me to a tutorial to install grub-legacy to my /dev/sda5 over grub2, Please & Thank you :)

---

### Post by Gina on 2009-07-26
With GRUB legacy I used configfile to chain to another GRUB so that the older system will update it's menu.lst to apply a new kernel.  Otherwise, the newer grub will load the original kernel in the earlier installed system and a kernel upgrade will not be chosen.  I've found, not surprisingly, that configfile needs both systems to use legacy grub - it doesn't work with grub2.

Currently, I have a newer install of Jaunty (actually Ultimate Edition 2.3) and the Karmic installation is older.  So ATM the Karmic kernel will not upgrade.  I was going to use chainloader to chain to Karmic's grub2 loader.  I was under the impression that this would work.

---

### Post by ranch hand on 2009-07-27
> **Gina said:**
> With GRUB legacy I used configfile to chain to another GRUB so that the older system will update it's menu.lst to apply a new kernel.  Otherwise, the newer grub will load the original kernel in the earlier installed system and a kernel upgrade will not be chosen.  I've found, not surprisingly, that configfile needs both systems to use legacy grub - it doesn't work with grub2.

Currently, I have a newer install of Jaunty (actually Ultimate Edition 2.3) and the Karmic installation is older.  So ATM the Karmic kernel will not upgrade.  I was going to use chainloader to chain to Karmic's grub2 loader.  I was under the impression that this would work.
If you log into your "older" 9.10 and run "sudo update-grub" it will, I betcha, pick up your UE installation.

If you want to then switch to grub2, still in 9.10 run "sudo install-grub /dev/sda" (or whatever drive you are on).  This should put you back to booting with 9.10 as the boot/root.

To set your time out edit /etc/default/grub in 9.10.  You will haveto run update-grub again to make it active to wht time you set.

---

### Post by Herman on 2009-07-27
> Well, thats all fine, but I'm trying to chainload into grub2 from grub-legacy and get error:
"error 13 invalid or unsupported format"I'm guessing you have another Ubuntu installation, Jaunty perhaps, with GRUB Legacy in it and you want to chainload your Karmic Koala from Jaunty's GRUB. 
Probably the reason you're getting Grub error 13 would be because you're probably trying to chainload GRUB2 by your Karmic partition's boot sector but GRUB2 has not yet been installed to the boot sector,  [Grub error 13]("http://members.iinet.net.au/%7Eherman546/p15.html#13").  
You could fix that by booting Karmic and running 'sudo grub-setup --force /dev/sda5
```
grub-setup --force /dev/sda5'
```Where: /dev/sda5 is your Karmic partition.
That should fix it so you can chainload Karmic from Legacy GRUB in your eariler Ubuntu.

You'll need to boot Karmic first probably, in order to do that, or chroot into it.
You should be able to boot Karmic from your GRUB Legacy from [Command Line Interface]("http://members.iinet.net.au/%7Eherman546/p15.html#cli") by doing a [Direct (kernel) Boot]("http://members.iinet.net.au/%7Eherman546/p15.html#First_method:_direct_kernel_boot.") . Or use Super GRUB Disk.

I'm not sure if it's easy to revert Karmic Koala to Legacy GRUB, you can take a look in Synaptic Package Manager and see if GRUB Legacy is listed. If so, you could easily use Synaptic to remove grub-pc and install grub 0.97. I'm only guessing though. 
I think you should keep GRUB2 in Karmic, you might get to like it after you have taken some time to get used to it. It's up to you though.

---

### Post by Herman on 2009-07-27
> With GRUB legacy I used configfile to chain to another GRUB so that the older system will update it's menu.lst to apply a new kernel. Otherwise, the newer grub will load the original kernel in the earlier installed system and a kernel upgrade will not be chosen. I've found, not surprisingly, that configfile needs both systems to use legacy grub - it doesn't work with grub2.:) Hello Gina,
When we use the 'configfile' command, the GRUB we're using reads the menu.lst or grub.cfg for instructions. It needs to be able to understand the commands in the file it is pointed to for everything to work properly. The important thing to understand is, it's the GRUB we start in that does the booting. For that reason it's usually only useful to use the configfile command between Linux installations that run similar versions of GRUB.

The chainloader command, on the other hand, boots the other boot loader, and hands over control to it. It's the other boot loader that does the booting. We can chainload incompatable versions of GRUB, or any other boot loader such as LILO, or even unsupported boot loaders like NTLDR or BCD.
For chainloading to work, the stage1 or IPL for the boot loader needs to be installed somewhere, such as a hard disk's MBR, or to the first sector of a partition, (partition boot sector). With Windows, the boot sector is installed by default, but with Linux distros the boot sector is normally not needed, so no boot code is installed there unless the user does it themselves.
To install GRUB 2 to a boot sector, we can use 'grub-setup --force', similar to the post above, and GRUB 2 will complain, but it install there anyway, and after that you'll be able to chainload your Karmic Koala from some other boot loader, such as Legacy GRUB. It will work, it doesn't work 'out of the box', but it will work. 

Regards, Herman :)

---

### Post by Herman on 2009-07-27
> If you log into your "older" 9.10 and run "sudo update-grub" it will, I betcha, pick up your UE installation.
If you want to then switch to grub2, still in 9.10 run "sudo install-grub /dev/sda" (or whatever drive you are on). This should put you back to booting with 9.10 as the boot/root.
To set your time out edit /etc/default/grub in 9.10. You will have to run update-grub again to make it active to wht time you set.I agree with you, ranch hand, GRUB 2 is a lot better than Legacy GRUB.  I'll bet there'll be a lot of belly-aching and complaining for a while until people get used to the new GRUB, but once people get used to it they won't want to go back. :)

---

### Post by randiroo76073 on 2009-07-27
I can accept that grub2 is better, but, what about chainloaders like me ? On the average I have 5+ distros installed at any one time. What files am I going to have to configure and where will they be kept ? I'm used to menu.lst, fstab, etc. Will I just have 1(that'ud be great :) )

Edit: Thanks for your help Herman, have enjoyed your site for awhile now. Guess I need to visit more often tho, tad bit of updating there :)

---

### Post by ranch hand on 2009-07-27
I am currently on my testing rig.  This is my main computer with the internals "off" in bios running on a dual SATA external enclosure with 2 WD 320Gb HDDs.  No raid so boot from sda (all / partitions) and /home partitions are all on sdb.

I have 8 (currently) OS' running on it booting with grub2.  4 of these OS' are grub-legacy OS' (8.04, SuperOS 9.04, 9.04 and Stoner1.1(9.04).  The rest are different configs of 9.10 including 1 installed just on sda because in A2 grub2 was having trouble booting (on here) the 2 partition installs.

Today I had a problem with A3 not piking up one of the 9.10 installs new kernal so I had to switch to that OS to boot from.
```

sudo update-grub

```
Had no trouble picking up all the other OS' correctly.  So;
```

sudo grub-install /dev/sda

```
and that was that.

That is all the "file editing" that I did.

This is an intensively script driven version of grub.  There are still some rough spots.

My problem today was with a version of 9.04 that I upgraded by just adding the 9.10 /etc/apt/sources.list to the existing 9.04 file without dropping any of the 9.04 stuff at all.   There may well be some "conflict" there that is making it hard for the other grub2 OS' to read this OS right.

The OS I am on now is the one that was the problem.  It picked up the 2.6.31-4 kernal on itself with update-grub but the others left it at '-3.  So I switched and everything is cool.

I am not on my production drive so I do not have all my links handy.  I will post some in a while that have to do with grub2.  You may find them useful.

I think that once we all learn the right files to edit in emergency conditions we will be happier but grub2 is built to take care of itself VERY well.

---

### Post by Gourgi on 2009-07-27
how can i load a grub2 configfile from grub legacy ? 
is it possible?
i tried the code below
```
title		Karmic Koala - Testing 
configfile (hd2,1)/boot/grub/grub.cfg
```
but instead of loading grub2 menu , it opens grub2 cli :(

---

### Post by Herman on 2009-07-27
I'm having fun testing GRUB 1.96 and so far it seems as if there's a lot for me to learn.

Right now it seems to me as if the most important thing about GRUB 2 for the average user is 'sudo update-grub' seems to be about all most people will need to know. 
The scripts and programs in GRUB 2 will automatically scan the computer and add direct kernel boot entires to the grub.cfg where possible. For Windows is adds a chainloader command entry.
For me, the update-grub script has been working perfectly, and adds direct kernel boot entries for all of my Linux installations. 
It would be important to keep running 'sudo update-grub' quite frequently if you have many operating systems which may be receiving kernel updates, for some people it would be a good idea to run 'sudo update-grub' at every boot-up if we want to be booting the newest kernels.

One criticism of it is, it doesn't always add user-friendly titles. Often the titles that appear in the GRUB Menu are rather cryptic, and could be a bit disorienting for new users. It looks like they have tried though, and a Linux user with any experience should find it simple enough to pick out the title they want to boot.  Some scrolling down may be required, as the list can be quite long.

My understanding is we're supposed to make our own files in /etc/grub.d/ and number them according to the sequence we want them to appear in our GRUB Menu, then run update-grub if we want to add our own customized boot entries. I haven't tried that out myself yet, but it's high on my list of things to do.

I thinks there's a lot to look forward to in GRUB 2, we just need to be open-minded and ready to accept new ways of doing things. It'll take a little work for a while at first while everything seems so strange and different, but I'll bet it won't be long before most of us will start getting comfortable with GRUB 2. It's just a matter of trying out all the new ways of doing things and practicing a little. :D

---

### Post by Herman on 2009-07-27
> how can i load a grub2 configfile from grub legacy ? 
is it possible?We can't use the configfile command between the two different GRUBs because they are so different that GRUB Legacy can't understand GRUB 2's grub.cfg and GRUB2 can't understand menu.lst. 

We can chainload instead. :D

---

### Post by ranch hand on 2009-07-27
> 
From Herman
My understanding is we're supposed to make our own files in /etc/grub.d/ and number them according to the sequence we want them to appear in our GRUB Menu, then run update-grub if we want to add our own customized boot entries. I haven't tried that out myself yet, but it's high on my list of things to do.

I got the impression that /etc/grub.d/40_custom was where that was to take place.  I have no idea (yet) how this is supposed to work.

For now I have a cheat sheet with my partitions listed and am going by partition # when looking for which to boot to.  I really want to know how we are to do that.  I did read that the ability to ad text is supposedly enabled now but haven't seen how or where to do it exactly and I surely can't read code to figure it out myself.

I am, however, used to editing /boot/grub/menu.lst to keep things up to date and clean.  I am sure that it will be easier in grub2 when we get our heads wrapped around the system.

---

### Post by Gourgi on 2009-07-27
> **Herman said:**
> We can't use the configfile command between the two different GRUBs because they are so different that GRUB Legacy can't understand GRUB 2's grub.cfg and GRUB2 can't understand menu.lst. 

We can chainload instead. :D
thanks for answering Herman.

i think the opposite works: load configfile from grub2 to menu.lst.
i did it before IIRC. i'll try it on reboot and post back.

---

### Post by ranch hand on 2009-07-27
Here are some links I have collected.  I do not vouch for their working or the folks writing knowing more than we already do.

I am sure that you can get confused reading them.  Confusion is the foundation of learning.

I hope that they are of some help to someone.

[http://wiki.archlinux.org/index.php/GRUB2](http://wiki.archlinux.org/index.php/GRUB2)

[http://grub.enbug.org/](http://grub.enbug.org/)

[http://grub.enbug.org/Manual](http://grub.enbug.org/Manual)

[http://grub.enbug.org/CommandList](http://grub.enbug.org/CommandList)

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

[https://wiki.ubuntu.com/KernelTeam/Grub2Testing](https://wiki.ubuntu.com/KernelTeam/Grub2Testing)

[http://ubuntuforums.org/showthread.php?t=1202444&highlight=grub](http://ubuntuforums.org/showthread.php?t=1202444&highlight=grub)

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

[http://grub.enbug.org/Grub2LiveCdInstallGuide](http://grub.enbug.org/Grub2LiveCdInstallGuide)

---

### Post by Gina on 2009-07-28
Thank you for your help Herman et al :) :)  Lots to read and try there :)

---

### Post by Herman on 2009-07-28
:D Thank you Gina, I'm having a lot of fun trying things out there and hopefully it will be some help to others. I think what I need next for the GRUB 2 section is some better kind of a index so people can look things up by what is is they might want to do, like 'How to make a GRUB mk-rescue CD' , 'How to Add your own custom entry to the GRUB Menu', and so on. Right now I'm still exploring and things are just indexed according to where I 'discover' them. (LOL) Anyway, I'll get there, I'll keep working on it. Thanks for your kind words, that's what makes it all worthwhile. :)

I'm still working on this and it will become on of my how-tos, but right at the moment I haven't quite been able to get it working yet. I can make a script to add a custom menu entry to my grub.cxfg alright, but for some strange reason the new entry doesn't show up in my GRUB Menu when I reboot. 
I can't for the life of me see what on earth I'm doing wrong. Unfortunately, I keep running short of time before I can get very much done as my spare time is broken into small chunks these days, at least during the working week.

Rather than keep you all waiting, here are the links explaining what I'm trying to do,
[Grub 2]("https://wiki.ubuntu.com/Grub2") - Ubuntu Wiki, especailly see: [Adding Entries to Grub 2]("https://wiki.ubuntu.com/Grub2#Adding%20Entries%20to%20Grub%202")
[Tweaking Grub 2]("http://www.drlock.com/blog/2008/07/11/tweaking-grub-2/") - DRLOCK.COM

I'm sure it's only something small that I'm overlooking, of course I'm trying to do something a little more interesting than simply following the instructions, I have a masochistic tendency to do everything the hard way first and learn what not to do before I find out what's right, (LOL). 
I'll be back with an update when I get it sorted out. Sorry for taking so long.

Regards, Herman :)

---

### Post by drs305 on 2009-07-28
I put together a good bit of the "Adding Entries to Grub 2" section of the wiki link mentioned above, which was developed by billybigrigger. I also created the [Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") thread.  If any of it is unclear feel free to let me know (for the forum post) or simply edit the wiki Grub 2 file (it is a wiki, after all).

I appreciate Herman's work and check his site often to see what he's added. 

And I'm hopeful a StartUp-Manager2 will eventually appear. The author of that app indicated he would work on one.

---

### Post by phenest on 2009-07-28
To get round chainloading, I did this:
```
menuentry "Karmic Koala" {
set root=(hd0,5)
linux /vmlinuz root=/dev/sda5 so quiet splash
initrd /initrd.img
```
This won't give you the choice of all the different kernels you may have installed, and only boots the most recent kernel.

---

### Post by Herman on 2009-07-29
```
#! /bin/sh -e
echo "Adding Parted Magic LiveCD .iso Boot" >&2
 cat << EOF

menuentry "Parted Magic" {
              set root=(hd2,5)
              loopback loop (hd2,5)/pmagic-3.4.iso
              linux (loop)/pmagic/bzImage isofrom=/dev/sdc5/pmagic-3.4.iso livecd boot=live quiet vga=791 noeject noprompt sleep=0 root=/dev/ram0 tmpfs_size=220M ramdisk_size=25000
              initrd (loop)/pmagic/initrd
}

EOF
```:) I don't think there's anything wrong with your excellent "Adding Entries to Grub 2" section of the wiki link, drs305. 
I think I'm having problems because I'm trying to do something a little outside the ordinary.

I have followed this how-to,  [Boot an ISO via Grub2]("http://michael-prokop.at/blog/2009/05/25/boot-an-iso-via-grub2/") - Mika's Blog, except I'm using a Parted Magic Live CD instead of grml which was used in that blog. 
I have been successful in getting the .iso file to boot from CLI mode GRUB2. 
Now I want to add a custom menu entry to boot my .iso file.

 :???: I seem to be able to get the entry into grub.cfg alright, but I can't get it to show up in my GRUB Menu at boot time.

Can anyone see what I'm doing wrong? :confused:

---

### Post by phenest on 2009-07-29
> **Herman said:**
> Can anyone see what I'm doing wrong? :confused:

No. I'm also trying to do this with an Ubuntu iso as discussed in [this thread]("http://ubuntuforums.org/showthread.php?t=1224417").

---

### Post by drs305 on 2009-07-29
Herman,

I deleted the contents of my /etc/grub.d/40_custom file and placed your contents inside. I then saved it, ran "sudo update-grub" and the menu entry was placed in grub.cfg. I then rebooted and the menu entry appeared on my Grub 2 menu. Of course, I couldn't really boot into it, but the menu entry was there and underlying content appeared correct.

You stated it appeared in your grub.cfg file so I assume you have an executable file inside the grub.d folder and that, since you have the echo command, you see it added to grub.cfg during "update-grub".

I know you do a *lot* of work with grub (thank you, by the way) and probably have a gazillion partitions and probably multiple /boot partitions. The only reason I can think of, as remote as it is, is that it is using a different grub.cfg at boot.

---

### Post by ranch hand on 2009-07-29
I need to thank you guys.  This thread is becoming both FUN and educational.

Grub2 is going to just rock.

---

### Post by randiroo76073 on 2009-07-29
I must be doing something completely wrong, I can't get Karmic to boot. I tried using SGD(ver-0.9770 & it just hangs with menu driven commands(1 hr of blinking cursor) Have tried tutorials(not all yet), have a grub folder that looks like a music folder(full of clef-note files). What can I be doing wrong ?

---

### Post by ranch hand on 2009-07-29
Get your LiveCD and boot from it.

Open a terminal and a browser and go to

[https://wiki.ubuntu.com/Grub2#Adding%20Entries%20to%20Grub%202](https://wiki.ubuntu.com/Grub2#Adding%20Entries%20to%20Grub%202)

and scroll down to "Recover Grub 2 via LiveCD" and follow those directions.  It would be good to read the whole thing so that you can be really confused (confusion is the foundation of learning).

Grub2 is very different than grub-legacy.  I think that it may very well be better once we learn what we are doing and it gets the bugs out.

---

### Post by Herman on 2009-07-29
> Herman,
I deleted the contents of my /etc/grub.d/40_custom file and placed your contents inside. I then saved it, ran "sudo update-grub" and the menu entry was placed in grub.cfg. I then rebooted and the menu entry appeared on my Grub 2 menu. Of course, I couldn't really boot into it, but the menu entry was there and underlying content appeared correct.
:D Okay, thanks drs305, so it works for other people, just not for me at the moment for some reason then.
I had already tried 01_ and 05_<filename>, because I wanted the entry at the top of my GRUB Menu. When those failed I tried 11_ and 41_<filename>, but neither of those worked. 
Your idea to try 40_custom seemed like a good idea. Maybe there's something special about placing a custom entry in that particular file, since that's what that file was made for. I tried it but still no luck, unfortunately, not for me at least. 
> You stated it appeared in your grub.cfg file so I assume you have an executable file inside the grub.d folder and that, since you have the echo command, you see it added to grub.cfg during "update-grub".
Yes, the entry is definitely being added successfully being added to my grub.cfg file, that's the strange part. 
> I know you do a *lot* of work with grub (thank you, by the way) and probably have a gazillion partitions and probably multiple /boot partitions. The only reason I can think of, as remote as it is, is that it is using a different grub.cfg at boot. Thank you, and thanks for your help right now too. 
Yes, I do have a lot of installations, and one thing that's different from standard with the installation I'm working from now is it's in an encrypted LVM, I don't know if that would matter, but I can't imagine how it could since GRUB2 is in my separate /boot and the issue I'm having seems to occur at boot time.
I tried adding a different custom entry and that appeared fine and booted Windows XP, so it's the right grub.cfg, but my Parted Magic entry still refuses to show up.
I tried deleting all the lines that are uncommon and replacing them with the Windows XP boot entry lines and then 'Parted Magic' shows up in my GRUB Menu, and boots Windows XP. So it's not the title, it's something in the boot entry lines that GRUB2 doesn't like, or so it seems.

I have now added the same boot entry to my GRUB2 in my Dedicated GRUB2 Partition and that works fine, the title showed up in my menu and I booted Parted Magic.iso.

It's good to know that it's possible for others to add it. 
I'm still puzzled about what it is about my Ubuntu installation's GRUB2 that's different. 
I'll get some continuous time to work on it pretty soon, the weekend is just around the corner. 
Thanks again for your help. There's still a possibility there's something basic I've missed, but I still can't think of what that might be. If it works for you it should work for me too.
Regards, Herman :)

---

### Post by Piscium on 2009-07-29
Yesterday I upgraded from Grub 1 to Grub 2. This thread was my main source of information so I would like to share my experiences here.

Basically the upgrade succeed, but I think I was lucky!

My first step was to open Synaptic and choose Grub 2 to be installed. A dialogue box opened up with a tick box asking if I wanted to chain load Grub 1 to Grub 2. I was not interested so did not tick the box. In that same dialogue box there was a message to the effect that whichever the choice made, I should run the command "upgrade-from-grub-legacy". 

Synaptic went fine and then I ran the said command. It told me that it was going to install Grub on MBR of the master disk. I was a bit scared! That was not what I wanted at all. I have Xubuntu on the slave disk. So beware if that is what you want. 

I looked at that command, which is just a shell script in /usr/sbin, and it unconditionally puts Grub on the master disk (hd0).

I googled and found that there has been a bug logged in Launchpad to the effect that "upgrade-from-grub-legacy" should not just blindly install grub on the first disk, it should either ask the user where to install the boot, or else install it in the same place where Grub 1 is.

I was lucky because I forgot to do sudo on the said command so it failed! It must be my guardian angel.

So afterwards, following the recommendations of this thread, I did:
sudo update-grub
sudo grub-install /dev/sdb

Note "sdb" because I wanted Grub on the slave disk.

Then I restarted the PC. I am running Xubuntu. I noticed that the Xubuntu window manager took a whole lot of time to close. The PC restarted and booted fine. Then I got my Xubuntu desktop but no Xubuntu panels! I am new to Xubuntu so it took me half an hour to fix this panel's issue (thanks to Google and these forums again). I think this must be a Xubuntu (more precisely Xfce) bug rather Grub's.

After that I got some Grub2 splash images with Synaptic, and installed a nice one with Grub 2 following the instructions at the bottom of this thread:
[http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/](http://blogs.koolwal.net/2008/12/16/how-to-grub2-and-grub-pc-installing-splash-images/)

Also changed the Grub timeout from 5 to 10 seconds. With Grub2 whenever one changes settings one needs to run "sudo update-grub" again.

It worked well.

By the way, I have Jaunty installed, this might not work with previous Ubuntu versions.

Later on there was the automatic upgrade to the new kernel and that was OK too. I noticed that update-grub was called as part of the kernel update. So all is fine and dandy.:)

António

---

### Post by Piscium on 2009-07-29
I looked at /usr/sbin/upgrade-from-grub-legacy to see what I was missing by not running that command. It has two commands that do cleanup, they are optional:

rm -f /boot/grub/{{xfs,reiserfs,e2fs,fat,jfs,minix}_stage1_5,stage{1,2}}
rm -f /boot/grub/menu.lst*

I ran both commands and they were fine. Also called Synaptic again and removed some unneded Grub 1 packages:
grub-doc
grub-splashimages

I think that is it.

António

---

### Post by randiroo76073 on 2009-07-29
"It would be good to read the whole thing so that you can be really confused (confusion is the foundation of learning)."

I'm already so confused I don't know which end is up(head or seat) LOL!

---

### Post by Piscium on 2009-07-29
> **randiroo76073 said:**
> I'm already so confused I don't know which end is up(head or seat) LOL!

I agree it is confusing! I was confused yesterday too, but thought that it would take me days to dispel the confusion, so decided to go ahead using intuition! 

I could afford to do that because I do not have anything irreplaceable on my Linux disk (sdb). 

There are some risks upgrading Grub. That is why for Karmic Koala it has been decided to have Grub 2 for new installs but not upgrading Grub for old installs.

---

### Post by randiroo76073 on 2009-07-29
I'm gonna do a fresh install(again :)) can anyone see anything to add to the following that might make a difference in chainloading from grub-legacy to grub2
Thanks
Randy

```
Recover Grub 2 via LiveCD

First, grab a copy of the latest Ubuntu LiveCD and boot it.

Open a terminal and type 
$ sudo fdisk -l

Now, you need to remember which device listed is your linux distribution, for reference, /dev/sda1 will be used. Now we need to mount the filesystem to /mnt 
$ sudo mount  /dev/sda1 /mnt

If you have /boot on a separate partition, that need's to be mounted aswell. For reference, /dev/sda2 will be used. 
$ sudo mount  /dev/sda2  /mnt/boot 

Make sure you don't mix these up, pay attention to the output of FDISK
Now mount the rest of your devices 
$ sudo mount --bind  /dev  /mnt/dev

Now chroot into your system 
$ sudo chroot  /mnt

You should be chroot'd into your system as root, you can now run commands as root, without the need for sudo.
Now you need to edit the /etc/default/grub file to fit your system 
$ nano  /etc/default/grub

When that is done you need to run update-grub to create the configuration file. 
$ update-grub

To install GRUB 2 to the MBR, next you need to run grub-install /dev/sda 
$ grub-install  /dev/sda

If you encounter any errors, try grub-install --recheck /dev/sda 
$ grub-install --recheck  /dev/sda

Press Ctrl+D to exit out of the chroot.
Once you exit back to your regular console, undo all the mounting, first the /dev 
$ sudo umount  /mnt/dev

Now you can unmount the root system 
$ sudo umount  /mnt

And you should be free to restart your system right into GRUB 2 and then into your system installation. 
```

---

### Post by randiroo76073 on 2009-07-30
> **ranch hand said:**
> Get your LiveCD and boot from it.

Open a terminal and a browser and go to

[https://wiki.ubuntu.com/Grub2#Adding%20Entries%20to%20Grub%202](https://wiki.ubuntu.com/Grub2#Adding%20Entries%20to%20Grub%202)

and scroll down to "Recover Grub 2 via LiveCD" and follow those directions.  It would be good to read the whole thing so that you can be really confused (confusion is the foundation of learning).

Grub2 is very different than grub-legacy.  I think that it may very well be better once we learn what we are doing and it gets the bugs out.

Well, have tried various things suggested here, including above, seems I'm not destined to boot from grub-legacy to grub2. I either get bounced right back to 9.04 boot menu or the dreaded "error 13"

---

### Post by Piscium on 2009-07-30
I read those instructions for chainloading from grub legacy to grub 2 and they sounded too complicated and there seemed to be too much potential for mishap. That is one of the reasons why I took the direct route, just replacing grub 1 with 2, it is simpler.

You might consider doing that. Perhaps you would need a rescue CD in case things go wrong, and do some backups.

Then use Synaptic to install grub 2 (it automatically removes some grub 1 files).

After that do 
sudo update-grub

Then using your favourite editor check /boot/grub/grub.cfg
See if everything looks fine. (If not you might go back to Synaptic and re-install Grub 1.)

Assuming update-grub went well then do
sudo grub-install /dev/sda

If that looks fine too just restart, then optionally add the finishing touches as I explained in my previous posts.

This should work with Jaunty. I have a 4.5 year old Dell Dimension with ext4. I would assume that if you are using Karmic it will also work.

Btw, I assume no responsibility, I am a beginner in these things, but the above worked for me!

> **randiroo76073 said:**
> Well, have tried various things suggested here, including above, seems I'm not destined to boot from grub-legacy to grub2. I either get bounced right back to 9.04 boot menu or the dreaded "error 13"

---

### Post by ranch hand on 2009-07-30
I am not chain loading either.  I like Grub2 even if it is not quite intigrated completely yet.

It gets better everytime it is updated and has actually been ahead of schedule.

My Mandriva2009-1 (KDE and Gnome) are not booting but all debian based distros are fine.

---

### Post by randiroo76073 on 2009-07-30
Well Hallelujah, finally got there, not thru chainloading tho, back to basics. This is the grub-legacy menu.lst entry I had to use:
```
title		Karmic 9.10,(sda5+6,r=sda5) 
uuid            21f60f2b-47b5-4800-b605-1318c157b2d9
kernel          /boot/vmlinuz-2.6.31-3-generic root=UUID=21f60f2b-47b5-4800-b605-1318c157b2d9 ro quiet splash
initrd          /boot/initrd.img-2.6.31-3-generic
quiet
savedefault
```

None of the others would work for me :confused:
Hope this helps someone else :)

Edit: Now I can have some FUN !

---

### Post by phenest on 2009-07-31
> **randiroo76073 said:**
> Well Hallelujah, finally got there, not thru chainloading tho, back to basics. This is the grub-legacy menu.lst entry I had to use:
```
title		Karmic 9.10,(sda5+6,r=sda5) 
uuid            21f60f2b-47b5-4800-b605-1318c157b2d9
kernel          /boot/vmlinuz-2.6.31-3-generic root=UUID=21f60f2b-47b5-4800-b605-1318c157b2d9 ro quiet splash
initrd          /boot/initrd.img-2.6.31-3-generic
quiet
savedefault
```

None of the others would work for me :confused:
Hope this helps someone else :)

Edit: Now I can have some FUN !

That's all very well, but what happens when the kernel on Karmic is upgraded? You'll have to change that again. Try using this instead:
```
title		Karmic 9.10,(sda5+6,r=sda5) 
uuid            21f60f2b-47b5-4800-b605-1318c157b2d9
kernel          /vmlinuz root=UUID=21f60f2b-47b5-4800-b605-1318c157b2d9 ro quiet splash
initrd          /initrd.img
quiet
savedefault
```
That will boot Karmic into what its latest kernel is, and saves you from having to update the menu.lst so often.

---

### Post by randiroo76073 on 2009-07-31
Thanks Phenest, hadn't even thought that far ahead yet, was just happy to get Karmic booted **LOL!** So much to learn about grub2 also, before I switch to it.

OT: could someone tell me where they hid "Login", want to change to auto. PM would not mess up thread :)

---

### Post by wayne_cat on 2009-07-31
> **randiroo76073 said:**
> Thanks Phenest, hadn't even thought that far ahead yet, was just happy to get Karmic booted **LOL!** So much to learn about grub2 also, before I switch to it.

OT: could someone tell me where they hid "Login", want to change to auto. PM would not mess up thread :)

GDM does not have a configuration application at the moment. But you can edit the configuration file:

Add the options AutomaticLoginEnable and AutomaticLogin in the daemon section in:

/etc/gdm/custom.conf

```
[daemon]

AutomaticLoginEnable=true

AutomaticLogin=rschmitt

[xdmcp]

[chooser]

[security]

[debug]

```

---

### Post by randiroo76073 on 2009-07-31
Thanks wayne_cat, appreciate info :)

---

### Post by ranch hand on 2009-07-31
My gripe about grub2, and my only real one, is how in flinderation do you add a simple label to the menu entry?

I have several OS' at any time on my box.  I need to be able to see a label to know where I am.  Right now I am using cheat sheets for 3 different drives (all boot independent of the others) to keep track of partitions.  This is a pain.

Yes I can edit (temporarily /boot/grub/grub.cfg.  This is a silly approach.

I hope that someone has an aswer for this sometime soon.  With that I would be really happy with the way this bugger works.

---

### Post by drs305 on 2009-07-31
> My gripe about grub2, and my only real one, is how in flinderation do you add a simple label to the menu entry?

Yes I can edit (temporarily /boot/grub/grub.cfg. This is a silly approach.


Add the comment to /etc/grub.d/40_custom (or any other executable file you make in grub.d). I don't know if you can just put a one-liner with "menuentry .... " that would qualify as a "label" or not, but if it accepts your comment in 40_custom it will be automatically added to any grub update. 

If you want it to appear at the top of the menu, use "01_custom". Just remember to make the file executable. For help on making the file, refer to the grub2 link in my signature line.

---

### Post by ranch hand on 2009-07-31
> **drs305 said:**
> Add the comment to /etc/grub.d/40_custom (or any other executable file you make in grub.d). I don't know if you can just put a one-liner with "menuentry .... " that would qualify as a "label" or not, but if it accepts your comment in 40_custom it will be automatically added to any grub update. 

If you want it to appear at the top of the menu, use "01_custom". Just remember to make the file executable. For help on making the file, refer to the grub2 link in my signature line.
All I see in that file is;
```

1   #!/bin/sh
2   exec tail -n +3 $0
3   # This file is an example on how to add custom entries
4

```
I will admit right up front that this does not appear to geve me an example of how to add a custom anything.

I need to add, for example, "Jaunty" to the menu entry.  Does this mean that I nead to copy the menu entry to this file with "Jaunty added?

How is this going to work the next time there is an update of the kernal and "update-grub" is run, getting its info from /grub.d/10, 20 + 30?

---

### Post by phenest on 2009-08-01
Comment out (or delete) the 'exec' line. It's not needed. Follow the link in my signature for how to use Grub2. It took me about 5 minutes to have all my OS's setup. I've even got a hidden menu too.
Here's my /etc/grub.d/40_custom:
```
#!/bin/sh
# This file is an example on how to add custom entries
echo "Adding Ubuntu Karmic Koala on sda5" >&2
cat << EOF
menuentry "Ubuntu Karmic Koala" {
        set root=(hd0,5)
        linux /vmlinuz root=/dev/sda5 so quiet splash
        initrd /initrd.img
}
EOF
```

---

### Post by drs305 on 2009-08-01
> **ranch hand said:**
> All I see in that file is;
```

1   #!/bin/sh
2   exec tail -n +3 $0
3   # This file is an example on how to add custom entries
4

```
I will admit right up front that this does not appear to geve me an example of how to add a custom anything.

I need to add, for example, "Jaunty" to the menu entry.  Does this mean that I nead to copy the menu entry to this file with "Jaunty added?

How is this going to work the next time there is an update of the kernal and "update-grub" is run, getting its info from /grub.d/10, 20 + 30?

The Grub2 Basics link in my signature line gives an example; but yes, you could copy the grub.cfg entry here and edit the title to whatever you want. Anytime update-grub is run, the 40_custom file will be incorporated into the grub.cfg menu. 40_custom entries will be placed at the bottom of the menu. If you want them at the top, you can create an executable file called 01_custom (or anything else starting with 01) and it will be placed at the top of the menu whenever update-grub is run. The format and details are in the link.

---

### Post by ranch hand on 2009-08-01
OK, I thought so.  Does this seem a little crazy to anyone else?

To have a label on the menu you get the partition listed twice.  You could stop grub from using /etc/grub.d/10 but then you wouldn't get updates at all.

I will give it a try with the custom ones on top I guess.  Better than a cheat sheet.  Must not be many nuts with lots of OS' out there.

I do not need a hidden menu.  I do have the timeout set at 100 so that I can read the bugger.  I think I may do away with the memtest entries.  They get set in duplicates more often than the other entries do.

---

### Post by ranch hand on 2009-08-01
Well, I have been reading too many cranky posts on the forums by folks who are complaining before they try something.  Geeze, had my panties in a bunch.  I am pretty sure my knickers were even in a knot.

Made a /etc/grub.d/01_custum file for my 32bit HDD.  It has 7 OS' on it but I need to work on the Mandriva ones (2) because while they are on the grub2 menu they don't boot (this may be the fault of the OS' as I was having a little trouble with them before grub2).  So I just created 5 entries.

Did screw up on my first trial with only 1 entry.  Fixed it and added 1 more, worked great.  Added the other 3, they all work great and are in the order I want and are all just the name I gave them.

While I still have the entire rest of the menu it is not a problem.  I don't need to look at it and it is no slower to load than it ever was.

So - not so good.  I am really going to have trouble finding something to complain about in grub2.  Bummer.

Thanks a big bunch phenest and drs305.  Sometimes a grumpy geezer just needs a hint and a kick in the pants.

---

### Post by cheesypoof on 2009-08-02
...

---

### Post by Herman on 2009-08-02
:D I solved my problems too, and relearned a few things I should have already known, and learned some new things too.

One lesson is to RTFM, I was mktrying to use the grub-mkconfig command and it wasn't mkworking for me because I was mkstupid and overlooked the mkmanual's -o option. 
Now I know that when we use the grub mk-config command it doesn't really do anything besides show us the new grub.cfg it would have made in the terminal. It needs the -o option with the path and filename to write after it.
I can see the sense in that, actually now that I know I'll keep on using grub mk-config in preference to update-grub.

That wasn't my main problem though, my main problem wouldn't have occured if I had been content to try making a custom entry with just an ordinary menu entry. The one I was trying to use worked fine from CLI mode, so I was expecting it to work from menu mode as well, and I had a hard time working out why it didn't. The problem wasn't an obvious one, at least not for me. 
I have a very long line after my linux command, with a lot of kernel options.
What I needed to do was go into my text editor settings and disable text wrapping so gedit wouldn't put in a carriage return. 

Anyway I'm mkhappy now I've mksolved it :D

mkregards, mkherman :)

---

### Post by ranch hand on 2009-08-02
WOW.  I will keep that in mind.  I am a grumpy geezer and no matter that I am excited about grub2, I admit to being frustrated by the learning involved.  All the main stuff I have now though and will play eith it until I have it straight.

Then I'll try some more.

I never really tried to change the look of grub-legacy.  I am with this one.  Have not got a background to work yet.  No biggy.

The menu works the way I need it too now and it should be easy to keep up.  Faster than grub-legacy now that i am getting the hang of it.

It really looks to be more flexible.

---

### Post by phenest on 2009-08-02
> **ranch hand said:**
> Have not got a background to work yet.  No biggy.

Sure that's a biggie! No, let's have a look...
```
sudo apt-get install grub2-splashimages
cd /boot/grub
sudo mkdir images
sudo cp /usr/share/images/grub/* images
```
Installing grub2-splashimages gives you some images guaranteed to work with Grub2. Copying them to /boot/grub/images is just in case you're using an encrypted filesystem (Grub can't read them).
Now open /etc/grub.d/05_debian_theme in your favourite editor and make these changes:
Line 16: change /boot/grub to /boot/grub/images and the filename to Plasma-lamp. i.e.
```
  for i in {**/boot/grub/images**,/usr/share/images/desktop-base}/**Plasma-lamp.**{png,tga} ; do
```
Line 39 & 40: change the colours to:
```
  set color_normal=**light-gray**/black
  set color_highlight=**white**/black
```
Then run:
```
sudo update-grub
```
Et voila!

Obviously, this only uses the same image every time. Maybe I'll write a script that will either use a random image or will ask you to choose one.

Further reading [here]("http://members.iinet.net/~herman546/p20/GRUB2%20Splashimages.html").

---

### Post by Herman on 2009-08-02
> Obviously, this only uses the same image every time. Maybe I'll write a script that will either use a random image or will ask you to choose one.:D With GNU GRUB Legacy I made a splashimage slide show once or twice by having a series of menu.lst files, (numbered in sequence like 'menu.2nd','menu3rd' and so on), each with a different splashimage. 
I used the configfile command and the timeout command to change from one menu.lst to the next, in a loop.
The configfile command for changing to the next menu.lst needs to be set as the default entry in each file. The same thing should be possible in GRUB 2.
Just an idea. :D

---

### Post by ranch hand on 2009-08-02
I will have to check back into the test drive to check but i think I did all those things.  Maybe I better update-grub again as I may have left that out, it was late last night.

Well, went to test drive for 64bit.  I had not run update-grub.  It is working now.  A rough (another late night project) combo of 3 photos from our collection (Olympus E-500 - a little old but nice).

I was afraid that I had converted the format to .tga wrong and would need to tweek it.  I guess i need to try a .png next to see if that works.

I still need to make a custom menu for this drive so I'll do that here (switched to test drive) and try the .png on the 32bit test drive.

---

### Post by drs305 on 2009-08-02
Unless it's changed, one other thing to look at when trying to get a splash image to work is the default line in the 05_debian_theme folder for the image location:
> 
for i in {/boot/grub,/usr/share/images/**desktop-base**}/

If your install the grub splash images via synaptic they are stored in: 
> 
for i in {/boot/grub,/usr/share/images/**grub**}


You may have to change either the script's image location or place the images in the "desktop-base" folder to get the image to display.

---

### Post by ranch hand on 2009-08-02
> **drs305 said:**
> Unless it's changed, one other thing to look at when trying to get a splash image to work is the default line in the 05_debian_theme folder for the image location:

If your install the grub splash images via synaptic they are stored in: 


You may have to change either the script's image location or place the images in the "desktop-base" folder to get the image to display.
I do have a home made image working.  I do not know for sure where it is coming from (I should eliminate them one at a time and find out) because I put the bugger in all three files.

What ever the case may be, it is fairly easy if you are awake enough to remember that NOTHING happens in grub2 without update-grub.  I was too tired last night.

---

### Post by cheesypoof on 2009-08-02
Is anyone having problems with the GRUB_GFXMODE command in '/etc/default/grub' not being properly included in their grub.cfg if it is uncommented? It does not seem to get picked up for me...

---

### Post by ranch hand on 2009-08-02
> **cheesypoof said:**
> Is anyone having problems with the GRUB_GFXMODE command in '/etc/default/grub' not being properly included in their grub.cfg if it is uncommented? It does not seem to get picked up for me...
I surely hope that unlike some folks who will remain nameless, that you ran "update-grub".

Nothing you do in grub2 will work until you run that.

---

### Post by xebian on 2009-08-02
Has anyone experienced this annoyance?

Not sure if it just me but it found the UUID and used it on the search line. However it insists on using /dev/sdaN for the root= ??? It's annoying when these /dev/sdAN changes when you have PnP drives.

I thought UUID is the proper and better way since Hardy? or Intrepid?

```

menuentry "Debian GNU/Linux (squeeze/sid) (on /dev/sda6)" {
        set root=(hd0,6)
        search --no-floppy --fs-uuid --set c48c772a-4217-482f-b264-344f303d2e20
        linux /boot/vmlinuz-2.6.30-1-amd64 root=/dev/sda6
        initrd /boot/initrd.img-2.6.30-1-amd64
}
```

What is even more weird is it picks up obsolete UUID if there is an old menu.lst around.

---

### Post by flavouride on 2009-08-02
ah that's pretty odd

however, a PnP hd will hardly alter the sequence of the hd0 or dev/sdaN partitions
they will just be dev/sdb or dev/sdc unless you install grub into the mbr of more than one fixed disks then the abc's might mix up
as a dos partition table should normally be arranged as
1,2 being primary partitions (dev/sda1 and dev/sda2)
3 being extended partition
=>5 being logical drives (dev/sda5 and dev/sda6 and so on)

---

### Post by drs305 on 2009-08-02
> **cheesypoof said:**
> Is anyone having problems with the GRUB_GFXMODE command in '/etc/default/grub' not being properly included in their grub.cfg if it is uncommented? It does not seem to get picked up for me...

cheesypoof,

It works for me. Here are some things to check:
1. Only one display mode uncommented in /etc/default/grub.
2. Make sure the mode is supported by your video. You can check the resolutions available via System, Preferences, Display. You should be able to check the video resolutions available from an app inside this menu.
3. Save the file (/etc/default/grub) once you have made the change.
4. Update grub2  (sudo update-grub).
5. Check that the GFX mode is now properly listed in /boot/grub/grub.cfg
6. Reboot.

Are you trying to use this mode in addition to a splash image? I have't combined the two yet; my changes work fine with a straight graphic menu.

---

### Post by vishalrao on 2009-08-02
> **xebian said:**
> Has anyone experienced this annoyance?

Not sure if it just me but it found the UUID and used it on the search line. However it insists on using /dev/sdaN for the root= ??? It's annoying when these /dev/sdAN changes when you have PnP drives.

I thought UUID is the proper and better way since Hardy? or Intrepid?

```

menuentry "Debian GNU/Linux (squeeze/sid) (on /dev/sda6)" {
        set root=(hd0,6)
        search --no-floppy --fs-uuid --set c48c772a-4217-482f-b264-344f303d2e20
        linux /boot/vmlinuz-2.6.30-1-amd64 root=/dev/sda6
        initrd /boot/initrd.img-2.6.30-1-amd64
}
```

What is even more weird is it picks up obsolete UUID if there is an old menu.lst around.

i think i had a similar problem trying to get fedora 11 to boot. although it has older kernel but in grub2 i tried changing linux/kernel root option portion from:

```
root=/dev/disk/by-uuid/xxxxxx
```

to:

```
root=UUID=xxxxxx
```


Try that?

---

### Post by vishalrao on 2009-08-02
now my question:

i have quad boot: win7rc, arch, karmic and fedora11.

i had to manually add fedora11 to "30_otheros".

the other entries for win7, arch and karmic show up automatically after running update-grub (thanks to 20_osprober i think).

now, after these entries are generated, how do i rearrange and relabel them? what is the proper way? edit the files in grub.d (how) or just edit grub.cfg (which i think is not recommended)?

The auto generated entries are karmic (default), win7, arch followed by my hand added fedora11.

I would like it to be arch (default), win7, karmic, fedora11 and preferably stay that way whenever update-grub is run (say on next aptitude safe-upgrade) so i dont have to keep customising them...

am i asking too much at this time?

---

### Post by MacUntu on 2009-08-02
> **vishalrao said:**
> am i asking too much at this time?

I'm afraid the answer is yes.

The only proper way would be to tell /etc/default/grub the preferred order and having a script like /etc/grub.d/99_sort that would sort existing entries according to that order.

[Edit: Obviously this has to happen in GRUB2, as scripts in /etc/grub.d/ are only part of the output for the new grub.cfg.]

For now I'd hand edit /boot/grub/grub.cfg and keep a copy of it (for upgrades, etc.).

---

### Post by vishalrao on 2009-08-02
> **MacUntu said:**
> I'm afraid the answer is yes.

thought so :D

> **MacUntu said:**
> The only proper way would be to tell /etc/default/grub the preferred order and having a script like /etc/grub.d/99_sort that would sort existing entries according to that order.

ouch ouch ouch, i think i'll leave the fancy scripting skillz work to the gurus, til grub2 stabilises and people get into the groove of how to do things with it.

> **MacUntu said:**
> For now I'd hand edit /boot/grub/grub.conf and keep a copy of it (for upgrades, etc.).

yup, i'll try that for the time being, thanks!

---

### Post by MacUntu on 2009-08-02
> **vishalrao said:**
> ouch ouch ouch, i think i'll leave the fancy scripting skillz work to the gurus, til grub2 stabilises and people get into the groove of how to do things with it.

Yeah that would be heavy scripting I guess. :) It just was a quick idea. Don't know how else you could combine the static "executing 00_..., 10_..., 20_..., ..." with having a preferred order, but tbh. I doubt we'll see that in Karmic.

I'd be happy enough about a way to turn off adding recovery mode and memtest entries, though.

---

### Post by ranch hand on 2009-08-02
> **vishalrao said:**
> now my question:

i have quad boot: win7rc, arch, karmic and fedora11.

i had to manually add fedora11 to "30_otheros".

the other entries for win7, arch and karmic show up automatically after running update-grub (thanks to 20_osprober i think).

now, after these entries are generated, how do i rearrange and relabel them? what is the proper way? edit the files in grub.d (how) or just edit grub.cfg (which i think is not recommended)?

The auto generated entries are karmic (default), win7, arch followed by my hand added fedora11.

I would like it to be arch (default), win7, karmic, fedora11 and preferably stay that way whenever update-grub is run (say on next aptitude safe-upgrade) so i dont have to keep customising them...

am i asking too much at this time?
No you are not asking to much.  The best I can tell you is to read this thread.  I got the help I needed to do this.

Briefly, grub.d is the key to everything.  The lower the file number the higher its content are on the menu.  I created a file "04_custom" and listed basically copy/pasted the entries for the OS boot from grub.cfg.

Here is my first entry for an installation of Stoner Edition1.0 (9.04) upgraded to 9.10A3 and the second an 9.10A2 installation (updated daily) that has had a Stoner edition theme pack added to it.  Kinky refers to Kinky kitten aname i prefer for Karmic;
```

#!/bin/sh 
# This file is an example on how to add custom entries 

echo "Adding KinkyStoner1.0 on sda12" >&2 
cat << EOF 
menuentry "KinkyStoner1.0 2.6.31-4-generic" {
	set root=(hd0,12)
	search --no-floppy --fs-uuid --set 2ee327b4-ea23-462e-9c85-9dfcb3b5617d
	linux	/boot/vmlinuz-2.6.31-4-generic root=UUID=2ee327b4-ea23-462e-9c85-9dfcb3b5617d ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-4-generic
}
EOF

echo "Adding KinkyStonerA2 on sda8" >&2 
cat << EOF 
menuentry "KinkyStonerA2 2.6.31-4-generic (on /dev/sda8)" {
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 3e5c2219-c1d2-4bb8-ac5c-47a95201876b
	linux /boot/vmlinuz-2.6.31-4-generic root=UUID=3e5c2219-c1d2-4bb8-ac5c-47a95201876b ro quiet splash
	initrd /boot/initrd.img-2.6.31-4-generic
}
EOF

```

The part of the entry I get on my menu list is the part I changed that reads
"KinkyStonerA2 2.6.31-4-generic (on /dev/sda8)".

I get a list of 8 OS' and then the menu that grub2 normally generates.  Kernal updates will have to be manually edited in the /etc/grub.d/04_custom file.

Works great after you run update-grub.

Start at pp5 of this thread to see posts by a grumpy geezer and the replies that helped create the file entries above.

---

### Post by MacUntu on 2009-08-02
Sure, you could also put your whole grub.cfg into 40_custom, edit it like you want, and delete everything else - but that's not what I'd call a proper way. With the next GRUB2 package upgrade you'd get a screwed grub.cfg (in vishalrao's case it would be: arch (default), win7, karmic, win7, arch, fedora11 :D).

---

### Post by ranch hand on 2009-08-03
> **MacUntu said:**
> Sure, you could also put your whole grub.cfg into 40_custom, edit it like you want, and delete everything else - but that's not what I'd call a proper way. With the next GRUB2 package upgrade you'd get a screwed grub.cfg.
You know, that is exactly what I thought.

The custom entries are on top of the regular grub.cfg menu, added there by update grub.  It not only works, it looks good.  The regular menu generated by the other grub.d files is not affected.

You can set it so that menu is not generated but it is the only one that is going to catch new installs and kernal updates.

Once the custom file is set up you will have to edit it to keep up.

A person with 1 or 2, even 3 OS' doesn't need to do this at all.  My shortest menu, still on grub-legacy, is 4 OS'.  The other 2 menus for my test platform drives have 7 (32bit OS' run on this box with 2 cpus shut down giving me a 32bit system) and 8 (64bit OS').  Reading through the menu even with a 100 second time out is a pain when all you have is kernal number and partition.

All my OS' are installed on 2 partitons.  The menu generated for grub.cfg starts with the one you are booting from and then to the one on partition 10,11,13,6,7,8,9 (booting from 12).  Add to that the mistaken entries of various memtests randomly scattered through this by grub2 (not quite finished yet but ahead of schedule) and it is a mess.  However, with the custom list I have 7 lines, 1 per OS, in the order I want.

Having to go edit 1 file when I get a kernal update and not have to sort through recovery an memtest entries to do it, seems pretty cool to me after grub-legacy (which I dearly love).

In short, yes this is the correct way to do this and it works slick.

The custom made (I also love gimp) background that I added to the menu and the font color changes so that I could read the menu over the background, were also all done in /etc/grub.d.  I think it is pretty slick boot manager.

I also think that it is good that it is coming with 9.10 as people are going to freak and we need to have the knowledge, experience, and the bugs worked out before 10.04 (LTS) comes along and people that just run LTS (my main OS is Hardy) will be updating and new folks coming in and it could be a real wreck if dumped on then.

I like messing with the box, particularly grub and I have been suffering from GAD (Grub Anxiety Disorder) as can be seen in my posts on pp5 (for which I am truely sorry).  When 9.10 comes out some of us better be ready for this thing.

Damn this is FUN.

---

### Post by drs305 on 2009-08-03
> **MacUntu said:**
> 
I'd be happy enough about a way to turn off adding recovery mode and memtest entries, though.

You turn off the memtest entries by editing the properties of /etc/grub.d/20_memtest86+  Just untick the 'executable' flag, or run the following:
```
sudo chmod -x /etc/grub.d/20_memtest86+
```
If the file isn't executable, it won't be included when update-grub is run.

To omit the recovery modes entirely, edit /etc/grub.d/10_linux and comment out these lines (they are lines 146-147 in my file):
> 
**#** linux_entry "${OS}, Linux ${version} (recovery mode)" \
**#**      "single ${GRUB_CMDLINE_LINUX}"


If you want one recovery mode option for insurance, place it in 40_custom. It will appear as the last entry on your menu.

---

### Post by MacUntu on 2009-08-03
Thanks for the info but I was thinking about a solution where I don't need to hack around. Currently the options configurable via /etc/default/grub are only a subset of what we had in the default options part of GRUB's menu.lst. This just needs to be completed. :)

---

### Post by ranch hand on 2009-08-03
> **MacUntu said:**
> Thanks for the info but I was thinking about a solution where I don't need to hack around. Currently the options configurable via /etc/default/grub are only a subset of what we had in the default options part of GRUB's menu.lst. This just needs to be completed. :)
I think that we need to try and use grub2 on its own instead of pining for grub-legacy.  I say that as one suffering from Grub Anxiety Disorder (GAD).

I believe that the new system is set up to be more flexible to future changes in file systems and different bootable media.

/etc/default/grub has one purpose.  /etc/grub.d has a separate purpose.  That they are not combined means more ease in adapting to unknown future developments.

While I am struggling with GAD, I am also excited by the, I think, increased power of grub2.

It is the "I think" that gnaws on the back of my mind.

---

### Post by drs305 on 2009-08-03
I can easily foresee entries in /etc/default/grub allowing the user to set a wide variety of options such as Recovery mode and memtest86+ entries. This will be followed by StartUp-Manager2 or an equivalent which will offer to make these changes for the user via a GUI app. The manual tweaks I have mentioned in this and other posts will be relatively easy to incorporate into the Grub 2 process.

---

### Post by ranch hand on 2009-08-03
OK, I need to get Mandriva to boot through grub2.

I was not sure it would boot as have had a little trouble with both KDE & Gnome versions.

Changed boot/root to 9.04 - grub-legacy.  Booted both so we know it will boot.

Changed back to 9.10 for boot/root and copied the grub-legacy menu entry for Man-Gnome to 01_custom and, I thought, modified it to work.

Did not work.

Changed it to;
```

menuentry "Man-Gnome, kernal 2.6.27.24-desktop586 (on /dev/sda12)" {
        set root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
	search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
	linux /boot/vmlinuz-2.6.27.24-desktop586 root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
	initrd /boot/initrd.img-2.6.27.24-desktop586 
}

```
Does not work.

Any idea as to the problem?

---

### Post by vishalrao on 2009-08-03
could it be the "set root=UUID=" line should be something like "set root=(hdx,y)" where x,y are the disk and partition numbers. note disk number starts from 0 but partition number starts from 1 for grub2.

so if grub legacy root was (hd0,11) then grub2 would be (hd0,12) since it shows sda12 in your post :)

---

### Post by phenest on 2009-08-03
I'm not sure splash=silent will work. If you want no splash, simply omit it. Also, I can't help but think those UUID's are making it overly complicated. Try doing hard links such as /dev/sda12 instead. Keep it simple to begin with. In fact, omit the search line too. Once it's working, you can always gradually add the other stuff back in.

---

### Post by drs305 on 2009-08-03
Talk about timely!  (Ref posts 71 & 74)

Our discussion of modifying the grub menu's recovery option was already under development it appears.  

In today's update, /etc/grub.d/10_linux was modified. The Recovery mode section now includes lines to exclude the Recovery mode from being listed in the grub menu. To disable it, add this line to **/etc/default/grub**:
> GRUB_DISABLE_LINUX_RECOVERY=true
**[COLOR="DarkRed"]This is why I think we will really enjoy Grub 2![/COLOR]**

Here is the section of /etc/grub.d/10_linux  (around line 150):
Old:
> 
  linux_entry "${OS}, Linux ${version}" \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}"
  linux_entry "${OS}, Linux ${version} (recovery mode)" \
      "single ${GRUB_CMDLINE_LINUX}"


New:
> 
  linux_entry "${OS}, Linux ${version}" \
      "${GRUB_CMDLINE_LINUX} ${GRUB_CMDLINE_EXTRA} ${GRUB_CMDLINE_LINUX_DEFAULT}"
[B]  if [ "x${GRUB_DISABLE_LINUX_RECOVERY}" != "xtrue" ]; then
    linux_entry "${OS}, Linux ${version} (recovery mode)" \
	"single ${GRUB_CMDLINE_LINUX}"
  fi[/B]


---

### Post by phenest on 2009-08-03
> **ranch hand said:**
> OK, I need to get Mandriva to boot through grub2.
```

menuentry "Man-Gnome, kernal 2.6.27.24-desktop586 (on /dev/sda12)" {
        set root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
	search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
	linux /boot/vmlinuz-2.6.27.24-desktop586 root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
	initrd /boot/initrd.img-2.6.27.24-desktop586 
}

```
Does not work.

Any idea as to the problem?

How about:
```
menuentry "Mandriva Gnome on /dev/sda12" {
linux (hd0,12)/boot/vmlinuz-2.6.27.24-desktop586 vga=788
initrd (hd0,12)/boot/initrd.img-2.6.27.24-desktop586
```

---

### Post by ranch hand on 2009-08-03
> **vishalrao said:**
> could it be the "set root=UUID=" line should be something like "set root=(hdx,y)" where x,y are the disk and partition numbers. note disk number starts from 0 but partition number starts from 1 for grub2.

so if grub legacy root was (hd0,11) then grub2 would be (hd0,12) since it shows sda12 in your post :)
I know but thought I would try something else.  This is the onethat does not work from grub.cfg;
```

menuentry "linux (on /dev/sda12)" {
	set root=(hd0,12)
	search --no-floppy --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
	linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e resume=UUID=59fe476e-6d4f-e390-ced9-f29328538dfc splash=silent vga=788
	initrd (hd0,11)/boot/initrd.img
}

```
I wonder about the 586 factor and if it just is not recognized.  I am getting the kernal must be mounted first error.

I am stumped.

---

### Post by ranch hand on 2009-08-03
> **phenest said:**
> How about:
```
menuentry "Mandriva Gnome on /dev/sda12" {
linux (hd0,12)/boot/vmlinuz-2.6.27.24-desktop586 vga=788
initrd (hd0,12)/boot/initrd.img-2.6.27.24-desktop586
```
I am going to give that whack right now.

---

### Post by xebian on 2009-08-03
> **vishalrao said:**
> i think i had a similar problem trying to get fedora 11 to boot. although it has older kernel but in grub2 i tried changing linux/kernel root option portion from:

```
root=/dev/disk/by-uuid/xxxxxx
```

to:

```
root=UUID=xxxxxx
```


Try that?

My point is who needs/wants device names when UUID is already known ?  Just use them, and if UUID on search line is NOT the same as the one on root=UUID parms then it's a big [COLOR="Red"]RED[/COLOR] Flag.
```

menuentry "Debian GNU/Linux (squeeze/sid) (on /dev/sda6)" {
        set root=(hd0,6)
        search --no-floppy --fs-uuid --set [COLOR="red"]c48c772a-4217-482f-b264-344f303d2e20[/COLOR]
        linux /boot/vmlinuz-2.6.30-1-amd64 [COLOR="red"]root=/dev/sda6[/COLOR]
        initrd /boot/initrd.img-2.6.30-1-amd64
}
```

---

### Post by ranch hand on 2009-08-03
> **ranch hand said:**
> I am going to give that whack right now.
error: must load kernal first

---

### Post by MacUntu on 2009-08-03
> **drs305 said:**
> Our discussion of modifying the grub menu's recovery option was already under development it appears.
Woohoo! \\:D/=D>

---

### Post by ranch hand on 2009-08-03
> **xebian said:**
> My point is who needs/wants device names when UUID is already known ?  Just use them, and if UUID on search line is NOT the same as the one on root=UUID parms then it's a big [COLOR="Red"]RED[/COLOR] Flag.
```

menuentry "Debian GNU/Linux (squeeze/sid) (on /dev/sda6)" {
        set root=(hd0,6)
        search --no-floppy --fs-uuid --set [COLOR="red"]c48c772a-4217-482f-b264-344f303d2e20[/COLOR]
        linux /boot/vmlinuz-2.6.30-1-amd64 [COLOR="red"]root=/dev/sda6[/COLOR]
        initrd /boot/initrd.img-2.6.30-1-amd64
}
```
I tried it like this;
```

menuentry "Mandriva Gnome on /dev/sda12" {
        set root=(hd0,12)
        search --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
        linux /boot/vmlinuz-2.6.27.21-desktop586-1mnb root=/dev/(hd0,12)
        initrd /boot/initrd.img-2.6.27.21-desktop586-1mnb
}
and 
menuentry "Mandriva Gnome on /dev/sda12" {
        set root=(hd0,12)
        search --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
        linux /boot/vmlinuz-2.6.27.21-desktop586-1mnb root=/dev/sda12
        initrd /boot/initrd.img-2.6.27.21-desktop586-1mnb
}

```
I do get a different error -> file not found

There has got to be a way or is the problem with 586?

---

### Post by papangul on 2009-08-04
I tried to switch to grub2 yesterday and it turned out to be one of the most irritating experiences I have had in a while. Grub2 worked nicely when I tried to chainload it from grub-legacy, but the problem occurred after issuing the 'update-from-grub-legacy' command. I got the 'Error 15' message on the next boot.

I have almost forgotten when I last tried to install grub manually, and I had no network to help me out. It took me half a day to recover from the mess.

---

### Post by cheesypoof on 2009-08-04
> **papangul said:**
> I tried to switch to grub2 yesterday and it turned out to be one of the most irritating experiences I have had in a while. Grub2 worked nicely when I tried to chainload it from grub-legacy, but the problem occurred after issuing the 'update-from-grub-legacy' command. I got the 'Error 15' message on the next boot.

I have almost forgotten when I last tried to install grub manually, and I had no network to help me out. It took me half a day to recover from the mess.

The same exact thing happened to me, however I loaded a jaunty livecd and followed the "If you messed up" section of: [https://wiki.ubuntu.com/KernelTeam/Grub2Testing]("https://wiki.ubuntu.com/KernelTeam/Grub2Testing"), which fixed the problem. If you try to switch over again in the future, and the problem reoccurs, try that website...

---

### Post by phenest on 2009-08-04
> **phenest said:**
> How about:
```
menuentry "Mandriva Gnome on /dev/sda12" {
linux (hd0,12)/boot/vmlinuz-2.6.27.24-desktop586 vga=788
initrd (hd0,12)/boot/initrd.img-2.6.27.24-desktop586
```

To start with, are you sure that Mandriva is on the 12th partition, on the first hard drive? Also, these kernel versions differ slightly. I don't use Mandriva, so is that correct?

> **ranch hand said:**
> I tried it like this;
```

menuentry "Mandriva Gnome on /dev/sda12" {
        set root=(hd0,12)
        search --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
        linux /boot/vmlinuz-2.6.27.21-desktop586-1mnb root=/dev/(hd0,12)
        initrd /boot/initrd.img-2.6.27.21-desktop586-1mnb
}
and 
menuentry "Mandriva Gnome on /dev/sda12" {
        set root=(hd0,12)
        search --fs-uuid --set c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
        linux /boot/vmlinuz-2.6.27.21-desktop586-1mnb root=/dev/sda12
        initrd /boot/initrd.img-2.6.27.21-desktop586-1mnb
}

```
I do get a different error -> file not found

There has got to be a way or is the problem with 586?

---

### Post by taavikko on 2009-08-04
```
menuentry "Mandriva Gnome on /dev/sda12" {
linux (hd0,12)/boot/vmlinuz-2.6.27.24-desktop586 vga=788
initrd (hd0,12)/boot/initrd.img-2.6.27.24-desktop586
```

This would imply that it needs to be on (hd0,11)
numbering starts from 0 so sda5 = hd0,4

---

### Post by phenest on 2009-08-04
> **taavikko said:**
> ```
menuentry "Mandriva Gnome on /dev/sda12" {
linux (hd0,12)/boot/vmlinuz-2.6.27.24-desktop586 vga=788
initrd (hd0,12)/boot/initrd.img-2.6.27.24-desktop586
```

This would imply that it needs to be on (hd0,11)
numbering starts from 0 so sda5 = hd0,4

No. Hard drive numbering starts at 0 (hd0), and partitions start at 1 (hd0,1).

---

### Post by taavikko on 2009-08-04
> **phenest said:**
> No. Hard drive numbering starts at 0 (hd0), and partitions start at 1 (hd0,1).

whups, so it does, thanks for correction, shouldn't try anything with migraine...

---

### Post by phenest on 2009-08-04
> **taavikko said:**
> whups, so it does, thanks for correction, shouldn't try anything with migraine...

An easy mistake considering so many number systems are zero based.

Ranch hand: I'm downloading Mandriva now, to dual boot with Ubuntu in a VM. I'll let you know what I find.

---

### Post by ronacc on 2009-08-04
and of course they are also referred to as SDA,SDB,etc which is not necessarily the same order that the bios sees them, and the UUID of a partition changes each time that partition is formated . There should be an app that lists out all of that info for each drive . I have 6 drives each with several partitions and it is real easy to get lost.

---

### Post by phenest on 2009-08-04
Ranch hand:

I installed Mandriva to a 2nd hard drive. Partition 5 has root on it, so:
```
menuentry "Mandriva" {
linux (hd1,5)/boot/vmlinuz
initrd (hd1,5)/boot/initrd.img
}
```
...worked fine for me.

What I would do is confirm the above works first, albeit change (hd1,5) for (hd0,12) that you are using. If all is well, remove the (hd0,12) and add the set root line:
```
set root=UUID=c23ad2ca-67a5-4a42-8fcc-3baa6d8e454e
```
...but you shouldn't need anything else. Make sure that the UUID is correct for that partition.

---

### Post by phenest on 2009-08-04
> **ronacc said:**
> and of course they are also referred to as SDA,SDB,etc which is not necessarily the same order that the bios sees them, and the UUID of a partition changes each time that partition is formated . There should be an app that lists out all of that info for each drive . I have 6 drives each with several partitions and it is real easy to get lost.

Just remember Grub doesn't understand /dev/whatever. It only knows the (hd0,1) format.

---

### Post by ronacc on 2009-08-04
I understand that but the problem sometimes is figuring out which drive is hd0 .I have on occasion had to resort to hitting E when the grub menu comes up and just start stabbing in hd0,1  * hd0,2 .....hd5,4 until I get a boot .

---

### Post by phenest on 2009-08-04
> **ronacc said:**
> I understand that but the problem sometimes is figuring out which drive is hd0 .I have on occasion had to resort to hitting E when the grub menu comes up and just start stabbing in hd0,1  * hd0,2 .....hd5,4 until I get a boot .

Try using <TAB> in Grub. It'll give suggestions. If you know what /dev it's on, it's just a question of converting to the Grub format, i.e. /dev/sdb5 is (hd1,5).

---

### Post by phenest on 2009-08-04
> **ronacc said:**
> There should be an app that lists out all of that info for each drive . I have 6 drives each with several partitions and it is real easy to get lost.

```
sudo vol_id -u /dev/sda1
```

---

### Post by taavikko on 2009-08-04
> **phenest said:**
> ```
sudo vol_id -u /dev/sda1
```

vol_id seems to be debrecated, so alternative is
```
sudo blkid
```

---

### Post by phenest on 2009-08-04
> **taavikko said:**
> vol_id seems to be debrecated, so alternative is
```
sudo blkid
```

Thanks. It seems you only need to type:
```
steve 12:14: ~ $ blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda1: TYPE="swap" UUID="a5076806-3e1d-4a1f-ade4-5f31c2b78672" 
/dev/sda3: LABEL="/home" UUID="8cd528d4-3837-4cc2-8942-07692a33cc68" TYPE="ext4" 
/dev/sda5: UUID="90e98646-31b2-4a67-a46d-8f6909234617" TYPE="ext4" 
/dev/sda2: UUID="40597855-d643-4b8e-bc52-a4795cd63a20" TYPE="ext4" 
/dev/sda6: UUID="e302b8d5-405e-41af-b9fe-27527939f6b7" TYPE="ext4" 
```

---

### Post by papangul on 2009-08-04
> **phenest said:**
> No. Hard drive numbering starts at 0 (hd0), and partitions start at 1 (hd0,1).
This is the section in my menu.lst that chainloads grub2(it works):```
title		Chainload into GRUB 2
root		(hd0,2)
kernel		/grub/core.img
```
That is my third primary partition- /dev/sda3 that is right now mounted as /boot. 

So the partition number '2' seems to be referring to the third partition here.

---

### Post by phenest on 2009-08-04
> **papangul said:**
> This is the section in my menu.lst that chainloads grub2(it works):```
title		Chainload into GRUB 2
root		(hd0,2)
kernel		/grub/core.img
```
That is my third primary partition- /dev/sda3 that is right now mounted as /boot. 

So the partition number '2' seems to be referring to the third partition here.

That's Grub1. Here's some reading for everyone:
[Grub naming convention]("http://www.gnu.org/software/grub/manual/html_node/Naming-convention.html") and [differences from Grub1]("http://grub.enbug.org/Manual#head-68cc51835aa5531f789f30d26708b7cdffa05769")

---

### Post by papangul on 2009-08-04
Thanks for the info! I need your help for sorting out another little problem. When I install grub2 in the MBR, how do I set grub2 to look in sda3 for the grub.cfg file?

---

### Post by Totzo on 2009-08-04
Does anyone know if there is a way to use "savedefault" in grub2? I can't seem to find any documentation on this, appologies in advance if I'm missing something obvious here!

---

### Post by phenest on 2009-08-04
> **papangul said:**
> Thanks for the info! I need your help for sorting out another little problem. When I install grub2 in the MBR, how do I set grub2 to look in sda3 for the grub.cfg file?

Check [this wiki]("https://wiki.ubuntu.com/KernelTeam/Grub2Testing"). Scroll down to 'If you messed up' and follow the instructions.

---

### Post by phenest on 2009-08-04
> **Totzo said:**
> Does anyone know if there is a way to use "savedefault" in grub2? I can't seem to find any documentation on this, appologies in advance if I'm missing something obvious here!

The obvious being that it doesn't exist, nor have any alternative. I found a bug reported on Launchpad but it was marked as 'WishList'.

---

### Post by papangul on 2009-08-04
> **phenest said:**
> Check [this wiki]("https://wiki.ubuntu.com/KernelTeam/Grub2Testing"). Scroll down to 'If you messed up' and follow the instructions.
I am just trying the 'grub-install' command right now, hope everything will be sorted out automagically, I don't have a live cd and my system doesn't boot from usb, so just praying, if that's going to help..

---

### Post by papangul on 2009-08-04
wow..it worked..(but how I don't know)...

---

### Post by Totzo on 2009-08-04
> **phenest said:**
> The obvious being that it doesn't exist, nor have any alternative. I found a bug reported on Launchpad but it was marked as 'WishList'.

That's odd, I'd have thought it would be backward to remove this option and not that hard to implement.

---

### Post by vishalrao on 2009-08-04
> **xebian said:**
> My point is who needs/wants device names when UUID is already known ?  Just use them, and if UUID on search line is NOT the same as the one on root=UUID parms then it's a big [COLOR="Red"]RED[/COLOR] Flag.


No red flag for me. I have differing UUIDs because my /boot and / are on different partitions...
To find out which UUID is for which disk try:

```
ls -al /dev/disk/by-uuid
```

---

### Post by phenest on 2009-08-04
> **Totzo said:**
> That's odd, I'd have thought it would be backward to remove this option and not that hard to implement.

I do believe that Grub2 is still under development. Check [here]("http://www.gnu.org/software/grub/grub-2.en.html").

---

### Post by drs305 on 2009-08-04
> **Totzo said:**
> That's odd, I'd have thought it would be backward to remove this option and not that hard to implement.

As phrenest mentioned, Grub 2 is still under development, so it may yet appear. 

Just yesterday Grub 2 was updated to include the option to prevent Recovery mode items from appearing in the menu if the user desires. [noparse](Post #78)[/noparse].

---

### Post by papangul on 2009-08-04
Grub2 seems to be lacking the 'hiddenmenu' option:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/386916](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/386916)

---

### Post by Totzo on 2009-08-04
> **phenest said:**
> I do believe that Grub2 is still under development. Check [here]("http://www.gnu.org/software/grub/grub-2.en.html").

I hear you, lets hope someone's watching the wishlist!  :)

---

### Post by Totzo on 2009-08-04
found this on the grub wiki todo list [[COLOR="Red"]here[/COLOR]]("http://grub.enbug.org/TodoList"):

> General Issues

    * Add journal playback support for all journaling filesystems.
    * Add support for internationalization (See AboutInternationalization). !!!
    * Write a manual. !!
    * Add a fancy menu interface which utilizes the VideoSubsystem extensively with many eye-candies. This is important to beat GRUB legacy. :) (ColinBennett is working on this)
    * Make multiboot portable. Perhaps even write a new standard.
    * Implement ModuleLoading in grub-emu.
    * Use GRUB memory management in grub-emu.
    * Add some of the missing commands (See CommandList). !
    * Add missing features into the menu entry editor (such as C-t).
    * **Support for multiple fallback entries and default saving as in GRUB Legacy.**
    * Security-related features (i.e. password and lock).
    * Look at the nested functions issue; removing nested functions is not an option. See NestedFunctions !!!
    * Add support for partitions containing partitions, this is for example used for Solaris partitions in an Apple partition, but also in many other cases.
    * Add support to load compressed modules. 

---

### Post by phenest on 2009-08-04
> **papangul said:**
> Grub2 seems to be lacking the 'hiddenmenu' option:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/386916](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/386916)

Not true. Try this...
```
#!/bin/sh
echo "Adding hidden menu" >&2
cat << EOF
echo -n "Press ESC for the menu... "
if sleep --verbose --interruptible ${GRUB_TIMEOUT} ; then
set timeout=0
else
set timeout=-1
fi
EOF 
```
...and save as 06_hidden_menu. Et voila!

Thanks to dinxter for this one.

---

### Post by papangul on 2009-08-04
sorry,didn't get it..where do I save it? Thanks a lot for the solution though(will be handy till grub2 gets some eyecandy)

---

### Post by ranch hand on 2009-08-04
@phenest
So much to reply to, wow.

I am on the drive now and running in 32bit mode.

Yes I am sure that this Mandriva is on sda12 and gparted agrees.

I only have the one drive "on" at the moment, I run them separately to avoid contaminating the other drives (the other internal is my production drive).

I ran "uname -a" and decided to use the entire kernal name to see if it helped.

I have edited the 01_custom file, with suitable corrections for hd0,12, to match yours.  I am having to use screem as I have the gedit crashs bug (yes reported).

Running update-grub.

Did you get the 32bit version and was it 586?  I downloaded the 64bit version but haven't had time to install yet.

I have heard (where I am not sure) that Ubuntu has shaky support for 586.

Update grub is done, 9.10 update is done - I better restart and see what happens.

EDIT

Well I am back.

phenest
I don't care what they say, you're a great guy.

I am on Mandriva-Gnome as I type.

This is great, thanks a HUGE bunch.  This helps in 3 important ways;
A) Mandriva-Gnome is booting from grub2
B) My Grub Anxiety Disorder is repressed for now
C) I can now try this on Mandriva-KDE (hd0,14)

Thanks again.

And thanks to everyone else that was in on this fiasco.

THIS REALLY IS FUN.

---

### Post by phenest on 2009-08-04
> **papangul said:**
> sorry,didn't get it..where do I save it? Thanks a lot for the solution though(will be handy till grub2 gets some eyecandy)

Save to /etc/grub.d . As for eye-candy, using a background picture has already been discussed in this thread.

---

### Post by taavikko on 2009-08-05
Has anyone noticed that grub uses only us -keyboard layout?
I really can't remember having this with the older grub.
Though I hardly touch it anyway...

either way, this in my opinion should be made configurable, if possible.

---

### Post by wayne_cat on 2009-08-05
> **taavikko said:**
> Has anyone noticed that grub uses only us -keyboard layout?
I really can't remember having this with the older grub.
Though I hardly touch it anyway...

either way, this in my opinion should be made configurable, if possible.

Would be a nice feature

btw ... the old grub also uses the us keyboard ... tested with 0.97-29ubuntu56 on Karmic

---

### Post by taavikko on 2009-08-05
> **wayne_cat said:**
> Would be a nice feature

btw ... the old grub also uses the us keyboard ... tested with 0.97-29ubuntu56 on Karmic

Thansk, couldn't test. haven't got any grub-legacy in da house.
(and no liveCD's)

Maybe someone should write a feature request.
Majority I suspect uses other than US layout?

---

### Post by phenest on 2009-08-05
I'm on UK Dvorak.

---

### Post by wayne_cat on 2009-08-05
discussions about localization / keyboard layout in grub2



[http://lists.gnu.org/archive/html/grub-devel/2008-09/msg00301.html](http://lists.gnu.org/archive/html/grub-devel/2008-09/msg00301.html)

[http://lists.gnu.org/archive/html/grub-devel/2008-09/msg00319.html](http://lists.gnu.org/archive/html/grub-devel/2008-09/msg00319.html)

---

### Post by taavikko on 2009-08-05
> **wayne_cat said:**
> discussions about localization / keyboard layout in grub2



[http://lists.gnu.org/archive/html/grub-devel/2008-09/msg00301.html](http://lists.gnu.org/archive/html/grub-devel/2008-09/msg00301.html)

[http://lists.gnu.org/archive/html/grub-devel/2008-09/msg00319.html](http://lists.gnu.org/archive/html/grub-devel/2008-09/msg00319.html)

Aargh, they're over an year old threads...
so i'll be thinking this will be a no go.

localized keyboard layouts would have been sweet.

---

### Post by wayne_cat on 2009-08-05
> **taavikko said:**
> Aargh, they're over an year old threads...
so i'll be thinking this will be a no go.

localized keyboard layouts would have been sweet.

hmm ... 6 month ago:

[http://lists.gnu.org/archive/html/grub-devel/2009-02/msg00092.html](http://lists.gnu.org/archive/html/grub-devel/2009-02/msg00092.html)

haven't found more about "Carles Pina" yet ... still searching the list

---

### Post by Herman on 2009-08-07
I was interested in finding a command that will tell us which version and exactly which update of GRUB we have. 
I looked for a text file in /boot/grub/  containing those details. We used to have a file like that in GRUB Legacy but I couldn't find one in GRUB 1.96.
I settled for this aptitude command instead,
```
sudo aptitude show grub-pc
```I just thought I'd post that in case it might be useful to anyone.

Regards, Herman :D

---

### Post by drs305 on 2009-08-07
> **Herman said:**
> I was interested in finding a command that will tell us which version and exactly which update of GRUB we have. 
Regards, Herman :D

Herman,

I did some poking around and found this (/usr/sbin/grub-install):
```

grub-install -v

```
> 
drs305@mycomputer:~$ grub-install -v
grub-install (GNU GRUB 1.96)


---

### Post by wayne_cat on 2009-08-07
How does os-prober find the installed systems? I have a chroot with Dapper on my notebook (on sda5) and os-prober "finds" it:

(last line)
 ```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-5-generic
Found initrd image: /boot/initrd.img-2.6.31-5-generic
Found linux image: /boot/vmlinuz-2.6.31-4-generic
Found initrd image: /boot/initrd.img-2.6.31-4-generic
Found linux image: /boot/vmlinuz-2.6.31-3-generic
Found initrd image: /boot/initrd.img-2.6.31-3-generic
Found linux image: /boot/vmlinuz-2.6.31-2-generic
Found initrd image: /boot/initrd.img-2.6.31-2-generic
Found linux image: /boot/vmlinuz-2.6.30-9-generic
Found initrd image: /boot/initrd.img-2.6.30-9-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Mac OS X on /dev/sda2
Found Ubuntu karmic (development branch) (9.10) on /dev/sda3
Found Ubuntu 6.06 LTS (6.06) on /dev/sda5
```There is no kernel in the chroot and so it does not add it as a boot option.

No problem ... I'm just curious ... which files uses os-prober to recognize an operating system?

---

### Post by dinxter on 2009-08-07
think it generates partition lists on /sys/block/ then runs the tests in /usr/lib/os-probes/mounted/ on them, dont quote me on that though :)

---

### Post by Piscium on 2009-08-12
Still experimenting with Grub2.

I explained in a previous post how I upgraded to grub2 using Synaptic to download and install grub2, followed by manually entering &#8220;sudo update-grub&#8221; and &#8220;sudo-grub-install&#8221;.

Today I installed 9.04 Kubuntu on a different partition of the same disk. Then I upgraded it to grub2, just for testing purposes, as I do not intend to boot from this partition. 

Instead of using Synaptic I called KpackageKit. I found it behaves differently from Synaptic.

First of all with Synaptic if you choose to install &#8220;grub-pc&#8221;, it tells you that it will uninstall &#8220;grub&#8221;, asking if you agree. KpackageKit does not do so, however at some point during the installation of &#8220;grub-pc&#8221; it issues an error message saying that grub (that is v. 1) needs to be uninstalled first. 

Then KpackageKit seemed to get into some infinite loop, or maybe I did something wrong. In any case, I ended up killing the KpackageKit process. I launched it again, and then chose grub for uninstall, applied, and it went fine. Then I chose grub-pc for install, applied, and it went fine.

But again it was different from Synaptic, because KpackageKit did not mention the possibility of chain loading. Instead it went ahead on its own and called &#8220;update-grub&#8221;. I know that because grub.cfg was created. But it did not do the whole job, as grub-install was not called. This means that if someone would reboot at this stage the only way to get back to the new Kubuntu partition would be through booting from another partition or by means of a rescue CD.

In a nutshell, if you are running Kubuntu and want to upgrade to grub2, this is one way to do it:
1.	Launch KpackageKit, search for &#8220;grub&#8221;, select it for uninstall, apply.
2.	Search for &#8220;grub-pc&#8221;, select it for install, apply.
3.	do &#8220;less /boot/grub/grub.cfg&#8221;. Take a look at it to see if it is OK.
4.	If so, do &#8220;sudo grub-install /dev/sda&#8221; to load grub2 on your MBR. 

So in this case there is no need to do &#8220;sudo update-grub&#8221; as it is done automatically by KpackageKit.

Note that this probably will not work with 8.10 or older, as I think grub-pc is not available on these versions.

António

---

### Post by ranch hand on 2009-08-12
I have a bad habit of installing Synaptic on Kubuntu installations because the package management is terrible.

The install you did through synaptic should have run update-grub too.  Were you watching the "details" when you did that?

---

### Post by Piscium on 2009-08-14
> **ranch hand said:**
> The install you did through synaptic should have run update-grub too.  Were you watching the "details" when you did that?

update-grub was not run. I checked the details, and also grub.cfg could not be found.

---

### Post by ranch hand on 2009-08-14
Check synaptic, search for "grub2" and install anything missing because something is.

If it all apears to be installed, reinstall.

---

### Post by mr_jrt on 2009-08-16
The savedefault option on my existing grub seems to have stopped working (/boot/grub/default gets updated...but the menu always starts on the first entry)...and that seemed like a good excuse to try grub2.

So far I've got it working mostly as I want...bar two things.

1) savedefault doesn't seem to work - making the exercise largely pointless :(
2) I can't find any mention anywhere of how people are adding dividers and spacing rows

1) means I'll comment out the chainloading and go back to figuring out why grub-legacy isn't working
2) ...the best I've got so far is adding this:
```
menuentry " " {
        echo
}
menuentry "&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;" {
        echo
}
menuentry " Others " {
        echo
}
menuentry "&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;&#9473;" {
        echo
}

```...which looks ok, but is, unlike as with grub legacy, executable. Meaning if you select it, the screen flashes before returning to the menu. Doesn't break anything, but is a bit rubbish.

Leaving out the command(s) results in the menuentry either dying or being ignored (and thus not displayed). echo was the least harmful command I could come up with :)

---

### Post by phenest on 2009-08-16
> **mr_jrt said:**
> The savedefault option on my existing grub seems to have stopped working 

It doesn't exist in Grub2 (yet).

---

### Post by mr_jrt on 2009-08-16
Yeah, that quote refers to the savedefault having stopped working my grub-legacy

...and for the record, I seem to have been mistaken. It seems you can execute spaces and dividers in grub-legacy, and they behave exactly as with grub2. My bad! Still rubbish though :p

[edit]
...and then, as if by magic, savedefault starts working again...

Truly, these computer things are magical at times. ;)

...though I can't see why removing the tabs between "default" & "saved" should cause it to start working. Hmm.

---

### Post by ranch hand on 2009-08-16
> **mr_jrt said:**
> Yeah, that quote refers to the savedefault having stopped working my grub-legacy

...and for the record, I seem to have been mistaken. It seems you can execute spaces and dividers in grub-legacy, and they behave exactly as with grub2. My bad! Still rubbish though :p

[edit]
...and then, as if by magic, savedefault starts working again...

Truly, these computer things are magical at times. ;)

...though I can't see why removing the tabs between "default" & "saved" should cause it to start working. Hmm.
I have not tried chain loading with grub-legacy.

I find that grub2 works fairly well on its own.  I have one drive (external dual with 2 320Gb WD HDDs) with 11 OS' and it is doing pretty well, screws up some and can't read the Mandriva ones well enough to boot them with its idea of a menu entry.

I use custom entries for all of them because then I can label them, have them where I want them in the menu, have a single line for each OS and the list is at the top of the menu so it is right therre and easy to use.

Grub2 is going to great.  There are a few really rough spots in it now though.

In grub-legacy you could move the OS you want as default to the top of the list in /boot/grub/menu.lst.

---

