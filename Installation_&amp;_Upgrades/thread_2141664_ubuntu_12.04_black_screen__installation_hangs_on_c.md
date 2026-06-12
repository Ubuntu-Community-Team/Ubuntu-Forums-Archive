---
title: "ubuntu 12.04 black screen / installation hangs on copying files"
date: 2013-05-03
forum: Installation &amp; Upgrades
---

### Post by nahak on 2013-05-03
I want to install Ubuntu 12.04 on HP ProBook 6440b.
There were four primary partitions on this computer: system, windows 7 files, recovery and hp tools. I removed system partition, reduced windows 7 partition and made two partitions for ubuntu: swap (512mb) and the second one for all system and user files.
Then I wanted to install Ubuntu and after last installator page (where I [COLOR=#000000][FONT=sans-serif]chose computer's name, login and password) black screen [/FONT][/COLOR]appeared[COLOR=#000000][FONT=sans-serif]. I changed installation options to 'nosetmode' and started installation again. Black screen didn't appear but a while after copying files process started installator hanged. I wasn't able to move coursor and hard drive diode was turned off.
[/FONT][/COLOR]If anyone has any suggestions I'd appreciate it.
(Sorry for my English)

---

### Post by 2F4U on 2013-05-03
Are you installing from a CD or USB stick? Did you verify the checksum of the downloaded iso file? Can you provide more information about your hardware?

---

### Post by nahak on 2013-05-03
I tried to install from dvd. What I said earlier was about Ubuntu 12.04 64bit. Then I tried to install 12.04 32bit and it copied about 75% of files and installation's window suddenly disappeared and nothing happend in next 15min. (but I was able to move coursor or chose options from menu (for example shout down option)). But installation didn't end. Then I tried to install 13.04 64bit and it didn't boot from dvd.
Now I tried to install 12.04 from pendrive and I got the message: 'failed to load session'.
And yes - I verified the checksum of iso files.

And as I said I have three primary partitions: one with windows 7 32bit files, hp_tools and hp_recovery. And I made an extended partition with two logical ones: swap and ext4 for ubuntu. 

Hardware:
processor: intel core i5 m430
ram: 10gb
graphics: Intel Graphics Media Accelerator HD (Core i5)

---

### Post by DWade on 2013-05-04
Ok, You have most of the same problems I do.

Here is your solution to load.

Intel 1st generation I3 and I5 processors with Intel HD graphics, are not very compatible with the Linux kernel after Ubuntu 10.10, I am not sure exactly which, but even debian, and gparted. won't work correctly with some effort. 

so, do you have a HDMI TV?  
If not then you'll have to burn a CD or DVD.
When it boots up you have to start immediately pressing the F4 key, to get the Text Boot up. 

Choosing F6 installation options, you need to choose three items
acpi=off
noapci
nomodeset
Then choose item on Try Ubuntu with out installing / the live mode.

This will allow it to boot up the normal vga mode and get it set for a boot up to live cd.  But sometimes even this does not seem to work.

What happens is that both the laptop LCD screen and HDMI port are the both HDMI outputs and for some reason the output HDMI port is choosen over the main LCD screen. Or it is seen as and external monitor and the internal is to be turned off, even if nothing is connected.

When it still goes to the blank screen plug in the external HDMI TV. You still need to boot up in to the live CD with those three item choosen.  It sets up the installation properly for grub to boot you with good video.  In my case I have two linux partitions with a windows partition, and I use an older program that installed in windows to boot my partitions, even though I could use the windows loader or even grub. Anyway boot from the grub boot loader in partition 3 sda3 to the linux in partition 2 sda2, will come up with a blank or black screen.

Now I have loaded Ubuntu 13.04 into my sda3 and I was have a very bad problem with it, until I discovered the blank screen could be fixed by turnning up the brightness.

and I noticed you set up partition in ext 4 for Ubuntu, it's not bigger tham 399 gigs is it? if it is make it 399 or less. Also use 32 bit Ubuntu.  I still have not gotten 13.04 64 bit to load on my laptop.

I hope this helps

---

### Post by nahak on 2013-05-04
So I tried this solution and after i have chosen 'Try Ubuntu without installing', 'Run Ubuntu in low-graphics mode for just one session' and selected OK when 'stand by one minute while the display restarts' appeared I got black screen and nothing happend.

But I'm not sure if problem with graphic card is the only problem I have. There is no black screen problem when I try to install ubuntu 12.04 32bit with 'nomodeset' option (I don't know if this option was accepted without choosing 'try ubutnu' option - I have chosen it and started installtion). In this case I have installation windows which disappears during copying files process. But no black screen and I can move coursor or choose options from top menu.

And there is no hdmi port in this notebook. I tried to install with an external monitor connected to vga but then I had installation window on one screen and coursor on another so it wasn't the best idea.

And now I tried to install Ubuntu 10.04 and there is the same problem - I can't launch it after choosing acpi=off, noapci, nomodeset options because I get black screen and I have the same problem with copying files during installation (black screen).

---

### Post by DWade on 2013-05-04
I looked at your notebook specs, and the only thing I can see is maybe the Memory, but 12.04 should load in 2 gigs of memory.

How is your hard drive partitioned, or how do you plan to partition it.

If you have windows on the computer, use Yumi or pendrive to put your iso on a usb stick.  Your CD writer could be bad, and use Image burn to make CD's. It will verify the cd to the image or DVD.

I never had a problem with 10.04, except for must of the apps didn't work good in 64 bit, and then I found the pae kernels, and a sound issue, which was patchable.  My google gagets worked in 10.04, but google quit support it.

let me know.

---

### Post by nahak on 2013-05-10
I installed hard drive from this computer to another notebook and then ubuntu installation went fine. I installed hard drive with ubuntu to previous notebook and it works. Maybe not the ideal way to solve this problem but it took less time.
Thanks for your interest.

---

### Post by DWade on 2013-05-10
Check out you Bios
See if there is a update.  and install it.
Or some other firmware updates

---

