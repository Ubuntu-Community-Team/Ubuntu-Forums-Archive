---
title: "Newbie trying to switch to Ubuntu"
date: 2008-10-15
forum: Installation &amp; Upgrades
---

### Post by Markstar on 2008-10-15
Hi,
while I do consider myself an expert when it comes to computer hardware and Windows (I'm a computer scientist), I only just now began to take a look at the Linux world and I am struggling to get comfortable. 

As I imagine that there are many people like me who are fed up with a bloated OS and constant threats from viruses, I thought I try to write one thread with all my issues and go from there. More complicated problems may require me to open up seperate threads but I imagine some things can be answered pretty quickly. Alright, here we go:

[SIZE="4"]_Top Priority_[/SIZE]

&#8226; [COLOR="Red"]**Graphic driver for ATI 4870**[/COLOR]
[INDENT]&#8728; [COLOR="Green"]Problem #1.1[/COLOR]: Installing via Synaptic didn't work (can't run native resolution of 1920*1600)
[INDENT]&#8227; download package from [http://ati.amd.com/support/drivers/](http://ati.amd.com/support/drivers/)[/INDENT]
&#8728; [COLOR="Green"]Problem #2[/COLOR]: Can't do anything with .run file
[INDENT]&#8227; right-click on file in file browser -> Permissions tab:
&#8227; Check "Allow executing file as program"[/INDENT]
&#8728; [COLOR="Green"]Problem #3[/COLOR]: ati-driver-installer....run must be run as super user - how does a newbie do that?
[INDENT]&#8227; [terminal] navigate to downloaded file, then: sudo ./ati...
[INDENT]&#8226; log file: /usr/share/ati
&#8226; advanced configuration: [terminal] aticonfig[/INDENT][/INDENT]
&#8728; [COLOR="Green"]Problem #1.2[/COLOR]: Still not the correct resolution, Desktop effect can also not be enabled
[INDENT]&#8227; driver needs to be enabled in System -> Administration -> Hardware Drivers[/INDENT]
&#8728; _[COLOR="Red"]Issues left:[/COLOR]_
[INDENT]&#8227; Reduce frequency
&#8227; Movies flicker!!! :(
&#8227; My 2nd monitor (also DVI) does not work correctly (in Windows, the 1st monitor is 1920*1200, the 2nd is 1024*1280 (90° rotated)).[/INDENT] [/INDENT]
&#8226; [COLOR="Red"]**Automatic CPU frequency adjustment for AMD 4850e**[/COLOR] To save energy and reduce heat...
[INDENT]&#8728; [task bar] Add to Panel... 
[INDENT]&#8227; CPU Frequency Scaling Monitor[/INDENT]
&#8728; _[COLOR="Red"]Issue left[/COLOR] _
[INDENT]&#8227; Only goes down to 1 GHz (5x) instead of 800 MHz (4x)
&#8227; Adjust voltage?[/INDENT][/INDENT]
&#8226; **[COLOR="Red"]Fan speed for Jetway HA06 (780G chipset)[/COLOR]** It works under Windows, but I can't get it to work under Ubuntu. 
[INDENT]&#8728; install lm-sensors
[INDENT]&#8227; [terminal] sensors-detect -> inserts modules in /etc/modules[/INDENT]
&#8728; run pwmconfig
[INDENT]&#8227; [COLOR="Red"]Problem #1[/COLOR]:  /usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed :([/INDENT][/INDENT]
&#8226; [COLOR="Green"]**Access Windows network**[/COLOR] (client and host) *//solved*
[INDENT]&#8728; Thank you cariboo907 for his tutorial as well as [this link]("http://ubuntuforums.org/showthread.php?t=202605"). 
&#8728; Drives can be added to the share by mounting them to the Samba share folder, e.g.:
[INDENT]&#8227; [terminal] sudo gedit /etc/fstab:  
[INDENT]&#8226; /dev/hda1/ 	/SHARE_FOLDER	ntfs-3g defaults,locale=en_US.UTF-8 0 0 (for NTFS partitions)[/INDENT]
[/INDENT]
&#8728; Mounting remote drives:
[INDENT]&#8227; Install smbfs package
&#8227; [terminal] sudo gedit /etc/fstab: 
[INDENT]&#8226;//HOST_IP/SHARE_NAME	/mnt/MOUNT_FOLDER	cifs	defaults,user=SHARE_USERNAME,password=SHARE_PASSWORD,uid=1000 0 0
[/INDENT][/INDENT]
&#8728; [COLOR="Red"]_Issue left_[/COLOR]: 
[INDENT]&#8227; I can see other computers but they seem to be empty in the file browser!
&#8227; Advanced User Administration (certain files for certain users)
&#8227; Places -> Network : Computers are there but contents are empty. 
[/INDENT][/INDENT]
&#8226; [COLOR="Green"]**xplorer2 replacement**[/COLOR] I'm looking for a NC-like file browser that also has a 3rd window with a tree view *// solved*
[INDENT]&#8728; XFE seems to be the best choice (Thank you kerry_s)[/INDENT]
&#8226; [COLOR="Red"]**Programming C++**[/COLOR] Currently only basic compiling needs, but what do I need to get QT working as well? Which packages to install for GNU-C++ (g++)?
&#8226; [COLOR="Red"]**Textpad replacement**[/COLOR] In Windows, that was my editor of choice - which one do you recommend to use in Ubuntu (I have not looked yet)?


[SIZE="4"]_Very Important_[/SIZE]

&#8226; [COLOR="Green"]**VNC**[/COLOR]   *// solved*
[INDENT]&#8728; [Synaptic] Install xtightvncviewer
&#8728; [Taskbar] Add to Panel...
[INDENT]&#8227; Custom Application Launcher 
[INDENT]&#8226; Command: /usr/bin/xtightvncviwer (+ Server IP) [/INDENT][/INDENT][/INDENT]
&#8226; [COLOR="Green"]**Windows-style font**[/COLOR]  *// solved*
[INDENT]&#8728; Used this tutorial: [http://ubuntuforums.org/showthread.php?t=208396](http://ubuntuforums.org/showthread.php?t=208396)
[INDENT]&#8227; [COLOR="Green"]Problem #1[/COLOR]: Afer reboot, I can enter my username and password, but it will not load the desktop (it does play the sound). 
[INDENT]&#8226; Boot Ubuntu in *safe mode*, repair X and inspect packages
&#8226; Enable ATI driver again[/INDENT][/INDENT][/INDENT]
&#8226; [COLOR="Green"]**Automatically mount other partitions (NTFS/FAT32)**[/COLOR] 
[INDENT]&#8728; [terminal] mkdir MOUNT_FOLDER
&#8728; sudo gedit /etc/fstab:
[INDENT]&#8227; /dev/hda1 /mnt/MOUNT_FOLDER ntfs-3g defaults,locale=en_US.UTF-8 0 0 (for NTFS)
&#8227; /dev/hda2 /mnt/MOUNT_FOLDER	vfat	defaults,user,dmask=000,fmask=111 0 0 (for FAT32)[/INDENT]
[/INDENT]
&#8226; [COLOR="Red"]**AC3 sound for videos**[/COLOR] My sound card (Audigy 2 eX) is connected with an optical cable to my sound system, which I hope to get working when watching DVDs (sound via the normal output was working out of the box)
&#8226; [COLOR="Red"]**Use same Thunderbird and Firefox data in all OS's**[/COLOR] 
[INDENT]&#8728; [/home/USERNAME/.mozilla/firefox/profiles.ini]
[INDENT]&#8227; IsRelative=0
&#8227; Path=PROFILE_PATH[/INDENT][/INDENT]
[INDENT]&#8728; **[COLOR="Red"]Problem #1[/COLOR]:**
[INDENT]&#8227; Firefox/Thunderbird will not start ("Firefox is already running..."). :([/INDENT]
&#8728; [COLOR="Green"]Problem #2[/COLOR]:
[INDENT]&#8227; Error when accessing Hotmail-Accounts
[INDENT]&#8226; Set ports to > 1024[/INDENT][/INDENT]
[/INDENT]


[SIZE="4"]_Also_[/SIZE]

&#8226; **[COLOR="Green"]Keyboard driver (Logitech G11)[/COLOR]** This keyboard has extra function keys that I would love to use also in Ubuntu
[INDENT]&#8728; I did the steps from [this page]("https://help.ubuntu.com/community/LogitechG15") (thx MetalHellsAngel). G-keys work now. :)
&#8728; [COLOR="Red"]_Issue left_[/COLOR]: 
[INDENT]&#8227; M-keys work as shortcut but do not activate different sets of G-keys.[/INDENT][/INDENT]
&#8226; **[COLOR="Green"]Configure advanced desktop effects[/COLOR]** Add compizconfig-settings-manager via Synaptics and then *System -> Preferences -> CompizConfig Settings manager*
&#8226; **[COLOR="Green"]Firefox: Enable Backspace to go to previous page[/COLOR]** In Firefox, enter URL "about:config" -> browser.backspace_action. Change value to 0. 
&#8226; **[COLOR="Red"]AVC-codec for videos[/COLOR]** So I can play my HD-movies
&#8226; **[COLOR="Red"]Virtual Desktop (like VMWare)[/COLOR]**
&#8226; **[COLOR="Red"]Wine[/COLOR]** While I don't like to drink it, I hear it is rather nice to get Windows programs (and games :p) to work
&#8226; **[COLOR="Red"]Mouse scrolls one page[/COLOR]** Grr, can't find the option where to turn this on. 
&#8226; **[COLOR="Green"]Clean up Grub menu[/COLOR]**
[INDENT]&#8728; [terminal] *sudo gedit /boot/grub/menu.lst*:
[INDENT]&#8227; Enable default ...saved
&#8227; Delete unnecessary entries
&#8227; Enable "Pretty colors" [/INDENT][/INDENT]
&#8226; **[COLOR="Red"]Change theme[/COLOR]** Well, when everything is else is done I would love to have a black theme.
&#8226; [COLOR="Green"]**Super key doesn't do anything**[/COLOR] *// solved *
[INDENT]&#8728; System -> Preferences -> Keyboard -> Layouts -> Layout Options -> Alt/Win key behavior -> Super is mapped to the Win-keys[/INDENT]

 

That is it for now, I would really appreciate any help on my issues and I will keep this post updated.

Thank you for your time!

Edit: Updated the post, [COLOR="Green"]green[/COLOR] means I solved this problem, [COLOR="Red"]red[/COLOR] means this is stuff I still hope to get to work.

---

### Post by 73ckn797 on 2008-10-15
Cannot address all concerns at once and too new to be able to. Check the following thread on how I got an ATI graphics card working.

[http://ubuntuforums.org/showthread.php?t=902913](http://ubuntuforums.org/showthread.php?t=902913) 

Search the threads under each area that you raise questions about.

Enjoy the ride.

---

### Post by Ms_Angel_D on 2008-10-15
> **Markstar said:**
> Hi,
&#8226; **[COLOR="Red"]Keyboard driver (Logitech G11)[/COLOR]** This keyboard has extra function keys that I would love to use also in Ubuntu
&#8226; **[COLOR="Red"]AVC-codec for videos[/COLOR]** So I can play my HD-movies
&#8226; **[COLOR="Red"]Virtual Desktop (like VMWare)[/COLOR]**
&#8226; **[COLOR="Red"]Wine[/COLOR]** While I don't like to drink it, I hear it is rather nice to get Windows programs (and games :p) to work
&#8226; **[COLOR="Red"]Mouse scrolls one page[/COLOR]** Grr, can't find the option where to turn this on. 
&#8226; **[COLOR="Red"]Clean up Grub menu[/COLOR]** To many entries and I would like to default to the last OS that was booted. I also hear it can be made to look nicer. :p
&#8226; **[COLOR="Red"]Change theme[/COLOR]** Well, when everything is else is done I would love to have a black theme.

That is it for now, I would really appreciate any help on my issues and I will keep this post updated.

Thank you for your time!

[LIST]
[*]Search Synaptic for G15 the drivers for the G11 and G15 are the same, and install g15daemon, libg15-1, libg15-dev, libg15render1, libg15render1-deb also here's some further documentation [https://help.ubuntu.com/community/LogitechG15](https://help.ubuntu.com/community/LogitechG15)
[*]Add the [medibuntu]("http://www.medibuntu.org/") repository and have a look at [this guide]("http://ubuntu-tutorials.com/2008/01/29/medibuntu-the-only-3rd-party-repo-i-use/")
[*]Virtualbox is in the repos check add/remove programs
[*]Wine - I recommend [Ubuntu Tweak]("http://www.ubuntu-tweak.com") you can install Wine using it as well as configuring a few other handy things in ubuntu.
[*]Mouse - Firefox > Edit > Preferences > advanced > Use autoscrolling
[*]Not sure about the grub thing sorry
[*]Theme [http://www.Gnome-look.org](http://www.Gnome-look.org)
[/LIST]

Hope this helps some :wink:

---

### Post by cariboo on 2008-10-15
> &#8728; Problem #1.1: Installing via Synaptic didn't work (can't run native resolution of 1920*1600)

    &#8227; download package from [http://ati.amd.com/support/drivers/](http://ati.amd.com/support/drivers/)

&#8728; Problem #2: Can't do anything with .run file

    &#8227; right-click on file in file browser -> Permissions tab:
    &#8227; Check "Allow executing file as program"

&#8728; Problem #3: ati-driver-installer....run must be run as super user - how does a newbie do that?

    &#8227; [terminal] navigate to downloaded file, then: sudo ./ati...

        • log file: /usr/share/ati
        • advanced configuration: [terminal] aticonfig

Installing a driver from source is usually beyond a newbie, but here goes:

Press Ctrl-Alt-F1 this will take you to a console, at the prompt type:

```
sudo /etc/init.d/gdm stop
```

Enter the password you setup during installation.This command stops the gnome desktop manager, I'm going to assume you downloaded the .run file to your desktop

```
chmod +x ~/*run
```

This makes the .run file executable

Next install build-essential:

```
sudo apt-get install build-essential
```

Then run the file:

```
sudo ~/*run
```

This runs the .run file as root, you need to be root to install anything in Linux. If it is anything like the Nvidia driver answer yes to all the questions. Once the driver installation is finished.

```
sudo /etc/init.d/gdm start
```

You really shouldn't need to do all of the above, There is a utility called envy in the repositories that automates the above process. Envy and envy-gtk are available in the rpeositoires, use System-->Administration-->Synaptics package Manager to install them, just hit the search button and search for envy.

> Access Windows network (client and host) I simply must access my files on other Windows computers as well as share the files with the others 

Ubuntu can access windows shares by default, the only problem may be the workgroup name. To set the workgroup name you will have to install samba, which you will need for the windows computers to see shares on your unbuntu computer. Here is the quick way, in a termianl type:

```
sudo apt-get install samba
```

To change the workgroup name press Alt-F2 and type:

```
gksu gedit /etc/samba/smb.conf
```

This will open a test editor so you can change the name of the workgroup. THe default workgroup in Ubuntu is WORKGROUP, change to your work group name, then save and exit the file. Now you have to restart sambe for the change to take effect. In a terminal type:

```
sudo /etc/init.d/samba restart
```

For setting up shares in samba see this:

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

This is a howto for an older version, but it will still work. I've been using the same basic samba configuration file for at least eight years and it has kept working through all the updates and different Linux distributions I have used over the years.

> Programming C++ Currently only basic compiling needs, but need to get QT working soon as well? Which packages to install for GNU-C++ (g++)?

The build-essential meta package that you would have installed earlier installa all the basics you need to compile programs form source. For QT just do a search using synaptic for QT most of the libs, and even QT-designer will be listed.

Jim

---

### Post by Markstar on 2008-10-15
Thank you guys! 

About the ATI drivers: I did get to install it, however, I can't seem to get the dual monitor thing to work and overclocking (or in my case underclocking) the card is also something that I would like to do. 

I will work through the list tomorrow!

---

### Post by Nancy Dz on 2008-10-15
I am very new here myself, but have a book with some trouble shooting options.

For a jittery Dvd playback problem...the book says in most cases that DMA for your DVD drive is not enabled. 

You can check weather it is running by entering this command:

sudo /sbin/hdparm /dev/hdc | grep dma

If it is disabled you will see:

using_dma = 1 (on)

To turn on DMA mode, enter:

sudo /sbin/hdparm -d1 /dev/hdc

If you can play DVD's just fine after that, it says that you should edit /etc/hdparm.conf (which I am assuming is a file in the etc folder on your hard drive) and add the following:

/dev/hdc {
dma = on
}

Hope that fixes it for you.  :)

---

### Post by Markstar on 2008-10-16
@MetalHellsAngel: Thanks, I will work on it. Right now I'm working on the Samba issue. But it is certainly good to hear that there is a way to get my G11 to fully function under Ubuntu! :)

@cariboo907: I followed your post and I am working through the other tutorial right now. Some questions though:
> -> path = /media/samba/

This suggests that you've mounted an hard drive or partition on /media/samba where all the shared files will be stored.How do I mount my partitions to that (or any) folder? 

I used the Ubuntu online documentation as well as Google, but couldn't find anything. :(

For example, in the documentation [here ]("http://library.gnome.org/users/user-guide/stable/gosnautilus-460.html") it says:
> The removable media has an entry in the /etc/fstab file. The /etc/fstab file describes the file systems that the computer uses.
But there is no fstab folder, even after I mounted one of my partitions (there is, however, now a folder in /media with my newly-mounted partition's name). :confused:

- What does *force group* mean?

Also:
- I noticed that when I create a new (text) file and edit it, a *.*~ file is created (e.g. test.txt~). Is that normal? Doesn't that take up quite some space after some time? Can I disable it (under Windows, the first thing I do is disable the Recycle Bin)? Or is it really recommended to leave it on, even if one makes backups of important system files before messing around?

@Nancy Dz: Thanks, but it's not just my DVD-drive, it's also the files on my computer. Even worse, the movie player also flickers when I just load an mp3 file (the sound is fine, but there is an animation in the window which I believe could look quite cool if it weren't for the heavy flickering). 


Alright, Windows networking is solved and I will try to work on the other issues. However, some other **very important** questions remain:
- What to use as a file manager?
- Which editor to use for programming?

Kind regards
  Markstar

---

### Post by Markstar on 2008-10-16
(This is an addition to my previous post.)

@MetalHellsAngel: I installed all the packages as you wrote. As this didn't work, I looked at you link which gave me some additional steps, but the G-keys still won't work. I can select the keyboard under System>Preferences>Keyboard>Layouts, but the M1-M3 buttons do not glow (usually one of them glowed depending on which one is activated) and I can't assign anything to the G-Keys.

I have installed medibuntu, I'll take a look at the media files on the weekend, as well as Virtualbox and Wine (and the Themes when there is time). 

> [*]Mouse - Firefox > Edit > Preferences > advanced > Use autoscrollingThis did not work. Also, I would like to scroll one page in all applications, not just Firefox. 

@cariboo907: In addition to the mounting problem, I also can't see the files shared by other computers (meaning I see the computers in *Places -> Network*, but the folder seems to be empty (even though there should be several shared partitions/folders). 

> The build-essential meta package that you would have installed earlier installa all the basics you need to compile programs form source. I'm sorry, what do you mean by that?


[I think I will open separate threads for my problems after all, this just gets way too complicated]

---

### Post by Ms_Angel_D on 2008-10-16
> **Markstar said:**
> (This is an addition to my previous post.)

@MetalHellsAngel: I installed all the packages as you wrote. As this didn't work, I looked at you link which gave me some additional steps, but the G-keys still won't work. I can select the keyboard under System>Preferences>Keyboard>Layouts, but the M1-M3 buttons do not glow (usually one of them glowed depending on which one is activated) and I can't assign anything to the G-Keys.

I have installed medibuntu, I'll take a look at the media files on the weekend, as well as Virtualbox and Wine (and the Themes when there is time). 

This did not work. Also, I would like to scroll one page in all applications, not just Firefox. 

You may wish to have a look at the [G15tools website]("http://www.g15tools.com"), they have support forums over there. I wish I could be of more assistance, in that area.

You may wish to take a look at mouse settings under the control center and see you can adjust some settings that way.

```
system > Preferences > Mouse
```

Else You may wish to try Google and see what you can come up with for your mouse.

Wish I could help further, but I'll be honest with you The LCD on my G15 works great, but I to was never able to get the gkeys working. Which sucks as I would like to be able to configure some compiz shortcuts using them. I have heard people have more success with the G11 gkeys though, hence my reason for sending you in that direction.

Angel

---

### Post by Markstar on 2008-10-16
> **MetalHellsAngel said:**
> You may wish to have a look at the [G15tools website]("http://www.g15tools.com"), they have support forums over there. I wish I could be of more assistance, in that area.Yes, I'll post there, I guess. But you have been a great help, thank you! :)

> You may wish to take a look at mouse settings under the control center and see you can adjust some settings that way.

```
system > Preferences > Mouse
```

Else You may wish to try Google and see what you can come up with for your mouse.I couldn't find anything in the preferences and Google wasn't much help either. It's not a big deal right now, maybe I'll figure it out later. 

> Wish I could help further, but I'll be honest with you The LCD on my G15 works great, but I to was never able to get the gkeys working. Which sucks as I would like to be able to configure some compiz shortcuts using them. I have heard people have more success with the G11 gkeys though, hence my reason for sending you in that direction.

AngelI'll try to work on it some more and let you know how it goes. 

Thanks again, I really appreciate any help on this! :)

---

### Post by waltons_pacman on 2008-10-22
> **Markstar said:**
> 
&#8226; **[COLOR="Green"]Keyboard driver (Logitech G11)[/COLOR]** This keyboard has extra function keys that I would love to use also in Ubuntu
[INDENT]&#8728; I did the steps from [this page]("https://help.ubuntu.com/community/LogitechG15") (thx MetalHellsAngel). G-keys work now. :)
&#8728; [COLOR="Red"]_Issue left_[/COLOR]: 
[INDENT]&#8227; M-keys work as shortcut but do not activate different sets of G-keys.[/INDENT][/INDENT]


if you want the G1-18 keys, M1-3, and MR keys to work correctly, follow the [solution]("http://ubuntuforums.org/showthread.php?t=946150&highlight=g11%2C+g15%2C+logitech") reply i left in my forum.
using the last section on g15macro, i was able to get g1-18 bound to any combination i want, and M1 M2 and M3 all change to different 'sets' of G1-18 keys.

hope that helps.

---

### Post by prince_niceguy on 2008-10-22
Have you tried upgrading to Ibex? I too have 780G chipset and seems there is much better support in Ibex than it was in hardy.

---

### Post by Markstar on 2008-10-24
> **prince_niceguy said:**
> Have you tried upgrading to Ibex? I too have 780G chipset and seems there is much better support in Ibex than it was in hardy.No I haven't... how do I do that? Is there a update function somewhere?

---

### Post by prince_niceguy on 2008-10-24
Use the following commands to update. It is going to be released on 30-Oct, but it is stable enough for use.

press alt + F2.

```

sudo update-manager -c -d

```

Give your password and it will display a new distribution release avaible 8.10. Select upgrade and wait for things to be downloaded. Once done you are all set with 8.10. Check out if it resolves your issues.

---

### Post by Markstar on 2008-10-24
> **prince_niceguy said:**
> Use the following commands to update. It is going to be released on 30-Oct, but it is stable enough for use.

press alt + F2.

```

sudo update-manager -c -d

```

Give your password and it will display a new distribution release avaible 8.10. Select upgrade and wait for things to be downloaded. Once done you are all set with 8.10. Check out if it resolves your issues.ALT + F2 didn't work, but it did work in the terminal so I am downloading the updates right now (it said 686MB ... that's pretty much the whole CD :rolleyes: ). 

I'll let you know how it goes, but I doubt many of my problems will be resolved by this (like the Thunderbird issue, etc).

---

### Post by prince_niceguy on 2008-10-25
So how did it go? did the install fix the resolution issue? 

for AC3... in the switches just enable i394 or i984 do not recall it. You should get that option anyways you will understand what I am saying :-)... Then use kaffeine or vlc media and audio options select passthrough, then your ac3 will come out of the optical output. One caveat... do not use mplayer as I have experienced it screws up the sound system when you select optical output in the same for audio playback... then you will end up removing and reinstalling te alsa.

Installing wine is easy.. just type

```
sudo aptitue install wine
```

for thunderbird and firefox I am assuming you are keeping a profile on a shared drive between your windows and linux box. Make sure your file permissions are same.

have you tried kate or gedit... kate has more features compared to gedit, but you can install more plugins from the repository using synaptic.

---

### Post by Markstar on 2008-10-29
The installation is not going very well at all. :(

Even though I have been working on Ubuntu quite a lot in the recent weeks, I have still not much closer to the solution in most of my problems. Actually, with the update to 8.10 things got even worse as not the system is even less responsive than before (always >20% CPU utilisation, video runs very slow sometimes - all in all A LOT worse than on XP). :mad:

I will continue to work on it as I am determined to get Ubuntu to a state where I can be productive again, but it is very frustrating and definitely not for the faint-hearted. I have yet to write my first line of code with it, heck, I can't even check my emails without copying the mail folder first. :mad:

Oh well, I'll keep you guys updated.

---

### Post by prince_niceguy on 2008-10-29
seems the desktop effects got enabled as it found the latest version of fglrx drivers. try disabling the desktop effect, that should reduce the cpu usage.

---

### Post by Markstar on 2008-10-29
> **prince_niceguy said:**
> seems the desktop effects got enabled as it found the latest version of fglrx drivers. try disabling the desktop effect, that should reduce the cpu usage.I enabled compiz because of some features (keyboard shortcuts, etc). 

But that doesn't mean the computer should have 20%+ load without even moving the mouse - that's just ridiculous!

BTW, I have not had time to do the AC3 thing, will do so tomorrow as well (I hope).

---

### Post by prince_niceguy on 2008-10-29
thats true but some how i have found that ati drivers are not that good at desktop effects, anyway mine is media center pc so keep it without the effects.

see if disabling helps or not.

---

### Post by steveneddy on 2008-10-29
I have two suggestions for you.

[B]Tackle each issue individually, solve it and move on to the next item of concern.

Second, post a separate thread for your most important issues individually.[/B]

This method has kept me from pulling all of my hair out.

1. Stability, reliability. Does it boot every time to the same configuration.

2. Video. Once the system is stable, video should be next.

3. Sound. If that is important.

4. Other hardware concerns including networking and remote file sharing/retrieval.

5. Wireless. If so equipped.

7. Compiz last. Get all of your other issues addressed and solved because Compiz will tear the whole house down if the video isn't just right.

These are my opinions only and represent my .02

---

### Post by Markstar on 2008-10-30
@prince_niceguy: No, disabling compiz did not bring a noticeable improvement. CPU-load is still about 20%, even though now at least it goes down to 10% from time to time (only for a fraction of a second, though, and it also goes up to 30% quite often)

> **steveneddy said:**
> I have two suggestions for you.

**Tackle each issue individually, solve it and move on to the next item of concern.**This does make sense and this is why I divided my first post into priorities. However, the sad truth is that if I had only moved on to the next problem after solving the previous one, I'd still be nowhere because nothing is working 100%, even after almost 3 weeks. :(

> **Second, post a separate thread for your most important issues individually.**

This method has kept me from pulling all of my hair out._I have:_

[b][CPU underclocking]("http://ubuntuforums.org/showthread.php?p=5998955#post5998955")
[CPU/graphic undervolting]("http://ubuntuforums.org/showthread.php?p=5999430#post5999430")
[Adjust fan speed]("http://ubuntuforums.org/showthread.php?t=949658")
[Search for a better file manager]("http://ubuntuforums.org/showthread.php?p=6002725#post6002725")
[Installing Xfe]("http://ubuntuforums.org/showthread.php?p=6018306#post6018306")
[Configuring G11 keyboard]("http://ubuntuforums.org/showthread.php?p=6012321#post6012321") and [here]("http://ubuntuforums.org/showthread.php?p=6012718#post6012718") 
[Mounting partitions]("http://ubuntuforums.org/showthread.php?t=953659")
[Mouse scrolling]("http://ubuntuforums.org/showthread.php?p=6002805#post6002805")
[Problems with Thunderbird & Firefox]("http://ubuntuforums.org/showthread.php?p=6011785#post6011785")
[Configuring "Places"]("http://ubuntuforums.org/showthread.php?p=6058615#post6058615")[/b]

Most of these items are still open to be solved (and I have some more issues as well which I am not even addressing at the moment).

Oh well, I am still determined to get away from Windows, even though Ubuntu has proven to be a pain in the *** so far and my girlfriend keeps telling me to give it up already and go back to what I'm good at.

---

### Post by prince_niceguy on 2008-10-30
which process is taking the highest cpu. Can you open a terminal and type top, that should given some idea what is taking chunck of your cpu. Hope it is not tracker as it indexes data, but that should come down after some days when it has completed indexing.... post the result of top and then we can figure out what is going wrong.

On my computer running kde4.1 my cpu usage is around 10% max in idle inspite of having ktorrent running full time.

---

