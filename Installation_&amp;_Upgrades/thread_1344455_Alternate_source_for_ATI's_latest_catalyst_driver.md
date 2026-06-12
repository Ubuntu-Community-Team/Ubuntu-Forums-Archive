---
title: "Alternate source for ATI's latest catalyst driver?"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by ucal on 2009-12-03
SUMMARY:
[LIST]
[*]I need a download source for the HD Radeon 3xxx drivers that isn't
[*]the official site (as it won't even let me download)
[*]or [http://wiki.cchtml.com/index.php/9.11](http://wiki.cchtml.com/index.php/9.11) as any time I download the file, it is corrupted and won't pass checksum
[*]I have been googling, it hasn't done me much good.  I was hoping that some others had run into similar problems.
[*]Now my long winded explanation:
[/LIST]

I've been trying the official site, but the download fails every time, due to a "/tmp/XAmcEOwy.bin.part could not be saved, because the source file could not be read." error.  

I've tried this site here (also the site I'm getting my instructions for install at [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide#Installing_the_drivers_manually), as it has a link to the driver I need, but there's a checksum error every time I attempt to install the driver.  Which is odd, because if I understand checksum (unlikely), the file, if it's corrupted on the distributor's end should render the same failing checksum every time.  In my case however, it yields a different, yet still failing checksum everytime, which I would imagine means it's getting corrupted in download.  I've tried to download in two different browsers, firefox and epiphany, but firefox is the only browser capable of actually getting to that download site, as epiphany can't connect for some reason.  

I guess all that is sort of irrellevant, hence the summary above and below the post.


SUMMARY:
[LIST]
[*]I need a download source for the HD Radeon 3xxx drivers that isn't
[*]the official site (as it won't even let me download)
[*]or [http://wiki.cchtml.com/index.php/9.11](http://wiki.cchtml.com/index.php/9.11) as any time I download the file, it is corrupted and won't pass checksum
[*]I have been googling, it hasn't done me much good.  I was hoping that some others had run into similar problems.
[/LIST]

---

### Post by u.b.u.n.t.u on 2009-12-03
Linux x86 or Linux x86_64?

---

### Post by ucal on 2009-12-03
> **u.b.u.n.t.u said:**
> Linux x86 or Linux x86_64?

x86_64.

---

### Post by u.b.u.n.t.u on 2009-12-03
Use a download manager.

[https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-11-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-9-11-x86.x86_64.run)


source:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.5&lang=English)

Alternatively try a different browser or set up a proxy to connect or download via a live CD of Ubuntu 9.10.

There is really no good reason not to be able to download ATI drivers.

---

### Post by ucal on 2009-12-03
Still getting a checksum error.  How would I go about setting up a proxy to download by live cd?

Is there any way to bipass the checksum error?

Alternatively, is there any way to do this other than "sh"ing the file?

EDIT:  I noticed on your wiki that the driver itself doesn't work with 9.10.  So even if I get it installed, it isn't going to help me get past the error that caused me to want to update it in the first place?

---

### Post by u.b.u.n.t.u on 2009-12-03
> **ucal said:**
> Still getting a checksum error.  How would I go about setting up a proxy to download by live cd?

Is there any way to bipass the checksum error?


Sorry to say this, but google that question. I would consider contacting your ISP helpdesk (as long as it is free to do so) and explain the problem.

> **ucal said:**
> Alternatively, is there any way to do this other than "sh"ing the file?


I think that is not an appropriate solution. You need free and open access to ATI drivers. That is the only acceptable solution.

> **ucal said:**
> EDIT:  I noticed on your wiki that the driver itself doesn't work with 9.10.  So even if I get it installed, it isn't going to help me get past the error that caused me to want to update it in the first place?

Maybe.

ATI 9.11 linux drivers do not work with my HD4850 GPU. They cause Ubuntu 9.10 to freeze at boot. Removal of the xorg.conf file, thereby defaulting to the VESA drivers is the only solution.

However ATI seem to update their drivers about once a month and so 9.12 may be released this month and hopefully resolve the problem.

---

### Post by ucal on 2009-12-03
I was able to download a non corrupted version today.  New driver successfully installed.  No idea why my dl was getting corrupted so much yesterday.

---

### Post by u.b.u.n.t.u on 2009-12-03
> **ucal said:**
> I was able to download a non corrupted version today.  New driver successfully installed.  No idea why my dl was getting corrupted so much yesterday.

Various possible reasons. Good that you have it sorted.

---

