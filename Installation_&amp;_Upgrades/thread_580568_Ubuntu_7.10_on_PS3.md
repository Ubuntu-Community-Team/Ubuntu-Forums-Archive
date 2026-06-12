---
title: "Ubuntu 7.10 on PS3"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by anoolio on 2007-10-18
I've just downloaded ubuntu-7.10-desktopo-powerpc+ps3.iso and am wondering if anyone has tried to install this or upgrade their PS3 7.04 install? Any issues or advice on doing this would be really appreciated.

---

### Post by LincolnT24 on 2007-10-19
yea i installed all 7.04 updates as it is required before upgrading to 7.10. i then ran the upgrade from the update manager menu, the installation went thru just fine (took bout 6 or 7 hours total with cable modem) but ran ito issue at first boot...it freezes at "booting system" *****anyone with same problem kno how to fix this? by the way i'm kindof a noob only had ubuntu 7.04  for a coupl weeks before upgrading 
thanks in advance.

---

### Post by whocarez_pt on 2007-10-19
Hi,

I'm having the same problem after upgrading from 7.04

Carlos

---

### Post by esso1974 on 2007-10-19
Same problem here :-(

Jimmy

---

### Post by mr_burns on 2007-10-20
No love here either...7.10 failed to boot after I used the upgrader tool in 7.04.

---

### Post by Onay on 2007-10-20
Has anyone tried doing a clean install? I've always had problems using the upgrader in my PC install, but clean installs usually seem to work.

---

### Post by oddroot on 2007-10-20
I had 7.04 installed on my PS3. I did the upgrade method. Also I followed the couple extra notes in the release notes for the ps3 and added the cell kernel:

$ sudo apt-get remove linux-image-powerpc64-smp linux-powerpc64-smp linux-restricted-modules-powerpc64-smp
$ sudo apt-get install linux-cell

After rebooting gutsy won't boot into X... Got errors complaining about the FBDEV in the log file. In looking elsewhere on the internet they had the UseDBDev commented out, so I tried that... Now it complains that I don't have the vesa module...

I'm a RH/Fedora guy so I mostly know my way around...

So 7.10 installed on a PS3, yes (through upgrade method in gnome), working properly after reboot, no...

Those of you that is seems like it mostly boots, but seems to be trying to reload the screen or something, you can hit ALT+CTRL+F1 to go to a command line terminal. You may be able to repair the installation from the command line.

---

### Post by whocarez_pt on 2007-10-20
i didn't find any solution, so the next step was dl alternate iso image and installing.
With sucess (minus the kernel problem - you have to select the correct kernel).

---

### Post by oddroot on 2007-10-20
So further to my issue of X not starting up properly. I switched over to terminal 1 (alt+ctrl+f1), and logged in.

cd /etc/X11
sudo /etc/init.d/gdm stop
sudo mv xorg.conf xorg.conf.default
sudo /etc/init.d/gdm start

And now it works... Mind you I also issued a 

psvideomode -v 5 
(1080p here)

But I don't think that influenced anything. Basically as far as I can tell the default xorg.conf for the ps3 is bogus. If you move it (mv commands above) and let Ubuntu reconfig it, it seems to work.

---

### Post by Spankmaster79 on 2007-10-20
> i didn't find any solution, so the next step was dl alternate iso image and installing.
With sucess (minus the kernel problem - you have to select the correct kernel).
did it really work??? I tried the alternate cd using the "linux-image-2.6.22-14-cell" Kernel and my system won't boot either....

---

### Post by oddroot on 2007-10-20
I had 7.04 on my ps3 this morning, did the upgrade procedure through gnome... Changed the kernel to the cell one... then rebooted. Aside from X not working, which i've detailed how I made it work above, everything seems to be good now :) 

Just testing out the wireless... GigE works though. (albeit it didn't seem to get a dhcp address by default, i had to assign it an ip address manually through command line) 

Maybe a reboot or two to see what state it comes up in on it's own is merited here :)

---

### Post by mr_burns on 2007-10-20
After my upgrade from 7.04 failed yesterday, I tried again today with a fresh install from the CD.  This didn't work either.  The install got hung up copying some files and froze.

Oddly enough, the screen resolution for the live image CD was stuck at 570x350 (approximate numbers), which made it impossible to see the dialog boxes properly for the install questions like name, location, password, etc.  Strange.

Anyone have thoughts about how long it might take for the bugs to be fixed?  I "joined" the linux community this summer, so I don't have experience from prior upgrade releases.

---

### Post by oddroot on 2007-10-20
another thing i've discovered is the kboot.conf file got overwritten in my upgrade... it was missing a key part to one of the lines that would enable it to start at the proper resolution: (/etc/kboot.conf)

the line that lists either linux or ubuntu or whatever

linux='/boot/vmlinux initrd=/boot/initrd.img root=UUID=xxxxxxxxxxxxxxxxxxxxxxx **video=ps3fb:mode:5** quiet splash'

The mode 5 corresponds to 1080p (YUV 60hz)... try ps3videomode -h for the different modes.

This will atleast bring things back to a better resolution.

So if you can get booted somewhat, hit alt+ctrl+f1 and log in... edit your /etc/kboot.conf and add the video stuff and reboot.

---

### Post by oddroot on 2007-10-20
See also:

[http://psubuntu.com/forum/viewtopic.php?t=13](http://psubuntu.com/forum/viewtopic.php?t=13)

for more of a description for getting full 1080p as well as getting X, and kboot done up properly with a better description than mine.

---

### Post by Cyberbian on 2007-10-21
I installed over an install of Yellowdog 5.2 that I couldnt get my Logitech bluetooth keyboard for PS3 to work with.

Only problem so far is the screen size is 300 by 200 or some such rubbish.   So I can't reconfigure in the GUI. I use a wireless connection which probably kept it from finding drivers for my 42" HDTV monitor. 

I'm going to move my Router temporarily to udate, and hopefully there will be more display options than the one available. 


The wireless config is too big a dispaly to see all of it on the screen and I can't shift offscreen top and bottom to complete correctly.

---

### Post by Cyberbian on 2007-10-21
Sorry OddRoot, I had not read the second page. So I missed your great entry just above my previous.

Thanks for the great soluton to the problem. 
Your a life saver!

I'll kick up the changes you suggested first chance. 

Rock on OddRoot!

---

### Post by isaac.tanner.madsen on 2007-10-21
I installed Kubuntu 7.10 (Gutsy) on my PS3 - few problems, and most of them easy enough to handle. Here's my HOWTO for those interested: 

[http://ikerspot.blogspot.com/2007/10/howto-install-kubuntu-710-gusty-on-ps3.html](http://ikerspot.blogspot.com/2007/10/howto-install-kubuntu-710-gusty-on-ps3.html)

---

### Post by Onay on 2007-10-21
a few things about your tutorial...

You might want to include the part where you need to format the disk and alot 10gb for the separate OS (and wipe all ps3 data).

Would I be better off installing Ubuntu using the alternate disc? Is it safer or more stable?

---

### Post by isaac.tanner.madsen on 2007-10-21
Thanks. I'll go back and edit the tutorial at some point in the next couple of days. 

I don't know if you'd be better off or not. The alternate Kubuntu CD was the only one I could find the other day. I don't know if they've put more up yet, but it worked fine. It's not a LiveCD or a graphic installer. Just an old-school installer. I don't know if that makes a difference for anyone. Works great though. I'll have to go back and try oddroot's 1080p trick. That looks useful. If it works, I'll add the link to my tutorial.

I go pretty in-depth as it is though, so I don't want to add too much. I like to keep things as simple as possible (which setting Kubuntu up through the alternate CD was not - took a couple days to figure everything out). I'll probably be adding a note or two about the network connection as well. I had to configure a couple of things as I was doing a fresh install while writing the tutorial. That took about 2 hours.

---

### Post by isaac.tanner.madsen on 2007-10-21
Also (not quite related to my last post), while using a live CD at low resolution, you can move things around by holding Alt and dragging the program with your mouse. That allows you to see everything you need to (though you still won't be seeing the entire screen at once).

---

### Post by Bimme on 2007-10-21
I finally did it, but as it seems a little more complicated than you others. Thank you all I wouldn't have made it without your tips.

Here is how I did it:
Installed Feisty 7.04 and updated all packages necessary (reboot).
Copied an iso of the alternative install disc for gutsy 7.10 and mounted it with the following commands (since gnome is ejecting the disc):

sudo bash
mkdir /mnt/gutsy 
mount -o loop -t iso9660 image.iso /mnt/gutsy

After this, all you have to do is start the installation:

/mnt/gutsy/cdromupgrade

After a couple of hours when it's finished you should probably install the correct kenel as described earlier in this thread, but I "forgot" to do it.
After reboot, it just crashed the system (The PS3 turned off the power flashing red!)
So I neded some rescue...
type sh in kboot to get a prompt.

chroot /mnt/root bash
mount -oremount,rw /

now edit /etc/kboot.conf to include a new line with the old kenrnel (if it didn't already exist, I had removed mine)

nano /etc/kboot.conf

The new line should contain vmlinux.old and initrd.img.old. Save with ctrl-o and exit with ctrl-x.
type reboot.

Now it will boot the kernel, but no window system and no network. It is also complaining about sdc and sdd once or twice every second. Fix the window system as described earlier in this thread.

Now fix the network by clicking the network icon and change it from roaming mode to dhcp.

Now you can update the kernel as described before in this thread.

Finally after restart it didn't find /dev/sda1 as specified i kboot.conf.
type sh in kboot and use chroot and mount... edit kboot.conf to have root as /dev/ps3da1
(My first installation of feisty failed because it was set to /dev/sdd1, changed it to /dev/sda1).

Now it finally seem to work!

---

### Post by mgillespie on 2007-10-21
7.10 is horibly broken on PS3.

I did a clean install, and these are the problems I observed on my 60GB Euro PS3.

1/ Screen resolution wrong during install, making the dialogs too big to do anything.

2/ After install, wired networking is broken

3./ After install, wireless networking is broken.

4/ Screen resolution is WAY too low, and locked, unable to change.

5/ Hang during shutdown, have to push and hold the I/O button for 10 secs or so, to force a power down.

I can't believe Ubuntu team did ANY QA on the PS3 release at least.

---

### Post by Cyberbian on 2007-10-21
Apparently not. Well at least we care!

We also need our own topic for PS3. They did not even give us that, or a mention in the downloads section. Were just PS3rd class netizens!

---

### Post by Maci_01 on 2007-10-21
PS3 has what, a 7 million person userbase? I wish the Ubuntu team realized its potential.

Isaac, I really appreciate the guide and will see how it goes.

Edit: Didn't work at all. I used Ubuntu not Kubuntu though. I was unable to correct the resolution and networking issues with a clean install (they worked in 7.04 though).

---

### Post by Astaroth_PoD on 2007-10-23
I did a clean install with the regular 7.10 ps3 cd, and had the problems mentioned here - resolution was too low (had to use Alt to move the installer around), after install no wired or wireless network available, no resolution selection in the X environment (don't know if that is possible though...) and the machine hangs alltogether on reboot. In addition, my keyboard/mouse doesn't work unless I replug the dongle after the OS boots. All of these worked fine on both Gentoo and Yellowdog. (2.6.16)

I was able to fix the resolution using ps3videomode, and have it stick on reboot by adding "video=ps3fb:mode:133" to the linux line in kboot.conf (1080p fullscreen YUV).

Wired networking works if you append the following to the file /etc/networking/interfaces:

auto eth0
iface eth0 inet dhcp

I haven't yet looked at the wireless since I don't use it, nor have I been able to do anything about the hang on reboot or the mouse/keyboard dongle replug.
7.10 still needs some major work :(

---

### Post by IMOC on 2007-10-23
I also did a clean install with the 7.10 PS3 live CD.  It went on okay with the following issues:

* Resolution too low during install - not a show-stopper as you can hold down ALT and move the windows around.
* Resolution too low after install - edit kboot.conf and add video=ps3fb:mode:XX as described in posts by others.
* Wired networking does not work straight away - this started working while I tried to get wireless working.  The post by Astaroth_PoD seems to have a fix for this.
* Wireless networking does not work straight away - I didn't chase this up as I have wired access available.
* Playing/ripping CDs does not work.

On the plus side some things I have found fixed in 7.10.

* Shutdown and restarts work without hanging now.
* Auto mounting a network drive using samba in /etc/fstab now works.

So it seems that the PS3 port still needs some effort to work out of the box, but it is slowly getting there.

---

### Post by sanosuke001 on 2007-10-23
I just recently tried to install 7.10 on my PS3 and had the same problems everyone else is having. I ended up installing 7.04 instead as I am new to the PS3 and didn't want to cut my teeth on a semi-defunct install. 

However, I have a 1080i HDTV and when setting my resolution to 4, I get the black bars. OK. I expected that. I set it to 132 and it goes off the screen. Again, expected. I went to my TV menu to try and find the setting for it to fit it but couldn't. Is this option not on all TVs? I have a Panasonic LCD (don't remember the model. If it's important, I can post again when I am home.)  If it's just not supported by all HDTVs then I can live with the black border but was curious if anyone knew for certain.


Also, I was looking to mess around with programming on the PS3 specifically using the SPEs. Anyone know of a good beginners guide or a API for programming for the PS3? Thanks!

---

### Post by Astaroth_PoD on 2007-10-24
> **sanosuke001 said:**
> However, I have a 1080i HDTV and when setting my resolution to 4, I get the black bars. OK. I expected that. I set it to 132 and it goes off the screen. Again, expected. I went to my TV menu to try and find the setting for it to fit it but couldn't. Is this option not on all TVs? I have a Panasonic LCD (don't remember the model. If it's important, I can post again when I am home.)  If it's just not supported by all HDTVs then I can live with the black border but was curious if anyone knew for certain.

The fullscreen/1:1 pixelmapping/full pixel/no overscan etc etc option is only available on some HD screens - usually the 1080p ones and some others that are newer. You'll probably have to live with the overscan issue, take comfort in knowing people are working on making it possible to adjust the black border width though.

---

### Post by sanosuke001 on 2007-10-25
> **Astaroth_PoD said:**
> The fullscreen/1:1 pixelmapping/full pixel/no overscan etc etc option is only available on some HD screens - usually the 1080p ones and some others that are newer. You'll probably have to live with the overscan issue, take comfort in knowing people are working on making it possible to adjust the black border width though.

Yah, I kind of expected that. The border isn't too bad as long as the resolution is higher than 536x400 or whatever the default was I'm happy.

---

### Post by Spankmaster79 on 2007-10-26
I'll have to say it's not all too bad. I installed from the Alternate CD and used the (probably older) "linux-image-2.6.22-14-cell kernel". Only reboot is not working what sucks... I can't really test all things you did, because I only use a normal TV, but as far as wireless networking goes, that worked after configuring it again with network-admin.

---

### Post by scotishhaggis on 2007-10-28
Sorry to steal the thread guys i really need a huge hand.

i tried to install 7.10 on my PS3 i partion the HD  in the PS3 gui. then installed the CD then selected Outher OS.

OK so so good . i have the install cd in the drive rebooted and taken to the kboot menu.

pressed enter to install linux. about 10 lines in to the install i get 
> ps3-echi-driver sb_05: USB bus 1 deregisterd
and it just hangs after this and does not seem to do anything

i have no clue on how to get back to the PS3 main GUI or get this installed

PLS help

---

### Post by sanosuke001 on 2007-10-29
To get back to the main PS3 menu, either type boot-game-os at the kboot: prompt or turn off the PS3 then turning it on by pressing the power button (not using the controller, on the PS3 itself) keep pressing until you hear two beeps. The first is it turning on and the second is it resetting itself to boot the PS3 OS. Both should work, but I've heard people having trouble with the command line approach with 7.10.


As for the USB problem, if you know for sure all 4 USB ports work for the PS3, I'd say its an OS problem. 7.10 is pretty buggy it seems. However, it is just speculation and I have no clue.

---

### Post by RealG187 on 2007-11-02
Does putting Ubuntu on a PS3 void the warranty? The guy at the sony store said it does (my brother bought one today!)

But I thought Sony's firmware support adding of Ubutnu and installing it does not affect or replace Sonys firmware though.

DOes this mean that I can run emulators on a PS3 and Ubutnu runs emulators, or use Firefox and torrents?

Also, there is no no to use Ubuntu to play copied PS3 games is their?

---

### Post by aysiu on 2007-11-02
> **RealG187 said:**
> Does putting Ubuntu on a PS3 void the warranty? The guy at the sony store said it does (my brother bought one today!)

But I thought Sony's firmware support adding of Ubutnu and installing it does not affect or replace Sonys firmware though.

DOes this mean that I can run emulators on a PS3 and Ubutnu runs emulators, or use Firefox and torrents?

Also, there is no no to use Ubuntu to play copied PS3 games is their?
Sony puts the ability to install another OS in the PS3 menu (see the attached screenshot), so they implicitly advocate it. They even [have instructions on the Playstation website](http://www.playstation.com/ps3-openplatform/index.html). The FAQ there mentions nothing about voiding the warranty.

If you take a look at [the actual PS3 warranty terms](http://www.us.playstation.com/Support/PS3/Warranties), there's no mention of *operating system*, *Ubuntu*, *Linux*, or anything else of the sort, let alone those things voiding the warranty.

All they say is > This warranty shall not be applicable and shall be void if the defect in the SCEA product has arisen through abuse, unreasonable use, mistreatment or neglect. 

---

### Post by RealG187 on 2007-11-02
I seen that in the menu.

So I am a PSP user and there was a stuggle to get "Homebrew" apps ([Definition of Homebrew]("http://bestwikiever.wikidot.com/Homebrew")) on it, like [Emulators]("http://bestwikiever.wikidot.com/Emulator") etc, but since there are emulators for Ubutnu I assume then I could run emulators!!!!



But any thing about backup of commercial game? Or that cannot be done yet?

---

### Post by RealG187 on 2007-11-02
BTW the menu is called the [xMB]("http://bestwikiever.wikidot.com/xMB")!

---

### Post by ninjaschwa on 2008-01-17
When I asked in store they told me it wouldn't void the insurance I got, nor Sony's warranty... guess it's up to Sony's discretion which is never a good thing :P

---

### Post by RealG187 on 2008-01-17
BTW, I knew the option was there, but the guy at the Sony Store said it would. He must not know....

---

### Post by ninjaschwa on 2008-04-16
Installing Ubuntu doesn't void the warranty, mine bust when trying to reinstall the bootloader [well technically my Ubuntu CD wasn't working fully, scratched I presume, so I used my YDL CD just to get the internet back temp and BOOM... think of a 360 ring of death on PS3 :( ] I took it into GAME and they couldn't do anything [60gb model - figures!] so I rang Sony and they're sending me a replacement tomorrow, they were made fully aware I had Ubuntu on it since I got it and it crashed during the YDL install. The guy on the other end of the phone was even asking my advice on installing Ubuntu, he never knew it was possible for other distros past YDL, which was quite suprising for tech support like...

---

### Post by RealG187 on 2008-04-16
Is there a way to mod the PS3?

---

### Post by ninjaschwa on 2008-04-18
I's have to pass on that one, at the moment Sony have limited what Ubuntu can access on the PS3 somewhat, like the GPU for a start, which means no Compiz, etc. but I'm no expert by any means it could be possible, but I think unless you have some vast coding knowledge pretty unlikely as it stands... Sony could suprise us all and allow developers to access the rest of the hardware yet...

In answer to the original thread topic, my replacement PS3 came today, works all fine and well. Installed 7.10 this morning using the _custom_ .iso file, it fixes most of the boot hangs I think as I've *so far* had seemless boot-ups, everything seems to work fine... just in the process of updating so it could all go wrong yet, who knows, will keep you posted...

---

