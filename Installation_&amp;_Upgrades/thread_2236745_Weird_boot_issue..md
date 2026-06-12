---
title: "Weird boot issue."
date: 2014-07-28
forum: Installation &amp; Upgrades
---

### Post by warren3 on 2014-07-28
Hi.

I wacked an old sata 2.5" HD in my base unit today and installed Ubuntu 14.04 LTS 64 bit edition.  Install seemed to go fine but everytime I boot I get this screen (see attached screen shot).

It just cycles round and round and then through the text the Ubuntu load screen flickers every couple of seconds.  If I press return I get to the login screen and everything seems ok from there.

My system is
Phenom 965
[COLOR=#333333][FONT=Arial]M5A97 EVO R2.0 MOBO[/FONT][/COLOR]

6670 passive graphics card
4gb ram

I also have  couple of other hard drives in my case that I disconnected when I was installing Ubuntu.  I was going to connect these up again but I am not so sure.  I may just run Ubuntu in a Virtual Box.

Cheers.

---

### Post by moore.bryan on 2014-07-29
Could you post your /etc/default/grub? I think it that may be the culprit...

---

### Post by warren3 on 2014-07-29
Hi Bryan.

Well I connected my HD back up (I disconnected it) that I installed Ubuntu on and it will no it boot.  It just says 'Please reboot and select proper boot media' or some such error.

When I go into bois and look at the boot options I see my drive and its called 'Ubuntu' and it has 'UEFI' logo over it.  I also see my drive again as a separate boot option but it just states the model number . 

Cheers.

---

### Post by Bucky Ball on 2014-07-29
Do you have any other drives in the machine or is this it? If there are others, are there operating systems on them? Did you have Windows installed anywhere? On any drive?

I generally completely wipe any old drives I install to. Odd things can sometimes crop up otherwise, usually to do with leftover boot bits.

Boot Repair may help, but hard to know as it is impossible to read what is on your scrolling screen so that gives no clue.

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

* Please attach large pics using the paperclip icon in the 'Go Advanced' or 'Adv Reply' window. I have edited your first post accordingly. Thanks. ;)

---

### Post by moore.bryan on 2014-07-29
I've had issues with UEFI in the past, but not recently. You *can* login though, right; you just need to hit "Enter" to get the prompt?

Could you post your entire /etc/default/grub file?

---

### Post by warren3 on 2014-07-29
> **Bucky Ball said:**
> Do you have any other drives in the machine or is this it? If there are others, are there operating systems on them? Did you have Windows installed anywhere? On any drive?

I generally completely wipe any old drives I install to. Odd things can sometimes crop up otherwise, usually to do with leftover boot bits.

Boot Repair may help, but hard to know as it is impossible to read what is on your scrolling screen so that gives no clue.

Get Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair](https://help.ubuntu.com/community/Boot-Repair#Getting_Boot-Repair)

* Please attach large pics using the paperclip icon in the 'Go Advanced' or 'Adv Reply' window. I have edited your first post accordingly. Thanks. ;)

Hi.  

My base unit has a 128GB SSD with Win7 pro on it and a 500gb hard drive just for FLAC's.  I disconnected both of these prior to installing Ubuntu on my 2.5"HD.  I did this as I was scared of screwing up my Win installation on my SSD.

To tell a lie I did connect my 2.5" HD with the SSD and 500GB HD attached, this was to delete the partition using Windows disk management utility.  I did not format the 2.5" HD at all, I just deleted the volume to show it showed unallocated space for the Ubuntu installation procedure. A few minutes after this process I did get a BSOD and I had to reset my PC.  When I rebooted into Windows my 2.5" HD was no longer seen.  I changed the molex connector for the 2.5" HD and went to install Ubuntu on the HD it was seen again.  This 2.5" HD is very old - it came with a 2007 Dell laptop - so maybe the HD is not the best and could be failing?

I am really unsure what to do TBH.  I have a online course on Linux starting this Friday and this Ubuntu procedure seems a little nightmarish to be.  I thought it would be easy.  I am really unsure about UEFI and secure boot installation.  Secure boot is on within my BIOS but I only have Windows 7 not 8, so should I disable secure boot for the Ubuntu install?

I don't want to mess up my Windows 7 install.  I have been thinking about partitioning my 500GB hard drive instead and putting Ubuntu on a 30GB partition and leaving all my drives connected so Ubuntu can see what HD's I have connected.  I am just worried that something could go wrong.  I am in two minds about whether just to buy a Celeron NUC for £100 and put Ubuntu on that and forget about trying to add this hard drive to my base unit.

> **moore.bryan said:**
> I've had issues with UEFI in the past, but not recently. You *can* login though, right; you just need to hit "Enter" to get the prompt?

Could you post your entire /etc/default/grub file?

I cannot login anymore.  I could yesterday but I have since disconnected and reconnectred the drive in question and I just get "[COLOR=#070F14][FONT=Verdana]Reboot and select proper boot device or insert boot media in selected boot device and press a key".[/FONT][/COLOR]
Cheers.

---

### Post by warren3 on 2014-07-30
HI.

Just a quick update.

I disabled fastboot and secureboot and the HD booted into Ubuntu.  Anyway I decided to install Ubuntu again using 'legacy' and not 'UEFI'.  It seems to be doing the same thing again although the first couple of boots seemed ok.

Here is my Grub file

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

Thanks.

---

### Post by warren3 on 2014-07-30
I also tried boot repair.  I now have GRUB when I boot from the HD, but after that I still get the screen issue in my original post.

Here is my URL

[URL="http://paste.ubuntu.com/7908442/"]http://paste.ubuntu.com/7908442/
[/URL]

---

