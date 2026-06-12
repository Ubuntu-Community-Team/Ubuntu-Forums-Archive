---
title: "Unable to boot ubuntu from live cd with Windows XP installed as first OS..."
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by WebEyeX on 2007-12-04
Hi,
I want to install Uuntu 7.10 with windows XP(Dual Boot-XP first installed).I make a partition on my new sata HDD and install xp on it.I left around 40 GB unpartitioned space for Ubuntu.Now the problem is Ubuntu is unable to boot from Live CD,actually it boots and after selecting start and install ubuntu kernel loads well then progress bar come but after this a blank screen with a cursor at the top left corner appears.

I also boot with the same CD before installing XP at that time i was booting.I think XP is creating some kind of problem.If Ubuntu can boot without XP installaed why not after installing XP on first partition.It does not look hardware issue to me because it is booting without XP installed.My system configration is as follows..

Intel D945GCNL Desktop Board
Intel Petium D 3.0 Ghz processor
2GB DDR2 RAM
Seagate 160 GB SATA HDD


Plz suggest me what i have to do.I am a newbie to Linux world...

Thanks

---

### Post by Neostart on 2007-12-04
Hi, my problem is the same. I have ...

CPU: Intel / Celeron** 1.7 GHz**
RAM: **1.25 GB**
Card: **Matrox Dual Screen** (use only one currently)** 16MB**
Disc: **250GB**
OS:** Windows XP Pro**

So, with upper configuration, I've made **7 **copies of Ubuntu LiveCD, to exclude bad** iso** or bad **rip**.

I launched - safe mode, normal / install mode or even developer install. Every time it switched to the so named: prompt screen. It's not good, I thought.

After 4 hours of searhing the website for an answer, tried also some commands in the prompt screen. They didn't do anything positive.

At the welcome install screen of Ubuntu, I hitted **F6** and added following command at the end, before "--" signs, like:
- all_generic_ide
- vgapoll

 or both of them simultanously. No effect.

Then, some of my colleague at work told me, the Ubuntu isn't stable version of Linux based systems, becuase of it's core. They didn't solved this kind of crash for a long time, so I'll be happy, if those commands could help you.

If not, forget the effort, switch to some other system, maybe S.u.s.e.? I know that the possibility of  working with Beryl 3D environment is mostly appealing, but I see no choice.

You can always use Fedora, it uses Beryl from what I herd.

I'm such a n00b :P

---

### Post by Neostart on 2007-12-04
> **WebEyeX said:**
> Hi,
I want to install Uuntu 7.10 with windows XP(Dual Boot-XP first installed).I make a partition on my new sata HDD and install xp on it.I left around 40 GB unpartitioned space for Ubuntu.Now the problem is Ubuntu is unable to boot from Live CD,actually it boots and after selecting start and install ubuntu kernel loads well then progress bar come but after this a blank screen with a cursor at the top left corner appears.

I also boot with the same CD before installing XP at that time i was booting.I think XP is creating some kind of problem.If Ubuntu can boot without XP installaed why not after installing XP on first partition.It does not look hardware issue to me because it is booting without XP installed.My system configration is as follows..

Intel D945GCNL Desktop Board
Intel Petium D 3.0 Ghz processor
2GB DDR2 RAM
Seagate 160 GB SATA HDD


Plz suggest me what i have to do.I am a newbie to Linux world...

Thanks


Hi, my problem is the same. I have ...

CPU: Intel / Celeron** 1.7 GHz**
RAM: **1.25 GB**
Card: **Matrox Dual Screen** (use only one currently)** 16MB**
Disc: **250GB**
OS:** Windows XP Pro**

So, with upper configuration, I've made **7 **copies of Ubuntu LiveCD, to exclude bad** iso** or bad **rip**.

I launched - safe mode, normal / install mode or even developer install. Every time it switched to the so named: prompt screen. It's not good, I thought.

After 4 hours of searhing the website for an answer, tried also some commands in the prompt screen. They didn't do anything positive.

At the welcome install screen of Ubuntu, I hitted **F6** and added following command at the end, before "--" signs, like:
- all_generic_ide
- vgapoll

 or both of them simultanously. No effect.

Then, some of my colleague at work told me, the Ubuntu isn't stable version of Linux based systems, becuase of it's core. They didn't solved this kind of crash for a long time, so I'll be happy, if those commands could help you.

If not, forget the effort, switch to some other system, maybe S.u.s.e.? I know that the possibility of  working with Beryl 3D environment is mostly appealing, but I see no choice.

You can always use Fedora, it uses Beryl from what I herd.

I'm such a n00b :P

---

### Post by maybeway36 on 2007-12-04
Try the alternate CD maybe.

---

### Post by Neostart on 2007-12-04
> **maybeway36 said:**
> Try the alternate CD maybe.

I don't know what it is - an alternate CD? From alternete reality or what?

since I've deleted the startup command "splash screen" I get commands listings after hitting the Install menu.

So I'm, one step further.

---

### Post by Pumalite on 2007-12-04
Download the Alternate CD from here: [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below the green sign 'Start Download'

---

### Post by clubsoda on 2007-12-06
WebEyeX,

It sounds like some part of your hardware is not being detected and is hanging the system.  Try what Neostart did, i.e. edit the boot line and remove "quiet splash", then post back the last few lines which come up onscreen before it crashes.

Neostart, your symptoms may be similar but I think your problem is different and belongs in a thread of its own...[quote=Neostart]I've made 7 copies of Ubuntu LiveCD, to exclude bad iso or bad rip.[/quote]Hint: The main menu on the CD has an option to check the integrity of the rip.  It's good you made plenty of extra copies though - maybe pass them around to your work colleagues? ;)  OK, enough stirring.  The bad news is that Matrox support in linux is still patchy, depending on the exact card and its configuration.  Best place to get your drivers is [http://matrox.tuxx-home.at](http://matrox.tuxx-home.at).  This won't necessarily help you get the LiveCD running though.  Consider installing Ubuntu with a different graphic card, then installing the Matrox drivers, patching xorg.conf and finally switching back to the Matrox card.

---

### Post by WebEyeX on 2007-12-06
Hi,
Thanks ClubSoda for ur reply.I will try ur suggestion.One thing i would like to mention here again all the problem is happening after installing the XP on first partition(I want to dual boot Ubuntu with XP).I tried Ubuntu's Live CD on the same system without XP installed and it worked well.

Now the question is if Live CD is working well without XP installed,Is XP creating some kind of problem or something else???

Thanks

---

### Post by WebEyeX on 2007-12-06
I tried every thing suggested here..But nothing is working for me..

1-Tried Live CD--Blank screen with a cursor
2-Tried Alternate CD--Installation start but after selecting language it got stuck and nothing happen(although i wait for 1 hour).
3-Tried 'wubi-cdboot' from live cd--It asked to restart and after doing that again a blank screen with a cursor.
4-Tried boot option 'nosplash'--Again blank screen.:confused::confused:

Plz Plz help me....:(

Important -- I can boot using Live CD with unpartitioned HDD.But can not boot with XP installed on first partition.

---

### Post by Pumalite on 2007-12-06
Get Gparted Live CD and resize XP partition if you haven't done it.

---

### Post by WebEyeX on 2007-12-06
> **Pumalite said:**
> Get Gparted Live CD and resize XP partition if you haven't done it.

Sorry what do u mean by Gparted Live CD.I have around 20 GB unpartitioned space for Ubuntu.Do i still need to resize XP partition?

---

### Post by Pumalite on 2007-12-06
If you have 20 GB of space, fine, but it has to be a partition. Ubuntu does not install in 'unallocated' space.

---

### Post by WebEyeX on 2007-12-06
Finally Ubuntu is being Installed.I used 'acpi=off noacpi' boot parameter and alternate cd to get it through.When every thing was looking fine and i was on my feet another problem was waiting for me.

After selecting Ubuntu from GRUB menu, my monitor is showing a box which has text something like 'Hz..?'.

Now i have two questions here what 'acpi=off noacpi' did and how to solve Hz..? problem.

---

### Post by Pumalite on 2007-12-06
You probably have to configure your xserver. If you have no command line:
Ctrl+Alt+F1 to get command line
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver.
At the end: startx
Or sudo /etc/init.d/gdm start

---

### Post by WebEyeX on 2007-12-06
> **Pumalite said:**
> You probably have to configure your xserver. If you have no command line:
Ctrl+Alt+F1 to get command line
sudo /etc/init.d/gdm stop
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver.
At the end: startx
Or sudo /etc/init.d/gdm start

I am sorry to say but i tried all the steps given here but still i am getting same green box 'Hz ?' after start up.
But when i run this command
'sudo /etc/init.d/gdm start'
Ubuntu boot but within few minutes it hang..Every thing get freeze and i have to restart manually.
I am really very disappointed.First it was problem to install now it is not working.......:mad:

---

### Post by clubsoda on 2007-12-07
WebEyeX,
The "Hz" box is your screen telling you it doesn't like the refresh rate which the graphic card is sending it, which sounds like a driver problem.  */var/log/Xorg.0.log* is your friend, look for errors, warnings or anything unexpected there.  You could post that log file here if you like.  Also look at *lspci -v* for your exact graphic chip and *xdpyinfo* for the current status of your screen.

Pumalite,
I agree that the vesa driver should work on just about anything but shouldn't there be open-source intel graphic drivers included in Ubuntu which might work better?

---

### Post by clubsoda on 2007-12-07
Going out on a limb here...
For *Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)* you might try ```
Driver "i810"
``` in your xorg.conf.  More info at [http://intellinuxgraphics.org/documentation.html](http://intellinuxgraphics.org/documentation.html).

No guarantees.

---

### Post by WebEyeX on 2007-12-07
Finally I have solved half of my problem.It was the splash screen which was creating problem.I used this command

$ sudo gedit /boot/grub/menu.lst

removed 'quite splash' and update the grub.Now i can use Ubuntu(without splash or boot screen though).

Well I would also like to thank all of you for your support.

Thanks again.

:guitar:

---

