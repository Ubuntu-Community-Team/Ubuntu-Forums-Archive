---
title: "Ubuntu Server &amp; Lubuntu Installation Problems"
date: 2011-08-21
forum: Installation &amp; Upgrades
---

### Post by Otterjasie on 2011-08-21
Hi All

I am a first-time Linux user.  I use a 600MHz Pentium III with 256MB Ram.  Therefore I searched for the most appropriate distrubutions of Linux before trying to install.  I verified the md5sums and wrote the discs at 8x and had Nero verify the CD's after burnig.

The two most promising options were Lubuntu and installing Ubuntu Server then adding Lxde or some other GUI.

LUBUNTU 11.04:

Firstly, when I boot from the CD I get the Graphics Initialisation failed / gfxboot failure problem.  I searched the forums and learned to type "help".  This lead me to the help index where you have access to some information through F1 to F9.

At this stage commands like "install" or "install vga=normal fb=false" is supposed to work according to the help information.  Upon typing for instance "install" I receive a response along the line of: "install" not a recognised kernel image

If I only press enter the system boots from the CD.  Then I right click on the "Install Lubuntu" icon and select open.  The Installer then opens.  I go through the motions of setting up the partitions etc.

The installer then starts to configure the partitions and so on, just about when the Installer asks me about the time zone it crashes.  I get a "partman" error message.  I copied the files "/var/log/syslog" and "/var/log/partman" to my windows data disc, but cannot open them from windows.  I can e-mail them to anyone who is interested.

Some help will be dearly appreciated.

UBUNTU SERVER

I have the same problems with the initial booting from the CD.  As before typing "help" gets me to the help menu.  With Ubuntu Server the commands like "install" are recognised and accepted.

I do however receive a message reading "Undefined video mode number: 314"  Then the system provides me with options to choose from.  I've tried several different options but all leads to the same end:  Ubuntu installs without problems, but when I boot the system after installation the terminal has a white background and displays illegible symbols...   Ctrl+Alt+F1 to F4, nothing changes.

The only video information I could gather from my bios is:  Primary Video adapter AGP.

Again, any advice will be welcome.

Cheers

---

### Post by tangelo on 2012-01-22
I have very similar problem.
I have HP Omnibook 6000 with 1GHz CPU and 256megs of RAM.

It started when I wanted to test desktop environment with my debian server. I installed lxde and right after it tried to start x the screen went blank and then had some strange white lines and garbage on it and then the whole system stopped responding. The sleep and power buttons didn't do anything and I had to remove AC and battery to be able to reboot the system. 

After fiddling a while and googling and trying different suggestions I gave up and installed lubuntu 10.11. After the install and reboot *bam* the exact same thing.

I've tried different VGA-modes and those VGA=ask VGA=normal options, but nothing helps. The screen turns dark and the backlight seems to get brighter for a while and then the whole system just freezes. I have a basic understanding on linux, but this is way beyond my skills.

EDIT: Yeah, after those VGA=ask tries I get that "Undefined video mode number: 314" error and no matter what mode I choose, it doesn't work.

---

### Post by tangelo on 2012-10-10
up

---

