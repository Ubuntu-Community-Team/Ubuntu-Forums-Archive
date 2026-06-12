---
title: "Install Ubuntu over Ubuntu game pack"
date: 2021-10-19
forum: Installation &amp; Upgrades
---

### Post by pussekatt on 2021-10-19
I have Ubuntu game pack installed on my laptop and I dont like it,so I am trying to install Ubuntu 20.04.20.According to the instructions I can just place it in the DVD drive and it will install.I have tried this and nothing happens.All I get is Ubuntu 20.04.20 flashes up in the top centre of the screen and thats it,nothing more.How can I install Ubuntu ? as I really dont like the game pack but I had Lubuntu installed before and I did like that.
One more thing that might help.My laptop is a Lenovo G 40-30 and it is very hard to get into the BIOS to force it to boot from CD/DVD.
Any help would be much appreciated,thank you.

---

### Post by tea for one on 2021-10-19
> **pussekatt said:**
> My laptop is a Lenovo G 40-30 and it is very hard to get into the BIOS to force it to boot from CD/DVD

In order to boot into a live session/installer of the Ubuntu family, you have to set the boot order of the DVD or USB.
This link offers information for your PC [https://support.lenovo.com/gb/en/solutions/ht500216](https://support.lenovo.com/gb/en/solutions/ht500216)

---

### Post by pussekatt on 2021-10-20
Thank you for your quick reply.I tried that Lenovo site before going on this forum.They reccomend using the special reset button/F2 or Fn and F2.I have tried all of these and this PC is VERY hard to get into the BIOS ( as I mentioned in my post ) apart from that though.The Ubuntu site says that all I need to do is insert the DVD and I get the option to install or try but as I said above I dont get this option ?!
Is there some way that I can get the PC to load the DVD after I am in Games pack ?

---

### Post by TheFu on 2021-10-20
Most Linux installers only work from a boot from the install disk, so there isn't a way to force install from a different release (whatever Ubuntu game pack is?).  I've never heard of *Ubuntu game pack* before, BTW.

I wouldn't use a DVD. I'd use a flash USB drive or SDHC flash storage to put an ISO onto (it can't just be copied onto an existing file system), then I'd use the boot menu from the computer BIOS to have it boot from whatever flash storage I inserted.  **sudo cp /path/to/ubuntu-xx.yy.iso /dev/sdz** is an example command. The "sdz" part needs to be correct for the flash storage to be used for the installer.  Do not point it at any HDD or SSD where you plan to install. That would cause a very bad day.

BTW, I have a 7 yr old system that doesn't like to let me into the BIOS too.  Usually takes 5-10 attempts for the key to be registered before it just boots into the default OS on the disk.  I have a few systems here and only that 1 has the issue and in 30 yrs dealing with computers, this single machine is the only one with the problem that I can recall ... well ... that was still booting at all. I have replacement for the guts of that system, just need some new RAM before it can be swapped out for a new motherboard, new cpu. Hopefully today I'll get to pick up the last missing parts.

---

### Post by grahammechanical on 2021-10-20
How did you install Ubuntu Game Pack? How did you install Lubuntu? Or, did someone else do it for you?

[https://ualinux.com/en/news/ubuntu-gamepack-20-04-release-platforms-for-running-games](https://ualinux.com/en/news/ubuntu-gamepack-20-04-release-platforms-for-running-games)

We need to do more than copy the Ubuntu ISO image to a DVD disc. We need to burn it to create a bootable DVD disc that will load Ubuntu. 

[https://ubuntu.com/tutorials/burn-a-dvd-on-ubuntu#1-getting-started](https://ubuntu.com/tutorials/burn-a-dvd-on-ubuntu#1-getting-started)

If we do not burn the ISO image to the DVD then the OS will simply see that there is a DVD disc in the DVD drive and register it as available for the user to access through the file manager. This will happen even if we have correctly burned the ISO image to the DVD disc and then put the DVD disc into the DVD drive whilst still running the original operating system. This is what I think that you are doing.

It is not possible to install an operating system over an existing operating system while we are running the existing operating system. We shutdown the operating system and power off. We put the DVD disc in the DVD drive and power back on and if the BIOS has been set to look for an operating system on the DVD drive before looking for an operating system on a hard drive then the Ubuntu live session will load.

It is true that the official instructions do make some assumptions about the knowledge of the potential Ubuntu user but they do say: "Restart the computer" in addition to "Put the Ubuntu DVD into your optical/DVD drive." If the BIOS is not set to look for an operating system on a DVD drive first, then your machine will load Ubuntu Games Pack and that operating system will not and cannot load the Ubuntu live session. This, on reflection, I think is what is happening for you.

Regards

---

### Post by tea for one on 2021-10-20
Assuming you have installed Ubuntu Games Pack in UEFI mode and that you can access a terminal, you could try:-
```
sudo systemctl reboot --firmware-setup

```

---

### Post by pussekatt on 2021-10-25
Yes,this laptop that I am using is a real pain to get into the BIOS.Sounds like the trouble you had.The problem is also that it takes about 3 minutes for Ubuntu Game pack to load before I can try a restart and try to enter the BIOS again,very time consuming,thats why I was hoping to install Ubuntu from the DVD

---

### Post by pussekatt on 2021-10-25
I burnt the Ubuntu DVD to disk.
I installed Lubuntu alongeside Windows just from putting the DVD in the drive thats why I was hoping to do the same with Ubuntu.
The thing is I liked Lubuntu but I thought it was too light so I installed the Ubuntu game pack but that is much too slow.I have now decided to go with the full Ubuntu instilation which is what I am trying to do here.

---

### Post by pussekatt on 2021-10-25
Thanks,I can do all that you suggest and I will try what you say tomorrow.Will let you know how I get on.

---

### Post by MAFoElffen on 2021-10-26
I do Warranty FRU for Lenovo, Dell and HP... hitting F2 repeating on boot will get you to the BIOS setup. BUT...

What you really need to do is on boot, keep hitting the F12 key will bring up the temp Boot Menu, so you can select an alternative media to boot from. I would create a USB Key to install from. DVD? What model Lenovo do you have and how old?

Me too: What is "Ubuntu Game Pack?"

---

### Post by pussekatt on 2021-10-28
My Lenovo is a G40 and its about 5 years old ( it came with Windows 8.1 installed ) I will definately try F12.I have been trying the "One Touch"reset but it only works sometimes.
Ubuntu Gamepack is from a Russian developer.It has Ubuntu 20.04 installed and all the software you need for playing games,eg Play on Lynux,Wine,Wine tricks etc.The main problem is that it is Sooooooo slow.It takes 3 minutes just to boot ( thats another reason I am having so much trouble getting into the BIOS ) 10 minutes to reboot 3 times,I get bored to tears.
Anyway,what I want to do is install Ubuntu 20.04 with only a couple of programes eg Dosbox and about 3 emulators and use the rest for learning Ubuntu.

---

### Post by TheFu on 2021-10-28
Boots on modern hardware should take 10-50 seconds.
A few systems here:
```

# ##############[ 40TB of storage, no SSD; 20K passmarks ]##############
$ systemd-analyze 
Startup finished in 5.049s (kernel) + 38.435s (userspace) = 43.484s
graphical.target reached after 38.431s in userspace

# ##############[ KVM Host w/  SSD & 1TB storage; 13K passmarks ]##############
$ systemd-analyze 
Startup finished in 9.212s (kernel) + 43.249s (userspace) = 52.462s
graphical.target reached after 14.111s in userspace

# ##############[ KVM Host w/13TB of storage, no SSD; 2.4K passmarks ]##############
$ systemd-analyze
Startup finished in 40.694s (kernel) + 1min 10.501s (userspace) = 1min 51.196s
graphical.target reached after 1min 10.487s in userspace
```

The first two systems are Ryzen 5s.
The last one is a 1st generation Core i5 - 11 yrs old and has 2 RAID1 arrays. This system doesn't actually have a working GPU.

**Something seems really wrong with "Ubuntu Game Pack".**

My 20.04 desktop runs inside a virtual machine on the 2nd system above.
```
$ systemd-analyze
Startup finished in 2.367s (kernel) + 5.170s (userspace) = 7.538s 
graphical.target reached after 5.145s in userspace
```
As you can see, it boots crazy fast, but it skips nearly all hardware checks since only virtual hardware is provided. The only aspect that might be considered "slow" is the virtual GPU - which uses QXL/SPICE.  For non-gaming GPU work, it is plenty fast.  However, TuxRacer can bring the graphics system to be slow.

If you'd like to know more about systemd-analyze, there's the manpage. It has other options that are useful. In general, on poorly setup system, a boot to login longer than 1 minute isn't something to expect. If you have that, there is lots of junk in the startup that just isn't needed/wanted.

BTW, it is safe to reboot using buttons while the grub screen is displayed.  After that, we need to wait for the OS, login, then use **sudo shutdown -r now** for a clean reboot.  Something is less clean when using **sudo reboot**, though I don't know what exactly.  Just that reboot is way too quick, so I know it doesn't do the same clean shutdown of processes, files, logs, before completing.

And lastly, be certain you patch at least weekly.  That's
```
sudo apt update
sudo apt full-upgrade
```
This will get new kernels, which is where most hardware support comes. It is possible to get newer kernels, but not recommended for someone new. Stick with those provided by Canonical's repos.
Every few weeks, run
```
sudo apt autoremove
sudo apt autoclean
```

If you want a system that always boots, don't automate these steps.

---

### Post by TheFu on 2021-10-28
Just watched this ... gaming on Linux with Pop! OS.  It's from Linus Tech Tips (3 months old), which is mostly about high-end gaming and less about Linux, but this episode is 100% Linux gaming.
[https://youtu.be/_Ua-d9OeUOg](https://youtu.be/_Ua-d9OeUOg)
Get ready to pause - he goes way too fast.  No VM. No passthru.  Looks to be all point-n-click. I think much of the ease has to do with the OS he selected and having newer versions than I have. That's on me. I'm not ready to run 20.04 on hardware yet.

---

### Post by pussekatt on 2021-10-29
@ tea for one  I entered that code you suggested in the terminal and it looks like it could work,but after entering the code the terminal asks me for my password.As there is only the wife and myself and the wife is not interested in computers,I dont use a password,so I am stuck at that point.

---

### Post by pussekatt on 2021-10-29
I know that Ubunto Game Pack takes much too long to load ( 3 minutes and 2 minutes to shutdown ) thats why,
1 - I want to uninstall it
2 - I want to install Ubuntu and set it up myself
3 - Thats why its taking me so long,because,just 3 restarts will take about 15 minutes.
I had a virus on my Windows PC once that slowed my PC down,but no where as slow as Ubuntu game pack.

---

### Post by pussekatt on 2021-10-29
I just watched that link you posted and I am impressed.I am trying to change to Linux because I have had it with MS and their pathetic ways.After watching that video I am going to look into Pop os.

---

### Post by tea for one on 2021-10-29
> **pussekatt said:**
> @ tea for one  I entered that code you suggested in the terminal and it looks like it could work,but after entering the code the terminal asks me for my password.As there is only the wife and myself and the wife is not interested in computers,I dont use a password,so I am stuck at that point.

Your installation of Ubuntu Game Pack did not require a login password?
That seems unusual.

Try the command without sudo and, if it fails, please post the exact error message.

Have you tried the suggestion by MAFoElffen from post 10?

---

### Post by TheFu on 2021-10-29
> **pussekatt said:**
> I just watched that link you posted and I am impressed.I am trying to change to Linux because I have had it with MS and their pathetic ways.After watching that video I am going to look into Pop os.

Don't be too impressed unless you have the same hardware.  

He was probably running a Core i9 w/ 64G of RAM and nvidia 3060 GPU and 2TB 4x NVMe storage. The important part is that someone, somewhere, is running Linux and gaming.  BTW, it isn't me. ;)

Also, when replying, please quote a bit of the message you are responding to - otherwise we can't always tell.

---

### Post by pussekatt on 2021-10-31
The Game pack did need a password but all I did when setting up the OS was hit enter when asked for a password.So,when that code you gave me asked for a password,I just pressed enter  but it would not accept that ?!

---

### Post by pussekatt on 2021-10-31
Success.Thank you all for all your input.I have learnt some very usefull things in this thread that im sure will help me in the future.
I manager to install Ubuntu 20.04.I switched of my laptop and tried the "1 button reset,for the 10th time" and it worked,so I have finally managed to get rid of Ubuntu game pack,what a terribly slow piece of software.
Now,as I get more into Linux/Ubuntu I am sure you will see more questions from me on these forums.
So,thank you all again,very much.Your help and advice was much appreciated.

---

### Post by TheFu on 2021-10-31
> **pussekatt said:**
> The Game pack did need a password but all I did when setting up the OS was hit enter when asked for a password.So,when that code you gave me asked for a password,I just pressed enter  but it would not accept that ?!

Well, that's a bad choice.  Unix-like OSes need a password.  You can try to set one now using the **passwd** command.

---

### Post by MAFoElffen on 2021-10-31
Working on the newer systems daily, I have had to learn lots of tricks  to get into their BIOS settings, and to be able to Boot from my  (Branded) advanced Technician Diagnostics USB Keys... It is sometimes  hard even for me, on some systems. I can understand it being hard for  Users. 

The one's I still have challenges with are the certain specifically unnamed (for security reasons) BIOS's, when their BIOS Settings are locked down, the  SmartCard Reader systems are failed and you need to diagnose 'which'  specific part of that SmartCard Reader system has 'failed'. Security is key, but if you  have lost physical security (physical possession of), there 'are'  ways...

*** FYI ***
On The EFI Boot Menu's:
Most now also include a way into the BIOS Firmware Settings. Some will add a way to turn off 'SecureBoot' as a specific menu item. This menu option is handy and makes things a lot simpler.

But still "some", where the BIOS is locked down, will now exclude USB booting from even being recognized even if USB booting is the only option changed to enabled in the BIOS... Until you go further into the BIOS and change some other settings... This makes things challenging. Because you get to the Boot Menu, and don't see the USB Keys in the Boot Menu. That is a clue that something needs to be changed in the BIOS Firmware for those to be recognized. 

Then again, some now do not show the USB devices (directly), but have a 'Boot-By-File' menu option, where you have to select to boot the specific UEFI boot file in the 'found' EFI directory's. Going down through those menu levels, then you see the devices, and the files within the EFI directories of those devices.

---

