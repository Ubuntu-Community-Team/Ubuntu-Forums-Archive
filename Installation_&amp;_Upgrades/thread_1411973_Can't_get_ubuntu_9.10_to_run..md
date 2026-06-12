---
title: "Can't get ubuntu 9.10 to run."
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by Jimmy1 on 2010-02-20
I am trying to use the ubuntu 9.10 live cd but it will not load up. After I select the boot ubuntu with no change to my computer it goes to a black screen with a white ubuntu logo that flashes for a few secs and then it just freezes(stops and does nothing). I have left it sit there for a few mins and it does nothing. I have checked the Md5 of the file and it's fine.

I have been trying to use ubuntu and other linux OS's on this computer for a while and can't get any of them to work. Any help would be greatly appreciated.

Here are the spec's of my computer.

1GB of RAM
3.06GHz processor(Intel pentium 4)
NVIDIA GeForce FX 5500 256MB graphics card

---

### Post by darkod on 2010-02-20
It might be an issue with the graphics driver. At the main menu hit F4 and select like Safe Graphics, then again Try Ubuntu if you need to. See if that will boot the live desktop.

---

### Post by Jimmy1 on 2010-02-20
Thanks for the help. :)


After I did that I was able to get past the white logo (still not able to load the Desktop) to a black screen, after it sat there for a few mins it gave this error code.

```
init: line 1: can't open /dev/sdb: no medium found
init: line 1: can't open /dev/sdc: no medium found
init: line 1: can't open /dev/sdc: no medium found
init: line 1: can't open /dev/sdd: no medium found
init: line 1: can't open /dev/sdd: no medium found
init: line 1: can't open /dev/sde: no medium found
init: line 1: can't open /dev/sde: no medium found

Mount: mounting /dev/sr0 on /cdrom failed: invalid argument
Mount: mounting /dev/sda1 on /cdrom failed: invalid argument

init: line 1: can't open /dev/sdb: no medium found
init: line 1: can't open /dev/sdb: no medium found
init: line 1: can't open /dev/sdc: no medium found
init: line 1: can't open /dev/sdc: no medium found
init: line 1: can't open /dev/sdd: no medium found
init: line 1: can't open /dev/sdd: no medium found
init: line 1: can't open /dev/sde: no medium found
init: line 1: can't open /dev/sde: no medium found

mount: mounting /dev/sr0 on /cdrom failed: invailid argument

BusyBox v1.13.3 (ubuntu 1:1.13.3-1ubuntu7) built-in shell(ash)
enter 'help' for a list of built-in commands

(initramfs) Unable to find a medium containins a live file system
```

---

### Post by Jimmy1 on 2010-02-22
Anyone know what those errors mean and how to fix it?

---

### Post by DawieS on 2010-02-22
To me those messages would mean that Ubuntu has partially loaded, and then failed to see any hard drives, or even the CD ROM from which it has loaded. This could be caused by a number of reasons, of which a few examples are:

- Incorrect hardware BIOS settings.
- Overclocking beyond working limits.
- Corrupt memory sticks (RAM).
- Incompatible hardware not supported by Ubuntu drivers.
- Incorrect connections on the motherboard (For example, CD ROM pinned as SLAVE, when in fact it is the ONLY device on the cable, and thus should be MASTER).

I would suggest that you eliminate the possible causes in the following sequence:
- Check the integrity of the Desktop Live CD (You have already)
- Check your RAM by running 'memtest' (on the Grub menu).
- Check all connections on the motherboard for validity.
- Experiment with BIOS settings (choose fail safe options instead of optimised/overclocked, enable SMART on hard drives, etc).

If you still have problems, research the compatibility of your hardware with Linux. This is fairly unlikely to be the problem, unless you have some weird motherboard...

---

### Post by Jimmy1 on 2010-02-23
> Check your RAM by running 'memtest' (on the Grub menu).
It checked out fine.
> Check all connections on the motherboard for validity.
I believe that is good.
> Experiment with BIOS settings (choose fail safe options instead of optimised/overclocked, enable SMART on hard drives, etc).
I changed a few things and it did not help, so I changed the settings back to what they were.
> If you still have problems, research the compatibility of your hardware with Linux.
I think it may have to do with my NVIDIA GeForce FX 5500 graphics card, I did some looking on that and it seems like it could cause some problems since I still have the onboard graphics card. What I think I am going to try is to plug my monitor into my onboard graphics card and then try ubuntu and see if it works and go from there.


Thank you :)

---

### Post by nikkkko on 2010-02-23
Hi,

I have the same problem and I don't think it's the graphics driver.  I get to the screen which allows me to choose to run live, install etc., hit live and ... nothing.  Eventually the cd just spins down.

The cd is fine, tested on other systems, and the computer was purchased from Dell with ubuntu pre-installed, (model XPS M1330), so you would imagine there would be no problem with the hardware.

---

### Post by darkod on 2010-02-23
> **nikkkko said:**
> Hi,

I have the same problem and I don't think it's the graphics driver.  I get to the screen which allows me to choose to run live, install etc., hit live and ... nothing.  Eventually the cd just spins down.

The cd is fine, tested on other systems, and the computer was purchased from Dell with ubuntu pre-installed, (model XPS M1330), so you would imagine there would be no problem with the hardware.

Even if you don't suspect the driver, no harm in trying safe mode. At the main menu hit F4 and select Safe Graphics. Not sure if you need to select Try Ubuntu again after that (never needed to use it). If you do need to, just select Try ubuntu and see if the live desktop loads.
You can also try to install from there hitting the Install icon on the desktop while you are still in safe graphics mode.

---

### Post by SeePU on 2010-02-23
What program or utility did you use to create the Live CD in the first place?  The OP's hardware is standard and not too old so it isn't a compatibility problem.   Although, the Nvidia hardware is getting a bit old, it is still supported by the binary driver?

The OP will probably want safe graphics mode anyway unless 9.10 defaults to VESA mode - and I believe it doesn't!  

As for the problems booting, it's possible there's a hardware problem but more often than not, it's usually something else.  OP, do you use Windows on that computer?  Can you boot normally usually?

I suspect the Live CD is faulty but without more info, it's all speculation.  Can you try that CD on another computer.   It's good to use process of elimination in a case like this, imho. :)

---

### Post by Jimmy1 on 2010-02-23
> What program or utility did you use to create the Live CD in the first place?
InfraRecorder.
> do you use Windows on that computer? Can you boot normally usually?
Yes I have Windows XP on it and it boots fine. If I can get ubuntu working I will set up a dual boot with it.
> Can you try that CD on another computer.
I just tryed it on 2 other computers and it loads up with no problems. I also have a virtual machine (VirtualBox) on the computer that I am trying to get ubuntu to work on, and I can use ubuntu (and any other linux OS that I have tryed) with no problem on it.



I tryed to switch my monitor back to the onboard card and my monitor could not pick anything up. Do I have to switch anything in the BIOS to try out my onboard card again? When I installed the Nvidia card a few years ago I did not have to change anything in the BIOS.

---

### Post by darkod on 2010-02-23
> **Jimmy1 said:**
> InfraRecorder.

Yes I have Windows XP on it and it boots fine. If I can get ubuntu working I will set up a dual boot with it.

I just tryed it on 2 other computers and it loads up with no problems. I also have a virtual machine (VirtualBox) on the computer that I am trying to get ubuntu to work on, and I can use ubuntu (and any other linux OS that I have tryed) with no problem on it.



I tryed to switch my monitor back to the onboard card and my monitor could not pick anything up. Do I have to switch anything in the BIOS to try out my onboard card again? When I installed the Nvidia card a few years ago I did not have to change anything in the BIOS.

Usually you would need to select in BIOS whether you are using the onboard video or a card.

---

### Post by ImTheBatman on 2010-02-23
As I said in another thread, I have the same problem as OP. What I managed to find out so far: 1.When loading through CD: a.If I just try to boot Ubuntu normally the screen turns black and nothing happens b.If I set my monitor to VGA (it's usually on DVI) I can see a bunch of colorful lines all over my screen, shaking c.If I use safe graphics I get to a command prompt but the whole screen is flashing  2.When loading through USB: a.same as 1.a b.same as 1.b c.I cannot find how to do safe graphics, F4 doesn't do anything and the advanced options menu is empty.

---

### Post by pmozingo on 2010-02-23
I can't get it to run either. I burned the .iso at 4X speed, tried it with my Windows XP computer and my Windows Vista computer. Locked both computers up and had to pull the plug on both of them. After reading a few posts on here I'm just about convinced it's a bad download. I'll stick with Windows for now.

---

### Post by Jimmy1 on 2010-02-23
> Usually you would need to select in BIOS whether you are using the onboard video or a card.
Ok I found the option for that but still have a quick question. After I change the primary video adapter from PCI to onboard do I let my Windows XP load or save the settings in the BIOS and shut my computer down right away and plug my monitor into the onboard card? 
Sorry I have never done this before.

Thanks

---

### Post by darkod on 2010-02-23
> **Jimmy1 said:**
> Ok I found the option for that but still have a quick question. After I change the primary video adapter from PCI to onboard do I let my Windows XP load or save the settings in the BIOS and shut my computer down right away and plug my monitor into the onboard card? 
Sorry I have never done this before.

Thanks

You have to save settings to BIOS or they will be lost. That automatically restarts the PC. Change the cable while it is restarting.

---

### Post by Jimmy1 on 2010-02-23
Thank you, got it switched over to the onboard fine. After I switched to the onboard card I tryed ubuntu, and it loaded up with no problems. :)

So I take it the problem is something with the Nvidia card, if I install ubuntu is there anything I can do to get the Nvidia card working with it? Do some kind of update or download the drivers for it?

---

### Post by darkod on 2010-02-23
> **Jimmy1 said:**
> Thank you, got it switched over to the onboard fine. After I switched to the onboard card I tryed ubuntu, and it loaded up with no problems. :)

So I take it the problem is something with the Nvidia card, if I install ubuntu is there anything I can do to get the Nvidia card working with it? Do some kind of update or download the drivers for it?

Usually it should be fine. In most cases the right driver is detected and will be offered to install it. The problem is to reach that stage if you don't have alternative video card. :)

---

### Post by Jimmy1 on 2010-02-23
Ok, thank you very much for your help. I will try installing it shortly. :)

---

### Post by nikkkko on 2010-02-23
Hey Jimmy - happy to see you got it working.

Sadly, no joy for me.  

I burned the disk using brasero on my xps m1330, currently running 9.1, but over which I want to reinstall to get rid of the Dell partition and all the nasty upgrades and half installs I've done over the last couple of years. (I just cannot get wine to run any more, no matter what).  The graphics are 128MB Nvidia GeForce Go 8400 and this laptop was bought new in 2007. 

I decided tonight to reburn the cd but brasero gave me errors twice, so I switched to another machine running K3B.  This burned fine, but gives me the same problem in that I cannot get beyond the menu options, even in safe mode.  The live cd works on neither machine, the second one being a much older desktop pc, although with relatively recent GeForce 6200 graphics.

I am now re-downloading, just in case, so I'll repost when I'm done.  

For what it's worth, I remember downloading a 9.1 version of kubuntu a while back and having the same problem on this machine, although it loaded fine on an ancient toshiba portege.

---

### Post by darkod on 2010-02-23
> **nikkkko said:**
> Hey Jimmy - happy to see you got it working.

Sadly, no joy for me.  

I burned the disk using brasero on my xps m1330, currently running 9.1, but over which I want to reinstall to get rid of the Dell partition and all the nasty upgrades and half installs I've done over the last couple of years. (I just cannot get wine to run any more, no matter what).  The graphics are 128MB Nvidia GeForce Go 8400 and this laptop was bought new in 2007. 

I decided tonight to reburn the cd but brasero gave me errors twice, so I switched to another machine running K3B.  This burned fine, but gives me the same problem in that I cannot get beyond the menu options, even in safe mode.  The live cd works on neither machine, the second one being a much older desktop pc, although with relatively recent GeForce 6200 graphics.

I am now re-downloading, just in case, so I'll repost when I'm done.  

For what it's worth, I remember downloading a 9.1 version of kubuntu a while back and having the same problem on this machine, although it loaded fine on an ancient toshiba portege.

I'm not yet sure when to use this, but it can't hurt. Boot the same cd again, at the menu highlight the Try Ubuntu option but don't hit Enter. Hit 'e' instead. It will show you the boot line(s) of commands. In the line starting with linux.... add acpi=off at the end. Hit Ctrl + X to boot.

You can move the cursor with the arrows to enter the above text where needed. See if it can help boot the live desktop.

---

### Post by nikkkko on 2010-02-24
I started again from scratch, new download, burned with K3B, (which I much prefer to Brasero), and this time it works.  

I can't explain why it didn't work before - perhaps it was a bum download and I read the checksum wrong.  Perhaps the burner in my Dell is less than solid, perhaps I have a dodgy stock of blank cd's. Actually I have no stock of cd's now as I went through most of them last night.

Anyway, thanks for your help and sorry the solution is so banal!

---

### Post by Jimmy1 on 2010-02-24
Ok, I got ubuntu to install with no problems. Dual boot works fine, so then I booted back into ubuntu installed the Nvidia driver it showed, rebooted my computer and then ubuntu would not start. So I switched my monitor back to my Nvidia card and it still would not boot. After I installed the driver I could not start ubuntu with the onboard card or the Nvidia card.

So I wiped the ubuntu harddrive clean and then reinstalled it again with no problems. This time I did not install the driver, so I tryed using the Nvidia card again and it would not work. Right now the only way I can get into ubuntu is by using the onboard card.

Did I do something wrong? And is there anything I can do to try to fix this?

---

### Post by darkod on 2010-02-24
Sounds like you did everything right. Give me some time to look into using FX 5500 with ubuntu.
Also, in case we find another driver, it would be helpful to know if you can at least install it in recovery mode. Can you try booting connected to the FX 5500 card, but in the grub menu (if you get that far) select the recovery mode entry, not the normal one.
See if that will load the command prompt, that's what you get in recovery mode.
At the command prompt you can issue 'reboot' or 'shutdown' command when you want to finish.

---

### Post by darkod on 2010-02-24
This is an old thread, but see if it helps with your FX 5500:
[http://ubuntuforums.org/showthread.php?t=33142](http://ubuntuforums.org/showthread.php?t=33142)

If you can boot the recovery mode entry ignore the PREWORK: section and start with
1. Figure out what PCI port....

Hopefully it works for you.

---

### Post by Jimmy1 on 2010-02-24
Thank you for your continued help.


OK, I think I did all of that right. After I rebooted ubuntu I changed the BIOS back to my Nvidia card and plugged my monitor back to the Nvidia card and tryed starting ubuntu. It still will not load up, but it did give my this error.
```
Mount: Mounting /sys on /root/sys failed: no such file or directory
Mount: Mounting /dev on /root/dev failed: no such file or directory
Mount: Mounting /sys on /root/sys failed: no such file or directory
Mount: Mounting /proc on /root/proc failed: no such file or directory

target filesystem doesn't have /sbin/init
no init found. Try passing init=bootarg.
```
After that code it put me back into the BusyBox like before.

While using my Nvidia card I can not get into ubuntu recovery mode before or after trying the steps from your last reply. I can get into it with no problem while using the onboard card.

> but in the grub menu (if you get that far)
I can get to that no problem using either card.

---

### Post by darkod on 2010-02-24
If the Nvidia is not letting you into recovery mode too, that sucks. I had another idea, but you need at least recovery mode and the Nvidia card to be enabled in BIOS, to try to install a driver. :(

---

### Post by darkod on 2010-02-24
OK, next idea.

Plug the monitor into the Nvidia, and of course enable it in BIOS. You said it shows the grub menu. The ubuntu normal entry should be highlighted by default, if it's not move the bar onto it. Don't press Enter. Hit 'e' instead.

It will show the commands to boot ubuntu. In the line starting with linux... at the end add vga=771. You can move the cursor with the arrows keys.

Hit Ctrl + X to boot. If we have any luck, it will allow you to boot the desktop with basic resolution (it will probably look like ancient but it's a start).

---

### Post by darkod on 2010-02-24
Another next idea.

Boot using the onboard card into ubuntu.

Go here:
[http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)

and select your card family ( 5 FX ) and Linux 32bit or 64bit, then click search. It should offer the driver version like 173.14.25. Download it. After it finishes it will probably be in your Downloads folder. Move it on desktop.

Then follow the instruction from here:
[http://ubuntuforums.org/showpost.php?p=7465688&postcount=23](http://ubuntuforums.org/showpost.php?p=7465688&postcount=23)

starting from 'now hit CTRL + ALT + F1', because you already downloaded your own driver.

At the end during the reboot don't forget to switch the cable to Nvidia and set the BIOS right. Hopefully that will add the Nvidia driver which is correct for 5500 and it should work.

---

### Post by headshottjosh on 2010-02-25
Hey i cant get 9.10 to run successfully, i have a similar problem as in when i try and install my comp randomly restarts itself.

I have amd 6000+ 
9800gtx 
4gb dd2 ram dual channel 

it restarts itself at any stage or my installation, i have managed to install it 2 times and every time it still restarts randomly like 2- 5min after boot. I have tried installing all updates through snaptic package manager still restarts though the hole process...
so i though fine lets install graphics card driver... tried version 180 the recommended installation, I restarted my comp for once and i booted into a black screen that is non responsive to anything, tried it again because others have had a similar problem, so i tried on my second installation success to do graphics driver 173. with again no success.

Any ideas coz im fresh out and im about to explode!

---

### Post by darkod on 2010-02-25
> **headshottjosh said:**
> Hey i cant get 9.10 to run successfully, i have a similar problem as in when i try and install my comp randomly restarts itself.

I have amd 6000+ 
9800gtx 
4gb dd2 ram dual channel 

it restarts itself at any stage or my installation, i have managed to install it 2 times and every time it still restarts randomly like 2- 5min after boot. I have tried installing all updates through snaptic package manager still restarts though the hole process...
so i though fine lets install graphics card driver... tried version 180 the recommended installation, I restarted my comp for once and i booted into a black screen that is non responsive to anything, tried it again because others have had a similar problem, so i tried on my second installation success to do graphics driver 173. with again no success.

Any ideas coz im fresh out and im about to explode!

According to the Nvidia website you need the 190.53 driver. If your recovery mode works, there are few options.

1. Boot in recovery mode and install the EnvyNG package which can help you install the 190.53 driver I guess (I have ATI so haven't used it for Nvidia drivers).

2. Download the driver yourself from Nvidia using the ubuntu live desktop, save it in your home folder inside your hdd install, then boot the hdd install in recovery mode and install the driver.

What do you feel up to? :)

---

### Post by ImTheBatman on 2010-02-25
> **ImTheBatman said:**
> As I said in another thread, I have the same problem as OP. What I managed to find out so far: 
1.When loading through CD: 
a.If I just try to boot Ubuntu normally the screen turns black and nothing happens 
b.If I set my monitor to VGA (it's usually on DVI) I can see a bunch of colorful lines all over my screen 
c.If I use safe graphics I get to a command prompt but the whole screen is flashing 
2.When loading through USB: 
a.same as 1.a 
b.same as 1.b 
c.I cannot find how to do safe graphics, F4 doesn't do anything and the advanced options menu is empty.

I still didn't manage to solve my problem :( 
But I did try the same CD (and USB) and on a friend's computer and it worked, so it's not a problem with the download or the burning. Do you have any idea what can it be? I'm using Nvidia GeForce 7300 LE and the other computer had an onboard video card

---

### Post by tommcd on 2010-02-25
For anyone who is having problems running the live CD, when you boot the Ubuntu live CD and get to the second screen shown here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
The first thing you need to do is run the option that says "check disc for defects". This will at least rule out a bad CD as the source of your problems.

For the nvidia geforce 5500 card:
According to this page:
[http://www.nvidia.com/object/linux_display_ia32_173.14.25.html](http://www.nvidia.com/object/linux_display_ia32_173.14.25.html) (click on "supported products).
the 173 driver supports the 5500. This is confirmed by checking the nvidia driver in the Ubuntu repos for Ubuntu 9.10:
[http://packages.ubuntu.com/karmic/nvidia-glx-173](http://packages.ubuntu.com/karmic/nvidia-glx-173)
Note the gforce 5500 card is listed there. The 185 driver in the Ubuntu repos only lists the Quadro FX 5500 card:
[http://packages.ubuntu.com/karmic/nvidia-glx-185](http://packages.ubuntu.com/karmic/nvidia-glx-185)
So, to install and configure the 173 driver from the Ubuntu repos in the most fail safe method possible, see post #6 in this thread:
[http://ubuntuforums.org/showpost.php?p=8880093&postcount=6](http://ubuntuforums.org/showpost.php?p=8880093&postcount=6)
Just substitute 173 for 185 when installing the nvidia driver. This assumes that you are starting from a fresh install, and have not yet installed any nvidia drivers.

If none of this works, then I would install Ubuntu from the alternate install CD. This is a text based install CD that will avoid any graphics related problems with the live CD. Then install the 173 driver according to post #6 in the thread I linked to above for the geforce 5500 card.
Note that the alternate install CD is just for installing Ubuntu. It will not allow you to try Ubuntu in live CD mode.
Hope this manages to help somebody.

---

### Post by Jimmy1 on 2010-02-25
> It will show the commands to boot ubuntu. In the line starting with linux... at the end add vga=771.
It did not work, it just sat at a black screen.

> **darkod said:**
> Another next idea.

Boot using the onboard card into ubuntu.

Go here:
[http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)

and select your card family ( 5 FX ) and Linux 32bit or 64bit, then click search. It should offer the driver version like 173.14.25. Download it. After it finishes it will probably be in your Downloads folder. Move it on desktop.

Then follow the instruction from here:
[http://ubuntuforums.org/showpost.php?p=7465688&postcount=23](http://ubuntuforums.org/showpost.php?p=7465688&postcount=23)

starting from 'now hit CTRL + ALT + F1', because you already downloaded your own driver.

At the end during the reboot don't forget to switch the cable to Nvidia and set the BIOS right. Hopefully that will add the Nvidia driver which is correct for 5500 and it should work.
Didn't work, did the same thing as before when trying to install the driver. I can't get into ubuntu with the Nvidia card or the onboard card, however I can get into the recovery mode with the onboard if that could help anything.
Also it gives me a error when trying to load ubuntu with the Nvidia card after I did the driver download.
```
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768
Killed
```
Not sure if it helps, but my normal screen setting is 1600x900.

---

### Post by darkod on 2010-02-25
At this point of time, and since you tried so many different things, I think it's best to try to install a fresh install using the alternate cd, as tommcd said.
Then on the fresh install try installing the 173 driver as per that post #6 from the last link in his post.

---

### Post by Jimmy1 on 2010-02-25
Ok, I will go ahead and start downloading the file and try it. :)

---

### Post by ImTheBatman on 2010-02-25
> **ImTheBatman said:**
> I still didn't manage to solve my problem :( 
But I did try the same CD (and USB) and on a friend's computer and it worked, so it's not a problem with the download or the burning. Do you have any idea what can it be? I'm using Nvidia GeForce 7300 LE and the other computer had an onboard video card

So, anything that can solve my problem? I can't even get to a working shell.

---

### Post by darkod on 2010-02-25
> **ImTheBatman said:**
> So, anything that can solve my problem? I can't even get to a working shell.

Using the alternate install image either from a cd or usb stick should be OK for you too. After the install you will just add the necessary driver depending on your video card. Note that the alternate installer is text based but it's easy to work with.

---

### Post by ImTheBatman on 2010-02-25
> **darkod said:**
> Using the alternate install image either from a cd or usb stick should be OK for you too. After the install you will just add the necessary driver depending on your video card. Note that the alternate installer is text based but it's easy to work with.
EDIT: okay I found it. I need the same drivers as the guy above, right?

---

### Post by darkod on 2010-02-25
> **ImTheBatman said:**
> EDIT: okay I found it. I need the same drivers as the guy above, right?

If it's FX 5500, definitely yes. Even for other card, it can be the same driver because it supports manu. On the nvidia download page click on Supported Products and it will show all models supported by that driver.

---

### Post by headshottjosh on 2010-02-25
Thanks darkod i will try that tonight if i can get it successfully installed again. Does anyone know y my computer would constantly restarting thou? i use a windows cd to just reformat my comp then before windows starts installing i eject the disk and restart the computer ready for a fresh install of ubuntu. But i have never previously had the problem of my comp constantly restarting? when i am reinstalling or formatting with windows disk i have no problems at all so wondering if anyone can suggest wat it could be? i can only assume it would be the graphic driver but i have no solid evidence just wondering if this can be confirmed because i would be spending hours reinstalling linux and finally get the gcard driver installed and then the problem still be there?

---

### Post by tommcd on 2010-02-26
> **ImTheBatman said:**
> EDIT: okay I found it. I need the same drivers as the guy above, right?
For the 7300 LE I would use the 185 driver from the Ubuntu repos. The 7000 series of cards should be better supported with the 185 driver. The 190 driver from nvidia.com supports the 7300 LE:
[http://www.nvidia.com/object/linux_display_ia32_190.53.html](http://www.nvidia.com/object/linux_display_ia32_190.53.html)
The 190 driver is not in the Ubuntu 9.10 repos though. But the 185 from the repos should work fine. I was running a 7600GT (until the stupid fan died on it) with the 185 driver from the Ubuntu repos with no problems.

---

### Post by darkod on 2010-02-26
> **headshottjosh said:**
> Thanks darkod i will try that tonight if i can get it successfully installed again. Does anyone know y my computer would constantly restarting thou? i use a windows cd to just reformat my comp then before windows starts installing i eject the disk and restart the computer ready for a fresh install of ubuntu. But i have never previously had the problem of my comp constantly restarting? when i am reinstalling or formatting with windows disk i have no problems at all so wondering if anyone can suggest wat it could be? i can only assume it would be the graphic driver but i have no solid evidence just wondering if this can be confirmed because i would be spending hours reinstalling linux and finally get the gcard driver installed and then the problem still be there?

It's probably the video driver. When karmic came out in October (and I haven't used ubuntu before), the Try Ubuntu option was restarting my pc just before it loads the live desktop. I was trying to figure it out for days. Then I simply installed with the Install Ubuntu option and the process finished fine.
However, on the first boot it continued to restart my pc just before the login screen. I have onboard ATI HD3200.
I found instructions how to add EnvyNG in recovery mode and to install a driver with it, and it's working fine ever since. Including all kernel updates, etc. So most probably it's the driver doing the restarting.

PS. At least for my card this problem is already removed in lucid. I have tested the daily image of lucid which is of course still under development, and the Try Ubuntu option is loading the live desktop just fine. No more restarting.

---

### Post by Jimmy1 on 2010-02-27
I have ran into another problem, I am trying to use the alternate CD, however when I get to the part where I have to partition the harddrive it gives me this error when I try to write the changes.
```

The attempt to mount a file system ext4 in SCSI3 (0,0,0), partition #5 (sda) at / failed.
```
I am doing the same partition as I did with the Livd CD and it worked with no problems.

Not sure if it matters, but I am using the Nvidia card while trying this.

---

### Post by tommcd on 2010-02-28
> **Jimmy1 said:**
>  I am trying to use the alternate CD, however when I get to the part where I have to partition the harddrive it gives me this error when I try to write the changes.
```

The attempt to mount a file system ext4 in SCSI3 (0,0,0), partition #5 (sda) at / failed.
```
I am doing the same partition as I did with the Livd CD and it worked with no problems.

Not sure if it matters, but I am using the Nvidia card while trying this.
The partitions should not be mounted while partitioning the drive. 
Do you already have your partitions set up the way you want them? If so, then choose manual partitioning. Select your root partition as label mount point /.
Select "use as" as ext3 or ext4 or whatever you want.
Select "yes" to format.
If you had the Ubuntu partition set as bootable before, then select it as bootable now. If you have Windows on the first partition and it is set as bootable, then don't worry about this.
You could also choose to delete the problematic partition. Then recreate it as mount point root (/).
You could also try partitioning from a Parted Magic live CD first, before you install Ubuntu:
[http://partedmagic.com/](http://partedmagic.com/)
Parted Magic works very well in my experience. You can even browse the net (and install flash) and listen to music all from the live CD while it is partitioning your hard drive!
Set up your partitions the way you want them and format them with the Parted Magic live CD.
**Note**: If you have a separate home partition that has data on it that you wish to save, then **do not** format it with either the Parted Magic live CD or the Ubuntu alternate CD. Just choose the mount point /home. Select "use as" as whatever type partition it is (ext3 or ext4 or whatever). And select "no, do not format this partition".
Hope this helps. I have never had this problem with the alternate CD. I always use manual partitioning though.

---

### Post by Jimmy1 on 2010-03-02
I tryed the different things with the alternate CD and have got the same results.

I have reinstalled ubuntu 9.10 using the Live CD, and trying some of the things again that have been posted in this thread. When trying to boot ubuntu while using my Nvidia card I get this error.
```
usplash setting mode 1152x864 failed
usplash: Using mode 1024x768
Killed
```

However, if I edit the boot line and take out "splash" I will get this error.
**Note**
I did not copy everything from the start of the "Call trace", if you need it I will go back and get it all. This is just the last few lines.
```

[2.344009] EIP [<c026a9267>] ext4_iget+0x56/0x710 SS:ESP0068:efb65d9c
[2.344009] CR2: 00000000f79f5000
[2.344009] ---[end trace f1991aaecleu22f]---

[2.396020] USB 5-1: new full speed USB devices using uhci_hcd and address 2
[2.569292] USB 5-1:configuration #1 chosen from 1 choice
[2.680112] ieee1394: Host added: ID:BUS[0-00:1023] GUID[00e0180000ce8c6f]
```

---

### Post by tommcd on 2010-03-03
> **Jimmy1 said:**
> I tryed the different things with the alternate CD and have got the same results.
It would help here if you stated exactly what you tried from the alternate CD. 
> **Jimmy1 said:**
> 
I have reinstalled ubuntu 9.10 using the Live CD, and trying some of the things again that have been posted in this thread.
Have you installed any nvidia drivers after doing a clean install of 9.10 from the alternate CD?

I am assuming here that you have not yet installed any nvidia drivers.
Boot to recovery mode if you can. Install the nvidia 173 driver:
```
sudo apt-get install nvidia-glx-173
```
Then configure the driver:
```
sudo nvidia-xconfig
```
Then reboot with "sudo reboot".
It has been a while since I booted Ubutnu to recovery mode. You may not even need to use sudo with those commands from recovery mode. I don't think you do.
I am not sure why you are having such difficulties getting to the desktop with the nvidia 5500.

---

### Post by sam.reader on 2010-03-03
Firstly you have a decent configuration.
it should be able to run Ubuntu 9.10 without any problems
I suggest you try to make a Virtual Ubuntu installation first as many say it requires less configuration.
If there is no problem with it then its definitely you gig.

---

### Post by Jimmy1 on 2010-03-03
> It would help here if you stated exactly what you tried from the alternate CD.
Sorry about that, what I meant was that I tryed the things you said in your reply.
> The partitions should not be mounted while partitioning the drive.
Do you already have your partitions set up the way you want them? If so, then choose manual partitioning. Select your root partition as label mount point /.
Select "use as" as ext3 or ext4 or whatever you want.
Select "yes" to format.
If you had the Ubuntu partition set as bootable before, then select it as bootable now. If you have Windows on the first partition and it is set as bootable, then don't worry about this.
You could also choose to delete the problematic partition. Then recreate it as mount point root (/).
You could also try partitioning from a Parted Magic live CD first, before you install Ubuntu:
[http://partedmagic.com/](http://partedmagic.com/)
Parted Magic works very well in my experience. You can even browse the net (and install flash) and listen to music all from the live CD while it is partitioning your hard drive!
Set up your partitions the way you want them and format them with the Parted Magic live CD.
Note: If you have a separate home partition that has data on it that you wish to save, then do not format it with either the Parted Magic live CD or the Ubuntu alternate CD. Just choose the mount point /home. Select "use as" as whatever type partition it is (ext3 or ext4 or whatever). And select "no, do not format this partition".
Hope this helps. I have never had this problem with the alternate CD. I always use manual partitioning though. 



> Have you installed any nvidia drivers after doing a clean install of 9.10 from the alternate CD?
I can't get the alternate CD to install ubuntu yet, it gives me that error when I try to partition my hard drive.
> I am assuming here that you have not yet installed any nvidia drivers.
I have tryed installing the nvidia drivers, but that was with the Live CD.

---

### Post by tommcd on 2010-03-04
> **Jimmy1 said:**
> 
I can't get the alternate CD to install ubuntu yet, it gives me that error when I try to partition my hard drive.

What happens when you try to partition the hard drive with the alternate CD? Do you get errors? If so post them.
Have you tried using the Parted Magic live CD to partition the hard drive? If you do not have any data on the hard drive that you need to save, then just delete all the partitions using the Parted Magic CD or the alternate CD and start over. You should at least be able to delete the partition(s) that you plan to install Ubuntu on. Then just partition the newly created free space and install Ubuntu to that.

---

### Post by Jimmy1 on 2010-03-04
I got ubuntu working with my Nvidia card. :)
All I had to do was run **sudo update-initramfs -u** in the recovery mode. Thank you all very much for your help.

Also, does anyone know what this did to fix the problem?
**sudo update-initramfs -u**











For anybody having the same problem I was having here is what I did to fix it.



**Please note**, this is for a Nvidia graphics card, I am not sure if this will work with any other card.



I installed ubuntu on my computer using my onboard graphics card, once it is installed, install the recommended driver card ubuntu finds for you. After it installed open up a terminal and type **sudo nvidia-xconfig**.
Now you will need to find what PCI # your card has, in a terminal run **lspci** and find your graphics card PCI slot. After you have that run this from a terminal
**sudo gedit /etc/X11/xorg.conf**
Find the section "Device" and add this line to it.
**BusID "PCI:2:3:0"**
You will have to change the numbers based on your own PCI slot.

Again in terminal run this.
**sudo gedit /etc/modules**
Add this to the end of the file. **nvidia**

This next part I am not sure if you can do it in the terminal or not, I had to do it in recovery mode. So, restart your computer and at the Grub screen select the recovery mode. At the next screen select normal boot (the first option), once you log in type this.
**sudo update-initramfs -u**
Once it is done type.
**sudo reboot**

After you have done this you will need to go back in your BIOS and switch your graphics card back to your nvidia card, plug your monitor back to your nvidia card as well. After this I was able to use ubuntu.



Hopefully this will help someone who had the same problem as I did. :)

---

### Post by tommcd on 2010-03-05
> **Jimmy1 said:**
> 
All I had to do was run **sudo update-initramfs -u** in the recovery mode. Thank you all very much for your help.

Also, does anyone know what this did to fix the problem?
**sudo update-initramfs -u**
The update-initramfs command updates the intramfs. The initramfs is the initrd that you need to boot the kernel. You can see the initrd line in /boot/grub/grub.cfg, right under the kernel line (which is now the "linux" line in grub2). The initrd is in your /boot directory along with the kernel(s) you have there. The -u switch updates the existing initramfs. See this:
[http://ftp.parisc-linux.org/cgi-bin/man/man2html?update-initramfs+8](http://ftp.parisc-linux.org/cgi-bin/man/man2html?update-initramfs+8)
And for all the details:
[http://en.wikipedia.org/wiki/Initramfs#Initramfs_in_comparison_with_initrd](http://en.wikipedia.org/wiki/Initramfs#Initramfs_in_comparison_with_initrd)
Just out of curiosity, how did you arrive at that solution? I would not have thought that updating the initrd would be necessary for adding the nvidia graphics card.

---

