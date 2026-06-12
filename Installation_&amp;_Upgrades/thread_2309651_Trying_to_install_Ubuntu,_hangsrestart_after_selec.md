---
title: "Trying to install Ubuntu, hangs/restart after selecting try/install ubuntu"
date: 2016-01-12
forum: Installation &amp; Upgrades
---

### Post by henrik13 on 2016-01-12
Hi Guys

So I really want to learn linux, but its like the universe tellls me that's not going to happen.

Anyways. I have windows 10 installed (x64) on a acer vn7-592g, it has a skylake 6300hq, 8gb ram, 1tb hybrid drive, and gtx 960m.

I have several usb sticks, ranging from 2gb to 16gb. I have disabled fast boot inside windows, and disabled secure boot inside the bios. I have UEFI.

So yesterday and today has been going trough guides on how to dual boot Windows 10 and ubuntu. I have shrinked the windows volume by 300gb, so i have a partition ready for ubuntu.

I downloaded 15.10@64-bit. And i tried using one of several programs
unetbootin, rufus, universal usb installer.

After formatting and letting the program do its thing, i restart the computer holding shift, go into the usb and select uefi usb drive. the menu with try ubunutu, install ubuntu shows. Ive tried both. When using UEFI i see the dots loading, and after about 5-10 seconds, the computer restarts and boots into Windows. Tried selecting USB as primary boot, but it doesnt boot from the USB by itself during boot.

When using legacy, after selecting install ubuntu, the dots stops loading during the logo, and it freezes, and i have to restart the computer.

Heres one of the examples of guides i have been using
[http://www.tecmint.com/ubuntu-15-10-desktop-installation-guide/](http://www.tecmint.com/ubuntu-15-10-desktop-installation-guide/)

Getting a bit fed up. I have tried several usb sticks, so i doubt thats the problem, i dont have a cd burner on my computer, and i really dont want to buy one just to find out it still doesnt work.

I think its weird that during UEFI it doesnt auto boot from the usb during start up, it still goes straight into Windows. I have USB hdd as first boot priority.

One time, i managed to get into try ubuntu desktop, I was greeted by a keyboard shortcut menu, but i had no mouse control etc, and it looked like the computer had frozen, clock wasnt moving etc.

Let me know what you want, im not experienced with ubuntu or linux in general so let me know what you need from me

Thanks for your help

---

### Post by Bucky Ball on 2016-01-12
Welcome. Do not use legacy if Windows is installed in UEFI. You are entering a world of problems. Stick with whatever Windows is installed in.

Boot from the install media and when you see a purple screen with the icon at the bottom, hit any key. That should take you to the options screen, but here, hit F6. Options should pop up. Choose 'nomodeset' and proceed with 'Try Ubuntu'. Any luck?

If you're getting to the options list with 'Try Ubuntu' 'Install Ubuntu' I'd forget about having problems with the USB. Not that. At those options, there is an option to 'Check disk for defects', or something like that. Do it and make sure all checks out there. The USB itself is probably fine but the ISO you downloaded or the burn itself may be corrupt. 

Where did you download the ISO from?

PS: Instead of trying to boot the USB from BIOS, just make sure it is booting in UEFI and reboot then try hitting F12 instead of whatever key you hit to get to BIOS. That should take you to a boot device screen. Choose the USB from there. Any different?

---

### Post by henrik13 on 2016-01-12
> **Bucky Ball said:**
> Welcome. Do not use legacy if Windows is installed in UEFI. You are entering a world of problems. Stick with whatever Windows is installed in.

Boot from the install media and when you see a purple screen with the icon at the bottom, hit any key. That should take you to the options screen, but here, hit F6. Options should pop up. Choose 'nomodeset' and proceed with 'Try Ubuntu'. Any luck?

If you're getting to the options list with 'Try Ubuntu' 'Install Ubuntu' I'd forget about having problems with the USB. Not that. At those options, there is an option to 'Check disk for defects', or something like that. Do it and make sure all checks out there. The USB itself is probably fine but the ISO you downloaded or the burn itself may be corrupt. 

Where did you download the ISO from?

PS: Instead of trying to boot the USB from BIOS, just make sure it is booting in UEFI and reboot then try hitting F12 instead of whatever key you hit to get to BIOS. That should take you to a boot device screen. Choose the USB from there. Any different?
Thank you

I managed to get it installed now, i was at the screen "remove media" and hit enter. the one after installation is finished.

I setup the install as follows

/ 25gb
/home 270gb
swap at 1gb

Now the problem is that when i boot i dont have grub2 to choose what OS to boot to. I goes straight into windows, i guess this is not right.

Anyone know how i can fix this, im tempted to just remove windows but im kinda dependent on windows on some programs.

added a pic of partition inside windows

---

### Post by Bucky Ball on 2016-01-12
Should be easy. Two ways to go. When you boot, after the manufacturer splash screen start hitting enter. That should get you there. To make it permanent, open a terminal at a desktop and paste this in:

```
sudo nano /etc/default/grub
```

Look for these lines and change them to reflect this:

```
GRUB_DEFAULT=0
# GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

Follow instructions at the bottom of the terminal to save and exit (control+x, 'y', enter), then this command:

```
sudo update-grub
```

Reboot and you should see the grub list.

PS: 2Gb /swap is generally recommended, but shouldn't matter. How much physical RAM do you have installed? Rest looks fine. :)

PPS: I will also make this point. Windows, as you can see from your screenshot, has no idea what EXT* partitions are. Therefore if you want to share stuff on your /home partition with Win you can't. The norm is to setup an NTFS partition to share data between the two OSs. The good news is that Ubuntu can read/write NTFS so you can access the Win partition. The bad news is that it is not a good recommended to change files on your Win OS partition. People do ...

As you're just setting off on your Linux journey, the way you have it now is probably going to be fine for you. You can always change things later (shrink the Win partition again and create a shared NTFS partition in the free space or some other variation).

---

### Post by henrik13 on 2016-01-12
> **Bucky Ball said:**
> Should be easy. Two ways to go. When you boot, after the manufacturer splash screen start hitting enter. That should get you there. To make it permanent, open a terminal at a desktop and paste this in:

```
sudo nano /etc/default/grub
```

Look for these lines and change them to reflect this:

```
GRUB_DEFAULT=0
# GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
```

Follow instructions at the bottom of the terminal to save and exit (control+x, 'y', enter), then this command:

```
sudo update-grub
```

Reboot and you should see the grub list.

PS: 2Gb /swap is generally recommended, but shouldn't matter. How much physical RAM do you have installed? Rest looks fine. :)

PPS: I will also make this point. Windows, as you can see from your screenshot, has no idea what EXT* partitions are. Therefore if you want to share stuff on your /home partition with Win you can't. The norm is to setup an NTFS partition to share data between the two OSs. The good news is that Ubuntu can read/write NTFS so you can access the Win partition. The bad news is that it is not a good recommended to change files on your Win OS partition. People do ...

As you're just setting off on your Linux journey, the way you have it now is probably going to be fine for you. You can always change things later (shrink the Win partition again and create a shared NTFS partition in the free space or some other variation).
Thank you
.
All though nothing happens when i press enter either before or after acer splash screen during boot, ive tried using the usb to go into a live version and using terminal there, but its just keeps restarting before i can enter ubuntu (try mode). I tried pressing escape during the ubuntu splash screen that comes during loading, to see the error messages, and it spamming one error message over and over again, before it restarts. 

But I need a break now, spent 10-12 hours today banging my head against the wall. Will update tomorrow.

THanks for all the help, very much appreciated

---

### Post by henrik13 on 2016-01-12
Just a final update before bed time, this is some (poor) pictures when i try to boot from a usb into try ubuntu 15.10@64-bit

pictures 2-4 is during ubuntu loading screen/splash screen, when u can press esc to see whats going on. last picture is after it restarts by itself.

---

### Post by henrik13 on 2016-01-12
just a quick update, after several installs of ubuntu i tried booting into live and update grub

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10


updated, still no boot menu during boot, straight into windows.


tried also to use boot-repair, and to fix boot errors, when its says replacing grub, the live version freezes, tried 2 times and the same thing is happening.[COLOR=#111111][FONT=Consolas]


[/FONT][/COLOR]

---

### Post by henrik13 on 2016-01-12
okay one last thing.

frustration reached max levels so installed linux mint, same problems, it installs fine. but grub doesnt show.

went into windows and find the solution (i think)

bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi

now i get grub by itself, can boot into mint, the problem i run into was that everything froze when installing nvidia drivers, and now i just get a black screen when trying to boot into. So im formatting the partitions now and one final times going to try ubuntu.

---

### Post by Bucky Ball on 2016-01-12
> **henrik13 said:**
> 
now i get grub by itself, can boot into mint, the problem i run into was that everything froze when installing nvidia drivers, and now i just get a black screen when trying to boot into. So im formatting the partitions now and one final times going to try ubuntu.

Well done. You got somewhere. :)

---

