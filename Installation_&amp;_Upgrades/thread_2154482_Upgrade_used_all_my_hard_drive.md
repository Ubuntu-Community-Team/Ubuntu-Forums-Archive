---
title: "Upgrade used all my hard drive"
date: 2013-06-14
forum: Installation &amp; Upgrades
---

### Post by Kenc3 on 2013-06-14
This project has been going on for days and nghts.
 I have a PC which had both Windows7 and Ubuntu 11.04 on it together. I decided to use the Ubuntu again and the challenges began.
 The PC is
Memory 2.0 GB
Processor Intel Core2 E7400 @2.80 X2
500 GB Hard Drive
Now the problem.

The Windows says it is 32 Bit. I have thought it was 32 bit all along.
I upgraded (sort of ) the Ubuntu during the last two days to 11.10. 
I noticed this morning that the Ubuntu says it is OS 64bit.
I had a flashing screen late last night when I finished and had to shut it down. I kept getting messages that I had only about 200 MB of space left on the hard drive. 
 
 I am trying to figure out if I have a good install or not and if the old stuff is off it already. 
 If I have a good install, can I partition to open more space on the Hard Drive and finally where do I find the screen to do this on 11.10?
 Sorry for the long post.
Ken

---

### Post by AgentZ86 on 2013-06-14
Ubuntu 11 is not supported I am assuming you must be talking about Ubuntu version 12.04 and 12.10 ? 

Please confirm this first please
Thanks

Then from the Live CD you can run without installing anything in order to inspect your machine further. 
Also from the live cd you can run Gparted. This is the partition tool so you can see exactly how many partitions and what types of partitions they are. And how much space is used / left on each one
Post that info here too

It's a start

---

### Post by Bashing-om on 2013-06-14
[COLOR=#000000]Oh ! Kenc3; What a situation you have inherited.

Trying to update End Of Life installs is trying to say the least using the proper channels to do so.
As you know 11.04 reached EOL sometime ago, 11.10 has also ended...A while back..
Did you use the "old.release" repositories to effect the upgrades ?

Are you able now to boot into ubuntu ? To where we can issue some command line commands to see what is ?
[/COLOR][INDENT=2][COLOR=#000000]
options may be very limited

[/COLOR][/INDENT]

---

### Post by Kenc3 on 2013-06-14
I made a USB stick and it is not recognized.
I had to spend all day yestereday and late into the night doing an upgrade from 11.04. I thought it was doing 32 bit.
If I could, I would take Ubuntu off the computer and start all over. It is a dual boot with 
Windows7.
By the way, Thanks.

---

### Post by Kenc3 on 2013-06-14
I am in 11.10 now on the other computer. I noticed there may be a problem with the USB drive I made using UNetbootin. It says something about a binary executable that may not work.
I am corresponding on a netbook and trying to fix a PC.
Ken

---

### Post by Bashing-om on 2013-06-14
[COLOR=#000000]Kenc3;

Yuk ! ... on the box you are trying to fix... can you boot a liveDVD of  ubuntu as a 32 bit architecture ? 64 bit machines will run a 32 bit architecture,,, if so ...we can look at the machine and tell what is what.
[/COLOR][INDENT=3][COLOR=#000000]
try'n to help[/COLOR][/INDENT]

---

### Post by Kenc3 on 2013-06-14
The one that says 64 bit is running now on the other computer. Looks pretty but looks can be deceiving.
 Meanwhile on the Netbook, I just installed Firefox cause I found out that IE will not download after 420MB.
 I also cleaned up a USB Drive. Now I need to find a good copy of 12.10 LTS. I plan to use UNetbootin again.
Ken

---

### Post by Kenc3 on 2013-06-14
I am remaking a usb DRIVE WITH 12.04 Live on it. It said something about if I wanted something, I think it had to do with netbooks, and I just went ahead and did whatever Unetbootin was going to do. It wil probably take all day to make the disk. It is 693MB.
Ken
BTW I am in the Philippines so it is morning here.

---

### Post by Bashing-om on 2013-06-14
[COLOR=#000000]Kenc3; hey

If you can run 64 bit (most likely from the hard ware specs you provided) you want to run the 64 bit version of ubuntu... will save a lot of bandwidth if we know in advance which architecture to download and install. From a live medium on the system you are fixing ... the command "dmidecode" will reveal a lot about the hard ware ..in particular ...64 bit !

12.04 is the way to go .......Long Term Support for lasting stability !
[/COLOR][INDENT=2][COLOR=#000000]
just try'n to help

[/COLOR][/INDENT]

---

### Post by Kenc3 on 2013-06-14
I have been Windows for so long that I have forgotten the codes and how to use them.
The Ubuntu is running on GUI (the one I picked up). I am not sure I want to change that right now.
I have the radio working on there now and I mimimized it and cannot find it to turn it off..
This is going to get interesting before I am finished.
I am retired so I have time to do this...if I live long enough...
Ken

---

### Post by Kenc3 on 2013-06-15
I think my Ubuntu is trying to help me but it is talking Ubuntuese.
 I pressed the button to upgrade from 11.10 to 12.04LTS and I got the message after awhile that I needed 1421MB. It said to use sudo aot-get clean to do this.
 I have the gui on now and am completely lost if I change to the other one. I don't even know how to change to the other screen.
 Can I remove the old system without going there or is there a way I can do it?
 I am on the netbook writing this so I can keep the answer on while I am fixing the PC.
Thanks in advance
Ken

---

### Post by Kenc3 on 2013-06-15
I cannot find out how to get rid of the old copy of Ubuntu 11.04.  I know that is the problem that is keeping me from upgrading to 12.04.
I need 1421MB and the most I have managed to get is 845.1 MB. That was in the download center.
How do I get rid of the old files???

---

### Post by Kenc3 on 2013-06-15
I finally managed to get enough room for the upgrade to 12.04 to begin. It will be a long night.
Someone bring me some coffee!
Thanks for all the help. I hope this goes okay.
Ken

---

### Post by Bashing-om on 2013-06-15
[COLOR=#000000]Kenc3; Simple is always better.

Are you doing this the hard way ? Trying to update and upgrade from the installation ?

Anything in ubuntu you want to keep, back it up now!

Much Much better to do a "clean" install as in ->
download the .iso image file
burn that .iso file as an "image" to CD ( can still fit on a CD in version 12.04)
boot the liveCD into "try ubuntu" mode
activate Gparted and delete the former ubuntu install (terminal command "sudo fdisk -l" to know )
install with the parameter "install along side of" 
answer the few questions the installer requires and 
insure that the bootloader - grub - is to be installed to "sda"

DONE .... up and running ubuntu 12.04 dual booting.
[/COLOR][INDENT=3][COLOR=#000000]
clean is better
 [/COLOR][/INDENT]

---

### Post by grahammechanical on 2013-06-15
@Kenc3

I think that some of your confusion is due to a misunderstanding. A 32bit CPU will only run a 32bit OS But a 64bit CPU will run both a 32bit OS or a 64bit OS. You can take it for granted that the Intel Core2 E7400 is a 64bit CPU. So, it can run both a 32bit Windows 7 and a 64bit Ubuntu. This must be the case because the Ubuntu installer will not let us install a 64bit Ubuntu onto a 32bit CPU machine.

Here is the proof

[http://ark.intel.com/products/36500](http://ark.intel.com/products/36500)

Regards.

I would like to add one more thing. Has anyone thought of the word "Wubi" as a reason for running out of disk space in the first place? An upgrade should remove old files. A new installation should be over the old installation but a Wubi install might install 12.04 and still leave 11.10 on there and then there might not be enough space in the Windows folder that is pretending to be a partition on the hard drive.

---

### Post by Kenc3 on 2013-06-15
I am running everything on 32 bit. I thought everything was going fine last night until about 12:30AM when everything stopped. It said it was preparing toconfigure libe-bin. I waited for a long time and then finally restarted the computer ( bad mistake). Now when I choose Ubuntu from the menu I get a pretty maroon screen...
 I finally went to bed a little after 1AM and am back at it again.
 I am convinced that Microsoft is trying to control what we put in the computers. When I try to choose Boot options I only get a series of ways to start Windows 7.
 I am trying to make a DVD today. If I cannot succeed in this I will order one from Ubuntu. I am determined to get this fixed before I go back to reading for librivox.
Ken

---

### Post by Kenc3 on 2013-06-16
This battle update is coming from my Netbook.
 I pulled out a portable DVD Writer that I bought a long time ago for the Netbook. The iso image would not burn on the Netbook but when I plugged the writer into the PC ot wrote the DVD for me. I did the right click and it went right through.
 Now I am waiting for the PC to boot from it.
 So far I have been sitting here for at least 30 minutes looking at a Maroon screen with Ubuntu on it and 5 dots uder it that go on and off.  I am afraid to stop the process now. Is this normal or did I make a defective DVD?
Ken

---

### Post by Bashing-om on 2013-06-16
[COLOR=#000000]Kenc3; 

Windows 7.. UEFI might be a factor... though UEFI was not prevalent until Windows8, but you might check your bios and see if that is a factor... then there is also "secure boot"... Is there a small ssd that Windows boots on ? So many things now-a-days to hinder installing an alternate operating system. One more hill to climb over !

If you can get a CD burned ..and remember to check the md5sum .. and boot that liveCD into "try ubuntu" mode ... will be a long way towards  dual booting ! 
[/COLOR][INDENT=2][COLOR=#000000]
hang in there, quit never done nothing [/COLOR][/INDENT]

---

### Post by Kenc3 on 2013-06-16
Where do I find the MD5sum and how do I check that?
In the meantime, the red dots stopped blinking on the screen and the green light on the DVD drive is blinking and also occassionally the red one on the hard Drive is blinking sometimes like if they are talking to each other getting ready for the next battle.
 The drive I made the DVD is not the same one I used to boot with. I think....
WOW! I just got a big screen full of writing. Looks like a lot of stuff is starting to configure.
maybe it is either replacing the old Ubuntu if it detected it or it is going to put Ubuntu on the hard drive and erase Windows. 
 Right now I wouldn't care either way just so it works.
Ken

---

### Post by Kenc3 on 2013-06-16
Everything is quiet. The lights on the CPU are all out except for an occasional flicker from the had drive light.
Thinking about restarting the computer and see if it comes on normally with 12.04 on Ubuntu. If not, I can always go back and restart with the DVD in.
Ken...

---

### Post by Kenc3 on 2013-06-16
I may not have Windows anymore but I will have Ubuntu 12.04. It is installing now.
I have not had a chance to check yet to see what I did but it is installing.
Ken

---

### Post by Kenc3 on 2013-06-16
I finally have Ubuntu 12.04 installing. I don't know if I wiped out Windows or not. I haven't checked yet.
Ken

---

### Post by AgentZ86 on 2013-06-16
do you have to upgrade or just install new copy. Forget unetbootin

You can make the live flash directly from the Ubuntu OS There is a startup disk option it creates the live CD/DVD or live flash drive directly from the OS itself
If your computer is a 64bit machine and has windows 32 on it this is OK to install 64 bit Ubuntu on a 64bit partition. The live CD/DVD or Flash of Ubuntu 12.04 64 bit will handle this for you.
Unless you prefer to intall the 32 bit version. OR if your machine is a 32 bit version and you have no other choice. 
If your machine is a 32 bit version then you have to install the Ubuntu 32bit option. But the install process will be the same as I suggest below


Once you create your startup disks from the OS of choice.
You select the ISO of the download to put on the disk plain and simple

Boot to the live drive CD/DVD or flash
Select the partition that has the old install on it. There will be options to overwrite the current installation and your dual boot will stay entact.
Just DO NOT overwrite your windows partition it will stay entacted.

Let 12.04 or 12.10 do everything for you
Don't let it write to the entire disk. It will give options along the way.

It will ask to install side by side with the others. but just Select the Old Ubuntu partition
Don't select any upgrade but do a full install. 
It will overwrite your home directories etc. and you will lose anything on your Ubuntu drive.
Sooooo that means if you want to keep any of that you have to move that to your windows partition while booted to your live CD/DVD or flash first
Then you can overwrite your old Ubuntu installation without losing your data files.

That should do it.

---

### Post by Bashing-om on 2013-06-16
[COLOR=#000000]Kenc3;

I am monitoring .. trying to keep up with your progress..
Be aware I am in GMT -6 time zone, so my responses are not the most timely in the world.
[/COLOR][INDENT=2][COLOR=#000000]
making progress

[/COLOR][/INDENT]

---

### Post by Kenc3 on 2013-06-16
Bash-  I finally got to bed early last night. The install didn't go the way the book said. I didn't get the option to put it beside my Windows. My options were to format or Wipe out Windows. It turned out that either one wiped out Windows.
 It took a long time for the upgrade but it finally finished around 6PM last night. This morning I found that some of it had not installed right and some of it was not finished. I let that fix itself and carried on.
 I am now listening to the Radio from Seattle and putting most of what I had on Windows back on. The things I lost were either not being used now. Some of them were expensive and I may have to see if they will work here. One of them was an expensive Movie making program. (Power Director)  
 It will take some getting used to this new system but Windows is gone. If I really miss it, I still have it on the Netbook and my son still fights it on his computer.
 For now, I don't ahve to worry about them wanting to use my computer....HaHa.
 Thanks for all the help.
 I still haven't figured out how to close one window at a time in Firefox. It only closes all or none. There are a few others I need to find. 
Ken:D

---

### Post by Bashing-om on 2013-06-16
[COLOR=#000000]Kenc3; Hey, way to go !

OK, If you have completed the install and if you have a good internet connection... very first thing to do is get that system updated, (will have system status for sure then)... 
Best policy is from the command line so you see all the generated text.
From the desk top do a key-combo ctl+alt+t for a terminal and in terminal do:
```
sudo apt-get update
sudo apt-get upgrade
```
which is:: sudo ==Super User DO for administrative privileges;
apt-get is the package manager
update ... to sync the databases between your system and that of the repository getting you the latest info
upgrade ... upgrades all your installed packages to latest available versions

[/COLOR][INDENT=3][COLOR=#000000]
then you should be set to go

[/COLOR][/INDENT]

---

### Post by Kenc3 on 2013-06-16
I am going to do that but I am worried that things are working so good right now. 
 I just got scared a minute ago when I got the message that my browser had been upgrded and I needed to restart. I did and a big maroon screen came up for a few minutes. Scared the crap out of me!
 I need to get rid of that thing that keeps asking me if I want so save passwords.
I will let you know how the stuff you gave me comes out. 
I am praying......
Ken

---

### Post by Kenc3 on 2013-06-16
The terminal just stopped. Probably a good idea to restart.
 I am putting in my radio stations that I listen to on the Internet. Wonder what there is from your area.
Ken

---

### Post by Bashing-om on 2013-06-16
[COLOR=#000000]Kenc3;

Hey,,, like, you are going to have to bite the bullet some time and update. May as well do it now before putting in a lot of work and effort only to (maybe only) have the system crash. Update/upgrade, if for no other reason than to be sure the system is solid and stable ! Also there are the security updates -> cheap insurance.

Here it is Alice 107.7 !
[/COLOR][INDENT=4][COLOR=#000000]ubuntu, operating system of choice

[/COLOR][/INDENT]

---

### Post by Kenc3 on 2013-06-16
I did those two you gave me. They are finished. Is there more to do?
Alice 107.7 is not available here.
I gotta go eat lunch.
How do I edit my profile and add a photo to my profile?
Ken

---

### Post by Bashing-om on 2013-06-16
[COLOR=#000000]Kenc3; Nope, not for now,,, explore your new system, get comfortable with it ,,, expect a learning curve and an ajustment to a different way of thinking ---------open source and no secrets.
For now you may be concerned if your windows is indeed gone bye bye ... in terminal do:
```
sudo fdisk -lu
``` which will list every partition on your system at large. If one of the columns in the output is not "ext4" and "swap" then ya got more than ubuntu somewhere.

 Got a question, ask... the only dumb question is the one that is not asked !
[/COLOR][INDENT=3][COLOR=#000000]
enjoy

[/COLOR][/INDENT]

---

### Post by Kenc3 on 2013-06-16
I got
 /dev/sda1  Boot w95 Fat32
/dev/sda2   Extended
/dev/sda5   Linux Swap  Solaris
/dec/sda6   Linux
They are listed as blocks.
If there are 512 bytes to a block then It comes out to about 504GB for my 500GB drive.
I am not sure what is going on but things seem to be working now. I really don't want any unexpected crashes or stoppages.
Ken
PS. Isn't it getting a bit late there?

---

### Post by Bashing-om on 2013-06-17
[COLOR=#000000]Kenc3;

Not much info in that last, "fdisk" provides a better "picture" I bet that the first sda1 partition is small and is a hold over from windows as the boot partition, that you had the disk set up then as GPT, and might even have been dynamic in the partitioning causing all the install problems.
ubuntu can deal with GPT partitioning,,, and if it works well, do not fix it.
[/COLOR][INDENT=2][COLOR=#000000]
if you are happy we are tickled

[/COLOR][/INDENT]

---

### Post by Kenc3 on 2013-06-17
One last question for tonight.
How do I put in my profile and photo?

---

### Post by Bashing-om on 2013-06-17
[COLOR=#000000]Kenc3; 
Are you in reference to this forum submitting the material ?
If so ...answer at least 25 questions on this forum...
That policy was instituted to keep the creepy crawlers ,ie web spiders, from flooding the forum.
Does not take long at all to acquire 25 points !

Policy: As the original topic of this thread has been successfully addressed, please mark this thread as solved, any new topic -> start another thread, that adds to your point value. One topic to each thread. You may have as many threads open at any time as you need.
We desire that this forum be frequented ... please take the time to read the introductory "stickies"... They will go a long way in greasing the skids in your introduction to ubuntu in general and this forum in particular. Explore the link in my sig for answers to almost any question you may have.

This aides others in seeking solutions and helps keep the forum tidy.
[/COLOR]Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.[INDENT=2][COLOR=#000000]
 Again, welcome to our world

[/COLOR][/INDENT]

---

### Post by Cheesemill on 2013-06-17
> **Kenc3 said:**
> One last question for tonight.
How do I put in my profile and photo?

Click on Settings at the top-right of any page.

---

### Post by Kenc3 on 2013-06-17
Thanks everyone!

---

