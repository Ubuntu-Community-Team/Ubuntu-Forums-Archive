---
title: "Ubuntu 6.06 upgrade failed (because of space). And now ?"
date: 2006-07-10
forum: Installation &amp; Upgrades
---

### Post by gcmelzi on 2006-07-10
Team, 
I'm quite new of Ubuntu: I have been running 5.10 for a few months on my old desktop (working well for my wife and my daugther's e.mail), installing all updates when suggested by the system.
When I saw system upgrade available, I just pushed the button: it took a while to download and upgrade, asking from time to time if I want to keep or subsitute modified scripts, and at the end, the system told me the upgrade was not successfull, and the system itself is unstable. 
Now, when I boot, I get the loging prompt, the password request, and then ... the login prompt again, as weel as the password request ... 
No user can login.
What can I do (other then check disk space requirements next time, as my disk space is right 3G) ? 
Thanks

---

### Post by john_spiral on 2006-07-10
choose the safe ubuntu option from the grub or lilo screen then run the below command in the shell:

sudo du -h

du: disk usage, not sure if it needs sudo powers but what the hell

---

### Post by gcmelzi on 2006-07-10
John,
   I run the command you suggested, but got a number of rows, one for each directory or more ... what should I get from the command ? Or do you want I save and append the output ?
Thanks. 
Giancarlo

---

### Post by whywontitwork on 2006-07-10
Hi this is my first post on the site


Gcmelzi

That’s amazing because the very same thing has just happened to me!

I’ve been using windows for about 10 years but the GWA rubbish is doing my head in! (if you know what I mean!) I had a “winmodem” so couldn’t use linux on the internet :-({|= 

Anyway just got a adsl router/modem – :p 

I tried installing ubuntu 5.04 from linux magazine DVD (first go at installing linux) it seemed to install ok and after rebooting asked if I wanted to download updates [-o< 

Answer ok and it seemed to download a huge amount of stuff – the said error out of space! –hell!:mad: 

Spent several hours tying to do the same thing again (with a bigger harddisk!) but it won’t reboot after the first part of the install –why?!:confused: 

Just read a thread about the boot loader problems![-X 

Totally fed-up

Oh well there is all day tomorrow to try again!


Andy:cool:

---

### Post by gcmelzi on 2006-07-10
Hi Andy, 
I must say Breezy worked fine: I installed it on February (grub, old dasd, 6G, to WIN98, another 3.2G dasd for Ubuntu), and updated every time suggested. I managed to get more users installed, a WiFi connection using Ndiswrapper, the desktop is now a printer server at home (others are using laptops), my wife has her own mail client under Thunderbird and my daughter is messaging her friends on MSN. But I made the mistake of upgrading the system (not just the proposed application) not checking the prereq. ](*,) 

Giancarlo

---

### Post by whywontitwork on 2006-07-10
hi Giancarlo:D 

I’m a total newbie with linux

I’m ok with things like partitioning and sorting hardware etc;) 

But there seems to be a serious fault with the new (6.06) update?:rolleyes: 

Especially the grub thingy](*,) 

Might try installing 5.04 from my DVD but without letting it update!

(I’m a point and click type of bloke!)

Andy8)

---

### Post by john_spiral on 2006-07-10
sorry gcmelzi gave wrong command (late night) command is:

df -h 

displays disc usage, please post your results

---

### Post by gcmelzi on 2006-07-11
Hi John, 
   here you are:

Filesystem   Dimens.  Usati   Disp.  Uso%   Montato su
/dev/hdb1      2.9G    2.7G      0   100%   /
varrun         125M     20K   125M     1%   /var/run
varlock        125M    4.0K   125M     1%   /var/lock
udev           125M    120K   125M     1%   /dev
devshm         125M       0   125M     0%   /dev/shm
lrm            125M     19M   107M    15%   /lib/modules/2.6.15-25-386/volatile
/dev/hda1      6.4G    3.8G   2.6G    60%   /media/windows

Thanks.
Giancarlo
(using fixed fonts looks quite better ...)

---

### Post by john_spiral on 2006-07-12
Hi gcmelzi!

looks like your hdb1 (second drive first partition) is well full :( 

Do you have any spare drives or can you afford to purchase say a 10GIG second hand drive?

---

### Post by gcmelzi on 2006-07-12
John,
I would like to recover some functionalities on this system, while looking for a second hand PC as the processor is slow, too (Celeron 400MHz).
I understand one of the option is start from new with a downloaded CD, I wonder whether I can recover the configuration work I did, unless 3G are not really enough for the new version. 
Other option is to get rid of Windows, why not?

---

### Post by gcmelzi on 2006-07-13
Hi John,
   yesterday night I've been able to free up some 1% space and the Gnome desktop went up (telling me 99% of the space is used).:mrgreen: 
Now I wonder how to free up more space, like the space used by temporary upgrade files which were never cleaned up because of the crash of the update procedure.:-k 
The upgrade tool tells me all the installed software is up to date: do I've to rely on it ?

Thanks.

---

### Post by john_spiral on 2006-07-15
Hi gcmelzi,

found the below thread running a search on 'space' in the thread titles:

HOWTO: Cleaning up all those unnecessary junk files...

[http://www.ubuntuforums.org/showthread.php?t=140920](http://www.ubuntuforums.org/showthread.php?t=140920)

Please tell us if it was any good?

before I forget, empty your trash and remove any accounts that you don't need i.e /home/username

another thread that might free up some more space:

[http://www.ubuntuforums.org/showthread.php?t=209577&highlight=space](http://www.ubuntuforums.org/showthread.php?t=209577&highlight=space)

remove old linux versions:

[http://www.ubuntuforums.org/showthread.php?t=195540&highlight=space](http://www.ubuntuforums.org/showthread.php?t=195540&highlight=space)

another thread with more tips:

[http://www.ubuntuforums.org/showthread.php?t=161681&page=2&highlight=space](http://www.ubuntuforums.org/showthread.php?t=161681&page=2&highlight=space)

check last post on:

[http://www.ubuntuforums.org/showthread.php?t=148737&highlight=space](http://www.ubuntuforums.org/showthread.php?t=148737&highlight=space)

caio

John

---

### Post by gcmelzi on 2006-07-17
Hi John, 
how many advices!
Will give them a try, several looks interesting, and let you know.
Thanks for the time spent for me.

Ciao
Giancarlo

---

### Post by gcmelzi on 2006-07-17
Hi John, 
   following the first link I've been uble too free up 70M, following the second link, other 460 Meg were available, and further 85 following instractions from the 3rd link.
Nothing else from other links.

Thanks for your help. =D> 
Giancarlo.

---

### Post by john_spiral on 2006-07-18
It's looking better gcmelzi,

have you considered moving your system over to xubuntu it's tailored for low spec machines like yours?

---

### Post by gcmelzi on 2006-07-18
Frankly said, it's an option I never considered.
But reading through the presentation it looks quite better tailored for the kind of system I'm using.
I'll give it a try, my concern is what I've to reconfigure, starting from network etc.(btw, need to use a USB Wireless Network Card with Ndiswrapper and share printer with Windows users), as I assume I've to install everything from new to take full advantage from the reduced size of Xubuntu.
Thanks for your tip, indeed.

Giancarlo.

---

### Post by gcmelzi on 2006-07-18
Btw, which version do you suggest to download: standard or alternate install CD?
Thanks.

---

### Post by john_spiral on 2006-07-19
I've done some digging, it looks like the alternative CD gives you more control during the install. The alternative CD also gives less problems on older machines (no GUI install).

check the below threads:

[http://www.ubuntuforums.org/showthread.php?t=214155&highlight=xubuntu](http://www.ubuntuforums.org/showthread.php?t=214155&highlight=xubuntu)

[http://www.ubuntuforums.org/showthread.php?t=217884&highlight=xubuntu](http://www.ubuntuforums.org/showthread.php?t=217884&highlight=xubuntu)

---

### Post by gcmelzi on 2006-07-24
Hi John, 
   definitely I gave a try @ xubuntu and it really fits better on my old PC. The desktop CD doesn't work at all, but the alternate is ok (it took a life to install, then I discoverd the CDROM drive was not properly closed ...).
I managed to get my WiFi usb card supported, and restored user files for mail and gaim (tar working perfectly).
Everything OK?
Not really: I'm not able to install any printer (better, I installed the gnome-cups-manager, had a severe discussion with localhost:631 admin user/password, installed driver for my Canon Bjc3000, but the print test page just moved the paper inside the printer and nothing more ...), and in general I find hard to find any documentation/how to guide for the Xfce desktop manager (once you install an application using synaptic, how can you add it to your desktop menu ?, etc.). 
And this is costing me a lot of time, probably because I'm not able to find the proper guide.
But I'm under the impression there is still a lack of documentation on xubuntu, while I've been able to find it for ubuntu and kubuntu.
Can you suggest any useful source where look for documentation/guide/howto ?   
Thanks.

---

### Post by john_spiral on 2006-07-24
Doesn't seem like there is much about.

[http://xubuntu.wordpress.com/](http://xubuntu.wordpress.com/) has a few interesting topics.

---

