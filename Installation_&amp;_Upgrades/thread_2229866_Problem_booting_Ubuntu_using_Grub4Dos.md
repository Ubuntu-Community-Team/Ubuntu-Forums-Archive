---
title: "Problem booting Ubuntu using Grub4Dos"
date: 2014-06-15
forum: Installation &amp; Upgrades
---

### Post by Al1000 on 2014-06-15
Hi,

Initially I had XP installed on the hard drive on the primary partition on my desktop pc, then I installed Lucid Puppy 5.2.8.6 on sda5 and used Grub4Dos for dual boot, and everything worked fine.

This evening I installed Ubuntu 12.04 on sda7 (and created a swap area on sda6 using the Ubuntu CD). The Ubuntu installer found XP no problem, but not Puppy (which I guess might be because it's a frugal installation). When I restarted the computer only Ubuntu and XP were available on the boot menu, but it booted into either without any problems.

So I deleted the existing Grub4Dos files, then booted up into the Puppy installation by booting from the Puppy CD, and ran Grub4Dos again. Now I have a boot menu with all three operating systems on it, but while it boots into either Puppy or XP, it won't boot into Ubuntu. When I select Ubuntu from the menu, a bunch of text scrolls down the screen far too fast for me to read, then when it stops a couple of seconds later, there is a flashing ''_'' (without the quotes) which looks like it's inviting me to type something, but nothing happens when I press buttons on the keyboard and the only way out I have found is to press the reset button on the computer. At this point, the line of text at the top of the screen, which is the first line that remains visible after the text scrolls down the screen, reads:

> [  0.749218] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

... in case that gives anyone a clue as to what's going on.

The Grub4Dos menu.lst file is:

                              >     [LEFT]# menu.lst produced by grub4dosconfig-v1.9.1
[/LEFT]
    [LEFT]color white/blue black/cyan white/black cyan/black[/LEFT]
    [LEFT]#splashimage=/splash.xpm[/LEFT]
    [LEFT]timeout 10[/LEFT]
    [LEFT]default 0

[/LEFT]
        [LEFT]# Frugal installed Puppy

[/LEFT]
        [LEFT]title Lupu 528 (sda5/puppy528)[/LEFT]
    [LEFT]  uuid 7b0f742b-518a-4061-bf29-362260602351[/LEFT]
    [LEFT]  kernel /puppy528/vmlinuz   psubdir=puppy528 pmedia=atahd pfix=fsck[/LEFT]
    [LEFT]  initrd /puppy528/initrd.gz

[/LEFT]
        [LEFT]                                   [LEFT]# Full installed Linux

[/LEFT]
        [LEFT]title Ubuntu 12.04.4 LTS (sda7)[/LEFT]
    [LEFT] uuid fa0ae3f4-4462-4bd3-98c4-e12b127f94b2
[/LEFT]
    [LEFT] kernel /vmlinuz root=/dev/sda7 ro
[/LEFT]
    
[/LEFT]
        [LEFT]# Windows
[/LEFT]
    [LEFT]# this entry searches Windows on the HDD and boot it up[/LEFT]
    [LEFT]title Windows\nBoot up Windows if installed[/LEFT]
    [LEFT]  errorcheck off[/LEFT]
    [LEFT]  find --set-root --ignore-floppies --ignore-cd  /bootmgr[/LEFT]
    [LEFT]  chainloader /bootmgr[/LEFT]
    [LEFT]  find --set-root --ignore-floppies --ignore-cd  /ntldr[/LEFT]
    [LEFT]  chainloader /ntldr[/LEFT]
    [LEFT]  find --set-root --ignore-floppies --ignore-cd   /io.sys[/LEFT]
    [LEFT]  chainloader /io.sys[/LEFT]
    [LEFT]  errorcheck on

[/LEFT]
        [LEFT]# Advanced Menu[/LEFT]
    [LEFT]title Advanced menu
[/LEFT]
    [LEFT]  configfile /menu-advanced.lst[/LEFT]
    [LEFT]  commandline[/LEFT]
    

I am relatively new to Linux. I had Ubuntu installed for a month or so as a dual boot with XP, before I discovered the hard drive was beginning to fail. I have also tried Mint 16 and Linux Lite 2.0 although only briefly, one after the other, and also both as dual boot systems with XP. I have been using Puppy for a couple of months on my laptop as a ''live'' operating system with a savefile on USB, but only installed it on my desktop pc the other day which was the first time I used Grub4Dos. I intend to mess around with Puppy and perhaps add additional frugal installations on sda5, so sticking with Grub4Dos for booting seems like the best option I am aware of.

If only I could get Ubuntu to boot from it. I haven't a clue why it won't, so any advice would be much appreciated.

---

### Post by grahammechanical on 2014-06-15
I know nothing about Grub4 Dos and it is a few years since Ubuntu/Grub used menu.lst and I messed around with it. Ubuntu now uses Grub 2.02 which does not use menu.lst any more. I do not see any reference to where the boot loader can find the Linux kernel.

Grub 2.02 looks for something like this.

> linux	/boot/vmlinuz-3.15.0-6-generic root=UUID=5decfcfc-cb12-4294-bebd-4f70c129258c ro  quiet splash $vt_handoff
initrd	/boot/initrd.img-3.15.0-6-generic


The kernel (vmlinuz-3.15.0-generic) is in /boot. Your menu.lst only points to sda7 as root but it does not direct the bootloader to where the kernel is in a Ubuntu installation.

That is the best that I can offer.

Regards.

---

### Post by Al1000 on 2014-06-15
Thanks for the information and I see what you mean. I read the instructions for Grub4Dos and found that they say:

> There is a trap in booting up full installed Puppy and/or other Linux OS. You need to specify the partition of the Linux kernel('vmlinuz') and the position of the root file system. The previous is direction to the Grub4Dos at the bootup process and the latter is direction to the Linux kernel. 

I ran Grub4Dos again after deleting the existing Grub4Dos files, and noticed that in the ''options'' box for the Puppy installation, it says: pmedia=atahd pfix=fsck

Whereas in the options box for the Ubuntu installation it just say: ro

I have also found I can boot into Ubuntu by selecting ''Find Grub2'' from the ''Advanced menu'' in the Grub4Dos boot menu, but of course that doesn't solve the original problem.

---

### Post by yancek on 2014-06-15
There are three example entries for a menu.lst file using Grub Legacy which should boot your Ubuntu.  I use all of them to boot different systems using Grub2.  They all boot.  You need to either chainload pointing to the correct partition or to the core.img file specifically,  it is usually in /boot/grub but on 14.04 and newer Ubuntu derivatives it is in /boot/grub/i386-pc directory. 

```
title Ubuntu-12.04-sda7
root (hd0,6)
kernel /boot/grub/core.img
#savedefault
####boot

title Mint Cinnamon
root (hd0,6)
kernel /boot/grub/core.img

title Peppermint Three-sda7
root (hd0,6)
chianloader +1
```

---

### Post by Al1000 on 2014-06-16
I deleted:

> [LEFT]title Ubuntu 12.04.4 LTS (sda7)
[/LEFT]
    [LEFT] uuid fa0ae3f4-4462-4bd3-98c4-e12b127f94b2
[/LEFT]
     kernel /vmlinuz root=/dev/sda7 ro

... and pasted:

> 
title Ubuntu-12.04-sda7 
root (hd0,6) 
kernel /boot/grub/core.img 
#savedefault 
####boot

..into menu.lst. It doesn't boot straight into Ubuntu when I select Ubuntu from the Grub4Dos boot menu, but it switches straight to the Grub2 boot menu and I can boot into Ubuntu from there. I suppose this is probably preferable, as it also gives me access to the other items in the Grub2 menu.

Many thainks for your help!

---

### Post by mörgæs on 2014-06-16
Please use Thread Tools for marking a thread 'solved'.

---

### Post by yancek on 2014-06-16
The examples I posted including the one you used basically chainload to the bootloader on that partition.  The entry you selected will boot a system with Grub2 if if has the core.img in the /boot/grub file.  The newest release of Ubuntu has it in the i386.pc sub-directory of /boot/grub so that change would need to be made in that case.  The chainloader entry would work the same for any system which has its bootloader on the root partition, whether it uses Grub Legacy, Grub2 or a windows system.

FYI, the last 2 lines in the entry are commented out.  They are not used and you could delete them if you want.

---

### Post by Al1000 on 2014-06-16
> **yancek said:**
> The examples I posted including the one you used basically chainload to the bootloader on that partition.  The entry you selected will boot a system with Grub2 if if has the core.img in the /boot/grub file.  The newest release of Ubuntu has it in the i386.pc sub-directory of /boot/grub so that change would need to be made in that case.  The chainloader entry would work the same for any system which has its bootloader on the root partition, whether it uses Grub Legacy, Grub2 or a windows system.

That's handy to know in case I decide to delete Ubuntu and install another Linux operating system on the same partition.

> FYI, the last 2 lines in the entry are commented out.  They are not used and you could delete them if you want.

Thanks, now that you mention that I recall commenting stuff out in Conky's configuration file that I didn't want it to display.

---

### Post by yancek on 2014-06-16
I've used the entry I posted that you indicate you are using to test different Ubuntu installs as well as Ubuntu derivatives.  Haven't had any problems booting them and haven't needed to change the menu.lst entry for any. Ubuntu-14.04 was different as the core.img file has moved down a directory to the i386-pc.  With a straight chainloader entry, one would not have to worry about that.

---

