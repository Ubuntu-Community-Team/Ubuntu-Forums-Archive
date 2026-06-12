---
title: "No Grub after installation"
date: 2011-06-20
forum: Installation &amp; Upgrades
---

### Post by pdiefend on 2011-06-20
Hello,

I have been working on a small embedded computer for a side project at my university and I have been having nothing but trouble since I started work.  Originally the system had Debian 3 on it and I was trying to install XUbuntu onto the system for others who were less familiar with Linux.  I replaced the hard drive before starting so I still have the original installation and all of the hardware is good.  Originally I tried to install XUbuntu onto the system using a live CD, but after that refused to start I fell back to the alternate install CD which worked.  The installation was a success, but then when I tried to start the computer, I would get passed the BIOS and I would get a blinking cursor, then the XUbuntu splash screen, then nothing and the system would halt.

Now for the weird part...

I tried to reinstall using the alternate install CD again, and instead of using the entire drive it re sized the partitions and installed a second instance of XUbuntu, but this time when I tried to boot the computer GRUB popped up after the BIOS screen and both instances of XUbuntu were there.  Aside from having two installations, They both only used a small partition (only ~500 MB).  Right now it works but I would rather get this working the right way if possible.  If anyone has any idea about what could be happening and how to fix this it would be much appreciated.  Thank you.

Also I tried this again and got the same results so it is a repeatable error.

Computer Specs:
Intel Pentium 5-M
512 MB RAM
(Additional information about the system is available if you need it)

Thanks again for reading through and any thoughts you may have.

Phil D

---

### Post by oldfred on 2011-06-20
Welcome to the forums.

I am not as familiar with Xubuntu. But the default installer normally sees any other installs and shrinks them to fit a new install in. If you want to reinstall over the top of an existing install you have to use manual install and choose / (root) and it finds swap normally if it exists.

How large is hard drive? With 512MB you should set swap at 1GB. 

Can you boot CD or USB to run liveCD? Alternate installer is not a liveCD.  If so run the boot info script or you should be able to run it from you Xubuntu install:

Your first install may just have needed grub2's boot loader reinstalled to the MBR, or had some parameter added to the grub command line to adjust for special hardware.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by pdiefend on 2011-06-20
Alright so I think I may have left out some information from my first post.  The Hard drive is 30 GB and is from a laptop, the swap space is setup properly and I am unable to boot from a live CD.  Because of this I believe the problem is in X or with a problem in the graphics.  I did get the same results as the first installation after I got GRUB working the second time (Meaning there was a cursor, brief splash screen then halt).  Although when I selected recovery mode in grub and selected fail safe graphics mode everything worked fine.

So right now what I need is a way to get GRUB to pop up so I can select recovery mode and fix the graphics setup after a first installation.  I am almost sure that Grub is popping up but the timeout is too short or it is not popping up but still working since I can get the splash screen.

So oldfred, you mentioned that I may need to reinstall GRUB2's boot loader to the master boot record which was probably what was happening when I inadvertently installed XUbuntu a second time.  I cannot use the Live CD or USB for this and I believe the problem that I am having now (with the graphics display or other) and the problem with the boot loader may be symptoms of the same overall error.

Thanks for your quick response and I hope that this additional info helps.  For now I will go through the links you posted and see if I can make any progress.

---

### Post by oldfred on 2011-06-20
With grub2 you are supposed to be able to get to the menu if you hold the shift key down from BIOS until menu appears. Old grub used escape key.

If you get grub> or grub rescue you should be able to manually boot:

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)
Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)
HOWTO: Boot & Install Ubuntu from the Grub Rescue Prompt 
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)


Manual boot:
grub rescue:
ls # Do you see (hd0), (hd0,1) ? If so, run the next command. If you see (hd0,5), use that instead of (hd0,1) in the next command.
configfile (hd0,1)/boot/grub/grub.cfg

Adjust drive, partition to your install:
sh:grub>ls
#If on (hd1,1) or sdb1
sh:grub>ls (hd1,1)/
#Should show the links vmlinuz & initrd.img
sh:grub>linux (hd1,1)/vmlinuz root=/dev/sdb1
sh:grub>initrd (hd1,1)/initrd.img
sh:grub>boot

---

### Post by pdiefend on 2011-06-21
Oldfred,

I tried what you said and I was able to get to the Grub menu which confirmed my suspicion that it was working, and I tried to use the methods listed above but none of them worked.  I even tried to use the recovery mode and the failsafeX option.  I was able to get a root terminal but no matter what I tried I could not get X manager to start.  At this point it has to be X that's not working, so the problem is not with booting the computer up but rather with X not properly working.

---

### Post by oldfred on 2011-06-21
What video card? I have nVidia and have to add nomodeset. Some others also use that same setting.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

---

### Post by pdiefend on 2011-06-22
None of this worked.  I have the system set up now where it doesn't start Xsession and boots directly to the terminal, and everything there works fine.  At this point the problem is definitely with Xsession.  The graphics card in the system is an embedded one and according to the documentation I have on the system says that it would work with intel i810 and vesa drivers.  Do you think that this problem can be fixed and I should keep going or should I try something else, such as a different OS?

---

### Post by oldfred on 2011-06-22
I do not have i915, but 945 on my portable but that just works for it.

Did these settings not work?

if you've got an i8xx Intel chipset, then the usual fix is to either add i915.modeset=1 or i915.modeset=0 to your boot
Other workarounds:
[https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

#To see video:
sudo lshw | grep -A 11 display
#Reconfigure graphics
sudo dpkg-reconfigure -phigh xserver-xorg
startx
#or now preferred restart gdm, I have seen all of these as preferred commands, but do not know if one is better or not.
sudo service gdm start
sudo /etc/init.d/gdm restart
sudo start gdm

---

### Post by pdiefend on 2011-06-22
None of the settings worked for me.  I have included the log files and some other relevant files in the attachment if your curious to see what is going on.  The main thing is after changing to the vesa driver for graphics, the system reports no valid modes and that screens were found but they did not have a useable configuration.  

After trying the lshw command you gave I got the following output:


```
root@ computer:~# lshw | grep -A 11 display
*-display UNCLAIMED
description: VGA compatible controller
product: 82852/855GM Integrated Graphics Device
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 02
width: 32 bits
clock 33 MHz
capabilities: pm bus_master cap_list
configuration: latency=0
resources: memory:d8000000-dfffffff(prefetchable) memory:f0000000-f007ffff ioport:f800(size=8)

```Hope this better explains the problem I am having.  Thanks for all of your help so far.

---

### Post by oldfred on 2011-06-22
Most of my notes are on nVidia as that is what I have. My portable is Intel but it has always just worked, so I have little info on it.

Since this thread title is grub related, you will not get many users with knowledge of video issues on Intel 82852/855GM.
 
I would suggest first searching forum for similar issues with Intel and posting a new thread with that in the title, so those that have solved it may respond.

I think using google is often better than the forums search function.
Just append site:ubuntuforums.org to your search terms.
I found this solved, but do not know if it has useful info or not:

[SOLVED] Working Intel driver for 82852/855GM 
[http://ubuntuforums.org/showthread.php?t=1464239](http://ubuntuforums.org/showthread.php?t=1464239)

---

### Post by pdiefend on 2011-06-22
Well thanks for the help.  I have been in contact with the manufactures of the system and they provided me with the original xorg.conf file that was intended to work with the drivers of the system, which sort of worked.  The System originally had Debain but the intent was to change it to Ubuntu which was easier to learn and use for those unfamiliar with linux.  I will change this to solved since Grub was there and the real problem was with X session.

Thanks for all your help.

---

