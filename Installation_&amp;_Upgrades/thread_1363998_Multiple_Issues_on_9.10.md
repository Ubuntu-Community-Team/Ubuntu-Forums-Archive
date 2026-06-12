---
title: "Multiple Issues on 9.10"
date: 2009-12-25
forum: Installation &amp; Upgrades
---

### Post by Coach_Mark on 2009-12-25
I have one laptop successfully converted to 9.04.  I am trying to convert two other laptops, one using 9.10, the other 9.10 Studio.  I am having several issues that I just can't seem to find the solution to...and it is the same issues on both 9.10 and Studio.

1.  When I go to change the menu and add "System Tools", I open it up, it gives me the list of all the different headers I can choose.  I check the box next to system tools, and two seconds later it becomes deselected.  

2.  I was fighting installing some software on 9.04, and a friend gave me the following instructions:

"Once you have the OS up and running, you have to enable the ability to log in to root and set the password for root. This is done by going to System>Administration>Users and Groups>Unlock>(your user password)>root>Properties>Set Password by Hand. After you've set your password, to save yourself from doing this later, go to System>Administration>Login Window>Security>Allow login by local system admin. This will enable you to log in as root, should you need to."

Everything works fine in 9.04.  In installed those programs, no problem.  But, in 9.10 and Studio, there is no such option in the Login Window (which I think is titled "Login Screen" in 9.10).  I got the other part--setting the password--done.  I even went through the list of permissions in the User screen and made sure everything was enabled (at least I think I did...everything should be checked...right?)  for myself and root (nothing was checked in root, by the way).  But, no matter what I do, it says I do not have permissions to do this when I run it from the desktop--which (again) I can do in 9.04.

3.  The external mice we use on our laptops do not work (and are getting no power) when plugged into either the Studio computer or the plain 9.10.  However, they work fine on the Windows computer and the 9.04 laptop, without installing a driver.  In fact, the mouse worked originally on the Studio, then stopped and began behaving as described.  After a re-install, same situation.  Is this related to the system adminstration...or something else?

4.  On both 9.10  system, nothing installable is recognized in the disc drive, but blank CDs are.

umm...short version...wth?  how do I solve all this?  I have a suspicion it all relates to the same thing, but...

---

### Post by oldfred on 2009-12-26
The minute you start doing things as administrator that you are not sure what you are doing will cause major problems. (been there and I do not recommend it)

Ubuntu uses sudo as one of its main design philosophies. Other linux have an administrator who knows what he is doing but only users are using the system. To allow users to temporarily do administrative tasks we preface the command with sudo or gksudo for graphical commands. All the help we give here as volunteers is based on that way of doing things. Somewhere in the forum was a discussion of this and they do not want anyone giving instructions on root logins as it is so dangerous for new users.

I think your friend gave you bad advice on setting up a root account because as you do things as an administrator that you should only do as a user you assign root as the owner and permissions and then cannot run it again as a user.  

Windows makes everyone and everything an administrator ( or did) and that is part of the reason windows is so insecure and has many issues.

If you install software thru synaptic or the software center you will have no problems installing it as you are temporarily running as the admin.

My portable has a USB wireless Logitech mouse. Windows never tells me anything about it but as soon as I installed Ubuntu it told me my battery level on my mouse. Not sure about your specific issue, but it seems strange that the mouse would stop working.

---

### Post by Coach_Mark on 2009-12-26
ok.  good to know...or rather remember since I think I already knew it (duh moment).  and that takes care of issues #2.  anyone with thoughts on the other three problems?...or #2, if you want to wade in...

---

### Post by tommcd on 2009-12-26
> **Coach_Mark said:**
> 
"Once you have the OS up and running, you have to enable the ability to log in to root and set the password for root. This is done by going to System>Administration>Users and Groups>Unlock>(your user password)>root>Properties>Set Password by Hand. After you've set your password, to save yourself from doing this later, go to System>Administration>Login Window>Security>Allow login by local system admin. This will enable you to log in as root, should you need to."
You should never run the system as root. You will have problems. This is very likely the cause of your problems. Other distros  have a root user, but you only become root in the terminal when you need to do something that requires root privileges. The rest of the time you run as a regular user. Ubuntu uses sudo to get root privileges instead of using a root account. 
> **Coach_Mark said:**
> 
  I even went through the list of permissions in the User screen and made sure everything was enabled (at least I think I did...everything should be checked...right?)  for myself and root (nothing was checked in root, by the way).  But, no matter what I do, it says I do not have permissions to do this when I run it from the desktop--which (again) I can do in 9.04.
What permissions did you change? And what did you change them to? This is very important. Changing permissions on things without a very good reason, and without knowing what you are doing, is a good way to break your system.
> **Coach_Mark said:**
> 
3.  The external mice we use on our laptops do not work (and are getting no power) ... Is this related to the system adminstration...or something else?
It could be if you are running as root, and if you changed permissions on system files. Boot the system with the mouse plugged in, login as a regular user, not as root, and open a terminal (applications > accessories > terminal) and run: **lsusb**. This means: list usb devices. It will tell us if the mouse is recognized. Post that here. Also post the output of **lspci**. This will list the hardware detected on your computer.

> **Coach_Mark said:**
> 
4.  On both 9.10  system, nothing installable is recognized in the disc drive, but blank CDs are.
.
What are you trying to install? Ubuntu has huge internet repositories for installing software. You need to do some reading here. This site is a very good place to start:
[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)
Specifically, for installing software:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
You should read that whole site though. I did.

---

### Post by Coach_Mark on 2009-12-26
I really appreciate all the feedback. I know how hard it is to figure this stuff out without being able to see it as it goes down. And I really appreciate all the links. I am still a noob at this, though I learn and catch on fast. so I will check those links as soon as I can.
 
I'm at work right now. so when I get home, I'll post back with the results of those terminal checks. In the meantime, I think I need to clear up something. I have not set up to run the system as root (at least i am pretty sure i haven't). I think that's what my friend was suggesting, but I couldn't figure it out...hence question 2. 
 
Now, to tommcd's points: 
 
The changed permissions--in Users and Groups, there is a permissions tab with lots of boxes in it. What I did was put check marks in all boxes. By the way, there were no boxes checked in Root.
 
Program Installation--in this case, it happens to be Windows XP to run in Virtual Box. I installed VB, and it starts just fine. But, when I put the XP disc in, VB said no bootable medium found. Further investigation revealed that when the XP disc is in the drive, it does not show up on any system screens--computer, files, no where. (additional example, on 9.04, it shows up on the desktop whenever something is in the drive, installable or not--but not on either 9.10 version). The computer gives no recognition to any disc placed in the CD drive that has programming on it. However, it does recognize and display the existence of blank CDs.
 
 
The mouse--I installed both versions with an external mouse plugged in at the time. When I first installed Studio, the mouse worked fine on that laptop. About two days later, it stopped. It wasn't even receiving power. I have made sure all the USB ports work by plugging in a "chill pad." However, no matter what USB I plug the mouse into on either of the 9.10 laptops, there is no power to the mouse. And, as I said originally, the same mouse work on both the 9.04 laptop and a Windows laptop--so the issue is not the mouse. Again, so far as I know, I am not running as root since I couldn't get that set up (and will undo it on 9.04 after the weekend...thanks for that).
 
I hope all this helps clear up the mud!

---

### Post by tommcd on 2009-12-26
> **Coach_Mark said:**
> 
The changed permissions--in Users and Groups, there is a permissions tab with lots of boxes in it. What I did was put check marks in all boxes. By the way, there were no boxes checked in Root.
So under: System > Administration > Users and Groups, then under: Properties > User Privileges, you enabled all the check boxes under your user name, and none of the boxes under root. Is that correct? If so, then that should be ok.
 > **Coach_Mark said:**
> 
Program Installation--in this case, it happens to be Windows XP to run in Virtual Box. I installed VB, and it starts just fine. But, when I put the XP disc in, VB said no bootable medium found... 
I have no experience with Virtual Box. Ubuntu should automount the Windows XP CD on the desktop though. With the XP CD in the drive, go to: Places > Home Folder. Then go to: File System in the left pane. Then open the media directory in the right pane where all the directories are. XP should be in one of the directories under media.
 Here is a guide to Virtual Box in Ubuntu that may help:
[http://howtoforge.com/installing-virtualbox-3.1-on-an-ubuntu-9.10-desktop](http://howtoforge.com/installing-virtualbox-3.1-on-an-ubuntu-9.10-desktop)
 > **Coach_Mark said:**
> 
The mouse--I installed both versions with an external mouse plugged in at the time. When I first installed Studio, the mouse worked fine on that laptop. About two days later, it stopped. It wasn't even receiving power. 
Is this on battery or AC power? Try the mouse on AC. Perhaps it is not getting enough power on battery. Also post the output of lsusb and lspci with the mouse plugged in. 
 What is the exact brand and model number of this laptop?

---

### Post by Coach_Mark on 2009-12-26
> **tommcd said:**
> With the XP CD in the drive, go to: Places > Home Folder. Then go to: File System in the left pane. Then open the media directory in the right pane where all the directories are. XP should be in one of the directories under media.therein lies the problem. when the CD is in the drive, the File system and media pane do not show there is a disc present. But, if I put a blank CD in, the disc is recognized. it's not just VB that doesn't see the disc.
 
(which is also how I realized there was a problem in the menu [see item 1 in original]. I am unable to add "System Tools" to the menu. If I select to add it, it deselects itself seconds later.)
 
 
> **tommcd said:**
> Is this on battery or AC power? Try the mouse on AC. Perhaps it is not getting enough power on battery.  Doesn't matter if it is on battery or AC. But, at the moment, the two laptops using 9.10 (one plain, one Studio) are running on AC, and the issue occurs on both of them.
 
I will post the model info for the two laptops, and the outputs as soon as I get home from work...about an hour or so.

---

### Post by tommcd on 2009-12-26
Here is another thing to try. Boot up the Ubuntu 9.10 live CD on the problematic laptop with the mouse plugged in and see if the mouse works from the live CD.
Also, when you first boot the 9.10 live CD first run the option to check the CD for defects. Then boot to the Ubuntu desktop (the option that says "use Ubuntu without making changes to your computer") and see if the mouse works from the live CD.

---

### Post by Coach_Mark on 2009-12-26
ok.  here are the outputs.  first computer is an HP dv6000 (actual model number is 6253cl), running 9.10 Studio.  it has a CD/DVD burner drive installed..

mbell82@coachmark:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

there are 3 USB ports.  at the time this was run, a chill pad was plugged into one of them and a working mouse in another.


mbell82@coachmark:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce Go 6150] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
07:05.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
07:05.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
07:05.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
07:05.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
07:05.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
mbell82@coachmark:~$ 


the second computer is an HP zx5000 (actual model is 5040), running plain 9.10.  I was wrong, by the way, the mouse works properly in this one...but it still has all the other problems involved in this thread.

bells4@bells4-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 09da:0006 A4 Tech Co., Ltd Optical Mouse WOP-35 / Trust 450L Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

(NOTE:  the mouse mentioned here is the same mouse that was installed on the dv6000.)

bells4@bells4-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 16)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Device 434c
00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] (rev 01)
02:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1620 PC Card Controller (rev 01)
02:04.2 System peripheral: Texas Instruments PCI1620 Firmware Loading Function (rev 01)
02:07.0 USB Controller: NEC Corporation USB (rev 43)
02:07.1 USB Controller: NEC Corporation USB (rev 43)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
bells4@bells4-laptop:~$ 

i'll let you know what the Live CD thing does in a bit.

---

### Post by Coach_Mark on 2009-12-26
one other thing...

the dv6000 is an AMD 64-bit processor, running 9.10 Studio.  and the zx5000 is a Pentium 4 32-bit processor, running plain 9.10 32-bit.  (We can make this easy and call the one running Studio "Number 1" and the plain 9.10 "Number 2")

---

### Post by oldfred on 2009-12-26
My desktop required me to change in BIOS - enable USB mouse/keyboard to get it to work. I do not know if your portable has the same settings in BIOS?

---

### Post by Coach_Mark on 2009-12-26
hmm...hadn't thought of that.  The laptop came with Windows Vista.  And, everything worked--but got bit by a bunch of viruses and finally made the plunge to Ubuntu.  Regardless, would overwriting that with Ubuntu change the BIOS setttings?

---

### Post by oldfred on 2009-12-26
Windows sometimes ignores the BIOS setting and works. Ubuntu sometimes used to, but they have updated things and now read the BIOS settings and assume that is what you want. My mouse worked in windows, not in old grub, but then in Ubuntu. This was on 9.04 I think, but definitely before Karmic. I had to keep switching from USB connector to my old keyboard and mouse ports until I found out what the problem was.

And it has not been just mouse & keyboard. Some other settings like on the hard drive have to be correct to allow one or the other system to work.

---

### Post by Coach_Mark on 2009-12-26
> **oldfred said:**
> My mouse worked in windows, not in old grub, but then in Ubuntu. This was on 9.04 I think, but definitely before Karmic. I had to keep switching from USB connector to my old keyboard and mouse ports until I found out what the problem was.that might explain why everything works in 9.04...but not in either 9.10 verisions...and why the disc drive might not be recognized i do not relish going through all the BIOS settings, though. blech! (note to self...run in Live CD to see what works...sorry...fell alseep before I could try that...)
 
ok. i'm still looking for thoughts on the menu issue, though. why would Ubuntu not let me add items to the displayed menu list?

---

### Post by Coach_Mark on 2009-12-27
I am not finding the settings I am looking for in BIOS.  Number 0ne (HP dv6000) is running PhoenixBIOS version F.40.  I can get into it, but I cannot get to a screen that lets me change any settings other than boot order.  Any idea where I would find those settings?  Also, the mouse is not enabled when using Live CD on that computer.  It also did not give me the option to use Live CD with Studio, but it did with plain 9.10.

---

### Post by tommcd on 2009-12-27
> **Coach_Mark said:**
> .. first computer is an HP dv6000 (actual model number is 6253cl), running 9.10 Studio.  it has a CD/DVD burner drive installed..
mbell82@coachmark:~$ lsusb
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

there are 3 USB ports.  at the time this was run, a chill pad was plugged into one of them and a **working mouse** in another.
Sorry I got back so late. I was at work all night...

So the mouse works then? Or is it that some mice work, and others do not?
Your output of lsusb does not actually show any usb devices. It just shows the usb hub. 
> **Coach_Mark said:**
> 
mbell82@coachmark:~$ lspci
...
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
...

Ubuntu does see you usb controller though. So the computer's hardware is recognized.
> **Coach_Mark said:**
> 
the second computer is an HP zx5000 (actual model is 5040), running plain 9.10.  I was wrong, by the way, the mouse works properly in this one...but it still has all the other problems involved in this thread.
 
So are the mice, or at least some mice, working on both machines then?
> **Coach_Mark said:**
> 
i'll let you know what the Live CD thing does in a bit.
I think it would be instructive to see what works from the live CD compared to your installed Ubuntu.

---

### Post by tommcd on 2009-12-27
> **Coach_Mark said:**
> 
ok. i'm still looking for thoughts on the menu issue, though. why would Ubuntu not let me add items to the displayed menu list?
I think the sort of problems you are experiencing are what you would expect if you enable the root account and start messing with permissions. From what you said you did, I don't think you changed anything important in your system file, but I can't be 100% sure. This is why I asked you to run the live CD and see if everything works. The live CD represents a pristine, unadulterated Ubuntu.
Also run the option to check the CD for defects. If your CD was bad when you installed it could cause any number of problems if it did manage to actually install, which yours did.

---

### Post by Coach_Mark on 2009-12-27
> **tommcd said:**
> I think the sort of problems you are experiencing are what you would expect if you enable the root account and start messing with permissions...Also run the option to check the CD for defects. If your CD was bad when you installed it could cause any number of problems if it did manage to actually install, which yours did.hmm...I hadn't thought I changed anything yet...other than checking all the permissions for my user name in the User Privilidges (which you said was ok). I know I wanted to go beyond that, based on what my friend had suggested. but, when I went to do it nothing matched up with what he was telling me to do and I did not continue. but...ok. it's at least a starting point, I'll try a reinstall tomorrow and let you know what the results are. oh, and I did run the check for defects before installing. (A habit from a series of bad ISO burns installing 9.04 on another computer.)
 
meanwhile...any thoughts on the BIOS suggestion and findings?
 
EDIT: sorry...missed your question about the mouse. NO. the mouse does not work on the dv6000. i was simply stating that I knew this was a working mouse that i was trying to use. sorry for the confusion on that. the same mouse does work when plugged into the zx5000, so the mouse issue no longer applies to that computer.  and, regarding Live CD:
> **Coach_Mark said:**
>  Also, the mouse is not enabled when using Live CD on that computer. It also did not give me the option to use Live CD with Studio, but it did with plain 9.10.i hope this edit helps make some sense of all this.

---

### Post by tommcd on 2009-12-28
> **Coach_Mark said:**
> hmm...I hadn't thought I changed anything yet...other than checking all the permissions for my user name in the User Privilidges (which you said was ok).
It does not sound like you changed anything critical based on what you have told me. However, since this is a new install, and since I am running out of ideas, it would be instructive for troubleshooting purposes to see if the mouse and the Windows XP disc are recognized on a fresh install. This is why I wanted you to try the mouse from the live CD.
So do a fresh install of 9.10 on the problematic computer(s). Install Ubuntu with the mouse connected. See if it works from a fresh install. Then get all the updates for 9.10 and see if it works after the updates.
> **Coach_Mark said:**
> 
meanwhile...any thoughts on the BIOS suggestion and findings?
 
Well, if you have different options for usb ports in the BIOS you could try them and see if any work. In post #15 in this thread you said there were not any options for usb in the BIOS beyond setting the boot order. I have the same thing in my Acer laptop. So your options may be limited here.
What brand of mouse is this anyway? Is it a simple 2 button plus a scroll wheel mouse? Or is it a fancy high end mouse with lots of buttons and stuff?  It has been a long time since I have seen a thread around here where Ubuntu could not recognize a simple 3 button mouse.

---

### Post by Coach_Mark on 2009-12-28
all right.  complete reinstall has been done on the HP dv6000 with Studio.  All issues are still present.  Nothing has been altered.

1.  cannot add System Tools to the menu.
2.  Mouse does not function.
3.  CD/DVD drive only recognizes blank discs


this leaves me wondering about the BIOS suggestion made earlier--Windows will work with incorrect BIOS settings but Ubuntu will not.  it was suggested I might have to make some changes.  but, in this particular version of Phoenix BIOS, I can only change the Boot order.  I cannot see any system configurations other than the boot order.  How would I check to see what those configurations are or change them?

---

### Post by Coach_Mark on 2009-12-28
Live CD and reinstall on zx5000 now complete. 

1.  cannot add "System Tools" to menu in Live CD or reinstalled version.
2.  mouse functions in both--so the mouse is a non-issue on this computer, now.
3.  (after reinstall) computer recognized Windows XP disc when inserted, but when removed still showed it as being in the drive.  and, after putting 9.10 disc back in drive, screen still showed XP disc, did not show 9.10 disc.  however, "Places" showed both as being present.

also, BIOS screen has the same issues.  it only allows resetting the boot order, though it is a different version of Phoenix BIOS.

---

### Post by tommcd on 2009-12-29
> **Coach_Mark said:**
> 
this leaves me wondering about the BIOS suggestion made earlier--Windows will work with incorrect BIOS settings but Ubuntu will not.  it was suggested I might have to make some changes.  but, in this particular version of Phoenix BIOS, I can only change the Boot order.  I cannot see any system configurations other than the boot order.  How would I check to see what those configurations are or change them?
If your BIOS does not include those options you can't change them. The BIOS in my Acer laptop is equally limited. There is nothing you can do about this. You can't do things that are not supported in your BIOS.

---

### Post by tommcd on 2009-12-29
> **Coach_Mark said:**
> 
1.  cannot add "System Tools" to menu in Live CD or reinstalled version.
Is this Ubuntu Studio? Or plain Ubuntu 9.10 you are using here?

Anyway, try this to get System Tools in your menu:
First install **gkrellm** using apt-get or synaptic. This is a lightweight GUI system monitor that I use all the time:
[http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html](http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html)
After you install gkrellm, it will be located under: Applications > System Tools on the top panel. This should give you the System Tools menu.
 Then right-click on the Applications menu on the top panel, then choose "edit menus". Then select "System Tools" in the left pane. This will show the items under System Tools in the right pane. You can then check the items you want to see under the System Tools menu, and they should then be added to the menu. This should be the same In Ubuntu and Ubuntu Studio.
> **Coach_Mark said:**
> 
2.  mouse functions in both--so the mouse is a non-issue on this computer, now.
Excellent! At least one problem is fixed. So there may have been something screwed up on your first install that could have been corrected with the fresh install.
> **Coach_Mark said:**
> 
3.  (after reinstall) computer recognized Windows XP disc when inserted, but when removed still showed it as being in the drive.  and, after putting 9.10 disc back in drive, screen still showed XP disc, did not show 9.10 disc.  however, "Places" showed both as being present.

When you put the XP disc in it should automount and open up the contents of the CD in a nautilus file manager window. If you remove the CD, but keep the file manager open, it will continue to show the contents of the XP CD until you close that window, or navigate away from it. Is this how it is working?
I'm not sure why the Places menu would continue to show both discs present.

As for the BIOS, you could check the manufacturer's website for a BIOS update. Sometimes an updated BIOS will provide newer features.

I have not been able to find anything useful for the HP dv6000 mouse issue. You said you reinstalled Ubuntu Studio on the dv6000. Have you tried a fresh install of Ubuntu 9.10 on the dv6000? I don't know if this will make a difference; but at this point I really don't know what else you could try here.

---

### Post by Coach_Mark on 2009-12-31
OK.  My Noob status is officially validated.  I forgot make sure there was an item in the "System Tools" section so it could be added to the menu.  (head-desk)  So, that issue is solved on both computers.

Yes.  What you described about the desktop display for the XP disc seems right.  I right clicked, and the menu had the option "unmount." when I click "unmount", and the disc has been removed, the item disappears from both locations. However, the file manager window was not open during all this.  Could this be a bug of some sort needing reporting elsewhere?

The good news is...the disc drive on the zx5000, running plain 9.10, now seem to work with programmed discs.  I am at this moment installing XP in Virtual Box!!

SO...it appears the only remaining problems are on the dv6000, running Studio.

having said that, I have a new twist on the Studio installation.  I experimented with a disc containing only pictures.  I know the disc is good.  I loaded everything on it to a system using 9.04 and the zx5000 running plain 9.10. But, when I put it into the dv6000 running Studio, I got the following error message: 

"Error mounting:  mount exited with exit code 1: helper failed with:
mount: block device /dev/sr0 is write protected, mounting read only
mount: wrong fs type, bad option, bad superblock on /dev/sr0, missing codepage or helper program, or other error
In some cases useful info is fond in syslog - try dmesg |tail or so"


And, to confirm, The mouse is still not functioning in the dv6000.  I did find a BIOS update that may not have been done on the dx6000.  But, all i find are instructions for flashing BIOS using DOS/Windows.  How do you do that in Ubuntu?

Oh, yeah.  There is one other, as yet unvisited, subject.  There is also a built in web cam and mic on the dv6000 unit.  anyone know where i can find some instructions for installing those so i can use them?

---

### Post by tommcd on 2009-12-31
> **Coach_Mark said:**
> 
Yes.  What you described about the desktop display for the XP disc seems right.  I right clicked, and the menu had the option "unmount." when I click "unmount", and the disc has been removed, the item disappears from both locations. However, the file manager window was not open during all this.  Could this be a bug of some sort needing reporting elsewhere? 
I don't think it is a bug. I think you are seeing the normal behavior. If you can mount, view, and copy items from the disc it sounds like it is behaving ok.
> **Coach_Mark said:**
> 
having said that, I have a new twist on the Studio installation.  I experimented with a disc containing only pictures.  I know the disc is good.  I loaded everything on it to a system using 9.04 and the zx5000 running plain 9.10. But, when I put it into the dv6000 running Studio, I got the following error message: 
"Error mounting: mount exited with exit code 1: helper failed with:
mount: block device /dev/sr0 is write protected, mounting read only ...

Does the CD icon show up on the desktop? If you look in under /media or /mount can you find the disc mounted there along with it's contents?
Also, post the output of:
```
cat /etc/fstab
```

> **Coach_Mark said:**
> 
And, to confirm, The mouse is still not functioning in the dv6000.  I did find a BIOS update that may not have been done on the dx6000.  But, all i find are instructions for flashing BIOS using DOS/Windows.  How do you do that in Ubuntu?
You can use Free DOS. Here are some tutorials on it:
[http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html](http://www.linuxinsight.com/how-to-flash-motherboard-bios-from-linux-no-dos-windows-no-floppy-drive.html)
[http://www.cyberciti.biz/tips/howto-flash-your-system-bios-under-linux.html](http://www.cyberciti.biz/tips/howto-flash-your-system-bios-under-linux.html)
[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)
If you have a Windows computer, you can make a bootable CD with the BIOS file and the flash utility as per the manufacturer's instructions and boot from that to flash the BIOS if you want to. 
Be careful with this. Does the new BIOS have any bug fixes or new features that you may need or want? If not, there is really no point in flashing the BIOS. 
I have no experience using webcams. None of my computers have one.

---

### Post by Coach_Mark on 2010-02-19
a quick update.  i delivered the offending HP laptop to a friend/mentor to handle as a project.  he made a couple of discoveries:

1.  there seem to be hardware issues on the hp dv6000, and a possible BIOS issue.
2.  i had installed (semi-successfully) 9.10 studio 64-bit.  the computer was billed as having an AMD64 and associated structure.  but, it turns out the architecture is i686.

so...there are issues not solved, yet.  but the ubuntu side seems to be on the back burner for a bit.  i will update when i know more.

thanks, by the way, for all the help.

---

