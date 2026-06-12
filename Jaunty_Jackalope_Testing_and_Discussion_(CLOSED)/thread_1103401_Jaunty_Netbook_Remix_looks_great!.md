---
title: "Jaunty Netbook Remix looks great!"
date: 2009-03-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jespdj on 2009-03-22
I noticed on the [Jaunty Alpha 6 download page](http://cdimage.ubuntu.com/releases/jaunty/alpha-6/) that there's an image for Jaunty Netbook Remix.

So I downloaded it, dd'ed it to an 1 GB USB stick and booted it on my Dell Mini 9. It works great! When Jaunty comes out I'm going to install this on my Mini 9.

Ubuntu 8.04 or 8.10 Netbook Remix were not really available as officially supported releases, as far as I know. Will Jaunty Netbook Remix be officially available just like the normal Ubuntu / Kubuntu / Xubuntu etc. releases?

---

### Post by robert.rankin.jr on 2009-03-22
There was an 8.10 netbook remix during alpha and beta. I can't seem to find it anywhere now, though. But I didn't like it at the time. Maybe this one is better? I'll check it out.

Seems like I found a hardy version here: [https://wiki.ubuntu.com/UNR#UNR%20Hardy%20Image%20Installation](https://wiki.ubuntu.com/UNR#UNR%20Hardy%20Image%20Installation)

Robert

---

### Post by rockin_goliath on 2009-03-22
Has its appearance changed at all? Screenshots please?

---

### Post by andrewabc on 2009-03-22
Where can I see screenshots of 9.04 UNR?
Or does it look the same as 8.10?

---

### Post by robert.rankin.jr on 2009-03-22
A screenshot is attached, as of Alpha 6. I haven't run all the updates yet, so don't know what changes there might be. The notification system doesn't seem to be updated, though, at this point.

Robert

---

### Post by MadsRH on 2009-03-23
Has the Netbook Remix the same release date as Ubuntu 9.04?

What's up with the icons? Canonical should really add high-res versions. These blurry ones looks really unprofessional.

---

### Post by cdwillis on 2009-03-23
I installed 9.04 netbook remix on my eee pc 1000he, but I immediately converted it to a regular style desktop. I just don't see a need for it.

---

### Post by ronacc on 2009-03-23
what is the cmd to burn netbook-remix to a usb stick ?

---

### Post by BCurtisWX on 2009-03-23
> **ronacc said:**
> what is the cmd to burn netbook-remix to a usb stick ?

dd if=<iso file name.iso> of=/dev/<location of USB flash drive>
(Note: This is a powerful command, make sure you know 100% that the of="" is truly your flash drive)
df will show you where your USB Flash Drive is mounted

---

### Post by rockin_goliath on 2009-03-23
You shouldn't need to use dd to do this, it might completely bork your usb stick. Why doesn't the LiveUSB utility (installed by default) in intrepid work for you?

---

### Post by dBuster on 2009-03-23
That netbook remix looks like it might be something that I could easily get my sister into...  Wonder how it will run on something other than a netbook??  Anyone tried it?  Screen resolution issues??

---

### Post by lzfy on 2009-03-23
What's the difference between this and the regular version besides the custom interface. Is it faster? does it include more drivers? I wanna try it on my Aspire One but have to know it for sure first.

---

### Post by pjalegria on 2009-03-23
I have it on my AAO and i love it, all hardware work, only a little tweak for wifi, and still is alpha realease :D

---

### Post by ronacc on 2009-03-23
> **rockin_goliath said:**
> You shouldn't need to use dd to do this, it might completely bork your usb stick. Why doesn't the LiveUSB utility (installed by default) in intrepid work for you?
 because the file is a .img and the live usb utility does not see it .

edit I'm not afraid of dd I've used it before I just got brainlock and forgot the exact format of the cmd .

---

### Post by andrewabc on 2009-03-23
> **ronacc said:**
> because the file is a .img and the live usb utility does not see it .


Wouldn't that be a bug?
Ubuntu has "create a usb startup disk", but it can not even load it's own images to usb sticks? Why would ubuntu use .img if its software can't even use it?

---

### Post by ronacc on 2009-03-23
I have no idea why they did it but both the netbook-remix and the mid low power arch  are .img not .iso , I agree it is strange since those are 2 that are very likely to be burned to a usb stick .

---

### Post by cdwillis on 2009-03-23
Correct me if I'm wrong but the program that creates the bootable usb stick uses iso images because it's for the average joe who doesn't know to download the img and use dd.

---

### Post by ronacc on 2009-03-23
the home page for unetbootin implies that it will work with .img files also but it wouldn't for me .

---

### Post by sgosnell on 2009-03-23
I installed the NBR on my Asus eee 701, and found it unusable.  The default action is for all the icons to be activated by a single click, making mouse movement across the desktop erratic and slow, because every icon grabs the focus.  The concept is good, the execution not so good.  If there were a way to change that, I would use it, but I didn't have the patience to suffer through the pain to investigate the settings possibilities.  I just ditched it.

---

### Post by ronacc on 2009-03-23
I'll be trying it later tonight on my eee 701 I'll see what I can do to change the behavior ( nautilus preferences ? ) .

---

### Post by dixon on 2009-03-23
I use [imagewriter]("http://ppa.launchpad.net/ogra/ubuntu/pool/main/u/usb-imagewriter/usb-imagewriter_0.1-1%7Eppa1_all.deb") to install the img onto my usb drive. But yet no luck - it's not working on HP mini 2140.

---

### Post by LegendofTom on 2009-03-23
Any idea if this will work on a Dell Mini 12?

---

### Post by joey-elijah on 2009-03-23
> **ronacc said:**
> I'll be trying it later tonight on my eee 701 I'll see what I can do to change the behavior ( nautilus preferences ? ) .

I'll await that post with eagerness, i have hardy with netbook remix interface and the array kernel all set up nicely atm so i don't want to ruin my little set up! Screen grabs would be great too

---

### Post by ronacc on 2009-03-23
I haven't installed it I just have it running off the usb stick but that shouldn't make any difference . The eratic / slow mouse movement only occurs on the remix desktop not in any windows/progs , it also occurs whether using mouse or touchpad . I haven't found where to try to tweek the behavior yet ( it wasn't nautilus preferences) , it must be a config issue since the essentialy the same interface does not act this way in eeebuntu or other remix editions . It is definately a problem with netbook-launcher , switching to the standard destop all is normal . I didn't do a screenshot , it looks the same to me as any other iteration of netbook-launcher . I prefer the regular desktop anyway .

---

### Post by andrewabc on 2009-03-23
> **cdwillis said:**
> Correct me if I'm wrong but the program that creates the bootable usb stick uses iso images because it's for the average joe who doesn't know to download the img and use dd.

I've been using ubuntu since 2006 and I have no idea what dd is. I don't want to use command line to put a bootable image on usb stick.

So if ubuntu program is for people who don't know what dd is, but it doesn't use .img which ubuntu offers that leaves me very confused and would make it difficult for netbook people to install ubuntu.

---

### Post by robert.rankin.jr on 2009-03-23
[https://bugs.launchpad.net/unetbootin/+bug/347678](https://bugs.launchpad.net/unetbootin/+bug/347678)

---

### Post by ronacc on 2009-03-23
confirmed your bug .

---

### Post by ronacc on 2009-03-23
opened bug# 347704  for erratic mouse in netbook-launcher .

---

### Post by #ernesto on 2009-03-25
Jaunty Alpha 6 Netbook Remix on MSI Wind netbook, running ok, with wifi driver working with no special configuration. Jaunty comes with the rtl8187 wifi drivers that weren't on Intrepid.
I installed it using Jaunty img on a pendrive with dd.

screenshot.

---

### Post by andrewabc on 2009-03-25
> **#ernesto said:**
> Jaunty Alpha 6 Netbook Remix on MSI Wind netbook, running ok, with wifi driver working with no special configuration. Jaunty comes with the rtl8187 wifi drivers that weren't on Intrepid.
I installed it using Jaunty img on a pendrive with dd.

screenshot.

To get the programs screen up (what is in your screenshot), do you just click on the top left ubuntu icon and it appears?

---

### Post by sgosnell on 2009-03-26
That's the desktop.  It's always there.  It works like a PDA, with the icons in place, and one click launches everything.  That's the problem, because every icon grabs the mouse cursor as soon as it touches the edge of the icon, and doesn't want to give it up.  The cursor is thus very slow and jerky, and the desktop is essentially unusable.  If a double-click were required, it would be much, much better.  Until that is changed, I won't use it.

---

### Post by rhbusby on 2009-03-26
I have the Jaunty remix on my Dell Mini 9. 32GB SSD, 2GB Ram,  Bios A04, 4GB SDHC card. I put it on a USB  drive using flashnul (I know it is a windows program. Oh well! :() It went on 1st try no problems. Only minor issue is teh sou8nd isue which I fixed by adding the line to the conf file. It  just works!  Even my GF who is a total Linux newbie is usingit and loves it. She has even embraced Open Office. 
I am drafting this reply oo  the Dell Mini, in fact.  It is Very easy!

Now working on GPS  and BT (have not tried them yet)

Even bought a second one so I can make a Hacintosh out of it (maybe).

:popcorn:

---

### Post by ecrisfield on 2009-03-28
So, I too am confused about the .img and .iso problem. I wanted to use USBCreator to make the 9.04 live usb, but I can't force the program to see anything but .iso. I can't find a way to convert .img to .iso.

Did I understand from a previous post that I can make a live usb from a .img using dd? And if so, could someone post the command again?

EDIT: OK, actually I found some nice help here:
[https://wiki.ubuntu.com/MobileTeam/Mobile/HowTo/ImageWriting](https://wiki.ubuntu.com/MobileTeam/Mobile/HowTo/ImageWriting)

---

### Post by SlCKB0Y on 2009-04-01
If youve got an aspire one Why not try my custom aspire one kernel?

It has lots of advantages

Faster boot time
Better Aspire One hardware support
Wifi LED functional
TuxOnIce for fast hibernation
Acerhdf for kernel fan control
PHC for undervolting and increased battery life

Jaunty works pretty well with the Aspire One and my kernel makes it better
The latest kernel is available at 
[http://www.ug.it.usyd.edu.au/~scole/releases/linux-image-2.6.28.3.20090331_sickboy.0.6_i386.deb](http://www.ug.it.usyd.edu.au/~scole/releases/linux-image-2.6.28.3.20090331_sickboy.0.6_i386.deb)

and normally they can be found at [www.aspireonekernel.com](www.aspireonekernel.com)

---

### Post by dazzler on 2009-04-01
I have Netbook Remix 8.04 currentl running on my eeepc, is there a terminal command to upgrade to jaunty as in the main distro?

---

### Post by howbag on 2009-04-02
> **dazzler said:**
> I have Netbook Remix 8.04 currentl running on my eeepc, is there a terminal command to upgrade to jaunty as in the main distro?

That would be ```
sudo update-manager -d
``` note that this will upgrade to the next release, so first to 8.10, then to 9.04

---

### Post by dazzler on 2009-04-02
> **howbag said:**
> That would be ```
sudo update-manager -d
``` note that this will upgrade to the next release, so first to 8.10, then to 9.04

Thank you didnt know if that command would just download the standard upgrade or not.

cheers

---

### Post by jake74 on 2009-04-19
Any news on a fix for the 701 EEE slow/jumpy behaviour in the UNR launcher?

---

### Post by go7Ul1ai on 2009-04-19
Edit: Meh.. Nevermind..

---

