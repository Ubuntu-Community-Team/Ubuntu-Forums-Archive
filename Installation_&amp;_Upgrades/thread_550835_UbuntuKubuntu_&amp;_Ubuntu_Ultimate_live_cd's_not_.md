---
title: "Ubuntu/Kubuntu &amp; Ubuntu Ultimate live cd's not starting"
date: 2007-09-14
forum: Installation &amp; Upgrades
---

### Post by jjames on 2007-09-14
Hi All

Some help would really be appreciated with getting ubuntu live cd starting up on my desktop. I've been spending the last 5 days reading forums but nothing suggested helps.
Problem:

When booting from the live cd's I get the screen where you need to select start normal or in safe graphics mode etc. When selecting either one of the two mentioned ubuntu starts its thing but just as it should load the gnome or kde interface I get a pretty messed up screen. I then hear the logon music playing and everything but cant see a damn thing. - So close but yet so far - as they say.

Any suggestions?

My desktop specs are:

Intel P4 3GHZ
1GB Ram
Onboard graphics
VIA P4M890 Chipset Motherboard
1 X 80GB SATA HDD
1 X IDE 80 GB HDD
Tv card
NIC
USB hub 
Bluetooth dongle

Any help on getting this going would be appreciated.

---

### Post by Pumalite on 2007-09-14
Get a command line: Ctrl+Alt+F1
sudo dpkg-reconfigure xserver-xorg
Choose most defaults, choose 'vesa' as the driver
Then: startx

---

### Post by jjames on 2007-09-14
Hey Pumalite  

Thanks for coming back in such short time! 

When do I need to do a Ctrl+Alt+F1. During the menu is shown or after I've already selected a mode?

Thanks
JJ

---

### Post by Pumalite on 2007-09-14
When you end up with a blank screen and without a command line. If you end up at a command line, you can skip that step.

---

### Post by jjames on 2007-09-14
Hi Pumalite 

So I managed to get the command line and went through the configuration procedure okay. When trying to run startx, I get a fatal server error "Server is already active for display 0. If this server is no longer running, remove/tmp/.X0-lock and start again"

Ho do I do the latter?

Regards
JJ

---

### Post by Pumalite on 2007-09-14
Before the command I gave you, do this:
sudo /etc/init.d/gdm stop
Then run the command I gave you.

---

### Post by jjames on 2007-09-14
Okay, I think I should mention that Im very new to linux and dont really know how to get my way around.....I can change dis etc and atleast know not to do a rm* but thats about as much :-)

---

### Post by jjames on 2007-09-14
I assume that I do sudo /etc/init.d/gdm stop before sudo dpkg-reconfigure xserver-xorg or should it be before startx?

---

### Post by jjames on 2007-09-14
Hi Pumalite

I get another error when runnung "sudo /etc/init.d/gdm stop";

sudo /etc/init.d/gdm: command not found

---

### Post by Pumalite on 2007-09-14
'When booting from the live cd's I get the screen where you need to select start normal or in safe graphics mode etc. When selecting either one of the two mentioned ubuntu starts its thing but just as it should load the gnome or kde interface I get a pretty messed up screen.'

At this point you enter: Ctrl+Alt+F1(to get a command line), then:
sudo /etc/init.d/gdm stop, then
sudo dpkg-reconfigure xserver-xorg

---

### Post by jjames on 2007-09-14
Hi Pumalite

Okay I did it like that and I get another error when runnung "sudo /etc/init.d/gdm stop";

sudo /etc/init.d/gdm: command not found

Thanks for the help!

---

### Post by Pumalite on 2007-09-14
That means you do not have your system installed. You should use Alternate CD for the installation (avoids graphics and other hardware problems):
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below green sign 'Start Download'

---

### Post by jjames on 2007-09-14
Thanks man! Let me try the text based installer. I installed a laptop with the gui and it worked nicely so I thought why not do my dektop as well....5 days later :-)

Let me start downloading.

Thanks again

Cheers!

---

### Post by Pumalite on 2007-09-14
You are welcome. Good luck.

---

### Post by jjames on 2007-09-14
Hi Pumalite

So while Im downloading Ive been playing around and noticed that after the fatal error I get it says " no screens found"

Now Im thinking that even the text based installer will not be able to start he gui....What do you think?

JJ

---

### Post by Pumalite on 2007-09-14
The Alternate CD is supposed to avoid that kind if problem. Let's see.

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by jjames on 2007-09-14
okay...

---

### Post by jjames on 2007-09-14
Hey Pumalite

I installed the system with the alternate cd but am experiencing the same problem when Kubuntu boots. No Gui.

I ran the commands you gave me earlier from the command line and still no luck.

Linux is waring me down man....

---

### Post by Pumalite on 2007-09-14
You are wearing ME down (lol). Post the specs of the new system you are installing to. I'm assuming you are using the Alternate CD.

---

### Post by jjames on 2007-09-14
Hi Pumalite

Yes I am using the Kubuntu alternate cd - kernel 2.6.20-15

My desktop specs are:

Intel P4 3GHZ
1GB Ram
Onboard graphics (64M)
VIA P4M890 Chipset Motherboard
1 X 80GB SATA HDD (Master) - Kubuntu on (hd0,2), WinXP on 1st partition 
1 X IDE 80 GB HDD(Slave)
Tv card
NIC
USB hub
Bluetooth dongle
BenQ FP91G X

Shout if you need anything else.

Thanx
JJ

---

### Post by Pumalite on 2007-09-14
Let's see if you have the system installed first. Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by jjames on 2007-09-14
Hi Pumalite

There is quite a bit to type here :-)
-------------------------------------------------------------------------
Disk /dev/sda:82.3 GB bla, bla

Device               Boot        ....................ID                 System
/dev/sda1                                                   7                   NTFS
/dev/sda2                                                   7                   NTFS
/dev/sda3           *                                      83                 Linux      (30GB)
/dev/sda4                                                   5                   Extended
/dev/sda5                                                   82                 Linux Swap / Solaris (1.3GB)

Partition table entries are not in disk order

(Here it lists the slave drive with 3 NTFS partitions)

-------------------------------------------------------------------------

cat output:

title Ubuntu, memtest86+
root (hd1,2) ...............I need to get this changed to (hd0,2) I change manually in grub @ the moment............
kernel /boot/memtest86+.bin
### END DEBIAN AUTOMAGIC KERNELS LIST
..............................
..............................
..............................
#This entry auto added by the Debian installer for non linux OS
#on /dev/sda1
title WinXP
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
---------------------------------------------------------------

Thats it
JJ

---

### Post by jjames on 2007-09-14
While we are here with /boot/grub/menu.lst, can you tell me how to vi this file so that I dont have to change the settings everytime I boot ?

I know the commands or getting around in vi is not so nice if you dont know it.....:-)

---

### Post by Pumalite on 2007-09-14
vi /boot/grub/menu.lst

It seems you just have to configure your xorg. But I'm not satisfied because you didn't copy and paste the outputs. Try to boot Live CD, mount partition and provide me with copy and paste of the commands I asked you. If not get Knoppix: [http://www.knoppix.org/](http://www.knoppix.org/) (it mounts partitions automatically) and give me the outputs.

---

### Post by jjames on 2007-09-14
Okay

I dont know how to copy and paste in a terminal window without a mouse in Ubuntu. I will try booting with knoppix...should have a copy here somewhere.

---

### Post by jjames on 2007-09-14
Oh, and I cant boot with the live cd's...same problem. Let me try knoppix

---

### Post by jjames on 2007-09-14
Hi Pumalite

Knoppix is a no go....also not booting. How do I copy and paste in ubuntu command line with no mouse?

---

### Post by Pumalite on 2007-09-14
If you cannot Knoppix, then there is something really wrong with your computer. Knoppix boots just about anywhere. I'm going to have to review the thread.

---

### Post by Pumalite on 2007-09-14
What's the meaning of this: Onboard graphics (64M)
And did you stop xserver before before running sudo dpkg-reconfigure?

---

### Post by jjames on 2007-09-14
According to my motherboard booklet the onboard graphics card has 64mb memory. I ran the following commands:

sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg 
startx

---

### Post by Pumalite on 2007-09-14
I'd say the onboard graphics are the problem and don't know what else to tell you. Sorry jjames. Maybe get an Nvidia AGP (whatever your board supports)

---

### Post by jjames on 2007-09-14
Okay, thanks anyway. Imanaged to mess up my xp installation as well :-)

It was worth a try though. 

Thanks for all the help Pumalite, much appreciated!

Cheers
JJ

---

### Post by Pumalite on 2007-09-14
Not all is lost. Plug in your XP CD, hir 'r' for Recovery>FIXMBR>FIXBOOT
Another thing is bothering me. You mentioned only sda in your typo, but what's in sdb and what hard drive are you booting from?. Is a SATA first?. or is the IDE first?. You could try to edit your menu.lst any way: Kubuntu: )hd0,2, Windows: (hd0,0) according to what you told me.

---

### Post by jjames on 2007-09-17
Hi Pumalite

Okay, I went out and bought a nice graphics card that cost me a pretty penny. Got home and realised that my dvi cable had gone missing so had to ge back yesterday and buy that.

Plugged it in and without any hasles, ubuntu booted up and is working. So, it was the onboard graphics card that screwed us around.

Thanks for the help buddy!

Cheers 
JJ

---

### Post by jjames on 2007-09-17
Let me ask you this, I downloaded the source code and data files for Chromium. When I run ./configure I get losts of failures and when I try to run make, it doesnt. 

The thing is I dont really know how to compile anything in Linux.

---

### Post by jjames on 2007-09-17
Does the files have to be in a specific folder or something? I just have it in my home directory...

---

### Post by Pumalite on 2007-09-17
Make sure you have build-essential.
sudo apt-get install build-essential

---

### Post by jjames on 2007-09-18
Hi Pumalite

So I played around with my mobile on linux and got connected to the internet from the linux box using wvdial. Dont think it was a 3g connection...more like gprs.

Anyway, got Chromium downloaded by using synops tool (you know what I mean....cos I dont know if the name is correct :-) )....I will  have a look at build-essential as well for next time.

I also installed some codecs for mp4 and mp3's however, I still can play them...

When trying to play a mp3 it says no supported codec found and wants to look for it online everytime. I downloaded and installed twice without errors but still cant play...

I did notice that it said it was uncertified software and then I just selected "to be installed" and clicked apply. Is there a setting somewhere where I should go and allow uncertified software?

Also, I made a launcher for wvdial. When clicking on the launcher it connection is opened but then there is no terminal window to press Ctrl+C to close the connection. I checked the man pages for wvdial but dont see any argument one can run with the command to close active connections. I later did a ps -ef, checked for the PID and killed it that way. But that is not too nice.....is there an alternative?

Cheers 
JJ

---

### Post by Pumalite on 2007-09-18
To play MP3. xvid,etc:
sudo apt-get install ubuntu-restricted-extras
sudo apt-get install vlc

---

### Post by jjames on 2007-09-19
Thanx mate! Will try tonight.

---

### Post by jjames on 2007-09-22
Hi Pumalite

Im having so trouble with wvdial. To be more specific, Im having trouble creating a launcher for it. I put the exact same command "sudo wvdial gprs" in the command as I put it in the terminal window. In the terminal window it works but in he launcher it doesnt. For tsome reason it doesnt see the [Dialer gprs]....

The out put I get when running the launcher:
----------------------------------------------------------------------------------------------------------------------
--> WvDial: Internet dialer version 1.56
--> Warning: section [Dialer grps] does not exist in wvdial.conf.
--> Cannot get information for serial port.
--> Initializing modem.
--> Sending: ATZ
ATZ
OK
--> Sending: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
OK
--> Modem initialized.
--> Sending: ATDT*99***1#
--> Waiting for carrier.
ATDT*99***1#
CONNECT
~[7f]}#@!}!} } }2}#}$@#}!}$}%\}"}&} }*} } g}%~
--> Carrier detected.  Starting PPP immediately.
--> Starting pppd at Sat Sep 22 15:25:24 2007
--> Pid of pppd: 16034
--> Using interface ppp0
--> pppd:  [07][06][08]&#65533;[06][06][08]
--> pppd:  [07][06][08]&#65533;[06][06][08]
--> pppd:  [07][06][08]&#65533;[06][06][08]
--> pppd:  [07][06][08]&#65533;[06][06][08]
--> pppd:  [07][06][08]&#65533;[06][06][08]
--> pppd:  [07][06][08]&#65533;[06][06][08]
--> Disconnecting at Sat Sep 22 15:25:28 2007
--> The PPP daemon has died: A modem hung up the phone (exit code = 16)
--> man pppd explains pppd error codes in more detail.
--> Try again and look into /var/log/messages and the wvdial and pppd man pages for more information.
--> Auto Reconnect will be attempted in 5 seconds
----------------------------------------------------------------------------------------------------------------------

Any ideas?

Cheers 
Justin

---

### Post by jjames on 2007-09-22
Oh....and Im connected to this forum now by making use of wvdial in the terminal....

---

### Post by Pumalite on 2007-09-22
Are you using an USB Modem?

---

### Post by jjames on 2007-09-22
Yep, using my nokia n95 on usb port.

---

### Post by Pumalite on 2007-09-22
That's your problem.

[http://forums.suselinuxsupport.de/lofiversion/index.php/t31843.html](http://forums.suselinuxsupport.de/lofiversion/index.php/t31843.html)
(it's from Suse, but it might give you an idea)

[http://mybroadband.co.za/vb/archive/index.php/t-27138.html](http://mybroadband.co.za/vb/archive/index.php/t-27138.html)

I  would check your modem for compatibility with Linux.

---

### Post by jjames on 2007-09-24
Hi

I doubt that it is the modem as it works when I run the commands from the terminal. Im typing this reply using that same modem but executed the command by terminal.

The problem is only when I create a launcher for the command.
wvdial does for some or other reason not see the [Dialer gprs] profile in the wvdial.conf file. But I know that the [Dialer gprs] is in the conf file abd that is the same conf Im running now....

Thanx
JJ

---

### Post by Pumalite on 2007-09-24
Glad you are advancing.

---

