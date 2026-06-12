---
title: "Help, Help, Trying to install Ubuntu 12.04"
date: 2012-09-11
forum: Installation &amp; Upgrades
---

### Post by lelovely7315 on 2012-09-11
[FONT=Arial]Hi there, 
    I am a beginner on this Linux. I sure want to get it going on all my computers. I am tired of VIRUSES on Windows. Plus I like what I see in the demo's, so I have been trying to install Ubuntu 12.04 (LTS) on one of my computers. I have four (4).[/FONT] But I have been having bad luck trying to get it installed. I have downloaded three copies of the OS and I have made five (5) cd's and two (2) USB sticks all good with the OS. And I can't get it installed!! I can get it to run in Demo, but when I try to install it it starts like it will install and I set my time, language, password and username. Then it gets to HD where it tells me what I will need in storage space. (I have a clean 200gb HD so that is not the problem.) This is where it stops, I get this error: UBI-Partman-exit code 10, and also UBI-Console-Setup- exit code 1. from that point on I get a little turning wheel for my cursor and the OS don't install. I have been trying to get this done for two (2) weeks now so HELP, HELP, HELP. Hope to hear from someone soon.   :( Thanks Larry

---

### Post by GeForce 9500GT on 2012-09-11
I found something which might help:
 
If you're able to boot into the selection screen where you have to choose between trying out Ubuntu or install Ubuntu, press F6 and then choose the option: **nodmraid**. Will this work?

---

### Post by Epodx64 on 2012-09-11
Whats all the specs on your computer? Processor,ram,hdd, ''video card'' , anything you think would be useful about the system I need more information to help you get Ubuntu installed if you can get into a live system maybe come to forums while your logged into the live system off the cd and we can help you more

---

### Post by lelovely7315 on 2012-09-11
Hi there, thanks for coming back so soon. Inside the computer is: CPU= AMD 2200XP, Video= nvidia GeForce FX5500, Motherboard is= ASUS K7???, Ram= 2gb, HD= Maxtor 200gb. I had this working with Zorin at one time. I hope this helps in getting this going.  Thanks Larry

---

### Post by NikTh on 2012-09-11
Hi , 

here is a similar Thread : [http://ubuntuforums.org/showthread.php?t=1498417](http://ubuntuforums.org/showthread.php?t=1498417)

nodmraid maybe is the parameter to avoid the error. (as @GeForce 9500GT mentioned) . 

Take a look here on how to pass this parameter : [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Thanks

---

### Post by lelovely7315 on 2012-09-11
Hi again, Well I have tried the F6 key on the boot screen, I had a choice so I picked nomodeset. Then I started to install the program, I made it through the questions without getting an error. So now I have this little round ball with the inside part spinning on the desktop. Now does this mean it is installing or what ? I have had this little ball before, how can I see if this OS is installing without stopping it ? I don't see a way of telling if it is installing or not. Plus how long will it take to install ? So I may have solved my problem, but I must wait and see if it installs .:( Thanks Larry.

---

### Post by Bartender on 2012-09-12
When Ubuntu's installing you get a little slideshow that talks about what you can do with it.  Multimedia, email, etc.  If you're not getting the slideshow then it's *probably* not installing.

---

### Post by Bashing-om on 2012-09-12
Lets go back to the basics:
   After the boot screen clears, press any key to obtain an ububtu options menu.
  Choose to check the disk (That is the install disk) for defects.
  Watching this thread; and I would have expected the "nomedeset" parameter to at least allow you to boot into the system (install an appropriate drive at a later time).

[INDENT]awaiting to see how I can assist <==BDQ

[/INDENT]

---

### Post by mips on 2012-09-12
What are the specs of your computer? CPU & RAM?

If you don't come right I would suggest trying the alternate cd images as you might have better luck with them,
32-bit--- [http://releases.ubuntu.com/12.04/ubuntu-12.04.1-server-i386.iso](http://releases.ubuntu.com/12.04/ubuntu-12.04.1-server-i386.iso)
64-bit--- [http://releases.ubuntu.com/12.04/ubuntu-12.04.1-alternate-amd64.iso](http://releases.ubuntu.com/12.04/ubuntu-12.04.1-alternate-amd64.iso)

---

### Post by Wim Sturkenboom on 2012-09-12
> **mips said:**
> What are the specs of your computer? CPU & RAM?
That was already asked (and answered) ;)

---

### Post by mips on 2012-09-12
> **Wim Sturkenboom said:**
> That was already asked (and answered) ;)

Oops. Specs seem fine.

---

### Post by lelovely7315 on 2012-09-13
Hi there, glad to hear from you. After the boot screen clears I can either go to CMOS and make changes or go to the boot menu. If I leave it alone it goes to a black screen with white writing telling what is in the case and all the drivers, etc. And then it stops, it will not go any farther. I was running it in Demo mode and I tried to install it yesterday. But it did not install, I can do everything in demo mode, but I can't install it.

---

### Post by lelovely7315 on 2012-09-13
Hi everyone, I can run Ubuntu 12.04 (LTS) in demo mone but I can't install it!!! What is the problem?

---

### Post by Bashing-om on 2012-09-13
How new is the box you are presently attempting to install on ?

see if this link applies:
[http://ubuntuforums.org/showthread.php?t=1974392](http://ubuntuforums.org/showthread.php?t=1974392)
Dual booting UEFI 
[INDENT]hth <==BDQ

[/INDENT]

---

### Post by lelovely7315 on 2012-09-14
Hi there, I am not running a Dual boot system. I am working with a clean 200gb HDD, 2gb of ram, AMD 2200xp CPU, an the rest is more than is needed to run the OS. This computer is for Linux only and not for windows. I have another computer for windows, which I will switch over to Linux as soon as I get a stable system going. So why can I run good in DEMO mode and not be able to install it on the computer?

---

### Post by Mohan1289 on 2012-09-14
Hi lelovely7315

If you have windows you can try wubi.exe(Windows Ubuntu Installer) which occupies 30Gb space at max..
It''s better if you installed like that since you are using Windows well rather than Linux.. 
It's better if you get used to Linux first and then install the Ubuntu in your Entire Hard Disk.

I hope this is helpful.

---

### Post by Mohan1289 on 2012-09-14
> **lelovely7315 said:**
> Hi there, I am not running a Dual boot system. I am working with a clean 200gb HDD, 2gb of ram, AMD 2200xp CPU, an the rest is more than is needed to run the OS. This computer is for Linux only and not for windows. I have another computer for windows, which I will switch over to Linux as soon as I get a stable system going. So why can I run good in DEMO mode and not be able to install it on the computer?

I think you took LIVE cd rather than Bootable Cd check it once.... 

or download from ubuntu.com and write the image to Empty CD then boot it

---

### Post by mips on 2012-09-14
You could always try the alternate install image from one of the other derivitives or boot a netinstall cd and try installing off the net.

---

### Post by Bucky Ball on 2012-09-14
*Thread moved to **Installation & Upgrades***

---

### Post by Bucky Ball on 2012-09-14
> **Mohan1289 said:**
> Hi lelovely7315

If you have windows you can try wubi.exe(Windows Ubuntu Installer) which occupies 30Gb space at max..
It''s better if you installed like that since you are using Windows well rather than Linux.. 
It's better if you get used to Linux first and then install the Ubuntu in your Entire Hard Disk.

I hope this is helpful.

The OP is NOT dual-booting or using win.

---

### Post by gordintoronto on 2012-09-14
> **lelovely7315 said:**
> Hi again, Well I have tried the F6 key on the boot screen, I had a choice so I picked nomodeset. Then I started to install the program, I made it through the questions without getting an error. So now I have this little round ball with the inside part spinning on the desktop. Now does this mean it is installing or what ? I have had this little ball before, how can I see if this OS is installing without stopping it ? I don't see a way of telling if it is installing or not. Plus how long will it take to install ? So I may have solved my problem, but I must wait and see if it installs .:( Thanks Larry.

This thread might contain your solution:
[http://ubuntuforums.org/showthread.php?t=1498417](http://ubuntuforums.org/showthread.php?t=1498417) 

After pressing F6, choose "other" and type in "nodmraid".

It might even be useful to see if RAID is enabled in the BIOS, and, if so, turn it off.

"nomodeset" is useful for dealing with balky video cards, usually cards which are too new to be supported in Ubuntu.

---

### Post by lelovely7315 on 2012-09-16
Hi again, 
        well I still have the problem with not being able to install Ubuntu 12.04 (LTS). I can get into Demo mode and run it just fine, ( I am using it now.) But I still cannot install it on the HDD, I have reformatted and cleaned the HDD, I even went to the Website and downloaded the OS again. Installed it on a new CD-R, and I can run it in Demo but I still can't install it. I don't get any errors and it acts like it is installing, only I get a black screen with a little ball on it spinning. This is getting FRUSTRATING, I sure want this OS on this computer!!  Any help and info will deeply appreciated.    Thanks Larry

---

### Post by grahammechanical on 2012-09-16
As you should not be having this kind of problem for so long, I am going to ask some stupid questions:

Is the Ubuntu live CD a 64bit ISO image? Are you trying to install it on a machine with a 32bit CPU?

It is just a wild thought. The 32bit Ubuntu will run on a 64bit CPU because of backwards compatibility but the 64bit version will not run on a 32bit CPU.

Regards.

P.S. I was just now reading through this link

[http://ubuntuforums.org/showthread.php?t=1498417]("http://ubuntuforums.org/showthread.php?t=1498417")

and another thought occurred to me. Is this 200GB disk the only one on the machine? If there are Windows disks in RAID configuration that maybe confusing the installer.

---

### Post by Bucky Ball on 2012-09-17
> **grahammechanical said:**
> 

Is the Ubuntu live CD a 64bit ISO image? Are you trying to install it on a machine with a 32bit CPU?

LiveCD runs fine so guessing the bits must be right. ;)

Boot from a LiveCD, launch Gparted. What is on the disk you are  attempting to install to? If you have four primary partitions there  already you are going to have problems as this is the limit (generally).  You may have mentioned it was a blank drive earlier and if so,  apologies.

If you do have four primary partitions already you are going to need to  delete one, make the free space an extended partition, then install  Ubuntu, which will need a / and /swap partition at least, on logical  drives inside the extended. We can help with this.

Just more ideas ... :wink:

(PS: Just to get this clear: You are booting from the LiveCD, getting to  the desktop, all fine, then clicking the 'Install Ubuntu' icon? Then  there is the spinning ball. How long are you waiting at the spinning  ball? The other option is to try the alternate install CD rather than  the Desktop. If it a prob with graphics this will help avoid it, among  other things. Exactly the same but text-based installation rather than  disco graphics. Try this page under 'Bit Torrent' down the page a bit:

[http://www.ubuntu.com/download/desktop/alternative-downloads](http://www.ubuntu.com/download/desktop/alternative-downloads)

... as downloading via torrent is foolproof as the image is checked on way.)

---

### Post by Bucky Ball on 2012-09-17
Boot from a LiveCD, launch Gparted. What is on the disk you are attempting to install to? If you have four primary partitions there already you are going to have problems as this is the limit (generally). You may have mentioned it was a blank drive earlier and if so, apologies.

If you do have four primary partitions already you are going to need to delete one, make the free space an extended partition, then install Ubuntu, which will need a / and /swap partition at least, on logical drives inside the extended. We can help with this.

Just more ideas ... ;)

(PS: Just to get this clear: You are booting from the LiveCD, getting to the desktop, all fine, then clicking the 'Install Ubuntu' icon? Then there is the spinning ball. How long are you waiting at the spinning ball? The other option is to try the alternate install CD rather than the Desktop. If it a prob with graphics this will help avoid it, among other things. Exactly the same but text-based installation rather than disco graphics.)

---

### Post by lelovely7315 on 2012-09-17
Hi everyone, 
    Thanks for the info, now I will try and answer some of the questions you asked. I am running a 32bit system and everything I download is 32bit.
    I only have one (1) HDD in this computer, and when I try to install the OS at one point I get to chose how I want to partition the HDD. So I get to see how the program has partitioned the HDD. What it has done is: sda1 ext4 4.6gb, then sda2 ext6 187.96gb, then a swap 2.1gb. I think I have those numbers and names correct. I also formatted the HDD twice and the program puts the same partitions back. 
    I have burned another CD this time the way the WebSite said, using Imgburn, still the same results, I am using it now in Demo mode!! I have also tried using a USB flash drive with the same results. I have about 7 .iso CD's and 3 USB drives. All of these I followed the directions that was on the web!!
    I do not see anything that is not correct on this computer, I just don't understand why It won't install!!  Give me some more info so I can get this going!!  Thanks Larry

---

### Post by lelovely7315 on 2012-09-20
Hi everyone,
    Well what I have tried really don't make any sense now!! I went and installed another HDD in this computer and installed Linux Zorin on it with no problems. I used it and tested Zorin for half a day. worked great!! 
    Then I tried to install Ubuntu again on the HDD and still it won't install!! Is there something wrong with Ubuntu? Like I said I have tried seven (7) different CD's and three (3) USB's with Ubuntu on them and still I can't install it, ( I can run it great in DEMO ), but can't install!! I have never had this much trouble installing a program on a computer.
    If anyone can think of something that I may have missed or you know of Please Let Me Know!!    Thanks Larry :(

---

