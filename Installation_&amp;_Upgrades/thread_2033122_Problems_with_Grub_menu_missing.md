---
title: "Problems with Grub menu missing"
date: 2012-07-25
forum: Installation &amp; Upgrades
---

### Post by Cathhsmom on 2012-07-25
I updated my husbands computer from 10.04 to 12.10 which has Windows Vista also installed.  It boots directly into Ubuntu without presenting the grub menu with Vista as a choice.  When I press the shift key after powering up, it just shows grub loading, but fails to show grub menu.  

What I have done is do 'sudo update-grub'  with no luck, 'boot repair' with no luck ( I am not sure what that program does.  

I am dangerous and brave because I lack total knowledge on fixing Ubuntu, but I am good at googleling.   I tried editing /etc/defautl/grub to change Hidden settings to >=1, then I save file to replace.   But looking at the file, the file is blank.  I do not know what happened to file.  

Vista is still on the computer, but I cannot boot into it.  

Please help me, pretty please.
Cindy

---

### Post by oldfred on 2012-07-25
If you have Boot-Repair, run the BootInfo and  post the link it creates to the long report on your system.

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by Cathhsmom on 2012-07-25
Below is the bootinfo:
[http://paste.ubuntu.com/1110496/](http://paste.ubuntu.com/1110496/)

---

### Post by oldfred on 2012-07-25
That is a new one. 

Script looks normal except you are missing /etc/default/grub.

You may just be able to copy one into your /etc/default or else you will have to uninstall grub2 & totally reinstall it.

gksudo gedit /etc/default/grub
Add text below, then run :
sudo update-grub

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
GRUB_DISABLE_OS_PROBER=false

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

```If that does not work:
If you can boot you do not have to chroot, but can skip the chroot step. This may be better if you also have other problems with grub2.

drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by Cathhsmom on 2012-07-25
I copied the text into my /etc/default/grub and there was no change in the results.  I followed the instructions on the purge and install.  I rebooted and the screen came with grub> .  How do I get out this jam?  Do I reinstall Ubuntu? 

I am very grateful for your help.

---

### Post by drs305 on 2012-07-25
You can install Boot Repair from the LiveCD just as you did previously from a running Ubuntu. 

After installing, run the Recommended Repair and hopefully BR will fix things for you. If not, run the info script and post the contents or link.

A Boot Repair link is in my signature line if you need one.

---

### Post by darkod on 2012-07-25
In the boot info results you were also missing /grub/core.img on sda5 but that should have been reinstalled when you purged and reinstalled grub.
When reinstalling, are you specifying that you have sda5 as separate /boot partition or not? That is important.

Can you post the new bootinfo link after you purged and reinstalled? We need to see how it looks like now.

---

### Post by drs305 on 2012-07-25
*darkod* brings up something that is important for running the Boot Repair fix as well. If you have a separate boot I believe you need to go into the Advanced tab and indicate that before running the repair.

---

### Post by Cathhsmom on 2012-07-25
Here is what I have after purge and reinstall:  [http://paste.ubuntu.com/1110904/](http://paste.ubuntu.com/1110904/)

---

### Post by darkod on 2012-07-25
Did you reinstall ubuntu? The fstab now says that sda7 was the root and sda6 was the /home during install. This was different in the previous results.

In general, it looks good now. It still doesn't work?

Just in case, to make sure gurb2 is correct on the MBR, you can boot into live mode with the 12.04 cd and in terminal try:
```
sudo mount /dev/sda7 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Restart and see if that helped.

There are remains of grub files on sda6 but otherwise your latest results looked good to me.

---

### Post by Cathhsmom on 2012-07-25
Hey Darkod,

You are right, I did a complete reinstall, and I manually setup a home directory, a swap and root directory.   But I did do the sudo commands that you gave me and then I rebooted, followed by boot repair for the report.  Here is the info:
[http://paste.ubuntu.com/1110965/](http://paste.ubuntu.com/1110965/) 

If I have not said it before, I am able to boot into Ubuntu directly, but I do not get the grub listing that shows my husband's Vista system.

Off subject: I dislike windows; in fact, I have only Ubuntu on my computer.  My husband would ditch windows if he could do Turbo tax on Ubuntu.   He uses Windows once a year.

---

### Post by drs305 on 2012-07-25
I'm not sure what is going on with your Ubuntu system, but you still have a /grub folder on sda6 (/home). Both the grub menu on sda6 (which should not be used) and on sda7 contain entries for Windows.

When Ubuntu boots, do you see a Grub menu? 
If not, does holding down the SHIFT key reveal it? 
If it does, is there a Windows entry then?

You can try making sure Grub is using only sda7's files, although it appears it already is. From a normally booted Ubuntu, run:
```
sudo grub-install /dev/sda7
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
The first command will ensure Grub looks at sda7.
The second command will generate a new grub.cfg file, specifically targeting the output to /boot/grub/grub.cfg
While running the second command see if the terminal output includes finding Windows.

---

### Post by darkod on 2012-07-25
I guess not formatting sda6 could have left the /grub folder there. But even with that, the boot process seems correct, and vista is included in grub.cfg. It should work as it is.

I don't have any more ideas right now.

---

