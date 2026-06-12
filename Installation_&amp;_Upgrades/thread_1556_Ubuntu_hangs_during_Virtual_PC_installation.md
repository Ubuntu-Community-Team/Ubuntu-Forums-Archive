---
title: "Ubuntu hangs during Virtual PC installation"
date: 2004-10-21
forum: Installation &amp; Upgrades
---

### Post by the_drudge on 2004-10-21
Hi,

I'm a newcomer to Ubuntu, and to this board.

I'm trying to install Ubuntu (the latest version downloaded via your website) using MS Virtual PC 2004.

The partitioning and initial installation works perfectly, but then when I reboot as instructed the process hangs, and I get one of the following messages:


1. Post-installation reboot error message:

"isapnp: checksum for device 1 is not valid (0x89)"
"isapnp: checksum for device 2 is not valid (0xbe)"

OR

2. Post-installation message when rebooting into recovery mode:

"VFS: Mounted root (cramfs filesystem) readonly."

I'd be grateful for any help.


The Drudge



Tech specs:
Pentium 4 3.0Ghz with 1Gb Ram
Win XP Pro
Latest version of Virtual PC
600Mb RAM  and 17 GB Virtual HD allocated to Virtual PC

---

### Post by photomoto on 2006-07-21
I was getting this same problem, and was not able to find any solutions on the interweb via google. 

My system would display this exact error message and just hang.

After much trial and error, virtual pc will continue past this error if you reduce the amount of ram you allocate to the virtual machine.

I am not sure what the limit is, but I was allocating 1 gig, and it would hang. I now use just 256 and it will continue the install process. I hope this helps someone.

---

### Post by zphelj on 2006-07-23
If you choose option F6 to specify more parms and then backspace over the 'quiet splash' options you will get a verbose boot on the console which will help you find out what's happening.  I found that when I also used F4 and choose 1024x768x16 it would boot clean  up to the network init on eth0.  To get that far I had to be sure the CD was on the second controler.  Setting the network card to 'disconnected' got me all the way to where install was 'normal'.  I'm using the MS loopback interface so it's a bit trickier than normal.

Anyway, it's working really well for me now ..

---

### Post by theog on 2006-07-24
God bless both of you... I was sitting here downloading this and downloading that after I kept getting:

isapnp checksum device 1 and device 2 no valid (0x89) and (0xbe) errors...  

still having some video issues, but I think I can work through those from another post...

---

### Post by Ptero-4 on 2006-07-24
You should use either the old Connectix VPC or Qemu/IEmulator. Don´t use M$ V$PC, it´s been rewritten in such way that it emulates non-standar hardware known to be incompatible with linux.

---

### Post by theog on 2006-07-24
> **Ptero-4 said:**
> You should use either the old Connectix VPC or Qemu/IEmulator. Don´t use M$ V$PC, it´s been rewritten in such way that it emulates non-standar hardware known to be incompatible with linux.

Whatever... [-( bla, bla, bla.... seems to working just fine... thanks for the tip (or should I say lack of a tip).



Anyway, it seems after reading this post:

During install it is a black screen after the warning, but if you let it go (you will see your cd rom drive working) it will install into a pretty desktop.  Seems to be working ok...

[http://coolthingoftheday.blogspot.com/2006/06/virtual-pc-2004-ubuntu-and-video.html](http://coolthingoftheday.blogspot.com/2006/06/virtual-pc-2004-ubuntu-and-video.html)

"If you like operating systems like me, no doubt you've recently tried to install Ubuntu 6.06 and have run into some installation problems with Virtual PC 2004 SP1 related to display issues.  Try this trick:

Move the selection to "Install In Safe Graphics Mode" (second option) 
Hit F6 to modify the install options. 
Enter "vga=771" before the double dashes "--". 
Hit Enter.
The install should work fine from there on in..." [Content leached almost in full]

---

### Post by Davewasthere on 2006-07-31
I managed to install okay by just selecting a resolution (using F4).

I only assigned 256 Meg to the install, and chose the 1024x768x32 graphics mode.

All seemed to work well. Only, I have to boot in recovery mode, then exit to go to runlevel 2 without corrupting the graphics display. (I'm only running a LAMP server, no X server)

---

### Post by krisfranorge on 2006-08-30
I just installed Ubuntu 6.06 Dekstop normaly, thanks to this post. 

Here's my solution

problem one:
the install stopped with the two
"isapnp: checksum for device"-messages
solution: lowered my allocated memory to 512mb. the error comes, but install continues


problem two:
resolution is ****** up. Can barely see whats happening onscreen.
press f4 before install and choose a compatible resolution...
the rest... piece of cake..

hope this helps someone;)

---

### Post by phil_dom on 2006-12-16
Thanks gang. Big help.

:mrgreen:

---

### Post by phil_dom on 2006-12-16
Lowering to 512 or 256M got me to the primary install menu.
Regardless of the display setting (F4) I can not get a readable display.
Any other solutions or ideas out there?

Thx,
dom

---

### Post by gilbertr on 2007-01-04
MS VPC has difficulties using the default resolution used by the ubuntu (and other debian distro) install.
At the initial screen, when you have selected your language and keyboard settings, press F6 and add 'vga=771' (without the quotes) before the double dash (--)

This will force the fail-safe 800x600 at 8-bit instead of 16-bit.

Once installed, you'll also need to edit the /boot/grub/menu.lst and include the option vga=771 at the end of your boot selection :
kernel          /boot/vmlinuz-2.6.15-23-server root=/dev/hda1 ro quiet splash vga=771

If you are running X, you will need to modify your xorg.conf also to use 8 or 15-bit depth rather than 24-bit.

---

### Post by hankchinaski on 2007-01-19
Hi everyone....  I have the same problem.
Ive been trying "safe graphics mode" and the "vga=771" bit, but still, booting the live CD looks all distorted, like [this]("http://www.flickr.com/photos/espressobuzz/361868847/").

So I can't install it.

I read trying it on a fixed size disk might help, but it doesnt.
Now I'm trying again, with all hardware acceleration turned off, using the same options, but I'm not optimistic.

Any further tips on this?
Thanks
Hank

---

### Post by hankchinaski on 2007-01-20
Tried again with all hardware acceleration turned off, but same result.
Is it time for me to get a Mac and run Parallel?  ;-)

ready to give up.

what is the quickest way to boot the live CD so it doesnt look like the attached?

Thanks,
Hank

---

### Post by Gaevs on 2007-01-25
Hello, just use the wiki for the installation on Virtual PC, let it run until it loads the graphical interface, press Crtl+Alt+F1, type "sudo dpkg-reconfigure xconfig-xorg", follow the instructions, anwer the questions but not change anything, then it will ask you for the color depth, just chose 16 bits and you are set to go, after the program closes and return to the command prompt, press Crtl+Alt+F7 and then Crtl+Alt+Backspace to reset the screen, and that's all, you can see!!

Hope this helps.
Sorry for my english, i'm a little rusty..

Gaevs

PD if that is not the command, perhaps i missplaced some leters.. just check in the wiki!

---

### Post by Davides on 2007-04-04
> **zphelj said:**
> If you choose option F6 to specify more parms and then backspace over the 'quiet splash' options you will get a verbose boot on the console which will help you find out what's happening.  I found that when I also used F4 and choose 1024x768x16 it would boot clean  up to the network init on eth0.  To get that far I had to be sure the CD was on the second controler.  Setting the network card to 'disconnected' got me all the way to where install was 'normal'.  I'm using the MS loopback interface so it's a bit trickier than normal.

Anyway, it's working really well for me now ..

This solution works perfect for me, in virtual pc 2004 and 2007 with 256 mb ram

---

### Post by ErikV on 2007-09-26
> **Davides said:**
> This solution works perfect for me, in virtual pc 2004 and 2007 with 256 mb ram

For me too!!

---

