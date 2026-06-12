---
title: "[SOLVED] Cooling fans gone crazy."
date: 2008-10-11
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mick8985 on 2008-10-11
After a recent update the cooling fan on my laptop runs constantly at full speed, apart from every 5 seconds or so it stops for a fraction of a second and continues at full speed.
It is extremely off putting and irritating, anyone else with this issue? I am using a dell M1330. I would like to file a bug but I don't know what to file it against.

---

### Post by xens on 2008-10-11
Same problem here on a Dell Latitude D630, this problem is related to gnome-power-manager.

---

### Post by mick8985 on 2008-10-11
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/281724](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/281724)

---

### Post by drobvice on 2008-10-11
Update your bios to A12.  I had the same problem on my 1330 after the OS warned me of a Partial Upgrade and upgrading the bios fixed it for me.

---

### Post by pejobe on 2008-10-11
The fan problem is an issue that many struggle with, including me.
I use a DELL m1330.
For the first three days with Intrepid fan was quite, then after an upgrade it all went to a nightmare. 
Fan is now on MAX speed all the time...

There are lots of posts on the subject and here is one:

[https://bugs.launchpad.net/dell/+bug/243637]("https://bugs.launchpad.net/dell/+bug/243637")

Here is another way maybe worth trying. I have not done it myself yet, but reply back if it is successful.

[http://movingtoubuntu.technicalbloke.co.uk/cpu_temperature_and_fan_speed]("http://movingtoubuntu.technicalbloke.co.uk/cpu_temperature_and_fan_speed")

After the upgrade (which really was a downturn) 
Firefox is slow and scrolling the page induce bad rendering and pieces from previous page is seen.

---

### Post by pejobe on 2008-10-11
> Update your bios to A12. I had the same problem on my 1330 after the OS warned me of a Partial Upgrade and upgrading the bios fixed it for me.

drobvice, please be more specifik. How to update the bios to A12.
Have been listening to my fan all day so my brain feels like butter...

---

### Post by mick8985 on 2008-10-11
[The bios update is an .exe]("http://support.euro.dell.com/support/downloads/driverslist.aspx?os=BIOSA&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=XPS_M1330&hidos=WLH&hidlang=en&TabIndex="), running this is wine could be dangerous? I dont have windows installed.

---

### Post by pejobe on 2008-10-11
found this about update BIOS of DELL with Ubuntu

[http://www.linuxscrew.com/2007/12/09/update-bios-of-dell-laptop-with-ubuntu/]("http://www.linuxscrew.com/2007/12/09/update-bios-of-dell-laptop-with-ubuntu/")

have run the script but still no success with the fan...

---

### Post by drobvice on 2008-10-11
I got my laptop from the windows section of Dell due to a deal and I did it from windows but there are instructions on the [website]("http://http://support.dell.com/support/downloads/download.aspx?deviceid=14178&fileid=263515&releaseid=R191967&SystemID=XPS_M1330#3DOS") on how to install from a bootable floppy (or a CD-RW maybe even a flash drive).  If you are unsure and can call Dell, you might try that.  I can't use them for support as, like I mentioned, mine is a windows laptop.

---

### Post by mick8985 on 2008-10-11
I can confirm the BIOS update fixes it, Basically follow [this]("https://wiki.ubuntu.com/DellBIOS")
You will need the bios update from [here]("http://support.euro.dell.com/support/downloads/driverslist.aspx?os=BIOSA&osl=EN&catid=-1&impid=-1&servicetag=&SystemID=XPS_M1330&hidos=WLH&hidlang=en&TabIndex=") 
Just comment out the whole if fi statement in the install.sh file and install the packages as per the tutorial, run install.sh
then use the command:
```
biosdisk install M1330A12.EXE
```
reboot, and make sure you have your laptop plugged in.
Still, if it was an update of gnome-power-manager that causes this then the bios update still shouldn't be necessary, this should be fixed before release since M1330 is a supported laptop, also why isn't biosdisk packaged? it has the dpkg files all there, the work is basically done already. A MOTU should really pick that package up.

---

### Post by drobvice on 2008-10-11
Hey, nice work dude!  I was going to try to update the bios from Ubuntu (just to learn how to do it) but had to shut off the fans!

*edit* Don't forget to update your bug report.

---

### Post by jetpeach on 2008-10-15
I used the top method with the Dell packages described on the page mentioned,
[https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS)
to fix the problem on my Inspiron 1420n. the packages took a little while to go through and check for some junk (i don't really know what it was doing), but worked fine.

i had just upgraded the nvidia drivers to the latest 177.80 and suddenly the fan went crazy. i'm glad not to have to downgrade and that the bios fix puts my fan back at normal (heck, i can't even hear it now so it almost seems even quieter than before).

note that you need to type "update-firmware --yes" for it to update on the next warm-reboot. the instructions just say update-firmware, but if you read the message from that command it tells you it _can_ be upgraded and to now type it with --yes if you really want to.

jet

---

### Post by halok on 2008-10-15
Downgrading to nvidia 173 driver fixed it for me, cant be bothered mucking around with bios updates if simply downgrading a driver works untill a workaround is sorted out.
Edit: btw this is on a inspiron 1420

---

### Post by slibuntu on 2008-10-20
Yeah, its the nVidia driver that seeems to do it, I'd recommend not to upgrade the bios, read up on the direct2dell blog about the nVidia chip problems.

---

### Post by jetpeach on 2008-10-21
i was afraid to upgrade the bios because heard it would make my fan run all the time, but for me this is not the case at all - the fan runs the same as before, maybe less...

---

### Post by cendant on 2008-10-26
Seems like the 8400GM chip used in Dell laptops is pretty bad, and updating the BIOS only hides things by constantly running  the system fan

My motherboard has already been replaced by Dell because of this

[http://direct2dell.com/one2one/archive/2008/07/25/nvidia-gpu-update-for-dell-laptop-owners.aspx](http://direct2dell.com/one2one/archive/2008/07/25/nvidia-gpu-update-for-dell-laptop-owners.aspx)

but even with A12 revision for Dell XPS 1330 I am starting to see the same problem with the new motherboard on Intrepid. 

Sick! and my warranty expires in November

---

