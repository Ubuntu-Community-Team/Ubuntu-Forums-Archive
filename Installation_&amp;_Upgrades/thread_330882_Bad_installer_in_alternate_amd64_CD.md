---
title: "Bad installer in alternate amd64 CD"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by coltrane on 2007-01-03
In the install process on the ubuntu-6.10-alternate-amd64 CD it asks for the normal user for non-administration tasks and then for it's password, there is no password asked for the root  (this is not the same as the graphical installer). The install resumes then completes, But when I log in as normal user the display freezes. however i can log-in to the GUI from recovery mode as root but never as normal user, I apparently don't have any permission.
The odd thing is my root folder has been made my home folder, I get shell prompts like this:-

root@x1-6-00-31-c8-90-ac-65:~# 

and for the other

normaluser@x1-6-00-31-c8-90-ac-65:/root$
                                                                          ^note the /root$.
my system is (if it helps) is..
ASUS A8N-SLI
2x GeForce 6600GT's
250G sata II
1 Gig DDR400
amd 3200 

Hope I've not been too vague.

---

### Post by coltrane on 2007-01-04
bump: Has anyone else had this problem with the ubuntu-6.10-alternate-amd64 CD. Can't figure out why it's not setting up users properly. I've checked the CD for defects but it has none.
I can only boot into X from recovery mode.
Normally ubuntu installers ask for a user for non-admin tasks and then a root password for admin' tasks.
There also seems to be no system-bus-socket running which makes life even more difficult as i can't get into users-admin to change anything.

Please Help, or at least let me know it's not just me having this problem:???:

---

### Post by egregor on 2007-01-05
I believe I'm having this same problem as well. I've had nothing but headaches with the amd64 CD and I might just switch to x86. Trying to boot to the desktop CD (regular or safe-mode) resulted in a garbled screen with no interaction, so I had to use the alternate installer. It didn't occur to me that it hadn't asked for a root password, I thought it was just something particular to Ubuntu.

Anyway, I finally got installation to complete, but now when I log in It basically just says it's booting the kernel, activating swap, and dumps me to a command line. I couldn't even find a /etc/X11/xorg.conf, or gdm binary anywhere!

amd x2, geforce 7800 gt.

---

### Post by coltrane on 2007-01-05
Thanks for the reply, I thought it was only me having this problem.

I don't understand how as a normal user ($), I can never login to X. I've gone through all the admin files i can find such as passwd, shadow, and group etc... and compared the with my other PC that does work and can't find any difference whatsoever, yet the 64 bit PC still says i have no permission to log into X, where on earth is it getting such information?

I tried using the "install a text based system"  (which only installs a Command Prompt type system), this seems to set up the users properly and I then get the proper :~$ instead of :/root$
but when I install gdm and xorg I stall can't login to X, I still have no permision.

I can only get X to work with the first install option, and then booting into recovery mode.

if I try and boot with the normal kernel it will get to the login screen then let me type my username and then everything freezes no mouse nothing](*,) 

It can't be hardware related as X works like a dream in recovery mode, but a nightmare otherwise.:mad: I'm using X now as I type this:confused: 

The only 64bit distro' i've got to work is Gentoo, but it's not a practical operating system for me.
I also tried Fedora core 6 (which shuts down the PC when it starts the firewall:confused: )
and OpenSuse 10.2 (which is also hopeless).

Please can someone put me out of my misery:( 

How can I get permission to login to X????:confused:

I got the D-bus working by following this thread [http://www.ubuntuforums.org/showthread.php?t=286260](http://www.ubuntuforums.org/showthread.php?t=286260)
but seems to forget it after reboot.

I think all my problems stem from the D-bus service not starting. I can only make it run if i reinstall the d-bus files but when I reboot it all disappears.
I'm beginning to think the 64bit Ubuntu is just a complete mess!

---

### Post by coltrane on 2007-01-05
I've had enough of ubuntu, I think I'll go back to trusty old knoppix, it's only 32bit but works on any PC and is easy and reliable to use.
I've spent hours and days trying to get ubuntu to work 32bit and 64bit, I don't usually get beat but I'm well pummeled this time:???: 
I think there's something fundamentally wrong with ubuntu that needs to be sorted out.

---

### Post by Nerdy on 2007-01-06
Add another freeze up to the list.
Installed the amd64 alternate cd.

After logging in the pc freezes completely.

I am able to login to the gui using root though.

---

### Post by coltrane on 2007-01-06
The only 64bit install that seems to work is Gentoo, so in the end went with that.
Still if anyone does come up with a solution or reason, I'd still love to know.

---

