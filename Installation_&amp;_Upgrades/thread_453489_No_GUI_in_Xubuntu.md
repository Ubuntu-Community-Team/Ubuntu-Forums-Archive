---
title: "No GUI in Xubuntu"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by dogeatery on 2007-05-24
I just did a clean installation of Xubuntu on my desktop computer from the live cd and it comes up to the load screen with the logo and hten goes to text and asks me to log in, then I am given a command line.  Where is my GUI?  what do I do from this command line?  I tried restarting the computer and it still brings me back to this same spot.

It comes up and says 'Loading, please wait...'

then:

kinit: trying to resume from /dev/disk/by-uuid/45083150-1cb8-4389-b4e5-8cab8197aca7
kinit: No resume image, doing normal boot...

Ubunto 7.04 dogeatery-desktop tty1

dogeatery-desktop login:


what should I do after logging in???

---

### Post by apunc1 on 2007-05-24
[http://ubuntuforums.org/showthread.php?p=2570272](http://ubuntuforums.org/showthread.php?p=2570272)

edit: this might help also [https://bugs.launchpad.net/ubuntu/+bug/103148](https://bugs.launchpad.net/ubuntu/+bug/103148)

---

### Post by th83 on 2007-05-24
Well i am sure u must have the right one. But do you have the server edition or the desktop edition? server edition does not come with GUI

---

### Post by dogeatery on 2007-05-24
thanks for the quick reply!

So what do I do, just wait it out and then once it loads up fix it with the commands in that thread?  Do I even bother logging in?

yes, th83, it's the right one...

---

### Post by apunc1 on 2007-05-24
what is the setup of your hard disk? is it a dual boot? did you recently partition?

---

### Post by dogeatery on 2007-05-24
two blank hard disks, one containing /root and the larger one containing /home, though neither has any data on them... I also created a swap partition on each (thsi may have been unnecessary but I am new to having separate hard drives and figured 'what the hell...')

no dual boot.  if you think it's a better idea, I can just remove the installation and run gparted live cd again to reformat and try starting from scratch

---

### Post by dannyboy79 on 2007-05-24
well, I am guessing it's because of your ATI card listed in your signature. That is if you installed the Desktop verison and not the server version. So when the command line comes up, just log in using the username and password you used during the install then So that you can at least get a gui so you can do some more reasearching how to install ati drivers using xubuntu, reconfigure your X-server and change the driver to vesa for the time being. here are the steps.

```
sudo dpkg-reconfigure xserver-xorg
```
this will open debconf blue screens, chose the vesa driver at the bottom of the first screen. then just chose what ever is correct for all the questions, anytime you don't know, just accept the defaults. when it asks if you want it to save all the settings, say yes and it'll exit back to the command line. now simply issue these commands:
```
sudo /etc/init.d/gdm stop
```
```
sudo /etc/init.d/gdm start
```

OR

```
sudo /etc/init.d/xdm stop
```
```
sudo /etc/init.d/xdm start
```
If X still doesn't load, then verify that vesa is your driver by issuing this command
```
cat /etc/X11/xorg.conf | grep "vesa"
```
if it returns "vesa", than we are ok and we'll just try to restart the computer by issueing
```
sudo shutdown -r now
```
If your computer goes back to the command line and not to gdm or is it xdm in Xubuntu and you DIDN'T see a blue screen stating that X serfver failed to load, than I am guessing you installed the server version and not the desktop version. If that's the case, I can help you fix that as well.

---

### Post by dannyboy79 on 2007-05-24
> **dogeatery said:**
> two blank hard disks, one containing /root and the larger one containing /home, though neither has any data on them... I also created a swap partition on each (thsi may have been unnecessary but I am new to having separate hard drives and figured 'what the hell...')

no dual boot.  if you think it's a better idea, I can just remove the installation and run gparted live cd again to reformat and try starting from scratch

NO NO, do NOT reinstall. That's the easy way out and WON'T solve your problem if it's an X server issue.  please try my instructions at a minimum before you reinstall. You did download the Desktop verison correct? DId you use the Alternate Install CD which installs in test mode, I beleive there may have been a OEM server install option, if you chose that than I believe that you installed the server version and not the Desktop version. Again, i can heklp you with that so let me  know.

---

### Post by dogeatery on 2007-05-24
ok I wno't reinstall, I'm trying it right now.  I should have mentioned that those specs are for the laptop on which I'm communicating with you but it was what I needed, the live cd also needed me to use vesa.  how much memory should be used by my video card?

---

### Post by dannyboy79 on 2007-05-24
Ok wait, what do you mean. Please inform me of what vid card you have in your machine. Also, what happens if at that command line BEFORE logging in, hit, ctrl-alt-f7 or ctrl-alt-f8 and that should get you to xdm or whatever login manager that Xubuntu uses.

How mcuh memory you should allow for your vid card is dependent upon how much system ram you have as well as how much memory your vid card has? what it's askling you is how much of you system ram you want to share with your video card. so you really only need to set a certain amount IF your video card has less than 64mb of ram BUT if you don't have that much ssystem ram than sthat's somethign to take into consideration.

---

### Post by dogeatery on 2007-05-24
oh my god, this is getting way more complicated than an ubuntu install should be...

it started asking me in text mode to provide video memory, card drivers, monitor specs, etc.  I just went with generic everything (to see what would happen) but there was stuff I couldn't answer for sure so I got out of it completely

when I hit ctrl+alt+f8 it kicked out to:

*checking battery state...
* running local boot scripts (/etc/rc.local)

then left me a blinking cursor with no prompt...



on this note I need to be off... thanks for your help, I will see what else I can dig up later tonite.  is there a way I can get the terminal to spit out all my system specs? (it's a bit of a frankenstein)

---

### Post by apunc1 on 2007-05-24
```
lspci
```

gives a lot of hardware info

---

### Post by dannyboy79 on 2007-05-24
> **dogeatery said:**
> oh my god, this is getting way more complicated than an ubuntu install should be...

it started asking me in text mode to provide video memory, card drivers, monitor specs, etc.  I just went with generic everything (to see what would happen) but there was stuff I couldn't answer for sure so I got out of it completely

when I hit ctrl+alt+f8 it kicked out to:

*checking battery state...
* running local boot scripts (/etc/rc.local)

then left me a blinking cursor with no prompt...



on this note I need to be off... thanks for your help, I will see what else I can dig up later tonite.  is there a way I can get the terminal to spit out all my system specs? (it's a bit of a frankenstein)

hence why I informed you to accept all the defaults if you weren't aware of what to choose. The ctrl-alt-f7 or ctrl-alt-f8 was something you were suppose to try if my first steps didn't work, and just so you are aware, ctrl-alt-f1 thru ctrl-alt-f7 (or is it f8) will get you to the different getty's or tty's on your machine, you can think of them as different workspaces kind of, so if you logged into tty1 origninally and then tried ctrl-alt-f8 and nohting was there or it only showed you the boot process and no command line, than you simply hit ctrl-alt-f1 to get back to tty1. What happened after you finished with debconf dpkg-reconfigure xserver-xorg and then stoping gdm and then restarting it??? and if that didn't work, you were suppose to restart. Im wondering if you followed my instructions?

Just as a side note, I found this solution which I would like you to try
The problem was in /etc/event.d/tty1 (and tty2 etc.)
The last two lines of the files /etc/event.d/tty1 and tty2 are
respawn
/sbin/getty 38400 tty1exec /sbin/getty 38400 tty1

but should be
exec /sbin/getty 38400 tty1
respawn

you can edit these files after you log into the command line. just use nano, so the command would be
sudo nano /etc/event.d/tty1
edit the file per above and save it by hitting, ctrl-x, then it'll ask you if you want to save the changes, hit y, then it'll ask what you want to name it, just hit enter to keep the same name. Now do that for tty2 andn then issue this so that your machine restarts.
sudo shutdown -r now

After fixing each of the tty files, the machine booted fine, though it needs a little push at the end by pressing enter.

---

### Post by dogeatery on 2007-05-24
wow thanks for all the help and interest in my problem!  =D>  I am at work currently but will be off at 11 and awake into the wee hours trying your solutions and I'll report back to you duly.

regarding ctrl+f8: it began asking about things for which I could provide no information and also had no idea about and I was afraid of messing up something integral so I just powered down before I effed it all up.  

I will try running the dpkg command first off, I tried messing about and ended up having another question to ask instead of following directions like I should have.  I will also run the command you guys gave me to get my hardware specs.  (it's mostly older stuff thrown together to salvage working parts from two different computers).

---

### Post by dannyboy79 on 2007-05-24
it would help if you were more specific, ctrl-alt-f8 shouldn't have resulted in anything asking you questions? the dpkg command should have been the only thing that asked you questions and this is the 3rd time I am writing this, just accept the defaults for anything you don't know and it will be fine! BUT now that I know you haven't done what I asked he first time, please read the post I added about the /etc/event.d/tty1 changes and see if that fixes it before you run the dpkg command. Also, you haven't really answered me regarding what cd you used to install xubuntu

---

### Post by dogeatery on 2007-05-25
sorry sorry no-- ctrl-alt-f8 just gave me no prompt with a cursor, I ran dpkg and put in all the defaults and then ran xdm stop but it said xdm couldn't be found.  (suddenly wondering how I might have installed server version from the same live cd that I used to run it on this computer...)

also changed that script in tty1 and tty2, rebooted, and it still brings me back to the prompt.

I also did the check and vesa is my driver

I checked the links provided by apunc -- a bit over my head but I managed to follow someone else's lead and when I typed command sudo vol_id -u /dev/???   I got output : /dev/vcs unknown volume type

---

### Post by dannyboy79 on 2007-05-25
> **dogeatery said:**
> sorry sorry no-- ctrl-alt-f8 just gave me no prompt with a cursor, I ran dpkg and put in all the defaults and then ran xdm stop but it said xdm couldn't be found.  (suddenly wondering how I might have installed server version from the same live cd that I used to run it on this computer...)

also changed that script in tty1 and tty2, rebooted, and it still brings me back to the prompt.

I also did the check and vesa is my driver

I checked the links provided by apunc -- a bit over my head but I managed to follow someone else's lead and when I typed command sudo vol_id -u /dev/???   I got output : /dev/vcs unknown volume type

Ok well I had specifically stated that you would have to try EITHER to start xdm or gdm sinbce I wasn't sure which login manager Xubuntu used. But I have found out now, it's gdm. Ok so you're saying that you used the live cd, then chose install from the desktop correct? If that's the case I am starting to wonder if you had a bad cd, did you verify it's md5sum before burning it? Did you burn it very slowly? OH nevermind, you did state that the same live cd that worked for you was the same one that you installed frmo correct? If that's the case than it wouldn't make sence that you had a bad disc?

We need to see the output from a file to see what's going on with the boot up process. Login into the cli and do this
dmesg > dmesg.log
this will create a file and save the output from the dmesg command and put it into that file. Then I want you to attach that however you can to this forum so we can see it. an easy way would be save it to a floppy or usb stick. you can do that by putting a floppy in the drive, then mount it using this command
sudo mount /dev/fd0 /media/floppy
that;s only if the mount point /media/floppy exists. If it doesn't, than just create a mount point using
sudo mkdir /media/floppy
after the flopppy is mounted you will be able to write it using sudo. you would do that using this command
sudo cp dmesg.log /media/floppy/
this will copy that dmesg.log file onto the floppy. Now you can check if it's there by issuing this
ls -la /media/floppy/
it should show you the 1 file. then make sure you unmount the floppy before ejecting it.
sudo umount /media/floppy

OR
if you want to use a usb stick, then just insert it and see if it got automounted by using this command
mount
this should show you all the devices and where they are mounted. it most likely auto-mounted in the /media/blahblah folder, meaning it'll create a mount point for you based on the volume name of the usb stick I believe. so after the usb  stick is mounted, then just issue the same commmand to copy the dmesg.log file onto it so that then you can upload to thios forum so we can all take a look at it. this should tell us what's making your computer not boot entirely. We can go from there. good luck

OR

at this point, if you're sick of all this troubleshooting, just try a reinstall. It would probably be quicker doing that than all this troubleshooting but I just like figuring stuff out so I have the knowledge to help others that come across this point BUT there does come a time where the amount of time to troubleshoot can be a waste which we are fast approaching.

---

### Post by dogeatery on 2007-05-25
Ok I made the dmsg.log file but I am having trouble finding media to write it to... USB sticks are not being found in fstab (something I DO need to learn how to modify) and I can't insert a floppy into my laptop... I do have a CD burner but I think you're right, we are approaching 'ad absurdum' on this

I am going to make a fresh install disk and re-partition and see how it all goes.  Thanks again for all your help and patience with me.

---

### Post by dannyboy79 on 2007-05-25
WAIT, usb sticks aren't suppose to be in FSTAB. When you plug it in, it should automount and if it doesn't you can always mount it yourself. It's possible that HAL (hardware abstract layer) isn't being started and this might be why the boot process stops and why usb stick isn't automounted. All you would have to do is check out 
dmesg | tail
after you inserted the usb stick to see if it said anything about the stick. if it does say something about it, it's most likely sda1 or sdb1 (it would be sda if it's your first SATA or usb drive in the system, sdb if it's the second and so on) If it is /dev/sda, then you would mount it using
sudo mount /dev/sda /media/mountpoint
again, make sure whereever you're mounting it is already created. good luck. you could check if HAL is running using this
ps aux | grep hal
OR
ps aux | grep Hal
OR
ps aux | grep HAL
this is because I am not sure how it'll show up as upper and lower case DO matter in linux whereas in windows you can do a search for hal and it would find Hal and others. good luck

---

### Post by dogeatery on 2007-05-25
aaaaah you got me too late, it's already been wiped and I'm trying a reinstall

I did try mounting /dev/sda and also sda1 and both times it said device not found in fstab or mtab

I tried /dev  ls and it showed sda and sda1 and also disk (which my laptop often calls a usb drive) but they wouldn't mount... 

I do have a question though... when I run the live cd I have to run in safe graphics mode, if I try the normal way it kicks me to a blue screen.  would this have been the source of my problems because I installed from safe graphics mode as well.  I can replicate hte problem and read you the blue screen output if you'd like

---

### Post by dannyboy79 on 2007-05-25
ok, the reason it wouldn't mount is because you have to specify the mount point if entries are not in the fstab. so if you were just typing
sudo mount /dev/sda
then what the mount command does is parse the mtab or the fstab file and see where it should mount it to, but since sda isn't in there because it's a usb stick, then it returns that error. So, when mounting stuff that is NOT in the fstab, you need to specify where it should be mounted hence why I instructed you to use
sudo mount /dev/fd0 /media/floppy 
in my floppy example.
Anyway, the safe graphics mode should not matter but I would suggest that you use the vesa driver in order to boot the live cd in normal mode, this can be done by using this temp fix here:
Boot live cd
2) press F6 key, remove splash and quiet from line, added break=bottom<enter>
This allows all messages to scroll across the screen and the break=bottom will eventually result in a busybox prompt. it'll be initramfs prompt.
3) you need to edit the xorg.conf driver, you would type in chroot nano /etc/X11/xorg.conf
4) you should now be using the text editor called nano and have the file xorg.conf open, page down until you find the line,
Driver "whatever"
and make it so that it has vesa, so it would be
Driver "vesa"
then hit control X, this will ask you at the bottom of the screen if you want to save, hit "Y", then it'll ask if you want to name it the same, hit "Y". 
5) now you should be back at the busybox prompt, hit control D
6) this should continue with loading the live cd.

now you should be able to perform the install without it crashing or freezing. once that occurs, this all may happen again when you try to boot your new system. just follow the instrucitons once again. then you should be good to go. also, once you have your install done and you do have an ati card, you won't have good graphics at all using vesa, you'll need to look into using Envy, it's a little automatic program for installing good drivers.

---

### Post by dogeatery on 2007-05-25
alright!  This did the trick!

I changed the xorg.conf file and then went back and did the dmesg on the new install and it came up so now I have an interface!  :popcorn:

I hope the rest of it goes a bit smoother...

Thanks again for all your help and advice!

---

### Post by dannyboy79 on 2007-05-25
ok, so you're saying that a fresh install has worked this time?? Well then just chalk it up to the install not working the first time. Glad you're set now!!!

---

