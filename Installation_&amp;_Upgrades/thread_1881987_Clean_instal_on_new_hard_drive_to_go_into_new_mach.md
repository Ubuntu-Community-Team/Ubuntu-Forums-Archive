---
title: "Clean instal on new hard drive to go into new machine"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by alexgogan on 2011-11-16
Hi,

Have searched high low and read so many pages to find this and lost now. But read pages and pages of answers that didn't so maybe it can't be done, but remember years ago I used to do this all the time but just forgot. 

What I want to do is the following

Have a rebuilt pc with BLANK hard drive (about to go in) and what I want to do is this. At the moment the hard drive is connected to win 7 pro 64bit. And can't format with dos, tried this on the CMS promt as well (format f:/s) 

Make this hard drive bootable then install ubuntu from a file that is in the hard drive.

Is this possible? If so is it just a case that I can then run Ubuntu from this.. sorry to appear stupid regarding this, but I am like a newbie >:¬}

And if its possible any help on this would be great

---

### Post by Mark Phelps on 2011-11-16
To make the blank drive bootable, you will have to install an OS -TO- it ... but you want to use it to install an OS -- catch 22.

The way to do this, without risking any changes to your Windows setup would be the following:
1) Burn a CD of the Ubuntu version you want
2) Disconnect the Windows drive
3) Connect up the target blank drive
4) Boot from the Ubuntu CD, install to the blank drive

That will make the drive bootable by default.

Then, reconnect the Windows drive -- but continue to boot from the Ubuntu drive.

Boot into Ubuntu, open a terminal, and enter "sudo update-grub".  That will regenerate the GRUB menu so that, when you reboot, you will be able to select which OS you want to use.

---

### Post by alexgogan on 2011-11-17
Hi Mark

I was thinking of doing something like that at the end if all else fails >:¬} which usually after hours of attempts is the first way to go instead of the "easy" ways.

Will give it a go over the weekend thanks.

Regards

Alex

---

### Post by alexgogan on 2011-11-21
Was thinking if I used the universal-usb-installer-easy-as-1-2-3/ to install this on my second drive in my existing box then take out the drive, through it in to the new box, do you thing that would work ?

---

