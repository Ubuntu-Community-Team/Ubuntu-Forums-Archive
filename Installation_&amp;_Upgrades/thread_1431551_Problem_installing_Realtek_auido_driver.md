---
title: "Problem installing Realtek auido driver"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by cmparizeau on 2010-03-16
Ok im TOTALLY new to Linux, but i have some computer skills, and i catch on pretty quick. So i downloaded my audio driver, and in the README it says to do a manual install. If someone can give me diections.... that would be stupendious, video even better. Basically i have NO idea how to even get to these files/menus. Without this driver i have no sound... and to me...thats a BIIG deal.


 Manual install:
Step 1. unzip source code
        tar xfvj alsa-driver-1.0.xx.tar.bz2

Step 2. Turn on sound support from kernel config 
	(soundcore module, default turn on)

Step 3. Complied source code
	a. cd alsa-driver-1.0.xx
	b. ./configure (--with-cards=hda-intel)<= for HDA options
	c. make
	d. make install
	e. alsaconf

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
 	(Please refer to the attached modules.conf)
	 
        snd-xxxx is the card ID.

	-- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
	   --- Intel ICH6 ICH7 ---------
               snd-hda-intel

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
	       snd-via82xx
           --- ATI Chipset  -------------------------------
	       snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
	# ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

Step 5. reboot your machine

Step 6. Use the alsamixer the disable mute (All audio line default is mute)
        Must to compile and to install the ALSA library and utility. (Use automatic install is already install)
        excute alsamixer


PLEASE HELP ME!!!

---

### Post by gordintoronto on 2010-03-16
You're thinking the Windows way, and making this a lot more complicated than it really is.  I would be very surprised if you need any of the stuff in your message.  Rather, you should open up the volume controls and uncheck any "mute" buttons you find. (Right-click the volume control near the top-right of your screen.)

If that doesn't work, open Accessories/Terminal and enter the command:
lspci

one of the lines of output will identify your sound card.  Paste that line back here.

Oh, you can also go to Preferences/Sound and fool around there.

Generally, Linux includes an enormous number of drivers right out of the box, and you don't have to install them, they just get loaded as needed.

---

### Post by Bucky Ball on 2010-03-16
Like gordintoronto says ... 

Linux is not windows. Your audio should work out of the box, but you may need to tweak a little.

---

### Post by cmparizeau on 2010-03-17
yeah.......imma dumb ***.... officially....... might help if the actual cords were plugged in right? yes i know im horrible




 Or wait does linux come with a program that makes all my wired accessories "wireless"?

Go ahead.... have fun with the above sentence.

---

