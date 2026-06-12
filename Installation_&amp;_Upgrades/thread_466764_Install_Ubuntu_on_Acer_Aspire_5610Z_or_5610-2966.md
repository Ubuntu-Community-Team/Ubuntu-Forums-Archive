---
title: "Install Ubuntu on Acer Aspire 5610Z or 5610-2966"
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by Sabot on 2007-06-07
I just received my new Acer 5610Z/5610-2966 and I thought I would share my Ubuntu install experience.  This Acer is a great little laptop by the way.

This laptop comes with Vista Home installed, so the first step is to backup Vista.  Just in case I want to sell it to someone that wants Vista installed on it in the future.

How to back up Vista:

1. Boot up your computer and open Acer eRecovery.
2. Pop in a DVD-R or DVD+R disk.
3. Click on Burn Disk at the bottom of eRecovery.
4. Click on Factory Restore Option at the top.
5. It will burn your DVD.

The Aspire comes with a Vista Upgrade Anywhere disk. You will need this disk when you want to restore Vista. If you ever need to restore, it is a simple but time consuming process.  You will need to use the Vista Upgrade Anywhere disk to install Vista. This will format your disk and remove the Grub boot loader.  Then you can boot off of the Factory Restore DVD you made and restore Vista with all the Acer extras and drivers.

Now the fun part.

Install Ubuntu:

1. Press F2 on Boot to access the Bios settings.
2. Set the DVD as the first boot device and save the Bios changes.
3. Pop in your Ubuntu install disk (You Should Use 7.04, but I used 6.10)
4. Erase entire drive and install (note my drive was partitioned into three partions for Vista. Partition 1 was a Vista Restore partition.  You gain almost 9 Gig of HD space by using Ubuntu instead of Vista.  Sweet!)

What does not work?
1. Special Laptop Buttons that line the right and top of keyboard.  They are shortcuts to access the Windows Media Player and IE,Email,Word processor.
2. Built in Media Card Reader.(Works Great in Ubuntu 7.10)
3. I was not able to test the modem, so I don't know if that works.
4. Wireless does not work out of the box because Acer uses a Broadcom Airforce One Card. Broadcom does not offer native Linux Drivers. Let me give you the fix for that.

How to get wireless working:

(These instructions only work if your 5610Z came with the BCM4318 [AirForce One 54g] Wlan card)
(You will need to be connected to the internet by a wired connection)
1. Install using Synaptic ndiswrapper-utils-1.8 and wifi-radar.
2. Download and expand the 32bit driver I have attached to this post. If you need the 64bit driver you can check the Ubuntu forums and you will find one. (You may need to be signed into the Ubuntu forums to download my attached file.)
3. Open a terminal window and navigate to driver folder and  type:  
```
sudo ndiswrapper -i bcmwl5.inf
```
4. ```
sudo modprobe ndiswrapper
```
5. ```
sudo gedit /etc/modprobe.d/blacklist
```
6. Blacklist the old broadcom driver by typing in the following at the bottom of the text file: ```
blacklist bcm43xx
```
7. Save Text File.
8. To Make your wireless start up with each boot you will need to add ndiswrapper to the modules that start at boot time: 
```
sudo gedit /etc/modules
```
9. At the bottom of the text file type:
```
ndiswrapper
```
10. Save Text File
11. Restart you laptop
12. Use wifi-radar to locate and connect to your wireless router.  wifi-radar is found under Applications>Internet in the upper left hand corner of your Ubuntu Desktop.

Ubuntu works great on this Laptop.  It uses both processors and seems very smooth and stable.
If anyone has any additional notes please add them below.

---

### Post by abenti on 2007-06-18
Took 5 minutes to install the wireless driver on my new Acer 5610z and Feisty Fawn. No need for Wi-Fi Radar, it worked perfectly with the default network manager. Thank you!

---

### Post by Deadburn on 2007-06-22
i need to try this!!!

---

### Post by NintenDave on 2007-07-02
Worked wonderfully, thankyou very much. Wireless worked straight away with Feisty.

---

### Post by kiboke on 2007-07-11
I have Acer Aspire 5610z and just did everything you wrote about wireless. Doesn't work. After reboot, wi-fi doesn't show anything on it's list. I tried wlassistant also, it sais there are no usable networks (or something like that).

I have kubuntu 7.04. Please help, this is not the first time I failed to get it to work.

---

### Post by phorum.ws on 2007-07-12
Hi All, okay I have an Acer TravelMate 4230 Series (but has the same setup as you are using with bios etc etc)/// okay I have 160gb, and this was already partitioned into 2 x 80gb - 1. has the vista installed with all programs, and the other is named DATA with nothing in it, so i turned this DATA 80bg partition into 2 equal partitions by using the Vista Shrink Method.

okay when i try and install Ubuntu using a 'manual' configuration when it asks what partition i wish to install in, i can only use a /root partition, meaning that Ubuntu is making the partitions all the same at 160gb max, and basically combining them all, even though they show up seperate.

so if i was to install in the main partition of 160gb (it says 85% free) and recommends using this free space for Ubuntu (or i can manually use the slider to make it like 20% if a like).... the concern with this is not losing my DATA partiton of 40gb and my DATA2 of 40gb, but i am scared the pain ACER partition that has VISTA and all my software and files on it will be erased if i select the /root.

will it erase everything?

how do i get around this? i do not have a vista CD so i cannot back everything up, and reinstall it once Ubuntu is on so this is not an option. 

there has to be a way around it, as the instructions i read said i could manually create a partition (which i did DATA2 - which was to hold Ubuntu), and Vista would be fine left on there in ACER (partition #1).

any ideas.

thanks heaps.

---

### Post by dca on 2007-07-13
Indeed, I have a 5610z, also.  The Orbicam doesn't work (no surprise), the special DVD buttons, and the media card reader do not work.  Surprisingly, the wireless works fine if you have the laptop w/ the Atheros wifi card...

---

### Post by Sabot on 2007-07-15
> **kiboke said:**
> I have Acer Aspire 5610z and just did everything you wrote about wireless. Doesn't work. After reboot, wi-fi doesn't show anything on it's list. I tried wlassistant also, it sais there are no usable networks (or something like that).

I have kubuntu 7.04. Please help, this is not the first time I failed to get it to work.

Mine did not show anything on the list unless I used wifi-radar.  Try that and let me know.  Also, make sure that your wireless card is BCM4318 [AirForce One 54g] 802.11g.

---

### Post by Sabot on 2007-07-15
> **phorum.ws said:**
> Hi All, okay I have an Acer TravelMate 4230 Series (but has the same setup as you are using with bios etc etc)/// okay I have 160gb, and this was already partitioned into 2 x 80gb - 1. has the vista installed with all programs, and the other is named DATA with nothing in it, so i turned this DATA 80bg partition into 2 equal partitions by using the Vista Shrink Method.

okay when i try and install Ubuntu using a 'manual' configuration when it asks what partition i wish to install in, i can only use a /root partition, meaning that Ubuntu is making the partitions all the same at 160gb max, and basically combining them all, even though they show up seperate.

so if i was to install in the main partition of 160gb (it says 85% free) and recommends using this free space for Ubuntu (or i can manually use the slider to make it like 20% if a like).... the concern with this is not losing my DATA partiton of 40gb and my DATA2 of 40gb, but i am scared the pain ACER partition that has VISTA and all my software and files on it will be erased if i select the /root.

will it erase everything?

how do i get around this? i do not have a vista CD so i cannot back everything up, and reinstall it once Ubuntu is on so this is not an option. 

there has to be a way around it, as the instructions i read said i could manually create a partition (which i did DATA2 - which was to hold Ubuntu), and Vista would be fine left on there in ACER (partition #1).

any ideas.

thanks heaps.

If you do not have a backup, I would not continue to try and install Ubuntu.  It is possible that you may mess up your partitions so that Vista will not work. If you wish to risk it anyway, Here is a link to some instructions that will allow you to shrink your Vista Partitions:

[http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/]("http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/")

It will allow you to shrink your partitions without data loss.  Then the Ubuntu install disk can use the unused space to install GNU/Linux on your computer.

---

### Post by dougsmith on 2007-07-27
i had a different driver in this exact model (Aspire 5610Z). mine has the Atheros AR5007EG. just had to dl the driver and blacklist 'ath_pci'. now on to the webcam.... :)

---

### Post by hmmmsomething on 2007-08-05
ok so i have an Acer Aspire 5610Z but it has a  Broadcom Corporation BCM4401-B0 100Base-TX (rev 02) 

wireless card... i was trying the tutorial, but being the newbie that i am i couldn't understand what to do in step 3.. i can open the terminal, but dont' know what it means by navigating to teh driver and inputting

---

### Post by Sabot on 2007-08-06
When you downloaded the driver from my post it saved it to your desktop.  You can then extract the file by right clicking the file on your desktop and  then select Extract Here.  This will create a folder called Broadcom Driver 32bit.tar.gz_FILES on your desktop.

To navigate to this folder in the terminal you can type:

> cd Desktop

Press Enter.

Then you can type:
> cd Broadcom Driver 32bit.tar.gz_FILES

Press Enter.

This will get you to the Driver directory.

---

### Post by hmmmsomething on 2007-08-06
alright so i manage to get through the process shown... but then i restarted and wifi radar showed nothing... i tried adding my network but that plan wasn't too succesful...

---

### Post by andrewperon on 2007-08-15
thanks for all the help !

---

### Post by dahli.llama on 2007-08-27
I just bought the Acer 5610z laptop yesterday and installing Ubuntu was a breeze.  The laptop came with two partitions already on the drive, so I just too the second, empty one and dropped Ubuntu 7.04 on without any troubles.

Wireless didn't work right away, but after reading this thread: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) I was able to get things working using the suggested ndiswrapper route.  It worked perfectly.

Also, installing the new Intel graphics drivers instantly let me run in the native 1280x800 mode.

Now I have a wonderful laptop running Beryl and I am very happy.  I just need to figure out how to get the webcam and the media card reader working and I'll be able to convince my wife to drop Windows completely on the laptop :D

---

### Post by Sabot on 2007-08-27
How did you install the new intel graphics drivers?

---

### Post by organic_matter on 2007-10-15
okay so i have a aspire 5610z 5610-[COLOR="Red"]2089[/COLOR]    	:shock:	:shock:	:shock:	:shock:	:shock:	:shock:	:shock:	:shock:	:

it has a athos card and i cant get it to work any thoughts?/


.:edit:.

7.04 fiesty fawn

---

### Post by kaffelars on 2007-10-19
I have an Aspire 5720Z running Gutsy and I had to use Ndiswrapper with a Windows driver to get wireless running.
Wrote a quick howto [here]("http://ubuntuforums.org/showthread.php?t=554531").
Good luck :)

---

### Post by tzykid on 2007-10-22
I have the Aspire 5610z with the BCM94311MCG wlan adaper. I did all the steps as shown and after I restart it no longer shows I have wireless where before it was showing I had the adapter. I do not kow much about linux so I might have over looked something. but as it stands it seems as though after I restart it doesn't even recognize the driver. If I unblacklist the original driver it shows back up in the network connections. thanks in advance for the help.

---

### Post by Sabot on 2007-10-24
These instructions are only for the BCM4318 [AirForce One 54g] wlan card.

---

### Post by crispben on 2007-11-07
OK, I have an Acer Aspire 5610Z and I had Feisty Fawn on it, but I recently upgraded to Gutsy Gibbon, it now takes a long time to find the wireless connection (with ndiswrapper), it used to be very quick with 7.04 but since I upgraded (7.10) it has a few problems like that.  Anyone else with this problem?

---

### Post by Sabot on 2007-11-07
Yes I had the same problem.  What you want to do is go into the network control panel under system>administration.  There you want to turn off the roaming for the wireless network.  Then you can select the wireless router you use and it should be fast again.  It seems that roaming is a problem.  I also use wifi radar to select the wireless routers when I am on the road, and it seems to work better than roaming.

---

### Post by crispben on 2007-12-29
> **Sabot said:**
> Yes I had the same problem.  What you want to do is go into the network control panel under system>administration.  There you want to turn off the roaming for the wireless network.  Then you can select the wireless router you use and it should be fast again.  It seems that roaming is a problem.  I also use wifi radar to select the wireless routers when I am on the road, and it seems to work better than roaming.

Thank for helping, although, it seems that that fix only works sometimes.  And in order for it to work again, it seems like I have to switch to Static IP then back to automatic DHCP and wait for it to refresh in order for it to work?  Maybe there is something additional I need to be doing, but sure seemed like NDISwrapper worked better.

---

### Post by Sabot on 2007-12-29
My instructions at the start of this thred use NDISwrapper.  Please use them for proper internet service.  If you use the automatic intall of the driver in 7.10, you will have service problems.

---

### Post by crispben on 2008-01-13
> **Sabot said:**
> My instructions at the start of this thred use NDISwrapper.  Please use them for proper internet service.  If you use the automatic intall of the driver in 7.10, you will have service problems.

Well, I have been tinkering on and off with ubuntu and the way I think I like it for awhile.  I ended up re-installing Ubuntu twice because it was connecting to the internet for updates (yet, i could still browse), that would make a whole bunch of problems arise.  So I have finally got a clean install of 7.10 and everything seems to work wonderfully.  The NDISwrapper connects almost instantly, I don't have to turn roaming on and I haven't even had to use wi-fi radar yet. 

I do however get the 

"[ 13.824086] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[ 13.824201] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0" 

error, but I have no idea what that affects, it doesn't seem to affect anything in my case.  It seems to be a common error for Acer's, does yours have a similar error Sabot? 

I also decided to put Vista :( back on as a dual boot because there are a few programs that I work with that do not work properly in WINE.  And now I have a sleep/standby problem every once in awhile.  My Vista will not sleep at all it just freezes the computer (but that is how it has always been), but now that I have a Vista partition I'm afraid that it may have done something with Ubuntu also (considering I've never had this problem before with 7.04-7.10).  I don't know though, I'm still very new at Ununtu.

---

### Post by misty soul on 2008-01-27
> **crispben said:**
> "[ 13.824086] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[ 13.824201] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0" .

I do also have these errors here. I think they are related to the card reader which is not supported. This is harmless.

---

### Post by anarkae on 2008-02-20
> **dougsmith said:**
> i had a different driver in this exact model (Aspire 5610Z). mine has the Atheros AR5007EG. just had to dl the driver and blacklist 'ath_pci'. now on to the webcam.... :)

I have this model (Atheros AR5007EG in my acer aspire 5610z) also 
and I don't know how to install the driver.
You could do this?

---

### Post by crispben on 2008-03-02
> **misty soul said:**
> I do also have these errors here. I think they are related to the card reader which is not supported. This is harmless.

My card readers work?

---

### Post by dlevans on 2008-03-27
I have an Acer 5610Z it had Vista on it, I put Ubuntu on it awhile ago then went to XP and now I have Kubuntu 7.10 but the Fn+Arrow Up/Arrow Down doesn't do the volume, the card reader doesn't work, and the wi-fi doesn't work I'm downloading 7.04 now because I heard the volume controls work and I'm hoping the card reader works with the 7.04
so my questions are:
what version are you using (7.04 or 7.10)?
will this work in Kubuntu as well as Ubuntu?
has anyone gotten the card reader to work or the Acer Oribi-Cam to work?
Thanks for your help and if you need anything (error logs etc.) my email address is [email]evansdustin@hotmail.com[/email] Thanks for your help :)

---

### Post by Sabot on 2008-03-27
The card reader starts working in 7.10.  I have tested SD and MMC cards.  The volume control works in 7.10 also.  If your 5610Z has a broadcom wireless card, the first post of this thread has instuctions on how to get that to work. The extra buttons around the keyboard do not work in any version.

---

### Post by dlevans on 2008-03-27
7.10 Ubuntu or Kubuntu sorry I know this is an Ubuntu forum but i didn't thing the KDE made that much of a difference does it? I thought it made things look different. I have 7.10 and the volume does not work and the card reader does not work. I'm downloading 7.04 and going to see if I upgrade to 7.10 if it will fix the problem and I'm thinking about re-installing Ubuntu 7.10 if it fixes my problems

---

### Post by Pumalite on 2008-03-27
[http://ubuntuforums.org/showthread.php?t=595979](http://ubuntuforums.org/showthread.php?t=595979)

---

### Post by dlevans on 2008-03-27
ok so I re-installed Ubuntu 7.10 and the card reader works but the thing is I like the way Kubuntu looks better so I'm installing the kubuntu-desktop from synaptic and the 243 updates as we speak. As soon as I loaded Ubuntu the card reader started working! I haven't had time to try the webcam but I don't thing its going to work :( once I get the updates and kubuntu-desktop installed I'll see if the card reader still works and try installing the wireless card like you talked about hopefully this "work-around" will be the best bet for me.

---

### Post by dlevans on 2008-03-28
IT WORKED!!!! Installing Ubuntu first, then Kubuntu makes my wireless card work, and the card reader work. Plus I get to use the KDE (which is my personal choice) and everything works!! I'm so happy it works now  :) oh by the way I have an Acer Aspire 5610Z Laptop.

---

### Post by dlevans on 2008-03-28
last thing on the acer that doesn't work... the volume goes between 0% and 11% anyone fixed this yet?

---

### Post by dlevans on 2008-03-29
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/kdeutils/+bug/118723](https://bugs.launchpad.net/ubuntu/+source/kdeutils/+bug/118723) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				i got the volume bar "fixed" it no longer goes between 0% and 11% it goes from 0% to 100% but the actual volume does nothing. watching youtube videos the volume can only be changed by the flash player thing itself not even clicking/dragging the Kmixer is there another volume controller program other than Kmix? has anyone gotten the volume to work i "fixed" it using this bug link and someone's patched .deb file that they said worked 
[https://bugs.launchpad.net/ubuntu/+source/kdeutils/+bug/118723](https://bugs.launchpad.net/ubuntu/+source/kdeutils/+bug/118723) if anyone has any help in getting the volume on an Acer 5610Z to work please let me know

---

### Post by dlevans on 2008-03-30
okay... I have no idea what happened but all of a sudden my card reader does not work did I unmount it somehow? 
lspci gives this :
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Generic system peripheral [0805]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
anyone got any advise?

---

### Post by yno037 on 2008-04-24
I've been working on fixing the fact I don't have wireless on my Aspire 5610Z with Broadcom .... after a long time with no success, ubuntu recognized it needed some driver for it to work. followed the instructions and now it's working fine. Even though I am glad it is working, I wish I would have found out it would eventually know to fix itself. I don't what finally triggered ubuntu (it was probably my 5th time restarting the laptop very frustrated). what I am trying to say, is you don't need to spend time installing ndiswrapper, or wifi-radar... it will eventually know to fix itself. Or better yet, how the heck you trigger the Driver check so that people will have less truble???

---

### Post by xaco1234 on 2008-04-27
anyone managed to get the webcam working??
or do it work in 8.04?? i still use 7.10. planing on updateing when i got time next summer.

---

### Post by olivertreend on 2008-05-17
I've had the Obricam working before... Skype seems to recognise it straight out the box, as it were.
:)

Shame about the media/shortcut buttons down the side and top, though.


EDIT: I forgot to mention, I'm using Linux Mint rather than Ubuntu, but it's built upon Gutsy so it *should* be the same.

---

### Post by xaco1234 on 2008-06-06
orbi cam does work out of the box in 8.04 atleast on my acer

---

### Post by snailmail on 2008-07-07
anyone get the media buttos working?

---

