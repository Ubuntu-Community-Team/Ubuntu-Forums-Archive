---
title: "Upgraded to edgy now its like a 486-66"
date: 2006-11-30
forum: Installation &amp; Upgrades
---

### Post by Mith73 on 2006-11-30
I switched to Ubuntu 4 months ago and I love it. Then last week I did a apt-get upgrade and all heck broke lose. Installed fine rebooted fine but arrgggh. After awhile or if I try to open to many windows at once i go into lag city. Applications will take up to 5 minutes to open. The whole time my desktop is not frozen but nothing responds right away and the mouse moves a few seconds after i move it and most of the time jumps clear across the screen. The windows programs i use with wine will crash or  do not start at all now. Firefox will crash 80% of the time. And when this is all happening the hard drive is spinning like crazy.
Example I will be using Blender and want to look at a photo when i open gThumb wam lag. But when i reboot and try it just fine. Then say i am doing the same thing and open up terminal or i get a upgrade alert everything will lock up. I left the system running for hours and it never recovers. Also have noticed my Internet has gotten spotty or just plain slow since the upgrade

amd 2400+
1 gig mem
Brand New maxtor 160 gig hard drive.
nvidia geforce 5500 fx
creative labs soundblaster platnuim 5.1
winfast mother board k76741mg
sony-dvd-rom
cd/cdr/cdrw/ CR-48x5te(which will read but will not burn since upgrade)

At one boot up the system did a fschk becuse the HD had been mounted 30 times and it found nothing wrong. The system was super fast and stable before the upgrade. Any ideals or hate to have to install dapper all over since backing up my files would involve buying another hard drive. about 50 gigs worth.

Mith

---

### Post by Trance Gemini on 2006-11-30
hmmm....

try this first:
```

sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

and then report back ;)

---

### Post by Mith73 on 2006-11-30
ok i did that. 

0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Fetched 4B in 2s (1B/s)  
Reading package lists... Done
The following packages will be upgraded:
  gnupg lvm2
Setting up gnupg (1.4.3-2ubuntu3.1) ...

I rebooted everything seemed fine.

started firefox 2 windows fine. Started Photoshop with crossover office fine. opened a photo with gthumb fine. started Banshee all heck broke lose. the only difference is there was only a 1 sec delay on the mouse. And force quit was able to work. However i clicked on the desktop instead, and lost all the icons on my desktop. Got banshee to shut down, no change stoped photoshop no change. Both took almost a minute to shutdown. Then 5 file folder windows open up showing my home folder and everything started to respond. However i still have no desktop icons.

Mith

Update. havent rebooted since using force quit on my desktop. No icons still after 10 minutes. However when ever i click on places home folder 5 windows pop up. have done it 5 times and it does the same thing everythime.

---

### Post by po0f on 2006-11-30
Mith73,

Nautilus draws the desktop as well as serves as a file manager.  Try closing all the Nautilus windows, opening up a terminal (Applications->Accessories->Terminal) and typing in just `nautilus`.

---

### Post by Mith73 on 2006-11-30
all I get when input nautilus in a terminal window. is 5 home folder windows and no desktop icons. Going to reboot and see what new fun things it throws my way.

Mith

After a reboot everything was fine did the same programs in the same order everything was fine shut down photoshop opened Blender and was hit with the lag again.

---

### Post by Mith73 on 2006-12-02
saw something when i did a reboot one time. something about a swap failed. so booted off the live cd and did a gparted. my main partition is listed as a ext3 then i have a partition listed as extended then there was on with a caution sign and was listed as unknown with a black box. Could the upgrade some how wiped out my swap drive space and if so could that be the cause for my lag. 

Mith

---

### Post by Kakihara on 2006-12-14
Yes. It may be a problem with swap. Uprade from dapper to edgy used to render your swap unusable and symptoms were similar. Try 'free' in console and see, if there is some swap present. try 'swapon -a' if it helps. It probably won't. If not, edit your /etc/fstab and find line with swap( probably something like: 'UUID=78bd6c70-72d5-4c6e-93fd-a25f011ca420 none swap sw 0 0') and change it to '/dev/hda5 none swap sw 0 0' with the correct partition as the first parameter. Then try 'swapon -a'. And 'free' to see if it works.
good luck

---

