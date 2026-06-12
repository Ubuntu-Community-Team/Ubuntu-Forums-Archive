---
title: "Disk usage outside design parameters"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by johnnybirdman on 2009-10-02
I see no forum posts on this issue.  Testing 9.10 beta on my dell Mini 9 (4GB SSD; stock from Dell)  I'm getting an error message and icon:
> DISK IS BEING USED OUTSIDE DESIGN PARAMETERS
Has anyone else encountered this error?

J.

---

### Post by Meow27 on 2009-10-02
i think its that ubuntu expects you to have ~4.5 GB free,

are you using the netbook version?

---

### Post by anyusername on 2009-10-02
Yes, I'm seeing it on my Asus Eee PC, with 4Gb SSD 'Hard Disk'. The advanced is showing a 'Read Error Rate' warning. I've only seen this message since installing Ubuntu 9.10.

---

### Post by johnnybirdman on 2009-10-06
> **Meow27 said:**
> i think its that ubuntu expects you to have ~4.5 GB free,

are you using the netbook version?

I am not using the UNR version, I didn't care for the 9.04 version but maybe I'll have to try the 9.10 UNR.
I guess with Ubuntu size does matter.
J.

---

### Post by johnnybirdman on 2009-10-06
> **anyusername said:**
> Yes, I'm seeing it on my Asus Eee PC, with 4Gb SSD 'Hard Disk'. The advanced is showing a 'Read Error Rate' warning. I've only seen this message since installing Ubuntu 9.10.

Yes.  I've had Ubuntu 9.04 installed for some time and no issues/warnings like this before 9.10 beta install (which is the first 9.10 install I've tried on my mini.)
J.

---

### Post by kansasnoob on 2009-10-06
Disc usage is crazy bad right now:

> lance@lance-desktop:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
[COLOR="Red"]/dev/sda3              6.3G   4.7G   1.4G  78% /[/COLOR]
udev                   1.1G   279k   1.1G   1% /dev
none                   1.1G   115k   1.1G   1% /dev/shm
none                   1.1G    95k   1.1G   1% /var/run
none                   1.1G      0   1.1G   0% /var/lock
none                   1.1G      0   1.1G   0% /lib/init/rw
/dev/sda10              11G   1.6G   8.7G  16% /home


I haven't yet figured out why but I suspect something to do with the "headers" updates earlier today, and I'd expect to see this resolve itself through updates very soon - probably with a kernel update to -12.

---

### Post by samichx on 2009-10-06
Another ASUS EEE 4G (701) Using UNR 9.10 with this error here. Although I am concerned that the error message is not a mistake. It is possibly a problem with ext4 as my girlfriend with another ASUS EEE does not have the same problem after keeping her ext3fs since Ubuntu8.

Can anyone else confirm this? Is there a conflict between small flash devices and ext4?

---

### Post by Robert Johnson on 2009-10-10
Yes, I'm being presented with the same error while running a liveUSB of UNR Karmic Beta (i386) on a Dell Mini 9 with a 4GB SSD. 

This SSD currently has UNR Jaunty (i386) on it. The Mini, of course, shipped with Dell's Ubuntu (lpia). The UNR (i386) install seemed to take up less space than Dell's install. My usage was about 70% after the UNR install, and I've filled it up to 90%.

Anyway, yes, I had no reason to suspect I would be having these alarming-looking S.M.A.R.T. errors in red, the tone of which is roughly "OMG copy all your stuff off of this disk NOW, it's about to goooooooooo" 

It says to "Backup all data and replace the disk" and lists several numbered attributes that it says are failing. Not the best introduction to Ubuntu, perhaps. Or maybe all our Mini 9 4GBs are failing now. What do you think?

---

### Post by Ormente on 2009-10-10
I had this also on a 701, one time. I checked my power manager options, and there unchecked the "stop hard drive when possible" option on the "on battery" tab (not sure for the words, as my Karmic is in french, but you get the idea). That seamed to solve the issue, but can't be sure because i gave the eee to a friend right after that and have no news about it.

---

### Post by ChristianConservative.ca on 2009-10-17
Same error here with my 9.10 Beta install, EeePC 701, 4GB solid state drive, installed via USB key with the UNR recommended partition allocation.

---

### Post by ChristianConservative.ca on 2009-10-17
Update, I actually noticed mine was also set to "Spin down disk when possible" in the Power Management console for "On Battery". Removed that checkbox, put it back into suspend mode, fired it back up like last time, error didn't reoccur.

Makes sense since there's no hard drive to spin down... perhaps sending a signal to the HDD that it doesn't understand... "outside parameters", if you will.  ;-)

---

### Post by ChristianConservative.ca on 2009-10-17
SCRATCH THAT... after a longer suspend, the same error comes up.  I'm thinking bug.

---

### Post by bennachie on 2009-10-17
I have experienced the same problem on my eeePC 4G (along with the hoary old message about the battery being broken, which I thought had been fixed). 

When the problem first arose, I tried both UNR and vanilla Gnome, getting the same "disk usage outside design parameters" message with both versions.

Incidentally, I am not certain that there are any real benefits to UNR on the eeePC 4G (there may be performance advantages on Atom-based netbooks) other than a marginal saving in screen real estate. UNR actually seems to use more disk space than the vanilla version, but neither could really be described as a resource hog. 

I have since carried out yet another install and update of the Gnome version. The update, of course, took me straight to the -14 kernel. So far, there have been no problems (apart from the irritating, but ultimately trivial, battery message).

---

### Post by ChristianConservative.ca on 2009-10-17
Getting the battery error as well.

---

### Post by johnnybirdman on 2009-10-18
> **ChristianConservative.ca said:**
> Getting the battery error as well.

I'm not getting any battery errors but the battery time seems to be much shorter than 9.04.

J.

---

### Post by ASJboarder on 2009-10-20
I have the same error.  Has anyone determined whether or not this is a Karmic issue or is my ssd actually failing?

Dell Mini 9 running 9.10 beta; stock ssd

---

### Post by sisyphus1978 on 2009-10-22
I thought it might be to do with ext3 on my eeepc 701 9.10 UNR so I reinstalled ext2. Just came back.

The question is, should I be worried?

---

### Post by johnnybirdman on 2009-10-22
> **sisyphus1978 said:**
> I thought it might be to do with ext3 on my eeepc 701 9.10 UNR so I reinstalled ext2. Just came back.

The question is, should I be worried?

There is nothing to confirm this as a legit error.  Also, after a search today there is no bug report to be found (from what I can tell).
I don't get this error with 9.04.

J.

---

### Post by danpre on 2009-10-26
I get the same disk error with 160GB SATA DISK
This is fresh install 9.10 with ext4 filesystem

Disk usage is only 7%.

DANIeL

---

### Post by johnnybirdman on 2009-10-27
> **danpre said:**
> I get the same disk error with 160GB SATA DISK
This is fresh install 9.10 with ext4 filesystem

Disk usage is only 7%.

DANIeL

Any reason to believe you disk is failing?
What type of disk?  SSD or standard HDD?
J.

---

### Post by danpre on 2009-10-27
> **johnnybirdman said:**
> Any reason to believe you disk is failing?
What type of disk?  SSD or standard HDD?
J.

sorry for false alarm

I have changed sata cable and it is ok now.
So, message was ok.

DANIeL

---

### Post by swiftsam on 2009-10-29
Just adding to the count of observations on this one.

I have an eeePC 701 4G, and just installed 9.10 netbook remix RC.  

No sign that anything was wrong before hand, and no actual performance problems now, but the "Disk is being used outside design parameters" warning has popped up a few times.

---

