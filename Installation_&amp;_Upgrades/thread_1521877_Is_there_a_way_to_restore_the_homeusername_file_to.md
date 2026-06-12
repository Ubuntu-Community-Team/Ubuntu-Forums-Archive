---
title: "Is there a way to restore the home/username file to a default state?"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by landstander on 2010-07-01
**System Specs:**
CPU: Intel Core2 Quad Extreme X9450
Memory: 4GB, Patriot DDR3 PC3-10666 1333Mhz
MoBo: ASUS P5E3 Delux
OpSys: Ubuntu 10.4 (64Bit)

**Short Description:**
I wanted to see what would happen if I upgraded from Kubuntu 8.04 (32bit) to Ubuntu 10.4 (64bit) by copying my home directory then restoring it after the upgrade. It almost worked sans a few interesting problems that I'm hoping might teach me a bit more about how Ubuntu works.

**Detailed Description:**
1. I copied my home directory to another hard disk.
2. I let the installation disk for Ubuntu 10.4 (64bit) reformat and overwrite the disk that contained Kubuntu 8.04 (32bit) and chose to maintain the partition and swap size for that disk.
3. Once I worked out some bugs in the hardware and got the OS up and running smoothly, I "merged" my home directory with the backup I had created in step one. (Merge was an option given to me when I was attempting to paste the files copied from the backup disk.)
4. It should also be noted that I was trying for a while last night to install TrueCrypt. In order to do that I had to check its "sig" file. The GUI for the gpg installation was complaining that I didn't have gtk+-2.0 installed so I installed gtk (I think it might have been 2.4 or whatever the most recent one was) from source without any errors. It got late so I gave up on attempting to install TrueCrypt any further.

**The Results:**
This morning the computer seemed to boot faster than it had been before, but I was left without a functioning Theme manager. It will open, and I can click on all of its features, but nothing seems to do anything. For example: If I right click on the desktop and choose "Change Desktop Background" Then select "Get more themes online", nothing happens. Also if I select the "theme" tab, there are only two themes listed when there used to be about 9 by default.

**Questions:**
1.) Is there a way to restore the files that are important for correct system operation (possibly all the files starting with a dot ".*") in my home directory to there default state like they would have been from a fresh install, but without doing a fresh install and without loosing any of the documents or archives in my home file?
2.) Is this even the correct approach or might this cause more problems? For example, if your computer had this problem would you try and restore the home directory, or would you troubleshoot each problem as it arises one at a time until everything became stable?
3.) What could I do next to continue troubleshooting the theme manager?

I'll keep researching and trying to find some links that can help while I wait for your responses. If I find anything that helps I'll post the fix here.

Thanks

---

### Post by mikewhatever on 2010-07-01
I think the way to deal with this is to create another user. From a terminal, 
```
sudo adduser landstander admin
```
then logout and login as the new user. If successful, copying your files over is point and click (your personal files, not the configs).

---

### Post by landstander on 2010-07-02
mikewhatever,

Thanks for the reply. I tried that, and it didn't work so I just reformatted the drive and started over, but your advice about not copying over the configs helped and besides the hardware issues the system now appears to be working as it should.

Thanks again for your help.

---

