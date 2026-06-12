---
title: "Can't boot ubuntu"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by ccalvinfowler@aol.com on 2007-07-23
After installing a fresh copy of ubuntu 7.0.4 in a new system with a brand new hard drive, ubuntu will not boot.
Installation completes successfully, but when it reboots, i get "no operating system found"

What do I do?

---

### Post by Pumalite on 2007-07-23
Could you give us a little more to go on? Specs? Dual booting? One hard drive? XP?. Vista?. It all counts.

---

### Post by ccalvinfowler@aol.com on 2007-07-23
When i posted message #1, i had 2 hard drives installed. both are brand new - out the box; motherboard is mti; cpu is amd athlon64; graphics card nvdia geforce fx5200.

I removed one hard drive and install/reboot worked fine.

Since i am new to linux, what next. I am stuck at a command prompt after reboot. i did get past the login and password part. after that i am at calvin@ubuntu:

anyone plz help.

---

### Post by Pumalite on 2007-07-23
Did you use 'Live CD'? 32 bit? 64 bit?. I suspect you might have a graphical interface problem. You could try the following at the command line: 'sudo dpkg-reconfigure xserver-xorg. Most defaults are OK. Choose 'vesa' as your driver.

---

### Post by ccalvinfowler@aol.com on 2007-07-23
i downloaded ubntu from the ubuntu site, x86 architecture(s is a personally built sysstandard computers...)

this is a personally built system.

---

### Post by Pumalite on 2007-07-23
Try the command I gave you. If it doesn't work, go with 'Alternate CD'. You avoid graphical interface problems.

---

### Post by ccalvinfowler@aol.com on 2007-07-23
tried  command line that you gave me and the out come is:

usr/sbin/dpkg-reconfigure must run be run as boot

---

### Post by ccalvinfowler@aol.com on 2007-07-23
i tried originally to install ubuntu w/2 hard drives so that i can run vista on another partition.  each hard drive is 160gb.

---

### Post by ccalvinfowler@aol.com on 2007-07-23
what do you mean alternate cd

---

### Post by Pumalite on 2007-07-23
How much memory do you have?

---

### Post by ccalvinfowler@aol.com on 2007-07-23
1g

---

### Post by Pumalite on 2007-07-23
Then you can go with Ubuntu Alternate CD: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Check the box below the green sign that says 'Start Download'

---

### Post by ccalvinfowler@aol.com on 2007-07-23
i am trying to rub ubuntu 7.04 server and i have already downloaded 3 times from different locations. the first two did not go past 85%.  the thrd copy was the only one that completed.   am trying one of the first disks again since i have removed one hard drive.

---

### Post by Pumalite on 2007-07-23
Usually torrent downloads are better than HTTP or FTP. Is important to do an md5sum on your iso before burn. Burn at 4x. Check your CD for corruption before install.

---

### Post by ccalvinfowler@aol.com on 2007-07-23
did so and disk and image are fine.

---

### Post by ccalvinfowler@aol.com on 2007-07-23
Have reinstalled another copy of ubuntu and same outcome. but i did manage to boot to menu run recovery mode and type in previous dpkg command and i received the message "xserver not installed"

What do I have to do now

---

### Post by Pumalite on 2007-07-23
Stumped here. Somebody jump in.

---

### Post by ccalvinfowler@aol.com on 2007-07-23
After doing further research, i have found that Ubuntu does not come with a GUI. I have tred to install a gnome gui or an ubuntu desktop, but to no avail. the computer does not have a connection to the internet but i have downloaded the xserver-xorg-core...deb, but i do not know how to transfer it to my other computer. the computer that has ubuntu is connected to my computer with the ubuntu, but as i said earlier, i am new to this.  Once i get help installing a gui, then I will be able to see what is going on.  Or do I need one.

I want to use that computer as a game server, and if i like it, i will install ubuntu client on my laptop. i would like to see what is going on, but if i can accomplish what i need without a gui, let me know.

---

### Post by Pumalite on 2007-07-23
See if you can install open-ssh and make it run. If firewalls; have to open port 22.

---

### Post by ccalvinfowler@aol.com on 2007-07-23
how do you install open-ssh

---

### Post by ccalvinfowler@aol.com on 2007-07-23
i have no packages on my computer.  As i said before, i am new and this is confusing to me. i hope that this is worth all of this tme

---

### Post by Pumalite on 2007-07-23
As I understand it one of your computers has connection to Internet, no? If so: Synaptic>Search>openssh>Install. Install Konqueror. Open it up. Where goes the URL, type fish://<username>@IP. You'll get the other computer's desktop. Then you can transfer any files you want.

---

### Post by ccalvinfowler@aol.com on 2007-07-23
i am currently downloading xubuntu to try that. i hope it works

---

