---
title: "installation issues install fails with good cd"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by rasbach on 2007-02-25
I downloaded the ubuntu-6.06.1-alternate-i386.iso today, the MD5 matched perfectly as reported in K3B, and the disk passes the integrity check with no problems.  Burned at 8x- the minimum that media or recorder would allow according to K3B.

I am trying to install Ubuntu as the sole OS on a Toshiba A35-S159 laptop that's had Ubuntu/SuSE/Debian on it many times before.  Never a problem before today.  

At first the disk would not boot, even when CD was in the first order- I had to make the boot sequence list the HD below removable devices and network boot and for some unknown reason it worked.

Now when I go through the install process, it fails in two areas:

Configuring the clock fails- I get an error that states "there was a problem reading data from the CD-ROM.  Please make sure it is in the drive.  If retrying does not work, you should check the integrity of the CD-ROM."   ( The disk is in, and as stated before the disk integrity was fine.)

So I am given the option to retry, I can click yes a hundred times (actually did that) but I need to click "No" to proceed.

Then after I set up my password, my screen turns red (and so does my face) and it says:

Debootstrap error
Invalid Release file: no valid components.

<Go Back>          <Continue>

I click continue...

Failed to install the base system

The base system installation into /target/ failed.

Check /var/log/syslog or see virtual console 4 for the details

So I execute a shell, and do a nano /var/log/syslog

I read through the log, and noticed the following interesting lines:

Buffer I/O error, dev hdc, sector 432
hdc: tray open
end_request: I/O error, dev hdc, sector 432
error: exiting on error base-installer/debootstrap

Any ideas guys?

---

### Post by rasbach on 2007-02-26
bump :(

---

### Post by rasbach on 2007-07-15
I found that if I use a DVD-R rather than a CD-R to boot the image- all goes well.  :KS

---

