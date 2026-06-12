---
title: "First time 6.06 LTS server install"
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by marcosscriven on 2006-12-20
Hi

I have a plethora of Ubuntu 6.06 LTS server questions.

Just to give you a little background: I have been a software developer for 8 years (mostly Java), and have an degree in computing (just to give you an idea of what level to pitch answers). I have a fair bit of knowledge of the Linux/Unix command line, but have never really got my hands dirty with installing things or sorting out things like config files. It was more about writing and installing java programs and then managing them - always had a sysadmin or two around as I have always worked in huge companies. I am planning to start my own business in the next 6 to 12 months, and part of that is going to be writing and hosting sites myself. Obviously to start with I don't want to be employing anyone as I am not guaranteed work, so I need to get up to speed on the admin side of things, and fast. 

On the hardware side, I have a single dedicated server online now. It is a P4 3GHz, 1Gig mem, 120Gb SCSI HD, 2 IP addresses, and a REALLY groovy eRIC express, which is like a KVM over the net. I installed from the 'mini.iso' distribution, as I could easily mount that over the net as a virtual CD, and boot from it. I now have a clean 'mini' server install.

So, here goes with the questions:

1) Firstly, I was unsure about the partitioning. I did a bit of rushed Googling, and ended up with this:

marcosscriven@DSVR002007:~$ sudo fdisk -l
Password:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2            2433       14593    97683232+   5  Extended
/dev/sda5            2433       14225    94727241   83  Linux
/dev/sda6           14226       14593     2955928+  82  Linux swap / Solaris

So basically I have the first 20GB as a primary EXT3 partition mounted to '/'
The next 197GB as a logical EXT3 partition mounted to '/home'
And the final 3GB as a logical SWAP partition (I used 3GB only as that is what the autopartitioning recommended)

Is that setup ok? I basically see '/' as a place for apps (which could always be replaced), and '/home' as business data which I need to guard with my life! Any comments/suggestions on that, pleas let me know!

2) Ok, the only thing I have installed so far is sshd, so that I can log in without using the KVM console. Ideally I would like the LAMP install, but that was not available on the 'mini.iso'. I just used the 'server' option at the boot prompt. Is there a one-liner I can do to get the same thing?

3) I chose 6.06 LTS, rather than 6.10, specifically because of the 5 year security support/updates. However, would 6.10 be just as good security wise, but with more features?

4) When using 'apt-get', applications just sort of go to the right place magically. However, for the few apps which are in the repository, I need to know the best place to install them? Is it /usr/bin or what?

5) Secondly, I assume it is best to always install things (if you have to manually) as root?

6) I'd LOVE to see a summary somewhere of the first few levels of the directory tree in Ubuntu, which summarises which each area is for (IE a list like / is for root, /etc is for blah blah blah), the reasoing behind it, and if it differs from other distros.

7) When I do install apps, either with apt-get or manually, I want to somehow keep a record of the salient config files, so that at some point in the future, if I want to rebuild, I can simply plug those files in again. I assume the best way is to have them in my home dir, and softlink to them from teh relevant directories?

6) When it comes to creating directories for webfiles etc, again I want them in the /home dir somewhere, and softlinked from the /var/www dir. However, it doesn't seem right to have them in my home dir (/home/marcosscriven/). Should I set up a 'web' user for instance, and have it all in '/home/web'? Also, where should general, non web data go? Do I need to create a 'general' user, or is it ok just to create a directory called 'general' under /home, and if so, what user/group should I use? I just want to get things right from the start...

7) I know how to setup a cron job to run 'apt-get upgrade' every night, but on a production server I think that might be a bad thing. What would be better is if I could somehow get an email showing that updates had become available, and what they were. Then I could go and run it manually, and ensure things go smoothly. Is there a way to run apt-get upgrade so it doesn't actually *do* it, but says what it *would* do? I could then pipe that to an email.

8) I've heard of something called 'webmin', which looks like it would make things easier, but I wonder if anyone would recommend it? Or does it make things harder to maintain in the end? (IE I will end up never really knowing how to manually edit the config files, or even where they are)

9) Is there a way to run apt-get non-interactively, when it requires answers to questions? the reason being I would REALLY like to just write down every command I run, and the options used in install, to create a script that I can just simply run with no intervention on the next box with a clean Ubuntu build (if I ever need/get that far)

10) Hmm, what was the other question... Oh yes: With apt-get, I don't get the latest versions of apps. Is it therefore better to install manually from the files downloaded from the relevant webpages? 

11) Are there any 'top tips', particularly security wise, you can give? I really want a very tight and efficient build.

Sorry for all the questions, wasn't sure if it was best to put them all out in one go, or piecemeal.

If any of you are kind enough to respond, even to just one, could you possibly give them the same numbers I have given them, for easy reference for me, and hopefully others!

Thanks

Marcos

---

### Post by derby007 on 2006-12-21
Piecemeal is the way to go: if u are prepared to browse around all the 'posts' and good at googling, i think you'll find all your answers.
3) Dapper 6.06 LTS is the way to go
5) ...manually...as root.... : yeah, ie. if u are installing .deb files, just 'double-click' on them and a Gdebi manager (or similar) window opens. Be aware of dependencies.
11) tips: [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

