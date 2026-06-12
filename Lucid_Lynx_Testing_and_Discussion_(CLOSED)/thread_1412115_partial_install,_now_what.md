---
title: "partial install, now what?"
date: 2010-02-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by gmoore777 on 2010-02-20
So I was installing LucidLynx from the Alternate CD (burned on Friday 2/19/2010), cause
I needed that to create an encrypted partition. I did all the
steps for encryption, LVM, Volumes, mount points, etc, 
but after it asked me for HTTP Proxy, I got a red screen and 
it said the installation failed at "Select and install software".
I tried that step a few more times, they failed, I skipped that step and did the Grub2 step and then the installation finished.

Rebooted. 

Grub comes up, I chose the top menu item (it was blinking as well).
It prompted for my Passphrase (cause this partition is now encrypted).
I end up at a black screen login prompt.(not surprising)
I can log in.
`dpkg -l | wc -l` shows only 280 packages installed.
/etc/apt/sources.list still only points to the CDROM.

So the big question: is there a way to salvage this partial
install or am I screwed and have to burn a new CD (slower speed)
and start all over?

---

### Post by gmoore777 on 2010-02-20
i just burned a new LucidLynx Alternate CD from today's build
and burned it at 9X instead of 47X, and I got the same exact problem at, I think, the same spot.
After the Proxy question, after apt gets it's 32 or so packages, then starts installing other stuff, then craps out.

---

### Post by Ibidem on 2010-02-20
I assume that it's Ubuntu proper.  Otherwise, substitute the name for ubuntu.
Insert CD, run Aptitude (if it is there) (sudo aptitude), select the ubuntu-desktop package from the CD.
(press /,
type name,
press +,
press g twice)
Wait till that's done.
If you don't have Aptitude, run
sudo apt-get install ubuntu-desktop
You should be able to run startx or gdm; when you reboot, it *should *give you a graphical login.

Ibidem

---

### Post by Ibidem on 2010-02-20
> **gmoore777 said:**
> i just burned a new LucidLynx Alternate CD from today's build
and burned it at 9X instead of 47X, and I got the same exact problem at, I think, the same spot.
After the Proxy question, after apt gets it's 32 or so packages, then starts installing other stuff, then craps out.
 
What repository are you using, and is your network connection good?

---

### Post by gmoore777 on 2010-02-20
getting image from:
[http://cdimage.ubuntu.com/daily/current/lucid-alternate-amd64.iso](http://cdimage.ubuntu.com/daily/current/lucid-alternate-amd64.iso)

I can try another network cable, but I believe the network connection is fine. (i'm at work and doing all the Google-ing and Forum-ing from my other computers.)

I ran `sudo aptitude` after booting up, I get a character based aptitude, it says I have Installed Packages (275), Not installed Packages (1122), Virtual Packages (401), Tasks (1645).
Not sure how to operate this Aptitude. I'll have to Google some.

---

### Post by gmoore777 on 2010-02-20
i did the `sudo apt-get install ubuntu-desktop`. (i prefer this method)
it prompted for me to put CD in, I did, it wanted to install 932 packages. Hit Y.
Then it scrolled, possibly 932 lines of:
<file name>.deb File not found.

So either my CDROM burner is dead, my CD drive in this
brand new Dell laptop is flaky, or the .ISO image or
something about it is flaky.

---

### Post by sparker256 on 2010-02-20
> **gmoore777 said:**
> getting image from:
[http://cdimage.ubuntu.com/daily/current/lucid-alternate-amd64.iso](http://cdimage.ubuntu.com/daily/current/lucid-alternate-amd64.iso)

I can try another network cable, but I believe the network connection is fine. (i'm at work and doing all the Google-ing and Forum-ing from my other computers.)

I ran `sudo aptitude` after booting up, I get a character based aptitude, it says I have Installed Packages (275), Not installed Packages (1122), Virtual Packages (401), Tasks (1645).
Not sure how to operate this Aptitude. I'll have to Google some.

This is the command I use.

sudo aptitude update && sudo aptitude safe-upgrade

Bill

---

### Post by gmoore777 on 2010-02-20
So i observed that my CD's files were under:
/media/apt/
I had nothing under /cdrom.
So then I edited /etc/apt/sources.list and changed the only 
line there from:
  deb cdrom:[big name]/ lucid main restricted
to
  deb file:/media/apt/ lucid main restricted

`sudo apt-get update; sudo apt-get install ubuntu-desktop` is now chugging along...
It has finished. I've since rebooted a couple of times.
It looks good.
I had to go into Synaptic Package Manager --> Repositories and do
all the settings manually as this was untouched.

I wonder what other things didn't get done cause the "normal" install never finished.
Anyone know?

I also have the top line in the grub menu still blinking at me.
Is that a new feature or does Grub know something I don't.

Thanks for your help.

---

### Post by VMC on 2010-02-20
> **sparker256 said:**
> This is the command I use.

sudo aptitude update && sudo aptitude safe-upgrade

Bill

I was using aptitude ,until after the 6th crash, I stopped and started using apt-get. Now I have no problem.

 There are several bug reports against aptitude crashing. This is one [bug]("https://bugs.launchpad.net/ubuntu/+source/aptitude/+bug/522928") I reported.

---

