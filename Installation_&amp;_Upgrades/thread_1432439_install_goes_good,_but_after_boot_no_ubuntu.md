---
title: "install goes good, but after boot no ubuntu"
date: 2010-03-17
forum: Installation &amp; Upgrades
---

### Post by jdenbrok on 2010-03-17
Hi all,

I am sorry for this being my first post and rightaway a new thread. I believe that in many forums this is bad behavior, however I couldnt find my problem. I want to start saying that I do know my way around with computer, but I know nothing about linux.

I have a computer (acer aspire 2000) with a broken cd player and it cant boot from usb, thus for a clean install only network is an option. I had windows xp on this computer and installed ubuntu with wubi without problems. Rightaway everything worked. This made me convident enought to make a fresh install. I booted with pxe and this worked, I could install ubuntu, the only problem was that the screen was flickering, but I could still read everything.

So during the installation of ubuntu 9.10 all goes very well. At the end I need to restart and then it crashes on the very first boot of ubuntu. I tried to install 9.04 as well, but with the same result.

the only line that really gives an error is:
acer-wmi: no or unsupported wmi interface

I dont know how important this is, online I read this happens to more people, but they can still get in ubuntu. Ubuntu also seems to just continue with starting services and even the comment OK after the lines describing the actions. (At 9.04 there is also a message "Ubuntu 9.04 ubuntu tty1")
Then at once I am asked for my username and password (all in a dos like surrounding, no graphics) and then I get a message that ubuntu is freeware and comes with "ABSOLUTELY NO WARRANTY" and then it says:
username@pcname:~$

I know that I can now use linux commands such as sudo su, but I dont know how to work with them. I expected to get the ubuntu surrounding. I have no clue what I can do further and actually even dont really know what to search for in forums such as this one. I googled every phrase that I see during start up, but it didnt lead me to an understandable solution.

My computer is old (acer aspire 2000 specs [http://reviews.cnet.com/laptops/acer-aspire-2000/4507-3121_7-30589601.html](http://reviews.cnet.com/laptops/acer-aspire-2000/4507-3121_7-30589601.html) ) so I assume all drivers should already be included in ubuntu. This assumption is also because the wubi install worked perfect.

---

### Post by C.S.Cameron on 2010-03-17
How far are you getting trying to boot?
If you press the Esc key while booting you might get several options.
You might have some luck if you try some of these.

---

### Post by jdenbrok on 2010-03-18
Thank you for your answer. I will try to give a more complete report tonight, yesterdayevening I tried to install 9.04 to see if that worked. With this install there are many lines on screen that I can't all copy. Besides I really want 9.10 and it should work because it did already after I installed it with wubi.

I did see the message that I can press ESC, I tried, but it's so fast that I did not succeed in getting options on several attempts.

Tonight I will reinstall 9.10 and then post everything that is put on screen during boot, hopefully then somebody can help.

Before I reinstall again, I am not completely sure about how to do my disk configuration when I am in that stage of installing ubuntu. I tried several options on several installs, but I think it would be better if I can delete my whole disk, including partitioning right now in the dos like screen, so that I can follow standard options. (Last time I took the first highlighted option and got a double boot with the previous attempt to install ubuntu.) I cannot access internet, at least if I use a comment where I need to get something it fails on downloading the package.

---

### Post by presence1960 on 2010-03-18
> **jdenbrok said:**
> Thank you for your answer. I will try to give a more complete report tonight, yesterdayevening I tried to install 9.04 to see if that worked. With this install there are many lines on screen that I can't all copy. Besides I really want 9.10 and it should work because it did already after I installed it with wubi.

I did see the message that I can press ESC, I tried, but it's so fast that I did not succeed in getting options on several attempts.

Tonight I will reinstall 9.10 and then post everything that is put on screen during boot, hopefully then somebody can help.

Before I reinstall again, I am not completely sure about how to do my disk configuration when I am in that stage of installing ubuntu. I tried several options on several installs, but I think it would be better if I can delete my whole disk, including partitioning right now in the dos like screen, so that I can follow standard options. (Last time I took the first highlighted option and got a double boot with the previous attempt to install ubuntu.) I cannot access internet, at least if I use a comment where I need to get something it fails on downloading the package.

When installing at the prepare disk space window choose "use entire disk". This will overwrite any existing partitions/data and automatically set up your ubuntu partitions for you using the entire disk. Make sure to back up any data you do not want to lose beforehand.

---

### Post by jdenbrok on 2010-03-18
I am being as complete as I can think of being. I really hope that somebody can point me in the good direction for installing ubuntu, alternatively if Ubuntu cannot be installed on my machine, is there another os that will install via pxe? Now I cannot use my computer at all.

I first followed this guide [https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot) .

The client computer boots with ubuntu and I choose install from the installer boot menu.

I get a flickering screen but can read questions. As the client can not connect to the internet via my server computer I now remove the cable between the computers and connect the client directly to the internet.

I am asked for language (Dutch), location (nl), keyboard layout, network interface (Ethernet), a hostname (ubuntu), archive mirror country (nl), mirror (only one option), http proxy (blank). Between brackets my choices.

Computer downloads and loads components.

Asked for partitioning method (guided - use entire disk), disc to partition (only one option), write changes to disk (yes).

Installing base system.

Asked for full name user (my name), username for account (first name), password (pass), use weak password (yes), encrypt home directory (no)

Configuring apt, select and install software

Asked how to manage updates (install security updates automatically)

Select and install software

Choose software to install (select none and press enter)

Select and install software, installing grub

Asked is clock set to UTC (yes), finish installation (continue)

I remove my internetcable get the screen form my computer then it sais on screen “Grub loading” and I get a new screen which is black for a few seconds and then sais:

fsck from util-linux-ng 2.16
/dev/sda1: clean, 47994/3571712 files, 529499/14279769 blocks
[     5.565972] acer-wmi: No or unsupported WMI interface, unable to load
* Setting preliminary keymap…
* Starting AppArmor profiles
* Setting up console font and keymap…
Ubuntu 9.10 ubuntu tty1

ubuntu login: joost (my first name)
Password: 
Linux ubuntu 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

The programs included with the Ubuntu system are free software:
The exact distribution terms for each program are described in the 
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To run a command as administrator (user “root”), use “sudo <command>”,
See “man sudo_root” for details.

joost@ubuntu:~$

After a restart I dont get the message between "The programs included" and "applicable law.".

I cannot access internet from this screen. I have a acer aspire 2000.

---

### Post by jdenbrok on 2010-03-18
I tried a lot of reboots and found out that if I choose the right moments I can actually get the grub loader. I reproduced this a few times.
My grub is GNU GRUB version 1.97~beta4

I have the options:
Ubuntu, Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-20-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

I think I dont need a memtest.

If I take recovery mode I get 6 options:
resume (arrives at same place as normal boot)
clean  (not used but doesnt seem logical to use)
dpkg (tried, but get error about downloading and nothing changes)
grub   (tried, reinstalled grub, no use)
netroot (I believe I can get the network working here, network not tested as i dont know good commands)
root

I can also press e in the first screen. Then I get a screen with:
GNU GRUB version 1.97~beta4
recordfail=1
if [ -n ${have_grubenv} ]; then save_env recordfail; fi
set quiet=1
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set d52d2759-0db0-428d-bcd9-2faf591b2\
6a2
linux /boot/vmlinuz-2.6.31-20-generic root=UUID=d52d2759-0db0-428d-b\
cd9-2faf591b2 ro    splash quiet
initrd /boot/initrd.img-2.6.31-20-generic

I hope this all should give enough information to get me out of my situation.

---

### Post by jdenbrok on 2010-03-19
If somebody still reads this. I found out I should just press shift and then I can go to the grubmenu, this is standard and leads me to believe the grub is not wrong.

Further I was told to use startx, I did but the computer said:
The program 'startx' is currently not installed. You can install it by typing
sudo apt-get install xinit
startx: command not found
I did "sudo apt-get install xinit" and now when I press startx a window opens with an error. Xsession:warning: xrdb command not found; X resources not merged.

I also found that if i use netboot I do connect to the internet.

When I used the dpkg option, I get: 
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded
which leads me to believe this doesnt change anything.

---

### Post by Ozymandias_117 on 2010-03-19
Assuming you have internet, (you can use ping [www.google.com](www.google.com) to check, press ctrl+c to end the ping) try
```
sudo apt-get update
sudo apt-get install ubuntu-desktop

```

Note: It may take a while to run

Edit: After it finishes, reboot :P

---

### Post by jdenbrok on 2010-03-20
Thank you Ozymandias_117

On another forum I found out the same solution so I believe it will work. I cannot acces my computer now to actually do it, but feel like chances are good. What I learned from the other forum is that I probably installed the server version of Ubuntu. That would explain everything and is also explainable because I did with the installation "Choose software to install (select none and press enter)" Apparantly I should have chosen some things, I dont know yet which and I cannot reproduce the list, but maybe someone can tell me which software I should at least install from this list? 

For now I fully believe "sudo apt-get update" and "sudo apt-get install ubuntu-desktop" should work.

Thanks everybody for your advise and solving this for me. Tomorrowevening I will be home and will check if this works and post here again. Probably for the last time. ;)

---

### Post by lisati on 2010-03-20
> **Ozymandias_117 said:**
> Assuming you have internet, (you can use ping [www.google.com](www.google.com) to check, press ctrl+c to end the ping) try
```
sudo apt-get update
sudo apt-get install ubuntu-desktop

```

Note: It may take a while to run

Edit: After it finishes, reboot :P
I only just noticed this thread, and was wondering if the OP installed a command-line-only version of Ubunutu (e.g. server edition). If so, the above should get a GUI installed.
> **jdenbrok said:**
> Thanks everybody for your advi[COLOR="Red"]c[/COLOR]e and solving this for me. Tomorrow evening I will be home and will check if this works and post here again. Probably for the last time. ;)

All the best, feel free to keep us posted on how you're getting on.

---

### Post by jdenbrok on 2010-03-23
During installation from pxe you get to choose software. As I said before I thought it was extra software because I saw things like "Audio creation and editing suite". But Ubuntu desktop is also in the list and I should have selected that one. Now I did and it worked. Also "sudo apt-get install ubuntu-desktop" worked.

Here is the complete list of software you can install via pxe and where I didnt know what to choose and choose nothing:
Basic Ubuntu Server
Cloud computing cluster
Cloud computing node
DNS-server
Edubuntu server
LAMP server
E-mail-server
Open SSH server
PostgreSQL database
Printserver
Samba file server
Tomcat Java server
Ubuntu Enterprise Cloud (instance)
Virtual Machine host
2D/3D creation and editing suite
Audio creation and editing suite
Edubuntu KDE desktop
Edubuntu desktop
Kubuntu desktop
Kubuntu netbook
LADSPA and DSSI audio plugins
Large selection of font packages
Mythbuntu additional roles
Mythbuntu frontend
Mythbuntu master backend
Mythbuntu slave backend
Ubuntu netbook remix
Ubuntu desktop
Video creation and editing suite
Xubuntu desktop
Manual package selection

---

