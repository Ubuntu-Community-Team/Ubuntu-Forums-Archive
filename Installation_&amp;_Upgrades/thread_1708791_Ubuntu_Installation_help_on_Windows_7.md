---
title: "Ubuntu Installation help on Windows 7"
date: 2011-03-17
forum: Installation &amp; Upgrades
---

### Post by cfree on 2011-03-17
[LEFT][/LEFT]I am trying to get Ubuntu installed on my laptop that is already running Windows 7. I want to dual boot. I have downloaded the cd and tried the Windows installer. When I use the Windows installer it reboots then I have the option to boot Ubuntu and I do so but it tells me that it is installing but just has a blinking underscore symbol. It does this for both the CD and the installer. I let it run for like 10 mins before I cut it off because it seems like it freezes just the underscore symbol blinking. Is this normal and can it take a while for it to set up while just displaying the underscore symbol? :confused:

---

### Post by nigou11 on 2011-03-17
What is this? Don't understand the computer program! Begin to learn these machinery

---

### Post by Dutch70 on 2011-03-17
> **nigou11 said:**
> What is this? Don't understand the computer program! Begin to learn these machinery

What kind of answer/help is that? This **is** a help & support forum. [-X

cfree, I believe you are talking about using Wubi to install Ubuntu inside of windows. If you are, can you not download the .exe, save it to your desktop and run it as administrator? 

That's how I installed it on my g/f computer. 

You can download the .exe from here...
[[COLOR="Blue"]http://www.ubuntu.com/desktop/get-ubuntu/windows-installer[/COLOR]]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer")

---

### Post by cfree on 2011-03-17
> **Dutch70 said:**
> What kind of answer/help is that? This **is** a help & support forum. [-X

cfree, I believe you are talking about using Wubi to install Ubuntu inside of windows. If you are, can you not download the .exe, save it to your desktop and run it as administrator? 

That's how I installed it on my g/f computer. 

You can download the .exe from here...
[[COLOR="Blue"]http://www.ubuntu.com/desktop/get-ubuntu/windows-installer[/COLOR]]("http://www.ubuntu.com/desktop/get-ubuntu/windows-installer")
 
Ok thanks man yeah im with you what was the other guy talking about though. But anyways thanks for the help :D

---

### Post by Dutch70 on 2011-03-17
> **cfree said:**
> Ok thanks man yeah im with you what was the other guy talking about though. But anyways thanks for the help :D

Ok, let us know how it works out for you. 

Best regards

---

### Post by cfree on 2011-03-17
> **Dutch70 said:**
> Ok, let us know how it works out for you. 

Best regards
yeah it is still doing the same thing. When i install it and reboot it gives me the option of win7 or Ubuntu and i go into Ubuntu and it says it is installing then says hit escape for more options and has a 5 sec counter. Then it proceeds with a _ symbol just blinking forever. Any suggestions? Oh and i tried the Wubi and gave me the same results as the CD

---

### Post by Dutch70 on 2011-03-18
I was hoping someone with more knowledge would answer, but since they didn't. 
Have you tried choosing 'nomodeset" at start up? 

No idea how to do that with Wubi, but that's what people generally do when they have this problem with a typical install. Maybe you can find something with Google, now that you know what to look for. 

You may want to check this thread...
[[COLOR="Blue"]Wubi Megathread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1639198")

good luck

---

### Post by bcbc on 2011-03-18
This post explains how to set nomodeset and other kernel boot options. [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

For the initial wubi install see post #8. After the wubi install it's the same as post #1 - even though it says "(not for wubi)"

If nomodeset doesn't help, then post back with your machine brand/model/graphics card. Usually there's someone else who's found out how to install for that particular machine and it's generally easy to search on that and find a solution.

---

### Post by carolinabranden on 2011-03-18
> **bcbc said:**
> This post explains how to set nomodeset and other kernel boot options. [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

For the initial wubi install see post #8. After the wubi install it's the same as post #1 - even though it says "(not for wubi)"

If nomodeset doesn't help, then post back with your machine brand/model/graphics card. Usually there's someone else who's found out how to install for that particular machine and it's generally easy to search on that and find a solution.




I myself have Windows 7 64-bit. Don't use Wubi. Keep an extra computer handy in case something goes wrong or you get confused during the installation. This is not a Windows OS after all. Below is a rough rundown of how to install Linux via CD/DVD Rom.

**1.**  You'll need a [[color="#8B0000"]blank partition[/color]](http://windows.microsoft.com/en-US/windows-vista/Can-I-repartition-my-hard-disk) on your HDD to install Linux on. Either shrink your existing volumes or purchase a separate HDD. 
Tip: Don't delete NTFS partitions while you're installing your distro. lol 
**2.**  Have a blank CD/DVD or [[color="#8B0000"]prepped[/color]](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer.exe) USB flash drive ready.
**3.**  Download then install [[color="#8B0000"]7-zip[/color]](http://www.7-zip.org/) utility tool  [[color="#8B0000"]32-bit[/color]](http://downloads.sourceforge.net/sevenzip/7z920.exe) or [[color="#8B0000"]64-bit[/color]](http://downloads.sourceforge.net/sevenzip/7z920-x64.msi) for Windows OS. 
**4.**  Download then install [[color="#8B0000"]Infra Recorder[/color]](http://infrarecorder.org).
**5.** Download the ISO 32-bit/64-bit version of Linux in your downloads folder.
**6.**  Open Downloads folder -> right click ISO zipped/compressed folder -> select 7-zip -> Extract Here. 
**7.**  Open Infra Recorder -> Actions -> Burn Image -> select distroname.iso -> click OK.
**8.**  Restart your computer -> enter bios -> reconfigure boot priority to 1st CD/DVD ROM 2nd HDD -> hit F10 -> hit y (yes).
Note: Please consult with your motherboard/computer manufacture manual for more information. Due to the sheer number of different bios configurations I am limited to what information I can provide.
**9.**  Put the ISO CD/DVD Rom into your computer after step eight.
**10.**  Follow Ubuntu install manager.


[SIZE="3"][color="#667C26"]Installation[/color][/SIZE]
[LIST]
[*][[color="#667C26"]Download Desktop ISO[/color]](http://www.ubuntu.com/desktop/get-ubuntu/download)
[*][[color="#667C26"]Installation[/color]](https://help.ubuntu.com/community/Installation)
[*][[color="#667C26"]BurningIsoHowto[/color]](https://help.ubuntu.com/community/BurningIsoHowto)
[*][[color="#667C26"]FromUSBStick[/color]](https://help.ubuntu.com/community/Installation/FromUSBStick)
[*][[color="#667C26"]Pre-Partitioning for Multiboot Systems[/color]](https://help.ubuntu.com/8.04/installation-guide/powerpc/non-debian-partitioning.html)
[/LIST]







[color="#DC143C"]**Warning!**
*All individuals carrying out advanced computer techniques risk temporary or permanent damage to their personal computer. _Neither_ Ubuntu Forums _nor_ its members are held liable for your actions. You have been warned.*[/color]

---

### Post by texas.chef94 on 2011-03-18
Is there a step by step anywhere for those of us more challenged then others. Please advise

---

### Post by bcbc on 2011-03-18
> **carolinabranden said:**
> I myself have Windows 7 64-bit. Don't use Wubi. Keep an extra computer handy in case something goes wrong or you get confused during the installation. This is not a Windows OS after all. Below is a rough rundown of how to install Linux via CD/DVD Rom.


The question of using wubi or not is one thing. But the OP needs to figure out why Ubuntu isn't booting. Since the problem is not Wubi-related, this won't change based on the install method. It's best to figure out booting problems using a live CD before going to the effort of partitioning your drive.

PS Ubuntu.com already has a very good guide on how to download and burn an ISO and install Ubuntu. [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

---

### Post by carolinabranden on 2011-03-18
> **bcbc said:**
> The question of using wubi or not is one thing. But the OP needs to figure out why Ubuntu isn't booting. Since the problem is not Wubi-related, this won't change based on the install method. It's best to figure out booting problems using a live CD before going to the effort of partitioning your drive.

PS Ubuntu.com already has a very good guide on how to download and burn an ISO and install Ubuntu. [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

I provided that link as well as others. The list is simply what I do to install a distro. :) lol

---

### Post by carolinabranden on 2011-03-18
> **cfree said:**
> yeah it is still doing the same thing. When i install it and reboot it gives me the option of win7 or Ubuntu and i go into Ubuntu and it says it is installing then says hit escape for more options and has a 5 sec counter. Then it proceeds with a _ symbol just blinking forever. Any suggestions? Oh and i tried the Wubi and gave me the same results as the CD

[LIST]
[*]Can you still access Windows 7? 
[*]What ISO were you using? 
[*]What computer/processor are you using?
[/LIST] 

First I'd remove [[color="#B22222"]Linux[/color]](http://ubuntuforums.org/showthread.php?t=508927) plus Grub then start over again. Follow the [[color="#B22222"]Download Desktop ISO[/color]](http://www.ubuntu.com/desktop/get-ubuntu/download) page. You download, unzip/decompress then burn the image to a CD. You don't have to select or change any settings when you burn it off [[color="#B22222"]Infra Recorder[/color]](http://infrarecorder.org/). There are any number of causes such as hardware software incompatibility, lack of hardware support or software misconfiguration.

---

### Post by carolinabranden on 2011-03-18
> **texas.chef94 said:**
> Is there a step by step anywhere for those of us more challenged then others. Please advise

We were all new to it at one time or another, so no worries. ;) There probably is somewhere, but I am not too sure where. Not too sure if I remember seeing anything like that at some time or not. I'll post a link if I see something. (^_^)

---

### Post by bcbc on 2011-03-18
> **cfree said:**
> ...the option to boot Ubuntu and I do so but it tells me that it is installing but just has a blinking underscore symbol. It does this for both the CD and the installer. I let it run for like 10 mins before I cut it off because it seems like it freezes just the underscore symbol blinking. Is this normal and can it take a while for it to set up while just displaying the underscore symbol? :confused:

> **carolinabranden said:**
> I provided that link as well as others. The list is simply what I do to install a distro. :) lol
You missed my point. That is: the OP has a problem. Your solution is how to install. I know you are trying to help... so I'm not trying to be snarky, but at the same time you don't want someone to think that you have provided a solution, and to go to all the trouble of partitioning and ... (all the other steps in your list) ... when it's not solving their problem.

---

### Post by carolinabranden on 2011-03-18
[QUOTE=bcbc]You missed my point. That is: the OP has a problem. Your solution is how to install. I know you are trying to help... so I'm not trying to be snarky, but at the same time you don't want someone to think that you have provided a solution, and to go to all the trouble of partitioning and ... (all the other steps in your list) ... when it's not solving their problem.[/QUOTE]

Good grief, you're right! lol Branden slaps himself for misreading. That's what I get for skimming through. I missed the first page. My forum settings have the newest posts first and oldest last. I think I need another cup of joe. lol

[QUOTE=cfree]I am trying to get Ubuntu installed on my laptop that is already running Windows 7. I want to dual boot. I have downloaded the cd and tried the Windows installer. When I use the Windows installer it reboots then I have the option to boot Ubuntu and I do so but it tells me that it is installing but just has a blinking underscore symbol. It does this for both the CD and the installer. I let it run for like 10 mins before I cut it off because it seems like it freezes just the underscore symbol blinking. Is this normal and can it take a while for it to set up while just displaying the underscore symbol?[/QUOTE]

On older/slower hardware it might take awhile to load. On this rig it took awhile for stuff to come up during the installation. Just let it do its thing. If Ubuntu loads too slowly on your computer, then get a lighter distro like Lubuntu or Puppy Linux.

---

