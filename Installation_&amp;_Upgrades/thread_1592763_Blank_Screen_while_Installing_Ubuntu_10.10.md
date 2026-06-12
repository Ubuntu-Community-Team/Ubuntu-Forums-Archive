---
title: "Blank Screen while Installing Ubuntu 10.10"
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by jonikang on 2010-10-10
Hi,

I am having issues with Ubuntu 10.10 GA 64bits (maybe with 32bits as well), where the screen goes blank during the installation.

I set the nomodeset = true for the installation, and i can get passed the installation. However, I still get blank screen upon rebooting the pc (after the installation). I seem no way to ssh into the machine as sshd is not installed by default. 

tried Crtl-Alt F2, doesn't bring back the screen as well. I know the system boots into the desktop environment, but I just can't see it on the screen.

Does anyone here know what's happening with the display?... I have Nvidia card, and I heard that this happens to ATI as well.


Cjeers.

---

### Post by jonikang on 2010-10-11
problem solved by setting the boot kernel to nomodeset and single param. and boot to text mode screen, then install the nvidia driver. It works very well now, and I can feel the speed of light! It's so fast... :-)


Thanks again, although noone has replied my post. ^____^

---

### Post by sradhakrishna on 2010-10-11
I have the same problem. Did you have to save the nomodeset option to the kernel command line just so its available everytime it boots?

From my memory, I didn't have to do this in 10.04. 

Secondly, which version of the nvidia drivers are you using? The ones from their website?

Please let me know.

Regards,
Radha.

---

### Post by jonikang on 2010-10-12
> **sradhakrishna said:**
> I have the same problem. Did you have to save the nomodeset option to the kernel command line just so its available everytime it boots?

From my memory, I didn't have to do this in 10.04. 

Secondly, which version of the nvidia drivers are you using? The ones from their website?

Please let me know.

Regards,
Radha.


I only set the param nomodeset once in the boot kernel, so I can go to the console mode. And then I install the nvidia driver using apt-get in the console. Once done, I reboot the machine and everything lines up nicely. :-)

You can also try to "startx" while in the console, it should bring up the gnome desktop environment for you as well.

Cheers.

---

### Post by mikeraser on 2010-10-12
<hello I'm having the same problem here I select the nomodeset to install ubuntu but after its all installed I reboot the Pc and the log in screen is black and I cant do anything how do I put the nomode set on the kernel.
Thank you very much

---

### Post by dfolk on 2010-10-12
Well. I came to the right place for my problem, but these answers are too advanced for me to execute.

Take this response
"problem solved by setting the boot kernel to nomodeset and single param. and boot to text mode screen, then install the nvidia driver"

I think I can set to nomodeset via the function keys during install.

Is that what you mean here??

and you said "and single param."

I have no idea what this means

"And then I install the nvidia driver using apt-get in the console"

Could someone tell me how to do that- in simple language a non unix expert can understand?

Thanks very much for your help

---

### Post by melvb on 2010-10-12
dfolk, this is my point I made in another post, the average enduser cant do this, does not know what it means, will bin the CD.

Look at all the posts in this forum section, 99% of the fixes are beyond the knowledge of the average enduser, hence to them Ubuntu does not work. I am not trolling just frustrated that no one in a position of authority regarding Ubuntu seems to take this seriously and hasn't for years because each new version since 7.10 is equally bad.

---

### Post by orfeas76 on 2010-10-12
I am having the same problem with Ati card on my touch-enabled laptop.
Ubuntu is there, but I can see nothing after 1st restart.
I managed to connect to the internet 
I can login with SSH and make changes. But what should I change ??? Help !!

---

### Post by jonikang on 2010-10-12
Here is what I did:-


On the Grub Menu, I select 

*"Ubuntu, with Linux 2.6.35-22-generic"* and press "e" so I can edit the boot parameter. 

On 

*linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3df857a3-9c1b-4fd3-b0fc-52838eaa2023 ro   quiet splash* 

I changed it to

*linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3df857a3-9c1b-4fd3-b0fc-52838eaa2023 ro   nomodeset single*

and press 'ctrl-x'.

You should be able to see the kernel loading messages from the screen, and if I am not wrong, you will see the console screen, (no GUI).

Log in with your username, and password. Then try *startx*. If you can boot into the desktop environment, congratulations! ..., if not you gonna have to try to use apt-get to install your graphic card driver off the console.

If you are on the desktop GUI, go ahead and activate the "Additional Drivers" under System > Administration. And reboot.

Hopefully this would resolve your issue. At least, that's what I did to resolve mine.

Cheers.

---

### Post by dfolk on 2010-10-12
A thousand thank yous Mr jonikang. That is exactly the kind of highly specific info that makes it work for one of my meager skills and knowledge.

---

### Post by orfeas76 on 2010-10-12
Well I cannot startX.
So I am stuck in terminal.

If my understanding is correct you suggest to get the latest Ati-catalyst from AMD (in case of Ati graphics).
But in the [Wiki]("http://wiki.cchtml.com/index.php/10.9") it is written that latest driver is uncompatible with the kernel.
Perhaps that's the case, I have that specific latest driver because I let the wifi update packages during installation ...:-k:-k

---

### Post by AklBlue on 2010-10-13
> **jonikang said:**
> Here is what I did:-


On the Grub Menu, I select 

*"Ubuntu, with Linux 2.6.35-22-generic"* and press "e" so I can edit the boot parameter. 

On 

*linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3df857a3-9c1b-4fd3-b0fc-52838eaa2023 ro   quiet splash* 

I changed it to

*linux	/boot/vmlinuz-2.6.35-22-generic root=UUID=3df857a3-9c1b-4fd3-b0fc-52838eaa2023 ro   nomodeset single*

and press 'ctrl-x'.

You should be able to see the kernel loading messages from the screen, and if I am not wrong, you will see the console screen, (no GUI).

Log in with your username, and password. Then try *startx*. If you can boot into the desktop environment, congratulations! ..., if not you gonna have to try to use apt-get to install your graphic card driver off the console.

If you are on the desktop GUI, go ahead and activate the "Additional Drivers" under System > Administration. And reboot.

Hopefully this would resolve your issue. At least, that's what I did to resolve mine.

Cheers.
Thanks .. worked for me. 
:-)

---

### Post by orfeas76 on 2010-10-13
I forgot to say
I also used the netbook edition

---

### Post by orfeas76 on 2010-10-13
ok, today I read that Xserver cannot work well with hybrid graphics..
This is my case
my laptop is the HP tm2t and has Intel and Ati graphics.
Windows switches automatically the graphics card depending on workload (or power estimate)

---

### Post by The J on 2010-10-27
> **orfeas76 said:**
> Well I cannot startX.
So I am stuck in terminal.

If my understanding is correct you suggest to get the latest Ati-catalyst from AMD (in case of Ati graphics).
But in the [Wiki]("http://wiki.cchtml.com/index.php/10.9") it is written that latest driver is uncompatible with the kernel.
Perhaps that's the case, I have that specific latest driver because I let the wifi update packages during installation ...:-k:-k

In addition to the advice given in this topic, I also had to uninstall the "xserver-xorg-video-radeon' package and reboot before I could get into KDE.  I'm getting the new ATI Catalyst drivers now, so we'll see if those work out.

Thanks, jonikang, for posting your solution.

EDIT:  Yup, this does the trick!  So, for people who are searching for a solution to the Ubuntu blank screen on startup issue on Google and have an ATI card, here's what worked for me:

1. Perform jonikang's steps outlined earlier in this thread, stopping when you get to the command line.
2. When you get to the command line, log in and remove (I did a purge) "xserver-xord-video-radeon" package.  Now reboot and redo jonikang's steps.
3. When back at the command line, try either "startx" or, what I did, "sudo start kdm" (use "sudo start gdm" if you run GNOME).
4. In there, download the newest ATI Catalyst driver from the ATI website and get the "build-essential" and "linux-headers-generic" from the repository.
5. Install the driver, reboot, and hopefully you should be able to start right up!

---

### Post by xx58 on 2011-03-06
How and where I find Grub menu? I am so tired this smart people, who giving advise witch working, but forget explain in English - HOW?

---

### Post by thinkinghorse on 2011-04-20
Can't get into Supervisor mode! Blank screen! Can't install graphics drivers!

(I think the GRUB menu is the menu that lets you choose which operating system to boot. I never see that on my system.) Having switched of the logo that my motherboard can display on startup I now see the American Megatrends BIOS screen and after that is a blank screen with a cursor on the top left.

I have assumed I need a driver for my "Zotac nVidia Gforce GTX550 Ti 1GB" graphics card. The nVidia website has a beta driver for the 560Ti and my hope is that the cards are sufficiently similar for it to work. I downloaded the file 
NVIDIA-Linux-x86_64-270.26.run
from the nVidea website on another machine but cannot install it because I can't get a supervisor mode terminal up on my system.

I am technically proficient but have spent very little time on the Linux command line.

Of course any help would be very much appreciated. I had hoped this system would boot straight up. Oh Dear.

Thank you

Tom

My System is:

Ubuntu 10.10 Latest 64bit version on 19 Apr 2011

Asus SABERTOOTH P67 R3 
 Intel Core i5 2500K 3.3GHz
 4 x Corsair Vengeance 4GB DDR3 1600Mhz
Zotac nVidia Gforce GTX 550 Ti 1GB

OCZ 120GB Vertex 2E SSD
 3 x Samsung HD103SJ Spinpoint F3 1TB Hard Drives  
Sony Optiarc AD-5260S 24x DVD±RW
 
Antec TruePower New 750W Modular PSU

---

### Post by ozzy999666 on 2011-06-26
Hello everybody, Im having that problem and i already tried those solutions but doesnt work for me, i mean, i change the entry with "nomodeset single" and then a lot of words appears (like in previus versions of Ubuntu) but then, it stops and freeze my laptop... the last line of text that appears is somtehing like "NET: registered protocol Family 1"......

I Really want to use Ubuntu... PLEASE HELP ME!!!!:(:(:(:(

EDIT: I have a Toshiba A655D-S5172 ATI graphics...

---

### Post by reauxbeauxboy on 2011-06-26
[QUOTE=thinkinghorse;10697845]Can't get into Supervisor mode! Blank screen! Can't install graphics drivers!

[I]...I can't get a supervisor mode terminal up on my system.

I am technically proficient but have spent very little time on the Linux command line.[/I]

So, I'm assuming that what you're saying is "I know HOW to get a terminal window up in Supervisor mode or issue commands as a supervisor, but my system isn't letting me." -- is that a correct assumption?

If it's not a correct assumption -- you should try "sudo" (without the quotes) before the command you're trying to 'run as' a Superuser.  For example, if your user wanted to use StartX, they would just type StartX and bring up the GUI -- but if you want the GUI to be "run as" the Superuser, then you would type "sudo StartX" and hit enter.  

Effectively (somebody correct me if I'm wrong) "sudo" means "Superuser Does ..."  Which is effectively the same but much simpler to execute than all those horribly syntaxed "RunAs COMPUTER\Administrator "C:\Windows\System32\Notebook.exe" < sometextfile.txt commands in Windows.  NOICE!

---

