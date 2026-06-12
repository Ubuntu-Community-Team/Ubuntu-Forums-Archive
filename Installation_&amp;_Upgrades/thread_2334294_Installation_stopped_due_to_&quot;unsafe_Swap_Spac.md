---
title: "Installation stopped due to &quot;unsafe Swap Space&quot;"
date: 2016-08-18
forum: Installation &amp; Upgrades
---

### Post by Tbuch on 2016-08-18
Every time I try to install Lubuntu encrypted on a Lenovo T60, the installation fails - due to "unsafe Swap Space"

Please see these pictures of my installation and the error message

[ATTACH=CONFIG]270733[/ATTACH][ATTACH=CONFIG]270734[/ATTACH]


When I check the drive with Gparted, it is apparently completely empty

[ATTACH=CONFIG]270735[/ATTACH]


What now to do??

---

### Post by RobGoss on 2016-08-18
I only see the 298.09 GB partition. I don't see any swap partition that maybe why you're getting this error message. Just create a 2, 3, GB partition and process with your installation

---

### Post by Tbuch on 2016-08-18
Do you mean I should create a 2 OR 3 GB partition??

---

### Post by RobGoss on 2016-08-18
> **Tbuch said:**
> Do you mean I should create a 2 OR 3 GB partition??

Yes when ever you are Installing any Linux distribution it is recommend to also create a swap partition as well this will help your system and it's performance 

In most cases you do not need a large swap partition a simple 2 to 3, GB will be sufficient

This might give you a better understanding how swaps partition are use and why we need then
[https://help.ubuntu.com/community/SwapFaq]("https://help.ubuntu.com/community/SwapFaq")

From the screen shots you posted it looks like this will be the only operating system on this machine correct?

---

### Post by Tbuch on 2016-08-18
> **RobGoss said:**
> 
From the screen shots you posted it looks like this will be the only operating system on this machine correct?

Yes that right - I will read the link later - now I just want to know If I create 3 GB partition - Then the Lubuntu installations have all what it need to create a swap partition?

---

### Post by RobGoss on 2016-08-18
As I stated once you create the swap area partition using gparted and use your primary disk space for your installation you should be good to go as long as you follow the on screen instructions

Once you create a swap partition and you run the installation it will not create another swap area just wanted to make that clear

---

### Post by Tbuch on 2016-08-18
Sorry if I am slow - But i am not sure what you mean
Have you explain how to create a "swap area partition" - you told me to create a 2 OR 3 GB partition - and I am asking you if this is the same as creating a Swap partition??

---

### Post by sudodus on 2016-08-18
Maybe the problem is zRAM - the Lubuntu desktop installer uses zRAM for swapping, which helps in computers with low RAM. But with encryption, you should boot into a live session 'Try Lubuntu' and ***swapoff***, which turns off using the zRAM

- Start a terminal window

- Check before and after with ```
swapon -s
```

- Run the following command ```
sudo swapoff -a
```

After that you can start the installer again (from the desktop icon), and I think it will work better.

---

### Post by Tbuch on 2016-08-18
YEs, thanks -  that have been my idea too - sadly I cannot use the "try Lubuntu"  funktion - nothing is happening except from a blinking "courser"

  [ATTACH=CONFIG]270738[/ATTACH]

---

### Post by sudodus on 2016-08-18
Maybe you have better luck with ***Lubuntu's alternate iso file***, which has a text mode debian installer. It does not use zRAM, so you should not have that problem. That method is also iso-tested according to this link

[Alternate Install (Unencrypted home) in Lubuntu Alternate i386 in Xenial Daily (archived)](http://iso.qa.ubuntu.com/qatracker/milestones/363/builds/126343/testcases/1660/results)

which describes how to install a system with LVM and encrypted disk: 'Select Guided - use entire disk and set up encrypted LVM'.

---

### Post by Tbuch on 2016-08-18
Thanks but no luck there too ;-)
[http://cdimage.ubuntu.com/lubuntu/xenial/daily/20160720/xenial-alternate-i386.iso](http://cdimage.ubuntu.com/lubuntu/xenial/daily/20160720/xenial-alternate-i386.iso) = The requested URL /lubuntu/xenial/daily/20160720/xenial-alternate-i386.iso was not found on this server.

---

### Post by RobGoss on 2016-08-18
What are the specs for your machine it might help us and others determine what's going on with your computer

---

### Post by Tbuch on 2016-08-18
[URL="http://ark.intel.com/Product.aspx?id=27255"];-)

IBM T60

Intel Core2 Duo T7200[/URL] 
2 GHz, 667 MHz FSB, 4M Cache, 65 nm, 34W, 100°C, PBGA479, PPGA478, 64-bit

[Mobile Intel I945GM Express Chipset Family]("http://www.intel.com/design/chipsets/mobile/945_fam.htm")
Dual-channel DDR2, 667 MHz system bus, PCI Express x16 graphics port, Serial ATA (version 1, 150 MB/s eller 1,5 Gbit/s)

2 x 2 GB Elpida EBE21UE8ACUA-8G-E 800 MHz/PC2-6400 (max 667 MHz) 

[Seagate Momentus 7200.4 ST9320423AS]("http://www.seagate.com/ww/v/index.jsp?name=st9320423as-momentus-7200.4-sata-320-gb-hd&vgnextoid=61029937c0780210VgnVCM1000001a48090aRCRD&locale=en-US#tTabContentOverview")
320 GB, 16 MB buffer, SATA 3Gb/s, 7200 RPM, Perpendicular, NCQ, 0° C to 60° C,

---

### Post by sudodus on 2016-08-18
> **Tbuch said:**
> Thanks but no luck there too ;-)
[http://cdimage.ubuntu.com/lubuntu/xenial/daily/20160720/xenial-alternate-i386.iso](http://cdimage.ubuntu.com/lubuntu/xenial/daily/20160720/xenial-alternate-i386.iso) = The requested URL /lubuntu/xenial/daily/20160720/xenial-alternate-i386.iso was not found on this server.

My bad: I did not say that you find the iso file there - only the instruction how to use it. I'm sorry for not explaining where to find the alternate iso file (and the other files). 

Try this link: [http://lubuntu.me/downloads/](http://lubuntu.me/downloads/). If you use the torrent (the right part of each button), the md5sum will be checked automatically (which makes sure you get a correctly downloaded iso file).

-o-

I am not sure but suspect that you have problems either with the graphics (to find a driver that works with your graphics chip) or with the wifi. If there are problems with graphics, you may need the [boot option](http://ubuntuforums.org/showthread.php?t=2230389&p=13370808#post13370808) ***nomodeset***, and after that install a proprietary driver.

Which iso file have you been trying to use? Lubuntu 16.04.1 LTS is much improved (compared to the original Lubuntu 16.04 LTS) particularly for some Intel graphics chips.

---

### Post by RobGoss on 2016-08-18
Have you try any other distributions besides Lubuntu? it might be a good idea to try another ISO file to see if this problem still persist 

I think it's very important to be able to run the live session this will tell you if your machine will stand a chance to run some of Ubuntu's distributions specially on older machines

---

### Post by Tbuch on 2016-08-18
> **sudodus said:**
> .

Which iso file have you been trying to use? Lubuntu 16.04.1 LTS is much improved (compared to the original Lubuntu 16.04 LTS) particularly for some Intel graphics chips.

Sorry but I needed some sleep (its night in denmark) - I was using lubuntu-16.04-desktop-amd64.iso

I will now try the Alternate installer - immediately, I cannot see that the Universal-USB-Installer can handle lubuntu-16.04.1-alternate - but I'll try to figure it out

---

### Post by Tbuch on 2016-08-18
> **RobGoss said:**
> Have you try any other distributions besides Lubuntu? if might be a good idea to try another ISO file to see if this problem still persist. I think it's very important to be able to run the live session this will tell you if your machine will stand a chance to run some of Ubuntu's distributions specially on older machines

Yes there have been a normal Ubuntu installation on the computer for an year

---

### Post by Tbuch on 2016-08-19
I came a long way with Lubuntu Alternate Installation - the whole installation went fine and then booted up again

[ATTACH=CONFIG]270744[/ATTACH]


I wrote the new password - it went fine - but then I got an error message

[ATTACH=CONFIG]270746[/ATTACH]


Then there just was a lighter illuminated screen with no cursor or anything on
After three quarters, I gave up and typed good old CTRL + ALT + Delete - and found that the system obviously not was gone down cause after that the system  restarted

---

### Post by Tbuch on 2016-08-19
I can use ctrl + alt + f1 to provide access to the terminal
But ctrl+alt+f7 provides no GUI

---

### Post by sudodus on 2016-08-19
Did you install the basic Lubuntu 16.04 LTS or the first point release Lubuntu 16.04.**[COLOR="#0000CD"]1[/COLOR]** LTS, which is likely to work better with your graphics chip?

Maybe it is enough to get everything up to date with the following commands in text mode:

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get install xserver-xorg-video-intel
```

and try the graphics mode after rebooting.

You can also try Xubuntu 16.04.**[COLOR="#0000CD"]1[/COLOR]** LTS. It might work better with your computer.

---

### Post by Tbuch on 2016-08-20
Yae I am pretty sure that it was the 04.1 from http://lubuntu.me/downloads/<br><br>I will read about Xubuntu - I need a OS for a energy efficient file-sync server

---

### Post by sudodus on 2016-08-20
If you want a server, I would recommend that you install Ubuntu Server with a text mode interface. A graphical user interface will use some 'horsepower' and RAM, and will also make the server more sensitive to attacks from the internet. I suggest that you learn the command lines necessary to run the server.

But if you want to use the computer for desktop tasks too, then you should explore different desktop environments (Lubuntu and Xubuntu come with two good candidates, LXDE and XFCE). But the most light-weight graphical aternative is a simple window manager plus the most necessary graphical tools, for example Fluxbox, Openbox or JWM. See the following links

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

[OBI/Xenial-32-txt](https://help.ubuntu.com/community/OBI/Xenial-32-txt)

---

### Post by Tbuch on 2016-08-20
Are any of the suggested OS able to run Teamviewer (I need a remote program) and syncthing ([https://syncthing.net/](https://syncthing.net/)) which - as I understand - need some kind of a browser?

---

### Post by Tbuch on 2016-08-20
So I finally got Lubuntu installed;-)

With great help from you, sudodus and AJenbo I did the following:

     
[LIST]
[*]I downloaded 16.04.1 LTS from [http://lubuntu.me/downloads/](http://lubuntu.me/downloads/) 
[*]I used "try Lubuntu" 
[*]In Terminal I wrote "sudo swapoff -a" (nb "-" on a Danish keyboard is "+") 
[*]Installed Lubuntu from the desktop shortcut 
[/LIST]

---

### Post by sudodus on 2016-08-20
I have no current experience, but two years ago I use Teamviewer with Lubuntu, and I think it works in all Ubuntu desktop flavours and versions (but not with Ubuntu Server).

I think Teamviewer should work with the listed window managers too. I have no experience of Syncthing, but it looks like it should work well with a linux server.

Ubuntu Server is very often run remotely. It is often installed headless, see this link, so it ***has to*** be managed remotely.

[What Is Headless Linux?](http://smallbusiness.chron.com/headless-linux-33715.html)

> The term "headless Linux" may conjure up images of Ichabod Crane and Sleepy Hollow, but in reality, a headless Linux server is just a server that has no monitor, keyboard or mouse. When large websites use hundreds of servers, it makes little sense to waste precious machine cycles polling unused devices. Instead, system management tasks are performed using the same network connections that handle Internet traffic.

---

### Post by Tbuch on 2016-08-20
Okay, thanks a lot - now for a while I am lucky that I got Lubuntu Installed encrypted ;-)

When I have time and resources I will try a raspberry pi installation

---

### Post by sudodus on 2016-08-20
Congratulations to a working encrypted Lubuntu system :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED.

Welcome back with a new thread, when you have new problems or questions.

---

