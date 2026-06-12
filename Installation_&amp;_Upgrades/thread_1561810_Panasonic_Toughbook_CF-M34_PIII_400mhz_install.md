---
title: "Panasonic Toughbook CF-M34 PIII 400mhz install"
date: 2010-08-26
forum: Installation &amp; Upgrades
---

### Post by petebarchetta on 2010-08-26
Hello all,

I have a Panasonic toughbook CF-M34, i wish to install ubuntu on it, the issue i have is that it does not have a CD drive to install to. it posseses one usb port (to which only boots off a panasonic USB floppy drive and no other), one nic port and a serial port. the drive in it is fresh with no previous OS on it so i cant instigate a dual boot, although that maybe the next step. 
i think it can boot from network so a netinstall can be done, but i've never done one so assistance would be good
i know its not an easy one i've picked :)
would and install of ubuntu on a similar vintage help? or will ubuntu only build the required device drivers for its host machine. for a PIII i assume Dapper or Hardy?
all suggestions useful

---

### Post by spcwingo on 2010-08-26
For that machine I would suggest Puppy, Damn Small Linux, Slitaz, or Tinycore.  I doubt very seriously that any *buntu would run on those specs with a GUI...terminal only would probably be okay.

---

### Post by petebarchetta on 2010-10-02
Irrespective of choice of OS I still have the issue of installing it onto the drive. So far I have removed the drive and formatted it to make it bootable in windows, then run unetbootin to copy the iso over. My issue is it drops to command prompt and I can't run the command from cli as it asks for it to be run from GUI,
any ideas ??

---

### Post by snowpine on 2010-10-02
Do I understand correctly that you can connect the drive to another computer (I'm assuming that's how you did the Unetbootin thing)? If so, you can simply install on the other computer and then swap the drive back. Be sure to choose the correct options at the Partitioning and Advanced GRUB bootloader steps for the correct drive. (If you are in doubt, you can disconnect your internal hard drive for safety.) As mentioned above, Ubuntu is probably not the best choice for older hardware.

---

### Post by davidvandoren on 2010-10-02
download the Xubuntu alternate that lets you install xubuntu on a pc with less then 256 mb ram. I succeeded installing it on an asus laptop with 128 mb ram.

But make sure you download the alternate version.

---

### Post by davidvandoren on 2010-10-02
Surprisingly yes!
I switched 4days ago an old 30G hard-drive from an old 32bit single core to a four core pc and the linux mint which was on it booted up with no problems. For the fun of it I updated it before reformatting the drive and installing ubuntu.

---

### Post by petebarchetta on 2010-10-03
The donor machine the 10gb drive came from was a tosh tecra 8000, everything booted up ok apart from the xserver bombs out and goes no further so I'll try a reinstall with the drive in the tecra and copy the xorg from the site over which should take care of the oddities that are in the toughbook. Should it make any difference of the processor type the tecra 8000 is pII and the toughbook is a pIII
will see how it goes when drive goes back over

---

### Post by petebarchetta on 2010-11-03
update:
Toughbook - CF-M34 PIII 400mhz, 512mbram 10gb HD. i have found does not sport the boot from network, the putting HD in a guest machine does not allow it to install properly as it picks up guest HW and not the machine its due to go in. if possible i'd like some help on just how i can get ubuntu or Xubuntu (flavour of 'buntu is academic at this point) on this little beasty

---

### Post by P4man on 2010-11-03
> **petebarchetta said:**
> the putting HD in a guest machine does not allow it to install properly 

It should as long as you dont install proprietary drivers (and dont install 64 bit version to end up on a 32 bit machine obviously), it should work without issues. Just do a full install on any machine you want, dont install proprietary drivers,  and plug the drive in to the toughbook. Hardware is detected at boot time, not install time as with windows.

If you really insisit on another approach, it is possible somehow to install grub and make it boot an ISO on the harddrive, that you could use to install (x)ubuntu on the rest of the drive, but you will have too google for instructions.


BTW, how is windows supposed to be (re)installed on the machine if it cant boot over the network, from USB or optical drive?

---

### Post by petebarchetta on 2010-11-03
When you mention standard install, I would assume it's a live cd /alternate 'esque install. At what point in the install does it probe hardware to find specific drivers? Reason I ask is the original disk came from a tecra 8000 and it got through the list it creates at bootup looking for hw but the system fell over at the xorg and it never reached the GUI, I have no issue with using grub for dos or just going pure linux install, my main issue is trying to get the drive to boot to something useful. Win98 was put on there as I could get it to boot up with a "bootable" win98 when it was setup from a xp machine with bootfiles, but getting an "iso" to kick off from a dos prompt is challenging hence looking at unetbootin and sticking the lubuntu iso on to try and get it to install

I've made a bootable lubuntu lynx key and plan to put it in a tosh m5 to kick off the install to removable media to try and workaround, I'll see how that goes

---

### Post by petebarchetta on 2010-11-21
I now have xubuntu installed on the toughbook by means of dropping the 40gb HD into a tosh tecra m1, the install went fine and revolted with no issues on m1. When drive is put into toughbook the splash screen pops up and machine goes through probing hardware, the bootup sequence then bails at the point when it starts up xorg.
Is there any default xorg command for starting up a basic xorg config?

---

### Post by petebarchetta on 2010-12-18
Xubuntu dapper is now installed and we have a working GUI, I'm surprised by how fast a 400mhz toughbook is running dapper, not sure if hardy heron would bog the machine down, having the usual fun with the network card (cisco aironet 340) with blacklist file. On board nic is functioning so we have network
will post xorg for anyone who is trying ubuntu on these machines.
Also have a option globetrotter fusion gt card I wanted to get working but I think that dapper is too old for this datacard mainly due to a /etc/network interfaces file error.
Anyone had sucess on the toughbook and ubuntu?

---

### Post by petebarchetta on 2011-01-11
hello all,

I have installed and am runnung Xubuntu Hardy, very fast for a slower processor. no issues as of yet excpet the inbuilt mobile modem and the touchscreen are not responding.
it sees network and my cisco aironet 340 card works out the tin. only issue i had was installation, as with this particular model it cant usb boot or install over the network so a donor machine is needed. this time is a tecra t9100, no issues on host install and donor machine accepts install too
Posting from it at present, toughbook cf-m34 400mhz 256mb (512mb installed) and a 40gb HD.

---

### Post by petebarchetta on 2011-03-24
hello all,

i'm tempted to upgrade this machine to the 10.04 LTS build on this machine, what concerns should i have, i know on older machines the change of kernels cauises no end of mayhem, but i  have always had good results on kit with LTS releases, in particular the toshiba kit which for some unknown reason does not like the interim releases but runs fine with the LTS ones

Xubuntu 8.04 works ok and i have a usb broadband donogle that requires the 0.7 version of network manager to function, can i just update NWM or is it a full rebuild as synaptic only shows the o.6 build with hardy

any info cheers guys...

---

### Post by snowpine on 2011-03-24
> **petebarchetta said:**
> hello all,

i'm tempted to upgrade this machine to the 10.04 LTS build on this machine, what concerns should i have, i know on older machines the change of kernels cauises no end of mayhem, but i  have always had good results on kit with LTS releases, in particular the toshiba kit which for some unknown reason does not like the interim releases but runs fine with the LTS ones

Xubuntu 8.04 works ok and i have a usb broadband donogle that requires the 0.7 version of network manager to function, can i just update NWM or is it a full rebuild as synaptic only shows the o.6 build with hardy

any info cheers guys...

I recommend you take 10.04 for a test drive using Unetbootin. Once you have used it extensively and are confident it has good support for your hardware, then you can either upgrade or fresh install. That is the cautious approach, anyways.

---

