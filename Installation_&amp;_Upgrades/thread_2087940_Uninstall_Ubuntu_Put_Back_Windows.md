---
title: "Uninstall Ubuntu Put Back Windows"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by Gronknation on 2012-11-25
A tale told by an idiot.

It was 6 o'clock in the mourning I haven't gone to bed all night. I was looking at random programs on the internet. And I installed Ubuntu on my Windows Vista Toshiba Labtop. Computer screen went black nothing was working so I held the power button down. Now computer won't boot.

I have spent 24 hours doing everything you could think of to re-boot my computer. Everything. Nothing would work. Nothing.

I kept thinking "I must of fried my hard drive by holding the power button down to turn it off I know your not supposed to do that". Just recently I had realized that I download Ubuntu. I'm pretty sure this is the problem why my computer won't boot what so ever.

2 Notes of Genius:
1. I'm almost positive my computer isn't even compatible with Ubuntu
2. I did not back up any of my precious precious pictures,documents,programs.

I want to uninstall Ubuntu while putting windows back. And I don't want to lose any of my stuff. Please help.

---

### Post by Bucky Ball on 2012-11-25
Hard to tell what you have installed and how from your description. Did you install Wubi which installs inside Windows or accidentally installed Ubuntu over Windows while trying to dual-boot? More info please ...

Your computer is totally incompatible with Ubuntu??? Highly unlikely. 

Boot from the install CD (the LiveCD) and 'Try Ubuntu'. You will get to the desktop. Once there, find Gparted in System>Administration. It may be called Partition Manager.

Take a screenshot of that and post it so we get a better idea of what you have done and what you have got. 

Your dual-boot, if that's what you were attempting, may be fine but the boot manager is stuffed. You could try using Boot Repair for this. You can install while booted from the LiveCD and run that, see if it fixes. It can also create a file telling us your boot info. If Boot Repair fails, create that file and post link.

[https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu](https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu)

When your booted into Ubuntu from the CD you should also be able to see your files on the Windows partition and copy them to another device. 

Good luck. I wouldn't panic at this point. Maybe simple but we'll know more when you post more info.

---

### Post by Gronknation on 2012-11-25
I'm a computer n00b so I hope I make sense.

I really do have the worst short time memory out of all the people in the history of the world. Well maybe not that bad, but it's bad. I can't remember exactly where I downloaded unbuntu. But I do remember downloading it on my computer. It was not on a CD or USB drive. 

I BELIEVE I downloaded the 12.0 from here [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

I have no way of getting to the desktop. I just get a blue screen for a few seconds - then the computer quickly re-starting. (I have tried everything from advanced boot options and system recovery options) The reason I think this is because of ubuntu is because I used a program called wondershare live boot to get my computer back. It doesn't work because I keep getting messages like 

"Can not find Windows on your computer!"

and

"Can not find any Windows on your hard disk"

Problems happened also after downloading Ubuntu.

---

### Post by carl4926 on 2012-11-25
But can you tell us if you burned Ubuntu to a CD and booted from the CD?
You'd surely remember that?

Or do you remember running an installer from the windows desktop?

---

### Post by Gronknation on 2012-11-25
Definitely an installer from the windows desktop. 

Sorry if I didn't make that clearer in my last post.

---

### Post by zombifier25 on 2012-11-25
If so, then you're using a Wubi installation, which creates a virtual drive on Windows to install Ubuntu from. A Wubi installation does NOT tamper with Windows' partition in anyway, and you can always uninstall it from Windows's Add or Remove Programs.

Here's the problem: **If you can't boot into Windows, then you can't boot into Wubi Ubuntu too.** So just a guess, but I think it's your Windows installation that's having problems.

---

### Post by carl4926 on 2012-11-25
It sounds like you ran the 'wubi'
This installs Ubuntu inside windows. I have never used it myself.
Wait for someone else to answer who has a understanding of it.

The more you fiddle with it, the more damage you could do. But I'm pretty sure your windows data will be intact.

---

### Post by Gronknation on 2012-11-25
> **zombifier25 said:**
> If so, then you're using a Wubi installation, which creates a virtual drive on Windows to install Ubuntu from. A Wubi installation does NOT tamper with Windows' partition in anyway, and you can always uninstall it from Windows's Add or Remove Programs.

Here's the problem: **If you can't boot into Windows, then you can't boot into Wubi Ubuntu too.** So just a guess, but I think it's your Windows installation that's having problems.
Really? That's what I was afraid of. I thought it was the Ubuntu just  because I found it weird that my computer couldn't find windows right  after I downloaded ubuntu.

> 

It sounds like you ran the 'wubi'
This installs Ubuntu inside windows. I have never used it myself.
Wait for someone else to answer who has a understanding of it.

The more you fiddle with it, the more damage you could do. But I'm pretty sure your windows data will be intact.Ok I will thankyou. I decided to stop fiddling with it after I posted this topic. Didn't want to do more damage.

---

### Post by carl4926 on 2012-11-25
>  So just a guess, but I think it's your Windows installation that's having problems.Looks like it.

That could be due to:
> Computer screen went black nothing was working so I held the power button down.


Next question: Do you have a Vista DVD? I mean a proper one, not some recovery thing

---

### Post by Gronknation on 2012-11-25
> **carl4926 said:**
> Looks like it.

That could be due to:



Next question: Do you have a Vista DVD? I mean a proper one, not some sh1ty recovery thing

I originally thought it was because I held the power botton. Just after I remembered downloading ubuntu. I was hoping it was ubuntu. 

I only held down the power botton once to turn my computer off. I know people who do it frequently and nothing happens to them. 

I have 2 basic Windows Vista disks I used to install Vista. Nothing else.


I had this happen to me before and I bought a SATA data connector 

[http://www.outletpc.com/xx8455.html?utm_source=xx8455&utm_medium=shopping%2Bengine&utm_campaign=googleproducts&gclid=CNHO7cvm6bMCFUQw4AodwSoA2w#TB_inline?height=600&width=550&inlineId=eyInsets&modal=false](http://www.outletpc.com/xx8455.html?utm_source=xx8455&utm_medium=shopping%2Bengine&utm_campaign=googleproducts&gclid=CNHO7cvm6bMCFUQw4AodwSoA2w#TB_inline?height=600&width=550&inlineId=eyInsets&modal=false)

and hooked it up as a second hard drive to my desktop computer. Worked great. I only took documents from it though, and I don't know if it could get things such as.....

Photos, I also do these projects in which I put my heart, soul, liver, kidneys etc. into and I always just keep them in my computer and just let them sit there. I was finally going through all these things and getting them organized. I don't want to re-do them. Along with the 2800 cars and 900 tracks I downloaded most of them downloaded one by one for NR2003 awhile back. Along with all the (way too many) programs I have downloaded in the past. (as you can tell I'm way too addicted to my computer, yes I know lol working on it.)

I would like to just get my computer back to the way it was, at all costs. I would rather not have to retrieve the data and then re-set my hard drive.





And thanks for all the help everyone. I appreciate it. I mean your not getting payed to help me or anything and are doing this out of your free time. It's appreciated.

---

### Post by glock356 on 2012-11-25
Hello!

I know only how to rescue your precious data(i have similar problem once)
Boot computer from any live CD or better(i use this) from [http://falconfour.com/projects.php?pid=7]("http://falconfour.com/projects.php?pid=7")

Once start screen of **FalconFour's Ultimate Boot CD** is loaded, select MiniLinux.

Mount your HD, select Midnight Coomander from file Manager menu and copy your data on external disk.
If this is possible on your comp now.

Problem is only how to download and burn FalconFour's Ultimate Boot CD since your comp is unusable now.

Ask friend, use any other Live CD...?

---

### Post by carl4926 on 2012-11-25
Use the Vista install media to:

> Select to "Repair your computer"
Select/put the radio button/dot next to "Use recovery tools that can help fix problems" --> Next
Select "command prompt"
enter this command: Bootrec.exe /FixBoot
enter this command: Bootrec.exe /FixMbr
enter this command: exit
Click to Restart

---

### Post by Gronknation on 2012-11-25
> Hello!

I know only how to rescue your precious data(i have similar problem once)
Boot computer from any live CD or better(i use this) from [http://falconfour.com/projects.php?pid=7](http://falconfour.com/projects.php?pid=7)

Once start screen of **FalconFour's Ultimate Boot CD** is loaded, select MiniLinux.

Mount your HD, select Midnight Coomander from file Manager menu and copy your data on external disk.
If this is possible on your comp now.

Problem is only how to download and burn FalconFour's Ultimate Boot CD since your comp is unusable now.

Ask friend, use any other Live CD...?Sadly my 2 friends don't  know anything about computers. Just sims and facebook. I could atleast  burn the program onto a blank CD and see what it does. 

Could I burn it on a desktop computer I have? And then use it on the not working computer?



                                                 > Select to "Repair your computer"
Select/put the radio button/dot next to "Use recovery tools that can help fix problems" --> Next
Select "command prompt"
enter this command: Bootrec.exe /FixBoot
enter this command: Bootrec.exe /FixMbr
enter this command: exit
Click to Restart                      Didn't work. I did everything you said. But I didn't see/do anything that said  

Select/put the radio button/dot next to "Use recovery tools that can help fix problems" --> Next

I clicked repair computer and then went into System Recovery Options.

---

### Post by carl4926 on 2012-11-25
Look at this page
[http://neosmart.net/wiki/display/EBCD/Recovering+the+Windows+Bootloader+from+the+DVD](http://neosmart.net/wiki/display/EBCD/Recovering+the+Windows+Bootloader+from+the+DVD)

---

### Post by pkadeel on 2012-11-25
> **Gronknation said:**
> Could I burn it on a desktop computer I have? And then use it on the not working computer?
The most simplest and easiest method was just go to your desktop computer and download the ubuntu iso and this time remember where you downloaded it.
[http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-desktop-i386.iso](http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-desktop-i386.iso)

Now take a new blank DVD and burn that iso on that DVD.
take that DVD out and shut down your desktop computer. Now put that DVD into your laptop and boot it up from that DVD. When asked, choose "Try Ubuntu" option and you will be able to view and recover all your data from the current HDD once you are in.

---

### Post by Bucky Ball on 2012-11-25
Just download the ISO, as suggested:

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

Burn a CD (create Disk Image), boot from it, get to the desktop by 'Try Ubuntu' (or it may just take your there). You should be able to see all partitions. Save your data to an external device ...

Easy, relatively quick and painless. Then you can wipe the lot and reinstall Windows (and install Ubuntu another partition if you like rather than a Wubi install). 

Good luck.

---

### Post by Bucky Ball on 2012-11-25
> **pkadeel said:**
> The most simplest and easiest method was just go to your desktop computer and download the ubuntu iso and this time remember where you downloaded it.
[http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-desktop-i386.iso](http://releases.ubuntu.com/12.04.1/ubuntu-12.04.1-desktop-i386.iso)

Now take a new blank DVD and burn that iso on that DVD.
take that DVD out and shut down your desktop computer. Now put that DVD into your laptop and boot it up from that DVD. When asked, choose "Try Ubuntu" option and you will be able to view and recover all your data from the current HDD once you are in.

+1. Exactly. This *is* the easiest and most simple and mentioned previously. You can then wipe the lot once you have your data secured on an external device and reinstall Windows (and Ubuntu on a separate partition for a real dual-boot if you feel like it).

Good luck ...

---

### Post by glock356 on 2012-11-25
> **Gronknation said:**
> Sadly my 2 friends don't  know anything about computers. Just sims and facebook. I could atleast  burn the program onto a blank CD and see what it does. 

**Could I burn it on a desktop computer I have?** And then use it on the not working computer?



                                                 Didn't work. I did everything you said. But I didn't see/do anything that said  

Select/put the radio button/dot next to "Use recovery tools that can help fix problems" --> Next

I clicked repair computer and then went into **System Recovery Options**.

If you asking me for dowload and burn FalconsFour Boot CD - yes, you could, if that computer hava a CD-DVD burner and is conected on internet
Download iso image FF Boot CD.
On CD-DVD burning program use Burn Image.
If you do not have any, download and install **Infra Recorder** or **ImgBurn** - ask Google where to find it.
When installed, open program, select Burn Image, find downloaded iso file of FF Boot CD, select minimal speed(for CD is usualy 8x) and hit Burn.
When burned, put CD in brokem comp., restart, select Boot from CD(usualy F12, on some comp. may be F8...?) - look on bios startup on the bottom of screen.
For continuing with FF Boot CD read my previus post.


For using Vista install DVD - i do not know how to look "Use Recovery Tool......"
In Windows 7 selection Command Promt is on the bottom of window - in Vista i think it be the same.
Clik on **_Command Prompt_** - black window appears an then type what **carl4926** wrote

bootrec.exe /fixmbr [Enter]
bootrec.exe /fixboot [Enter]
exit [Enter]

Remove Vista DVD and reboot computer

---

### Post by Gronknation on 2012-12-01
I'm back. Took me a while to get a CD. Having two problems 

I either get this message

Error 0x800703EE "The volume for a file has been externally altered such that the opened file is no longer valid"

or

Either the disc in the CD or DVD burner isn't writable disc or it's full.

Please insert a writable disc in into drive D


I haven't altered the file and the CD is large enough for the file.


It did ask me when I first put the CD in

"Would you rather have it be like a USB drive where you can delete stuff"

or

"Would you rather have it like a CD and everything stays on there"

Those weren't the exact words but around that. And I clicked USB Drive. 

It's a Memorex CD-R





Also the CD started with 702 MB. I put the iso on then deleted. There is nothing currently on the CD but there is only 249MB left.







[SIZE=4][B]
UNREAL

[/B][SIZE=4][SIZE=2]Looked everywhere for these CDs. So [SIZE=2]we found them. They only had 700MB[SIZE=2] or 4.6 GB [SIZE=2]you couldn't put something in between. So after an awful day without the computer I come home and format the drive. Now I'm left with 57[SIZE=2]6 MB. I bou[SIZE=2]ght CD-RW[SIZE=2]. Because I ha[SIZE=2]d a CD-R and has NOTHING on it and it took up 75% of the spa[SIZE=2]ce. For whatever stupid [SIZE=2]reason, there was NOTHING on it. And I couldn't get the space back[SIZE=2], because once things take up space on a CD-R you can't get your space back![/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE][/SIZE]

---

### Post by Gronknation on 2012-12-01
Got everything back!! Thank you guys so much. When I formatted the CD it went to 574 but when I burned the program on it, it went to 695 MB. Weird.

Thanks again for helping. You have no idea how much stuff was saved. It's really nice of you guys to help me out. Without getting payed, and just doing it to help people.

You saved everything!!!!!

Lesson Learned: Back Up Your ****

---

