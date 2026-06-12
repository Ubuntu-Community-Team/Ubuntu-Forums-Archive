---
title: "First Time Linux User, and Can't even Install it."
date: 2010-03-13
forum: Installation &amp; Upgrades
---

### Post by blackwand on 2010-03-13
[SIZE=2]I have the following configuration
Motherboard: Asus P5Q SE/R
Processor: Intel Core 2 2.5GHz processor
Memory: 4 GB of Ram 
HDD: 80GB WD HDD[/SIZE][SIZE=2]
PSU: 550W Corsair Power Supply
Graphics:[/SIZE][SIZE=1][SIZE=2]GeForce 7600GS 256MB 128-bit GDDR2 PCI Express x16 SLI Support Video Card
2x Optical Drives (an old Dell DVD Drive from back in the day, and 1 Plextor CD-RW from back in the day)

I am trying to install Ubuntu via a CD of the i386 disc that I downloaded and burnt. I do a text based install and try to do a 'live-install.'

This gets started and I get "Loading /casper/vmlinux...................." and then "Loading /casper/initrd.lz.........................................................." and then the screen blinks and when it comes back the cursor is at the top of the screen and basically hangs. I can't type anything, everything that was on teh screen before is still on teh screen, except the cursor is at the top of the screen, and it just sits there for even 1 hour or longer, by which time i usually come back, get frustrated and turn it off.

Andy ideas or help?!?! I have tried reading some of the install problems and stuff, so I took out the only PCI card, I could (which was a 10/100 network card) had to leave graphics card in, since I don't have onboard graphics. I also have other windows 7 PCs, so I don't know if there is any remote capability, where I can unplug the graphics card or not. I am thoroughly confused... :o(

Let me know if you need any more information, please let me know.

Thanks.[/SIZE]     
[/SIZE]

---

### Post by CZARofLA on 2010-03-13
I will be honest and sya that I dont know how to completely solve your problem but I would go to the Ubuntu web-site, download a new copy, and burn it with a legitimate burner at the slowest speeds. Always seems to work for me

---

### Post by halj32 on 2010-03-13
have you checked the cd for errors??
do a md5 check or when booting click on check disk.. any errors check your *.iso and burn another disk

---

### Post by blackwand on 2010-03-13
I have my main computer, which is a Windows 7 computer, with newer hardware. I used that to burn the disk. I re-downloaded and re-burned the image and tried again. I seem to get stuck in the same location. I did an md5 check on the image after i downloaded it, and then again on some of the various files in the disk after i burned it. Overall, no errors yet.

I try doing the check disk when the installer comes up, but it does the same thing. It clears the screen and then stalls with the cursor up at the top of the screen. Then nothing happens.

---

### Post by kooia on 2010-03-13
Look at
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)
for windows xp
 
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_vista_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_vista_installed_first.htm)
for vista

---

### Post by OldMerovingian on 2010-03-13
> **blackwand said:**
> [SIZE=2]I have the following configuration
Motherboard: Asus P5Q SE/R
Processor: Intel Core 2 2.5GHz processor
Memory: 4 GB of Ram 
HDD: 80GB WD HDD[/SIZE][SIZE=2]
PSU: 550W Corsair Power Supply
Graphics:[/SIZE][SIZE=1][SIZE=2]GeForce 7600GS 256MB 128-bit GDDR2 PCI Express x16 SLI Support Video Card
2x Optical Drives (an old Dell DVD Drive from back in the day, and 1 Plextor CD-RW from back in the day)

I am trying to install Ubuntu via a CD of the i386 disc that I downloaded and burnt. I do a text based install and try to do a 'live-install.'

This gets started and I get "Loading /casper/vmlinux...................." and then "Loading /casper/initrd.lz.........................................................." and then the screen blinks and when it comes back the cursor is at the top of the screen and basically hangs. I can't type anything, everything that was on teh screen before is still on teh screen, except the cursor is at the top of the screen, and it just sits there for even 1 hour or longer, by which time i usually come back, get frustrated and turn it off.

Andy ideas or help?!?! I have tried reading some of the install problems and stuff, so I took out the only PCI card, I could (which was a 10/100 network card) had to leave graphics card in, since I don't have onboard graphics. I also have other windows 7 PCs, so I don't know if there is any remote capability, where I can unplug the graphics card or not. I am thoroughly confused... :o(

Let me know if you need any more information, please let me know.

Thanks.[/SIZE]     
[/SIZE]

Any particular reason you are doing a text base live install?  Have you tried the GUI install then updating?  I have done that several times and never had an issue.

---

### Post by blackwand on 2010-03-13
I am not trying to dual boot. I just have 2 machines. My main Windows 7 machine, and another machine that I am trying to install Ubuntu on.

I tried the graphical install, but it just immediately goes blank the cursor blinks at the top of the screen, and i get no status information and it just sits there. I was hoping with the text based, I'll at least have some information to pass on, but still nothing.

---

### Post by OldMerovingian on 2010-03-13
> **blackwand said:**
> I am not trying to dual boot. I just have 2 machines. My main Windows 7 machine, and another machine that I am trying to install Ubuntu on.

I tried the graphical install, but it just immediately goes blank the cursor blinks at the top of the screen, and i get no status information and it just sits there. I was hoping with the text based, I'll at least have some information to pass on, but still nothing.

Thats odd.  It may be the cd burner or the software you are using.  Try to download the .iso again, then burn it at the slowest speed.  Also, try a new burning software.  I had an issue with K3b on Kubuntu not burning DVDs correctly, but Brassero did.

---

### Post by linux4me on 2010-03-13
As well as running "check CD for errors" on the target machine, I would also run the "memory test" option from the Live CD to make sure you don't have a problem with RAM, but my guess as to what is causing it is that those old optical drives may be having difficulty reading the discs you burned on the other machine. 

To confirm that, I would first make sure that the machine will run Ubuntu from the Live CD. If it does, if you don't have another optical drive to install and try and there's no OS on the target machine to download and burn one using one of the two currently installed drives, take a look at the options for [installing Ubuntu without a CD]("https://help.ubuntu.com/community/Installation"). (You'll have to scroll down to that section.) If you can do one of them, you can bypass the optical drive to see if that's the problem.

---

### Post by blackwand on 2010-03-14
@Linux4Me: You were right. Something was going on with the old drives. I just took the drive i burned the disc with, and moved it over to this machine. Plugged it in, and it worked fine. Now it is completely installed and working!

Thanks everyone for the help and ideas!

---

