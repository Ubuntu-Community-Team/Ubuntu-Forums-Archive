---
title: "Installation stops after graphical loading screen"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by Hyuuga on 2006-12-01
trying to install 6.10

When i try to install (i tried both install options) it loads for a while before it gives me a non-graphical screen saying:

> busybox v1.1.3 (debian 1:1.1.3-2ubuntu3) buildt-in shell (ash)
type in "help" for a list of available commands

/bin/sh: cab't access tty; job control turned off
(something)

the "something" is something i can't remember entirely. but it made no real sense to me and it won't let me type in help to see list of available commands.
my question is; why the hell am i getting this? and how can i bypass it and install???

btw i got a 232gb SATA harddrive together with an 80gb ATA harddrive.

thanks to having to reinstall windows for the 6th time this year i had to reinstall windows on the 232gb. this somehow also uninstalled ubuntu which was on the 80gb of a format windows can't read. after this windows hasn't even found the harddrive so i can't reformat it, if a lack of non-sata harddrive is the problem.

---

### Post by Hyuuga on 2006-12-02
sorry to bump, but i really need an answer

---

### Post by MattiasJow on 2006-12-02
I have the exact same error, can't do much if i can't even boot the thing, tried several images. and cd isn't defect.

---

### Post by Hyuuga on 2006-12-02
yeah, i hope someone will help soon, i wanna install ubuntu!!
maybe i should try installing Kubuntu or Xubuntu?

---

### Post by darryn.smith on 2006-12-02
I get the same thing. 

My hardware is:

MSI K9NGM2 w/ AM2 4200+
SATA drives
and Nvidia 6600 PCI-E (onboard disabled) 

Perhaps the SATA is causing the troubles.   Do you guys also have SATA drives?

---

### Post by darryn.smith on 2006-12-02
solution for me..  (and I should have tried this 1st since I had this before with Suse..)    acpi=off  

Hopefully thats the only bug in the install.  

Enjoy. 


(btw I'm using  AMD64 (x86_64) 6.10 I should have mentioned that before)

---

### Post by Hyuuga on 2006-12-02
ehh, i'm sure there's an option for that IN linux, but is there in windows? and if not how do i turn acpi off? i'll let you know if i figure it out myself.
oh and i got a pentium 4.

---

### Post by darryn.smith on 2006-12-02
When you boot from the install media.. 

You'll get the list of options..  Start or install Ubuntu etc.. etc etc.. 

At the bottom you'll see F6 Other Options

Press F6. It'll bring up the Boot Options. 

backspace and take out the quiet (only so you can watch it start-up helps in finding out why something isn't working) 

on the same line enter   acpi=off 

press enter and it'll boot.   If it boots nicely then that was the problem. 

AFTER your done the install, you'll need to make that change permanent. So edit this file:

open a terminal type :

sudo gedit /boot/grub/menu.lst

add acpi=off     to the kernel lines at the bottom of file .. 

example:

kernel       /boot/vmlinuz-2.6.17-10-generic root=/dev/sda1 acpi=off ro single

(your line might be slightly different, but you can see where to put that acpi) Add it to both kernel lines. (recovery mode & standard)

That should do it. 

Enjoy.

---

### Post by notatoad on 2006-12-02
AAGH!!!!  i was having this problem so i tried doing acpi=off and deleting quiet.  now my usb devices don't work (no keyboard) and my sound doesn't work, and i still have no operating system.  help please

---

### Post by Hyuuga on 2006-12-03
could you please be more specific? trying to backspacing just "quiet" then writing in acpi=off in it's place did not work. neither did backspacing everything that came after quiet as well and then putting in acpi=off. please write exactly what text should be written under "other options".

sorry to be such a trouble.

edit:
and i only see one line under "other options" so how could i *not* write it on the same line?

---

### Post by darryn.smith on 2006-12-03
notatoad - It sounds like more of a Bios issue with your system. Check in your bios to see if USB (Keyboard & Mouse) support is turned on or not. Also if you check google you'll find many people have had the same troubles. 

The reason you remove quiet & splash from the boot options is so you can see where the system is hanging. 

After pressing F6

Boot Options ._size=1048576 root=/dev/ram rw acpi=off

if thats not working try acpi=force

press enter & it should boot :) 

(your size might be different as I'm using amd version, don't change yours.)

---

### Post by Hyuuga on 2006-12-04
edit: oops sorry, i somehow missed the last post.
i'll try it. and that size is the RAM of your computer not anything cpu-related, btw. i got the same size :P (and intel pentium 4)

edit2:
damn it didn't work. I'll google it then

edit3:
only option i found was to try the alternative install *or* another linux distro. If the alternate install doesn't work, which distro other than ubuntu is kindest on linux newbies?

---

### Post by darryn.smith on 2006-12-04
Re ram, I believe it's just a default setting. As that computer has 2GB's (not 1) :) 

No flames please :) 

Anyhow..  I have to say.. I love OpenSuse 10.1  (tho I did have to add acpi=off on that one as well)  HOWEVER with the recent MS / Novell deal I'm not too impressed with Novell these days. 
I've used GNU/Linux for 10+ years. Every couple of years the distro leader seems to change. 

2006 is not the year for Fedora.
Fedora Core 6 isn't all that impressive in my opinion. In fact perhaps it would have been better to skip 6 all together. 

Edgy - Hmmm  well, I've already had some annoying bugs.. My mouse for instance will move but the UI is unresponsive to the clicks.. this comes and goes. I haven't been able to figure out what package is causing this. There's nothing in the logs to even give me an idea..   LET me tell you that it really sucks when your working on something.. and you are forced to reboot.  

Suse 10.1 is excellent. Wonderfully organized desktop, well integrated. It's one thing I think ubuntu should DIRECTLY adopt. A helpful note.  DO NOT use the package manager that comes with 10.1, instead use smart. (google smart package manager, then download the rpm for latest version. And you can't sudo smart --gui. Instead open a terminal and type su then at root prompt smart --gui) I still use Suse 10.1 on my Thinkpad everyday. I'll move away from that when I have my desktop working perfectly.  DAMN MS and that dumb Novell exec. I might create my own distro a combination of Suse 10.1 and edgy, the layout of 10.1, the configuration files, but the core of edgy. (mostly talk tho since I'm quite busy lol) 

Linspire - Well..  it's perfect for the user that doesn't want MS but isn't really interested in Linux either. In my opinion it's good for out of the box use, but you never really learn anything and hence you'll never really be able to move on to a more hands on Linux.  Again just my thoughts. It's perfect for my family. They have no real idea whats happening when they click things. I'd recommend it to non-computer savy people. 

Mandriva - Actually not too bad. I can't say much about it. I've only played with it a few times. I had no real problems to report. It didn't capture me, but it did gain a certain level of respect. 

There's ton's more I've installed and played with.  And no offense to all the distro's I haven't listed. There are many. 

I guess the real question and often the one that's never really asked. What do you intend to use your computer for? That really has an impact on the distro's you should consider. And your views on close-source usage. (like nvidia binary drivers, flash, adobe etc)  

I use my laptop for business. So number one is easy of use and flexibility.  I have huge collections of pdf, documents etc. So Suse fits like a glove. The Z60T has a crap video chipset so XGL and other intense graphics aren't important. (tho 10.1 has xgl out of the box) My Desktop is my play around and do everything computer, the video card is Nvidia 6600GT, AM2 4200+ etc. So I'd love the extra desktop effects. AS cool as they are I still tend to leave them off. It's not perfectly stable, little bugs like incorrectly sized mplayer windows, or sometimes rarely recently the loss of the boarders.  And the wobbles get boring :) The effects are very cool for the friends. But serve little practical use right now. Who actually watches a video under a semi-transparent terminal window? I'd be distracted and end up closing the terminal to  watch the video and getting nothing done. 
On my asterisk box it's FreeBSD, tho could just as well be Fedora (server config), Redhat, Debian etc.  

 Two people I REALLY  hope ubuntu would hire...  or at least directly offer a position..  Nat Friedman along with Miguel de Icaza. Those two would help Ubuntu in the corporate desktop world. I admire Nat. 

Well enough said. :)

---

### Post by drtvasudevan on 2006-12-04
> **Hyuuga said:**
> edit: oops sorry, i somehow missed the last post.
edit3:
only option i found was to try the alternative install *or* another linux distro. If the alternate install doesn't work, which distro other than ubuntu is kindest on linux newbies?

i have the same problem.
it is a q of hardware incompatibility.
(what system specs? mobo?)
so far only fedora core 6 seems promising.
downloading now.
will let you know later if it got installed.
ps: and that something is initramfs

---

### Post by Hyuuga on 2006-12-05
argh. the alternative install works. but the bios insists on not finding the 80gig ATA 2 (IDE) harddrive i want to install it on...
edit:
hehe yeah i figured that it was initramfs. seen that screen so many times now i got an eyesore :P

---

