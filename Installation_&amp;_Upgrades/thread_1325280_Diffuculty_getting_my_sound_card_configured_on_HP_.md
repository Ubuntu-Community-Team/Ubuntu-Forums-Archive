---
title: "Diffuculty getting my sound card configured on HP Pavilion dv7-3085dx"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by pigs_eye_bozo on 2009-11-13
I am trying to get my head phones working on a new HP Pavilion dv7-3085dx.  The sound card works but plugging my head phones in does not mute the speaker.

My card is: HDA Intel
Chip is: IDT 92HD75b3X5

I loaded Ubuntu on this computer previously.  By, following the instructions posted by gn0st1c on 10/28/09, i got this working.  However, I a did this in my /home directory.  I am unclear as to whether this should be in the home directory or else where.  And why or why not.

[INDENT]gnostic@GnoStiC-dv7:~$ cat /proc/asound/card0/codec#* | grep -i codec
Codec: IDT 92HD75B3X5


what i did to get sound was;

wget -c [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2](ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.21.tar.bz2)
wget -c [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.21.tar.bz2](ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.21.tar.bz2)
wget -c [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.21.tar.bz2](ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.21.tar.bz2)
tar xvf alsa-driver-1.0.21.tar.bz2 
tar xvf alsa-lib-1.0.21.tar.bz2
tar xvf alsa-utils-1.0.21.tar.bz2 
cd alsa-driver-1.0.21/
./configure --with-cards=hda-intel
make
sudo make install
cd ..

cd alsa-lib-1.0.21/
./configure 
make
sudo make install
cd ..
cd alsa-utils-1.0.21/
./configure 
make
sudo make install


up to here, as you can see there is nothing special.. now we have to add our sound card model to alsa-base.conf based on codec info we have BUT there is no model listed for our card in alsa configuration guide; [http://paste.ubuntu.com/238572/](http://paste.ubuntu.com/238572/) 

so i picked the nearest number which is STAC92HD71B* :)

	STAC92HD71B*
	  ref		Reference board
	  dell-m4-1	Dell desktops
	  dell-m4-2	Dell desktops

	STAC92HD73*
	  ref		Reference board
	  dell-m6	Dell desktops


adding the following line to /etc/modprobe.d/alsa-base.conf solved my no sound problem, i may work for you too.. dell-m6 would probably work but i had sound with dell-m4-2 so i didn't bother to test..

options snd-hda-intel model=dell-m4-2
[/INDENT]            

I have followed many links in the forums and read about using wget in two Ubuntu manuals and it remains unclear.

It seems to me this should be in my /etc/modprobe.d directory with the alsa-base.conf files.  However, when I try to build it there it get the following error.

[INDENT]make dep
make[1]: Entering directory `/etc/modprobe.d/alsa-driver-1.0.21'
make[2]: Entering directory `/etc/modprobe.d/alsa-driver-1.0.21/acore'
copying file alsa-kernel/core/info.c
cp: cannot create regular file `info.c': Permission denied
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/etc/modprobe.d/alsa-driver-1.0.21/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/etc/modprobe.d/alsa-driver-1.0.21'
make: *** [include/sndversions.h] Error 2
john@john-laptop:/etc/modprobe.d/alsa-driver-1.0.21$ sudo make
make dep
make[1]: Entering directory `/etc/modprobe.d/alsa-driver-1.0.21'
make[2]: Entering directory `/etc/modprobe.d/alsa-driver-1.0.21/acore'
copying file alsa-kernel/core/info.c
/etc/modprobe.d/alsa-driver-1.0.21/utils/patch-alsa: 24: patch: not found
make[2]: *** [info.c] Error 1
make[2]: Leaving directory `/etc/modprobe.d/alsa-driver-1.0.21/acore'
make[1]: *** [dep] Error 1
make[1]: Leaving directory `/etc/modprobe.d/alsa-driver-1.0.21'
make: *** [include/sndversions.h] Error 2

[/INDENT]Finally, as I said it worked, or at least seemed to work in the /home directory.  My concern is if every time I need to do something like this I do it in my home directory that directory will quickly become a house keeping nightmare. 

Also, any relatively clear, concise discussion of what is where and why (i.g. file system) would be something I would greatly love to read.

Any help would be much appreciated.

Thanks

---

