---
title: "when i install linix i just get a blank screen ?? help"
date: 2008-03-12
forum: Installation &amp; Upgrades
---

### Post by Greg2bt on 2008-03-12
I am new to the whole Ubuntu thing first off... But what is my problem is i am getting a blank screen when I try to install Ubuntu. The Ubuntu "install screen" comes up fine and then when I try to perform a action it just gives me a blank screen. And yes I have tried it in safe graphics mode too. PLZ help??

---

### Post by Greg2bt on 2008-03-12
and i have a 8800 gts and 2 gb or ram, anyone know what the problem is??

---

### Post by Pumalite on 2008-03-12
Install with the Alternate CD. Download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below sign 'Start Download'
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on your iso, burn at 4x or less, use CD-R, check CD integrity after burn and before install

---

### Post by Greg2bt on 2008-03-12
do you mean the server edition or what?

---

### Post by Jiffyman on 2008-03-12
The alternative CD is a non graphical install. To me it sounds like it can't start the X server by it's self. When the CD loads up and gets to the blank screen press Ctrl+Alt+F1 or is it Ctrl+Alt+F2, anways a terminal/command prompt should then pop up afterwards type in "startx" without quotes.

Note: When the install is complete you have to perform the same steps to start the graphical interface each time you boot unless you install the restricted video driver. Well thats how I fixed it anyway.

---

### Post by Greg2bt on 2008-03-13
i tried that and it still didn't work...

---

### Post by Pumalite on 2008-03-13
Give details and post exact error messages.

---

### Post by Pumalite on 2008-03-13
I just read your PM.
If you end up with a blank screen at the end of the installation:
Ctrl+Alt+F1 to get command line. At the command line:
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver. Then:
startx

---

### Post by marstein on 2008-03-13
I may have the same problem - using 7.10 AMD64 DVD installing on a Gigabyte P35-DSR3 board with E8400 CPU and 4 GB of RAM and a 8800GTS 640MB card.
The DVD seems to boot okay and the DVD drive and HDs do things, but the screen stays black. It's as if there is no video signal at all after the first boot screen.

---

### Post by gtdaqua on 2008-03-14
> **marstein said:**
> I may have the same problem - using 7.10 AMD64 DVD installing on a Gigabyte P35-DSR3 board with E8400 CPU and 4 GB of RAM and a 8800GTS 640MB card.
The DVD seems to boot okay and the DVD drive and HDs do things, but the screen stays black. It's as if there is no video signal at all after the first boot screen.

can u press ctrl+alt+f1 and go to terminal logon screen directly? if yes, then your display drivers have to be reinstalled. tell us if this is the case and i will post how to do a nvidia driver installation.

---

### Post by slipline on 2008-03-16
I have the same problem

EVGA 680I, EVGA 8800GTS, 6600 c2d

300gb NVRaid Raid 0, All drives including dvd are sata. 

Boot to Live CD or DVD, Kernel load indicator shows up , gets to 100 and then screen goes blank. I hear the CD spin and it does stuff for a bit but nothing after that. 

THere is nothign wrong with the images. I have burned them several times in windows and linux at 4x. CRC checked and all good. There is just nothing going on. Cant even get a term or get to any error messages. 

Im quite sad as I thought ubuntu was pretty painless to install. Im having a hell of a time with her. 

I got SUSE to install but couldnt get nv-glx modules to load properly.

---

### Post by Pumalite on 2008-03-16
Maybe you have a Fake Raid:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by slipline on 2008-03-16
yeah its fakeraid for sure but i cant even get to configure options for that. I am installing with altcd in txt mode now. It appears as if ubuntu is ignoring the NVRaid and seeing both drives. Im just going to install to one drive now and see what happens. 

SUSE had no problems, picked up the array as 1 drive and installed accordingly.

---

### Post by miragul on 2008-03-17
I have the same problem with an EN8800 GTS card, blank screen from install cd's or HDD.

I wonder if this is only caused by the 8800 GTS card or if this is some weird combination of other hardware + 8800 GTS. 

I previously had an ATI card in the same machine without any problems.

I was able to boot single user and start xorg manually though, worked fine with nv/nvidia/vesa drivers. 

Perhaps it's a problem with framebuffer during the bootscreen?

---

### Post by tqvn2004 on 2008-03-17
> **gtdaqua said:**
> can u press ctrl+alt+f1 and go to terminal logon screen directly? if yes, then your display drivers have to be reinstalled. tell us if this is the case and i will post how to do a nvidia driver installation.

I dont know if I got the same problem as the others. I have installed Ubuntu 7.10 on my desktop, intel Core2Quad, 2GB, GTS8600 Nvidia, 500GB SATA. The installation went well, and after it finished, I was able to login for about 2 minutes. Then the screen went blank, it seems there is no signal from the graphic card. And the keyboard is hang, caplock key does not trigger the caplock led, and ctr+alt+f1 does not function.

I restart, and the problem happen again intermittently. Sometimes after 1 minutes, it hang up with the blank screen, sometimes after 20 minutes. I am a newbie in Linux, and this is really scary...

For your information, I have disable the nvidia driver, run all the updates, and dual boot with XP. My Ubuntu is fresh, I only add emacs, wine and texlive-latex-base from the repositories...

---

### Post by Pumalite on 2008-03-17
Download driver from here:
[http://www.nvidia.com/Download/index.aspx](http://www.nvidia.com/Download/index.aspx)
Then install it in Virttual Terminal:
Ctrl+Alt+F1
username
password
sudo /etc/init.d/gdm stop
sudo sh /path/to/driver/NVIDIA-Linuxxxxxx.run
Accept license
Let driver compile the module into your kernel
Let driver reconfigure your xorg.conf file
Then: startx
Make sure you have build-essential first:
sudo aptitude install build-essential

---

### Post by tqvn2004 on 2008-03-18
Hi Pumalite, I have done as you said, but I just got another black screen and had to restart just now :( 

No clue where the problem might be... It is like playing lotto: yesterday I can use my Ubuntu for the whole day without any problem. Restart today, got one crash. Restart again and now (after 30 minutes), no crash...

---

### Post by marstein on 2008-03-18
I did what pumalite suggests and the driver installed - and the screen finally used the whole resolution of the monitor. But rebooting brought a warning message that I was using a low resolution and after logging in I had a really weird double image. It was hard to make anything out but it I found that the nvidia driver was NOT running. Also the restricted drivers manager showed that the nvidia driver was disabled. I enabled it, rebooted and the same problem. How can I make the driver stick?

---

### Post by Greg2bt on 2008-03-20
so i did download the driver but that did allow me to get to the tan screen and then it frezzes like the mouse wont move what do i want to do now?? and this pc i built is nice and fast with sore two and 2 gb so its not like its slow.. can anyone help?

---

### Post by Pumalite on 2008-03-20
[http://ubuntuforums.org/showthread.php?t=729995](http://ubuntuforums.org/showthread.php?t=729995)

---

### Post by Greg2bt on 2008-03-20
well i just want to know what to do from here??

---

### Post by gumdrop66 on 2008-03-20
me too!!!!'ve tried over and over to install from cd.. and i dont understand all of the 'fixes' and answers..like turning off apci, turning off splash etc :(
help!

---

### Post by wilson757 on 2008-03-21
Let me know if you figure it out or have any other thoughts on how to t/s it some more. I seem to be having a similar problem trying to install personal X64. After waiting about a minute into start/install I do get "ubuntu is running in low-graphics mode" box and it ask me if I need to configure, shut down or continue. If i leave it in low mode it displays this....
*starting deferred execution scheduler atd [ok]
*starting periodic command scheduler crond [ok]
*checking battery state... [ok]
*running local boot scripts (/etc/rc.local) [ok]



thank you for your time

__________________
-E4500(OC @ 3014), 2gig ddr2@ 725, 8800gts, ASUS P5E-VM

---

### Post by serhiy30 on 2008-03-23
I tryed every install , i think i installed it in command line ,at list my screen is staying  and no over range sign pops up.
thats what i have on my screen

---

### Post by serhiy30 on 2008-03-23
I tryed every install , i think i installed it in command line ,at list my screen is staying  and no over range sign pops up.
thats what i have on my screen
[IMG][[IMG]http://img146.imageshack.us/img146/8095/0323080902vk8.th.jpg[/IMG]](http://img146.imageshack.us/my.php?image=0323080902vk8.jpg)[/IMG]

---

### Post by Pumalite on 2008-03-23
When your hardware is incompatible and nothings works, there still exist 'boot parameters' that can be used alone or in combination. Here is a guide on how to use them:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
And a small collection of them to get you started:
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
Use the most common first:
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317 vga=791
In case of resolution problems:
[http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters](http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters)

---

### Post by Greg2bt on 2008-03-24
is there a number i can call for Ubuntu help?

---

