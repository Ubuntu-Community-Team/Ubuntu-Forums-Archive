---
title: "Ubuntu 18.04 or 19.10 Installation Issues"
date: 2020-03-19
forum: Installation &amp; Upgrades
---

### Post by jt1990 on 2020-03-19
Good morning all,

I have a laptop (HP Pavilion 15-au063nr) that was having an issue with Ubuntu 16.04 where the log files kept rapidly expanding and filling the hard drive.  I did some research and found that the solution was to upgrade to the next version of Ubuntu - 18.04.  I have tried this multiple times, as well as upgrading to 19.10, with no success.  Every time I set the installation going it would freeze on formatting the hard drive.  So I replaced the hard drive.  Once or twice it got as far as "Almost finished copying files", but still froze and never finished installing.  I have been able to install Windows, I have been able to install Debian, but I have *not* been able to install Mint.  Does anybody have any ideas as to what the heck is going on with this?  I have run hardware self diagnostics and everything seems to check out.  As a side note, I *have* been able to get Ubuntu 16.04 installed, but it still gives the log file error and fills the hard drive up.

Thanks in advance for any suggestions!

---

### Post by dragonfly41 on 2020-03-19
If you have Windows running, one route I would follow is to install Rufus on Windows.  Next download a full Mint iso.
Then use Rufus to create a Mint LiveUSB. Then boot into the Mint LiveUSB to first try and then install Mint on the target drive.

Alternatively create Mint LiveUSB through mkusb on your Ubuntu 16.04.

These are just ideas since I do not use Mint.  But I do refer to [this Mint thread]("https://forums.linuxmint.com/viewtopic.php?t=287353") for advice on using rEFInd.

[P.S.] Neither am I an HP laptop user (I am on Dell) so[ I would study UEFI usage on your laptop]("https://support.hp.com/gb-en/document/c03801890").

---

### Post by jt1990 on 2020-03-19
I have tried setting up both Ubuntu and Mint through Rufus, but ultimately I am looking to get Ubuntu installed.  I will check into the UEFI thing...

Thanks!

---

### Post by jt1990 on 2020-03-23
Anybody have any more suggestions on this?  Thanks!

---

### Post by ipv on 2020-03-27
> **jt1990 said:**
> Anybody have any more suggestions on this?

start a fresh win install, preferably with a disc.

format & delete all partitions :

[ATTACH=CONFIG]285325[/ATTACH]

the entire disk, total size & free space, should now show as unallocated space :

[ATTACH=CONFIG]285326[/ATTACH]

do not click on new / next. close the installation window which will cancel the installation process.

pop-out the 10 disc, pop-in the 'buntu disc, re-boot & start installation. hopefully it should go through without a glitch.

this has helped me earlier when i was stuck on installation with a brand new seagate barracuda.

am assuming you have verified the check sums of the iso you have downloaded.

---

### Post by jt1990 on 2020-03-31
I have not verified the checksums, but I have tried this with several different versions of Ubuntu and anything above 18.04 gives me the error.  I will try with the Win10 disk and go from there.  Thanks for the suggestion!

---

