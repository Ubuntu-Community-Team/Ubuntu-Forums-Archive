---
title: "Will i be able to install the newest version of ubuntu?"
date: 2016-06-20
forum: Installation &amp; Upgrades
---

### Post by blaablaaguy on 2016-06-20
Hi,

Im thinking of buying a Dell Latitude E5420 and just wanted to check if i will be able to install the newest version of ubuntu on it
It has 4gb of ram and a 250GB HD

---

### Post by Rex Bouwense on 2016-06-20
With that much RAM, I do not see a problem installing Ubuntu 16.04 on it.  By the way welcome to the forums.

---

### Post by RobGoss on 2016-06-20
Hello and welcome to the forum, I don't see any reason why you would not be able to run Ubuntu on that machine the Ram is more then enough you would have to check to see what kind of graphic card it has. Try running the Live desktop to see if thing loads up and you should have some kind of idea what to expect

---

### Post by mastablasta on 2016-06-21
if oyu have Windows on it then ***speccy*** program Will give you your hardware info report you can attach here and we cna help you better. Ther eis enough RAM, but oyu also need a descent and well supported graphics card to run stock ubuntu.

---

### Post by blaablaaguy on 2016-06-22
Thanks, 

I havent actually bought the laptop yet (im still looking for one) and have settled on ordering a different model (Packard Bell EasyNote TE69). Its got the same amount of ram and a larger 1TB harddrive and its "graphics adapter" (i have no idea if thats the same thing as a graphics card) is "HD Graphics 5500" :| I suppose i could try out ubuntu when it comes and if it doesnt work i could use debian or just stick with windows

---

### Post by howefield on 2016-06-22
Check the specifications against this page, although it is for 12.04, looks good for 16.04 being able to run pretty sweetly.

Seeing a few problems with the Packard Bell EasyNote TE69 albeit somewhat older threads. Usually a search with your favourite engine with the laptop model name with Ubuntu appended will often show up any show stoppers.

---

### Post by mastablasta on 2016-06-23
HD5500 is a graphics chip on CPU. yes, from user standpoint it is the same. it displays everything on screen. HD5500 should be compatible as Intel drivers are usually inlcuded in Kernel (core of the OS). Gen 5 (5000 series) should work fine. here is the status: [SIZE=2][https://www.x.org/wiki/IntelGraphicsDriver/](https://www.x.org/wiki/IntelGraphicsDriver/)
[/SIZE]

---

### Post by blaablaaguy on 2016-07-06
Thanks,

Ive received the laptop which came with windows 10 preinstalled and since im not comfortable with that, i would like to install ubuntu over windows and completely erase windows. How could i acheive this? Can i do it with a live cd?

PS: Please keep in mind im only 14 :)

---

### Post by mörgæs on 2016-07-06
Yes, if Ubuntu works in a live boot there is a good chance that it also does when installed. Best is to use a wired internet connection during install.

Be aware that some people posting here will encourage you to keep Windows even though you clearly state that you have no need for it.

---

### Post by X-RED_Tech on 2016-07-06
> **mörgæs said:**
> Be aware that some people posting here will encourage you to keep Windows even though you clearly state that you have no need for it.

Certainly I'm not one of them.
I would keep Windows for any BIOS/UEFI update because generally it's easier with the Windows software vendors insist on these days. It used to be possible to make a DOS bootable USB with the Dell's updates but I haven't used one in a long time so perhaps things have changed. They shouldn't, especially in the professional line Latitude.

---

### Post by blaablaaguy on 2016-07-06
I think you must have mistunderstood, i mean that if i install ubuntu, will windows be completely erased off my hard drive?

---

### Post by X-RED_Tech on 2016-07-06
It depends on your choices during installation.
You can choose to erase the whole drive and install Ubuntu. Or you can choose to dual-boot in which case the best way is to boot Windows first, shrink one or more partitions to make room for the second OS, reboot and let Windows correct for the new partition sizes; then you can boot Ubuntu and choose install alongside or something else to make your own scheme of partitions.

---

### Post by mörgæs on 2016-07-06
You can do both: Erase Windows during the process or install both systems side by side.

---

### Post by RobGoss on 2016-07-06
> **blaablaaguy said:**
> Thanks,

Ive received the laptop which came with windows 10 preinstalled and since im not comfortable with that, i would like to install ubuntu over windows and completely erase windows. How could i acheive this? Can i do it with a live cd?

PS: Please keep in mind im only 14 :)

Hello and welcome, Yes it's fairly simple just run the live USB or DVD and when you see Try Ubuntu choose  Install Ubuntu instead and let the installation begin

When you see the screen how would you like to install choose Erase drive and install Ubuntu.

Then let the installation complete and your done

---

### Post by bapoumba on 2016-07-06
One duplicate post moved out of public view.

---

### Post by blaablaaguy on 2016-07-08
I made a cd wuth the 32bit version, put it into my disk drive and pressed f12 when booting up to get into my systems boot manager. The disk drive wasnt listed in there so i made another 32bit cd and had the same issue. Then i went into bios and put my disk drive at the top of the boot sequence but my laptop still booted into windows. I tried a 64bit disk instead and i could boot from it using the boot manager but when i selected the "try out ubuntu" option and got a black screen. I waited a good few minutes but ubuntu still wouldnt start.
Any ideas? Should i try out an older version of ubuntu?
EDIT: Or should i try a live USB flashdrive instead

---

### Post by mörgæs on 2016-07-08
Stick to a 64 bit 16.04. 

When the live boot appears to hang what happens if you press Ctrl + Alt + F1?

---

### Post by oldfred on 2016-07-08
Many newer Intel chips need a boot parameter:
 # Usually Intel works with one of these which you add like the nomodeset parameter used with nVidia or AMD video:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size 

You add boot parameter to grub's Linux line when booting in UEFI boot mode. Only use 64 bit to boot in UEFI mode.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to add boot parameters
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by blaablaaguy on 2016-07-09
Im not sure if i understood you properly, do i need to add a boot parameter and after that set quitsplash to nomodeset? How can i open a terminal to create a boot parameter if i cant access the os.

I tried Ctrl Alt F1 but that didnt do anything, the screen stayed black.

Not sure if this is relevent but my ubuntu disk seems to booting in UEFI mode (so is windows 10).

---

### Post by banceu_sergiu_ione on 2016-07-09
This way should be more easy for who is still new.
I suggest you have a read of this post: [Boot Options Ubuntu]("https://help.ubuntu.com/community/BootOptions").

If you go into Advance Welcome Page Options ( press any key when small logo appear) , press F6 and select acpi=off, noappic, nolapic. Then use 'Try without install' to see if it work properly. If does, then you can reboot, use same parameters and run installation, alongside windows if you want to keep  your windows, or erase disk and install if you only want ubuntu.

From Advance Welcome Page you can also edit the boot command line if really need to add different parameters. You can see how to, in the link i had posted.

---

### Post by blaablaaguy on 2016-07-09
When i use the Live CD my menu looks similar to this image and i dont get the purple screen with the little logo at the bottom. 
[http://i.stack.imgur.com/rL6Jh.jpg](http://i.stack.imgur.com/rL6Jh.jpg)
Edit: If i boot the disk in "legacy" mode instead of uefi i can get into the advanced options menu but selecting "try out ubuntu" gives a black screen with a blinking cursor in the top left corner

---

### Post by banceu_sergiu_ione on 2016-07-09
When you get that Menu, press ' E ' and you access the grub options.
Use arrows to move and search for the line:

linux      /casper/vmlinuz.efi       file =/cdrom/pressed/ubuntu.seed     boot = casper quite splash

You add what boot option need at end of ' quite spalsh ' remamber to give ' space ' after splash
try add acpi=off
then press F10 or Ctrl+X to boot and see if it boot
if not, try also the options #oldfred had gave to you and see which work

---

### Post by blaablaaguy on 2016-07-09
E wont open up the grub options in the advanced options menu but it does when i boot in UEFI mode and get the other menu. Should i enter the parameters in there? 
In the advanced options if you press F6 it lets you choose some options, ive allready tried acpi=off in there.

Im close to giving up now... :(

---

### Post by banceu_sergiu_ione on 2016-07-09
First of all, you have to install Ubuntu in same way windows is installed, otherwise you wont be able to boot both. 
Windows UEFI mode install implies any other OS install on UEFI.
Since for sure windows is installed in UEFI you must go with that way.
So, boot in UEFI mode, and at Menu list, press E. Search for line I posted up, and type the boot option after ' quite spalsh '.
Now, I don't know what boot option you need to get it work so you have to type 1 option at time and boot, see if work - if not reboot and enter a new different option and repeat since it work. If still not work, then go try adding more option like 2 or 3 .
Have a look to what boot options did #oldfred suggested to you.

---

### Post by oldfred on 2016-07-09
With the UEFI systems, you do not want the BIOS boot screen with the accessibility icons at bottom, but do want grub menu which you should be with UEFI boot.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    
 How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by blaablaaguy on 2016-07-09
Tried all the boot parameters oldfred posted, none of them worked. I think i might try a different linux distro instead

---

### Post by mörgæs on 2016-07-09
It's better to post exactly what you tried than saying 'I did what you suggested'. It will give people a better foundation for helping you.

---

### Post by blaablaaguy on 2016-07-09
I pressed e at the UEFI Ubuntu menu and added the first boot parameter oldfred posted after the words "quiet splash" and tried to run the os like that. When it didnt work i rebooted and tried the second boot parameter and after that tried the last two, replacing "1280x1024" with my monitors size. All of them took me to that black screen.

---

### Post by banceu_sergiu_ione on 2016-07-09
How about you try boot with quite off.
You have to press E at Menu, enter the boot and delete 'quite' . Then press F10 and see what errors you get. 
'quite' parameter make the kernel load in quite, I mean it do not print any error while loading. Switch 'quite' off by delete it from boot parameters load, will make the system to print all the loading process and you may be able to see what error you get and a possibility to see what parameter to add at boot to be able to run it.

Could you also add a picture of your Grub Option after you had press E key at Menu ?

---

### Post by blaablaaguy on 2016-07-09
Removing quiet gives the same black screen, no error messages. 
I tried to attatch a picture but the forum wouldnt accept my JPG image for some reason.

---

### Post by banceu_sergiu_ione on 2016-07-09
The pic is to big in size?

Its weird you get nothing print on screen while load if 'quite' is off.

Try add ' debug ' and see what it print. ' quite ' must be on off, so delete it.

---

### Post by blaablaaguy on 2016-07-10
removing quite and adding debug at the same time gave the same black screen but if set my system to boot windows *and *ubuntu in legacy mode i get the screen showed in the last image. The other two images is what i get after pressing e in the UEFI ubuntu menu.

---

### Post by oldfred on 2016-07-10
Did you replace quiet splash with nomodeset?
Or is it booting with Intel and needs an Intel boot parameter?

What actual laptop did you finally get, make & model?

---

### Post by blaablaaguy on 2016-07-10
All i did was remove "quiet".
I ended up gettin a packard bell easynote ENTE69BH. It has 4gb of ram a terabyte hardribe and an intel i3 processor.
EDIT: This person seems to be have had a similar problem. Should i make a complete windows backup and try downgrading BIOS?
EDIT: Oops, forgot the link http://askubuntu.com/questions/792923/install-hangs-black-screen-net-protocol

---

### Post by oldfred on 2016-07-10
Packard Bell is now part of Acer. A low cost version.
Generally better to upgrade to newest UEFI.
Acer did have to downgrade UEFI, posted many times, but newer posts say an even newer UEFI works.

But Acer is one vendor that requires you to set a UEFI supervisory password and then set trust on the ubuntu/grub .efi files in the ESP.
You may have a similar UEFI?

 Packard Bell Easynote manually renamed bootx64.efi, but best not to rename Windows efi boot file. Windows will overwrite that with updates anyway.
[http://ubuntuforums.org/showthread.php?t=2234019](http://ubuntuforums.org/showthread.php?t=2234019)

See if you have settings like these Acer. Users described what they did. Read several as some are a bit more complete than others.

 Acer Trust Settings - details:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
Boot Parameter required
[http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10](http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10) 

       
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)

---

### Post by blaablaaguy on 2016-07-11
The trust setting thing didnt work, there was no <ubuntu> option, probably because ubuntu isnt actuall installed on my computer. The boot parameter didnt work in legacy mode or uefi mode.

---

### Post by oldfred on 2016-07-11
If not installed then no it will not work.

You still then need boot parameters to boot live installer.
What i3 chip, 4th (Haswell), 5th or 6th gen(Skylake)?  No other video chip?

Some need Intel boot parameters and other parameter also:
       # Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

---

### Post by blaablaaguy on 2016-07-11
Its a 5th gen chip. Im not sure about the video chip, i cant find much information about my laptop model.

---

### Post by oldfred on 2016-07-11
If Intel only, nomodeset usually does not work and you have to replace quiet splash with one of the Intel boot parameters and possibly others also.

 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
 i915.preliminary_hw_support=1 #Skylake some versions of Ubuntu -For linux kernels older than 4.3.x, i915.preliminary_hw_support=1 must be added to your boot parameters for the driver to work on the new Intel Skylake (6th gen.) GPUs. On a fully updated system running kernel 4.3.x and up, this step is unneccesary.

---

### Post by blaablaaguy on 2016-07-11
Thanks, ill try them and see how it goes. I just tried debian, linux mint, and ubuntu trusty tahr and all of them gave black screens (as far as i can rememeber).

---

