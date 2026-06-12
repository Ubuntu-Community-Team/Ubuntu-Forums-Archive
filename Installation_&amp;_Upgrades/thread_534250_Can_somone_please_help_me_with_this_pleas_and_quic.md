---
title: "Can somone please help me with this pleas and quickly"
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by PaulBarentt on 2007-08-25
hi I earlier on today I installed Ubuntu on  a older PC so that i could receive radio frequencys like police dispatchers fire service and airport transmitions I found i link that has a howto guide but they are not clear my tv card is a saa7134 based chipset however the programming is written for debian sarge systems here is the page 
  	
	 
Radio arrow Radio On Linux arrow Scanning the 'waves with your TV card
Main Menu

    * Home

Login Form
Username

Password

Remember me
Lost Password?
No account yet? Register
Latest News

    * Scanning the 'waves with your TV card

	  	
Popular

    * Scanning the 'waves with your TV card

Scanning the 'waves with your TV card 	Print 	Email
Sunday, 15 October 2006
If you have a TV capture card in your computer, you probably already have all the hardware you need to listen in on much more than just TV and radio (only software changes are needed). The hardware will also allow you to hear emergency services, taxi and freight radios, UHF citizen band radio, aircraft transmissions, and more.

In this article, I show you how you can make your Linux distribution (I used Debian Sarge, but other distros should work too, as long as you have a 2.6.x Linux kernel) and SAA7134 based TV card tune into those frequencies you can't get at with a normal radio or TV.

SAA7134 is a popular chip for tuner cards. It needs to be attached to a tuner such as the FI1216. This configuration is used on a number of popular TV cards (this list is taken from Linux kernel file drivers/media/video/saa7134/saa7134-cards.c):

    * Proteus Pro [philips reference design]
    * LifeView FlyVIDEO2000 and LifeView FlyVIDEO3000
    * EMPRESS
    * SKNet Monster TV
    * Tevion MD 9717
    * KNC One TV-Station DVR and KNC One TV-Station RDS
    * Typhoon TV Tuner RDS and Typhoon TV+Radio 90031
    * Terratec Cinergy 400 TV
    * Medion 5044 and Medion 7134
    * Kworld/KuroutoShikou SAA7130-TVPCI
    * Terratec Cinergy 600 TV
    * ELSA EX-VISION 300TV and ELSA EX-VISION 500TV
    * ASUS TV-FM 7134
    * AOPEN VA1000 POWER
    * 10MOONS PCI TV CAPTURE CARD
    * BMK MPEX
    * Compro VideoMate TV
    * Matrox CronosPlus
    * AverMedia M156 / Medion 2819
    * ASUS TV-FM 7133
    * Pinnacle PCTV Stereo (saa7134)
    * Manli MuchTV M-TV002 and M-TV001
    * Nagase Sangyo TransGear 3000TV
    * Elitegroup ECS TVP3XP FM1216 Tuner Card(PAL-BG,FM) and FM1236 Tuner Card (NTSC,FM)
    * AVACS SmartTV
    * AVerMedia DVD EZMaker and AVerMedia 305
    * Noval Prime TV 7133
    * UPMOST PURPLE TV
    * Items MuchTV Plus / IT-005

I have only tested this with my FlyVideo 3000, although I expect that many of the above will also work. Other cards have similar hardware, but you will need to do some of the work yourself.

The exact range of frequencies you will have access to depends on the specific tuner you have. However, it will be about 44 MHz (below the standard FM frequency, in the VHF range) all the way up to about 958 MHz, in the UHF range.

The standard kernel driver, however, is not suitable for tuning into anything other than TV, because it has a limited set of tuner frequencies which it looks for at the detection stage. However, I have produced a modified kernel driver which will let you tune to arbitrary frequencies. I also produced a user-space program to control it. Grab the software package from here.

Untar the software package. You also need to install the kernel source corresponding to the kernel on your system (most distros come with a kernel source package). Go into the kernel subdirectory of the package, and then type:

make -C /usr/src/kernel-source-2.6.8 M=`pwd` modules <---- I tried that instead of that I enterd make -C /usr/src/linux-headers-2.6.20-15/kernel M=`pwd` modules
 using terminal and it said make: Entering directory `/usr/src/linux-headers-2.6.20-15/kernel'
make: *** No rule to make target `modules'.  Stop.
make: Leaving directory `/usr/src/linux-headers-2.6.20-15/kernel'
root@paul-desktop:~# 



You need to replace the /usr/src/kernel-source-2.6.8 with the path to your kernel sources (that path is right for Debian Sarge systems). Now, you need to remove any saa7134 package you might have on your system, and replace it with the module you just compiled. You can do that like this (you must be root first):

rmmod saa7134
 
 insmod ./saa7134.ko oss=1
 
 

You might also want to copy the saa7134.ko over the existing saa7134.ko in /lib/modules/2.6.version/kernel/drivers/media/video/, so it comes back when you restart your system.

Once you have put your package into the kernel, your kernel is ready to start tuning in. Go up a level in the software package, and type make. This will produce a setfreq binary. To tune into a radio frequency, you need to give two parameters:

    * The frequency of the station you want to tune into.
    * The optimal frequency at which to decode the sound. This depends on the bandwidth of the signal. For television sound, use 5000, 5500 or 6000. Most other FM radio signals use a narrower band, and 1000 generally works well. Even if you get the station frequency right, getting this one right is almost as important, or you won't hear much.

You need to figure out what frequency you want to tune into. A good way to do this is to look up spectrum licenses with the government body that allocates frequencies (if that information is readily available). You can also get lists for many countries from scanner clubs in your country. Another option would be just to try all frequencies in a certain range until you hit something.

For New Zealand, I used the frequency list from NZScanners. For example, one of the Central 1 Police frequency is 75.47500. I can tune into that by using ./setfreq 75.475 1000.

Now that you've got it working, here's a helpful hint, especially if you are getting poor reception: a good antenna makes a lot of difference. The antenna that came with your card is probably not very good, so consider investing in at least a bunny's ear antenna. You might get better reception still by connecting to an exterior VHF/UHF antenna (the same type as for normal television reception). Lower frequency reception may need a different antenna.

Another hint: On Linux, you have a lot more options for what to do with the sound than on your average scanner radio. You can read samples off your dsp device (it will often be dsp1, if your soundcard is already /dev/dsp). Turn off sound direct to the sound-card using a mixer program, and use a program like sox to process your sound as it goes from dsp1 to dsp. You can filter out distracting low frequency noise using the highp filter (anything below 50Hz is just distracting, and doesn't help much in identifying what they are saying). You could also potentially record sounds off the device, and stream it to other enthusiasts across the Internet, and even decode pager messages (but check that this is legal in your country before you try, especially if you are going to post about it!).

 
Last Updated ( Sunday, 22 October 2006 )
  	  	
Who's Online
We have 3 guests online



please help me i am stuck

ehat I want somone to do is to tell me what I am doing wrong 

Thanks

---

### Post by PaulBarentt on 2007-08-25
is there anyone who can helpme here really dont have time to wait around


Thanks

---

### Post by pgar23 on 2007-08-25
which step are you on?
can you just post the url link instead of all its text please. thanks.

---

### Post by pgar23 on 2007-08-25
which distro r u using?

---

### Post by PaulBarentt on 2007-08-25
heres the step You also need to install the kernel source corresponding to the kernel on your system (most distros come with a kernel source package). Go into the kernel subdirectory of the package, and then type:

make -C /usr/src/kernel-source-2.6.8 M=`pwd` modules

and the url [http://www.amxl.com/option,com_content/task,view/id,1/Itemid,1/](http://www.amxl.com/option,com_content/task,view/id,1/Itemid,1/)

---

### Post by pgar23 on 2007-08-25
which distro r u using? once again.

---

### Post by PaulBarentt on 2007-08-25
i am using ubuntu  7.04 if thatis the distro

---

### Post by pgar23 on 2007-08-25
yes that is the distro.
First I want to let you know that this guys software stuff sounds bogus, it sound like some fake bs that  i wouldnt trust. but if you want it I will attempt to assist you in installing this bs.
First of all where did you save the scannertuner-0.1.tar.tgz file?

---

### Post by PaulBarentt on 2007-08-25
I will take a chance there I saved that file to my desktop

---

### Post by pgar23 on 2007-08-25
ok run
```

cd /home/<your username here>/Desktop
```be sure to capitalize the "D" in desktop.
then if u run "ls" which is not necessary but it will show you the file is on your desktop.
once u have cd'd into ur Desktop, run
```
tar zxvf scannertuner-0.1.tar.tgz
```

---

### Post by PaulBarentt on 2007-08-25
Ok I am logged on as root i found my way there through /root/desktop I have opened the zip file and where must I extract it to?

---

### Post by pgar23 on 2007-08-25
Don't logon as root. This is dangerous when you dont know what youre doing, log back on as a regular user (ie. username, usernames pswd) not as root tho.
Once logged on as a regular user, open the terminal.
This is under APPLICATIONS>ACCESSORIES>TERMINAL.

then run the commands i gave you above this reply. The above commands can be run as a regular user. I dont think you should need super user privelages. If u do, just type
```
sudo
```
in front of the commands I gave you.

---

### Post by eentonig on 2007-08-25
>  and quickly

What's the rush?

---

### Post by PaulBarentt on 2007-08-25
OK I ran terminal and I did those commands and I got this 
scannertuner-0.1/
scannertuner-0.1/kernel/
scannertuner-0.1/kernel/saa7134-i2c.c
scannertuner-0.1/kernel/saa7134-vbi.c
scannertuner-0.1/kernel/videodev2.h
scannertuner-0.1/kernel/Makefile
scannertuner-0.1/kernel/saa7134-ts.c
scannertuner-0.1/kernel/saa7134-input.c
scannertuner-0.1/kernel/saa7134-video.c
scannertuner-0.1/kernel/tuner.c
scannertuner-0.1/kernel/saa7134-reg.h
scannertuner-0.1/kernel/saa7134-core.c
scannertuner-0.1/kernel/saa7134-cards.c
scannertuner-0.1/kernel/saa6752hs.c
scannertuner-0.1/kernel/saa7134-oss.c
scannertuner-0.1/kernel/saa7134.h
scannertuner-0.1/kernel/saa7134-tvaudio.c
scannertuner-0.1/COPYING
scannertuner-0.1/COPYING~
scannertuner-0.1/setfreq.c~
scannertuner-0.1/setfreq.c
scannertuner-0.1/Makefile

---

### Post by ddrichardson on 2007-08-25
Can  I issue a caveat here, what this chap is proposing in his guide is illegal in the UK and I would imagine many other countries - altering wireless/radio equipment without license.

---

### Post by PaulBarentt on 2007-08-25
legal in NZ ok what i did was i had another attempt I located the folder that i thought was the kernel folder then i used the command  make -C /usr/src/linux-headers-2.6.20-15/kernel M=`pwd` modules and it said make: Entering directory `/usr/src/linux-headers-2.6.20-15/kernel'
make: *** No rule to make target `modules'.  Stop.
make: Leaving directory `/usr/src/linux-headers-2.6.20-15/kernel'
root@paul-desktop:~#
now what is going on

---

### Post by PaulBarentt on 2007-08-25
can somone please assist me here as I would like to get this done as soon as possibile so I can listen to aviation  frequencies and time is ticking by

---

### Post by ddrichardson on 2007-08-26
I think the guide wants you to enter the package kernel directory and do a make - not the system one:```
cd scannertuner-0.1/kernel
make
```

---

### Post by PaulBarentt on 2007-08-26
thanks I now have another problem when I do this as i am in the final stage however when I go to make because that's what I am supposed to do i get this gcc -lm -Wall -ggdb setfreq.c -o setfreq
In file included from setfreq.c:27:
/usr/include/linux/videodev.h:176: error: ‘VIDEO_MAX_FRAME’ undeclared here (not in a function)
make: *** [setfreq] Error 1


whats going on

---

### Post by ddrichardson on 2007-08-26
Without seeing the code I can only tell you that its using an undeclared function. As to where the coder has gone wrong I can't.

---

