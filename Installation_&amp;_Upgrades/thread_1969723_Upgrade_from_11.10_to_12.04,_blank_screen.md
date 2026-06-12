---
title: "Upgrade from 11.10 to 12.04, blank screen"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by silverbullet007 on 2012-04-30
Hardware: HP generic minitower, Athlon II X2 215, 2gb DDR3, SATA2 hdd, Nvidia MCP61 chipset, ATI radeon HD 5700

Ran 11.10 perfect.. I mean totally perfect.

Upgraded to 12.04, process was long but painless..long because I'm up in BFE Michigan.

First reboot presented me with a black screen with > stopping system v runlevel compatibilityGoogled and followed instruction here: [http://askubuntu.com/questions/125428/grub-complains-of-no-such-partition-after-installing-1204]("http://askubuntu.com/questions/125428/grub-complains-of-no-such-partition-after-installing-1204")

Rebooted and got a grub error prompt.  Generated a pastebin here: [http://paste.ubuntu.com/957845/]("http://paste.ubuntu.com/957845/")  

I *believe* my issue is video related.. however with an Nvidia chipset and an ATI video card my belief could be wrong.

Thanks!

---

### Post by oldfred on 2012-04-30
Boot report looks normal, I agree that it probably is video related or possibly other boot parameters. 
Can you turn off one or the other video?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Is this considered an Optimus video system that supposedly lets you switch? There have been issues with Optimus systems.

---

### Post by silverbullet007 on 2012-04-30
Ok I booted off a live CD, altered the /etc/default/grub file to add the *nomodeset* to the GRUB_CMDLINE_LINUX line however rebooting results in a *missing operating system* message.


I resolved that with help from here: [http://askubuntu.com/questions/78758/unable-to-boot-missing-operating-system]("http://askubuntu.com/questions/78758/unable-to-boot-missing-operating-system")

Now I get a grub menu, but im back to the > Stopping system v runlevel compatiability...ok then hangs.

---

### Post by silverbullet007 on 2012-04-30
I just logged in via Alt ctrl f1 command line, rechecked the /etc/default/grub file and nomodeset was gone.  Put it back into the file and rebooted.  However now I dont get the text prior to the hang..

---

### Post by silverbullet007 on 2012-04-30
I dont believe it's Optimus.. the onboard if Nvidia based while the PCIe card is ATI.  The BIOS is set for PCI-E as Primary Video.  there is no available option to disable the onboard.  I wonder about possible removing all ATI software?

---

### Post by ravisghosh on 2012-04-30
Even I am stuck with a black screen upon upgrade from 11.10 to 12.04. I can get to shell using recovery, but cant get X working.

**Install:** Install was not easy. I was unable to upgrade as I was getting the error message "E:Couldn't configure pre-depend libtinfo5 for libncurses5, probably a dependency cycle."

Followed instructions on [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/924079](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/924079)

and installed apt first by:
> sed 's/oneiric/precise/g' -i /etc/apt/sources.list
apt-get update
apt-get install apt python-apt
sed 's/precise/oneiric/g' -i /etc/apt/sources.list
do-release-upgrade

**Problem:** Upon reboot, the screen would blink for a moment, go complete black like switched off, and then it would seem like it is on but would be black.

**Solutions I Tried:** I searched the web and found some solutions though none of them worked for me. Here are the solutions that didn't work so far:
**1. **Go to BIOS>Security>I/O Interface Security/New Interface Card and set it to locked.

I didn't find anything like I/O Interface Security at all.

**2. **Add "nomodeset" to kernel command line and boot.

Didn't work, getting same black screen.

**3. **Add "radeon.modeset=0" to kernel command line and boot.

Didn't work, getting same black screen.

**4. ** Somewhere it was mentioned that boot with kernel 3.0.0.14 would work.

Didn't work, getting same black screen.

**5. ** When I logged into recovery and ran aptitude to check if there were any packages uninstalled, I found that there were lot of errors related to dependency and it asked me to remove some 150 packages which I did.

Didn't work, getting same black screen.

**System Config:** Dell Studio 1555 - 2.4 Ghz processor, 320 GB HD, 4 GB RAM, ATI Radeon HD 4570 graphics card.

Any help would be sincerely appreciated.

---

### Post by oldfred on 2012-04-30
You cannot just add nomodeset to the grub file in your install unless you run sudo update-grub from within your install to rewrite grub.cfg. 

You just need to add it to your boot stanza as you boot. Only if you need it permanently after you boot into your install can you add it to grub & then update.

On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by silverbullet007 on 2012-05-01
Ahh roger that, I've got you now.

Ok so hitting E i removed splash and quiet replacing them with nomodeset and hitting Ctrl X booted.  This time the purple *background* flashed twice then back to text but showing much more than usual.

I see normal boot lines such as:
> Starting AppArmor
Starting PBIS Services
Starting CPU interrupt balancing deamon
etc

Then after another 16 or so "Starting" lines I see:

> /etc/rc2.d/S201likewise: 36: .: Can't open /usr/libexec/like-wise/likewise-open/init-likewise.sh speech-dispatcher disabled; edit /etc/default/speech-dispatcher saned disabled; edit /etc/default/saned

Then Starting Apache2...
> Checking battery state
Stopping cold plug devices
Stopping log initial device creation
Starting load fallback graphics devices
Starting GNOME display manager
Starting LIghtDM Display manager
Starting userspace bootsplash
Stopping system V runlevel compatibility
Stopping GNOME display manager
Stopping userspace bootsplash

then halts.

Do you think i need to Nvidia drivers.. even though I'm using the ATI card?  Or should I maybe remove the ATI?

---

### Post by oldfred on 2012-05-01
No, drivers are proprietary to each vendor. I think it is fglrx for ATI, but I am not sure. The generic drivers are supposed to let you at least boot to a system, but may not be optimal.

Without quiet & splash you see the entire boot process, that is copied into a log file every time you boot, in case you need to review it after you boot.

It looks like it is just the gui not loading, you should be able to use recovery mode and get to a menu of several choices. It will offer to run updates which may be worth doing and you also should be able to get to a command line.

I think some of the previous links have detail info on ATI cards, I only know the nVidia suggestions.

---

### Post by silverbullet007 on 2012-05-01
Ahh thanks fred.

Ok so starting in recovery-mode I try the dpkg option, which asks if I want to upgrade 52MB worth of stuff.. I agree to.  Upgrades include gnome games, gnomine, sudoku, samba-common, smbclient, xserver-common and xserver-core.

Updated them all, said they completed successfully.  tried booting into failsafeX, same > no screens found error.  Ran dpkg once more, found zero updates.  tried the normal boot and displayed 
>  swapon failed: device or resource busy
mountall: swapon terminated with status 255
mountall: problem activating swap
initctl: event failed
skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
": usr.sbin.rsyslogd
Starting web server apache2 ok
Checking battery state ok
halted..

---

### Post by silverbullet007 on 2012-05-01
I will try removing the ATI card and using onboard video.

---

### Post by silverbullet007 on 2012-05-01
Removed ATI FirePro card, set the BIOS to use onboard video and now booting normally, or holding shift for grub... apparently the onboard video adapter puts out a mode that my 22" LCD doesn't support.  Go figure.

Hit down, and Enter as if I could see the display.  Got the recovery-mode menu, checking dpkg for updates.. none available. Tried failsafeX, and got a gui asking me to choose between a few options (im sure you know what they are) then my keyboard/mouse input suddenly died.  So I can't choose an option.  Rebooting to try again.

---

### Post by silverbullet007 on 2012-05-01
No dice.. each time i try failsafeX I get the screen asking to choose between run in low-graphics for one session, reconfigure the graphics, troubleshoot the error or exit to console.  No keyboard or mouse inputs available.

---

### Post by oldfred on 2012-05-01
I have had grub2 not recognize keyboard & mouse unless I used ps/2 ports. Then I found there was a setting in BIOS to enable USB mouse & keyboard. It seems both Windows & Ubuntu used their own drivers but grub did not.

There may be other BIOS settings you should change?

---

### Post by silverbullet007 on 2012-05-01
You know I just got fed up with trying to figure this out.. formatted and did a fresh install of 12.04.  Didn't really have much in the way of data on there.  Should I mark as solved or something else?

FWIW: there was no BIOS setting related to USB or PS/2 input devices.  multiple keyboards and mice didn't make a difference.

---

### Post by silverbullet007 on 2012-05-02
Oh damn near forgot.. Thanks for all your help Fred.  I think out of all the times ever needing the forums here you have been the nicest and most willing to lend a virtual hand.

---

### Post by oldfred on 2012-05-02
Is keyboard still an issue? I was reviewing notes and BIOS setting for fast boot was reported by one user as a keyboard issue. Not sure how.

---

### Post by samfraser on 2012-05-04
Hi, I've got the same problem, worked perfectly in 11.04 with my ASUS Eee PC Seashell netbook.

After upgrade I now have a blank desktop with some files I'd left on there, I get get to the shell but gnome has not loaded, looks like a default X session...

Reading through this post a lot of options have been tried without much avail, am I best to just go for a fresh install via usb?

Very disappointing!:(

---

### Post by caffeineme on 2012-05-07
Same thing is happening to me, running Ubuntu Server 12.04 without ANY gui. I suspect it is somehow tied to Samba, as the OS seems fine until I start adding Samba and configuring it. After that, reboot, and presented with NO login prompt and a blank screen. 

Using the motherboard's onboard video, and no GUI, so video drivers shouldn't be an issue. 

Posting this on 5/7/12, downloaded a new ISO on 5/6 (AMD 64 bit) in the hopes that maybe a new ISO had been provided/patched. No love. 

Hoping there's a fix in the works. I'm fearing that a lot of the config that I've done on a new server will be going to waste. :(

---

### Post by oldfred on 2012-05-08
@samfraser
Did you go thru the links in post #2 as it sounds like the typical video issue. I have always had to use nomodeset until I get the nVidia drivers installed. May be best to start your own thread so all who have some idea on video issues can contribute, best to include specs & video card model.

@caffeineme
Do not know server. Since you have only one system can you hold shift and get grub menu, so you can try recovery mode. On desktop you select whether you want login or not during install and there are gui settings for changing, but I have not tried from command line.

---

### Post by caffeineme on 2012-05-08
Thanks. I tried the holding SHIFT at boot, ineffective. I get all the normal POST messages and pre-boot....as soon as it goes to GRUB, I get a blank screen...with the monitor displaying "Can't display this video mode" or similar. So, I don't know that GRUB ever has a chance to start. The OS just dies after the system's initial bootup. 

I'm going to wait a few days, see if a new ISO is released that MAY contain a fix, and will rebuild using that. This is my 2nd time building this system, my RAID array is safe, so I haven't suffered any data loss, just time spent, but I'm learning as I go.

---

### Post by oldfred on 2012-05-08
You may then need this:

vga=xxx is a deprecated boot option
Use this with your monitor size in 
sudo nano /etc/default/grub
GRUB_GFXMODE=640x480

Then:
sudo update-grub

---

