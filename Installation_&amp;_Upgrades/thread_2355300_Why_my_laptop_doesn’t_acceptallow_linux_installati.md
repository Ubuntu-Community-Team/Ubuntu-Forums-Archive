---
title: "Why my laptop doesn’t accept/allow linux installation? Linux"
date: 2017-03-11
forum: Installation &amp; Upgrades
---

### Post by timomak on 2017-03-11
Hi all,
I tried to boot with a Linux os and so choose one of them. I  started with Lubuntu and Ubuntu, after changing the settings in boot  order. Both os proceeded to a certain point.
 As for lubuntu, this  was up to language selection, installation panel then the installation  icon (with the points) of lubuntu. After waiting long and tried eject  the installation dvd, a huge info appeared were I was only able to see  the authentication word but no time to read.
As for Ubuntu the process stops to the installation icon and then throws me out.
I tried twice , first with HDD on and another without HDD on the machine.

  Then I tried boot from a friend’s computer and boot was successful for both os.
My  machine is a travelmate 244LC with Intel Celeron 2,6 cpu 1,5 G ram  (upgrade possibility up to 2 G) and phoenix bios TM 240. It was  purchased to be bundled with windows xp (there was 3 dvd’s with the os  in the package).

  The question is if there is a sort of authetication issues from the  vendor and or microsoft, something that doesn’t allow proceed further.  Or i could be some advanced bios settings such x11 server or something  like that.
 I don’t think there is a hardware issue as more heavy  distros of linux work for less powerful machines. At that moment the  machine runs windows 7.
If you have any suggestion about bios settings or other that may help proceed to the installation please let me know
Thank you

---

### Post by oldfred on 2017-03-11
Most Windows 7 installs use all 4 primary partitions.
Do you have an available primary partition to be the extended partition and act as container for all the logical partitions? 
While Windows only installs to primary partitions, Linux installs to logical partitions without issue.

Post this from live installer.
sudo parted -l

Often better to partition in advance. Then the installer can use the swap on the hard drive to help speed up the install.

I have a laptop from 2006 originally XP with 1.5GB of RAM. I retired it a year or two ago and it had 12.04. With Ubuntu Unity was just too much, while it installed full Ubuntu it took forever to do anything. I installed fallback/gnome panel and it worked well. 
Just as a test I did recently install 16.04, just to see if it worked and was a bit slow but even Unity worked ok. But now I have a desktop with an SSD, so everything else is slow. :)

Most would say if less than 2GB of RAM use Lubuntu.

Some newer Bay Trail Celeron chips had issues and needed boot parameters with older versions of Ubuntu. Not sure if still issue or not.
       Bay Trail freeze need boot parameter: intel_idle.max_cstate=1 or patches, see comments
[https://bugzilla.kernel.org/show_bug.cgi?id=109051](https://bugzilla.kernel.org/show_bug.cgi?id=109051)
Many Intel Bay Trail Devices Have Been Borked On Linux For The Past Year - Mar 2016
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](http://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)

---

### Post by timomak on 2017-03-11
Hi Oldfred,
Thanks for your answer.
I&#8217;m somehow advanced with computing, windows and android. But a beginner with linux and this is my first participation in a linux distro site.
My intention is to install a Linux distro let&#8217;s say lubuntu in another partition as my main os and keep win 7 as it is now for 2[SUP]nd[/SUP] option

- My HDD is 80 G of size with a primary partition of approx 40 G, occupied (not fully) by win 7. The other space is still inactive because I left it so for installing a Linux os
- I also have another smaller HDD 30 G size(the machine mounts only one HDD) occupied by win xp, no partition here or just one for the hole disk, which I keep just in case, of any problems with win 7. Xp still work fine.

I think I begin understand what you are saying, that the installer doesn&#8217;t &#8216;see&#8217; an appropriate partition for further proceeding !
If so, how on my friend&#8217;s laptop the trial session was ok with HDD mounted or removed from the machine (only thing I see in disks manager of friend&#8217;s comp is a loop small disk, I don&#8217;t know what it is). Also, why when I removed the HDD form my laptop didn&#8217;t play trial session ? I admit here that the procedure in this case moved a little further.
Still, is this why when I tried once to boot from usb, I received the message &#8216;os not found&#8217; ?

But to proceed by steps.
1. I&#8217;m not familiarized with partitioning and I admit I have to read the procedure. So you propose to create another partition for the installer to be able to boot ? If windows manages up to 4 partitions would it be possible for linux install ?
2.  What is the workaround >computer administration> disk admin> choose the space> create partition ? secondary or logical, or it is the same thing ?
3. It would be fine if you explain the &#8216;post from live installer - sudo parted-l . I&#8217;m sure I&#8217;ve seen this before but, excuse, I don&#8217;t know what is it.

It is much time I work for this issue and I look forward to finish and start on a new os, to personalize and do normal daily use. I think I go deep waters without much knowledge, does it worth !?  but it may end with success.It will be good having your guidelines on this subject when you have some time available


Thank you

---

### Post by oldfred on 2017-03-11
From live installer, go into terminal. Then copy & paste the command. Most commands even spaces are important and depending on font used, space may not be obvious.
sudo parted -l

With Linux we end up having to use terminal. There are many gui/desktops and each is enough different it is just about impossible to walk a user thru commands and then more difficult to post results. You can easily copy & paste output from terminal back to here in forum. If long output we do prefer using code tags, which are easy to add with forum's advanced editor and # icon.
I really hate the Windows blogs & forums that show screen shots and how to do something and my screens are not at all like the screens they post. Rarely with Windows do you find the terminal commands which Windows does have.
 
Get a terminal by <ctrl_+alt+F1> & back to gui with ctrl alt f7
[https://help.ubuntu.com/community/UsingTheTerminal/](https://help.ubuntu.com/community/UsingTheTerminal/)
In Ubuntu you start a terminal window with ctrl + alt + t
or via the menu Program -- Accessories -- Terminal 
Or with Unity & dash (first icon on left side top) type in terminal.

---

### Post by timomak on 2017-03-12
Hi,
May be there was a misunderstanding in what i wrote here (english is not my native language). I mean that i was _just looking_  to see how is linux and not trying to install the software. i was just doing a trial session that didn't work with my pc. So what has to do with HDD partitions,this should work even without HDD mounted on the machine. In this case are the above commands necessary or helpful ?

---

### Post by mörgæs on 2017-03-12
So, are you saying that not even Lubuntu made a successful live boot?

---

### Post by sudodus on 2017-03-12
> **timomak said:**
> Hi all,
As for lubuntu, this  was up to language selection, installation panel then the installation  icon (with the points) of lubuntu. After waiting long and tried eject  the installation dvd, a huge info appeared were I was only able to see  the authentication word but no time to read.


I would guess that there is problems with some particular hardware, maybe the graphics or wifi chip/card. Please tell us as much as possible about the computer. (There might be different hardware in a computer with a certain model number.) Please specify your computer, at least

- Brand name and model (we know 'Travelmate 244LC')
- CPU (we know 'Intel Celeron 2,6')
- RAM (we know '1.5 GiB')
- graphics chip/card
- wifi chip/card (maybe a USB dongle?)

It will help us help you. Maybe we can suggest that you boot with some [boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808), for example nomodeset, acpi=off, noapic ...

---

### Post by timomak on 2017-03-12
[FONT=helvetica]Except info below, **wifi/Ralink and 3g/ZTE dongles are used for network connection** (_* not mounted from *_[/FONT]_*[FONT=helvetica] the beginning [/FONT]*_[FONT=helvetica]_*during life session/ tria*_l)
The available hardware resources are as follows:[/FONT]
 
[LIST]
[*]Intel Celeron (Pentium 4 based) 2.6 GHz processor 
[*]Acer (Phoenix) BIOS, TM 240 v 1.14, most recent version is 1.15 
[*]256 MB DDR-RAM module** Now is 1,5 G (upgrade possibility up to 2G)** 
[*]Hitachi 30 GB UltraATA/100 HDD** Now mounted 80 G** 
[*]Intel 82855 GM integrated graphics controller (16 MB dedicated shared memory, up to 64 MB dynamically) 
[*]QSI DVD/CD-RW combo drive 
[*]Synaptics touch pad with 2 buttons and 2-axis pad 
[*]Realtek RTL-8139 Ethernet controller 
[*]Texas Instruments PCI1520 PCMCIA controller 
[*]Intel 82801DBM chipset 
[*]Agere Systems AC'97 v.92 modem 
[*]Crystal (Cirrus Logic) AC'97 audio controller 
[*]Fast IrDA port 
[*]4 USB 2.0 ports 
[*]2 PCMCIA ports 
[*]Ethernet port 
[*]Headphone jack 
[*]Microphone jack 
[*]Parallel port 
[*]VGA port (outgoing only) for external monitor 
[*]85 keys slim keyboard 
[*]6 special keys (Mail, WWW, 2 Custom, Bluetooth and Wireless) 
[*]Power key 
[*]14 Fn keys 
[*]16 keys numblock 
[*]15" TFT Screen, 1024x768 native resolution 
[/LIST]

---

### Post by timomak on 2017-03-12
You should also see this.
[http://www.linux-laptop.net/hosted/mandriva-acer-243xc.html](http://www.linux-laptop.net/hosted/mandriva-acer-243xc.html)

---

### Post by sudodus on 2017-03-12
> **timomak said:**
> You should also see this.
[http://www.linux-laptop.net/hosted/mandriva-acer-243xc.html](http://www.linux-laptop.net/hosted/mandriva-acer-243xc.html)

Thanks for all these details :-)

There is a tip in the link about Mandriva to use the boot option **vga=791**

I suggest that you try that according to this link, [Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)

Otherwise, if you do not connect the wifi dongle, I think you should be able to get Lubuntu running. You can try some other boot options too.

I suggest that you start trying Lubuntu 16.04.1 LTS.

See the following link about tips of which versions to try, [How to select the version and flavour of Ubuntu](https://ubuntuforums.org/showthread.php?t=2230389&p=13540865#post13540865)

---

### Post by timomak on 2017-03-12
Thank you Sudodus,
The funny !! thing after you asked about the devices in your previous msg, i plug the wifi adaptor and tried Ubundu 14.04 live cd, in plus i blow air the cd drive just in case of dust. And SUCCESS. Ubuntu proceeded to trial session. I noticed that is very heavy using almost 90% of cpu and 450MB ram (this is not much) 
I also tried Lubuntu but it turned off the machine after a while. I think Lubuntu iso is rather damaged.
Anyway i'll come back later when i will test the iso

---

### Post by sudodus on 2017-03-13
Well, you can check the iso file with md5sum, and you can check installation media at the boot menu according to this link,

[Checking the iso file and the boot drive - detailed tips](https://ubuntuforums.org/showthread.php?t=2196858&p=13511608#post13511608)

Look for 'Check the disk for defect'

-o-

I suggest that you open the computer (whatever can be opened), and try to blow away dust that may create problems not only in the CD drive.

---

### Post by timomak on 2017-03-13
ok
I will proceed by steps as it seems to me not so easy. I will follow your guidelines as described. But if possible give me a feedback for the following.

1. What do I press to access commands during booting procedure (do i need)? 
2. When tried to make a usb bootable with Rufus, I received a notification that a file in the iso of Lubuntu named syslinux is not the correct one and the software asked me to connect to the network to download two included files ldlinux.sys and ldlinux.bss. 
But when I burn a dvd with the same iso, aren&#8217;t these two files necessary ? if so where can I put these 2 files in order to be included in the burned iso dvd (I have downloaded the files before). Could this be a reason of non booting ?  
3. Trying to download the new Lubuntu 16.04.1 LTS the site directs me to download a 16.04.2 LTS version, is this correct ? I don&#8217;t find 16.04.1
4. The Mandriva case (vga=791)I suppose is to be done after having successfully instal the os, correct ? If not, do I have to access commands during booting to try boot options as described in your article.(nonodeset, forcepae)
5. This case does applies to me too [http://askubuntu.com/questions/108505/how-do-i-install-ubuntu-11-10-on-an-acer-travelmate-240](http://askubuntu.com/questions/108505/how-do-i-install-ubuntu-11-10-on-an-acer-travelmate-240)
6. The case of Morgaes (above) is applicable to me too?
HDD is not yet prepared with second partition to be able to install linux but that&#8217;s not an issue for the moment I guess.

I&#8217;ll go for it when time available and come back when face difficulties

---

### Post by sudodus on 2017-03-13
Please use the default font.

> **timomak said:**
> ok
I will proceed by steps as it seems to me not so easy. I will follow your guidelines as described. But if possible give me a feedback for the following.

1. What do I press to access commands during booting procedure (do i need)?

See this link: [Boot options](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808)
> 
2. When tried to make a usb bootable with Rufus, I received a notification that a file in the iso of Lubuntu named syslinux is not the correct one and the software asked me to connect to the network to download two included files ldlinux.sys and ldlinux.bss.
But when I burn a dvd with the same iso, aren’t these two files necessary ? if so where can I put these 2 files in order to be included in the burned iso dvd (I have downloaded the files before). Could this be a reason of non booting ?

If you ***clone*** the iso file to a DVD disk or use a cloning tool to create a USB boot drive, for example [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) in Windows or [mkusb](https://help.ubuntu.com/community/mkusb) in linux, you should ***not*** tamper with any syslinux files. A cloned drive will work (if the iso file was downloaded correctly).

I'm not sure about that problem with Rufus.
> 
3. Trying to download the new Lubuntu 16.04.1 LTS the site directs me to download a 16.04.2 LTS version, is this correct ? I don’t find 16.04.1

See this link: [old-releases.ubuntu.com/releases/xenial](http://old-releases.ubuntu.com/releases/xenial/)
> 
4. The Mandriva case (vga=791)I suppose is to be done after having successfully instal the os, correct ? If not, do I have to access commands during booting to try boot options as described in your article.(nonodeset, forcepae)

Yes and no. You can use boot options ***both*** in the live session (booted from DVD or USB) and in the installed system.
> 
5. This case does applies to me too [http://askubuntu.com/questions/108505/how-do-i-install-ubuntu-11-10-on-an-acer-travelmate-240](http://askubuntu.com/questions/108505/how-do-i-install-ubuntu-11-10-on-an-acer-travelmate-240)

OK. (Wubi is deprecated. It does not work with newer versions of Windows and it is no longer supported.) The advice to burn the DVD with slowest possible speed is very important.
> 
6. The case of Morgaes (above) is applicable to me too?
HDD is not yet prepared with second partition to be able to install linux but that’s not an issue for the moment I guess.

I’ll go for it when time available and come back when face difficulties

First make the computer work with a live system (booted from DVD or USB). Later you can start thinking about installing.

---

### Post by timomak on 2017-03-13
Very well,
Only thing is that the proposed site for downloading, is for Ubuntu 16.04.1 and not for Lubuntu 16.04.1.LTS
I found this [http://lubuntu.me/lubuntu-16-04-1/](http://lubuntu.me/lubuntu-16-04-1/) which directs to lubutntu 16.04.2.
I will try with it.

---

### Post by sudodus on 2017-03-13
Sorry. Here is a link for Lubuntu 16.04, **16.04.1** and 16.04.2. Please scroll down to find it.

[cdimage.ubuntu.com/lubuntu/releases/16.04.1/release](http://cdimage.ubuntu.com/lubuntu/releases/16.04.1/release/)

Lubuntu 14.04.1 LTS will reach end of life next month, so I recommend version 16.04.1 LTS.

---

### Post by timomak on 2017-03-13
Ok fine, Thanks

---

### Post by timomak on 2017-03-14
Back again,
I finally downloaded the iso successfully, then checked with winMD5Sum and it's correct.
Now 
- i'll buy a black dvd to burn the iso probably with Xfburn form the other pc (i'll check if there is any speed option there)
- I'll try also to clean the optical with a cotton tip, 
- If try to boot, having wifi adapter pluged in is helpful i guess, correct?

bye for the moment.

---

### Post by sudodus on 2017-03-14
> **timomak said:**
> 
- If try to boot, having wifi adapter pluged in is helpful i guess, correct?


You can try with and without wifi adapter plugged in. Let us hope that Lubuntu can use the wifi adapter.

---

### Post by timomak on 2017-03-14
Back here, but not lucky !
I burned the iso and checked as described in the site. The media is with no defects
1. Started the trial session with the wifi adapter plugged in. Went to a certain point with the lubuntu logo on screen and the point below, then after a while, let's say 8 - 10 min suspended function automaticaly
2. Then i tried checking memory, but after some time in non fall safe mode, the fan started to run full speed. I decided to stop the test.
3 Thinking of a possible incompatibility between the 2 ram chips i removed the one of 512 mb and run check again in fail safe mode. After enough this time, fan speed again on full. Stopped the check.
4. Then I start a second trial session with 1 G ram and without wifi plugged in. During this turn, the logo stayed for a long on screen, and after 20 -25 min a huge amount of information appeared on screen, i didn't understand much, and i closed the machine.

Now what, do you think trying other boot options before checking another version ?

---

### Post by sudodus on 2017-03-15
You seem to have big problems with Lubuntu. Maybe it is time to try some other linux distros for old computers. I suggest that you try

Knoppix, Puppy Linux (Wary Puppy and TahrPup), and Tiny Core. It is quite possible that at least one of these linux distros will work well in your computer.

---

### Post by timomak on 2017-03-15
Yes, it seems so, and i like Lubuntu environment.!
Anyway, we keep in touch.

---

### Post by sudodus on 2017-03-15
Yes, we keep in touch. I still want to help you, even if it might be with another linux distro. Later on, maybe, we will find out what goes wrong with Lubuntu and can fix it.

---

### Post by timomak on 2017-03-15
Thank you,
I can say that you do a great job, both communicatively and technically.
I'll do a double check again in case that something is missing, and read the other boot options as well. Of course it takes much time but will arrange this step by step.

---

### Post by sudodus on 2017-03-15
I can add one distro to the alternative list: ToriOS, so

***Knoppix, Puppy Linux (Wary Puppy and TahrPup), Tiny Core and ToriOS.***

You can also read the following thread, which contains a lot of valuable tips for linux in old computers,

[Old hardware brought back to life](https://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by timomak on 2017-03-16
Hi Sudodus,
i'm trying to apply  some boot options according to your posts as well Oldfred post for intel. I would like to ask is this proceedure (reboots w/changes acording to boot options proposed) risky to harm bios or other so turn the computer unsusable ? Also where i enter the option forcepae, in the popup window or down to the command line after the dashes ?

---

### Post by mörgæs on 2017-03-16
A Pentium 4 does not need forcepae.

---

### Post by timomak on 2017-03-16
It's a celeron (pentium 4 based). Applies the same i guess ?

---

### Post by sudodus on 2017-03-16
Yes, I think so: You will *not* need forcepae. (Anyway, if needed, it will not work at all, and you will be notified about the problem.)

And I don't think it is risky.

---

### Post by timomak on 2017-03-18
Hey guys,
It look i haven't good skills for a handyman !
It seems that i turned mothrerboard off !.
Yesterday, while working w/ win7 i turned to sleep mode for half an hour . later instead of having two leds on i.e. power and sleep mode leds, there was 1 more led, the media or disk activity( a small rectangular icon). I pressed the power buton but nothing happened. Then i pressed for 6 sec power button to turn off the machine. After that i tried to power on but only media led lights on and nothing happens, no sound from the fan no activity.
Then i removed HDisk and ram modules and mount only one ram module, the original one(from factory). But again only thing that happens is media/disk led that lights on. Any ideas about?

The other thing is that the only tool to do my job now is my friends's lenovo which i run with the live cd's
I have heard that runing with live cd's or even usb's is a much safer way regarding passwords (let's say) for state tax sites or ebaniking services, something like 'safebrowsing of avast' . Do you know if this is safe enough to work, until check my machine's problem?
Thank you again

---

### Post by sudodus on 2017-03-18
Maybe not so convenient to run a live-only system, where you cannot save system things to survive a reboot, but definitely a safe way. Reboot and get a fresh system!

-o-

An alternative, that is not as safe, but more convenient, is to run a persistent live system (typically run from a USB pendrive). You can create such a system with mkusb according to the following links.

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/persistent](https://help.ubuntu.com/community/mkusb/persistent)

But you can boot your persistent live drive without persistence, and have the same level of security as any live-only system, when you connect to your internet bank.

-o-

An alternative is 'simple persistence' according to the following link. It can be used with the system in a DVD disk and a partition for persistence somewhere else, for example in the internal drive or in a separate USB pendrive.

[mkusb/sp](https://help.ubuntu.com/community/mkusb/sp)

---

### Post by timomak on 2017-03-18
Yes, it's annoying to repeat tasks with no resume option, even set time is a problem.
But first off all, is there anyway of checking if motherboard is finally harmed ?:confused:

Now, i thought usb live system would be an option and would work as a small hard disk, store some preferences and resume from standby. Would also an antivirus be installed there ?
I still don't get well the difference between a simple bootable system usb(live) and a persistent live drive. In the case of a live system dvd i understand the need to have also a usb drive do do the job( is this the persistent drive?) But if everything is in a bootable usb by mkusb, why do it persistent, is this safer ?

As about safety.security, is possible during live session to be infected by malware ?
With linux in general, do we need also an antivirus program ?

In my case the lenovo HDD is damaged and so i removed it.


Just now i found an article explaining the difference and data percistancy mode in the live session. 

[https://www.maketecheasier.com/persistent-live-usb-vs-f](https://www.maketecheasier.com/persistent-live-usb-vs-f).

---

### Post by sudodus on 2017-03-18
> **timomak said:**
> 
Yes, it's annoying to repeat tasks with no resume option, even set time is a problem.
But first off all, is there anyway of checking if motherboard is finally harmed ?:confused:

I am not a hardware guy. I have no good answer to that question. I suggest that you create a new thread with a good descripttive title in the [Ubuntu hardware forum](https://ubuntuforums.org/forumdisplay.php?f=332).
> 
Now, i thought usb live system would be an option and would work as a small hard disk, store some preferences and resume from standby. Would also an antivirus be installed there ?

Yes, but you need no antivirus for linux. There are other things to consider. See this links,
[Ubuntu security forum](https://ubuntuforums.org/forumdisplay.php?f=338)
[https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
> 
I still don't get well the difference between a simple bootable system usb(live) and a persistent live drive. In the case of a live system dvd i understand the need to have also a usb drive do do the job( is this the persistent drive?) But if everything is in a bootable usb by mkusb, why do it persistent, is this safer ?

You found a link describing it :-)

A persistent live system is not safer, it is more ***convenient*** than a live-only system. But an installed system can be both safe and convenient. It can be installed into an external drive, for example USB pendrive, in the same way as if it were installed into an internal drive.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)
> 
As about safety.security, is possible during live session to be infected by malware ?

It is 'always' possible :-( See the links about security above.
> 
With linux in general, do we need also an antivirus program ?

No
> 
In my case the lenovo HDD is damaged and so i removed it.


---

### Post by timomak on 2017-03-19
Very well :smile:

---

### Post by timomak on 2017-03-21
[SIZE=3]Hi,
I finally have instal the minimal ubuntu/lubuntu 14.04 in a usb drive.
But when i try to login something goes wrong. It asks for login, i put the username >enter, then below link appears password, i enter password but the cursor doesn't enter any input, letter or number. How login ? 
[/SIZE]

---

### Post by sudodus on 2017-03-21
In text mode there is no echo (there are no dots or stars printed to the screen), but the password is read anyway. So after you have entered the password, press the Enter key, and you will be bogged in :-)

If you don't know what you have entered, you can press the backspace key a sufficient number of times to clear the input buffer, and then enter the password (and finish with the Enter key).

---

### Post by timomak on 2017-03-21
Thanks.

---

### Post by timomak on 2017-04-13
Hi everybody,
I&#8217;ll continue from the point we last time met here.
A few words for my acer machine, which stopped working. I removed processor and rtc -cmos battery. The other day when i assembled and turned 
power on, the machine started working again. Thinking that the problem was the motherboard, i was surprised and i assume it was a reset needed. However, it seems there is an issue with Ram modules or the motherboard to be checked. For the moment i keep it for reserve as works ok with win xp also with win 7. 
Ram modules or mothreboard could be an issue when trying to boot w/ Lubuntu.

Then I decided to purchase a refurbished Dell machine, which specifications are:
Dell Latitude D630
&#65279;
CPU                         -Intel Core 2 Duo T7250 / 2,2 GHz 
Chipset Type           -Mobile Intel GM965 Express 
&#65279;RAM                        -2 GB (2 x 1 GB) &#65279;Max Supported Size 4 GB &#65279;
Resolution                -1280 x 800 (WXGA) &#65279;
Graphics Processor  -Intel GMA X3100 
HDD                        -80 GB

I tried lubuntu 16.04.1 LTS/ubuntu 16.10 on it and both work fine without 
any changes or settings.

But there is an issue with installation.
I prepared  the HDD from windows, with one partition for windows and a second for Lubuntu,  (as RAW because the only option for files while partitioning was NTFS), leaving a space of around 10 GB non allocated for data storage.
During installation, in partitioning menu i chose &#8216;something else&#8217;  instead of &#8216;install alongside with windows&#8217;.
When i chose the disk/partition (E)designed for Lubuntu, and set root files, ext4 and mount point, /:E  installation didn&#8217;t go further and asked me to make corrections. It seems there is a problem with swap space ?.
What i need is a dual boot system with windows in front(as secondary option) and Lubuntu as the main os. That is why i created the two partitions, unless the raw files in the 2nd partition is not appropriate for installation.
I red this article before installing but with no much luck, [https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu)
What are the options i have on this subject ?
Thank you

---

### Post by sudodus on 2017-04-17
I suggest that you ***try with gparted when booted from a Lubuntu live system*** (created from a Lubuntu desktop iso file). You can create an ext4 file system for the partition to become the root partition and format the other partition as linux swap. Then use these partitions from 'Something else' in the installer (you need not format them again).

If this does not work, there might be a problem with the partitions themselves, for example that Windows created dynamic parttions, that do not work with linux. In this case you should

1. use Windows to remove the [dynamic] partitions,
2. reboot into Lubuntu live system,
3. create partitions and
4. after that create an ext4 file system for the partition to become the root partition and
5. format the other partition as linux swap.
6. Finally, start the installer and use these partitions from 'Something else'.

---

### Post by timomak on 2017-04-18
Thank you very much for the support.
The next couple of days i will go on and let you know about.

---

### Post by timomak on 2017-04-20
Hi Sudodus,
And finally, installation successful !
I followed your instructions as well from this post [https://ubuntuforums.org/showthread.php?t=1872303](https://ubuntuforums.org/showthread.php?t=1872303).
-Dual boot is activated
-cpu usase : 1 % in idle, around 41 % when video is playing.
-Ram usage:152 % in idle, around 430 MB when video is playing.

First off all i would like to thank you for the support, as well as the other people in this forum.

Basically i made some mistakes which i will state below.
I will start with a conclusion: I assume that unsuccessful trial session with the acer notebook was a short of hardware failure either with ram modules, motherboard or both. Although the machine is working with win xp and win7, operation is somehow slow which is probably due to those issues. However, I suppose that possible installation would be successful but i didn&#8217;t go further. Perhaps i will check this when time available.

Now, installation was done twice (although the first was also successful) in order to reset partition volumes . But i have some doubts about possible mistakes i did  during the second install:
1. Swap. After partitioning as you described, and during installation, i set root files ext4 and mount / but was no other option for swap, which was only set before, during partitioning. Is swap installed to its place or to the root partition?
2. Bootloader. In the final screen for bootloader instead of choosing the HDD for than, i chose again the root partition and pressed &#8216;install&#8217;. Is bootloader installed correctly in this case or also installed in root partition? 
Note:Before second installation, i deleted the partitions created before (with lubuntu installed) and restarted the proccedure from the beginning. In the meantime i tried to boot windows, but couldn&#8217;t start, as bootloader was erased (normal?). After installing again Lubuntu dual boot option is effective. 
Is there a way to verify the above or better reinstall ?
Here are a few screenshots.
I couldn't edit photos. i clarify here: partitioning scheme photo no 214610
                                                         a look at the disks      ''         ''  125125
                                                         the system folders     ''         ''  124741

Thank you in advance

---

### Post by sudodus on 2017-04-21
> **timomak said:**
> Hi Sudodus,
And finally, installation successful !
I followed your instructions as well from this post [https://ubuntuforums.org/showthread.php?t=1872303](https://ubuntuforums.org/showthread.php?t=1872303).
-Dual boot is activated
-cpu usase : 1 % in idle, around 41 % when video is playing.
-Ram usage:152 % in idle, around 430 MB when video is playing.

First off all i would like to thank you for the support, as well as the other people in this forum.

Basically i made some mistakes which i will state below.
I will start with a conclusion: I assume that unsuccessful trial session with the acer notebook was a short of hardware failure either with ram modules, motherboard or both. Although the machine is working with win xp and win7, operation is somehow slow which is probably due to those issues. However, I suppose that possible installation would be successful but i didn’t go further. Perhaps i will check this when time available.

Now, installation was done twice (although the first was also successful) in order to reset partition volumes . But i have some doubts about possible mistakes i did  during the second install:
1. Swap. After partitioning as you described, and during installation, i set root files ext4 and mount / but was no other option for swap, which was only set before, during partitioning. Is swap installed to its place or to the root partition?
2. Bootloader. In the final screen for bootloader instead of choosing the HDD for than, i chose again the root partition and pressed ‘install’. Is bootloader installed correctly in this case or also installed in root partition? 
Note:Before second installation, i deleted the partitions created before (with lubuntu installed) and restarted the proccedure from the beginning. In the meantime i tried to boot windows, but couldn’t start, as bootloader was erased (normal?). After installing again Lubuntu dual boot option is effective. 
Is there a way to verify the above or better reinstall ?
Here are a few screenshots.
I couldn't edit photos. i clarify here: partitioning scheme photo no 214610
                                                         a look at the disks      ''         ''  125125
                                                         the system folders     ''         ''  124741

Thank you in advance

There is swap according to your screenshots.

The bootloader should be installed to the (head of) drive /dev/sdx, not to a partition /dev/sdxn. But it works, so somehow you got it right.

please mark the thread as SOLVED

---

### Post by timomak on 2017-04-21
Perfect. [IMG]https://ubuntuforums.org/images/icons/icon6.png[/IMG]

---

