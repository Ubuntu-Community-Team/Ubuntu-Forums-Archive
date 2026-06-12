---
title: "Samba lockup on boot"
date: 2005-04-05
forum: Installation &amp; Upgrades
---

### Post by tikkitembo on 2005-04-05
Hi,

I'm new to ubuntu and coming back to linux after a mulit-year year hiatus.  I installed Warty and everything seems to be working fine.  I did a sudo apt-get install of samba and smbfs and I'm able to browse Windows network drives.  However, after rebooting a couple of times, when I started up the last time, the system hangs when loading the SAMBA daemon.

I've blown away and reinstalled warty twice.  Everything works fine for awhile and then SAMBA will hang on boot.

Questions:

1. Is there a way in Linux to get by the SAMBA daemon and continue loading the os? (control key combo, etc.)

2. Any ideas on what could be causing this?  I know I need to provide more information so please answer no. 1 for me and I'll reboot and get my smb.conf. uploaded.

Tikki

---

### Post by p!=f on 2005-04-05
Hi and welcome on forums,

First, you do not need to reinstall whole system just because one daemon doesn't work or refuses to start. This is Microsoft approach. :)

1. You may try CTRL+C when you can see "Starting SAMBA daemons...". It should terminate its startup.
2. I've never experienced this problem with Samba but a similar one with dnsmasq. The problem was with .conf file. Could you post your /etc/samba/smb.conf here? (post it within [ code ] and [ /code ] brackets (remove spaces) so it's more readable in the thread). Did you tweak it?
3. Could you be please more descriptive about your setup?

---

### Post by tikkitembo on 2005-04-06
Hi,

Thanks for the help.  I tried Ctrl-C and it didn't help.  I'm still stuck at "* Starting Samba Daemons" Tried rebooting and ctrl-c again when it stops.

Any other suggestions?  I can't send the smb.conf yet until I can get it to reboot.

Here's the information I can give you:

Computer - Compaq DeskPro EN upgraded to a 933 MHz Intel CPU with 512MB RAM and a Western Digital WD4000 7200 RPM 40GB hard drive.  It has built in video and I'm using a KDS 15 inch LCD display at 1024x768.  The printer is an Epson Stylus Color 670 and Warty auto-detected the printer and I installed the driver.  It's only setup for local printing for now.  After installing the Warty OS with default settings, I installed the printer driver and installed Samba using:

sudo apt-get install samba
sudo apt-get install smbfs

After running these two commands, I go into the "Computer" "System Configuration" and "Network" and changed the workgroup to "atl".  I'm able to see Windows servers after this.

After this I installed the Mozilla Flash plugin.  I tried rebooting and I hang on "* Starting Samba Daemon" every time now.

If you can just get me to where I can boot, I'll send my smb.conf file for review.  Also, the computer is hooked to the network via wired ethernet 100mbit through a Linksys WRT54G with WEP enabled. (however the ubuntu machine is not using wireless)

Thanks again for all of the help.

Tikki

---

### Post by tikkitembo on 2005-04-08
Hi,

Does anyone have suggestions for me on how to get out of this hang?  I may go to LinSpire 5 to see if it makes a difference.

Thanks for any help,

Powell

---

### Post by p!=f on 2005-04-08
I'm sorry but I don't have anything useful in my mind right now. :| I've never experienced Samba lockups during boot so I can't share any experience with you. :(
Try to google for samba lockups. Maybe you dig something useful.
Anyone who has some experience with this issue is welcome to help. :)

Edit: The only thing which hits my mind is that wireless card. Maybe Samba is set up to listen on this interface but it's actually not initialize during boot (?) Posting smb.conf and dmesg here would be much of help.

---

