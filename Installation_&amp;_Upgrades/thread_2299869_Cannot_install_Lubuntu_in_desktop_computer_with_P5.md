---
title: "Cannot install Lubuntu in desktop computer with P5KPL AM SE motherboard"
date: 2015-10-21
forum: Installation &amp; Upgrades
---

### Post by KayeNg on 2015-10-21
Hi guys.  In my working Lubuntu system, I made a Lubuntu live CD using the burning software Brasero.  (For some reason, the other computer in which Lubuntu is to be installed in cannot boot from flash drive, no matter what settings I try in BIOS, hence the need for live CD.)

I then insert the live cd onto the other computer.  It boots fine, I can even connect to the internet using the live CD.  But if I proceed to install it in the hard drive, I never seem to get pass the page where I type in the username, computer name, password, etc.  I always get a message like "Sorry, the installer crashed..."

I tried Bodhi Linux live CD, same thing--"Sorry, the installer crashed..." , so I guess I can rule out the possibility that the burn process was unsuccessful (?).  

I wonder if it has anything to do with the optical drive (dvd writer) being damaged a little; I have to insert a paperclip into the tiny hole in the front to force the tray to eject.  I assume it doesn't affect the Lubuntu installation since I can boot from it and even connect to the net using the live CD.

FYI, the computer is old, maybe around 2007 (?). The motherboard is asus P5KPL AM SE.

The hard drive is around 32-34 GB.  RAM is 1 GB

Help please! Thank you.

---

### Post by sudodus on 2015-10-22
If you run Lubuntu live, you run from a desktop iso file, and many of the current files are too big to fit in a CD (the limit is 703 Mibibytes) as shown by

```
ls -lh file.iso
```

To be exact, the limit is **737280000 bytes** =  737280000/1024/1024 Mibibytes = [B]703.125 Mibibytes
[/B]

For example, the following iso file is within CD size with a very small margin

```
[SIZE=3]ls -l lubuntu-14.04.2-desktop-i386.iso

-rw------- 1 sudodus sudodus 737[COLOR="#0000CD"]**1**[/COLOR]48928 feb 18  2015 lubuntu-14.04.2-desktop-i386.iso[/SIZE]
```

The alternate iso files are generally smaller. Even the brand new Lubuntu 15.10 i386 (32-bit) alternate iso file is within CD size.

If you can burn and run DVD disks, there is no problem with the size of the iso files.

I find ***k3b*** more reliable than Brasero for burning CD/DVD disks. Burn at the lowest speed available.

-o-

There may be a hardware problem somewhere else, for example in the motherboard itself, or in the HDD or in the RAM.

While booting from the CD, you can try ***memtest*** to test the RAM. Run for hours. One error is too much.

When running live, you can check the HDD.

- Check the S.M.A.R.T. information (with Disks)

- Check the file system(s) with tools suitable for whatever filesystems there are.

---

### Post by KayeNg on 2015-10-22
Sorry, it was burned on a dvd, and it works just fine. Just hours ago I used it to install Lubuntu 15.04 (?) on my laptop.  Everything went smoothly.  This live cd (or DVD) is NOT the problem, apparently.  (I used Brasero to burn the iso, by the way, and I don't think I burned it at the lowest speed.)

I was also successful in installing windows xp onto the old desktop computer, so I guess HDD problem can be ruled out too?  Or do I still have to check the s.m.a.r.t. information?  Sorry, I'm not anywhere near the computer right now.

About the RAM, do I just type memtest in terminal while running the live CD? I think it gave me an error message.

As for the motherboard, I seem to have successfully updated the BIOS by downloading P5KPL-AM-SE-0702.zip here:  
[http://www.asus.com/support/Download/1/22/45/11/29/](http://www.asus.com/support/Download/1/22/45/11/29/)           
The one under BIOS. If you access it via archive manager, you will see the modified date as August 26, 2010.    I have yet to try booting from live USB after the BIOS update. I'll try later.

If live CD still crashes, what next? Should I try really old versions of Lubuntu? Like something from 2007, if it exists?

---

### Post by sudodus on 2015-10-23
OK, I misunderstood. You are not limited by the CD size.

You find memtest in the grub menu.

There might be problems because of bad drivers for graphics or wifi. In such cases it might work better with an older linux version. But I would recommend a version that is still supported, so that you receive security updates. Ubuntu 12.04 LTS is the oldest supported version of Ubuntu. But it needs more horsepower and RAM, than what is available in that old computer, so I would recommend a light-weight community re-spin based on 12.04, for example ***Bento, Bodhi, LXLE,*** or ***ToriOS***.

If still problems, I suggest that you try ***Wary Puppy, TahrPup*** or ***Tiny Core***.

[COLOR="#696969"]*Only for testing:* If you do not intend to connect the computer to the internet, you can use old versions of linux without risk, for example Ubuntu 8.04 LTS or 10.04 LTS, but it is ***not*** what I recommend, and it will be difficult to install additional program packages.[/COLOR]

---

### Post by mörgæs on 2015-10-23
The motherboard is not that old. It has an LGA 775 socket which indicates that the hardware is not obsolete.

Have you tried the [minimal 15.10 ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")?

Yes, memtest would be interesting to see.

---

### Post by v3.xx on 2015-10-23
> **mörgæs said:**
> Have you tried the [minimal 15.10 ISO]("https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall")?

The mini iso is only 40MB in size, the installer downloads the packages from the internet.

Install instructions here
[https://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/](https://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/)

And in your case for installing a minimal Lubuntu install, you would enter one command.

```
sudo apt-get install lubuntu-core
```

or for a full desktop install

```
sudo apt-get install lubuntu-desktop
```

Here's the package lists
[http://packages.ubuntu.com/wily/lubuntu-core](http://packages.ubuntu.com/wily/lubuntu-core)
[http://packages.ubuntu.com/wily/lubuntu-desktop](http://packages.ubuntu.com/wily/lubuntu-desktop)

---

### Post by KayeNg on 2015-10-23
Hi guys, in Disks --> S.M.A.R.T. , what would you be looking for? Because the Read Error Rate has a value like 3132345646 something like that (I didn't write it down), but at the top I saw "Disk is OK".  So I guess the hard drive is ok? 

I don't know if I should proceed with memtest, it seems unnecessary so far;  I using windows xp right now as I'm typing this, and the system is really fast.  

I want to try the minimal install of Lubuntu 14.04.  I have downloaded the mini.iso (which is about 31 MB).  According to the installation instructions in [https://www.maketecheasier.com/insta...on-old-laptop/]("https://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/") , I should burn it to cd and boot from it.  Just one question, would I be given a choice between installing lubuntu-core and lubuntu-desktop?

Also, I still find it weird that I cannot use live USB on this old desktop computer, because to me it's not that old.  Can anyone confirm that P5KPL-AM SE really doesn't support usb booting?

---

### Post by sudodus on 2015-10-23
Yes, the installer in Ubuntu mini.iso would give you a choice between installing lubuntu-core and lubuntu-desktop (and many other alternatives too).

-o-

It is good that the HDD has a S.M.A.R.T. info telling it is OK.

But it is really rather easy to run memtest. Why don't you want to do it?

I cannot confirm anything about booting from USB, but it is possible in most computers that are less than 12 years old. See this link for some tips,

[FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

---

### Post by KayeNg on 2015-10-26
Hey guys, so I burned the mini install, boot the cd (or dvd), and it started with the installation process.  It went smoothly and I was able to choose "Lubuntu Desktop" as the one to be installed (others were kubuntu, etc. etc).  When it was done, I was prompted to remove the cd and restart.  I expected the computer to boot from the hard drive which I thought should now have the full lubuntu desktop operating system installed in it (or am I wrong?).     All I got was a terminal prompt.  Is this normal?

So I have no desktop screen, nothing whatsoever except the full black terminal screen.  So I typed 
sudo apt-get install lubuntu-desktop
and it began to install, again.  Towards the end there was a connection error, but it did finished.  I rebooted.  Still the same full black terminal screen.

What am I doing wrong?

---

### Post by v3.xx on 2015-10-26
Ok, that's weird. Try updating your system and post any errors you get.

```
sudo apt-get update && sudo apt-get dist-upgrade
```

Going back to your first post suggest other problems and I'm not sure what.

---

### Post by Ars_Ivci on 2015-10-26
Are you choosing the right architecture, 32/64 bit?

---

### Post by mörgæs on 2015-10-27
> **Ars_Ivci said:**
> Are you choosing the right architecture, 32/64 bit?

If that were the problem then we would have seen an explicit error message.

---

### Post by KayeNg on 2015-10-27
I'll try 
sudo apt-get update && sudo apt-get dist-upgrade
several hours from now as I'm not anywhere near the computer right now.

I have something to add, for now.  In this guide 

[https://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/](https://www.maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/)

...under the Post Installation part, it says

"Now that you have finished the installation, it is only half the  battle. You still need to install the desktop manager and several  required applications.
1. Restart the computer. Press “Alt + F1”  when the grub loader appears. This will bring you to the command prompt.  (If you didn’t press “Alt + F1, you will only see a blank screen)."

I didn't see any grub. There was no grub screen.  It was only the full black terminal screen like I said in my previous post.  No grub at all.

Then numbers 2 and 3 says

> 2. In the command prompt, first login with your username and password. Next, type the following:

[FONT=monospace][COLOR=#c20cb9]**sudo**[/COLOR] [COLOR=#c20cb9]**apt-get install**[/COLOR] gdm network-manager[/FONT]

This will install the *gdm* login manager and the *network-manager*. Optionally, you can replace the “gdm” with “lightdm” or “lxdm“. You can also use “*wicd*” as the alternative to network-manager.
3. Next, choose your desktop manager. You can choose to use Gnome, Openbox, LXDE, Fluxbox, XFCE, WindowMaker, etc.



If I want to install Lubuntu, do I use lightdm or lxdm?  For number 3, do I choose lxde?

---

### Post by v3.xx on 2015-10-27
The first part of that link (installing the mini.iso) was for you.  The second part will not apply to you.

I just skip down to the last check box and do a manual install.  Either using one of the commands in post#6 or creating if you just want lxde.  Lxde can also be added to Lubuntu and then you could choose which one to run.

Your display manager (lightdm) comes packaged with lubuntu and core package.

---

### Post by KayeNg on 2015-10-28
Success.  Lubuntu currently installed in hard drive.  I did it by using the same mini.iso that I used earlier, but instead of choosing "Lubuntu Desktop", I chose to do manual installation.  After it finished, I was prompted to restart the computer.  No grub, no desktop screen, still the same full black terminal screen.  So I typed 
sudo apt-get install lubuntu-desktop

then it finished. It did not restart by itself so I had to push the power button of the computer.  Then it was able to boot from the hard drive. 
Right now I am typing this within the Lubuntu system in the hard drive.  It has a few problems though.

1.  Internet connection icon that is beside the volume icon is missing/invisible.  It's just an empty space.  If I right-click the empty space, I
see:  Enable Networking, Connection Information, and Edit Connections.
If I click Connection Information, I get:
"Error displaying connection information:  No valid active connections found!"
This is all while the computer IS connected to the internet via tethering of my cell phone.  I can surf just fine.

2.  No sound even after installing pulseaudio volume control.  If I try to open pulseaudio, I get this:
> 
Connection to PulseAudio failed. Automatic retry in 5s
In this case this is likely because PULSE_SERVER in the Environment/X11 Root Window Properties or default-server
in client.conf is misconfigured.
This situation can also arise when PulseAudio crashed and left stale details in the X11 Root Window.
If this is the case, then PulseAudio should autospawn again, or if this is not configured you should run
start-pulseaudio-x11 manually.

If I type 
start-pulseaudio-x11
in terminal, I get:
Connection failure: Connection refused
pa_context_connect() failed: Connection refused
user@user:~$

3.  Is this a cause for concern?  Disks --> SMART Data and Self-test
Read Error Rate ----- Value is 48954363
because "...A non-zero value indicates a problem with either the disk surface or read/write heads."

4.  Still no GRUB screen.  It goes straight to Lubuntu system.

Thanks guys.

---

### Post by v3.xx on 2015-10-28
I can do #3, but you may have better luck starting new threads for new problems.

I have found the SMART test to be a reliable overview.  The read error is explained here.

[http://askubuntu.com/questions/20393/how-do-i-interpret-hdd-s-m-a-r-t-results](http://askubuntu.com/questions/20393/how-do-i-interpret-hdd-s-m-a-r-t-results)

---

### Post by KayeNg on 2015-10-28
Thanks for the SMART link!  I also want to ask, as I'm typing this using my laptop, SMART is indicating that the temperature is 47 degrees celcius.  Is this normal for laptops??

The desktop computer which I'm working on (the subject of this thread), was about 40 or 41 degrees while I was working on it.

Are these temperatures normal?

---

### Post by mörgæs on 2015-10-29
Yes, the temperatures are all right. 

It surprises me that you still have so many errors. Did you follow all advice given in the thread, especially using 15.10 and running the commands in post #10?

---

### Post by KayeNg on 2015-10-30
I believe I have followed all advice, EXCEPT using 15.10.  I believe I used 14.04

> user@user:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Lubuntu 14.04.3 LTS
Release:    14.04
Codename:    trusty
user@user:~$ 

GRUB screen is OK now; it's visible.  I think editing /etc/default/grub did the trick.  I added # to this line GRUB_HIDDEN_TIMEOUT=0

like so:

> #GRUB_HIDDEN_TIMEOUT=0

So, just to be clear, the problems left is

1.  Internet connection icon that is beside the volume icon is  missing/invisible.  It's just an empty space.  If I right-click the  empty space, I
see:  Enable Networking, Connection Information, and Edit Connections.
If I click Connection Information, I get:
"Error displaying connection information:  No valid active connections found!"
This is all while the computer IS connected to the internet via tethering of my cell phone.  I can surf just fine.

2.  No sound even after installing pulseaudio volume control.  If I try to open pulseaudio, I get this:
>  	 		 			 			 				Connection to PulseAudio failed. Automatic retry in 5s
In this case this is likely because PULSE_SERVER in the Environment/X11 Root Window Properties or default-server
in client.conf is misconfigured.
This situation can also arise when PulseAudio crashed and left stale details in the X11 Root Window.
If this is the case, then PulseAudio should autospawn again, or if this is not configured you should run
start-pulseaudio-x11 manually. 			 		

 	
 


Everything else seems fine.  I'll try installing the epson printer.

---

### Post by sudodus on 2015-10-30
Sometimes you need to play a music file or a video clip with audio for a long time and at the same time run ***pavucontrol*** and use the menus to *change the settings in as many menus as you can think of*. Finally you might find the correct setting, and you will hear the music.

---

### Post by KayeNg on 2015-10-30
Yes sudodus, I've tried that before and it worked on my other desktop computer.  On this desktop computer that I'm working on right now, the problem is the pavucontrol doesn't even open, so I can't adjust anything.  I get this message insead.
> 
Connection to PulseAudio failed. Automatic retry in 5s
In this case this is likely because PULSE_SERVER in the Environment/X11 Root Window Properties or default-server
in client.conf is misconfigured.
This situation can also arise when PulseAudio crashed and left stale details in the X11 Root Window.
If this is the case, then PulseAudio should autospawn again, or if this is not configured you should run
start-pulseaudio-x11 manually.

---

### Post by sudodus on 2015-10-30
1. What happens when you run

```
start-pulseaudio-x11
```

2. Are you still running the version **15.04**? What happens when you run a ***live*** session (booted from a DVD/USB drive) of

2.1 Lubuntu
2.2 Xubuntu
2.3 Another version of Lubuntu or Xubuntu: 14.04.1, 14.04 .2, 15.10
2.4 A community re-spin based on Ubuntu 12.04 LTS, for example Bento, Bodhi, LXLE?

---

### Post by KayeNg on 2015-11-04
I repeat the whole installation process.  The sound is working now.  The internet connection icon is visible but doesn't change appearance when it's connected; it always showing as disconnected.  Small problem, no biggie.  Everything else seems fine.  I'll mark this thread as solved now.  I guess what helped me the most are these suggestions:

1.  Use mini.iso , as first suggested by [**[COLOR=#DD4814][B]mörgæs**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=939075")

2.  Instead of choosing to install Lubuntu-desktop, I chose the manual install as suggested by [**[COLOR=#000000]v3.xx[/COLOR]**[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=1937239") in post #14

Thanks a lot everyone!!!

---

