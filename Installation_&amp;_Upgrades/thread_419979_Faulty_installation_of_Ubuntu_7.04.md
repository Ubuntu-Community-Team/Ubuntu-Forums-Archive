---
title: "Faulty installation of Ubuntu 7.04"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by abandi on 2007-04-23
Hi all
I am a physician, so you can guess how much I know about tech stuff. I installed Ubuntu 6.10 on my desktop and am happy with everything(networking, accessing windows partition etc.) I decided to go with Ubuntu 7.04 on my laptop as I have a WPC54G network card and read on the net about problems with configuring it in 6.10. 
I burned the ISO image and checked md5sum and installed 7.04. Everything seemed to be ok but I could not configure my wireless card. One of the several things that I tried was uncomment certain things in the /etc/network/interfaces file.(ofcourse as suggested on one of the forums). When I rebooted, the system froze after the login. The screen remains blank and a white rectangle box appears on the top left corner, like a terminal window, but empty. The key board, mouse stop working. I am not sure if changing network interface file caused this. Now I am thinking of unistalling ubuntu from windows with MbrFix.exe. Will it remove the GRUB? Please advise on the best method for unistalling so I can do a fresh install. And please note that I am an absolute tech illiterate !
Thanks

---

### Post by thegreatmichael on 2007-04-23
I have the same issue!  I have tried to re-login, and sometimes it would get farther than others, originally not showing the splash screen, but now finally, it will login, but then after a moment, it will log back out.  The only thing I can think of (for my situation, please respond if you have the same issue) is that I had Beryl running before the upgrade, and once I was finally able to login I tried to switch over to it from plane old metacity, but now I can't stay logged in for more than 1 minute.

---

### Post by abandi on 2007-04-23
I did not have Beryl. I think we are not the only people having problems with blank screens. I noticed that I am able to login ok randomly. It is very unpredictable. I strongly feel it is a bug in the 7.04 version and hope somebody fixes it soon. 
For now I have decided to uninstall it and load 6.10. Will upgrade when the bugs are fixed

---

### Post by Louis Sanchez on 2007-04-23
I have the same problem. :confused: 
my first ubuntu installation, i have a nvidia geforce 7300 LE.
When booting, i see an error when loading "daemon" or somting like that. It says it timed out.
Help would be most appreciated. Ill post my log as soon as i can find it lol.

EDIT: abandi, u said it was working before u edited this file. Do u know how it was before? It might be the key to our problem. thx.

---

### Post by Louis Sanchez on 2007-04-23
I managed to copy the exact error:

Starting Avahi mDNS/DNS_SD Daemon 'avahi Daemon
A timeout reached while waiting for return value
Could not return value for daemon process.

Thats before i reach the login screen. Then i try to login.
> The screen remains blank and a white rectangle box appears on the top left corner, like a terminal window, but empty.
Thats what happens to me.

I press ctrl + alt + f4  and get this at the bottom of the screen:

Starting Common Unix Printing System: cupsd

It never starts apparently.

My system specs:

Dell Dimension DXP061
Intel(R) Core(TM)2 CPU
  6300 @ 1.86Ghz
1.86Ghz, 1.00 GB of RAM

GRAPHIC CARD:
Nvidia Geforce 7300 LE

Any help appreciated.

---

### Post by funkychicken9000 on 2007-04-24
I also have the "white box terminal" problem.  Any ideas?

---

### Post by Louis Sanchez on 2007-04-24
whats your specs?

---

### Post by Louis Sanchez on 2007-04-25
*bump* Cmon, somebody has to atleast have a suggestion...

---

### Post by super.rad on 2007-04-25
another one here with the blank screen with white rectangle in top corner, i also edited the /etc/network/interfaces file last night and only just tried logging in. anyone? would really like to sort it out rather than have to reinstall ubuntu again

---

### Post by super.rad on 2007-04-25
after reading a few other things it sounds like its doing this because i edited the /etc/network/interfaces could anyone tell me how to "reset" this to its default settings

---

### Post by Louis Sanchez on 2007-04-25
Dont bother reinstalling, since nothing changed when i did.

---

### Post by abandi on 2007-04-26
I fixed the GRUB first with FixMBR.exe and then completed deleted the partition containing Ubuntu. I installed 6.10 in which WPC54G wireless card apparantly worked out of the box. I am having the same problems with the card despite trying all the things suggested on various forums. The card picks up the network signals but does not connect. wlan0 is always displayed as 'disconnected'. I hope to spend some time this weekend to see if I can figure a way out of this mess. Will let you guys know if I succeed!

---

### Post by eapache on 2007-04-26
If you edited a file and it broke something, press Ctrl-Alt-F1, login, and use the command

sudo nano <file path here>

without the tags. This will open a command-line text-editor of the file. Change the stuff back to what it was, and then press Ctrl-O to save, and Ctrl-something (I forget, it's listed at the bottom) to exit. Then use the command

sudo shutdown -h now

to turn off safely. Turn the computer back on and it should be working (without network, but at least you'll be able to log in).

Hope this helps.

---

### Post by Louis Sanchez on 2007-04-26
Thx for the help. But i never edited any files, it just never loads. :(

---

### Post by Louis Sanchez on 2007-04-29
*bump*
cuz i would really, *really* like to get ubuntu working.

---

### Post by Louis Sanchez on 2007-05-03
another *bump*
cuz somebody, somewhere will have an answer to my problem.

---

