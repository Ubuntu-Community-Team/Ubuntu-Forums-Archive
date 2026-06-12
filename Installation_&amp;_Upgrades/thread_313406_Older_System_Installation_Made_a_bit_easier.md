---
title: "Older System Installation Made a bit easier"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by magic_ninja on 2006-12-06
Low Level System - v.1 Dec. 5, 2006 10:43pm CST

This is just a little something I decided to put together to mabye help someone out.  I don't know if it is of any use, but the main object of this "guide" is to help someone out that gets stuck in my situation, and for the install via the Breezy LiveCD - graphical install.  The way I went about matters probably wasn't the best of options, but it did work for me and may work for someone else.

Here are the specs of the system I performed this on

_Compaq Presario 1600 Laptop_

15 Inch monitor
Pentium III 500mhz 256k cache
196 megs SDRAM
USB Cable Modem + 4 Port Microsystems USB Hub (10 dollar wal-mart special)
Grade A "Designed for Microsoft Windows 98" label
12 Gig Toshiba hdd

Now as you can see, the specs on this system are fairly old, but it runs ubuntu like a true champ.  The main purpose of this cd is to listen to music and to do homework for various classes in college and high school.

My primary problem was that when I booted into the livecd graphical installer version, I ran into a lot of trouble.  It took 94 seconds for a click on the desktop to register and a good 5-10 minutes to get almost fully booted.  So I think that it's safe to say that performance was a BIG issue.  Then on top of that, when I did wait for it to start, the Install icon on the desktop hung the system.  So I decided to try to only boot what was needed to get the job done...and it was a little tricky due to my lack of another machine, no CD burner, internet access, and the fact that I hadn't attempted something like this for a couple years.  Anyway now that you understand a little bit of the situation, you can compare this to your situation to see if it's even similar to your situation and the problems your facing with your system.

**Primary Problems**
Low DVDROM Performance
Graphical Installer Hangs at Disk partitioning once working
Random system hangs

**Steps**

1. Put the CDROM in the drive and boot.
2. Once at the Ubuntu boot screen move to the "Safe Graphical Mode" section
3. Press F6 to get to the startup permimiters and flags, use the left or right arrow keys to move to the end and remove the "Splash" option completely.  Then delete the "quite" and replace it with verbose.
4. Wait for the system to boot fully and get into Gnome, I would suggest getting the boot started, then walking away for a while if your system specs are mine or lower](*,) .
5. Press Alt + F1 to switch to tty1
6. You should see the ubuntu command prompt on a black screen at this point, note your system will probably still be running slow.

FROM THIS POINT ON READ CAREFULLY

7. Make sure your data is backed up.  You can always repartition and resize later, but for me, the custom disk partitioning option just hung my system every time.  You will have to wipe your entire disk if this occurs on your machine, then it might hang, and might not depending on the individual system.

8.Once at the command prompt type  "pgrep gdm", minus the of course.
9.You should get an output something like:
     5098
     5074
of course the numbers are varied and most likely will not match, but anyway
10.type "sudo kill <insert pid number here>" for each of the two numbers, this will kill the gdm (or Gnome Display Manager)
11.Type "xinit"  -->this will start a very basic x with a terminal and there is no need to run any more programs

12.  Now your ready to start.  Your Live boot should run so much better now that you don't have a fairly bulky display manager running.  At this terminal you can do a variety of things
         Type "mozilla-firefox" to browse the web if you have the internet
         Type "gaim" and use the IRC option to get to #ubuntu on                                               irc.freenode.net for additional help.  This is VERY useful if your having additional trouble this guide does not address.  If you just want to try the install (reccomended) then just type "sudo ubiquity" at the prompt and wait for the install to appear.Insert your information for the first 4 steps and you shouldn't have any trouble.

13. Now your at a possible trouble point.  I am going to reccomend that you erase the entire disk (if you backed up your data) and let ubuntu do the partitioning, and you can always resize partitions later to get the partition table how you want it.  You can try a manual partitioning, and may have luck but my PC constantly froze.  Let the installer run, and follow the wizard (if you selected erase entire disk) and read through the output the program gives you to make sure its correct.

With any luck you will reboot into a freshly installed ubuntu desktop on your old hardware with minimal difficulty.

I hope this guide may help at least one person out with their trouble, and please excuse the lack of formatting in this document.  Please feel free to post any suggestions, comments, changes or questions and I would be glad to update/modify this document.  Good luck and enjoy Ubuntu.

Magic-Ninja

---

### Post by Sef on 2006-12-06
I think it is interesting what you did, but it is rather too hard for the average user who just wants things to work.  Certainly if someone wants to try something different, it would be useful; however, Breezy Badger is an old version, so downloading it would be a problem, if you don't have one.  This may work with Edgy or Dapper though.

---

### Post by eye208 on 2006-12-06
> **magic_ninja said:**
> 
4. Wait for the system to boot fully and get into Gnome, I would suggest getting the boot started, then walking away for a while if your system specs are mine or lower](*,) .

In order to avoid loading most of Gnome's eye candy in the first place, press F6 at the boot screen, then replace "splash" with "single". This will boot the Live CD into single user console mode. Enter the following commands to switch into multiuser console mode without X:

**# apt-get remove gdm** (or kdm in case of using a Kubuntu disc)
**# telinit 2 ; exit**

Now you can sudo apt-get remove even more stuff (themes etc.) to prevent them from loading. You can also do lots of other things here, e.g. **sudo dpkg-reconfigure -pmedium xserver-xorg** to adjust display settings and troubleshoot "out of range" problems with certain monitors. When you're ready, enter **startx** to run the GUI.

---

### Post by enietering on 2006-12-06
thanks so much for making this!
i have an ancient gateway solo laptop (PII 333, 196MB)
and the installer would hang when i tryed to load it from GNOME
but thanks to your post i was able to install it!

EN

---

### Post by djheadley on 2006-12-07
I also have a gatweay solo (PII, 333, 196 ram) and I had a lot of trouble trying to install Edgy so I went back to Dapper.  Dapper runs pretty good.  I'm trying to find more memory and a larger hard drive for it - I still dual boot with Win as I volunteer at my church and that's what they use.

---

### Post by magic_ninja on 2006-12-07
Thanks for the feedback, I will probably update the tutorial some once I get more.  This wasn't really intended for the new user or average user, but more someone in a tight spot that needs to see what they can do.  I must confess though...this was an Edgy cd that i installed and I didn't realize it.  Just got the net back and a computer back after a year and a half and kinda got stuck in a tight spot, and thought i downloaded breezy, set all my repos to breezy repos, then realized I was running Edgy, heh.  Anyway I got all my reps worked out, but perhaps I should just edit the post and change my version, if you guys have any more ideas of things to add just let me know.

---

### Post by K.Mandla on 2006-12-08
Good ideas here. I've tried knocking down a live CD session to make space for other stuff, but I hadn't ever heard of some of these ideas.

Just curious: Is it easier to install this way, or to install a server and build up? Or is that defeating the point? :rolleyes:

---

### Post by magic_ninja on 2006-12-09
Well, the only real server's i've ever set up have been some local file servers at my school and the occasional network or ftp server at my house, but its not usually necessary seeing that I only own 2 computers.  If you want a server it would probably be best to just install a minimal installation and then install only the packages you need to help with security. Now to answer a couple questions.

I was asked if the install was easier this way, and the answer is "not really".  It was just a workaround I thought about because I had played with linux on some older machines before.  I have a really small house and don't really have much room for my bulky desktop system, and just aquired this laptop, so I figured it would be easier to just use it then clean out a room to put a desk.  (I live in a small trailer house, heh).  Eventually I'll get my other machine out of my storage and hook it up and try the latest version of some linux distro on it.  I was thinking about trying Xandros.

The other point I would like to make (obvious ADHD baby syndrome aside) is that the only reason I removed most of the gnome and X eye candy and "useless" stuff is because my laptop would not run it at an even remotely reasonable speed.  Its like I put windows 98 se on a comradore 64 DOS machine.  Plus the fact that I believe an operating system OS shouldn't need all that high level graphical bs.  Its really a great idea to have a live cd and install cd in one, but I just don't like it.  Anyway if you wanna toy around with it some more just post if you get problems.

---

### Post by kerry_s on 2006-12-09
> **magic_ninja said:**
> Well, the only real server's i've ever set up have been some local file servers at my school and the occasional network or ftp server at my house, but its not usually necessary seeing that I only own 2 computers.  If you want a server it would probably be best to just install a minimal installation and then install only the packages you need to help with security. Now to answer a couple questions.

I was asked if the install was easier this way, and the answer is "not really".  It was just a workaround I thought about because I had played with linux on some older machines before.  I have a really small house and don't really have much room for my bulky desktop system, and just aquired this laptop, so I figured it would be easier to just use it then clean out a room to put a desk.  (I live in a small trailer house, heh).  Eventually I'll get my other machine out of my storage and hook it up and try the latest version of some linux distro on it.  I was thinking about trying Xandros.

The other point I would like to make (obvious ADHD baby syndrome aside) is that the only reason I removed most of the gnome and X eye candy and "useless" stuff is because my laptop would not run it at an even remotely reasonable speed.  Its like I put windows 98 se on a comradore 64 DOS machine.  Plus the fact that I believe an operating system OS shouldn't need all that high level graphical bs.  Its really a great idea to have a live cd and install cd in one, but I just don't like it.  Anyway if you wanna toy around with it some more just post if you get problems.


Dude, you have really got to learn about using the command-line/server install, it makes installing on old under powered systems a synch. Just because we call it a server install dosen't mean it installs a server or is just used for a server. What it does is install a base system, then you choose what you want to make it in to. For example, you want to install ubuntu but your hardware is not the greatest so the livecd won't work & you don't want all that extra stuff that comes with a full install, here's were the command-line/server install comes in handy. You do this->

command-line/server install
login
sudo su
nano /etc/apt/sources.list
comment(#) out the cdrom & uncomment all the repos (ctrl+ X & Y & enter to save)
apt-get update
apt-get install x-window-system-core gdm gnome-core
reboot

That's it you have just installed a barebones gnome system.
But what if you want something else, for instance you want a barebones kde, you just change->
apt-get install x-window-system-core gdm gnome-core
to
apt-get install x-window-system-core kdm kde-core

But you hear that xubuntu is better for older systems, so you decide you want a mini xubuntu, so then you just do this->
apt-get install x-window-system-core gdm xfce4

But you say hay, i want the lightest fastest system i can get, i want to pick my own applications so this computer can fly! So you do some reading & you make a list, now you got a idea of what you want, it's time to put it all together->

command-line/server install
login
sudo su
nano /etc/apt/sources.list
comment(#) out the cdrom & uncomment all the repos (ctrl+ X & Y & enter to save)
apt-get update
apt-get install x-window-system-core (your applications here)
reboot

Then you say "Yay! I just built a custom system to fit my needs"

Just incase your curios, here's what i use->
apt-get install x-window-system-core gdm fluxbox synaptic emelfm leafpad 

fluxbox=window manager
synaptic=package manager
emelfm=filemanager
leafpad=editor

That's just enough to get me to a nice fast basic gui system. I usally start by trimming the base down more, so i fire up synaptic & start removing stuff i know i dont need, after trimming then i install the rest of my app's.

Amazing what you can do with a simple command-line/server install & just 1 alternate cd or netinstall mini.iso, isn't it?

---

### Post by magic_ninja on 2006-12-09
You know what, thats pretty cool man.  I told you I'm just a novice linux user, I have a lot to learn, but I also know quite a bit.  I even said in my tutorial that there ewas probably a much better way, but here is the thing, I had no internet connection or a way to burn a CD without spending half a day doing it (via my friend's comp.) and it was like 12:30 am and I just thought about doing it like that by tinkering with the regular edgy live install.  I think that next time I reinstall, I'm going to do it that way, it seems nice.  Anyway I appreciate the feedback.

---

