---
title: "Doesn't Detect Network Card"
date: 2005-06-23
forum: Installation &amp; Upgrades
---

### Post by Ennead on 2005-06-23
I just loaded Ubuntu, and so far everything seems to be working except my network card.  During the install, it said that I might need to install a different driver, so after retrying several times, I skipped that part.  The card is a 3Com Etherlink III ISA, and the whole system is fairly old (AMD K6 550MHz CPU).  

How do I load a new driver, and where can I get it? 

Also, when I installed Ubuntu, I was never asked for a password for my root account, but now I can't get into my root account because it asks for a password and I don't know the password.  Any Ideas?    ](*,) 

If someone could just point me to the right documentation, that would be a great help.  I haven't been able to find it on my own.  Thanks!

---

### Post by alaithea on 2005-06-23
I'm new to this stuff myself, so I can't help with the network card, but check out the following link, with regard to the root account in Ubuntu.
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by mingus on 2005-06-24
[QUOTE=Ennead]I just loaded Ubuntu, and so far everything seems to be working except my network card.  During the install, it said that I might need to install a different driver, so after retrying several times, I skipped that part.  The card is a 3Com Etherlink III ISA, and the whole system is fairly old (AMD K6 550MHz CPU).  

How do I load a new driver, and where can I get it? [/QUOTE]

it's 3c509 . . .

[http://ubuntuforums.org/archive/index.php/t-16694.html](http://ubuntuforums.org/archive/index.php/t-16694.html)

and this one because it may need tweaking because it's ISA

[http://ubuntuforums.org/archive/index.php/t-4396.html](http://ubuntuforums.org/archive/index.php/t-4396.html)

Re root password:  If it hasn't been set, in a terminal do:  passwd root

PS.  Google and forum search is your friend

---

### Post by Ennead on 2005-06-25
THANK YOU!  Alaithea and Mingus.  Thank you.  Your advice worked, and I am now online via my ISA card.  I can see from the links you provided that I have a lot to learn about the root account, but I finally have my first fully functional Linux machine, and I am positively THRILLED!   \\:D/  \\:D/

---

### Post by mingus on 2005-06-25
happy to have been of some help . . .

a quick question back if you don't mind . . .

how is your 550MHz K6 performing?  and how much RAM do you have?  I'm thinking about putting Ubuntu on a similar box I've got.

---

### Post by cvmostert on 2005-06-25
Hi mingus, it looks like you have been loads of help to install a 3 com ethernet card..

i have the same card and just installed ubuntu.. i tried the sudo modprobe 3c509 and not even a flicker of light on my modem.. i have cable.. i had another linux on beforehand and it worked fine....

can you think of anything else that could have gone wrong?

thank you
 :-x

---

### Post by cvmostert on 2005-06-25
I have to boot with a knoppix live cd to get on the internet... knoppix kde configures the network fine and i can surf fine... but... :-) i want to use ubuntu!
take care,
chris

---

### Post by mingus on 2005-06-25
if the 2 links above don't help, post back the outputs of

$lspci

$ifconf

BTW, a common misunderstanding is that because something works with the Live-CD it will automatically do so immediately after installation.  Not so.  The Live-CD kernel has just about all hw detection compiled into it, like the W$ install setup.exe pgm.  The installation will config what can be straightforwardly setup, but for old ISA or new video, etc. that require special drivers, not so - that is a post-install step (again, just like W$, unless you do the F6 thing during install).  The good news is that if the Live-CD sees it, then it can be installed & configured after install.

---

### Post by cvmostert on 2005-06-26
Hi there, here are the stuff you asked for... hope we can figure something out...

chris@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:352 errors:0 dropped:0 overruns:0 frame:0
          TX packets:352 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:30370 (29.6 KiB)  TX bytes:30370 (29.6 KiB)

chris@ubuntu:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
0000:00:01.0 PCI bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
0000:00:07.0 ISA bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:0c.0 Multimedia audio controller: Yamaha Corporation YMF-724F [DS-1 Audio Controller] (rev 03)
0000:00:0e.0 SCSI storage controller: LSI Logic / Symbios Logic 53c875 (rev 04)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV4 [RIVA TNT] (rev 04)



that is while the cable is connected... 

 :-|

---

### Post by mingus on 2005-06-26
the driver has not been installed . . . try $sudo modprobe 3c509

now when you do $lspci you should see a line ref'g to a 3Com adapter or controller

and do $ifconfig and you should see a new device it will prob be eth0 or eth1

now go to System/Administration/Networking to configure it depending on how you connect to the net (DHCP, static, etc)

if this works, open a terminal and do $sudo gedit /etc/modules
Add 3c509 and save the file
reboot and you should be there

---

### Post by cvmostert on 2005-06-26
Hi, me again, i tried what you said and funny enouch it does not change the lspci or ifconfig output? I am using another live cd... puppy, i had to configure the 3com card here aswell and it worked fine... with 3c509...

on the system with ubuntu... i even tried adding the 3c509 command and  saving at the end of the modules list.

still nothing... really do not know what the problem might be... 

hope we get to the root of the prob... can there be another interference? just wondering...
 ](*,)

---

### Post by mingus on 2005-06-26
[QUOTE=cvmostert]Hi, me again, i tried what you said and funny enouch it does not change the lspci or ifconfig output? I am using another live cd... puppy, i had to configure the 3com card here aswell and it worked fine... with 3c509...

on the system with ubuntu... i even tried adding the 3c509 command and  saving at the end of the modules list.

still nothing... really do not know what the problem might be... 

hope we get to the root of the prob... can there be another interference? just wondering...
 ](*,)[/QUOTE]

You need to do this from inside Ubuntu, not a live-cd.

---

### Post by cvmostert on 2005-06-27
I did it from inside ubuntu and not after booting from the live cd.  :???: 

only after it did not work... I started to play with live cd's. The live cd was just to make sure that the network card actually worked.

bottom line... i did it from inside ubuntu as you said i should. nada...

---

### Post by cvmostert on 2005-06-27
ha ha... clever me... i thought there was something i left out!...


>>>now go to System/Administration/Networking to configure it depending on how >>>you connect to the net (DHCP, static, etc)



sorry and thank you... i am online with ubuntu now... :-)

great stuf... NOW the fun and games start.... \\:D/

---

### Post by mingus on 2005-06-27
Your welcome and . . . congratulations!

---

### Post by Ennead on 2005-06-27
To cvmostert : 

I didn't mention this earlier because it didn't seem important at the time, but I couldn't get sudo modprobe to work on my machine either.  I assumed I was doing something wrong and just went ahead and edited /etc/modules as directed.  It still didn't work until I also edited the ethernet connection under /system/admin/networking/network settings, also as directed above.  I double-clicked the ethernet connection  text area (which said that it was disabled, checked the box for "this device is configured" and changed the configuration to DHCP.  At that point, my card started working, and my ethernet connecton is now declared to be active.  BTW, I have DSL.

To Mingus:

I have 320MB RAM (256+64) and it's been running great.  True, I have to wait a few seconds for most things, but it's worth it to me to have a Linux machine.  This computer was previously running Win98, and THAT was so slow that nobody wanted to use it.  That's how I got the machine.  As for the Ubuntu, a friend of mine gave me a CD about the same time as I acquired the hardware, and the rest is (recent) history.

Thanks for the clarification about the live CD vs the install CD.  I was under that misconception, too, and I'm happy to know the truth about it.

---

