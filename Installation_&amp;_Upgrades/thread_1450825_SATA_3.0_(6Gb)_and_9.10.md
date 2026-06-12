---
title: "SATA 3.0 (6Gb) and 9.10"
date: 2010-04-09
forum: Installation &amp; Upgrades
---

### Post by whammond on 2010-04-09
I'd like to install 9.10 on one of the Newer Motherboards that support SATA 3.0 (6Gb Drives), with a SATA 3.0 Drive.

Does anyone know if Ubuntu supports these new standards or needs to...?

---

### Post by Slim Odds on 2010-04-09
> **whammond said:**
> I'd like to install 9.10 on one of the Newer Motherboards that support SATA 3.0 (6Gb Drives), with a SATA 3.0 Drive.

Does anyone know if Ubuntu supports these new standards or needs to...?

Would it be hard to try it?

---

### Post by alexdelprogramador on 2010-04-09
> **Slim Odds said:**
> Would it be hard to try it?

yea!! :)

Im agree with slim.

you just only to start an ubuntu live-cd or live-usb, and see if your sata 3.0 device is located by the system.

If it does, it can be installed.

bye

---

### Post by whammond on 2010-04-09
To be more specific I set up a Server with a Gigabyte 790 chipset using OpenSuSE 11.2 as a Samba Server. It does a few strange things. Can't load a GUI, not a problem. But to log in you have to cause the graphic login to fail once, then it's takes you to the command line login. Not the more serious issue.

This Server hosts DBF Files for a legacy Foxpro Application. It seems to have problems opening and closing files, will sometime hold a lock even though the files have all been closed.

Could be a Samba Issue, but his all worked great until the new motherboard and Hard Drive.

My first avenue of investigation was to see if any of the Distros support or even need to
support the new standards.

I'm sure that the new SATA 3.0 (6Gb Data Transfer) is backwardly compatible, but what I want is faster, that mean support for the Standard.

I could go to a Server Motherboard configuration with SAS, but for a small File Server it would be very expensive and overkill for the need.

---

### Post by Sundevildaddy on 2011-01-11
As we have just torn our hair out over for the past couple of hours, No, Ubuntu will not recognize Sata 3.0 on IDE drive settings.

It WILL, however, recognize Sata 3 on AHCI (Boot Settings > set ALL IDE settings to AHCI/Like Sata Drive settings).  Please note: If you are Dual Booting with Windows, you wil BSOD (*gasp* big surprise) and be unable to load Winblows.

This has to be performed on a "Clean" system with no OS installed. 

If you wish to Dual Boot, switch to AHCI FIRST, then install Winblows SECOND, then Ubuntu.  (Installing Ubuntu before Win is a headache [to say the least] waiting to happen).

Hope this helps everyone avoid the trials, tribulations, hair-pulling and down right joyous time we just had *facepalms* 

(to note: if using a MECHANICAL HDD, you will not notice any difference in speeds.  Please read >> [http://ubuntuforums.org/showthread.php?t=1456238](http://ubuntuforums.org/showthread.php?t=1456238) "Looking at this review:
[http://www.testfreaks.com/blog/revie...-st32000641as/]("http://www.testfreaks.com/blog/review/review-of-seagate-2tb-barracuda-xt-sata6-desktop-hard-drive-st32000641as/")

It looks like we should not expect much out of SATA3 when using a mechanical HD !!! :sad:

I guess I have to settle with this, not so bad, of a speed!"""

~Sun
:guitar:

---

