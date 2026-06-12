---
title: "HELP ! Grub Rescue&gt; prompt"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by mster on 2010-09-14
I did a stupid stupid thing - I was using Maverick Meerkat 10.10 but couldn't get mp3 or avi files to play (or any media apart from streaming content)

So I thought I would install 10.04 instead - it didn't work and I got so frustrated that I formatted the drive and tried to re-install 10.04 (I had to put it on a USB with the pendrive installer using my husband's PC as my CD drive doesn't work on my laptop.

Now all I can get is grub rescue> prompt.

Can anything be done to fix this?

I did back up all my files to my external Hard Drive before I did all this - so I haven't lost any data - just a HDD !

Thank you

Mster

p.s. yes I know I am an idiot.

---

### Post by drs305 on 2010-09-14
Can you boot to the installed Desktop if you leave the thumb drive in when you boot? If so, is the "Install" icon in the top left?

If it looks like your normal install (no Install icon and the terminal prompt includes your username): 
Open a terminal (Applications, Accessories, Terminal) and run this command:
```
sudo grub-install /dev/sda
```

If not, do you see the "Install" icon?

If so:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Then reboot.

If you can't boot even with the thumb drive we can try to get you to your install from the Grub 2 command prompt. I would initially direct you to the Command Line/Rescue part of the community doc:
[https://help.ubuntu.com/community/Grub2 Rescue Mode]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode")

---

### Post by mster on 2010-09-14
> **drs305 said:**
> Can you boot to the installed Desktop if you leave the thumb drive in when you boot? If so, is the "Install" icon in the top left?

If it looks like your normal install (no Install icon and the terminal prompt includes your username): 
Open a terminal (Applications, Accessories, Terminal) and run this command:
```
sudo grub-install /dev/sda
```

If not, do you see the "Install" icon?

If so:
```
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Then reboot.

If you can't boot even with the thumb drive we can try to get you to your install from the Grub 2 command prompt. I would initially direct you to the Command Line/Rescue part of the community doc:
[https://help.ubuntu.com/community/Grub2 Rescue Mode]("https://help.ubuntu.com/community/Grub2#Rescue%20Mode")


Hi

Thanks so much for your response - I cannot boot at all, I don't get into a normal command prompt just Grub rescue one and it doesn't recognise any commands.

Thanks for the link, I'll have a read.

---

### Post by drs305 on 2010-09-14
> **mster said:**
> Hi

Thanks so much for your response - I cannot boot at all, I don't get into a normal command prompt just Grub rescue one and it doesn't recognise any commands.

Thanks for the link, I'll have a read.

If you have questions about booting from the rescue prompt just ask.

How were you able to install 10.04? If you can get to a prompt that asks if you want to install or try, you should be able to boot to the LiveCD Desktop, from which we can fix Grub.

---

### Post by mster on 2010-09-14
> **drs305 said:**
> If you have questions about booting from the rescue prompt just ask.

How were you able to install 10.04? If you can get to a prompt that asks if you want to install or try, you should be able to boot to the LiveCD Desktop, from which we can fix Grub.

I wasn't able to install 10.04, I tried to install it from  a usb stick by using the pendrive installer to convert the iso file to a bootable one.

It wont load, just goes to grub rescue> prompt.

9.10 however, I can get to the do you want to install or try screen, but that gets stuck part way through installing  - it freezes on the line

"[0.032028] ACPI: Core revision 20090521"

---

### Post by wilee-nilee on 2010-09-14
For me since you have tried a few installs a look at what is where would be helpful. Can you run the bootscript in my signature, and post in code tags as described. You can also enable the code tags in the reply by highlighting the text then clicking on the # icon in the reply panel.

You just need to boot a live version of a Ubuntu cd any version basically will work for running the script.

The only thing other I would let you know about here is the support time.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I wonder if originally that the Maverick setup was just missing some codecs, that you were not aware of. I can play everything on my Maverick setup that plays on Lucid.

---

### Post by mster on 2010-09-15
> **wilee-nilee said:**
> For me since you have tried a few installs a look at what is where would be helpful. Can you run the bootscript in my signature, and post in code tags as described. You can also enable the code tags in the reply by highlighting the text then clicking on the # icon in the reply panel.

You just need to boot a live version of a Ubuntu cd any version basically will work for running the script.

The only thing other I would let you know about here is the support time.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

I wonder if originally that the Maverick setup was just missing some codecs, that you were not aware of. I can play everything on my Maverick setup that plays on Lucid.

Hi Wilee Nilee

Thank you for your response.

I downloaded your bootscript but I am not sure how I am meant to run it as all I can get to is the Grub Rescue> prompt - I cannot get any version of Linux to load on my laptop.

Also I have no CD Drive it stopped working ages ago.  I have tried booting from USB and although my system does seem to accept it, the system will not load, it keeps getting stuck on the way in at the core revision line I mentioned above.

It's only Ubuntu 9.10 that I can even get that far, all of the others just produce a blank screen.

Anything I can try now?

I am hoping for something to stick on my usb that means I can get into the Laptop, as I can't do anything with the Grub Rescue prompt it doesn't recognise anything apart from the ls command.

Thank you

M

---

### Post by binoyjayan on 2010-09-15
Hi mstr,

I also have a similar issue. I'll tell you about in a while but before that let us consider your case. It seems that what you would just need is a bootable pendrive(since you system doesn't have a working cd drive). Create a bootable pendrive (from another system, hopefully you huband's system which I think works) with an [COLOR=Red]Ubuntu LIVE ISO[/COLOR] (Try to use the same version installed in your system) and using a utility named [universal usb installer.]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/") Remember to properly eject the pendrive before removing it. 

Now that you have a bootable pendrive, plug it on and boot from it. Change the boot priority in BIOS by pressing DEL or Alt+F2 or F2 or F11 key(varies from system to system). Make the first boot option as pendrive. Now this will take you to the Ubuntu Desktop. From here you can install grub to recover your system to boot to all the operating systems you have in your system. The grub installer will auto detect all the Operating systems and will show them in the boot prompt. To learn how to install grub onto your hard drive, visit 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Now, talking about my problem, I have my laptop installed with Windows 7 and I installed ubuntu from USB drive. But after I went into Windows 7(from the dual boot option given by grub)  and did a reboot, the MBR was cleared by windows7. So, I again did a live boot from my USB drive and installed the grub. You can find the help for it at:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


Hope your problem gets solved by this...:) 


After installing grub, when I rebooted, I could see the GRUB loader with dual boot options but once I boot in to windows, the MBR gets corrupted again and get an error "Module not found" at the startup...:o  It seems that windows 7 was some how finding the MBR changed and overwriting it but with a bad content...:( 

Some one please help me out in how to stop windows 7 from overwriting the MBR each time windows boots..

**Important point to note**: Is the system from where you create bootable usb 64 bit.? If so run the usb installer in a 32 bit compatibility mode. To do this, right click on the program, click on "Compatibiliy tab" and check the box "Run this program in compatibility mode for Windows XP". This could be a reason why one might not be able to create a bootable pendrive properly. Also make sure to download the LIVE ISO image and not the installation ISO to create a bootable pendrive.

---

### Post by mster on 2010-09-15
Hi binoyjayan

Thank you for your helpful response.  When I try and load up Ubuntu from my pendrive using the website that you mentioned (I had already done this previously about 10-20 times) my screen freezes on the core revision line as I mentioned above.

This is what I get - I took a photo with my digital camera.

Hope this makes sense to someone.

Cheers
Mster

[http://yfrog.com/bf20100915myscreenj](http://yfrog.com/bf20100915myscreenj)

---

### Post by binoyjayan on 2010-09-15
Hi 

Did you check if you are able to boot with the USB disk you created in any other system.?
Also it is not clear if you are indeed booting from USB or from the harddrive.
If you are booting from USB, it should at first show a boot menu where options are there to either run a
live cd, to install to hard drive or to run the recovery software. I recommend that you select the 
"Try" option instead of installing or if still doesnt work, try the "recovery" 
option and try to boot into any bootable partition if available.
It should be something like:

[COLOR="Red"]Ubuntu, kernel 2.6.17-10-generic (recovery mode)[/COLOR]

Let me know what is the first screen shown by the bootable usb.

---

### Post by mster on 2010-09-15
> **binoyjayan said:**
> Hi 

Did you check if you are able to boot with the USB disk you created in any other system.?

Nope. I don't want to risk mucking up my husbands PC!

I am at the moment downloading "Puppy" to try and boot from another USB stick - I have 4 others but they're too small for ordinary Linux so I need to try a small one!

This is just in case it was the USB stick all along!

fingers crossed

M

---

### Post by mster on 2010-09-16
Well I tried using several different USB sticks to install 9.10 and also Lucid Puppy but it didn't work.

With one USB it just went to grub rescue> with the others it gave a message something like "remove all other media and press any key to restart"

I didn't have anything else installed or in any of the USB ports, not even a mouse so I just pressed enter and it gave me the same message again?

Marianne

---

### Post by binoyjayan on 2010-09-16
Hi Marianne,

I would say that you try booting any other PCs using the USB drive.
Of it boots properly, then we can rule out the chance that there was anything bad about the USB drive itself. While doing so, make sure that you only use the LIVE ISO and not the install ISO. Or you can try any of the alternate ISOs.

If you have torrent client s/w installed, you can try the following:


For 64 bit machines:
[http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-alternate-amd64.iso.torrent](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-alternate-amd64.iso.torrent)

For 32 bit machine:
[http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-alternate-i386.iso.torrent](http://releases.ubuntu.com/10.04.1/ubuntu-10.04.1-alternate-i386.iso.torrent)

You can also go for direct download. 

If you just go with LIVE boot option. It can be something like 

"Try Ubuntu without any changes to your computer". 

See the link [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

It will not harm your PC as long as you don't install anything.

Or if nothing works out, try installing windows, and install ubuntu in a Virtual Machine like the powerful [VMWare Workstation]("http://www.vmware.com/products/workstation/") or the opensource [Virtual Box]("http://www.virtualbox.org/").

Enjoy..:-)

Binoy

---

