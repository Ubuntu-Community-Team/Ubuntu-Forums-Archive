---
title: "ubuntu wont load up after software update"
date: 2013-05-11
forum: Installation &amp; Upgrades
---

### Post by crewrecline on 2013-05-11
I will state that im not computer literate.  i had ubuntu 12.4 on an acer aspire.  i did an update and after it restarted ubuntu wouldnt boot up any long and all im getting is a dos like screen.  again sorry if im not saying this stuff right.  as soon as it boots up i get the ubuntu purple screen but then it goes to black screen that says:
"stopping system v runlevel compatibility"   [ok]
"starting"                                              [ok]
"stopping cold plug devices"                     [ok]
                                                           [ok] stopping log initial device creation
                                                           [ok] starting save udev log and update rules
                                                           [ok] stopping save udev log and update rules
if someone can help i would greatly appreciate it.

---

### Post by Bashing-om on 2013-05-11
crewrecline; Hi Welcome to the forum .

Is ubuntu 12.04 the only operating system installed on your computer ?
If only one instance of ubuntu installed; Try this and advise results:
Cold boot the computer, as soon as the bios screen clears depress and hold the shift key -> grub menu;
Arrow down to an earlier kernel entry line (non recovery) and hit the enter key to boot with the selected kernel.

Can you now boot to the GUI login and login to your system ?[INDENT=2]
just try'n to help

[/INDENT]

---

### Post by crewrecline on 2013-05-11
i did what you said and i got a screen that gave me the options:
ubuntu
advanced options for ubuntu
memory test (memtest86+)
memory test (memtest86+, serial consol ######)

---

### Post by crewrecline on 2013-05-11
the advanced options gave me entries that look like (ubuntu, with linux 3.5.0-28-generic (recovery mode))

---

### Post by Bashing-om on 2013-05-11
crewrecline;

Looks like you are running 12.04.2 with the enhanced kernel, and that the inplace (re-)install removed the older kernels, no biggy.
Let's try this, in the process to get you a graphics driver loaded:
Boot to that grub menu, with the "ubuntu" entry highlighted, press the "e" key for edit mode -> kernel boot parameters screen;
arrow down to the line similar to :"linux /boot/vmlinuz-3.2.0-24-generic root=UUID=dbd69ed2-530c-4409-8f5a-a3f1ea41fc67 ro quiet splash $vt_handoff" ; Arrow across to the terms "quiet splash" and insert the term "nomodeset" - with out the quotes-;
Key combo ctl+x to continue the boot process. 
Do you now boot to the GUI -- degraded graphics ??

Yes ? If so lets see about installing a graphics driver:
key combo ctl+alt+t yields a terminal, post the out put of terminal codes:
```
lsb_release -a
 uname -r
lspci | grep VGA
lspci -nnk | grep -iA3 vga
```
Depending on the output is what is advised for the next step.[INDENT=4]
A tale in the telling

[/INDENT]

---

### Post by crewrecline on 2013-05-11
alright so it booted to a screen that has blue lines going vertically across the screen

---

### Post by Bashing-om on 2013-05-11
No usable GUI desk top ?
Else will have to go to a "text" login to get the info.[INDENT]
stepp'n small

[/INDENT]

---

### Post by crewrecline on 2013-05-12
this is the furthest it has gotten.  not sure if this is what your looking for or not.
[IMG]http://server.myspace-shack.com/d21/photo 8.jpg[/IMG]

---

### Post by Bashing-om on 2013-05-12
crewrecline; Hey.

Yeah, that will work as you have come up with a means to xfer the info back to us.

At that login prompt go ahead and enter your user name <enter key> and then enter your password <enter key>, nothing will be reflected back to the screen when password is entered (security reasons),

In that terminal do these terminal commands:
```

lsb_release -a  
uname -r
sudo lshw -C display
lspci -nnk | grep -iA3 vga
``` so we know what we are working with - version,card and driver info.[INDENT=2]
ain't no step for a stepper

[/INDENT]

---

### Post by crewrecline on 2013-05-12
alrighty
[IMG]http://server.myspace-shack.com/d21/photo 9.jpg[/IMG]

---

### Post by Bashing-om on 2013-05-12
crewrecline; Good job !
Sorry for delay in response, got busy elsewise.


At this point I do not know.
Here's the situation:
Running (as you know) version 13.04 with kernel 3.5.0-28 // 64 bit 
You are running Intel for a graphics card that is well supported out of the box by ubuntuu
The driver loaded is for Intel (i915 driver)
(Intel does not honor the "nomodeset" kernel boot option ->blue lines)

So, after this leap forward you just completed, back to baby steps.

From the text login -> what results in terminal code
```
sudo service lightdm start
``` Post back the output, looking for indications of errors.

Be advised I Have not installed 13.04 to this time and thus have not had an oportunity to investigate it --- Soonest I go to town I will pick up some DVDs and get it installed -- I expect the lightdm command is still valid to initiate the desk top from the command line interface.

Pending is looking at the log files for indicative errors.[INDENT=2]
we be look'n

[/INDENT]

---

### Post by crewrecline on 2013-05-12
its no problem i really appreciate someone helping me, wish i was abit more computer smart tho.  but this is what i got when i typed that in
[IMG]http://server.myspace-shack.com/d21/photo 10.jpg[/IMG]

---

### Post by Bashing-om on 2013-05-12
crewrecline;
It is my pleasure to assist (and teach)...participation in the open source movement.

UHHH... back up --your last screen shot -> you were not logged in.

Get to the grub menu, edit in "text" in the kernel boot parameter command line, log in at the terminal and post the out put of terminal command: -- this method is non-persistent, must be re-done each boot--.
```
sudo service lightdm start
``` just to see what happens when you attempt to start the desktop environment.[INDENT]
try'n to step out

[/INDENT]

---

### Post by crewrecline on 2013-05-12
it says
lightdm start/running, process 1707

---

### Post by Bashing-om on 2013-05-12
crewrecline;

Well that is better than I anticipated/// OK ...

From that exact point (after issuing the lightdm start command) do:
key combo clt+alt+f7 
That takes you to the GUI login;
login there and see if you can get to the GUI desk top... what does it look like ?
to return to the terminal -> key combo clt+alt+f1
[INDENT=2]
it is what it is

[/INDENT]

---

### Post by crewrecline on 2013-05-12
alright after issuing the lightdm start command it takes me straight to this, on the right side of the screen it says [ok] for all of them
[IMG]http://server.myspace-shack.com/d21/photo 11.jpg[/IMG]
i hit ctl alt f7 and nothing happens
when i go back to the terminal it looks like this
[IMG]http://server.myspace-shack.com/d21/photo 12.jpg[/IMG]
i also tried ctl alt f7 here too but it takes me back to the first picture

---

### Post by Bashing-om on 2013-05-12
crewrecline;

IDK, but something here is definitely not kosher, With the invocation of the second start lightdm - as one is already started - I would have expected an advisory that it was already running .

I hate to run you through hoops. but let's check from the beginning.
shut down and start all over from the beginning:
terminal code to shut the system down safely:
```
sudo shutdown -P now
```
wait a minute or so and fire the box back up
get to the grub menu, do the "text" insert routine;
login to that terminal
```
sudo service lightdm start
```
only run this command one time
now key combo ctl+alt+f7

Still no GUI login ?[INDENT]
Again I say I am not certain that the "lightdm start" command remains valid in 13.04 version ... someone running 13.04 test and advise please ...



[/INDENT]
[INDENT=3]poke'n to see what haps

[/INDENT]

---

### Post by crewrecline on 2013-05-12
still no GUI login

---

### Post by Bashing-om on 2013-05-12
crewrecline;
It is now time to look at some log files;
It may be most useful to look at the Xorg log file first.
```

sudo apt-get install pastebinit
cat /var/log/Xorg.0.log | pastebinit
```
Copy and paste the URL from the last command into your next post.

I am going to be away from the keyboard for a spell,- quality time with my better half -  I will return this evening.[INDENT=2]
try'n to see what is not going on

[/INDENT]

---

### Post by crewrecline on 2013-05-12
alrighty, this is what i got
[IMG]http://server.myspace-shack.com/d21/photo 13.jpg[/IMG]

---

### Post by Bashing-om on 2013-05-12
crewrecline;
I was totally unprepared for that kind of output.. much deeper problems than a graphics issue....
lemme look over this slopyation some what and get back at you with more questions !
[INDENT=2]
I'll be baaacck

[/INDENT]

---

### Post by crewrecline on 2013-05-12
alright thx

---

### Post by Bashing-om on 2013-05-12
crewrecline; OH Dear !

Revised situation:
Several new packages are semi-installed and trying to install dependencies for older versions (yukk)
Several old packages remain and trying to install the newer versions (package manager is screaming )
The graphics installation is likely good and the desktop environment is hosed;[INDENT]gnome-control center
gnome-panel
gnome-shell
[/INDENT]
just for starters.

My considered advise at this stage:
Save your data, download the install .iso, burn that .iso to disk, and do a clean install. Even if we were to repair what we know of in the current system, doubts would always remain of it's stability.
Repairing would be a long process on a largely unknown file system - lot's of changes to the 13.04 version - and, as much faith as I have in the package managers abilities, I have doubts that it can cope with all the problems in this type of situation.

It is your call. If we proceed to fix this install, it will be a in depth learning process on both of our parts. This process will be long and entail a bit of trial and error (maybe lots - 13.04 !) with no guaranty of ultimate success.

Once your data is backed up, and an installDVD in hand, it is but a matter of 30 minutes to be up and running on 13.04.


[INDENT=2]so What are we going to do ?  
[/INDENT]

---

### Post by crewrecline on 2013-05-12
just to avoid headache on your part id rather just do the new install.  problem is ive tried to burn those types of files to a disk before and it never worked.  i was going to try pearl linux awhile back but i was never sure how to burn it to a disc properly or even install it.  it is fairly sad that i cant do even this much when im going to be majoring in computer information systems.

---

### Post by Bashing-om on 2013-05-12
crewrecline;

To get you over the concern about burning a liveDVD: Later releases(ubuntu) must be burned to DVD - they have gotten that big.
Get the .iso file here:
[http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/)
md5SUM :
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Tutorials on how to burn:
[https://help.ubuntu.com/community/MakeALiveCD/DVD/](https://help.ubuntu.com/community/MakeALiveCD/DVD/)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Follow the simple prompts in the install wizard to install, and done !

My method:
D/L the .iso file, verify the md5sum, burn to disk at lowest speed, boot the liveCD, verify (menu option) the disk integrity, make any changes to my partitions in the liveCD with GParted[not required in a simple wizard guided install], install to hard disk....and done.

Remember, we are here to assist and get you over any hurdle.[INDENT=2]
best regards

[/INDENT]

---

### Post by crewrecline on 2013-05-13
thank you but do those work for windows?  at the moment im using a windows 7 computer

---

### Post by Bashing-om on 2013-05-13
crewrecline; 
Dual booting with Windows, one has to jump through a couple more hoops. As you already have ubuntu set up on that same system, should not be a big deal. Make sure you know what partition is what system - Windows prefers to be in that first partition.
To verify partitions on all disks; terminal command:
[code[sudo fdisk -lu[/code]
Windows is marked NTFS and ubuntu is ext4 :
These tutorials will help:
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/)
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)
See post #13
[http://ubuntuforums.org/showthread.php?t=2126166&page=2](http://ubuntuforums.org/showthread.php?t=2126166&page=2)

No luck to it, just prior prudent planning -> anything can happen, always a good practice to back up ALL data, even Windows' and if you place a lot of value on your Windows, be prepared - just in that eventuality - to restore it also.

Any other questions or concerns, please ask ! I want that you are comfortable doing this.
[INDENT=2]
all the better, fresh start
[/INDENT]

---

