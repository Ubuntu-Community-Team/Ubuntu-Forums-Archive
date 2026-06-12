---
title: "Installing Ubuntu and grub 2 on a second hard drive."
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by lynchy67 on 2011-04-11
[COLOR=black][FONT=Verdana][SIZE=2]Hi All newbie here.[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=2]I've been reading and searching the forums here and most of the problems I have read about stem from writing the grub2 to the MBR of the primary drive.[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=2]So i'm trying to avoid these problems if possible.[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=2]Heres what I'm trying to achieve.[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=2]I have two seperate hard drives in my PC, on the first is Vista Home Premium 64bit.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2]The second drive is now completely empty and has just been reformated to NTFS with the standard 4096 setting. [/SIZE][/FONT][/COLOR]
 
[SIZE=4][SIZE=2]I would like to install Ubuntu 10.10 [COLOR=red]and[/COLOR][/SIZE] [COLOR=black][FONT=Verdana][SIZE=2]grub2 onto the second drive so that nothing is written to the primary drive at all. In a thread I read it mentioned that to do this I would need to use a "Specify Partitions Manually (Advanced)" option.[/SIZE][/FONT][/COLOR][/SIZE]
 
[COLOR=black][FONT=Verdana][SIZE=2]My thinking is that I can just use the same process I'm using to run Ubuntu from a dvd disk to start Ubuntu once installed on the second drive. The process is an F10 "Boot Menu" when the computer is first turned on just before it starts to run Vista. [/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=2]So my question is about the advanced installer options. [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2]Is there a walkthough available anywhere? (with screenshots maybe).[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2]I'm just worried that something may come up in the advanced installer that I have no knowlege of.[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=2]I can re-format the second drive again from within Ubuntu running from disk if I need to (NTFS???). Also when running Ubuntu from disk I can still see the main primary drive and all its files. It would be nice to have this option but its not essential.[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=2]My system.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2]Windows Vista Home Premium 6.0.2002 SP2 Build 6002.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=2]64 Bit, Intel Q8200 Quad core, 8GB Ram, Nvidia 9600GT 512MB[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=2]Thanks you in advance for any help you can give.[/SIZE][/FONT][/COLOR]

---

### Post by Dutch70 on 2011-04-11
Hi and welcome to UF

I strongly recommend you unplug your hdd with windows on it. If it's not plugged in, you can't mess it up. After installing Ubuntu to the other hdd. Plug in your windows hdd and hit escape while booting to choose the hdd you want to boot. Login to Ubuntu, and run this from a terminal.
```
sudo update-grub
```
After that, it will see your windows install on the next reboot, and it won't be messed up.

You will have to reformat your hdd to ext3 or ext4, I suggest formatting to the latest ext4 unless you have a reason not to.

How to install with a /home & pictures...:P
[[COLOR="Red"]Installing-Ubuntu-10-04-LTS[/COLOR]]("http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml")

Also, there are many questions and recommendations for the size of your swap partition. I recommend making it equal to the size of your physical RAM. Add about 10% for good measure and overflow if you want. Read this...
[[COLOR="Red"]SwapFaq[/COLOR]]("https://help.ubuntu.com/community/SwapFaq")

---

### Post by lynchy67 on 2011-04-11
Thank you Dutch70.
 
"If it's not plugged in, you can't mess it up."
 
Can't argue with the logic of that. The ultimate safe mode :D
 
I'll give that a go. Cheers.

---

### Post by Dutch70 on 2011-04-11
lol, just don't forget to touch something metal (like your power supply) to discharge any static electricity in your body before touching anything else inside the computer, or it will the ultimate (&%*^) mode. ;)

And your welcome, let us know how it goes.

---

### Post by lynchy67 on 2011-04-11
Well it went very well. I think.:D

Safe in my knowledge that the Vista drive was unplugged I decided that during the installation I might as well use the whole drive. So I chose that option thinking it would reformat the drive in the format you mentioned anyway.

Not sure it has though.
I just ran Ubuntu to run that script you mentioned and took a look at the "Computer" and its already showing the vista and system partitions on that primary windows drive. The the second Ubuntu drive is now called "File System" and the properties started counting up the files on the disk and got to about 150GB? but its a 120GB drive. OOPS :P

Ubuntu runs fine from the F10 Boot Menu and Vista loads automatically if I don't hit F10.

So the Windows drive is fine but I think I should unplug it again and start the Ubuntu installation again.

To clarify a few things then.
Should I run Ubuntu from the dvd disk again and reformat the second drive again from Ubuntu this time running from disk.

---

### Post by Dutch70 on 2011-04-11
If it installed, it's formatted. You can't install Ubuntu on a hdd formatted with ntfs. Micro$oft would never allow that. :P

However, if you didn't create a /home, you'll more than likely regret it one of these days & possibly very soon. ;)


After you update your grub, it should have windows in your grub2 menu without having to hit F10. Windows should show up in Nautilus before you run that command.

To see how things are, you'll need to be logged in to Ubuntu. 
Check Gparted for a look at your hdd's and partitions. Also, Disk Utility is a good tool.

---

### Post by lynchy67 on 2011-04-11
> **Dutch70 said:**
> If it installed, it's formatted. You can't install Ubuntu on a hdd formatted with ntfs. Micro$oft would never allow that. :P

However, if you didn't create a /home, you'll more than likely regret it one of these days & possibly very soon. ;)

After you update your grub, it should be picking up windows without having to hit F10.

To see how things are, you'll need to be logged in to Ubuntu. 
Check Gparted for a look at your hdd's and partitions. Also, Disk Utility is a good tool.

I think you may have misunderstood.

I only use F10 to boot into Ubuntu on my second drive.
If I don't hit F10 as my computer first starts it automatically loads into Vista. This is exactly as I want it to work.

I think you may be be giving me to much credit as I haven't a clue what Gparted is. :)

---

### Post by lynchy67 on 2011-04-11
Ok yes the disk utility shows the second drive as having a few bad sectors.

And it is ext4 :P

---

### Post by Dutch70 on 2011-04-11
> **lynchy67 said:**
> I think you may have misunderstood.

I only use F10 to boot into Ubuntu on my second drive.
If I don't hit F10 as my computer first starts it automatically loads into Vista. This is exactly as I want it to work.

I think you may be be giving me to much credit as I haven't a clue what Gparted is. :)

Hahaa...ok, that's what I meant ...lol j/k. 

Gparted is the partition editor for Gnome. Really nice application.

---

### Post by lynchy67 on 2011-04-11
Smart Data (Whatever that is :-)   ) gives a warning of Reallocated Sector Count and a tool tip that warns of imminent disk failure. 

OO scary. maybe need another hard drive, that one is quite old anyway. 

I'll look into Gparted and /home.

At least vista is safe, thanks to you. Cheers.

---

### Post by Dutch70 on 2011-04-11
How many bad sectors does it show? I've had 9 bad sectors on one of my hdd's for almost a year with no problems, it's when they start to grow that you really have to worry & they can grow fast.

/home is similar do documents & settings in windows. Having a /home will allow you to reinstall Ubuntu without losing your data or even your settings. Comes in real handy if you have problems you can't get fixed easily, or if you want to do a fresh install instead of an upgrade. Such as when 11.04 comes out on April 28th. Lots of people upgrade just fine, I've never been able to do it successfully, it takes a long time and is quite complicated in comparison to a fresh install, which takes about 20 min.

Glad you got everything installed ok. 
Happy Ubuntuing ;)

---

### Post by Dutch70 on 2011-04-11
I do want to reiterate, since you know how to create a usb stick now, you really should check out Kubuntu from a live cd/usb. I think you'll be surprised.

---

### Post by lynchy67 on 2011-04-11
Ah Now I see what you mean about needing the /home directory soon :p
 
Just downloading kubuntu now.
 
I'll stick with this drive till it dies. Only using it for Blender at the moment so I'll backup files to USB as I go.
 
Thanks for all your help.

---

### Post by Dutch70 on 2011-04-11
I haven't used it yet, but Clonezilla comes highly recommended for backing up your entire hdd.

---

