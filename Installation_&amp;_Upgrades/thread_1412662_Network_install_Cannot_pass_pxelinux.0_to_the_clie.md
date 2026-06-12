---
title: "Network install: Cannot pass pxelinux.0 to the client machine (bootptab - how?)"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by Zalanthas on 2010-02-21
Hi,

This is my first post here. I must say, moving from Windows to Ubuntu was like emerging from dark ages into renaissance... I feel like I can tell something to Ubuntu and it will understand me :). Well, two weeks has passed and I know my way around Desktop Edition. Now, I would like to get my hands on Server Edition, but I could not succeed properly installing one into my home server. If anyone can help me out with my problems, I will be very glad.

Here it goes (but please keep in my that I have no prior experience with Linux) =>

For the last several days I am trying to install Hardy Server LTS 32-bit Edition to IBM Netfinity 4000r server.

I tried to install from "several" different live-cds (checked m5sum and did everything for all of them) and none of them booted (the server has cd-rom and I can get into the bios to boot from it, but when it tries to boot, it does not recognize the boot sector). I tried 64-bit, and somehow it boots and shows me the install screen. But, since my server is not 64-bit, it says it cannot continue. Gives me i686 suggestion. I tried other i686 specific linux distros and none of them worked either.

I even tried to boot with live GpartedCD, but it failed as well.


So, my last resort is installing via network boot (my bios does not support usb boot eventhough there are 2 usb ports at the back). 

I have Ubuntu 9.10 running from persistent USB stick at my Laptop and will use it as host server for the install.

Last two days I spent countless hours trying to figure out the related help files and documentation with no end result. I learned tons of new stuff, but since I am a newbie to Linux and Ubuntu, I could not understand the seemingly basic stuff.

I am in dire need. Please help me :). Here is what I have done =>

Main help files I used are these =>

[https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)
[https://help.ubuntu.com/8.10/installation-guide/i386/install-tftp.html](https://help.ubuntu.com/8.10/installation-guide/i386/install-tftp.html)

Both says that I need bootp server, tftp-hpa server, and access to the routers. I installed bootpd and tftp-hpa via apt-get and have access to my router.

I can see them at /etc/inetd.conf =>
bootps  dgram udp wait root /usr/sbin/bootpd     bootpd -i -t 120
tftp    dgram udp wait root /usr/sbin/in.tftpd /usr/sbin/in.tftpd -s /var/lib/tftpboot

* Here I don't understand why "/usr/sbin/in.tftpd" prints twice.

I also did this =>
RUN_DAEMON="yes" (it was "no" when I first installed and I changed it to "yes")
OPTIONS="-l -s /var/lib/tftpboot


Than, as instructed at the documentation, I created /etc/bootptab file for bootp server, so that it can read the specs that I give to it. Here is my /etc/bootptab file =>

client:\
  :ha="00:06:29:XE:E3:CD":\ (MAC of the server)
  :ip=192.168.2.4:\  (IP of the server, from router)
  :sa=192.168.2.2:\  (IP of host)
  :sm=255.255.255.0:\
  :td=/tftpboot:\
  :hd=/netboot:\
  :bf=pxelinux.0:

Here is the things that I don't understand =>

client:\
Am I supposed to enter something different than "client" here? My server does not have an assigned name at the router level. When I check it from my router for the MAC Address, it does not specify a name for it. I see the names of other computers in the LAN.

:sa=192.168.2.2:\
I know this should me the host computer's IP, right? My host computer's ip is actually 192.168.2.2. But, when I boot the IBM Netfinity via PXE-boot, it tells me that the DHCP's IP is 192.168.2.1, not my host's IP ending with 2. What should I do?

:gw=:\
Do I need to use gw instead of sa? The examples in the documents have different setups. One uses sa and the other uses gw for host IP.

:td=/tftpboot:\
I have tftpd-hpa installed. What should I write down for :td=???:\. There are some reference to this => /var/lib/tftpboot. Should I write it instead of simple /tftpboot?

:hd=/netboot:\
I installed netboot tarball and extracted into /var/lib/tftpboot and it become /var/lib/tftpboot/netboot... and my pxelinux.0 is in it. So, should I write :hd= with /netboot:



On top of all of this, I have no idea how to start or restart both bootpd and tftpd-hpa servers. I am changing /etc/bootptab file to try different setups, but I am afraid that my changes are not registering. When I edit /etc/bootptab, do I need to restart-reload something? Maybe this /etc/inetd.conf or this /etc/init.d/inetd? If yes, how can I do it?

I tried this and did not work =>
sudo /etc/init.d/inetd reload


Right now, my server boots with PXE, prints me its MAC address, than client IP, but than it says boot image was not received/transferred.
Error: PXE-E53: No boot filename received

after that, it tries cd-rom, but fails to boot again
1962 Drive does not contain a valid boot record.

I imagine, I am doing something wrong with /etc/bootptab file, possibly the location is wrong???


Could anyone help this poor newbie? I feel that I am losing my mind :).

---

### Post by Zalanthas on 2010-02-22
I could start network install from Windows (in my previous post I was asking how to do it from Ubuntu).

I would like to share my experience of Windows Server Netboot for Ubuntu so that people who were lost like me can find a way and save their fine heads from going bald :)


THIS IS A COMPLETE BEGINNER'S GUIDE TO NETBOOT UBUNTU FROM WINDOWS TFTP/DHCP SERVER (no cd - no usb support needed)

Home: Acting as tftp/dhcp server, Windows PC
Client: The place where Ubuntu will be installed from LAN/Network

I will use netboot file for installation (it is a very small file containing just the kernel, the rest will be automatically downloaded from internet along the way). If you don't have internet access, you need to prepare the full iso file. I am a newbie :), so, just made it work with netboot.tar.gz and don't know what you need to do if you don't have internet access. Sorry.

1) Download and install tftpd32.exe from this [COLOR=Red]_*[link]("http://tftpd32.jounin.net/download/Tftpd32-3.35-setup.exe")*_[/COLOR]
2) Create a folder in your harddrive and name it tftp (it can be anywhere, not important).
3) Download your preferred Netboot.tar.gz: mine is Hardy LTS 8.04 and can get it from this [COLOR=Red]_*[link]("http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/installer-i386/current/images/netboot/")*_[/COLOR].
4) Extract the tar.gz file using 7-zip or WinRar into the tftp folder your created in step 2. You need to see ubuntu-installer folder and pxelinux.0 file. For that, you may need to extract twice.
5) Delete pxelinux.0 file (for some reason when you extract netboot.tar.gz, pxelinux.0 comes empty)
6) Go back to the netboot.tar.gz download location of step 3 and download a new pxelinux.0 file seperately and put it into the same location, where you deleted one in step 5. 
7) Erase pxelinux.cfp FILE -at default, it is unrecognized by windows- from tftp folder. Then browse into ubuntu-installer folder (comes when you extract netboot.tar.gz) and copy pxelinux.cfg FOLDER and paste it into tftp folder next to pxelinux.0 and ubuntu-installer.


NOW YOU CAN START TFTPD32.EXE


8- When it pops-up, change current directory to the tftp folder you created in step 2.
Server interface comes automatic, showing the host pc's (in this case, your windows based pc) IP.
9) Open your internet browser and access your router via 192.168.1.1 or 2.1 (whichever is working for you). Login.
10) Connect your ethernet cable to the client machine and start it. Configure it so that it boots from network with PXE.
11) Find DHCP Client list. This is the place you can see assigned IPs and MAC addresses. Refresh and get the IP of the client machine. While you are in the router, find/check your IP Pool and write down from which IP it starts.
12) Browse into program files/tftpd32 folder and open tftpd32.ini with notepad. Make sure your unclick -always open with notepad- since we don't want to change ini to txt. It needs to stay as ini for the program to run.
13) Enter this to a new line 0A:0B:0C:0D:0E:0F=192.168.1.75. Make sure you enter your client's MAC and IP you just pulled from your router at step 11, not the one I just gave you. Save and close.
14) Return to running tftpd32 and enter IP pool starting address and make sure size of pool = 0. This will force it to assign a static IP to your client machine from the ini file you just edited at step 13.
15) Boot file = pxelinux.0 (your are going to type this in, there is no browse and select)
16) WINS / DNS Server = 192.168.1.1 or 2.1 (depending on how you can access to your router).
16) Default router = same as step 16
17) Mask = 255.255.255.0

S
A
V
E

SAVE

Restart client machine.

tftpd32 will show you the MAC and IP of the client machine at DHCP Server tab.

you will also see it in your boot screen at your client computer and all the other IPs.

You can follow the progress at Log Viewer in tftpd32.


After that, -hopefully- you should see Ubuntu Install page.


I hope this solution works for you.





[COLOR=Red]BUT, I still don't know how to do the same from an Ubuntu machine. If I am going to make a complete transition from Windows to Ubuntu, than I should be able to do everything from Ubuntu, right :) ?

Please, my questions in the first post still stands. I really need help.[/COLOR]

---

### Post by Zalanthas on 2010-02-24
There is a very self exlonatory guide for PXE booting over network with Ubuntu Host =>

[COLOR=Black][yogesh.girikumar]("http://ubuntuforums.org/member.php?u=986828")'s post[/COLOR] explains in detail how to do it.. if you are stuck with PXE Netbooting, it will ease most of your pains.

[http://ubuntuforums.org/showthread.php?t=1413126](http://ubuntuforums.org/showthread.php?t=1413126)

---

### Post by darkdragn on 2010-02-24
It's actually a lot easier then the documentation says. In all seriousness, i've been doing it with dhcp3-server and opentftpd. The basic tftpd and tftpd-hpa had the same issue that i was running into, blksize limitations. I hate doing step by step things, but you can ask me any questions you want. 

For the dhcp server all you have to have is a simple subnet declaration, and a reference to your host computer, which is running opentftpd... but we'll get to the last part later. Here's what mine has:

subnet 10.129.15.128 netmask 255.255.255.224 {
  range 10.129.15.140 10.129.15.150;
  option routers 10.129.15.1;
  option interface-mtu 1400;
}

next-server 10.129.15.131;
filename "/pxelinux.0";

Obviously the tftp server's root directory is going to contain the file pxelinux.0 , and a folder called pxelinux.cfg. As far as the folder is concerned all you're required to have is a file named default. Within there you can have a quick reference to a kernel and an initrd. You can get  the pxelinux.0 from /usr/lib/syslinux on any ubuntu install. As for me, i'm a bit fancy with my menus. lol, here's what i mean:

# Default boot option to use
       DEFAULT pxelinux.cfg/vesamenu.c32

       # Prompt user for selection
       PROMPT 0
       TIMEOUT 50

       menu INCLUDE pxelinux.cfg/graphics.conf
       MENU ROWS 10
       MENU TITLE PXE (DARKDRAGN)

       LABEL part
         MENU LABEL ^1. Parted Magic Options
         KERNEL pxelinux.cfg/vesamenu.c32
         APPEND pxelinux.cfg/default.old

and pxelinux.cfg/default.old looks something like this

   # Default boot option to use
       DEFAULT pxelinux.cfg/vesamenu.c32

       # Prompt user for selection
       PROMPT 0
       TIMEOUT 100
       # Excess Information
       MENU F1 part/boot/message.txt

#      menu INCLUDE pxelinux.cfg/graphics.conf
       MENU ROWS 10
       MENU TITLE PXE (DARKDRAGN)
       MENU BACKGROUND part/boot/syslinux/splashpm.png
       MENU TABMSG Press <TAB> to edit options or <F1> for more information

       LABEL part
         MENU LABEL ^1. Parted
         KERNEL pmagic/bzImage
         APPEND initrd=pmagic/initramfs edd=off noapic load_ramdisk=1 prompt_ramdisk=0 rw vga=791 sleep=0 loglevel=0 keymap=us


Yes, when using pxelinux you can do menu include to put in configuration lines from another file. It's the same as having them in this config file, only easy to group similar lines together like this. In there i have a line that reads:
menu background pxelinux.cfg/bt4.jpg
Meaning you can have a background image to make it pretty, but i'm not sure if the default version that comes with ubuntu is new enough to support that, so i didn't put it in the bulk grouping of my config, so it doesn't confuse you guys. For more information on the images consult [http://syslinux.zytor.com/wiki/index.php/Comboot/menu.c32](http://syslinux.zytor.com/wiki/index.php/Comboot/menu.c32) ... (As you can see i use vesamenu.c32, ^_^) Here's the exact entry:

**MENU BACKGROUND** *background*  For vesamenu.c32, sets the background image.  The background    can either be a color (see MENU COLOR) or the name of an image    file, which should be 640x480 pixels and either in PNG or JPEG format. 


Also, if you want to pass to other menus, just use the .c32 file (menu, or vesamenu) as the kernel, and have the config file in the append. But... on to the business at hand...
Opentftp, get it from [http://sourceforge.net/projects/tftp-server/](http://sourceforge.net/projects/tftp-server/) . Compile, and make sure that tftpd, tftpd-hpa, xinetd, or inetd isn't running to interfere with opentftpd. This have a really cool feature btw, you can run it with the -v argument and get a constant on screen log. After the compile, copy the opentftpd.ini over to the /etc directory, and open it for editing. The only thing you really have to change is the root directory. It's pretty self explanatory, in case you want to change anything else... here's what i mean:

[HOME]
#You should specify home directory(s) here
#The home directory can be specified
#in two different ways, with alias or
#bare names without aliases. Using alias you
#can specify upto 8 directories like
#routers=c:/RouterImages/Images
#without aliases, only one directory can
#be specified, which will become root
#directory for tftp.
#mixup of bare names and aliases not allowed
#default will be home directory of user
/tftpboot

(Obviously /tftpboot is the directory i'm using.) Other than that there's nothing else you have to do. Start the dhcp server, start opentftpd make sure the cfg is right... such as in my example with default.old, the local file structure is as follows:

/tftpboot/pmagic/
/tftpboot/pmagic/bzImage
/tftpboot/pmagic/pmodules
/tftpboot/pmagic/pmodules/scripts
/tftpboot/pmagic/initramfs

But in the config it reads:
pmagic/bzImage
pmagic/initramfs

I just wanted to mention that, /tftpboot is literally read as the root for the tftpserver... good luck!!

---

