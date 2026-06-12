---
title: "Ubuntu Wont Work At Alll!!!!!!!!!!!!!!!"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by gnrathon on 2008-02-20
I am a noobi so let me try my best

Okay so i got the Live CD
i booted it up and i liked what i saw
so i decided to install it
i decided to let it delete all my data
i ran the installation with no problem
then i rebooted the computer and 
.....
thats where it sucked
it would load ANYTHING!!!!!
all i would see is
Grubs loading..... 1...2....3
then
 _ a white cursor would just sit there and blink with no response
i tried installing it over and over but every time that stupid cursor would mock me:(

and i cant download and burn a CD cause i dont have a burner
and cant afford one
[COLOR="DarkRed"][B][COLOR="Red"][U][SIZE="5"]
PLEASE someone help ME!!!!!!!!!
I REALLY NEED MY COMPUTER!!!!!!
[/SIZE][/U][/COLOR][/B][/COLOR]
I have no idea what to do!!!:confused:

EDIT: oh and the CD doesnt have any flaws
already checked

---

### Post by coastdweller on 2008-02-20
Have you only one drive in the system? I would dig around the bios and see if you have "RAID" mode set instead of Native mode.

Who knows really, just stabbing at it here.

---

### Post by gnrathon on 2008-02-20
> **coastdweller said:**
> Have you only one drive in the system? I would dig around the bios and see if you have "RAID" mode set instead of Native mode.

Who knows really, just stabbing at it here.

I dont know what any of that stuff is:confused:

---

### Post by Partyboi2 on 2008-02-20
try [restoring grub]("http://ubuntuforums.org/showthread.php?t=224351") and see what happens

---

### Post by gnrathon on 2008-02-20
> **Partyboi2 said:**
> try [restoring grub]("http://ubuntuforums.org/showthread.php?t=224351") and see what happens

did it 
no effect at all

what the hell happened:confused:

---

### Post by Partyboi2 on 2008-02-20
what are your system specs?

---

### Post by Cannaregio on 2008-02-20
> **gnrathon said:**
> I am a noobi so let me try my best
...
it would load ANYTHING!!!!!
all i would see is
Grubs loading..... 1...2....3
then
 _ a white cursor would just sit there and blink with no response


I think it could most probably be a graphic card problem

1) What's your graphic card?
2) CTRL+F4 brings you to a tty? If so, you can fix everything chnging gdm to gdm- so that it does not start and with 
sudo dpkg-reconfigure (-phigh)
xserver-xorg
3) Can you boot with your own Ubuntu live CD?
4) Can you boot with a gparted or knoppix live CD?
5) ALT+SYSRequest+ R S E I U B does or does not reboot?

---

### Post by gnrathon on 2008-02-20
> **Cannaregio said:**
> I think it could most probably be a graphic card problem

1) What's your graphic card?
2) CTRL+F4 brings you to a tty? If so, you can fix everything chnging gdm to gdm- so that it does not start and with 
sudo dpkg-reconfigure (-phigh)
xserver-xorg
3) Can you boot with your own Ubuntu live CD?
4) Can you boot with a gparted or knoppix live CD?
5) ALT+SYSRequest+ R S E I U B does or does not reboot?

Dell Optiplex 320
Intel Celeron D 3.06 GHz
ATI Radeaon Xpress 1100
512 ? MB RAM
Yes i can run the Live CD
30 GB Hard Drive

Grub wont work at all

EDIT: Now i get an error message
saying:
ERROR 15!


**_[COLOR="Red"]HOW CAN I FIX THIS PROBLEM!!!!![/COLOR]_**

---

### Post by froy02 on 2008-02-21
If you can boot with live cd post the contents of your /boot/grub/menu.lst file.  Did you by any chance edit the file?

---

### Post by gnrathon on 2008-02-21
> **froy02 said:**
> If you can boot with live cd post the contents of your /boot/grub/menu.lst file.  Did you by any chance edit the file?

no i didnt
i dont even now what that is

---

### Post by confused57 on 2008-02-21
Open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

If you get a grub boot menu(you may need to press "Esc" during boot up when prompted), can you boot into Recovery mode?

---

### Post by gnrathon on 2008-02-21
> **confused57 said:**
> Open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
-l is a lowercase "L"

If you get a grub boot menu(you may need to press "Esc" during boot up when prompted), can you boot into Recovery mode?

no

nothing will work:(

---

### Post by confused57 on 2008-02-21
It seems the Dell Optiplex 320 isn't very compatible with Linux, you may want to check out post #4 in this thread:
[http://ubuntuforums.org/showthread.php?t=409345](http://ubuntuforums.org/showthread.php?t=409345)

It appears that you need lilo to boot Ubuntu on this particular pc.

---

### Post by gnrathon on 2008-02-21
> **confused57 said:**
> It seems the Dell Optiplex 320 isn't very compatible with Linux, you may want to check out post #4 in this thread:
[http://ubuntuforums.org/showthread.php?t=409345](http://ubuntuforums.org/showthread.php?t=409345)

It appears that you need lilo to boot Ubuntu on this particular pc.

whats lilo
is it an alternitive to grub
and how do i go about apply and instaling it?

---

### Post by loboc on 2008-02-21
A Reinstall wont cost you anything so why not redo it with a /boot partition This happened when I got a huge new hardrive and this fixed it.

Fire up the installer and when you get to the partiton editor portion go into manual mode.

Delete all the existing partions

Create a boot partition at the from of the disk of 128 megs this is where grub will reside

type: ext3
mount point /boot

Creat a swap partion of 756 MB 0r 1 Gig to match your 512 megs of ram

type swap


Partition the rest of the disk as ext3 mount point /

Continue the Install

---

### Post by loboc on 2008-02-21
[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/partitioning.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/partitioning.html)

---

### Post by confused57 on 2008-02-21
> **gnrathon said:**
> whats lilo
is it an alternitive to grub
and how do i go about apply and instaling it?
Yes, lilo is an alternate bootloader...this howto may be easier to follow to install lilo to your hard drive installed Ubuntu, using the Ubuntu live cd:
[http://users.bigpond.net.au/hermanzone/p4.html#Install_Lilo_from_a_Linux_LiveCD](http://users.bigpond.net.au/hermanzone/p4.html#Install_Lilo_from_a_Linux_LiveCD)

You might want to check how your hard drive is recognized, with the command I gave you earlier:
```
sudo fdisk -l
```

---

### Post by gnrathon on 2008-02-21
> **loboc said:**
> A Reinstall wont cost you anything so why not redo it with a /boot partition This happened when I got a huge new hardrive and this fixed it.

Fire up the installer and when you get to the partiton editor portion go into manual mode.

Delete all the existing partions

Create a boot partition at the from of the disk of 128 megs this is where grub will reside

type: ext3
mount point /boot

Creat a swap partion of 756 MB 0r 1 Gig to match your 512 megs of ram

type swap


Partition the rest of the disk as ext3 mount point /

Continue the Install

didnt work:confused::(:confused::confused::confused::confused:

**[SIZE="5"][COLOR="Red"]_what else can i do!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!_[/COLOR][/SIZE]**

---

### Post by confused57 on 2008-02-21
Here's a Google search for Dell Optiplex 320 linux:
[http://www.google.com/search?hl=en&q=Dell+Optiplex+320+linux&btnG=Google+Search](http://www.google.com/search?hl=en&q=Dell+Optiplex+320+linux&btnG=Google+Search)
There seems to be incompatiblities with your pc and linux, but you have an advantage in that the live cd worked.

The best possible solution I saw was to try installing lilo, which the last link I gave you shows you how to do...it would probably be a matter of using the Ubuntu live cd and copying & pasting the commands, but substitute your Ubuntu partition in place of the examples given.  It's not going to be easy and may or may not work, but it's going to take some effort on your part.

---

### Post by daehenoc on 2008-03-05
As posted in your other thread:

For a Dell Optiplex 320, you have to use the alternate installer CD, as well as follow the instructions I have just put at the bottom of this page:
[https://wiki.ubuntu.com/DellOptiplex320](https://wiki.ubuntu.com/DellOptiplex320)

You will wind up with a computer that uses the Lilo boot loader, and you have to have a copy of the Ubuntu alternate install disc, but you get a working system!

---

