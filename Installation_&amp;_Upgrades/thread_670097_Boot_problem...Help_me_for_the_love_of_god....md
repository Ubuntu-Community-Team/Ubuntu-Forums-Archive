---
title: "Boot problem...Help me for the love of god..."
date: 2008-01-17
forum: Installation &amp; Upgrades
---

### Post by ppkstat on 2008-01-17
Hi ppl. I'll try to keep this as condensed as possible.

I thought i take the plunge and try ubuntu (i am NOT experienced with Linux). I had the idea of installing the OS in a 500GB external hard drive i have so I dont mess up with my current normal Windows installation.

So...I boot from the live cd i end up at ubuntus desktop and i see that my usb drive is normally recognised and mounted, while on the same time My normal hard disk which is a RAID 0 array was NOT recognised. Thats ideal i thought, ill install ubuntu on my usb drive and theres no way it can mess up my win installation because it can't see the drive. Right? WRONG.

What happens is that ubuntu install itself in a partition of my usb drive and GOES AND INSTALLS ITS BOOT MANAGER ON MY MAIN HARD DRIVE (the raid array that coudnt recognise).

End result? I can't boot to windows coz i get a GRUB error (21). I cant boot to the Ubuntu install on my external usb (it says missing operating system).

The only thing i CAN do is to run the live cd. 

The obvious solutions would be boot from windows cd and fix mbr. I cant try it right now coz i dont have a win cd, but i doubt it could work because it wouldnt prolly see my hard drive since the RAID drivers wouldnt have installed yet.

So...Any ideas how can i resolve this from the live cd and put an end in my agony? Please help....:(

---

### Post by Craigus on 2008-01-17
Get the supergrub disk:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by ppkstat on 2008-01-17
Will this recognise my raid aray so it can overwrite the MBR?

Ill try it when i get access to another pc.

---

### Post by crabhunter on 2008-01-17
I had the same thing and it really pissed me off.
I have never found a Linux distro that would load on my raid setup so I always install them on a separate ide drive.
This time ubuntu put its boot manager on just one of the pair of drives meaning i couldent even fix the windows install from the rescue option,Vista reported that there was nothing to rescue.
I had to do a re-install,but after i put Vista and Xp back on the raid setup I found I could still boot ubuntu if I set the bios to boot of the ide.
So I am Very pissed of with Ubuntu over that.
Going slightly off track,the only way I can boot ubuntu is the keep changing the bios.
I wish there was on option at install of putting grub on a floppy like you used to be able to do in old versions of Suse.The if I wanted to use Linux i could just put in the floppy.
Another option would be if easybcd would boot Linux on a different drive.
I have found it will find operating systems on the same drive as it is installed on,if only it could see my ide drive my problems would be fixed.
BTW next time you install Ubuntu disconnect your raid drives first,that's what I shall do in the future.
Mike

---

### Post by ppkstat on 2008-01-17
> **crabhunter said:**
> 
This time ubuntu put its boot manager on just one of the pair of drives meaning i couldent even fix the windows install from the rescue option,Vista reported that there was nothing to rescue.


My god that happened to me as well. Ubuntu put its boot manager in the first of the hard drives of my raid array (hd0 as ubuntu says).

Does that mean I lost all my data? I am installing a supposed to be better than windows OS and it destroys my data even if i choose NOT to interfere with my main HD?

Honestly i am confused. And panicked.

---

### Post by crabhunter on 2008-01-17
Well I couldent rescue mine but it was a fresh install and I had just done a massive backup as it was the first time I had installed Vista.
I just hope for your sake someone knows a fix.
I didnt try the good old fixmbr from an old 98 cd, 98 dosent seem to need raid drivers for some reason.
Give that a go,I dont think you can make it worse now.
Mike

---

