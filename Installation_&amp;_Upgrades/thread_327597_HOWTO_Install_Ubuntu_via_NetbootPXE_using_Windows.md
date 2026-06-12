---
title: "HOWTO: Install Ubuntu via Netboot/PXE using Windows"
date: 2006-12-29
forum: Installation &amp; Upgrades
---

### Post by scaryant on 2006-12-29
Here's a brief overview of what you need and need to do to complete this;

1. One Windows based (XP/2000) to host TFTP Server, network enabled
2. One PC to have Ubuntu installed on to, with Intel PXE Boot capability
3. DHCP & TFTP Server ([download Tftpd32]("http://tftpd32.jounin.net/") (freeware)
4. Download Ubuntu [netboot.tar.gz]("http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/")
5. Live Internet Connection preferably via xDSL (broadband)
6. If you have a ADSL modem "router" with DHCP enabled, then you must temporarily disable the DHCP. You will only have a "router" if you have the capability to run more than one PC on your home network.

**Setup your network environment**
This procedure is a rough guide as a lot of home environments are different, you DO NOT need to do this if your network is configured with static IP Addresses (which means you are not using DHCP on your router aka where IP Address are Dynamically Allocated to PC's on your network)
1. Start > Run > type *CMD* > OK
2. At the command prompt type *ipconfig /all*
3. Copy down the following details: *IP Address, Subnet Mask, Default Gateway, DNS Servers*
[INDENT]- Your IP Address should look something like 192.168.1.3[/INDENT]
4. Log onto your router via the web interface (most ADSL routers have this)
[INDENT]- Normally you can do this by typing the Default Gateway address into your web browser[/INDENT]
5. Locate the section that relates to the DHCP Server, disable the DHCP server, save changes.
6. Now setup your Windows PC with a static IP Address 
[INDENT]Start > Control Panel > Network Connections > right-click *Local Area Network* > select *Properties* from floating menu[/INDENT]
[INDENT]NB: If you're using wireless networking, instead of Local Area Network, select Wireless Network Connection, then right-click and select Properties.[/INDENT]
7. On General tab, scroll down and select *Internet Protocol (TCP/IP)*
8. Click *Properties*
9. Select *Use the following IP Address*
10. In IP Address type the IP Address you wrote down eg 192.168.1.2
11. Enter the Subnet Mask you wrote down eg 255.255.255.0
12. Enter the Default Gateway eg 192.168.1.5
13. Select *Use the following DNS Server addresses*
14. Enter the DNS Server Address you wrote down (most likely the same as Default Gateway) eg 192.168.1.5
15. Click OK to set changes to TCP/IP
16. Click OK to close network settings.
NB: We will revert these changes later.

**Download & Configure DHCP/TFTP Server**
1. Once you have downloaded the TFTPd32 Software, create a directory on the server PC. eg C:\tftpd32
2. Extract the TFTPd32 software to the directory you created
[INDENT]You should have 3 files: tftpd32.exe, TFTPD32.HLP, uninst.exe[/INDENT]
3. Run the tftpd32.exe which will start the DHCP/TFTP Server for Windows
4. Select the DHCP Server Tab
5. In *IP Pool starting address* enter an IP Address greater than the one you gave your Windows machine. eg if your windows machine was 192.168.1.2 enter 192.168.1.3
6. In *Size of Pool* enter the number of machines you intend on having Ubuntu installed on (each machine will need an IP Address)
7. In *Boot File* enter *pxelinux.0*
8. In WINS/DNS Server enter your DNS Server Address you wrote down eg 192.168.1.5
9. Enter the same number in *Default router*
10. Enter the number you wrote down for Subnet Mask in *Mask*
11. In *Lan* enter *lan* - doesn't matter what you enter here really
12. You must have this software running when you reboot the other PC(s) for PXE to pick-up the Ubuntu install.
13. If your other PC has Windows on it, it might be a good idea to ensure that the DHCP is working. 

If the settings you copied down are correct, then your second PC should get an IP Address, DNS Server, Gateway IP Address etc and you should be able to surf the net. It is imperative that you can surf the net, because the Ubuntu installer gets the install files from the net for the installation.

If you can't, then one of your IP addresses may be incorrect or the network card might not be functioning correctly. Unfortunately troubleshooting is beyond the scope of this howto.

**Extract & Configure Ubuntu Image**
1. Download and use WinZip to extract the files from netboot.tar.gz
2. Copy the *ubuntu-installer* directory and it's contents to your TFTP directory eg C:\tftpd32\ubuntu-installer
3. Also *copy* the entire *contents* of \ubuntu-installer\i386\ directory to the TFTP directory C:\tftpd32\
[INDENT]This is duplication I realise, but for some reason you must have some or all of these files duplicated this way for the install to boot. I didn't have time to figure out which one needs to be there, so I just duplicated the lot... how lazy am I?![/INDENT]

**Running the Ubuntu Install**
1. Have your Windows machine running, with the TFTP Server running and connected to the local network (by wire or wireless, doesn't matter)
2. Reboot the machine you want to install Ubuntu on and enter the BIOS (normally requires the user to hit an F key eg F2)
3. Locate the Boot sequence in the BIOS and change the priority so that LAN boot is first, then HDD.
4. Save changes and exit, reboot.
5. The PXE Boot should appear and attempt to first retrieve an IP Address, then it should begin loading the Ubuntu installer. Wow!
6. Run through the install as documented...

**Clean Up**
1. Once the install is completed, you can close the TFTP/DHCP Server
2. Delete the directory and files you created for the TFTP Server eg Delete the directory C:\Tftpd32
3. Re-enable DHCP on your router (follow the instructions for "Setup your network environment" steps 1-5)
4. Re-enable DHCP for your Windows machine (TFTP Server) (Follow the instructions for "Setup your network environment" steps 6-16 however where Select "Use the following IP Address/DNS Server Addresses" was written, select the option "Obtain an Address Automatically"

... and you're done! Feel free to edit, praise, update or amend this as it was just a brain dump that I thought would help ppl as it took me all day to get working!

Cheers

:D

---

### Post by DigitalDaiquiri on 2006-12-31
EDIT: NM mate, I found out the reason for the problem.  I didn't have the correct directory set in the TFTP/DHCP Server. Thanks for all of your help though!

Amazingly well written guide mate!  I have spent upwards of 20 hours in the past few days trying to accomplish the same task on a Ubuntu server using the tutorial at [http://www.howtoforge.com/ubuntu_pxe_install_server]("http://www.howtoforge.com/ubuntu_pxe_install_server") In comparison I was able to accomplish the bulk of your guide without many issues.  The only problem I have is the detection of the pxelinux.0 file from the computer on which I'm trying to install Ubuntu.  The computer I'm booting in PXE detects my DCHP Server Windows box, receives a client IP, mask, DHCP IP, and Gateway IP.  It then lists two errors:

```
TFTP.
PXE-T01: File not found
PXE-E3B: TFTP Error - File Not found
```

I am able to surf the net on another computer on the network just fine, so I would assume that the DHCP isn't the problem.

In your guide you mentioned copying both the "ubuntu-installer" directory and the contents of the "\ubuntu-installer\i386\" directory into C:\tftpd32\ .  I didn't have a tftpd32 directory in my C:\ directory so I assumed that you meant for me to create one.  Will the PXE be able to find the appropriate file anywhere on the computer or does it need to be in a certain location?  I absolutely appreciate your days work on writing this guide, and I would be so gracious if you could help me with my issue.  After all I am trying to install Ubuntu on my mothers laptop (which lacks both CD-ROM, and Floppy drives) to help spread Linux.  Thanks again for your help. :D

---

### Post by scaryant on 2006-12-31
Hi There,

Thanks, for the comment... now to your questions.

Q: > I didn't have a tftpd32 directory in my C:\ directory so I assumed that you meant for me to create one.

A: Yep. You must create one, doesn't have to be named that though you can name it what you like. But keep it short and simple.

Q: > In your guide you mentioned copying both the "ubuntu-installer" directory and the contents of the "\ubuntu-installer\i386\" directory into C:\tftpd32\ .

A: Yeh, that's correct I basically had all the contents of the i386 directory *pxelinux.0, linux, initrd.gz, boot-screens, pxelinux.cfg, pxelinux.cfg.serial-9600* in the C:\tftpd32\ directory and then I also had all these files in C:\tftpd32\ubuntu-installer\i386\..

Important to note, if I didn't have the files copied this way the PXE boot loader would either not find the pxelinux.0 or it would fail as it loaded the install boot sequence complaining that the install couldn't find specific files in the \ubuntu-installer\i386\ directory.

Q: > Will the PXE be able to find the appropriate file anywhere on the computer or does it need to be in a certain location? 

A: Yes, if you're using the TFTP/DHCP server I linked to you can specify the file path to the boot image on the DHCP Server tab in the *Boot file* field. In my example I've located the boot image (pxelinux.0) in the directory where I'm running the TFTP server, so there's no need to specify the file path, just the file.

To be honest though I'd keep it simple, if you want to put it in another directory use simple directory names eg less than 8 characters, no symbols like - or _ or spaces. Something like C:\temp\bootimg\pxeloader\ 

You might get away with something more complex but some older BIOS' may not like it.

> I absolutely appreciate your days work on writing this guide, and I would be so gracious if you could help me with my issue.

No problems, good luck, let me know how you go! :-D

---

### Post by scaryant on 2006-12-31
Sorry I should have said, that it does appear that the your TFTP and DHCP server are working correctly. It appears that you are also connecting to the TFTP Server, however it seems the TFTP Server is not able to locate the boot image (pxelinux.0). This may be because you haven't put the pxelinux.0 file in the correct place (in the case of the document above C:\tftpd32\pxelinux.0 and for good measure copy it to C:\tftpd32\ubuntu-installer\i386 with the rest of the files as explained earlier.

One thing that I didn't mention in the documentation above is ensure that you have **disabled any firewalls** that are on your Windows machine hosting the TFTP server. This might be a source of trouble if the port the TFTP Server is operating over is blocked.

If you're using the Windows XP firewall you can follow these [instructions]("http://www.microsoft.com/technet/community/columns/cableguy/cg0204.mspx") to disable it.

Be sure to re-enable as part of your clean up once you're done. ;)

Cheers

---

### Post by dessip on 2007-01-05
Hey,
THank you for your guide, this is excellent, i have such a old cd drive and it takes forever for it to do anything. but i was wonderinf if there is any way that you could do a PXE boot from a local install,. because my internet connection is really slow, and also i can not manage it, so if it was possible to be able to do it from a local source that would be excellent.

Thank you

---

### Post by scaryant on 2007-01-06
No worries. I'm almost certain you could do an install without using the net to download the files during the install, however it would probably involve using the ISO image of the Ubuntu software so you'd have to download this first - which is probably going to take you just as long. The only way to get around that would be to order a copy of the cd or get one from a friend and create the ISO image using some cd burning software.

To get it to work I think you probably need to re-configure one or two of the files in the ubuntu-installer directory. I'll see if I can find out...

---

### Post by dixonp on 2007-01-06
I did it with the ubuntu-6.10-alternate-i386.iso image: apparently you just need to export the APT repository present on the iso over HTTP. See:

[http://ubuntuforums.org/showthread.php?t=332343](http://ubuntuforums.org/showthread.php?t=332343)

But by doing that I ran into what seems an installer bug: a GPG error preventing packages from being authenticated, and aborting the installation. Fortunately I found a workaround (see thread). I would appreciate if someone could point out what I did wrong.

---

### Post by dessip on 2007-01-14
Hey,

That is excellent thank you, lets see if i can get it working :)

---

### Post by phuturism on 2007-01-22
Scaryant - thank you so much.

I have a toshiba portege 3480CT laptop  with a USB CDROM drive that cannot be booted from the BIOS.  After lots of pain trying to install from dos floppies with modified USB CDROM drivers and files, I gave up and tried a netboot from Ubuntu - this was too hard for me because I am only two weeks into my linux/ubuntu experience  - so as plan b I went to your windows xp install option as I had a wn xp machine available on my LAN.  Fortunately the laptop has a PXE/LAN boot option in the bios so all I had to do was set this as boot in the bios.

This worked ALMOST first time.  I had some small problems - first, the netboot.tar pxelinux.0 once decompressed had a file size of zero bytes - I don't know if the problem was a corrupt netboot file on the server you specified or just a glitch decompressing.  I overcame this by manually downloading and replacing the file from the [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/) directory online.

> **Extract & Configure Ubuntu Image**
1. Download and use WinZip to extract the files from netboot.tar.gz
2. Copy the *ubuntu-installer* directory and it's contents to your TFTP directory eg C:\tftpd32\ubuntu-installer
3. Also *copy* the entire *contents* of \ubuntu-installer\i386\ directory to the TFTP directory C:\tftpd32\
[INDENT]This is duplication I realise, but for some reason you must have some or all of these files duplicated this way for the install to boot. I didn't have time to figure out which one needs to be there, so I just duplicated the lot... how lazy am I?![/INDENT]

Did all that and install progressed well for about ten seconds until I got a "kernel panic" and abort.  Looking at the TFTP32 syslog I found that the install was not finding the files in the pxelinux.cfg and the pxelinux.cfg.serial-9600 directory (possibly only the first was important, but I did the fix below on both folders just in case, following your redundancy/lazyness approach)

First, I had to put the pxelinux.cfg and the pxelinux.cfg.serial-9600 directory in the root level of the tftp directory.  Then, I had to manually edit the names of the "default" files within each of these folders to match the MAC ID of the client machine.  Apparently you can also use the IP address or the hex MAC ID.  The TFTP syslog assists here as it tells you exactly the names of the files the client is looking for and not finding so you can just copy them and manually rename the "default" file.

After this it worked like a charm - this was at around 1am so I went to bed and most of the installation was complete by the time I woke up.  It also had the bonus of allowing me to choose Xubuntu as my default desktop which was what I was hoping to get anyway.

> ... and you're done! Feel free to edit, praise, update or amend this as it was just a brain dump that I thought would help ppl as it took me all day to get working!

Cheers

:D

Great job!  I wish I had tried this before around twelve hours of pain finding and modifying dos floppies which got me nowhere!

If anyone is trying this and needs assistance let me know.

---

### Post by Big_Bob on 2007-01-22
I have DHCP/TFTP part of the install running with no problem, but I'm also trying to serve the packages from the same Windows machine running mini web server. I mount the ubuntu-6.10-alternate-i386.iso image, point the web server to it's root and boot the target PC. Install runs OK, I select location, keyboard, for archive location I enter IP of the Windows machine with the running web server and install continues by copying packages, but it fails to find libstdc++6, libsigc++2, ntpdate, vim-common and vim-tiny. I've tried several times, it's only those 5 pkgs, that the installer can't get. I've checked the exported image and the packages are of course there. Anyone having an idea what's wrong? Thanks.

---

### Post by phuturism on 2007-01-23
> **Big_Bob said:**
> I have DHCP/TFTP part of the install running with no problem, but I'm also trying to serve the packages from the same Windows machine running mini web server. I mount the ubuntu-6.10-alternate-i386.iso image, point the web server to it's root and boot the target PC. Install runs OK, I select location, keyboard, for archive location I enter IP of the Windows machine with the running web server and install continues by copying packages, but it fails to find libstdc++6, libsigc++2, ntpdate, vim-common and vim-tiny. I've tried several times, it's only those 5 pkgs, that the installer can't get. I've checked the exported image and the packages are of course there. Anyone having an idea what's wrong? Thanks.

Sounds like you are more advanced than me as I did not try an install from the ISO but rather just from the net ...  but nevertheless..

Does the tftp32 log give any indication of where the client expects the file to be found?

---

### Post by Big_Bob on 2007-01-25
In the meantime I have found an answer to my own question. Problem was, that the web server that I was trying to use on the Windows machine was not good enough. I've tried iWeb and Xitani, but only Apache was able to do the job. If anyone is interested in this kind of install, see [[COLOR="Blue"]this thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=332343"). With the help from dixonp I was able to make it.

---

### Post by haaskaa on 2007-02-01
[SIZE="4"]Worked like a charm, every step on the way!![/SIZE]

Had an old laptop with a disfunctional cd-drive and this was just what I needed.

Noticed one thing though: My router interface kept kicking me out of the web config-interface everytime I tried to stop the dhcp, so I thought I'd try it anyway WITH the dhcp running. As I rebooted my client PC, the installer automatically configured the dhcp access (or something like that, I can't remember exactly what it said). It then carried on with the normal install (specify country, language etc). I.e. no need to stop the dhcp it seems...

Anyway, thanks for a great guide. My old Packard Bell is reborn ;)

---

### Post by jojogabi on 2007-03-12
I was trying to install ubuntu on my dell c400 laptop. I have read your post and followed it and let me thank you and all for taking the time to inform us newbies. I am on my third day on this endeavour and would like to ask you for your much appreciated insights. My install comes to a halt on the client where tftp is with just ellipsis and not showing any error message or progress and on the tftpd32 sys log shows "Rcvd DHCP Discover Msg for IP 0.0.0.0, Mac 00:08:74:21:A0:DA [12/03 00:00:56.201]
DHCP: proposed address 192.168.2.4 [12/03 00:00:56.201]
Rcvd DHCP Rqst Msg for IP 0.0.0.0, Mac 00:08:74:21:A0:DA [12/03 00:00:57.143]
Previously allocated address acked [12/03 00:00:57.143]
Connection received from 192.168.2.4 on port 28995 [12/03 00:00:58.134]
Read request for file <pxelinux.0>. Mode octet [12/03 00:00:58.134]
Using local port 3406 [12/03 00:00:58.134]
<pxelinux.0>: sent 26 blks, 13156 bytes in 0 s. 0 blk resent [12/03 00:00:58.134]"

---

### Post by jojogabi on 2007-03-14
Finally I have ubuntu on my laptop installed via netboot + tftp. I know I should have exhausted everything first before posting. Anyways, when I finally get every component to work it turns out on the client side should run pxe booting instead of TFTP! sorry to bug u guys!

---

### Post by Hermelo on 2007-05-22
[QUOTE=phuturism;2050529]Scaryant - thank you so much.

I have a toshiba portege 3480CT laptop  with a USB CDROM drive that cannot be booted from the BIOS.  After lots of pain trying to install from dos floppies with modified USB CDROM drivers and files, I gave up and tried a netboot from Ubuntu - this was too hard for me because I am only two weeks into my linux/ubuntu experience  - so as plan b I went to your windows xp install option as I had a wn xp machine available on my LAN.  Fortunately the laptop has a PXE/LAN boot option in the bios so all I had to do was set this as boot in the bios.

This worked ALMOST first time.  I had some small problems - first, the netboot.tar pxelinux.0 once decompressed had a file size of zero bytes - I don't know if the problem was a corrupt netboot file on the server you specified or just a glitch decompressing.  I overcame this by manually downloading and replacing the file from the [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/) directory online.
Hi,

 I have exactly same computer (Toshiba 3480ct) and after my installation of xp crushes,
I managed (last week) to install Ubuntu in it taking the hdd, plugging  it in other computer
(in ide0), wiping and formatting the drive, installing Ubuntu, taking the hdd back to the
toshiba, wich showed me command prompt, than running 'sudo dpkg-reconfigure -phigh
xserver-org' , manually configuring the video, than it is working....

 The point is that I am feeling Ubuntu kinda slow for this computer... I managed to get
internet working using ndiswrapper, but  I am not sure if is because of my connection
restrictions (university's connection, for example torrents, radios, camera on msn doesn't 
work at all) or any error of myself, but the add/remove doesn't find any repository. Keep
giving me error... 
 
 Well anyway, is there anyway to install Kubuntu (wich I think is more apropriete to my
machine (P3 Coppermine 600Mhz, 192Mb RAM, 70Gb Hdd, but unfortunately without
floppy nor cd drive... that's why is wasn't easy to put Ubuntu -> and even worst to put
windows in it, as they don't permit hardware changes after installation.... ).

 Resuming. Is there anyway to install Kubuntu from INSIDE Ubuntu, without floppy, cd,
etc? Because I gave back the desktop I borrow in order to install Ubuntu... And is not 
nice to keep open else where's desktop ...

THanks

---

### Post by syarlett on 2007-06-29
Hi,

Is it possible to extract the contents of an Ubuntu CD into a local folder on the Windows pc, and have the PXE laptop boot up and install from this folder rather than off the internet?

Or alternatively, find a way to 'share' the CDROM on the windows pc and have the laptop instal from there?

Thanks, hope to hear from someone soon :-)

Cheers Steve

---

### Post by keldrum on 2007-12-06
Hi All,

I've just completed a netboot install of gutsy where I followed your steps (thanks again) & in addition to your instructions, I used the local repository option to get the files from an apache server running on another local ubuntu box. (much faster than web install - see: [http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/](http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/)).

To be clear, I used the pxe netboot files from the ubuntu-7.10-server-i386.iso on my tftp server (I mounted the cd & copied the files from /install/netboot/ubuntu-installer/i386/). The local repository I set up was made of the files extracted from the same ubuntu-7.10-server-i386.iso. The installation (PXE boot & all package installation) completed successfully & the system is up and running.

The problem I'm having is that the installation options during the PXE boot seem only to be desktop based (I want a server install) even though all the files are from the server ISO. ie. During the start of the PXE based install I can only choose from the "default" or "cli - minimal" install (there is no "server" option) and, having selected the "cli - minimal" option, I end up with a "generic" kernel & packages as opposed to the "server" kernel and packages, which are what I want.

Has anyone else had this problem? Is anyone aware of a way to get a server based install option from the PXE boot?

I'd appreciate any help.

Thanks,

keldrum

---

### Post by tomminger on 2008-02-12
Hi,
i was trying to install ubuntu via Netboot to my laptop (Samsung R50 without working dvd-drive and no running OS).
when running the netboot, i get the following error message:
error 10054 in system call recv An existing connection was forcíbly closed by the remote host.
can you help me with this?
cheers
Thomas

---

### Post by phuturism on 2008-03-18
> **keldrum said:**
> Hi All,

I've just completed a netboot install of gutsy where I followed your steps (thanks again) & in addition to your instructions, I used the local repository option to get the files from an apache server running on another local ubuntu box. (much faster than web install - see: [http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/](http://ubuntu-tutorials.com/2007/10/08/how-to-install-ubuntu-locally-over-the-network/)).

To be clear, I used the pxe netboot files from the ubuntu-7.10-server-i386.iso on my tftp server (I mounted the cd & copied the files from /install/netboot/ubuntu-installer/i386/). The local repository I set up was made of the files extracted from the same ubuntu-7.10-server-i386.iso. The installation (PXE boot & all package installation) completed successfully & the system is up and running.

The problem I'm having is that the installation options during the PXE boot seem only to be desktop based (I want a server install) even though all the files are from the server ISO. ie. During the start of the PXE based install I can only choose from the "default" or "cli - minimal" install (there is no "server" option) and, having selected the "cli - minimal" option, I end up with a "generic" kernel & packages as opposed to the "server" kernel and packages, which are what I want.

Has anyone else had this problem? Is anyone aware of a way to get a server based install option from the PXE boot?

I'd appreciate any help.

Thanks,

keldrum

This isn't quite what you are asking but you can use a tool called debfoster to remove all packages except those relating to a server/minimal install on the destination pc.  I actually did this on the same laptop I mentioned earlier in the thread because I wanted to run a lightweight gui which only required a server/base install to run fluxbox on top.

Here's a thread on it [http://ubuntuforums.org/showthread.php?t=442974&highlight=debfoster](http://ubuntuforums.org/showthread.php?t=442974&highlight=debfoster)

hope it helps!!!

---

### Post by lflashl on 2008-04-14
> **syarlett said:**
> Hi,

Is it possible to extract the contents of an Ubuntu CD into a local folder on the Windows pc, and have the PXE laptop boot up and install from this folder rather than off the internet?

Or alternatively, find a way to 'share' the CDROM on the windows pc and have the laptop instal from there?

Thanks, hope to hear from someone soon :-)

Cheers Steve

Did you find a simple way around this issue? im wishing to install from ISO and not NET

---

