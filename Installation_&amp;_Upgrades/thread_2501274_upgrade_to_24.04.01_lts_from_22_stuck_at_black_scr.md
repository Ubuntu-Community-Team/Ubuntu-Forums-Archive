---
title: "upgrade to 24.04.01 lts from 22 stuck at black screen login"
date: 2024-09-30
forum: Installation &amp; Upgrades
---

### Post by rapattack on 2024-09-30
sorry i am not going to be good at describing whats happening but here goes. i did google a lot but due to disability i can read on forever to find solutions. scanning pages confirmed none of them matched anyway. my desktop computer is stuck at 'xxxxxxx-system-product-name login:'
when i shutdown via the power button it shows the purple screen with ubuntu 24.04.01.
i tried booting using ctrl-alt-f1 then f2 then on and on to f8 but nothing happened. i am unsure of the timing. should i have my fingers on those keys prior to pressing power button? then from there i was unsure but nothing happening so no good. i have seen i should log into grub but been years since i have done that and when i google that info it doesnt match this version of ubuntu and makes no difference or the info is incomplete. especially since due to disability i am still probably a beginner. bear with me as i have to keep pulling out a laptop in a small space and dont often have the energy to proceed for a couple of days

---

### Post by rapattack on 2024-09-30
......................................................

---

### Post by oldfred on 2024-09-30
What brand/model system?
What video card/chip?

If UEFI install, you press escape just after UEFI/BIOS screen but before grub menu would normally appear. Timing can be critical.
Then you may be able to boot grub recovery mode.

Did you name the user & system "xxxxxxx-system-product-name" so you are getting non-gui log-in?
Does it then not let you type your password? It will not show that you are typing or show any characters.

---

### Post by rapattack on 2024-10-01
> **oldfred said:**
> What brand/model system?
What video card/chip?

If UEFI install, you press escape just after UEFI/BIOS screen but before grub menu would normally appear. Timing can be critical.
Then you may be able to boot grub recovery mode.

Did you name the user & system "xxxxxxx-system-product-name" so you are getting non-gui log-in?
Does it then not let you type your password? It will not show that you are typing or show any characters.

its an onboard video. i cant remember my boards brand and the machine is a nightmare to pull out from its place. i am injured right now so will be weeks before i can remove it then open. i really should write down this info .
i dont remember what install it is sorry. the bios screen doesnt show. i cant remember why or i did something years ago.i dont see any menu. yes i dont know the timing.
i didnt name it with the xxxxx. its just my real name . i replaced the real name with xxxx for this post . non gui login yes but cant login. oh i didnt think it was asking me for my password . i presumed since it doesnt present like a real login. so i was able to type my password which shows but when i press enter nothing happens

---

### Post by oldfred on 2024-10-01
Do you get grub menu? or if BIOS install hold shift key from vendor UEFI/BIOS screen, or if UEFI press Escape key just after UEFI/BIOS screen.
Then boot recovery mode?

If you can boot live installer, you can get lots of detail on your system.
Have you updated UEFI/BIOS firmware to latest available. And if SSD its firmware? 
Even older system may have an update. My system from 2017 had several updates, but nothing lately.
Compare to vendors support site
sudo dmidecode -s bios-version
udisksctl status

Summary hardware info
inxi -Fxz
Even more concise
inxi -bz

If older system with limited hardware Ubuntu is too much system. It now is for newer systems.
Ubuntu would not even install on my 2006 laptop, even though server & Kubuntu did install.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

### Post by rapattack on 2024-10-02
> **oldfred said:**
> Do you get grub menu? or if BIOS install hold shift key from vendor UEFI/BIOS screen, or if UEFI press Escape key just after UEFI/BIOS screen.
Then boot recovery mode?

If you can boot live installer, you can get lots of detail on your system.
Have you updated UEFI/BIOS firmware to latest available. And if SSD its firmware? 
Even older system may have an update. My system from 2017 had several updates, but nothing lately.
Compare to vendors support site
sudo dmidecode -s bios-version
udisksctl status

Summary hardware info
inxi -Fxz
Even more concise
inxi -bz

If older system with limited hardware Ubuntu is too much system. It now is for newer systems.
Ubuntu would not even install on my 2006 laptop, even though server & Kubuntu did install.
[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

i dont know how to get the grub menu. bios anything doesnt show during boot. i dont know what boot recovery mode is sorry.
sorry dont know what boot live installer is. i know what a live dvd is but thats not how i installed the os. i have never done live usb .
sorry cant get into anything to find any info. i do have an ssd drive thatis the master drive that was installed last year.....do u need info on that?

my machine is not terribly old so that wouldnt be the issue. sorry i did a lot of research and forgot it all due to disability but i know the age of the hardware is not the issue. i see a lot of ppl complaining on the net about this upgrade. wish i looked for that prior but fatigue made me hit the upgrade thing and leave the machine alone for a while. sorry if i dont include enough info. i know my machine is good hardware wise

---

### Post by oldfred on 2024-10-02
I did not think Ubuntu installed via DVD for several years as ISO is too large.
So are you using one of the lightweight flavors that has a smaller ISO?

I stopped using DVDs years ago when flash drives dropped a lot in price. Flash drives were reusable, where DVD was a one time write. And often burned a "coaster" or bad burn. I actually used one as a coaster for years.

When you turn on computer it should show vendor's logo. Then if BIOS boot install, hold shift key until grub menu appears and second line in grub menu is recovery mode.

---

### Post by grahammechanical on 2024-10-02
> non gui login yes but cant login. oh i didnt think it was asking me for  my password . i presumed since it doesnt present like a real login. so i  was able to type my password which shows but when i press enter nothing  happens

A non gui login means that you are logging into Linux and the desktop environment has not loaded. You need to use commands. What is the command to start the desktop environment? I do not know. It may be possible for you to update/upgrade the operating system.

```
sudo apt update
```

```
sudo apt upgrade
```

Does that work?

To shutdown the system

[code]sudo shutdown --halt now]

should shutdown the system

Regards

---

### Post by rapattack on 2024-10-03
> **oldfred said:**
> I did not think Ubuntu installed via DVD for several years as ISO is too large.
So are you using one of the lightweight flavors that has a smaller ISO?

I stopped using DVDs years ago when flash drives dropped a lot in price. Flash drives were reusable, where DVD was a one time write. And often burned a "coaster" or bad burn. I actually used one as a coaster for years.

When you turn on computer it should show vendor's logo. Then if BIOS boot install, hold shift key until grub menu appears and second line in grub menu is recovery mode.

oh ok yes been a while since i have done that. i didnt install via dvd. i installed via the os. the thing that pops up and says u need to upgrade. i am using ubuntu lts
yes defeinately good reason to use usb instead. i do have a new 16gb one. i used old dvds for scaring birds away from the porch because they used to fly in and smack into my windows lol. after a few years the birds stopped doing it and by then the dvds dropped off during strong weather. sorry birds 
yes i dont see the bios thing at all. vendors logo thats possible. i will take another look after i type out what happened. i was able to login today. i dont know why it didnt work before. i ran sudo apt full-upgrade and i got 

the following package is automatically installed and is no longer required: acpid
use 'sudo apt autoremove' to remove it.

#
#patches available for packages affected by cups remote code execution issue
#tracked by cve-2024-47076, cve-2024-47175, cve-2024-47176, and cve-2024-47177
#for more see: [https://ubuntu.com/blog/cups-remote-code-execution](https://ubuntu.com/blog/cups-remote-code-execution)

#
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.

back to login. conflicted if i do the autoremove or not


so i tried another boot and videoed what shows on the screen and i get this when tapping the shift key
[ ok ] finished plymouth-quit-wait.service - hold until boot process finishes up.
[ ok ] finished plymouth.quit.service - terminate plymouth boot screen.

then i tried without shift key and i saw
starting colord.service - manage, install and generate color profiles...
[ ok ] finished plymouth-quit-wait.service - hold until boot process finishes up.
[ ok ] finished plymouth.quit.service - terminate plymouth boot screen.

unfortunately no vendors name

dont know if any of this means anything

---

### Post by rapattack on 2024-10-03
> **grahammechanical said:**
> A non gui login means that you are logging into Linux and the desktop environment has not loaded. You need to use commands. What is the command to start the desktop environment? I do not know. It may be possible for you to update/upgrade the operating system.

```
sudo apt update
```

```
sudo apt upgrade
```

Does that work?

To shutdown the system

[code]sudo shutdown --halt now]

should shutdown the system

Regards

thanks i often forget terms.
ok was about to do first command and it says i can upgrade
upgrade done and seems it wants me to autoremove some stuff
. i am never quite sure i should.
wants me to me remove
acpid
thanks i had forgot the shutdown command

---

### Post by rapattack on 2024-10-04
btw i am still in the same position so the commands havent made me able to login via the gui

---

### Post by rapattack on 2024-10-04
interesting when i do the command sudo shutdown --halt now it turns the screen off but the computer is still running. i can hear it

---

### Post by daren3 on 2024-10-05
[COLOR=#000000][FONT=Arial]I had a similar situation that happened when I tried to upgrade to 24.04.1 lts on my older Asus laptop that has a dual boot setup with Ubuntu 22.04 lts and Windows 10. I received a prompt from the system which informed me of the available upgrade. I made sure everything was updated and upgraded (via apt) before I clicked on the &#8220;Upgrade Now&#8221; button and started the process, which was surprisingly quick relative to the warning of a potential multiple hours process.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]The installer/upgrader told me when it was ready to reboot. When the system rebooted, I was met with this screen (borrowed from the Internet):
[IMG]https://lh7-rt.googleusercontent.com/docsz/AD_4nXfApInJ8DhdXE2kzXs0ysW2aC8EDfCbotOsr7dLRhibNvcO1V9ACOKMUzA15mtCUmG_mhfaj_ft7ydT_HTfU8leE0Ur_PHZofEGDQnN28Bwg-QafUgQHWrIjLbml_9_PNNaJp5ZeEBIXJMsKy5IAEtyCk7Q?key=V2o8F95vXftrEdy4UwgqMw[/IMG]

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]This is typed from the picture I took of my laptop&#8217;s screen (please be aware, there might be typos):[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]```
Gave up waiting for root file system device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
 - Missing modules (cat /proc/modules; ls /dev)
 ALERT! UUID=e2ce86bd-7099-4e0a-bb94-219047401534 does not exist. Dropping to a shell!
 
 BusyBox v1.30.1 (Ubuntu1:1.30.1-7ubuntu3.1) built-in shell (ash)
 Enter 'help' for a list of built-in commands.
 
 (initramfs)
```

From there, it took me about four hours to solve the issue. Yep, four hours. FML. Yes, Ubuntu, I still love you, but you&#8217;re on my short list right now. Here&#8217;s what I had to do to solve the problem:

_**Step One: **_Get the PC to boot into the new 24.04.1 installation:

[LIST=1]
[*]Find yourself a live Ubuntu DVD or USB drive and boot it. I used an older 20.04 live DVD I&#8217;ve had on-hand for a while, and I chose the &#8220;Try Ubuntu&#8221; option.
[*]Once at the live desktop, I first established a network connection and then I opened a terminal and sudoed to root by typing: &#8220;sudu su -&#8221; (without the quotes).
[*]I used fdisk to find the correct hard drive. At the root prompt, I typed: fdisk -l and looked for the EFI and Ubuntu partitions on my HDD. My laptop&#8217;s hard drive (sda) has six partitions:
sda1 = Windows recovery environment
sda2 = EFI System
sda3 = Microsoft reserved
sda4 = Microsoft basic data (main Windows 10 partition)
sda5 = Windows recovery environment
sda6 = Linux filesystem

I noted that sda2 and sda6 were the two needing help.
[*]Continuing as root (su), I mounted the two partitions in the mount directory /mnt:
[LIST=1]
[*]root@ASUS-laptop:~# mount /dev/sda6 /mnt
[*]root@ASUS-laptop:~# mount /dev/sda2 /mnt/boot/efi

I then mounted /dev, /dev/pts, /proc, /sys, and /run in the mount directory:
[/LIST]

[*]root@ASUS-laptop:~# for i in /dev /dev/pts /proc /sys /run; do mount -B $i /mnt$i; done

I Chrooted into the mount directory:
[*]root@ASUS-laptop:~# chroot /mnt

I needed to update initramfs, but I got a warning saying the &#8220;EFI variables cannot be set on this system.&#8221; So I had to mount them manually:
[*]root@ASUS-laptop:~# mount -t efivarfs none /sys/firmware/efi/efivars

Then I updated initramfs:
[*]root@ASUS-laptop:~# update-initramfs -u

I installed Grub on the sda drive:
[*]root@ASUS-laptop:~# grub-install /dev/sda

Then I updated grub:
[*]root@ASUS-laptop:~# update-grub

Doing this allowed Grub to find the Linux images and Windows 10 installation.
I then checked to make sure the Ubuntu installation was the first choice on the list:
[*]root@ASUS-laptop:~# efibootmgr

Doing this, I was able to verify it was going to boot into Ubuntu. I then exited the prompt and rebooted:
[*]root@ASUS-laptop:~# exit
[*]root@ASUS-laptop:~# reboot
[/LIST]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
This allowed the laptop to boot into the new Ubuntu installation but, to my dismay, I was greeted with a terminal login rather than the desktop login. I logged in using my regular credentials, and also found the laptop no longer had a network connection. Here&#8217;s what I was able to do to get the network up and running and restore the Ubuntu desktop environment:

_**Step Two:**_ Get the network connection up and running:

[LIST=1]
[*]When logged in, I ran the command [userchanged]@ASUS-laptop:~$ sudo dhclient
Doing this fired up the hardwired interface and allowed the laptop to join the network.
[/LIST]

_**Step Three:**_ Restore the Ubuntu desktop environment:

[LIST=1]
[*]I first purged the gdm3 environment. This step may be optional, your mileage may vary. I decided to purge gdm3 because of a post I found/read/followed. Again, this step may be optional for you and your installation:
[LIST]
[*][userchanged]@ASUS-laptop:~$ sudo apt purge gdm3
[/LIST]

[*][NOTICE]: I then reinstalled the gdm3 environment. Doing this, I feel, was a mistake. I rebooted after reinstalling gdm3 and I got a generic Debian environment and all the files I had on my desktop were missing. In addition, apps wouldn&#8217;t run; I couldn&#8217;t even start anything like open terminal (even using ctrl-alt-t), Firefox, etc. If you can avoid this step, you should.
[*]I then installed the Ubuntu desktop environment:
[LIST]
[*][userchanged]@ASUS-laptop:~$ sudo apt install ubuntu-desktop
[/LIST]
[/LIST]
Doing this and then rebooting the laptop brought the system back to life. All of my desktop files were there, the network connections were restored, and apps would run as normal.

I really hope this helps someone. It took me a while to research and work through the processes. It also took me a while to type all this out from all my notes. In typing this out, I may have missed a step and, if so, I apologize in advance.

Ubuntu, if you&#8217;re reading this you&#8217;re still on my short list. I hope you polish future upgrades a little more before you push them out. I don&#8217;t totally blame you though, since my dual-boot situation is a little out of the ordinary. But, I feel there&#8217;s a bunch who have a dual-boot installation like me who may not have been so fortunate to find and fix the failed upgrade path and may have chosen to completely reinstall.
[/FONT][/COLOR]

---

### Post by rapattack on 2024-10-23
> **daren3 said:**
> [COLOR=#000000][FONT=Arial]I had a similar situation that happened when I tried to upgrade to 24.04.1 lts on my older Asus laptop that has a dual boot setup with Ubuntu 22.04 lts and Windows 10. I received a prompt from the system which informed me of the available upgrade. I made sure everything was updated and upgraded (via apt) before I clicked on the “Upgrade Now” button and started the process, which was surprisingly quick relative to the warning of a potential multiple hours process.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]The installer/upgrader told me when it was ready to reboot. When the system rebooted, I was met with this screen (borrowed from the Internet):
[IMG]https://lh7-rt.googleusercontent.com/docsz/AD_4nXfApInJ8DhdXE2kzXs0ysW2aC8EDfCbotOsr7dLRhibNvcO1V9ACOKMUzA15mtCUmG_mhfaj_ft7ydT_HTfU8leE0Ur_PHZofEGDQnN28Bwg-QafUgQHWrIjLbml_9_PNNaJp5ZeEBIXJMsKy5IAEtyCk7Q?key=V2o8F95vXftrEdy4UwgqMw[/IMG]

[/FONT][/COLOR][COLOR=#000000][FONT=Arial]This is typed from the picture I took of my laptop’s screen (please be aware, there might be typos):[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]```
Gave up waiting for root file system device. Common problems:
 - Boot args (cat /proc/cmdline)
   - Check rootdelay= (did the system wait long enough?)
 - Missing modules (cat /proc/modules; ls /dev)
 ALERT! UUID=e2ce86bd-7099-4e0a-bb94-219047401534 does not exist. Dropping to a shell!
 
 BusyBox v1.30.1 (Ubuntu1:1.30.1-7ubuntu3.1) built-in shell (ash)
 Enter 'help' for a list of built-in commands.
 
 (initramfs)
```

From there, it took me about four hours to solve the issue. Yep, four hours. FML. Yes, Ubuntu, I still love you, but you’re on my short list right now. Here’s what I had to do to solve the problem:

_**Step One: **_Get the PC to boot into the new 24.04.1 installation:

[LIST=1]
[*]Find yourself a live Ubuntu DVD or USB drive and boot it. I used an older 20.04 live DVD I’ve had on-hand for a while, and I chose the “Try Ubuntu” option.
[*]Once at the live desktop, I first established a network connection and then I opened a terminal and sudoed to root by typing: “sudu su -” (without the quotes).
[*]I used fdisk to find the correct hard drive. At the root prompt, I typed: fdisk -l and looked for the EFI and Ubuntu partitions on my HDD. My laptop’s hard drive (sda) has six partitions:
sda1 = Windows recovery environment
sda2 = EFI System
sda3 = Microsoft reserved
sda4 = Microsoft basic data (main Windows 10 partition)
sda5 = Windows recovery environment
sda6 = Linux filesystem

I noted that sda2 and sda6 were the two needing help.
[*]Continuing as root (su), I mounted the two partitions in the mount directory /mnt:
[LIST=1]
[*]root@ASUS-laptop:~# mount /dev/sda6 /mnt
[*]root@ASUS-laptop:~# mount /dev/sda2 /mnt/boot/efi

I then mounted /dev, /dev/pts, /proc, /sys, and /run in the mount directory:
[/LIST]

[*]root@ASUS-laptop:~# for i in /dev /dev/pts /proc /sys /run; do mount -B $i /mnt$i; done

I Chrooted into the mount directory:
[*]root@ASUS-laptop:~# chroot /mnt

I needed to update initramfs, but I got a warning saying the “EFI variables cannot be set on this system.” So I had to mount them manually:
[*]root@ASUS-laptop:~# mount -t efivarfs none /sys/firmware/efi/efivars

Then I updated initramfs:
[*]root@ASUS-laptop:~# update-initramfs -u

I installed Grub on the sda drive:
[*]root@ASUS-laptop:~# grub-install /dev/sda

Then I updated grub:
[*]root@ASUS-laptop:~# update-grub

Doing this allowed Grub to find the Linux images and Windows 10 installation.
I then checked to make sure the Ubuntu installation was the first choice on the list:
[*]root@ASUS-laptop:~# efibootmgr

Doing this, I was able to verify it was going to boot into Ubuntu. I then exited the prompt and rebooted:
[*]root@ASUS-laptop:~# exit
[*]root@ASUS-laptop:~# reboot
[/LIST]
[/FONT][/COLOR][COLOR=#000000][FONT=Arial]
This allowed the laptop to boot into the new Ubuntu installation but, to my dismay, I was greeted with a terminal login rather than the desktop login. I logged in using my regular credentials, and also found the laptop no longer had a network connection. Here’s what I was able to do to get the network up and running and restore the Ubuntu desktop environment:

_**Step Two:**_ Get the network connection up and running:

[LIST=1]
[*]When logged in, I ran the command [userchanged]@ASUS-laptop:~$ sudo dhclient
Doing this fired up the hardwired interface and allowed the laptop to join the network.
[/LIST]

_**Step Three:**_ Restore the Ubuntu desktop environment:

[LIST=1]
[*]I first purged the gdm3 environment. This step may be optional, your mileage may vary. I decided to purge gdm3 because of a post I found/read/followed. Again, this step may be optional for you and your installation:
[LIST]
[*][userchanged]@ASUS-laptop:~$ sudo apt purge gdm3
[/LIST]

[*][NOTICE]: I then reinstalled the gdm3 environment. Doing this, I feel, was a mistake. I rebooted after reinstalling gdm3 and I got a generic Debian environment and all the files I had on my desktop were missing. In addition, apps wouldn’t run; I couldn’t even start anything like open terminal (even using ctrl-alt-t), Firefox, etc. If you can avoid this step, you should.
[*]I then installed the Ubuntu desktop environment:
[LIST]
[*][userchanged]@ASUS-laptop:~$ sudo apt install ubuntu-desktop
[/LIST]
[/LIST]
Doing this and then rebooting the laptop brought the system back to life. All of my desktop files were there, the network connections were restored, and apps would run as normal.

I really hope this helps someone. It took me a while to research and work through the processes. It also took me a while to type all this out from all my notes. In typing this out, I may have missed a step and, if so, I apologize in advance.

Ubuntu, if you’re reading this you’re still on my short list. I hope you polish future upgrades a little more before you push them out. I don’t totally blame you though, since my dual-boot situation is a little out of the ordinary. But, I feel there’s a bunch who have a dual-boot installation like me who may not have been so fortunate to find and fix the failed upgrade path and may have chosen to completely reinstall.
[/FONT][/COLOR]

sorry took me so long to get back online. covid and then an accident. i cant remember if i updated and upgraded prior. didnt know that i should have.
this seemed the longest upgrade i have done of ubuntu. i dont know why. i kept having to come back to the machine.
ouch four hours to solve gee.
ok i might have a live dvd somewhere but i dont have a dvd installed on the machine anymore. i might have chucked it out. i havent made a live usb before so this is going to take me time to get that happening. recovering from 3 major things and i keep getting interruptions. wish i could remember how to use fdisk ....i am so terrible with commands now. from memory my primary drive is sda1. i think i was able to find that out last week when i typed something.
i will come back on when i can get myself better sorted.
yes despite this experience ubuntu is my thing. been using it such a long time. not that i have experimented much with other distros

---

### Post by rapattack on 2024-11-21
so sorry havent been back on here for a while. i was able to get into ubuntu and its working well now. i cant remember exactly what did it as i had trouble with my phone as well(had lineageos installed and well volte wasnt happening so had to flash the phone with stock os)....then theres life getting in the way. anyway all good

---

### Post by rapattack on 2024-11-21
so sorry havent been back on here for a while. i was able to get into ubuntu and its working well now. i cant remember exactly what i did as i had trouble with my phone as well(had lineageos installed and well volte wasnt happening so had to flash the phone with stock os)....then theres life getting in the way. anyway all good

---

