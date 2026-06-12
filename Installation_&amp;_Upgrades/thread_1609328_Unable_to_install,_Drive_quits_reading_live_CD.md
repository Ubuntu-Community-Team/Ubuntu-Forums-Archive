---
title: "Unable to install, Drive quits reading live CD"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by oxf on 2010-10-30
Hi,

I decided to install Maverick on another PC in the house. I downloaded and burnt the 10:10 live CD three weeks ago and installed it on my laptop without problem.

Now when try to install on this it read the CD as first boot device, goes to the language selection, and then the "try without installing/Install/check disk" etc. I select either "install" or "try without installing" and after s few seconds the drive spins down and thats it...nothing more happens.

I know the CD's fine as I already  installed with it and the PC in question currently has a working version of Karmic on it. PC is an Acer L100 and the CD is the 32 bit version.

So what's going on? anyone got any ideas?

Thanks!

Update: After posting this I've played around a bit more. It seems most attempts it doesnt want  to read the Live CD at all. After trying to boot from it and displaying the copyright line "isolinux........" it jump straight GRUB and boots my present OS. I've just tried the Karmic CD  too and the same thing is happening. So maybe points to a problem with the CD drive??

---

### Post by mörgæs on 2010-10-30
You probably need to add boot options:
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
Have you tried nomodeset?

---

### Post by oxf on 2010-10-30
> **mörgæs said:**
> You probably need to add boot options:
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
Have you tried nomodeset?

Thanks....

Uhm I don't really know what I've got got going on here!

Most of the time, like 90%+, I can't even get to boot options. It just want to load the existing GRUB that I already have installed on the PC. So again it doesn't seem to want to read the CD.

When, after several attempts I have got it to start reading the Live CD I selected F6 and nomodeset. That did seem to help briefly and it started to install. However, after a minute or so I then get an error "unable to mount kernel".

Oh god its going to be one of those days......

---

### Post by mörgæs on 2010-10-30
You could also try booting from USB. Creating the USB stick with the latest version of Unetbootin seems to give the best results.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by oxf on 2010-10-31
Just for curiousity I tried booting from the Live CD's for Karmic, Lucid and of course Maverick.
Karmic booted up OK, however Lucid and Maverick refused to boot. They both had the same problem, i.e. after selecting install/try ubuntu the drive quit reading the CD.
What changed with the Lucid release??

Anyway back to Maverick. I tried the Live CD again and hit F6. The top option here is to select "No ACPI". I toggled it briefly on and then off again deciding I didn't want to mess with that.
Returned to boot and it loaded the Live CD without any problem!
Once booted I clicked on the "Install" icon and it installed Maverick without any problems!

Why this happened I have no idea at all. If anyone has any thoughts I'd sure be interested to hear them.

I'll mark this as solved, well sort of that is, since I managed to install it.

---

### Post by mörgæs on 2010-10-31
Are you absolutely sure that you toggled it off again? 
If you leave it on, does it boot? 

If you can reproduce it, it is worth opening a bug report in Launchpad. Deserves some attention.

---

### Post by oxf on 2010-11-01
> **mörgæs said:**
> Are you absolutely sure that you toggled it off again? 
If you leave it on, does it boot? 

If you can reproduce it, it is worth opening a bug report in Launchpad. Deserves some attention.

Yes I definately toggled it back off again!

Also I found that I couldn't boot from a USB either with this problem
I'll report it on launchpad.
Cheers!

---

### Post by mörgæs on 2010-11-01
Good, please post the link to the bug report. There might be others interested in following the process.

---

