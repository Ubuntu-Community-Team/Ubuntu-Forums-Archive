---
title: "Lubuntu on Pentium III processor and 384MB of RAM"
date: 2014-03-02
forum: Installation &amp; Upgrades
---

### Post by ZTP on 2014-03-02
Hello everyone. I'm not a computer expert, but I recently bought an old computer for less than 10€ and I wanted to install Lubuntu on it but I accomplished nothing but failures so far.

The computer has a Pentium III processor and 384MB of RAM, with a 10GB hard disk. It has (had!) Windows XP Home on it.

I have some live CDs with different distros, so I tried to enter the BIOS menu to make it boot from CD - turns out there's no such thing as a BIOS menu, only a CMOS menu. From there I set the CD-ROM as primary master instead of the hard disk, but all the different CDs I tried to boot from gave me the same error: ATAPI incompatible. I managed to burn two CDs using Nero from the Windows XP installed on the same machine, so I guess the optical drive is working, right?

The machine has two USB ports, but only one is working. I highly doubt it's able to boot from USB flash drive, but I still tried to stick it in and disable both the primary and secondary master/slaves to force it to try to boot from something else, to no end.

I did the same with a floppy disk and I successfully booted eBoot (a minimal Linux distro) from a single floppy disk, so at least that works, but it's so small it's useless to me casual user... I need a "true" OS 

I cleaned the CMOS and removed and inserted the battery back, hoping to unlock the BIOS or something, I tried it all.

I downloaded Smart Boot Manager and successfully executed it but I didn't find an option to boot from CD.

I downloaded Wubi and launched it, but it kept giving me weird errors mid-installation and aborted.

I downloaded a Lubuntu ISO, extracted the kernel and initrd and put them in C: and reconfigured the boot.ini to give me the option to load grldr during boot, downloaded grub4dos, managed to get into grub menu and manually loaded kernel and initrd. Seemed to work fine, but I got stuck at a busybox/initramfs prompt.

I downloaded UNetbootin and launched it, but the first installation of Lubuntu failed after a while because I was trying to dual boot it with Windows and I didn't have enough space on the hard disk. I restarted it going #yolomode and giving Lubuntu the full disk, basically formatting the hard disk and deleting Windows for good. Seemed to work fine, kept downloading for a long while, I followed the installation wizard step by step and finally I read "Installation complete, reboot now?". I rebooted... now Lubuntu is obviously the only OS left in my machine, so it booted that, only to arrive to a black screen with blurred unreadable text that seems to be a shell (but it isn't: I tried a few commands and it acted weird). I took a photo of the screen just in case.

[IMG]http://i.imgur.com/bseGbJO.jpg?1[/IMG]

I rebooted multiple times but this always happens. 

Now I don't even have Windows anymore, and I don't know what to do. I'm left with a computer that won't seem to boot from CD and has basically no OS. I googled a lot and it seems there's a way to install from multiple floppies, but unfortunately I only have two and one of them is damaged and can't be used (and to say I was glad I found a working one after 10+ years, good thing I never throw anything). Even then, for some reason I don't think it'd work and it seems to be by far the most technical/scary way to install the OS.

Can you guys please help me? I'm clueless as to what to do. I know it's just a cheap and old computer, but it still drives me mad! 

When I turn it on, I see the Packard Bell logo and just two options: Esc to go to POST and F2 to open CMOS menu. I tried blindly F1, F12, Ctrl+Alt+S and any other combination I found on the web. Nothing.

Any help, hint, suggestion, or even a plain "You're an idiot, you should have done this and that" is warmly welcome because as of now I think I have no more tools left to try.

Unfortunately I don't know the model of my motherboard and I didn't manage to find it. I browsed the Packard Bell site to find it out but it looks like there was a serial number printed on a sticker on the side of the chassis that now isn't there. As I said I'm no expert and I can't tell what model it is just by looking at it.

Thanks in advance and please forgive my ignorance and occasional English slips, this isn't my native language.

---

### Post by Bashing-om on 2014-03-02
ZTP; Hi ! Welcome to the forum .

OK, You are doing well(er) than you think.
Take a breather, and a good cup of coffee and have a read:
[https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall](https://help.ubuntu.com/community/Lubuntu/Documentation/MinimalInstall)

Maybe you (re-)install, maybe not.
Try this:
Boot the install and as soon as the "CMOS" (??) screen clears, depress and hold the right shift key -> grub boot menu;
With the highest kernel (NON-recovery) version highlighted, depress the 'e' key for edit mode ->
Boot parameters screen; arrow down and across to the terms "quiet splash" and add the term "nomodeset" - without the quotes -;
key combo ctl+x to continue the boot process to what we hope is a GUI login.

Depending on what graphics card you have installed, the boot parameter "nomodeset" may not be applicable. But, likely.
If you can not boot to the GUI, will see what can be done to get ya to a Command Line Interface and acquire additional info to allow us to advise how to adjust the booting to get ya up.

Additional help is pending what results from these attempts.

[INDENT][INDENT]hey, it's 'buntu
[INDENT][INDENT][INDENT]all things are possible
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Lars Noodén on 2014-03-02
Have you tried Lubuntu 12.04 to see if that works?  The older version has some differences which often makes it work better with older CPUs.

---

### Post by mörgæs on 2014-03-02
For Lubuntu 12.04 is short term support. The only supported option is 13.10. 

ZTP, are you sure that you want to invest time in the old iron? If you are lucky you will get a system on which you are able to watch only the simplest web pages. If it were mine I would try to sell it and get my 10 &#8364; back.

---

### Post by grahammechanical on 2014-03-02
The term CMOS refers to the chip that holds the BIOS. You need to make sure that you are running a distribution of Linux compatible with your CPU. If the CPU is 32bit then you need a 32bit version of Ubuntu. A 64bit version will not run. If the CPU is 64bit then you can use either 32bit Ubuntu or 64bit Ubuntu but there is still one more thing that you need to check about the CPU. Is it a PAE CPU. Physical Address Extension is a feature to allow 32bit CPUs to access Memory (RAM) more than 4 gigabytes.

If the CPU is non-PAE then you need a version with a Non-PAE Linux kernel. Ubuntu now only has PAE versions.

> [COLOR=#333333][FONT=Ubuntu]Because PAE is close to being ubiquitous it is now a requirement for Ubuntu: During installation the processor is prompted for the PAE flag, and only if present the process will carry on. [/FONT][/COLOR]

[https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

So, I ask, does the Pentium III meet the requirement for having PAE?

Regards.

---

### Post by mörgæs on 2014-03-03
All Pentium 3's are 32 bit and support PAE.

---

### Post by ZTP on 2014-03-04
@Bashing-om: thanks! Your suggestion really did something, but I still have some issues. Adding nomodeset I managed to boot Lubuntu but there's no GUI... which is not *terrible* by any means, but there's more bad news. Whenever I reboot I have to edit the file again and add the "nomodeset" again! Plus for some weird reason my computer is EXTREMELY slow when editing that file; whenever I press an arrow or letter key, it takes up to 10 seconds for it to execute -_-

Is there a way to save those changes? The prompt said it had "minimun Emacs commands" available, but I never used Emacs, I use Vi. So I googled a bit and it turns out I have to press Ctrl-x and then Ctrl-s to save, but the first combination is the one that makes me exit and boot!

When it reboots without the "nomodeset" it's blurred again and I can't read anything, but I discovered what that is: it's the Lubuntu login prompt! I blindly entered my login name and password and I received a blurred version of the same welcome screen I got when it worked properly. 

So in the end I'm able to login properly and I have a command line OS, but I have to spend literally 20 minutes every time to edit that file (at first I thought my keyboard wasn't connected...). That's one big step forward, thanks again. Now do you have any idea/suggestion as to what to do next?

The OS is fully functioning, I have my home and everything. I guess there might be a way to edit that very same file from within the OS... ?

@mörgæs: I know it's a very old machine, and I know I could get a way more usable one for about 100€-150€, but to me that's some money and all I really need now is a way to learn "how to Linux" and why not, a command line OS could be cool, but I think I'll need a GUI support at least in the beginning - I'd gladly switch between the two for the first times. Also, I program simple things as a hobby and that sure isn't hardware demanding :)

Thanks to the other two guys as well for the interest. If anyone has any idea how to improve my current situation, please let me know!

---

### Post by sudodus on 2014-03-04
See these links about old computers and suitable operating systems for them,
[URL="http://ubuntuforums.org/showthread.php?t=2130640"]
Old hardware brought back to life
[/URL][Light Linux Distributions - Hardware Testing (RAM)]("http://ubuntuforums.org/showthread.php?t=1582027")

My personal tips are ***Knoppix***, ***Puppy***, ***DSL*** or if it is OK without graphics: ***Ubuntu mini.iso*** and make a small server.

---

### Post by David_Wright on 2014-03-04
> **ZTP said:**
> @mörgæs: I know it's a very old machine, and I know I could get a way more usable one for about 100€-150€, but to me that's some money and all I really need now is a way to learn "how to Linux" and why not, a command line OS could be cool, but I think I'll need a GUI support at least in the beginning - I'd gladly switch between the two for the first times. Also, I program simple things as a hobby and that sure isn't hardware demanding :)

Thanks to the other two guys as well for the interest. If anyone has any idea how to improve my current situation, please let me know!
Sudodus beat me to it - I was going to suggest Puppy Linux.  It's very light and will boot off of a USB stick (and can save all updates back to the same USB stick).  It's a branch of the Linux tree but seems a good place to start playing with the system . . . .it's what I did.  There are many, many variants but I think that Lucid Puppy is probably a good starting point for old hardware.

---

### Post by sudodus on 2014-03-04
If you decide to go along the Puppy track, try also Wary,

[http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm](http://puppylinux.org/main/Long-Term-Supported%20WaryPuppy.htm)

---

### Post by mastablasta on 2014-03-04
have a look at this on how to get minimal Ubutnu OS installed: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal) 
should work ok on your maschine.

I have old Chrunchbang installed on 1.2Ghz with 224 mb ram available. newer one would probably work as well. haven't upgraded yet. might be worth a look. install is almost as simple as in ubuntu though you may need some more manual configuring after it's is installed.

to boot from USB one can use PLOP boot manager - it will boot from floppy and then you will see a menu offering you to boot from USB.

changing boot options permanently on existing installation is described here (move a bit down the page): [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by ZTP on 2014-03-04
Ok, I'm thankful for all the answers but please read this: [SIZE=3]**I do not need suggestions on which Linux distro to install**[/SIZE] (at the moment). My computer refuses to boot from CD or USB no matter which tool I try.

I have another problem and goal: whenever I boot, it automatically boots Lubuntu (which is what I want) without a GUI but the text is all blurred and unreadable.

If I do, however, enter the grub menu holding SHIFT and tell it to boot Ubuntu (which is just the menuentry name for Lubuntu), it works fine, i.e. there's still no GUI but the OS is fully functioning and readable. It's weird because Ubuntu IS the first one on the list and thus manually selecting it should be just the same at don't giving it any input.

To achieve this I manually edited the /boot/grub/grub.cfg file adding "nomodeset" after "quiet splash" on the Ubuntu menuentry. Then I edited /etc/default/grub putting GRUB_DEFAULT=saved to force it to load Lubuntu everytime; I also added the voice GRUB_SAVEDEFAULT=true, then sudo update-grub, then did step 1 once again because the update overwrote grub.cfg (I didn't know that). This might have been overkill because GRUB_DEFAULT was already set at 0 and Lubuntu is the first menuentry in grub.cfg, so in theory this change was useless, but I wanted to be sure it's not trying to load anything else.

_So if I turn on the computer it boots Lubuntu but it's unreadable. If I enter the grub menu and tell it to boot Lubuntu form there, it loads just fine. You guys have any idea how that might be possible?_

---

### Post by Bashing-om on 2014-03-04
ZTP; Hello,

OK, working with what we have to work with. Not a problem to try !
Graphics is the issue, and that issue is dependent on a graphics driver, that is dependent on what the graphics interface is.
Heads up, if it turns out to be SIS graphics on that old box, you are in for a long hard row to get graphics working.

To get your question of a persistent "nomodeset" one does edit the file /etc/default/grub -> this line: "GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"" and add "nomodeset" @ quiet splash.

OK, here is a thought to get ya booting to a functional terminal to enable us to get relevant hardware information.

Edit that line and remove the terms quiet splash and insert the terms "text and  nomodeset" . One then boots to a terminal (TTY1).
Also something else we might be able to do is from the grub boot terminal, find out what graphical modes are supported and also edit the line in /etc/default grub to use that initial resolution (???) -> GRUB_GFXMODE=1600x900 ( where 1600x900 is the highest resolution MY monitor will support, yours will be different !) 
To know what modes are supported -> boot grub command line command 'vbeinfo'.

Once completed editing the grub file, as you know, the terminal command
```

sudo update-grub

```must be issued to propagate the change to the rest of the system control files.


Once we are at a system terminal (TTY1); post back the out put of terminal commands:
```

lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
To see your graphics card and info.

let us  see what 
[INDENT][INDENT]we can make happen
[/INDENT][/INDENT]

---

### Post by xxx6 on 2014-04-10
> **mörgæs said:**
> All Pentium 3's support PAE

R U sure???

---

### Post by xxx6 on 2014-04-10
> **ZTP said:**
>  [SIZE=3]**I do not need suggestions on which Linux distro to install**[/SIZE] 

no need to yell!

btw: if U have still Xp try this tool 4 boot from USB: [http://www.plop.at/en/bootmanager/mbrinstall.html](http://www.plop.at/en/bootmanager/mbrinstall.html)

---

### Post by mörgæs on 2014-04-11
> **xxx6 said:**
> R U sure???

I'm sure about everything I post unless I clearly state otherwise. 
Please don't spread more PAE-fear. We have enough of that already.

---

