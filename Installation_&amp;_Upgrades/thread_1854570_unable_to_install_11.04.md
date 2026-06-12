---
title: "unable to install 11.04?"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by cindylo on 2011-10-04
I reboot(installed inside of windows 7 64-bit ultimate) and it partitions and formats the allocated space to ext4(I think). Then starts copying the files it halfway-3/4 done and the screen goes black with the circle(mouse) still spinning then text comes up. The last thing it says(thats not code) is downloading firmware(or something like that) and I have to restart my pc to go back into windows. I have tried everything. Any ideas?

---

### Post by garvinrick4 on 2011-10-04
> (installed inside of windows 7 64-bit ultimate)Hi Cindylo, Welcome to the Ubuntu Forums
Your install inside of Windows is called a WUBI install, the other type is a Partition install.
There will be user that uses WUBI around be patient. There are a few great users with knowledge
in WUBI.
From now on put WUBI in your title (prefix) so as users will spot it browsing through titles. Take care Cindylo.

---

### Post by cindylo on 2011-10-04
Thanks but how do I edit the ubuntu to WUBI? And yes it is WUBI.

---

### Post by garvinrick4 on 2011-10-04
> Thanks but how do I edit the ubuntu to WUBI? And yes it is WUBI.[COLOR=Black]When one of the mods sees this thread[/COLOR] they will for you (the users with red names) there are quite
a few in session right now.

---

### Post by garvinrick4 on 2011-10-04
@cindylo
 You did download a .iso file of Ubuntu and BURN to a Disk? Then put the disk in while in Windows
and click on wubu.exe
Choose size you want minumum of 10 gig preferably 20 gig or more. Then choose user name
and password and then install?

## Go into Windows now and look right next to USERS in C: drive and check to make sure that
Ubuntu is not there if is. Go to add and remove programs and remove before starting over.

Here is download link and the WUBI GUIDE. Keep me updated on your progress.
[Download Ubuntu | Ubuntu]("http://www.ubuntu.com/getubuntu/download") 

[WubiGuide - Ubuntu Wiki]("https://wiki.ubuntu.com/WubiGuide")

## The two Wubi specialists that I use are rubi1200 and bcbc and they are both offline right now
I had a WUBI install at one time so I will give you any skill set that I own on the subject.

---

### Post by cindylo on 2011-10-04
I did all that and it still gives the black text screen halfway through the copy process. And its an .iso file mounted in windows then after I click install in windows then I restart and it attempts to finish the install.

---

### Post by garvinrick4 on 2011-10-04
You did BURN the iso file to a CD?

---

### Post by cindylo on 2011-10-04
Nope I didn't. Do I need to? Can I use the USB creator instead?

---

### Post by garvinrick4 on 2011-10-04
> **cindylo said:**
> Nope I didn't. Do I need to? Can I use the USB creator instead?
Yes that will do also. Then put it in when Windows is running and click on wubi.exe
Keep me updated.

---

### Post by bcbc on 2011-10-05
This is a bit of a strange problem. It's during the 2nd stage (ubuntu) install that it's freezing. I've heard some reports that this can happen while downloading updates (that's the default during the install - to download, but not install the most recent package updates).

So what I'd suggest is to disconnect from the internet during the ubuntu install phase. 

If disconnecting from the net doesn't help, I'd suggest booting from the USB and selecting "Try it" and see if that works - might be some compatibility issue. 

PS Running wubi from a USB can be a problem due to a bad size check that's designed to prevent wubi running on DVD ISO's. Unfortunately it blocks USB installs where the partition is > 900k - but only after copying it to the hard drive (and some USBs can be big).

Edit: might be the bug [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/743359](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/743359)

---

### Post by cindylo on 2011-10-05
So use the USB creator and "try it"? Also try disconnecting from internet right?

---

### Post by bcbc on 2011-10-05
It's not necessary to disconnect from the net when booting from the USB in live mode (Try it). I was suggesting that if you try reinstalling with Wubi then you should disconnect from the net.

The live USB is useful to see if your hardware is compatible with Ubuntu.

---

### Post by cindylo on 2011-10-05
So I need to put in on a USB and "try it"(cause I have no cd's). Also disconnect the ethernet cable right?

---

### Post by bcbc on 2011-10-05
> **cindylo said:**
> So I need to put in on a USB and "try it"(cause I have no cd's). Also disconnect the ethernet cable right?

Leave the ethernet cable in. Boot from the USB and select "Try it". 

Play around with Ubuntu and report back if everything works well including the internet.

---

