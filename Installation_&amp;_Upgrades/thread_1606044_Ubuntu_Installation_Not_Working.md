---
title: "Ubuntu Installation Not Working"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by ShadowVegan on 2010-10-26
A few hours ago I removed Vista from my HDD and completely wiped and overwrote everything. I then tried to install Ubuntu. On the screen where it asks for my name, computer name, username, password, and if I want to encrypt a folder, the loading bar got to about 75% and froze. I waited a while, and when it did nothing, I wiped my HDD again and tried installation with a different Ubuntu CD. Again, it froze at the same spot. This time I waited probably between a half hour and hour. To get from 0 to ~75% it only took a few minutes or less, so I highly doubt that I didn't wait long enough. Same thing happened with both disks. What should I do? And should I wipe my HDD first (since it probably has Ubuntu partially-installed)?
Specs:
Asus G50VT
286GB HDD
4GB RAM
2.13GHz processor
any others needed, let me know.

The disks both work fine for booting from the disk. I am on using Ubuntu from the disk now, just can't install it.

Thanks.

---

### Post by mörgæs on 2010-10-26
You don't need to format the hard drive. It will be done in the process.

Have you tried the alternate version?

---

### Post by ShadowVegan on 2010-10-26
> **mörgæs said:**
> You don't need to format the hard drive. It will be done in the process.

Have you tried the alternate version?

What do you mean by alternate version? 64 bit? Older release? If possible I want to use one of the disks I already have so I don't have to reinstall Vista to make another disk, but if you think a different version would work better I'll try that.

---

### Post by mörgæs on 2010-10-26
The alternate version is the text-bases installer:
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

Trying both 10.04 and 10.10 is a good first step.

Remember to have wired internet access while installing.

---

### Post by swaprava on 2010-10-26
> **ShadowVegan said:**
> A few hours ago I removed Vista from my HDD and completely wiped and overwrote everything. I then tried to install Ubuntu. On the screen where it asks for my name, computer name, username, password, and if I want to encrypt a folder, the loading bar got to about 75% and froze. I waited a while, and when it did nothing, I wiped my HDD again and tried installation with a different Ubuntu CD. Again, it froze at the same spot. This time I waited probably between a half hour and hour. To get from 0 to ~75% it only took a few minutes or less, so I highly doubt that I didn't wait long enough. Same thing happened with both disks. What should I do? And should I wipe my HDD first (since it probably has Ubuntu partially-installed)?
Specs:
Asus G50VT
286GB HDD
4GB RAM
2.13GHz processor
any others needed, let me know.

The disks both work fine for booting from the disk. I am on using Ubuntu from the disk now, just can't install it.

Thanks.
 

How long did you wait at 75%? In this GUI mode, if you watch closely, you might see what the installation is doing right on top of the progress bar. For example, something like

```
installing dpkg
```

If you see that these messages are changing over time even though the progress bar is frozen at 75%, you needn't worry. For certain hardware it might take longer time and appear to be frozen, while it is not. Make perfectly sure that everything is **really **frozen before aborting the installation.

---

### Post by ShadowVegan on 2010-10-26
It was actually closer to 80%. I have installation open now and it's been at that spot for about 5 hours. (only took a few minutes to get that far) Nothing changes.

It says 'Ready when you are' in the dark gray box, right above the orange status bar. When I click on 'Ready when you are' it opens the black text box and the last thing it says is 'Oct 26 14:17:01 ubuntu CRON[9484]: (root) CMD (   cd / && run-parts --report c/cron.hourly)'

It also says ^C after that because I attempted to copy it using ctrl+C, which didn't work and instead added the ^C, which is actually the last thing it says, but I doubt that matters...

Also, I checked the box that says 'Encrypt my home folder' (right when I started installation), not sure if that means anything.

Since it says 'Ready when you are' does it mean it's waiting for me to do something?

Are there any differences between the CD and text versions? If I install the text version, will I end up exactly the same as if I install a CD version?

Thanks

---

### Post by mörgæs on 2010-10-26
> **ShadowVegan said:**
> 
Are there any differences between the CD and text versions? 


Only the installation process itself. The finished system is the same.

---

### Post by ShadowVegan on 2010-10-26
I made a 10.04 disk at my university's library today and it successfully installed. I'll keep the text-based installation in mind in case I decide to switch to 10.10. Thanks for the suggestions!

---

### Post by mörgæs on 2010-10-27
Good, please mark the thread 'solved'.

---

