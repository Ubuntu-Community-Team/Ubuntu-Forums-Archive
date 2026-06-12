---
title: "PC boots straight into windows (dual install)"
date: 2020-04-28
forum: Installation &amp; Upgrades
---

### Post by injen on 2020-04-28
Hi all,

Firstly, thanks to anyone reading this. Here is my story: I've got a laptop that needed some love so I erased all drives and freshly installed both Win10 and Ubuntu 20.04. The laptop has 1 ssd drive and 1 hdd, so I've installed both operating systems on the ssd and all the file directories on the larger hdd, I did this by manually installing ubuntu and specifying the /home partition on the larger hdd. Both operating systems work correctly. My issue is that whenever I start the PC, I don't see grub and the PC launches Win10 automatically.

If I use my bios option to be able to select boot device, I can then select Ubuntu to load, it is then that I see grub menu with both the options for ubuntu and windows 10. Since I have installed Ubuntu manually it is likely that something isn't quite the way it should be. 

Any help on the matter is greatly appreciated, I've ried boot-repair with no success.

Thanks,

Injen

---

### Post by CelticWarrior on 2020-04-28
Welcome.

The typical cause for what you describe is having the OSes installed in different modes, one in UEFI mode (as it should be for any UEFI hardware) and that one is most likely Windows, and one, Ubuntu, installed in Legacy/CSM mode because booted that way and/or due to an incorrect manual partitioning/selection of partitions. In a computer with an already installed Windows in UEFI mode, users intending to do manual partitioning should not forget to a) boot the installer in UEFI mode and b) select the ESP (EFI System Partition) along with all the other required partitions.

To confirm you can use [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair"). Use the 2nd option to install it in the same USB you used to install Ubuntu, just make sure it is booting in UEFI mode.

---

### Post by injen on 2020-04-28
OK, thanks for your answer. I will try reinstalling and see what happens. Will get back to you when i get a chance.

---

### Post by ubfan1 on 2020-04-28
Posting a link to the boot-repair report would be helpful, along with the make/model of your machine.  That should answer questions like in what mode is Windows installed, Ubuntu in the same mode? Is the SSD sda?  etc.

---

### Post by yancek on 2020-04-28
There is Ubuntu documentation on dual booting with windows 10 at the link below.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by injen on 2020-04-29
> **ubfan1 said:**
> Posting a link to the boot-repair report would be helpful, along with the make/model of your machine.  That should answer questions like in what mode is Windows installed, Ubuntu in the same mode? Is the SSD sda?  etc.

Hi again,The make and model - HP Pavilion dv7

I will try posting the results of boot-repair but I don't know how&#8230; When I boot pc into boot repair to make the report i tried posting the results with the web browser it has with it but it was just a Wall of text, ignoring all the break lines. And I cant copy results onto usb because the operating system it launches does not launch any usb's plugged in :p

Will try again later.

---

### Post by yancek on 2020-04-29
When you run boot repair with the Create BootInfo Summary option as instructed, you should get a link when it finishes and that is what you should post here.

---

### Post by injen on 2020-04-29
Hi again,

I'm actually having trouble getting the boot repair information here.

I've tried both approches on this page:

[FONT=Verdana,Arial,Tahoma,Calibri,Geneva,sans-serif]https://help.ubuntu.com/community/Boot-Repair

I'm able to get the information while launching it from a usb, but I'm not able to share that information with you. I don't get a link that I could paste in the forum, just a file destination of where the txt file has been created, see image.

The problem is, if I try to copy and paste the text from the text editor into this forum the text copies as a wall of text ignoring all the line breaks.

If i try option 2 from the web page, an error occurs while running "[LEFT][COLOR=#333333][FONT=UbuntuMono]sudo apt-get install -y boot-repair && boot-repair" It starts running but then an error occurs and Repair-Boot stops scanning.

Running Ubuntu 20.04.

Any suggestions welcome.
[/FONT][/COLOR][/LEFT]


[/FONT]

---

### Post by injen on 2020-05-01
Hi again,

I  was finally able to get a link to paste bin for Boot Reapir:

[FONT=Verdana][paste.ubuntu.com/p/y4YmQkVVh6/]("http://paste.ubuntu.com/p/y4YmQkVVh6/")

Any help on the matter is greatly appreciated.
[/FONT]

---

### Post by CelticWarrior on 2020-05-01
It looks fine now.
First assure Windows is booting correctly by its own -> Change the boot order in UEFI settings to "Windows bootloader manager".

If Windows works as expected when booting it directly then change the boot order to "Ubuntu". This should give you the Grub menu from which both OSes can be booted. If it boots Ubuntu directly without that Grub menu then run 'sudo update-grub'.

---

### Post by injen on 2020-05-01
Hi again,

I think this has been my problem from the start, see image named "1" to see  what the startup menu looks like for the pc (hp Pavilion dv7). Hitting F10 brings up image named "3", as you can see the only boot option under UEFI i get is "OS boot Manager", however if in the startup menú I hit F9 (image named "2") for the boot option menú I can select Ubuntu to launch and enter the Grub menu, but I can't set it as default so that the pc launches it every time on start up. At the momento I have to hit Esc on launch every time then hit F9 and select the desired boot manager manually.

All operating systems work fine, the only issue is getting the pc to start with the Ubuntu boot Manager (Grub)

Thanks again.

---

### Post by jeremy31 on 2020-05-01
In image 1 go to OS Boot Manager and put ubuntu on top of the list and then press F10 twice, save settings, see if it boots to Grub

---

### Post by injen on 2020-05-01
Hi again :)

That is the problem, the ONLY option under the uefi bios is "OS boot Manager" that's it, I can't get to a list of options in which to select windows or ubuntu boot manager and this always launches Win10.

However by manually selecting start up with F9 I do get to see a list of boot managers.

Beats me...

---

### Post by oldfred on 2020-05-01
Some with HP have posted that an Update to UEFI then let them change boot order.
Every other UEFI lets you use efibootmgr, but HP seems to reset (or is it Windows?) boot order to Windows first.
So make sure you have latest UEFI from HP for your system.

---

### Post by injen on 2020-05-01
Hi again,

Already did that, the computer is now 7 years old but I installed the latest bios (i supose UEFI is part of this?) from manufacturer which is dated 2016.

[https://support.hp.com/es-es/drivers/selfservice/hp-pavilion-dv7-7000-entertainment-notebook-pc-series/5226224/model/5259338](https://support.hp.com/es-es/drivers/selfservice/hp-pavilion-dv7-7000-entertainment-notebook-pc-series/5226224/model/5259338)

Thanks

---

### Post by CelticWarrior on 2020-05-01
UEFI replaces BIOS, one isn't part of the other, one is there *instead* of the other.
Unfortunately many vendor still use the now wrong acronym/terminology and it generates all sorts of confusions.
So, when you see "BIOS updates" in the website that is what you're looking, regadless of it being an actual old BIOS or the new UEFI.

---

### Post by injen on 2020-05-01
I see, thanks for the information.

Yes, I have the lastest UEFI from the manufacturer then. I supose my problem might be linked to restrictions of the manufacturers UEFI. I'm tempted to try the installation in legacy mode then, I think I was able to perform the instalation in that way in the past and get straight into the grub menu on startup.

I will wait a bit to see if anyone comes up with any ideas, otherwise will try reinstalling in legacy mode and will keep you informed.

---

### Post by jeremy31 on 2020-05-01
When I go into BIOS on my HP and then to system configuration, Boot Options I can click on the OS Boot Menu and see a screen like the one below.  When it was dual boot with Windows 10 it also had Windows Boot Loader as a choice

---

### Post by ubfan1 on 2020-05-01
In the EFI partition (mounted at /boot/efi), check the size of /boot/efi/EFI/Boot/bootx64.efi, if it is the same size as  ...EFI/ubuntu/shimx64.efi, then copy ...EFI/ubuntu/grubx64.efi to ...EFI/Boot/grubx64.efi.  I think shim still needs a local copy of the grubx file to successfully boot.  That may be the issue which makes the device boot fail.  If the size is the same as grubx64.efi, then it should be OK, just without secure boot.

---

### Post by yancek on 2020-05-01
On your HP, using the F9 key will make a one time change to the boot order so if you have windows and ubuntu installed, you can select either and on next boot it will boot whatever you have set as the default.  To make a permanent change, you need to access the BIOS using the F10 key and go to System Configuration and Boot Order and highlight OS Boot Manager.  If there is an arrow to the left of this entry, that means there are multiple entries.  Arrow down to OS Boot Manager so it is highlighted and hit the Enter key and you should see the options in a small windows to the right.  To make a permanent change, highlight an entry and hit F5 key to move an option down, F6 to move an option up.

---

### Post by kurt18947 on 2020-05-03
I wonder if Injen is being bitten by this. It appears to be HP specific

[https://www.zdnet.com/article/the-refind-boot-loader-for-uefi-systems-a-life-and-sanity-saver/](https://www.zdnet.com/article/the-refind-boot-loader-for-uefi-systems-a-life-and-sanity-saver/)

Specifically, I wonder if this is a fix:

The rEFInd documentation mentions that some systems, particularly HP  systems, don't allow the boot manager configuration to be changed to  anything other than the default *bootmgfw.efi* program. Well, I  learned long ago that when faced with such inflexibility, the simple  solution is to just give it what it wants--and the rEFInd documentation  suggests about the same thing.
 Move the EFI/Microsoft/Boot directory out of the way (rename it), move the refind directory to that name, and rename *refind.efi* to *bootmgfw.efi*.

---

### Post by dragonfly41 on 2020-05-03
I have read the above article and I support the writer's views.

> Besides, rEFInd itself really is a beauty, and it works exceptionally well. 

I have Dell, not HP, and I use rEFInd for a multi-OS configuration.

After installing rEFInd (I will not give instructions here since they are well documented by Rod Smith the author) there should be no need to move or rename any directories.  The file which I use in /boot/efi/EFI/refind is refind_x64.efi which takes me to a boot menu with nice eye candy.  The theme is tweaked in refind.conf.
In refind.conf I can even set the order of scannng so I look for external drive before internal drive (I am writing this on external SSD Ubuntu). Search through the comments/notes in refind.conf.

When installing Ubuntu I now create an ESP for each OS which I use (not a single ESP which Windows expects).

So **+1** for rEFInd.

---

### Post by oldfred on 2020-05-03
We used to also recommend renaming/copying shimx64.efi to /Microsoft/boot/bootmgfw.efi.
But found that Windows updates overwrote that. And grub only boots working Windows so with a Windows update, you lose grub and grub boot of Windows. I would expect the same with rEFInd.

But UEFI has fallback or hard drive boot entry and at least newer systems support that. It is the same path/file that UEFI uses to boot external drives. /EFI/Boot/bootx64.efi.
Normally rEFInd suggests using bootx64.efi for its boot.

Grub several years ago started to add /EFI/Boot/bootx64.efi as a copy of shimx64.efi.
Boot-Repair for a number of years copies shimx64.efi to /EFI/Boot/bootx64.efi and renames bootx64.efi to bkpbootx64.efi and adds a new Windows entry in 25_custom to boot the bkp file.

Some early UEFI implementations may not have the fallback or hard drive entry.

---

### Post by injen on 2020-05-05
Thanks all for your answers.

I've had to lay off for a few days since my wife needed to use her laptop. I'm now able to tinker a bit more with it so I'll get back to you once I've had a play around. Odd thing is that I've had both operating systems installed on this PC before (Win 7 and Ubuntu 18.04) with no problem launching grub, although I think I might have installed both in legacy mode in the past, I seem to remember having similar issues when installing those systems uefi mode.

Thanks.

---

### Post by injen on 2020-05-05
> **jeremy31 said:**
> When I go into BIOS on my HP and then to system configuration, Boot Options I can click on the OS Boot Menu and see a screen like the one below.  When it was dual boot with Windows 10 it also had Windows Boot Loader as a choice

That does not appear on mine. All I get is OS Boot Manager with no sub menu to choose launchers, nothing, no matter if I hit "enter" or any other key. I never get a list like the one your image shows.

---

### Post by siepo on 2020-05-05
I also have an old HP notebook and face the same problem. I had to shuffle efi files after every W10 cumulative update. BIOS updates made no change in this respect. In the end, I gave up and nowadays I just use F9 and 'boot from efi file' to boot Linux. This in spite of Linux being my main OS.

---

### Post by injen on 2020-05-05
> **siepo said:**
> I also have an old HP notebook and face the same problem. I had to shuffle efi files after every W10 cumulative update. BIOS updates made no change in this respect. In the end, I gave up and nowadays I just use F9 and 'boot from efi file' to boot Linux. This in spite of Linux being my main OS.

Hi,

Yeah, I've tried all the suggestions posted here, and I think it will be the best solution as things are. I don't want to be messing around with renaming efi files since it is my wife's computer and she will be thrown every time windows update resets the efi files, I think the easiest option is for her to get used to hitting F9 at boot.

Thanks all for your time and help.

---

### Post by kurt18947 on 2020-05-06
There might be one other option if you want to play with it, BootIt. I haven't used the UEFI version - I did use the earlier preUEFI version. One potential down side to BootIt is that once installed, you must use BootIt partition tools. Using a mixture of BootIt and Linux partition tools may well result in a non-booting machine. I have experienced Windows overwriting GRUB on my desktop machine but Boot-Repair on a flash drive was able to put things right. Because I use Windows so infrequently on the desktop machine I have it installed on a separate SSD. I keep the Windows SSD unplugged except when I need Windows. So far that hasn't messed with GRUB on the NVME drive that contains Ubuntu and other distros.

[https://www.terabyteunlimited.com/bootit-uefi.htm](https://www.terabyteunlimited.com/bootit-uefi.htm)

---

### Post by injen on 2020-05-06
Thanks for the suggestion. But anything that makes it harder than hitting F9 key and then booting the desired system (and which works every time) is not going to be a solution, but thanks for the idea!

---

