---
title: "Tried upgrading from 12.04 LTS to 12.10, froze while installing, now will not reboot."
date: 2014-03-16
forum: Installation &amp; Upgrades
---

### Post by helveteca on 2014-03-16
Hello,

My computer is locked up on black screen so I can't pull any relevant info at the moment. What I do know is that I was running Ubuntu 12.04 LTS on my Sony Vaio PCV-V210P. It seemed to be having problems installing anything new. I decided to try to upgrade in the Software center. Well after an hour and a half of downloading, it started installing packages, and then about 75% through it froze. I waited, then restarted. The startup screens showing "SONY" and "Intel Pentium Inside" seem to pop up fine, and then it's black screen with the fan running continuously.  If this is a quick fix that I'm too ignorant to figure out on my own, then any help is appreciated. Otherwise, I have no problems wiping this thing clean and starting over. 

Thanks!

---

### Post by David D. on 2014-03-17
You will likely need to reinstall.  You do realize that 12.10 reaches end of life next month (April 2014), whereas 12.04 LTS is good until April 2017.

My recommendation is to go back to the 12.04LTS, then upgrade to the 14.04LTS when it is released next month (April 2014).  You can do an LTS release to LTS release upgrade, but an upgrade from 12.10 would require going through all the intermediate releases (13.04 and 13.10) to reach 14.04LTS.  Of course you always have the option of doing a fresh install.

---

### Post by helveteca on 2014-03-17
Hi, thank you very much for that. Actually for the last few hours I've been trying to do a fresh install. I've got the disc with the iso, put it in and restarted. It won't boot from the cd. I double checked the disc to make sure it was properly burned; all the files were there. I then tested the computer by putting in my Damn Small Linux disc, and that started right up. 

When I put the 12.04 disc in now, it goes through the proper start up procedure, then the screen just starts flickering purple, then black, then half purple / half condensed bios mode. Is there something I'm doing wrong? I'm so frustrated now, I keep googling possible solutions and seem to keep hitting dead ends at every turn.

---

### Post by David D. on 2014-03-17
I did some searching and found some instructions that may help you.

1) Press “Shift button” while it loads from the cd – it should give you configuration screen.

2) Press F6 for additional options and select “nomodeset” option.

3) Pick Install Ubuntu and you should be good to go.

Once it is installed, check for and install any available additional drivers.

Good luck.

---

### Post by helveteca on 2014-03-17
Ok, so in trying that method; I pressed shift while loading, that took me to the "GNU GRUB" purple screen. Hitting F6 did nothing. The screen had several options and I posted some pics below to better explain my results;

When I hit shift as the disc loaded, this screen came up (GNU GRUB MAIN SCREEN)

[IMG]http://i107.photobucket.com/albums/m287/mirandasnyder/20140317_105002.jpg[/IMG]

When choosing to go "ADVANCED OPTIONS FOR UBUNTU" this came up

[IMG]http://i107.photobucket.com/albums/m287/mirandasnyder/20140317_105035.jpg[/IMG]

But when back at the GNU GRUB MAIN SCREEN, and hitting "e" for edit, this came up

EDIT PAGE 1
[IMG]http://i107.photobucket.com/albums/m287/mirandasnyder/20140317_105753.jpg[/IMG]

EDIT PAGE 2
[IMG]http://i107.photobucket.com/albums/m287/mirandasnyder/20140317_105822.jpg[/IMG]

This is where things get even harder for me. I'm not advanced enough yet to even understand some of the proposed solutions that I'm reading.

---

### Post by David D. on 2014-03-17
I think you have an incomplete install, because it was interrupted.  Have you tried the shift key and setting "nomode" to fix the flickering while booting from the DVD to reinstall?

---

### Post by helveteca on 2014-03-17
Hitting the shift key in which context? Hitting the shift key during restart or at any other time takes me back to the GNU GRUB screen. I've tried everything, I can't seem to fix the problem, nor even do a fresh install.

---

### Post by David D. on 2014-03-17
Please refer to post #4.  You do not want to restart, your install never finished so there are files and set-up missing.  

Please place the install DVD in the optical drive and restart the computer to boot from the install DVD.  When the boot process starts, hit the shift key to enter install options (not grub options booting from the HHD).  Then select F6 to go to the additional options page and select "nomode".  Let the computer go through the complete process of booting from the DVD in the "try Ubuntu" option.  Open GParted and use that program (on the DVD) to reformat the partition you want to install Ubuntu on the HDD.  Close GParted, and try a fresh install again.

---

### Post by helveteca on 2014-03-17
The problem is, it will not load from the CD/DVD drive. Although it is set to boot from CD/DVD.

---

### Post by SuperFreak on 2014-03-17
> **helveteca said:**
> I then tested the computer by putting in my Damn Small Linux disc, and that started right up. 




If you can still boot into Live version of this perhaps you can use it to reformat your hard drive and start over

this might help[http://www.linuxquestions.org/questions/damnsmalllinux-42/does-dsl-have-a-format-hd-option-641884/]("http://www.linuxquestions.org/questions/damnsmalllinux-42/does-dsl-have-a-format-hd-option-641884/")

---

### Post by helveteca on 2014-03-17
Hi! Do you mean use DSL to reformat the HD? So now we're opening up another can of worms. I have no idea how to do that with Damn Small Linux. Could you walk me through that?

As it stands, Damn Small Linux definitely starts right up, yet, when I put in Ubuntu 12.04.4 LTS disc, the drive says "DISK BOOT FAILURE INSERT SYSTEM DISK AND PRESS ENTER". Same as for my Windows 7 Ulitmate install disc too (though I did disable all other set up options for now to just strictly boot from the optical). No issue with DSL. I will google how to reformat through DSL to try and get this thing going. Hopefully I find a solution, if not, I'm definitely learning a lot about command lines as I go.

---

### Post by SuperFreak on 2014-03-17
> **helveteca said:**
> Hi! Do you mean use DSL to reformat the HD? So now we're opening up another can of worms. I have no idea how to do that with Damn Small Linux. Could you walk me through that?

As it stands, Damn Small Linux definitely starts right up, yet, when I put in Ubuntu 12.04.4 LTS disc, the drive says "DISK BOOT FAILURE INSERT SYSTEM DISK AND PRESS ENTER". Same as for my Windows 7 Ulitmate install disc too (though I did disable all other set up options for now to just strictly boot from the optical). No issue with DSL. I will google how to reformat through DSL to try and get this thing going. Hopefully I find a solution, if not, I'm definitely learning a lot about command lines as I go.

Sorry I can't guide you as I have never used DSL. Appears you have to use the Command Line to format and the link I provided might help [http://www.linuxquestions.org/questions/damnsmalllinux-42/does-dsl-have-a-format-hd-option-641884/]("http://www.linuxquestions.org/questions/damnsmalllinux-42/does-dsl-have-a-format-hd-option-641884/")

---

### Post by SuperFreak on 2014-03-17
I think , looking at my link you would use Parted to reformat. Have a look[ HERE]("http://www.gnu.org/software/parted/") and [HERE]("http://www.gnu.org/software/parted/manual/")

or if you need a Graphical interface you could create a bootable Live disc or USB of GParted and hopefully your computer will boot to it [http://gparted.org/livecd.php]("http://gparted.org/livecd.php")

Hope it works out

---

### Post by helveteca on 2014-03-19
Hello, Thank you for all your suggestions. I tried the Gparted boot, that didn't work either. So I went ahead and installed the Damn Small Linux to the hard drive and it looks like it will be my new OS for now... totally bummed about that. Going from Ubuntu to DSL is like living in a big house then having to go live in a mobile home. Haha!

I'm now left with a last resort (taking the computer to a shop) and last last resort (strapping a couple M80's to my Vaio and getting another computer dedicated to Ubuntu only).

WOAH I just thought of something... DSL is burned onto a CD, and all the other boot discs are on DVDs. Maybe I disabled something in root that allows the optical to read DVD's? I'm hoping this is my solution. If this solves the issue I'll post how it was done.

---

### Post by SuperFreak on 2014-03-19
Sorry GParted didn't work. There are other rescue discs that might help (Hiren's Rescue discue which is largely windows based but might work and several Linux based)

---

### Post by helveteca on 2014-03-24
I got it fixed now! It took about 20 hours to figure out. As I suspected before, my CD drive wasn't reading DVDs, and wasn't booting from USB either. I had to use a CD with my old Ubuntu disk burned onto it. It barely made it through that too, a lot of clicking sounds coming from the CD drive and for a moment there it was hung up at the intro. I just let it sit and it worked itself out. 

I'm so grateful, for a while there I was working with Damn Small Linux and welcomed it as my new OS, I couldn't handle it after a day, it was a little too advanced for me.

---

### Post by SuperFreak on 2014-03-25
That's great. Perhaps you could mark thread as SOLVED. Go the first post click on Thread tools at top and choose SOLVED

---

