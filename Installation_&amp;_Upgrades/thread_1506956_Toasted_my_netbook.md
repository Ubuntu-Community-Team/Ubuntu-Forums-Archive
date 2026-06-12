---
title: "Toasted my netbook?"
date: 2010-06-10
forum: Installation &amp; Upgrades
---

### Post by dlgoldie on 2010-06-10
Hello - I have been struggling to install a good distro on my eeePC 700, with no success.  Now I've done something to it so no distro will install - I can only run an operating system from a USB stick.  And the F9 factory settings restore doesn't work either.  I've tried every distro I can find.

Any ideas for me?  Is my netbook toast?  I kinda liked it.

---

### Post by dlgoldie on 2010-06-14
Someone out there must have an answer for me!  Please help.

---

### Post by darkod on 2010-06-14
If you boot ubuntu in live mode, and open Gparted does it see the hdd/ssd?

In terminal if you run:

sudo fdisk -l

does it show it?

---

### Post by dlgoldie on 2010-06-19
In terminal, following your directions, all I get is a "greater than" > and a blinking cursor.

In my attempt to get something to install, I took off the latest Ubuntu and I now have Leeenux on the stick.

Thanks for any help you can give me.  I had left my netbook at my cabin so it wasn't until today that I could try your suggestion.

---

### Post by darkod on 2010-06-19
So, now you have ubuntu stick to boot with right?

Load the live mode and open Gparted in System-Administration.

Does it show the hdd and any partitions on it?

---

### Post by irv on 2010-06-19
> **dlgoldie said:**
> Hello - I have been struggling to install a good distro on my eeePC 700, with no success.  Now I've done something to it so no distro will install - I can only run an operating system from a USB stick.  And the F9 factory settings restore doesn't work either.  I've tried every distro I can find.

Any ideas for me?  Is my netbook toast?  I kinda liked it.

Please describe exactly what you are doing and what happen when you try to install Ubuntu. Just saying “with no success” does not tell us what you are doing and what is happening. When you try to install from the USB stick what happens? And what is it telling you? Can't it find your Hard drive? More information would help. “Toasted my netbook does not tell us what you did”?

---

### Post by dlgoldie on 2010-06-19
darko, thanks for your patience.  In this version, in system administration, I have authorizations, computer janitor, hardware drivers, install, log file viewer, login window, network proxy, network tools and partition editor.  No Gparted.  in accessories I have something called GNOME commander.

---

### Post by dlgoldie on 2010-06-19
Irv, what happenes is that no matter what distro I try to install, it gets through the complete installation but doesn't complete it.  So that when I try to boot up without the stick, I have a blinking cursor.  I can run any distro in live mode.  I've somehow removed the F9 "restore factory settings" from the drive as well.

---

### Post by darkod on 2010-06-19
You must have Gparted in live mode. It's not there in the installed version by default, but if booting in live mode it should be there.

Lets see what you have exactly. In live mode, download the boot info script from my signature, run it and post the content of your results file as explained here:
[http://ubuntuforums.org/showpost.php?p=8844901&postcount=4](http://ubuntuforums.org/showpost.php?p=8844901&postcount=4)

---

### Post by dlgoldie on 2010-06-19
what do I open the script with?

---

### Post by dlgoldie on 2010-06-19
whoops, I got it.

---

### Post by darkod on 2010-06-19
No need to open it with anything. Just know where it is because the execution command depends on the location of the script file. If it's on the desktop as in the example, you execute it in terminal with:

sudo bash ~/Desktop/boot_info_script*.sh

Type exactly, linux makes difference between small and capital letters in file and folder names. That will create the results.txt file in the same folder where the script is, in our example on the desktop.

---

### Post by dlgoldie on 2010-06-19
is this meaningful?  I can't get the boot info script to run because my cursor in terminal is custom@custom:-$

---

### Post by dlgoldie on 2010-06-19
Thanks for your help, darko and irv.  I need to stop working on this now and get on with my Saturday.  Any other thoughts will be appreciated.  I am very new at this as you can see but I love Linux when it works.

---

### Post by darkod on 2010-06-19
It might be the reason for your "problems". The prompt should be usually ubuntu@ubuntu. You might have ended up with some custom image file.

I would recommend getting a new image file, best from torrent because it checks for corruption during download.

---

### Post by irv on 2010-06-19
Yes, and make sure you get it from [http://www.ubuntu.com/]("http://www.ubuntu.com/")

---

### Post by dlgoldie on 2010-06-21
OK, Darko and Irv - I'm back.
 
I have the netbook remix on the USB stick now and in GParted, this is what I see:

Partition  File system    size   used       unused     flags  
/dev/sda1  ext4          3.51GB  1.22        2.29 GB    boot
/dev/sda2   extended     219.64 MiB
/dev/sda5   linux-swap    219.61 MiB

---

### Post by dlgoldie on 2010-06-21
Because I'm a glutton for punishment, I tried to install the netbook remix again.  It didn't work, but now in GParted I've got:

1.0 MiB unallocated
/dev/sda1 ext4 3.51GB 2.22 GiB 1.29 GiB boot
/dev/sda2 extended 221.0 MiB
/dev/sda5 Linux-swap 221.00 MiB

---

### Post by darkod on 2010-06-21
Is /dev/sda your usb stick or the netbook SSD? It's only 4GB in size, that's too little for ubuntu install. You'll soon run out of space.

---

### Post by dlgoldie on 2010-06-21
Well, that's a good question, isn't it?  I think it's the drive, because I can see the stick on the drop down menu in the upper right corner,

An eeePC 700 only has 4GB of memory.

---

### Post by darkod on 2010-06-21
Having only 4GB SSD might explain the custom@custom you were seeing. I guess it's a watered down version of ubuntu. Have you tried Xubuntu which is for machines with smaller hdd, like yours?

I don't think you will be able to run the full standard ubuntu on only 4GB. The default installation is around 3.5GB. Maybe that's why it's not booting after install.

I think Xubuntu also has live mode, try it out first how you like it. Another option for small linux distro is Puppy Linux for example.

Or if you have your original linux that came with the netbook (if it came with linux), you can try installing that.

---

### Post by pxr on 2010-06-21
I've got a eee pc 700 that I've put Eeebuntu on in the past, but only version 2.0

you can get a copy here

[http://eeebuntu.virginmedia.com/Eeebuntu%202.0%20Editions/index.html](http://eeebuntu.virginmedia.com/Eeebuntu%202.0%20Editions/index.html)

I used the 'Standard' but didn't install any swap 'cos there's not a lot of space once its installed

I'd say once you get to the partitioning bit of the install choose the manual option then delete all the other partitions in sda and make 1 x 4.0GB partition mounted as root.

Or another choice is to use the original restore disc and create a USB stick with the disc image, that blows everything away and gets you back to the 'Fisher Price' interface.

---

### Post by dlgoldie on 2010-06-21
Bingo, PXR.  That's what I'm going to try!

Thanks everyone.  I'll post a report.

Dorothy

---

### Post by dlgoldie on 2010-06-21
PXR, what program did you use to install the iso onto the USB stick?

---

### Post by irv on 2010-06-21
Just for future thought, here is the specs on installing Ubuntu 10.04:
Ubuntu Desktop Edition

    * 1 GHz x86 processor
    * 1 Gb of system memory (RAM)
    * 15 GB of hard-drive space (although this can be split onto 2 drives, a 5Gb / and a 10Gb /home fairly easily)
    * Graphics card and monitor capable of 1024 by 768
    * Either a Cd/Dvd-drive or a Usb socket (or both)
    * Internet access is helpful

---

### Post by pxr on 2010-06-21
You stretched my memory there a bit.....

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

also available in the ubuntu repositories if you've got another machine running ubuntu just search for unetbootin in synaptic.

For the original restore disc I ripped it with k3b to an iso image then used the above. For eeeubuntu just use the download.

But DON'T 'upgrade to eeebuntu 3.0 there's not enough space to make it happen(a friend of mine tried it and locked the whole thing out). I've also got an eee pc 900 running eeebuntu 3.0, a basic install is 3.1GB leaving just over 500MB on the primary 3.7GB drive( you get a fast SSD of 3.7GB and a slower one of 'bout 15GB with a 900)

---

### Post by dlgoldie on 2010-06-21
I'm at the "create partition" screen now.  do I choose primary or logical?

Beginning or end for the partition location?

Use as ext3 journaling file system?  or other option?

And lastly, which mount point?

Thanks so much.

---

### Post by darkod on 2010-06-21
Primary.
As already mentioned, if you create one single partition from the whole SSD it doesn't matter beginning or end. Select beginning for example. You are using all space for it, right?
ext3
mount point /

---

### Post by pxr on 2010-06-21
Darkod is correct, just blow away everything and create a primary partition (ext3) mounted as '/'

damn your fast !! Hope it goes well(I'm staying up late just to check - I'm in Thailand and the time is just coming up to midnight)

Pete

---

### Post by dlgoldie on 2010-06-21
Pete, hang in there for a few more minutes.  It's almost done.  I'm really hoping this is the answer because I love this little netbook.

Dorothy

---

### Post by dlgoldie on 2010-06-21
Crap.  Go to bed, Pete, and thanks anyway.  I've got the damn blinking cursor and nothing else.  I give up, for now.

Thanks for your help, though.

Dorothy

---

### Post by pxr on 2010-06-21
Also once you get it running some of the windows will 'disappear' off the bottom of the screen, from memory its something like Alt-click-drag to move it up and get to the buttons at the bottom, but also I used to plug it into an external monitor and do any settings I needed to do.

for the external monitor to work correctly you need to reboot the X server with Ctrl-Alt-<backspace> check this out on how to re-enable

[http://ubuntuforums.org/showthread.php?t=1183156](http://ubuntuforums.org/showthread.php?t=1183156)

or just reboot.

---

### Post by pxr on 2010-06-21
try typing 

startx


did you choose auto login or something like that ?

---

### Post by dlgoldie on 2010-06-21
nothing registers when I type at the cursor.  I did not choose auto login.

---

### Post by pxr on 2010-06-21
Strange - - my 700 is in a drawer, I'll dig it out and - - I'll load up a(or is that an) USB tomorrow with eeebuntu and follow 'my own' instructions to install( it's got the original interface at the moment) and see what happens.

You should be able to send me a note to my personal email from this forum - I've got that option turned on - then we can catch up tomorrow my time, probably later today your time.

Or you might want to try again(to install eeebuntu) and select the auto login, I think it's on the screen where you choose your user name and password

---

### Post by dlgoldie on 2010-06-21
Ok, what the heck.  I'll try it.

---

