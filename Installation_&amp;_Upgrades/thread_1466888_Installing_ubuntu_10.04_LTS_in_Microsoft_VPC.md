---
title: "Installing ubuntu 10.04 LTS in Microsoft VPC"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by MrDerekBush on 2010-04-30
Hello Ubuntu Community!

I figured that my first post in this  forum should be a helpful one.  I've notice several posts regarding  people having issues installing Ubuntu 10.04 LTS in the Microsoft  Virtual PC environment.  Instead of simply telling these people to use  virtual box or a different virtualization solution, I think we should  welcome our Microsoft brethren to the fold - as some of us don't have a  choice ;).  I personally work in a Microsoft based development shop, so  its mandated that I use MS based products, but wanted to be able to try  out the new version of Ubuntu.  I was able to make some progress on the  install this morning, and here's what I did:

1: Create a brand  new VM with a fixed disk.

2: Before booting for the first time,  point the DVD drive to the ubuntu.iso on your system

3: Start the  VM and keep tapping the "F4" key until you get to the language  selection screen.

4: Hit escape to clear the language selection,  and then hit "F6" for other options and to bring up the Boot options  string.  Then hit escape again to clear the selection box.

5:  edit the Boot Option string by deleting  the part that says “**quiet  splash -**” and replace  it with “**vga=791 noreplace-paravirt**”

6: Select  the "Try ubuntu without installing" option.

7: Wait for it to  boot completely into the desktop environment.

8: Once in, run the  Install Ubuntu script on the desktop and follow the prompts. 

And  this is as far as I got.  At this point the grub configuration needs to  be edited, but since this version uses grub 2.x, I'm not as familiar  and will poke at this as time permits.  Hopefully this gets some of you  out there moving forward with this.

Thanks,

-Derek

---

### Post by texhead on 2010-05-10
Thanks MrDerekBush, Even tho i am using Kubuntu 10.04 this got me through to installation.

Thanks again.

[edit] After installation the virtual session failed and wouldn't boot into Kubuntu, back to the drawing board.....[/edit]

---

### Post by pessimism on 2010-05-11
To edit grub's configuration after you install do this

places ->XGB Filesystem to mount hard drive
sudo mount -o bind /dev /media/<long gibberish id number>/dev
sudo chroot /media/<long gibberish id number>/ /bin/bash
mount -t proc none /proc
nano /etc/default/grub
remove quiet splash from grub_cmdline_linux_default
comment grub_hidden_timeout

nano /etc/grub.d/10_linux
under linux_entry section, change args="$4" to
args="$4 noreplace-paravirt"
save and exit
update-grub    ignore cannot find list of partitions error


From there I have issues with seeing the console, there are different solutions involving setting grub to text console, nomodeset as kernel parameter, setting a grub graphic resolution etc.  I tried a few combinations but the kernel always locks and shuts off the VM just after processor detection at the line
ftrace: allocating 22402 entries in 44 pages

noapic, nolapic, acpi=off all had no effect

---

### Post by crouz on 2010-06-05
I am running Ubuntu 10.04 Server through Microsoft Virtual PC 2007 on a Windows 7 64-bit OS.

Just adding any VPC valid VGA mode, e.g vga=788, avoids the crash for me and it also fixes the broken graphics. For graphic mode details please refer to [http://www.pendrivelinux.com/vga-boot-modes-to-set-screen-resolution/](http://www.pendrivelinux.com/vga-boot-modes-to-set-screen-resolution/)

The noreplace-paravirt is not required for me.

To fix this permanently (or at least until you install a new kernel), make the same edit to /boot/grub/menu.lst. By default it is the first entry in the kernel list that is used.

---

### Post by qpackard on 2010-06-09
xp pro sp3
vpc 2007 sp1
Ubuntu 10.04
Dell d410 latitude
2048Mb ram
1.73 GHz
P&P Monitor, 9152GM/GMS/910GML

I have set up my vpc with 512mb, Ubuntu loads up (takes forever,) but when I try to move the mouse around to select Install the screen chops itself into horizontal pieces, the mouse does not respond properly and the cursor will not respond to the tab, shift or arrow keys. Have tried this about 5 times and expecting different results everytime, but it is always the same. Any suggestions to make it work?

---

### Post by OneSeventeen on 2010-06-13
> **MrDerekBush said:**
> I've notice several posts regarding  people having issues installing Ubuntu 10.04 LTS in the Microsoft  Virtual PC environment.  Instead of simply telling these people to use  virtual box or a different virtualization solution, I think we should  welcome our Microsoft brethren to the fold - as some of us don't have a  choice ;).

Awesome, AWESOME attitude!

Oh, and thanks for the help, Ubuntu 10.04 installing now on my Windows 7 machine without installing yet another virtual machine environment to junk up my hardware manager... I love VMware and virtualbox, but Virtual PC came with my Windows 7 Ultimate along with a legit copy of Windows XP Pro, which lets me do what I need to for my business.  Nothing is worse than having several virtual environments generating their own virtual network adapters and virtual hardware adapters just so I can use geek-politically-correct software where I can.

**EDIT:** I tried rebooting the VM and it got stuck on *casper is resyncing snapshots and caching reboot files...  after I forced it to power off, it just sat there for a while with a blinking cursor...
any tips? Did I do something wrong?

Thanks again for all the help!

---

### Post by squa89 on 2010-06-16
> **OneSeventeen said:**
> Awesome, AWESOME attitude!

Oh, and thanks for the help, Ubuntu 10.04 installing now on my Windows 7 machine without installing yet another virtual machine environment to junk up my hardware manager... I love VMware and virtualbox, but Virtual PC came with my Windows 7 Ultimate along with a legit copy of Windows XP Pro, which lets me do what I need to for my business.  Nothing is worse than having several virtual environments generating their own virtual network adapters and virtual hardware adapters just so I can use geek-politically-correct software where I can.

**EDIT:** I tried rebooting the VM and it got stuck on *casper is resyncing snapshots and caching reboot files...  after I forced it to power off, it just sat there for a while with a blinking cursor...
any tips? Did I do something wrong?

Thanks again for all the help!


I'm about at the same place as OneSeventeen.  I followed the OP's steps and it appeared to install Ubuntu successfully to my virtual hard drive.  At the end of the installation it said it needed to reboot and gave me a message similar to "casper is resyncing snapshots and caching reboot files".  It then did attempt to reboot.  

However, when VPC rebooted, it quickly flashed a terminal/command-line type message on the screen and then shut down.  All subsequent attempts to start up the VPC end up with the same outcome.  The virtual hard drive shows about 2.5 GB of space used, so it does appear files were installed.  Just not working.

Attached is a screen grab of the one message I get prior to VPC shutting down when I try to run it.

Anyone have any thoughts?

BTW, I'm relatively new to the whole Linux world, so if I missed something simplistic, I apologize in advance :-P

---

### Post by markwilson on 2010-06-24
Thank you @MrDerekBush for posting a ***real*** *solution* instead of a "install another virtual machine manager" workaround - I too work in an environment where I'm already using Virtual PC and I don't want the complexity of adding Virtual Box or VMware Workstation to the mix!
 
Following Derek's instructions, and then @pessimism's additional commands, with the inclusion of ```
vga=788
``` to /etc/default/grub in place of quiet splash as @crouz suggested, I was able to get Ubuntu 10.04 Desktop (32-bit) to work on Windows Virtual PC, on top of Windows 7 Enterprise x64 (I did add the ```
noreplace-paravirt
``` to /etc/grub.d/10_linux, even though it may not be needed)
 
I too had the message about casper resyncing snapshots (on shutdown after installing).  I left it for a while (about an hour, perhaps) but then I had to go home so I hibernated the VM.  When I brought it back online the next day, it just booted Ubuntu as normal.

---

### Post by pestaa on 2010-06-26
> **OneSeventeen said:**
> 
**EDIT:** I tried rebooting the VM and it got stuck on *casper is resyncing snapshots and caching reboot files...  after I forced it to power off, it just sat there for a while with a blinking cursor...
any tips? Did I do something wrong?

At this point, I pressed Enter.

---

### Post by RonSMeyer on 2010-06-26
After numerous attempts I finally got it to install and boot. 
However the functionality is limited: 

Sound doesn't work
Can only get 800x600
Mouse wheel doesn't work 

Can those thing be made to work? 
Would they work with virtual-box or vmware?

---

### Post by RonSMeyer on 2010-07-01
Naw, I gave up after wasting an entire week on this. Installed Virtual Box and everything worked perfectly the first time.

---

### Post by Shede on 2010-07-20
> **pessimism said:**
> To edit grub's configuration after you install do this
  
From there I have issues with seeing the console, there are different solutions involving setting grub to text console, nomodeset as kernel parameter, setting a grub graphic resolution etc. I tried a few combinations but the kernel always locks and shuts off the VM just after processor detection at the line
ftrace: allocating 22402 entries in 44 pages
 
noapic, nolapic, acpi=off all had no effect
 
I can get arround that by disabling Virtualization in the CMOS.
 
Not an elegant solution, but it does work.

---

### Post by jjdd88 on 2010-08-09
I follow the steps to install ubuntu successfully.  But after reboot,  IT keep power off.  How to boot up in text mode?  I have no chance to change anything because it keep power off.
I do try boot options,  but no luck maybe due to I don't know what to try.
 
Thanks
 
Joseph

---

### Post by lemorange on 2010-08-17
> **pessimism said:**
> To edit grub's configuration after you install do this
 
places ->XGB Filesystem to mount hard drive
sudo mount -o bind /dev /media/<long gibberish id number>/dev
sudo chroot /media/<long gibberish id number>/ /bin/bash
mount -t proc none /proc
nano /etc/default/grub
remove quiet splash from grub_cmdline_linux_default
comment grub_hidden_timeout
 
nano /etc/grub.d/10_linux
under linux_entry section, change args="$4" to
args="$4 noreplace-paravirt"
save and exit
update-grub ignore cannot find list of partitions error
 
  

 
follow the steps given above but for
 
**remove quiet splash from grub_cmdline_linux_default**
 
instead of having the commandline empty as suggested above, change to
 
**grub_cmdline_linux_default="vga=791"** 
 
reboot and press 'e'when in the grub boot menu. Check "vga=791  noreplace-paravirt" is there. You will be able to see Ubuntu boot up ok.
 
also I found it easier if installed a GUI mount manager just after the OS installation (i.e.: still in the Live-CD mode)
I had the hdd mounted as /media/sda1 and it saved me some effort with the "long gibberish id number"

---

### Post by ossifer on 2010-08-20
> **pessimism said:**
> To edit grub's configuration after you install do this

places ->XGB Filesystem to mount hard drive


I'm familiar with the rest of the commands but I have a feeling I'm missing some terminology with this line. What does this mean?

Edit:
Should I let the installer complete it's work and reboot before editing the grub conf file? If so, how do I get it to boot far enough to have any access to config file? If not, where do I go to find the file in the live environment?

Initially, I assumed I was chrooting into the permanent environment before I left the live environment but there is no long, gibberish ID number in /media so I can't get far enough to chroot.

Edit 2: Nevermind, I closed the terminal and tried again. It worked. It's all going fine, still in the live environment.

However, I do wonder what this is:
```
update-grub ignore cannot find list of partitions error
```

---

### Post by lemorange on 2010-08-24
1. 
XGB Filesystem, where X is some number of GB. 
ex.: 10GB Filesystem, etc. which basically means your harddisk. You will see it in the Place menu, top pannel.
 
2. 
'long gibberish ID number' can be found in /dev/disk/by-uuid
 
3. 
In my case, Places menu somehow did not list my filesystem so I had to install Disk Utility from the Synaptic in order to mount the hard disk before following the steps originally given. 
 
Also, there is no point in re-booting unless the grub config files are modifed and update-gub is performed before the re-boot.
 
The idea is to modify grub setting installed in the HDD, so if one somehow fails to chroot, all the modifications made are just 'temporary' and Ubuntu will not boot from the HDD.

---

### Post by Chudilo on 2010-08-25
> **RonSMeyer said:**
> After numerous attempts I finally got it to install and boot. 
However the functionality is limited: 

Sound doesn't work
Can only get 800x600
Mouse wheel doesn't work 

Can those thing be made to work? 
Would they work with virtual-box or vmware?

I was able to set everything up without doing anything special in XP professional with service pack 3.

Video is limited 800x600; seems like Virtual PC is limiting it until Virtual PC additions are installed. Will investigate further.

---

### Post by franklin84 on 2010-08-25
Same problems!
But the instructions of [MrDerekBush]("http://ubuntuforums.org/member.php?u=1063013") works for me!

Now Ubunto is installed and I don't know how to use this commands:
"places ->XGB Filesystem to mount hard drive
sudo mount -o bind /dev /media/<long gibberish id number>/dev
sudo chroot /media/<long gibberish id number>/ /bin/bash
mount -t proc none /proc"

Please help me!
It won't work if I insert my ID that I found in  /dev/disk/by-uuid

If I shoutdown the VPC it don't reboot and exit's few seconds later :-x


Best regards
Frank



PS: Sorry for my bad English, I'm from Germany :-9

---

### Post by Maddalot on 2010-08-25
Okey, i found a way to boot the installation.

1. Press and hold SHIFT down while starting WM
2. GRUB menu starts
3. Edit the command you want to run by pressing 'e'
4. Replace"**quiet  splash**"with "**vga=788 noreplace-paravirt**”
5. Ctrl-x
6. Now booting

Edit you boot settings to the same as over and tada.

:popcorn:

---

### Post by blurfocus on 2010-08-27
Frank,

Maybe this way of restating the instructions will be more clear:

1. create a new virtual hard drive for the VirtualPC virtual machine
2. load the Ubuntu ISO into the virtual DVD (CD) drive.
3. reboot the virtual machine from the virtual DVD drive
4. press F4 a few times until you see the menu asking for a language
5. press the ESC key
6. Use the up/down arrow keys to make sure that you have selected "Try Ubuntu without Installing" option.
7. press F6
8. press ESC again
9. use the backspace key to erase "quiet splash --" and then type "vga=788" instead (without the quotes)
10. press ENTER to boot from the virtual DVD drive (try ubuntu without installing)
11. after it boots, doubleclick on the icon that mentions "Installing Ubuntu"
12. Once Ubuntu is installed, do _not_ reboot.  Instead hit "Continue to Test"
13. Click the Places menu at the top and choose the virtual hard drive from the list. It will have the capacity of the drive as part of the name e.g. "20GB Filesystem" or whatever. This will mount your hard disk so that the following commands will work.
14. Now click the top left menu "Applications" and choose "Terminal" from the list.  This will give you a command line prompt.
15. Type the following commands:

sudo mount -o bind /dev /media/<press TAB here to see the big number>/dev
sudo chroot /media/<press TAB here>/ /bin/bash
mount -t proc none /proc
nano /etc/default/grub

16. In the nano editor, replace "quiet splash" with "vga=788 noreplace-paravirt"
17. put a # at the beginning of the GRUB_HIDDEN_TIMEOUT line to comment it out.
18. save the file and exit the nano editor
19. Now type: update-grub at the shell prompt.  This is a command that will process the changes that you made to /etc/default/grub.
20. now type: sync; exit; exit
21. Then reboot the virtual machine
22. If the reboot stalls out, then press the ENTER key

At this point, it should boot the graphical Ubuntu login screen and present you with your username as one of the login choices.

Note: other people came up with these instructions.  I just combined them all into one post and explained some things in more detail.

Good luck.

-John

> **franklin84 said:**
> Same problems!
But the instructions of [MrDerekBush]("http://ubuntuforums.org/member.php?u=1063013") works for me!

Now Ubunto is installed and I don't know how to use this commands:
"places ->XGB Filesystem to mount hard drive
sudo mount -o bind /dev /media/<long gibberish id number>/dev
sudo chroot /media/<long gibberish id number>/ /bin/bash
mount -t proc none /proc"

Please help me!
It won't work if I insert my ID that I found in  /dev/disk/by-uuid

If I shoutdown the VPC it don't reboot and exit's few seconds later :-x


Best regards
Frank



PS: Sorry for my bad English, I'm from Germany :-9

---

### Post by blurfocus on 2010-08-28
Or you can try this set of instructions with screenshots and everything:

[http://www.hanselman.com/blog/InstallingUbuntu104LTSOnWindowsVirtualPCOnWindows7.aspx?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+ScottHanselman+%28Scott+Hanselman+-+ComputerZen.com%29](http://www.hanselman.com/blog/InstallingUbuntu104LTSOnWindowsVirtualPCOnWindows7.aspx?utm_source=feedburner&utm_medium=feed&utm_campaign=Feed%3A+ScottHanselman+%28Scott+Hanselman+-+ComputerZen.com%29)

> **blurfocus said:**
> Frank,

Maybe this way of restating the instructions will be more clear:

1. create a new virtual hard drive for the VirtualPC virtual machine
2. load the Ubuntu ISO into the virtual DVD (CD) drive.
3. reboot the virtual machine from the virtual DVD drive
4. press F4 a few times until you see the menu asking for a language
5. press the ESC key
6. Use the up/down arrow keys to make sure that you have selected "Try Ubuntu without Installing" option.
7. press F6
8. press ESC again
9. use the backspace key to erase "quiet splash --" and then type "vga=788" instead (without the quotes)
10. press ENTER to boot from the virtual DVD drive (try ubuntu without installing)
11. after it boots, doubleclick on the icon that mentions "Installing Ubuntu"
12. Once Ubuntu is installed, do _not_ reboot.  Instead hit "Continue to Test"
13. Click the Places menu at the top and choose the virtual hard drive from the list. It will have the capacity of the drive as part of the name e.g. "20GB Filesystem" or whatever. This will mount your hard disk so that the following commands will work.
14. Now click the top left menu "Applications" and choose "Terminal" from the list.  This will give you a command line prompt.
15. Type the following commands:

sudo mount -o bind /dev /media/<press TAB here to see the big number>/dev
sudo chroot /media/<press TAB here>/ /bin/bash
mount -t proc none /proc
nano /etc/default/grub

16. In the nano editor, replace "quiet splash" with "vga=788 noreplace-paravirt"
17. put a # at the beginning of the GRUB_HIDDEN_TIMEOUT line to comment it out.
18. save the file and exit the nano editor
19. Now type: update-grub at the shell prompt.  This is a command that will process the changes that you made to /etc/default/grub.
20. now type: sync; exit; exit
21. Then reboot the virtual machine
22. If the reboot stalls out, then press the ENTER key

At this point, it should boot the graphical Ubuntu login screen and present you with your username as one of the login choices.

Note: other people came up with these instructions.  I just combined them all into one post and explained some things in more detail.

Good luck.

-John

---

### Post by franklin84 on 2010-08-28
Thanks blurfocus!
That's really great instructions with these nice screenshoots.


Is this way also possible with Xubunto or Kubunto?
I can't find "XX GB Filesystem" :-((


Best regards
Frank

---

### Post by lemorange on 2010-08-30
> **franklin84 said:**
> Thanks blurfocus!
That's really great instructions with these nice screenshoots.
 
 
Is this way also possible with Xubunto or Kubunto?
I can't find "XX GB Filesystem" :-((
 
 
Best regards
Frank
 
I had the same problem with Xubuntu and solved it by installaing Disk Utility, available from the Ubuntu Software Center, while still in the LIVE mode. 
Very simple GUI for mounting stuff.

---

### Post by Galvanise on 2010-08-30
Hi!

Sorry for my english but i'm portuguese! :D

I was trying to do this but i'm not getting it. :confused:

When i reboot my virtual pc appears to me that 

[IMG]http://img837.imageshack.us/img837/3660/ubuntun.jpg[/IMG]

or that

[IMG]http://img440.imageshack.us/img440/7291/ubuntu2.jpg[/IMG]

or something else but notting more happens...

Can i get some help?

---

### Post by franklin84 on 2010-11-17
Hello!

It works, but...

I can't find any USB device like USB Stick or Hard-Drive!!

Anyone the same Problem?


Best regards,
FRank

---

