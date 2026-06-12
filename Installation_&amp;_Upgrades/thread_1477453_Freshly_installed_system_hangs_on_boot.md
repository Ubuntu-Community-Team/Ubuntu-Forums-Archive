---
title: "Freshly installed system hangs on boot"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by nac.est on 2010-05-08
I've just installed Ubuntu 10.04 netbook remix on an acer Aspire One D250, specs below:
Processor Name: Intel Atom N270
Processor Speed: 1.6 GHz
RAM: 1 GB
Graphics Card: Intel Graphics Media Accelerator 950
Storage Capacity: 160 GB

I had to resize the win partition, making a new partition for Ubuntu of about 15GB. I then installed the system. Everything went without problems.
I was able to boot once, and verified that everything worked as intented.

However, after that, 90% of the times I reboot the bootup process hangs at a blank screen (with a blinking underscore), immediately after grub selection.
If I select "recovery mode" in grub I can see the bootup messages, but the process hangs, all except one time, right after:
```

[2.304418] ata2: DUMMY
[2.304487] ata3: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344200 irq28
[2.304584] ata4: DUMMY

```
and does nothing more. There are no error messages or hints to the source of the problem, to my eyes.
I've noticed that sometimes even the loading screen of the live cd will hang indefinitely, leaving me no choice other than a hard-reboot.

The rare times that the system does boot normally, everything works normally.
I've tried installing using both the ext4 and ext3 filesystems.

I couldn't find anything like this on the forums. Am I doing something wrong?
Do you need more details?

---

### Post by fleder on 2010-05-09
Same here with HP Compaq Mini 110c - the hardware specs are exactly the same.

I stuck to ext2 for a separate /boot partition and ext3 for the system root (/).
Also, there is a Windows XP Professional installation alongside.

```
[       1.272502] ata4: DUMMY
```is the last line it is displaying.

Ubuntu 10.04 i386 Netbook Remix

---

### Post by fleder on 2010-05-09
I managed to get it boot up once by switching it off, taking out the battery, putting it back in, hooking the netbook up to the power supply and plugging in the LAN connection I used for installing Ubuntu (regular GRUB boot option).

When I was in the lucky situation to have a running system I took advantage to do both "sudo aptitude update" and "sudo aptitude full-upgrade" and install the proprietary Broadcom WLAN device driver.

Since then it has been starting up reliably.

---

### Post by hnavag73 on 2010-05-09
> **fleder said:**
> I managed to get it boot up once by switching it off, taking out the battery, putting it back in, hooking the netbook up to the power supply and plugging in the LAN connection I used for installing Ubuntu (regular GRUB boot option).

When I was in the lucky situation to have a running system I took advantage to do both "sudo aptitude update" and "sudo aptitude full-upgrade" and install the proprietary Broadcom WLAN device driver.

Since then it has been starting up reliably.

I did that with my Aspire One D250 and it did the update & upgrade, but after doing the required restart it didn't boot :( it just showed the blank screen with the blinking cursor... anyone has another solution???

---

### Post by nac.est on 2010-05-10
Sorry for the late update, but I may have found a solution/workaround.
If you add the "nolapic" kernel option to the bootup script, the system does boot (almost) normally. The only glitch is that it takes a few seconds more than I'd expect and it very briefly displays a couple of warning/error messages that I can't read. After that, however, everything is fine.

For instructions on how to add the option, see [_this thread_]("http://ubuntuforums.org/showthread.php?t=1195275"). I simply added nolapic inside the quotes after GRUB_CMDLINE_LINUX_DEFAULT in /etc/default/grub, and ran sudo update-grub.

Unfortunately I'm not knowledgeable about kernels and their options, so I'm not totally confident the consequences of adding nolapic.

---

### Post by yonagi on 2010-05-12
> **nac.est said:**
> Sorry for the late update, but I may have found a solution/workaround.
If you add the "nolapic" kernel option to the bootup script, the system does boot (almost) normally.

I just installed 10.04 UNR on my Gateway LT2030u and had the same issue on reboot. This netbook uses the same processor and graphics card with the same amount of RAM. I managed to finally get into the installation to add "nolapic" as you recommended. Five test reboots later, and I've yet to see any issues. Unfortunately, I'm also not certain what "nolapic" does, so I've got something to Google later today!

---

### Post by hnavag73 on 2010-05-15
finally got the booting sorted out with this:

gksudo gedit /etc/default/grub

add it to the GRUB_CMDLINE_LINUX_DEFAULT line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hpet=force nolapic"

save the file then run

sudo update-grub

---

### Post by visionjinx on 2010-05-15
> **nac.est said:**
> I've just installed Ubuntu 10.04 netbook remix on an acer Aspire One D250, specs below:
Processor Name: Intel Atom N270
Processor Speed: 1.6 GHz
RAM: 1 GB
Graphics Card: Intel Graphics Media Accelerator 950
Storage Capacity: 160 GB

I had to resize the win partition, making a new partition for Ubuntu of about 15GB. I then installed the system. Everything went without problems.
I was able to boot once, and verified that everything worked as intented.

However, after that, 90% of the times I reboot the bootup process hangs at a blank screen (with a blinking underscore), immediately after grub selection.
If I select "recovery mode" in grub I can see the bootup messages, but the process hangs, all except one time, right after:
```

[2.304418] ata2: DUMMY
[2.304487] ata3: SATA max UDMA/133 abar m1024@0x58344000 port 0x58344200 irq28
[2.304584] ata4: DUMMY

```and does nothing more. There are no error messages or hints to the source of the problem, to my eyes.
I've noticed that sometimes even the loading screen of the live cd will hang indefinitely, leaving me no choice other than a hard-reboot.

The rare times that the system does boot normally, everything works normally.
I've tried installing using both the ext4 and ext3 filesystems.

I couldn't find anything like this on the forums. Am I doing something wrong?
Do you need more details?


Hi Group, I am new to this forum (first post infact) and wanted to add to this also as I had the very same experience. 

I tried the live version first and all seemed to be OK, so I installed it and same issue as the original poster.

I just got a blank screen with a flashing cursor, I could get it to boot very rarely (about the same 90% failure) and when digging I got the same thing as well, things seemed to hang at 

ata4: DUMMY

I even had quite a few issues trying to get into the recovery mode when presented with the boot options (trying to get to a basic root command line I could use).

Just wanted to add to this post as I am having the same issues as well and hope the Ubuntu team can find the issue and get a fix out for what ever is causing this. I am not new to linux (CentOS/RHEL is mainly what I work with) but am pretty new to Ubuntu, although I had installed and played with some of the earlier versions a bit.

Some info on my system:

I just installed Ubuntu 10.04 netbook edition on my Compaq Mini (Compaq Mini CQ10) and it has basically the same specs as the original poster, I have it dual boot with the WIndows XP Home version that it came with (just incase I needed to revert to it for whatever reason, but do prefer linux most definitely, which is why I am trying this distro out)

I tried the suggestions posted here and it did seem to boot although I am not sure if this is a fix for the issue or if it will resurface again. (Haven't played with it long enough to know yet)

When I did get it first booted before (although it did hang when first rebooting after install) I did do the updates immediately so am not sure if there was something in there or what that caused this.

I plan on installing the desktop release a bit later today (on a desktop system) so hopefully I wont have this issue again and it's just restricted to netbooks. This version does look pretty cool though so am pretty stoked to give it a go! :)

Thanks for your time! 
Vision Jinx

---

### Post by Hippy Tesla on 2010-05-22
MY SOLUTION THAT WORKED:

I had the same problem after installing 10.04 on my netbook a few hours ago. Then I read this thread, and tried things you guys posted, but nothing happenned. Just the black screen with a blinking cursos, or in diagnostic mode "ata 4 DUMMY" error.

Then I disabled my wireless adapter as a boot device from BIOS (the adapter is Broadcom 43xx), and it booted. Although it couldn't detect my home wireless SSID (the wireless LED is blue, which means it's enabled and drivers are loaded), I connected the LAN cable and ran the complete system update. It's still downloading, so I'll let you know if that completely fixes the problem :)

This adapter had problems with Windows XP (for some reason recognised by Ubuntu and PartitionMagic 8.0 as Windows Vista) until I updated its driver for two times, until it worked.

---

### Post by spotted zebra on 2010-05-26
> **hnavag73 said:**
> finally got the booting sorted out with this:

gksudo gedit /etc/default/grub

add it to the GRUB_CMDLINE_LINUX_DEFAULT line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hpet=force nolapic"

save the file then run

sudo update-grub

thanks so much for this it worked perfectly.

a word to anyone getting frustrated just keep turning it off and on until your system boots. i had to do it about 15 times before it got one to take. after that is it is a small amount of code editing and you are home free.

does anyone know how to speed up the boot at all. this snippet of code really seems to slow it down. i am not complaining because it works now but i would like to optimize my system.

thanks again to all. do i hear a sticky for this thread in solving the problem?????

one last thing can someone point me to where it explains what this code means? i can do things blindly but i would like to have a basic understanding of what i did.

---

### Post by JulianHarty on 2010-06-08
> **spotted zebra said:**
> thanks so much for this it worked perfectly.

a word to anyone getting frustrated just keep turning it off and on until your system boots. i had to do it about 15 times before it got one to take. after that is it is a small amount of code editing and you are home free.

does anyone know how to speed up the boot at all. this snippet of code really seems to slow it down. i am not complaining because it works now but i would like to optimize my system.

thanks again to all. do i hear a sticky for this thread in solving the problem?????

one last thing can someone point me to where it explains what this code means? i can do things blindly but i would like to have a basic understanding of what i did.

Another tip is to add the parameters in GRUB command line, which is available at startup. I simply added:  [FONT=Courier New]hpet=force nolapic[/FONT] after [FONT=Courier New]quiet splash[/FONT] before booting my sulking netbook, and I was then able to login and add the parameters to /etc/default/grub as the post explained.

Thanks all for helping me get my Acer Aspire One to boot again after enabling the proprietary b43 network drivers in lucid linx 10.04

---

### Post by Jammyc on 2010-06-08
> **hnavag73 said:**
> finally got the booting sorted out with this:

gksudo gedit /etc/default/grub

add it to the GRUB_CMDLINE_LINUX_DEFAULT line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hpet=force nolapic"

save the file then run

sudo update-grub
Sorry to necrothread, but is there any chance someone could explain to a complete noob what this means? I can edit it at the grub menu and log in. Just wondering how to make that permanent?

---

### Post by nac.est on 2010-06-08
> **Jammyc said:**
> Sorry to necrothread, but is there any chance someone could explain to a complete noob what this means? I can edit it at the grub menu and log in. Just wondering how to make that permanent?

After you've successfully logged in Ubuntu, open a terminal and paste
```
gksudo gedit /etc/default/grub
```
in it. It will ask for your password and then open the editor with the configuration file. Look for the line that starts with
```
GRUB_CMDLINE_LINUX_DEFAULT
```
and change it so that it looks like this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hpet=force nolapic"
```
save the file and then, in the terminal, execute
```
sudo update-grub
```

After that the change should be permanent.

---

### Post by Joshun on 2010-06-08
@JammyC: Go into terminal (Apps>Accessories>Terminal). Type in the first command:
```
gksudo gedit /etc/default/grub
```
find the line that reads > GRUB_CMDLINE_LINUX_DEFAULTchange everything in the quotation marks to ```
quiet splash hpet=force nolapic 
```so that the line should now read:
```
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hpet=force nolapic" 
```click save and close the editing window
now type into terminal ```
 sudo update-grub 
```and reboot.

---

### Post by irvie on 2010-06-21
Just chiming in that I am experiencing the same issue and am looking for a permenant fix that doesn't involve disabling APIC.

Workaround is working for me, but has anyone filed a bug report?

---

### Post by Devotus on 2010-07-31
> **Joshun said:**
> @JammyC: Go into terminal (Apps>Accessories>Terminal). Type in the first command:
```
gksudo gedit /etc/default/grub
```
find the line that reads change everything in the quotation marks to ```
quiet splash hpet=force nolapic 
```so that the line should now read:
```
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash hpet=force nolapic" 
```click save and close the editing window
now type into terminal ```
 sudo update-grub 
```and reboot.
 
I am new to the forums guys, my name is Peter, from Florence, Italy.
 
THANK YOU VERY MUCH for your help!!
 
I fixed all with this solution, but one more question remain to answer for anyone that need to know: how to have a succesfull login to Ubuntu?
 
I don't know how and why, but at the first menu screen (the very first list of kernel boot options) (1) I choosed "e" option and (2) pressed Ctrl-x to boot; after 20 seconds I could then log in. That worked for me, but dunno if it could help somebody else.
 
Anyway thank you again from a NOOOOOOB!     
 
Peter

---

### Post by moloboo on 2010-08-27
Well, I have the same problem as you, but my computer is an spanish one, do somebody know how I could write the caracter "=" ?...I know is a little big problem...

---

