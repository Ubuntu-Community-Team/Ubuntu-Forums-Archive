---
title: "Install ubuntu on 6720s notebook over winvista"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by tamma on 2007-12-27
Hello,

      I am a newbee in the linux world, I'v just bought a 6720s notebook T5470 1.6Ghz, win vista professionnal 6.0, graphic Mobile Intel 965 express and 2G ram.
      The problem is that i cannot install ubuntu feisty 7.04 over win vista, after the boot and the install menu the screen  becomes black and... nothing, I tried both the liveCD and the alternate CD 
      Please help me solve this issue

---

### Post by Pumalite on 2007-12-27
Take a look at this first.
[http://ubuntuforums.org/showthread.php?t=611619](http://ubuntuforums.org/showthread.php?t=611619)
 If you decide to go for it, you'll have to DBan your drive: [http://dban.sourceforge.net/](http://dban.sourceforge.net/)
Then get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Boot from it, delete everything in your hard drive if any is left, make a new large partition of your whole hard drive formatted ext3. Then a good scheme is:
10 GB for '/'
1 GB for /swap
The rest for /home.
Install Ubuntu, go Manual and use already made partitions.

---

### Post by tamma on 2007-12-31
thank you for your response .. but I am willing to have dual boot with existing winvista 
until I get enough handon ubuntu.
Also, I wish to use ubuntu feisty instead of gutsy, so my big question is ; Are all
drivers available for my compaq 6720s???? does gutsy provide all the necessary drivers too?
Thank you in advance.

---

### Post by Pumalite on 2007-12-31
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by jakovina on 2007-12-31
> **tamma said:**
> thank you for your response .. but I am willing to have dual boot with existing winvista 
until I get enough handon ubuntu.
Also, I wish to use ubuntu feisty instead of gutsy, so my big question is ; Are all
drivers available for my compaq 6720s???? does gutsy provide all the necessary drivers too?
Thank you in advance.

Tamma!
I have just installed Gutsy on HP Compaq 6720s that came with FreeDOS.
(I am just writing this on it)
I have encountered following problems with this laptop:
1. LAN adapter didn't work  - I have updated BIOS from HP's site and problem is SOLVED!
2. Battery reporting was weird - SOLVED after BIOS updating
You can find BIOS updates on: [http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=3442833&prodTypeId=321957&prodSeriesId=3442832&swLang=8&taskId=135&swEnvOID=1093](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareIndex.jsp?lang=en&cc=us&prodNameId=3442833&prodTypeId=321957&prodSeriesId=3442832&swLang=8&taskId=135&swEnvOID=1093)

3. Wireless adapter didn't work initially - SOLVED after I have enabled nonfree Firmware for adapter

4. Modem (winmodem) is not working - I am still working arround to solve this,

---

### Post by tamma on 2008-01-01
This is in fact what a have tried before but didn't work ... beside I don't want to completely remove winvista because of the warrabty (among other reasons).

---

### Post by Pumalite on 2008-01-01
If you want dual boot, you have to allocate space for Ubuntu with Vista's partitioner first, then install Ubuntu.

---

### Post by tamma on 2008-01-01
Hi 
     I prepaid  a free drive with 15 G space but I don't know how to set up the swap and "/" partitions, can you show me how to?
    Thank you for your time and effort.

---

### Post by Pumalite on 2008-01-01
I cam do something better. Here is a link to the best guide in partitioning:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by tamma on 2008-01-01
Hi
    I think this procedure in the link you provided is not the enough ; I already tried to install ubunut but as I said n my first post the problem is that the screen turn into black and then I got nothing.
    Also I tried both the LiveCD and the AlternateCD ; the same problem.

---

### Post by Pumalite on 2008-01-01
What is a 'prepaid a free drive with 15 G space'?

---

### Post by tamma on 2008-01-01
Sorry it was a typing mistake ; I wanted to say "I prepared a free disk space of 15Gbytes".
I mean my problem now is how to make the**_ proper partitionning of a drive_** into winvista for the ubunut OS.
The link you provided didn't help me sort out this issue.
Thanks a lot for your help.

---

### Post by Pumalite on 2008-01-01
I imagine this allocated space was formatted. Am I right?

---

### Post by tamma on 2008-01-01
Yes in fact .. I formatted NTFS because winvista utility don't provide ext3 nor  swap formatting possibilites.

---

### Post by Pumalite on 2008-01-01
Install and go Manual, A good scheme for the new partition is:
10 GB for '/'
2x RAM up to 1 GB for /swap
The rest for /home

---

### Post by tamma on 2008-01-02
OK..I think I will install "partition magic" and I will try to do the partitionning you showed me above, because from the winvista disk manager tool I can't do the requested partitionning.
Thanks.

---

### Post by Pumalite on 2008-01-02
Don't do that. Get Gparted Live0 CD:
[http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk, boot from it, and do the partitioning.

---

### Post by tamma on 2008-01-02
I have a question ; is the Gparted LiveCD bootable (from start of the laptop) because it seems me that Gparted only works in a linux environement and is not designed to work in a winvista.

---

### Post by Pumalite on 2008-01-02
It can boot anywhere.

---

### Post by tamma on 2008-01-04
Hi Pumalite;

        I used Gparted liveCD (burned on a DVD media) but instead of the GUI interface I get a prompte of grub ; **grub>** which means** text mode** !!!! and I don't know what to do later !!! at this point the text mode provides many commandes but I have no idea what to do ..help.

---

### Post by tamma on 2008-01-04
Hi ;
         I just want to add that I used the Gparted LiveCD from the boot of the laptop.
         Also, I already tried to install mandriva LiveCD and it's OK ; the only problem is the display which is not correct, I tried also solaris 10 but it didn't recognize the keyboard ==> not OK.

---

### Post by Pumalite on 2008-01-04
At the boot prompt press 'Enter'. Good for most computers,

---

### Post by tamma on 2008-01-04
The enter command just gives a return to grub prompt.
when presseng "tab" the system displays ; possible commands : backgound blocklist boot cat chainloader etc......
I enter the "reboot" in order to restart the laptop and come back to winvista.
Any other suggestions that may help please.

---

### Post by Pumalite on 2008-01-04
Doesn't sound like Gparted Live CD. Did you boot Super Grub by ant chance?

---

### Post by tamma on 2008-01-04
I downloaded and burned the Gparted liveCD iso image "gparted-livecd-0.3.4-11.iso" ; I got an error from nero 7 that says something like "the block size does not match the image size" I just ignore and continue burning on a DVD medium (I already found that a DVD can be used instead of CD for winvista only).
I dont understand your last question "Did you boot Super Grub by ant chance?"

---

### Post by Pumalite on 2008-01-04
Forget about the question. Try to get version 0.3.4-0. Use ImgBurn: [http://www.imgburn.com/index.php?act=download](http://www.imgburn.com/index.php?act=download)
Install. Go to Mode>ISO>Burn.

---

### Post by tamma on 2008-01-04
Hi ;
         I downloaded and burnded the Gparted version 0.3.4-0 which is a very good tool, I made the patition as follow ; 15G as ext3 (primary) and 2G as linux_swap (primary) is that ok ? 
         Anyway, I started from the Ubuntu liveCD (7.04) and this time is was working at the begining... 
after a while I get an error related to X server and then provide information like ;

[B]X window system ver : 7.2.0
Release Date : 22 January 2007.
X protocol version 11, Revision 0, Release 7.2
Build operating system : linux ubuntu.
current operating system : linux ubuntu 2.6.20-15 GENERIC #2 SMP sun Apr 15 07:36:31 UTC 2007 i686
build date : 04 apr 2007
.............;
..........[/B]

after I validate the "OK" button then dislapys the next message :

[B]X server is now disabled
Restart GDM when it is configured correctly[/B]

---

### Post by Pumalite on 2008-01-04
sudo dpkg-reconfigure xserver-xorg
Accept most defaults.
Choose vesa as the driver Then: startx

---

### Post by tamma on 2008-01-05
Hi ;
    I followed the instructions you provided but at the end I get the following error ; 

**XIO : fatal error 104 (connection reset by peer) on X server ":0.0" after 0 requests (0 known processed) with 0 events remaining.**

    I realized after doing some search (X server forum), that I need to make update, but I need a wireline internet connection and I have wifi connection (driver not working in the text mode).

---

### Post by Pumalite on 2008-01-05
That's right, you need to be wired during installation, your wireless driver you'll have to configure after the installation.

---

### Post by AlesUbu123 on 2008-01-06
Hi tamma!

I have the same laptop and Ubuntu installation works ok for me - are you trying to install Ubuntu Feisty Fawn 7.04 or Ubuntu Gutsy Gibbon 7.10?

Note that 7.04 will not work out of the box for HP 6720s but 7.10 most probably will!

Regards!

---

### Post by tamma on 2008-03-16
I have installed ubuntu gutsy and its working fine ..
thank you very much to both of you Pumalite and AlesUbu123

---

### Post by Pumalite on 2008-03-16
Glad you got it working.

---

