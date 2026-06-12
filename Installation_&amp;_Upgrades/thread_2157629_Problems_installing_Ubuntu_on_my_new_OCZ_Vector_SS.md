---
title: "Problems installing Ubuntu on my new OCZ Vector SSD"
date: 2013-06-26
forum: Installation &amp; Upgrades
---

### Post by mlu17 on 2013-06-26
Hey guys,

I have a Desktop PC in which I already have Windows 8 running on a OCZ Agility 3 SSD, my files are on a seperate 320GB Harddisk and now I bought a new OCZ Vector 128GB SSD to put Ubuntu on it.

The problem I have is that no matter which Version of Ubuntu I install on the OCZ Vector SSD (I tried 12.04, 13.04, 13.10), after the installation is done, and I boot into Ubuntu, my computer freezes and I can't do anything than restart it with the reset button on the front panel of my tower.

What I am not sure now is if this is a hardware issue in general (which I really really doubt, becaus Windows 8 is running perfectly) or maybe a graphics card issue? I have a Radeon HD 6850 from Sapphire. Could the SSD be corrupted or damaged?
Next thing which I am not sure about is the BIOS settings. Is it DEFINETELY nessecary to put BIOS to AHCI mode instead of IDE to make Ubuntu run on that SSD? 

Because the problem is, it is now set to IDE. As soon as I put it to AHCI, my Windows 8 SSD is not recognized correctly anymore and I can't boot it. This sure was my fault as I installed Windows 8 on the SSD while BIOS was set to IDE (I didn't know that before).

So, do you have any advices what I could try to get Ubuntu running on that 2nd SSD? Or where I should start to troubleshoot?
I had no chance to get any log files as the computer freezes completely and I couldn't either start a console or not even get into a text-console with Ctrl+Alt+F1

Regards,
Michael

Edit:
You might want to know that everything else works fine. I installed the bootloader of Ubuntu onto the new OCZ Vector SSD where Ubuntu is installed.
Then I went into Windows 8 and added a new Bootloader entry in the Windows Bootloader with EasyBCD which automatically looked up the Linux entry on the other SSD. 
So when I start my computer I can chose between Windows 8 or Ubuntu and Ubuntu starts totally normal when I chose it.
From now on when I see the Desktop sometimes the screen flickers a little and I still can work on it. But after 2-3 more minutes some windows get dark like they are stuck and then the whole computer freezes.
I also sometimes got a pop-up message where it says that compiz got killed by signal 7.

If you need any more info please tell me, I try to provide it then.

Edit2:
I also installed the Radeon HD 6XXX drivers from the amd.com support site but no change of the circumstance.

---

### Post by TheFu on 2013-06-26
I dno't know anything about anything, but doesn't Win8 require the use of UEFI?  Are you certain there aren't any Ubuntu requirements around using a UEFI BIOS that you've missed?

Google found this: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Hopefully, some of the other guys with UEFI experience will jump in and help now. I've seen many posts on that topic in these forums.

---

### Post by mlu17 on 2013-06-26
thanks for your reply.

I don't have UEFI. Btw my mobo is a Gigabyte GA-MA785GT-UD3H rev 1.0 
I upgraded my Windows 7 to Windows in online mode. 
What wonders me is that everything went fine during the installation. no errors at all. all disks get recognised and so on. even the normal boot action is totally normal. but I'm to inexperienced to know if my problem still could occur due to wrong bios settings.

I'll definitely take a look to your link and wait for some other helpful guys to jump in like you said.

Regards, 
Michael

Edit: Okay, I just put the Bios to AHCI mode and installed Ubuntu 12.04 on my OCZ Vector SSD.
After the installation and the first boot after about 2 minutes the computer again freezed completely.
I rebooted the computer and when I was at the desktop again, I received a blackscreen with a kernel panic.
Picture attached, I hope you guys can read it.
[ATTACH=CONFIG]244189[/ATTACH]

---

### Post by oldfred on 2013-06-26
Only systems with pre-installed Windows 8 have UEFI with secure boot. 

If you install Windows (or Ubuntu) yourself,  you can install in either UEFI or BIOS mode depending on if hardware also supports UEFI. But both systems must be installed in the same boot mode.

Seems like a video issue, but it may also need other boot parameters? If you did not have AHCI set when you installed Windows you may need to add the AHCI drivers before resetting BIOS. I thought AHCI was required to support trim but some recently said no. So now I am not sure.

I only have nVidia, but have some links to more info on AMD.

       [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by mlu17 on 2013-06-26
Hi oldfred,

thank you for your reply.

AHCI is working properly now. I uncluded the AHCI drivers before installing Ubuntu on the SSD.

The problem is, I don't even have the chance to install the amd drivers because the system freezes before. So what are my choices?

---

### Post by oldfred on 2013-06-26
Can you use nomodeset or recovery mode?

---

### Post by mlu17 on 2013-06-26
I tried to set nomodeset with pressing "e" while I see the boot menu of Ubuntu.
But then it looked like this:
[ATTACH=CONFIG]244198[/ATTACH]

I then tried recovery mode and archived a Xorg logfile.
Here it is, I hope it gives you a hint whats going wrong here :/ I hope I can attach a .zip file
[ATTACH]244199[/ATTACH]

---

### Post by oldfred on 2013-06-26
I see this error but have not looked a Xorg files for years. My nVidia just works (once I install the proprietary driver).

(EE) Failed to load module "fglrx" (module does not exist, 0)

So you do not have the ATI driver installed.

---

### Post by mlu17 on 2013-06-26
Is there a way to install the driver in recovery mode or somehow else?

---

### Post by oldfred on 2013-06-26
I have seen several alternatives, but I only have nVidia so I not know what is correct or if it varies depending on version.
If from recovery mode you can get to command line:

       Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)
sudo apt-get install fglrx
#sudo aticonfig --initial -f
sudo aticonfig --adapter=all --initial
After reboot to get Catalyst Control Center
sudo apt-get install fglrx-amdcccle

And I have seen this:

 sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-headers-generic
sudo apt-get install fglrx-updates

---

### Post by mlu17 on 2013-06-27
Hi oldfred,

thank you again for your reply.

I'll give it a try when I'm home. 
Only concern I have is to get my wifi working while in recovery mode. 
I unfortunately don't have access to a wired network.

I'll report back.

Edit:
@oldfred
You have seen my screenshot in my last post when I turned nomodeset on in grub.
Does this mean that nomodeset does simply not work on my computer or that I just missed something?
Would it make sense to install Ubuntu from the scratch witch nomodeset enabled to avoid the graphics problems and then install first the ati drivers?

---

### Post by oldfred on 2013-06-27
I thought nomodeset worked as it forces it to stay in a default mode that supposedly works. Or more like liveCD.

I have noticed the newer versions use nomodeset on the recovery mode.

So I so not know why you got the screen you got?

You may do better with a new thread with your model AMD & video issue in the title, so those that know your type of video will respond.

---

### Post by mlu17 on 2013-06-27
Okay thank you.
Should I also post a link to this thread in the post?
Or would it make sense to switch to start from onboard graphics in bios, install the amd drivers and then switch back to PCI graphics?

---

### Post by oldfred on 2013-06-27
You can always post link but best to give most up to date info, so those that may help have the best info without having to read lots of unrelated detail.

Do you also have dual graphics? And can you set that in BIOS? Include that info as it is important, but I do not know much about it.

---

### Post by mlu17 on 2013-06-28
I have a MA-785GT-UD3H rev 1.0 Motherboard from Gigabyte which has a integrated graphic chip ([COLOR=#434343][FONT=Arial]ATI Radeon HD 4200) and I have an extra PCI-E Sapphire Radeon HD 6850 graphic card.
In Bios I can say which one should be first initialised. So if I have my monitor connected to my PCI-E graphic card (which it normally is) I set the Bios to first initialise the PCI-E graphics. But I would also set it to the internal onboard graphic chip and plug the monitor in there.
But both are Radeons I just noticed :) So no clue if it makes a difference at all.

[/FONT][/COLOR][COLOR=#434343][FONT=Arial]I marked this post as solved as you assumed its a graphic card problem and I should create a new post.
Thanks for you help so far, I appreciate it.[/FONT][/COLOR]

---

