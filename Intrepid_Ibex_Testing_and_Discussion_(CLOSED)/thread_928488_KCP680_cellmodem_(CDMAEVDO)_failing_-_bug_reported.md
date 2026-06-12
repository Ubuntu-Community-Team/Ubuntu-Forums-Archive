---
title: "KCP680 cellmodem (CDMA/EVDO) failing - bug reported, and airprime module MISSING!?"
date: 2008-09-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Jim March on 2008-09-24
Short form: my Kyocera KPC680 cellmodem works great at first but then the connection dies after a few minutes.  Manually restarting can result in a full system freeze.

I've filed a very detailed bug report at:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/273842](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/273842)

I won't re-hash everything here but basically everybody who has managed to get this card working (in previous Ubuntus using WVDial scripts) has tweaked on the airprime.c file and then compiled it as a kernel module.  After downloading the sources to 2.6.27-4 and searching it, there's NO airprime-anything in there so the system is apparently using "something else" (Goddess only knows what) and it's blowing rainbow chunks.

Best answer: somebody has an airprime module set up with KPC680 stuff in it, or worst case I can use a 2006/7-era version and tweak it to add KPC680 info.  Thanks to a utility called USBView I have serious details on this card; I've posted the complete output of that program into the bug report above.

Anybody have any more info as to what's up here?

---

### Post by Nullack on 2008-09-24
Without meeting this its likely to be marked incomplete:

[https://wiki.ubuntu.com/KernelTeamBugPolicies](https://wiki.ubuntu.com/KernelTeamBugPolicies)

Also Jim is this a regression - did it work in Hardy? If so, please tag as per:

[http://ubuntuforums.org/showthread.php?t=924782](http://ubuntuforums.org/showthread.php?t=924782)

---

### Post by Jim March on 2008-09-24
I don't know if this is a regression or not, because I don't know if the airprime driver was included in Hardy.  I have a grand total of one computer to work with and it's on Intrepid as I type this.

I put the attachments in there, and odd thing: lspci-vvnn.log has NO entry for the KPC680 even though it was in there and recognized by NM7.  Does that mean there's no kernel-level support present?

---

### Post by Jim March on 2008-09-24
Ah...turns out the support for my critter has migrated to a driver called "option" at /linux-source-2.6.27/drivers/usb/serial - looking at option.c it's obvious KPC680 support is at least supposed to be in there.

Huh.

Ummm...anybody got an idea why it's barfing? There's a patch covering this card in this file documented at:

[http://www.mail-archive.com/linux-usb@vger.kernel.org/msg01944.html](http://www.mail-archive.com/linux-usb@vger.kernel.org/msg01944.html)

The code doesn't look quite the same as what's in Ubuntu's option.c file but knowing nothing about this language :( I can't tell if the Dan Williams patch code is functionally equivelent to what's in option.c or not...

:(

---

### Post by Jim March on 2008-10-04
ALL my problems are now solved.  I'm updated to the Beta1 state but that wasn't the fix - the issue was edits to /etc/ppp/options as I've described here:

[http://ubuntuforums.org/showpost.php?p=5903831&postcount=9](http://ubuntuforums.org/showpost.php?p=5903831&postcount=9)

Short form: do:

sudo gedit /etc/ppp/options

...and look for the lines "lcp-echo-interval" and "lcp-echo-failure" - set both to "0" (no quotes, and a space before the 0) instead of the defaults.

Before finding this I had trouble with this card AND a Sprint-based U680 device borrowed from a friend (which despite the "680" is a totally different critter internally from the KPC680).  I'm not able to test this setup with the Sprint U680 but I suspect this is the answer.

---

