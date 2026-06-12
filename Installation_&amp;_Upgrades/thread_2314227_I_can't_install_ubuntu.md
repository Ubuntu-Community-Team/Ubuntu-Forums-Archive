---
title: "I can't install ubuntu"
date: 2016-02-19
forum: Installation &amp; Upgrades
---

### Post by billys2 on 2016-02-19
Well,im kinda new on linux so i wanted to install ubuntu on my laptop . My laptop is the Acer Extensa 5230 and its OS is Windows 7 .So , i downloaded the Ubuntu-14.04.4 and i burnt the iso to my usb . I checked it on my desktop and i could boot from usb. When i tried to install it on my laptop it got stuck at the loading screen after the 1st menu that is showing . I tried to find a solution but nothing . Also, i pressed the down arrow before it stack during the installation and the last command was this "stopping system v initialisation compatibility" . Any help guys ?

---

### Post by slickymaster on 2016-02-19
*Moved to the ***Installation & Upgrades*** sub-forum*

---

### Post by oldfred on 2016-02-19
Best to see details:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by grahammechanical on 2016-02-19
> it got stuck at the loading screen after the 1st menu that is showing

I do not know what you mean by that sentence. We usually see a kind of desktop with 2 large boxes to click. One will be labelled Try Ubuntu. The other will be labelled Install Ubuntu. Were you offered that choice? did you choose Try Ubuntu? How did the live session run? Or did something else happen? I am not all sure how far the installation process ran before it got stuck. Why did you do this?

> Also, i pressed the down arrow before it stack during the installation

Does this happen each time you try to install? Or have you only tried once?

Regards

---

### Post by oldfred on 2016-02-19
I thought it was after install, do not need Boot-Repair's report until after an install and issues.

Are all 4 primary partitions in use? 

And is system have limited memory & older video?
If older system Lubuntu or Xubuntu may work better.

---

### Post by billys2 on 2016-02-19
> **grahammechanical said:**
> I do not know what you mean by that sentence. We usually see a kind of desktop with 2 large boxes to click. One will be labelled Try Ubuntu. The other will be labelled Install Ubuntu. Were you offered that choice? did you choose Try Ubuntu? How did the live session run? Or did something else happen? I am not all sure how far the installation process ran before it got stuck. Why did you do this?



Does this happen each time you try to install? Or have you only tried once?

Regards

i mean after that menu that u can choose to try ubuntu or to install it . I tried both of these choices but i had the same result . What do u mean about the live session  ? 
Also i checked it again and it stacked on another sentence now which is "setting up X socket directories" .

> **oldfred said:**
> I thought it was after install, do not need Boot-Repair's report until after an install and issues.

Are all 4 primary partitions in use? 

And is system have limited memory & older video?
If older system Lubuntu or Xubuntu may work better.

i haven't create 4 partitions because i can't install it yet . The laptop has 2 gb ram . I don't think that the video card is that old .

---

### Post by ajgreeny on 2016-02-19
What video card has it got? If nvidia you may need to boot to the live USB using nomodeset boot option which requires you to hit F6 at the first purple screen you see with the small man/keyboard icons at the bottom.

Having checked, it looks as if that machine has fairly old Intel graphics, which at that age may not be high spec enough to run the unity desktop.  As oldfred suggested, have a look at Xubuntu which ought to run very well.

---

### Post by billys2 on 2016-02-19
> **ajgreeny said:**
> What video card has it got? If nvidia you may need to boot to the live USB using nomodeset boot option which requires you to hit F6 at the first purple screen you see with the small man/keyboard icons at the bottom.

Having checked, it looks as if that machine has fairly old Intel graphics, which at that age may not be high spec enough to run the unity desktop.  As oldfred suggested, have a look at Xubuntu which ought to run very well.

Laptop's video card is Mobile Intel(R) 4 Series Express Chipset Family .So , what do u suggest ? Do i have to download Xubuntu ?
Btw F6 doesn't work .

I just tried to install Xubuntu and the installation stack again at the same command . I really don't understand what is going on . I want so much to try Linux as an OS but ...

---

### Post by oldfred on 2016-02-19
Do you get tiny icons at bottom of screen when first booting from DVD?
Press any key then f6 and then you may need Intel parameter instead of nomodeset boot parameter.

 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic


 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by billys2 on 2016-02-19
> **oldfred said:**
> Do you get tiny icons at bottom of screen when first booting from DVD?
Press any key then f6 and then you may need Intel parameter instead of nomodeset boot parameter.

 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic


 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I don't get any icons . The boot menu that i get is something like that [IMG]http://lh3.ggpht.com/_S0f-AWxKVdM/Se3aOVhQEgI/AAAAAAAAH7s/L4JzMQFrIm0/usbuntu-boot%5B4%5D.png?imgmax=800[/IMG]  . It says try ubuntu and install ubuntu to the 1st 2 lines but the backscreen and the sentence on the bottom its the same.
I can only hit the tab button to edit .So where do i put these commands ?

---

### Post by billys2 on 2016-02-19
I managed to install the ubuntu 10 version . I don't know how... i changed the sata to IDE and and i used that monodeset command .Now i can't upgrade to the new versions through the update manager cuz it's not supported .Also i tried to install the last version but again it stack on the same spot

Is it possible to install a new version of ubuntu without booting from bios ?

I tried to install ubuntu 14.04 and i added the nomodeset at the end of the code but now it stucks one step after . I took a picture with my cell phone of the installation [https://drive.google.com/file/d/0BzV2gxmZdmNHMkFmbmlXNVlxNHM/view?usp=sharing](https://drive.google.com/file/d/0BzV2gxmZdmNHMkFmbmlXNVlxNHM/view?usp=sharing)

---

### Post by oldfred on 2016-02-20
Where it stops is not usually the problem. It may be before that. Did previous screens show any errors?
Better to have SATA mode not IDE mode on drives.

Have you  tried the Intel boot parameters, not nomodeset?

---

### Post by ajgreeny on 2016-02-20
> **Charles_Williamson said:**
> You can check this link

It is an ultimate guide on install ubuntu with windows.

Click Here: <snipped spam blog>
That leads to a dead end and simply shows how to make a USB installer disk.

For a better guide to all of the procedure see [http://ubuntuforums.org/showthread.php?t=2230389](http://ubuntuforums.org/showthread.php?t=2230389)

---

### Post by billys2 on 2016-02-20
> **oldfred said:**
> Where it stops is not usually the problem. It may be before that. Did previous screens show any errors?
Better to have SATA mode not IDE mode on drives.

Have you  tried the Intel boot parameters, not nomodeset?

i there is an error at the start of booting which is this " pwconv failed to change the mode of etc passwd to 0600 "  . 
Im gonna try with the intel parameters now . Do i have to try them one by one ?

---

### Post by billys2 on 2016-02-20
Well i managed to install it by adding these parameters [COLOR=#000000]"acpi=off", "noapic", "nolapic" and "nomodereset"  but now is not starting up after the restart . =/ 
After the grub menu is stucking again . [/COLOR]

---

### Post by oldfred on 2016-02-20
Usually you do not need all the parameters.
But you often need then again after the install. And some you may need to make permanent.
Best to experiment on boot in grub menu to find what works. 
Then we can edit grub to include those parameters all the time.

---

### Post by billys2 on 2016-02-20
> **oldfred said:**
> Usually you do not need all the parameters.
But you often need then again after the install. And some you may need to make permanent.
Best to experiment on boot in grub menu to find what works. 
Then we can edit grub to include those parameters all the time.

Ok so when i put these params after the quiet splash ubuntu starts successfully.What do u suggest ? Should i try every parameter alone to check what it works ? Also is there any consequences if i use them all ?

---

### Post by oldfred on 2016-02-20
Do not know enough about boot parameters. 
Some turn off things that normally are expected, but becuase hardware does not support it. 
Or hard has feature that software cannot use.

       gksudo gedit /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel.
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only.
[/LIST]
        o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 

 Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by billys2 on 2016-02-20
> **oldfred said:**
> Do not know enough about boot parameters. 
Some turn off things that normally are expected, but becuase hardware does not support it. 
Or hard has feature that software cannot use.

       gksudo gedit /etc/default/grub
[https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29](https://help.ubuntu.com/community/Grub2#A.2BAC8-etc.2BAC8-default.2BAC8-grub_.28file.29)
GRUB_CMD_LINUX


[LIST]
[*]Entries on this  are added to the end of the 'linux' command  (GRUB legacy's "kernel" ) for both normal and recovery modes. It is used to pass options to the kernel. 
[/LIST]
 GRUB_CMD_LINUX_DEFAULT="quiet splash"

[LIST]
[*]This  imports any entries to the end of the 'linux'  (GRUB legacy's "kernel" ). The entries are appended to the end of the normal mode only. 
[/LIST]
        o To view a black screen with boot processes displayed in text, remove "quiet splash". To see the grub splash image plus a condensed text output, use "splash". 

 Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

I've got GRUB_CMDLINE_LINUX and GRUB_CMDLINE_LINUX_DEFAULT . It's the same thing,right ? Now i have to write the parameters that i used to start the boot on grub_cmdline_linux ?

---

### Post by oldfred on 2016-02-21
The are not the same. 
In the grub menu you have multiple boot stanzas.
You normally only edit the default or the one with quiet splash.
But if system will not even boot into recovery mode, with out the parameters, you may need to add to the recovery mode and normal boot entry. 
Do not add to both or you get double entries on linux line. 

After editing anything related to grub be sure to run this, as this is the only way editing is added to grub.cfg.
sudo update-grub

On first boot after edit, check that entry is correct when you reboot.

---

### Post by billys2 on 2016-02-21
I added the parameter acpi=off and now my laptop is starting up :D Also i removed "quiet splash" and left only the splash parameter . So that fixed the shutdown problem .I think that now my ubuntu is working well . I really want to thank everyone for your help and your time . Thanks you so much guys !!!!

---

### Post by oldfred on 2016-02-21
Glad it is working.

You can change to solved.

---

