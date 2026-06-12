---
title: "Installation fails when entering User Info data"
date: 2021-06-07
forum: Installation &amp; Upgrades
---

### Post by daryl9 on 2021-06-07
I just replaced the hard drive in my laptop.  It had a spinning disk, and I replaced it with an SSD.  I downloaded ubuntu-20.04.2.0-desktop-amd64, put it on a USB drive and attempted to install.  

The disk check comes back with 269 errors, but I try the install anyway. It crashes as soon as I enter user logon information with > Installer encountered an error copying files to the hard drive.  Error 5 Input/Output.....

I rewrote the USB drive, same issue.  I redownloaded the ISO image, same error. I downloaded a third time directly from the REPO, this time I get 303 errors when checking the installation media.

I decided to try another distribution and it installed just fine.  I used the exact same USB drive and SSD hard drive so there are no issues with either of them.  I'm guessing there must be an issue with the ISO image getting corrupted or something.  The checksum check out just fine, so I really don't know why I'm having this issue.

Thanks

Daryl

---

### Post by QIII on 2021-06-07
From what URL did you download?

---

### Post by TheFu on 2021-06-07
Probably corrupted download.
Are you checking the ISO **sha256sum** file before trying to shove it onto the flash storage?  Reputable download sites will have the ISO and the sha256sum data for comparison.  

If the sha256 checks out, then there is something wrong with the method used to put the ISO onto the flash media.  I use **cp** to follow the K.I.S.S. principle.  dd, ddrescue, or if you want to use bloated tools, rufus, unetbootin, or etcher can be used.  Meh.   cp is already there and works.  Just target the flash drive device in /dev/ .... the whole device, not a partition.  Don't get the wrong device. It is easy to wipe your OS if you get the wrong one.

---

### Post by daryl9 on 2021-06-09
The first two downloads came from this URL:
[https://ubuntu.com/download/desktop/thank-you?version=20.04.2.0&architecture=amd64](https://ubuntu.com/download/desktop/thank-you?version=20.04.2.0&architecture=amd64)

The third download came from this URL:
[http://www.releases.ubuntu.com/20.04/ubuntu-20.04.2.0-desktop-amd64.iso](http://www.releases.ubuntu.com/20.04/ubuntu-20.04.2.0-desktop-amd64.iso)

I use Rufus to install ISO's onto thumb drives, have for years and works just fine.  If I have my laptop working, then I probably would have used Etcher, but my laptop is not working, hence needing to do a fresh install.  The hard drive died and needed to be replaced, this is why I am rebuilding it.

Yes, I did verify the checksum, and yes, it checked out each and every time. 

I am currently running Fedora on this laptop.  CentOS and Fedora both install without issues.  I downloaded them images, verified the checksum, used Rufu to install the ISO onto the thumb drive and installed onto the laptop, so method is not the issue, the issue is with the ISO images itself. 

Daryl

---

### Post by TheFu on 2021-06-09
>  The disk check comes back with 269 errors, but I try the install anyway. It crashes as soon as I enter user logon information with 

Bad disk?  Have you looked at the SMART data?
Does the Live-Boot "Try Ubuntu" environment work?  Is it just an installation issue?

---

### Post by daryl9 on 2021-06-09
> **TheFu said:**
> Bad disk?  Have you looked at the SMART data?
Does the Live-Boot "Try Ubuntu" environment work?  Is it just an installation issue?

I wipe the USB drive and reformat it before installing the ISO image on it.  

I have a local repo that I use to patch and update my equipment.  Can I do a network install from that?  Is there a network installer somewhere that I can download?  I don't think that I've ever seen one out there.

Thanks

Daryl

---

### Post by TheFu on 2021-06-09
> **daryl9 said:**
> I wipe the USB drive and reformat it before installing the ISO image on it.  

I have a local repo that I use to patch and update my equipment.  Can I do a network install from that?  Is there a network installer somewhere that I can download?  I don't think that I've ever seen one out there.

You misunderstand.  I'm talking about the drive inside the computer where you want the install to write.  Is that disk ok or not?  New drives fail usually about 1% of them. Sometimes in the first few days and sometimes in the first few months.  That includes SSDs. 

Boot from the USB Flash drive where you "imaged" ubuntu. On the boot screen, there should be a "try ubuntu" option.  Choose that.  This should work and won't touch the internal computer storage until we specifically ask for that.  There should be a drive management tool - "Disks" in the menu somewhere.  Run that.  Select the entire drive (probably on the left pane), then look for "SMART" in the different menu choices. SMART is 2 steps.  

[LIST=1]
[*]Run a test
[*]View the results of a test
[/LIST]
Until the test is run, there isn't any viable SMART data to review.
A "short test" is less than 2-3 minutes for any storage today.
A "long test" is 3+ hrs for HDDs and probably 10 minutes for SSDs.
After the test time is up, review the results.  Look for things that should be zero, but aren't.  There are hundreds of posts in these forums about SMART data. There are lots of webpages, mainly from storage and storage testing software companies, that explain what each data element in SMART means.  This "Disks" GUI tool isn't the best interface to smart data. It dumbs the information down just a little too much, IMHO. There's a CLI tool - **smartclt** which is excellent.  The package name is **smartmontools**, I think. 

BTW, it is very helpful when replying if you could include the post you are replaying at, with the answers to the specific questions asked. We can't read minds, so we ask questions.

---

### Post by daryl9 on 2021-06-09
It took me some digging, but I found a network installer that I'll try.

Daryl

---

