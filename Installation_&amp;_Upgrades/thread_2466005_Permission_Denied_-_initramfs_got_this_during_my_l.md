---
title: "Permission Denied - initramfs got this during my last update w/ generating kern links"
date: 2021-08-17
forum: Installation &amp; Upgrades
---

### Post by slaytanicprion on 2021-08-17
It's too bad I can't find, even through UM's Log Checker, those lines. But this morning some updates showed up, one being linux-firmware:all 1.187.16

Well, I don't know what's wrong with Software Updater. When update-initramfs was generating whatever it does when a kernel update is done, y'know, I can't find anybody who has had the same problem as me just now. I had installed 5.4.0-81 but had not rebooted yet. I got something similar to this but not exactly this :

```
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-21-generic
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_cMSNY6/scripts/init-premount/mdadm: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_cMSNY6/scripts/panic/console_setup: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_cMSNY6/scripts/local-premount/fixrtc: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_cMSNY6/scripts/local-premount/ntfs_3g: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_cMSNY6/scripts/local-premount/resume: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_cMSNY6/scripts/nfs-top/udev: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_cMSNY6/scripts/init-bottom/udev: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_cMSNY6/scripts/local-bottom/ntfs_3g: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_cMSNY6/scripts/init-top/all_generic_ide: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_cMSNY6/scripts/init-top/blacklist: Permission denied
/usr/sbin/mkinitramfs: 329: /tmp/mkinitramfs_cMSNY6/scripts/init-top/udev: Permission denied
```

Except Generating /boot/whatver 5.4.0-81 then 5.4.0-80 etc. was worded differently and it was denied the permission to update the firmware.

Now I'm told that next time I reboot, I might be screwed, initramfs is not acting normal. 

Even sudo update-initramfs to try and redo it manually tells me permission denied. What?!? I know the drive ubuntu is on would benefit from an fsck but I don't know how to do that without it destroying the system, so I'm pushing doing it until I got free time. Is Ubuntu now so insecure that somebody has entered my computer and is lowering sudo's access? I really don't like this, I'll have to backup everything I'm afraid (I haven't so far because that install is pretty new, I was waiting on being able to clear an entire drive just for Ubuntu. I got the "I had broadband in the late 90's" issue where I have so much data, moving everything around to create space on my internal drives is a headache, I need a larger third internal HDD, maybe a SSD (I'm obviously not going to run an OS on an external drive, even if I have a USB 3.0/SATA-III drive dock that is seen as internal by the system, it's not the best kind of HD, a WD Blue, it's just a data drive.) But I'm mentioning this here only because it could be a clue that the drive is having trouble. logs do tell me a lot about sdb (where ubuntu mate 20.4.2 is) having errors, but i'm able to run and install anything and I got no functionality bugs at all. Even gamed a bit from games on Steam and locally installed, a few games that have linux versions....everything's working fine. BUT... I do not like the little info about such errors on 3 search engines, that one is the closest to whats going, except it only hiccuped when linux-firmware's newest version, not the other updates.

Anyways, if someone could tell me how to grep or in some other way get the actual error messages when this happened so you guys can have a clearer view of what I'm experiencing, please tell me, Log Viewer doesn't show me anything like that, the best I can see is from dpkg.log but it only mentions what was installed, not what happened during installation.

---

### Post by MAFoElffen on 2021-08-17
That sometimes occurs when the folder structure of older kernels that were installed in the past doesn't exist anymore to rebuild your older kernels or they had gotten changed somehow...

Try this from a terminal session...
```
sudo purge-old-kernels
sudo apt autoremove
sudo apt update
sudo apt upgrade
```

---

### Post by slaytanicprion on 2021-08-17
Yeah, 5.4.-0.81 had been installed in a previous update, but I hadn't  rebooted since then, so I was still using 5.4.0-80. Maybe that's why it  went wrong. I'll try this. I had kernels older than .80 but I got rid of  them, cleanly, by actually following a post in here...we don't have the  luxury of ukuu anymore and somehow the Ubuntu Mate Software Updater  isn't like the plain Ubuntu I used from 11.04 to 12.04, there's no easy  gui where one can see the kernels that are new.

I thought one  could do updates without rebooting in Debian based Linux anyway and it  wouldn't cause conflicts with future incoming updates. What could have  caused "                     That sometimes occurs when the folder structure of older kernels  that were installed in the past doesn't exist anymore to rebuild your  older kernels or they had gotten changed somehow..." I haven't messed  with the kernel except by installing the newer ones from Software  Updater. I also got rid of the older ones with autoremove in a previous  session, I had rebooted since then.

I'll see what happens, I'm  not very comfortable messing around with initramfs and kernels. I'm a  moderately knowledgeable guy when it comes to Debian and Debian  subflavours, I might have known more in the past when after Ubuntu 12.04  I used Linux Mint 13.x to 17.3, when I was playing with the system a  lot in virtual machines to see what I could get away with without  completely destroying my system, like one does a lot with Synaptic or  command line when they don't know much and are learning Linux in general  like I was back 11 years ago.

But btw, there's no updates left to be done in Software Updater, so I don't know why I would upgrade, all that will do is install packages I don't want installed (don't need nvidia-prime, I have 2 AMD video adapters in CrossFire). When I look in Synaptic, it says that linux-firmware is the latest version, the one that gave me all those permission denied errors when Generating the grub menu. It looks like the package installed fine, but initram-fs update or mkinitramfs (I should have taken a screengrab, why would those update dialogs not be logged is beyond me).

---

### Post by MAFoElffen on 2021-08-17
Usually, you keep the current and last two kernels, by rule of thumb... Are your kernels in the GA or HWE range?

I have a script that checks the Ubuntu Repo's and returns the current HWE Kernel package version info for a Release Version... That way I can look at a machine and determine what series it's running on and if it is up to date.

---

### Post by slaytanicprion on 2021-08-17
I've been out of the loop for a while, what's the GA or HWE ranges? It's what I've done, I still have .0-79. I'm running on the second latest because I haven't rebooted since I installed 0-81.

I know it's running right now on 5.4.0-80-generic x86_64 by doing just uname -r. That's not really the issue here, I'm afraid to get a black busybox next time I reboot. I haven't had the chance to run 5.4.0-81 yet, I haven't rebooted when that update showed up last week.I did it without issue. 

The Generating...part at the end just threw me off, permission denied...from the software updater? sudo update-initramfs gives me permission denied. I know what kernel I'm running on, that's not really the issue right now, but thanks, I'll know who to ask when I could need such a script.

The linux-firmware package seems to have been installed successfully, but from the little I could find, I'm in trouble if something with such a high priority as the system's own software updater gets denied permissions.

I'll run Boot-Repair, that always worked with me back when I knew I was doomed to losing a perfectly fine (otherwise) install. I got it installed right here too, don't just have it on an old DVD, and even then that Boot-Repair OS which is just Lubuntu with a bunch of repair/tech tools might be a bit old now, unless the whole thing hasn't changed much since 2017. I stopped using any distros for a while when I got mad at the newest kernels Linux Mint 17.3 was forcing me to install, which a dozen kernels later, the proprietary AMD video drivers didn't work anymore.

---

### Post by MAFoElffen on 2021-08-18
If you are running Kernel 5.4.x, then you are running GA, without the Hardware Enablement stack (HWE). HWE is actually more than just the kernel, but adds more abilities for graphics and other hardware for newer machines, and machines with "abilities".

The main differences in the Kernel series between the two, is that the GA Kernels keep to a limited range throughout the LTS lifespan. The relase will just say 20.04 (generally). The HWE series kernels are newer, for instance, for 20.0.4.2 are currently in the 5.11.x range.

So you are using GA Kernels.

So wait a minute... You say you have a new kernel installed and have this error afterwards? Meaning it started after that... And you have yet to reboot to use the newer?

That does change things... Because if the toolset got changed, besides the kernel, then the error might just be because things are out of since with other updates that occurred with the toolset.

You can reboot, an if there are errors, then bring up the Grub Menu, to select an earlier kernel.

---

### Post by slaytanicprion on 2021-08-25
I haven't rebooted yet, but will likely do so soon, as I am removing an old useless 100/10 ethernet adapter from my main PC and replacing it with an eSATA-III adapter (I got the cable, I didn't take a chance and just bought a package with all sorts of cords and wires for cheap on ebay).

So, now I have more updates accumulating...I shouldn't do them right? Not until I have rebooted in the latest kernel and see what's what? Because whatever changes linux-firmware's update did to the kernels I have installed (last 3 ones), they didn't work as you all saw, first time ever I saw an administrative task get a permission denied response during initramfs-update after all updates have been installed.

I don't fancy reinstalling everything, I was getting close to where everything I want is installed and every personal quirks and security hardening are done. Hence my apprehension regarding rebooting at all. Can I get confirmation that this isn't a now broken install? Shouldn't have updated while I had a new kernel hanging that I didn't reboot in, it was never an issue before when updates showed up, but I guess linux-firmware isn't exactly a vanilla update...

Any words of wisdom appreciated at this point! :neutral:

---

### Post by not-published on 2021-08-25
go into the place where package info and trigger scripts are stored (sorry i know only the debian old locations for these)

read the trigger script

mkinitramfs is an old tool that may not be getting attention

however:  POST THE SCRIPT

it may not be permissions that are the problem.  you could have ... missing /dev/foo files that mkinitramfs is asking for that aren't present?  you could have MOUNT refusing to use a ramfs (of some compression type) if you haven't first loaded the kernel module that supports cramfs (or some newer type)

it could be ubuntu is using CPIO or something else and "abandoned" initramfs or not - that I can't tell you

i can say:  you have the script on your HD, it shows the script line arguments to mkiniramfs , so find it and post it so we know where to begin searching for problems

---

### Post by slaytanicprion on 2021-08-25
[HR][/HR]I have the Log File Viewer that comes with Ubuntu MATE, but there's  nothing that shows those errors, I searched all the files and that part  of the update is not kept anywhere. I only see the new packages that  have been installed in the dpkg logs, it's as close as it gets, I can't  even do sudo initramfs-update it also give me permission denied. Is  there a log file that simply shows you the same thing one sees in the  Software Installer when one sees the black terminal box. I should have  made a screengrab, I know. If so, I will not walk but run and find it  and copy/paste it here. The thing I pasted up there isn't exactly what I got, it's something I found elsewhere that looked the most like what I experienced, I had much less errors, only the following part showed up wrong, when it started this process for the three kernels I have installed, including 5.4.0-81 which I had not even tried yet. I couldn't find anything resembling my issue exactly..which is strange, I've found much more obscure stuff by pasting log parts I didn't understand in search engines before when I had issues in the past.
Processing triggers for initramfs-tools ...
update-initramfs: Generating (paraphrased) for 5.4.0-81...... permission denied
update-initramfs: ^^^^^^^^^^^^^^^^^^ 5.4.0-80..... permission denied

It tried again a few times then gave up and I don't recall anything alarming at the end like Segmentation fault or such. After I'm told if there is a way to find the logs that show me exactly what I saw in my last update process, I will do some of the things I was recommended here. I'm afraid I'll have to use Boot-Repair if I can't reboot in a newer kernel eventually. It's not like Windows where the system will freeze eventually sometimes heh.

---

### Post by not-published on 2021-08-25
[https://launchpad.net/ubuntu/+source/initramfs-tools/0.136ubuntu6](https://launchpad.net/ubuntu/+source/initramfs-tools/0.136ubuntu6)

ok.  I traced some of it.

/etc/initramfs-tools/scripts/init-premount/   IS EMPTY on default install

LINE 329

# umask 0022
# export PATH='/usr/bin:/sbin:/bin'
(if DEST dir exists)

DESTDIR="$(mktemp -d "${TMPDIR:-/var/tmp}/mkinitramfs_XXXXXX")" || exit 1

cp -p "/usr/share/initramfs-tools/scripts/${b}" "${DESTDIR}/scripts/$(dirname "${b}")/"

the installer is running  update-initramfs (which is in the package for you to see/read plain text), which then runs mkinitramfs.

FILE /usr/share/initramfs-tools/scripts/madm  does not exist, default install on my PC.  It could also be that  permissions on that folder are wrong OR permissions were dropped as well as the file is missing.  unfortunately it works on my PC so i can't tell you why your permission would be denied.

[U]DID YOU:  try running this a "root user", meaning without using sudo ?  If so, does it work ?

Also:  did you realize Debian then Ubuntu use ALLOT of shell FILE duplicate FD re-directions.  It means if you run it interactive and shouldn't it won't work.  It means if it is to be run non-interactive and shouldn't it won't work.  It means you shell re-direction mechanism can't be "broken" ... ie, /dev/stdin  /dev/stdout  must be proper character files and shell redirections should work.  You should only run the (update) exactly in the manner that UBUNTU prescribes it be run using the same shell (probably bash).  You should have NO active redirections when you do it.  I mention it because the scripts involved definitely do use multiple re-directions.  If redirections go wrong:  ubuntu or debian does unpredictable hard to trace things.  So be sure to use a "clean shell" and run it as prescribed in the official howto.[/U]

Did you intsall developer tools?  Did you install all the raid packages that you depend on that add madm to the init-tools scripts ?  Sometimes things like  "mkinitramfs" are not complete unless developer tools haven't been installed or specific packages are installed.
>  update-initramfs: Generating /boot/initrd.img-2.6.32-21-generic

my problem here is I cannot find the string "Generating ... generic" anywhere so I'm not completely SURE
that the trigger script or some other didn't interfere

---

### Post by slaytanicprion on 2021-08-31
That's a highly technical post for me here. I can answer a few questions though.

> "_DID YOU:  try running this a "root user", meaning without using sudo ?  If so, does it work ?"_
I  haven't used su to change the root user password, I don't know what it  is, I used to change it due to some quirks eons ago, but not now. I just  simply used the GUI Software Updater, which doesn't ask for your  password unlike say old school Synaptic, it's just like doing sudo apt  update && sudo apt upgrade, except I don't do it there because  strangely I am offered one extra update there I do not need, for nvidia  video adapters, I have 2 AMD graphic cards so I do the updates through  the Software Updater. I assume it does its thing at an elevated level. I  successfully updated this OS before and initramfs mkinitramfs didn't  have this problem. I cannot do it again, yes I have now new updates but I  don't want to do them and cause more issues (not likely, but I'm going  to have to run Boot-Repair before rebooting, I thought about previous  much more serious issues I had in the past and Boot-Repair cleared  everything up).

What is a clean shell again? I might have known  that before when I was learning linux hardcore and building debian  builts from scratch for fun. I remember when I used other Distros there  was a Terminal and an Administrator Terminal...but they're the same  thing if one decides to open the regular terminal with admin rights  isn't it?

Developer tools such as say libx265-dev? If you're  talking about something else, I'd like to know. Of course for many  programs I've had to install python of many versions etc.

I'm  going to do a Boot-Repair sometime this week, see what happens. But I'm  not liking Ubuntu-Mate's Software Installer in 20.04.x (it was different  in 18.04), never saw the official software updating gui of a distro  have issues like this. I'll tell all what happens if I could reboot fine  in 5.4.0-81. Thankfully I got more than one desktop or laptop, but the  one ubuntu mate is on is my most powerful and made to be relevant for a  long time desktop with pieces I chose myself.

---

### Post by slaytanicprion on 2021-09-08
To anyone who cares to see what happened with those permission denied initramfs after a significant update (linux-firmware) where it got permission denied from the distro's (in this case Software Updater, which doesn't ask me for my pw), but where I successfully installed and had initramfs/mkinitramfs do their job just fine after using it...I'll be doing what I haven't done since I started this thread, reboot, after doing Boot-Repair just to be sure, it doesn't break anything if there's nothing to break, at least the way I always did it. The fact the package itself installed fine....I don't have too much to lose. I got the little data on the OS partition I wanted to keep backed up so it wouldn't be the end of the world if i had to reinstall 20.04.2...would just be really annoying.

---

### Post by slaytanicprion on 2021-09-22
Alright, I was up to 90+ needed updates so I decided to reboot. I have screengrabs of the same exact thing happening, so you all can finally see exactly what is happening with initramfs and mkinitramfs and the kernels after doing important updates, mostly kernel updates it looks like, I went from 5.4.0-81-generic to 5.4.0-86-generic (uname -r output).
The first time it happened it told me to change some file's setting regarding initramfs and change a line's value from "yes" from "no". Now a message I see when booting after the initial Ubuntu Mate logo screen, I get for a few seconds a line about this very same subject showing up, nothing else, then the login portal shows up and everything works as it should....a bit poorly at times, but the hard drive it is on needs replacement, it's not entirely fubar, but has many bad blocks, I don't keep anything important on the OS partition so it's no issue. I'll show you happens with those permission denied kernel related initramfs/mkinitramfs messages when updating that I get which do not get logged in anywhere, so I had to reboot and do the updates and reboot again and see what happens after unfortunately seeing those same semi-worrying update errors (that do not cause any packages to be fail to install and be installed corrupted.

[URL="https://imgbox.com/V1zIgThV"][IMG]https://thumbs2.imgbox.com/39/80/V1zIgThV_t.png[/IMG]
[/URL][[IMG]https://thumbs2.imgbox.com/94/d0/GWwLwGgq_t.png[/IMG]]("https://imgbox.com/GWwLwGgq")
 
[[IMG]https://thumbs2.imgbox.com/40/e3/pYQB2RCp_t.png[/IMG]](https://imgbox.com/pYQB2RCp)

[[IMG]https://thumbs2.imgbox.com/47/32/qFPozxUJ_t.png[/IMG]](https://imgbox.com/qFPozxUJ)
^
In this one last screengrab, I noticed with Synaptic that there were still important updates not being made by Ubuntu Mate's Software Installer....(which, I don't know if it's me...kind of sucks compared to UM 18.04 LTS), and I got the same treatment. But new kernels get installed fine, there's only one thing you'd need to see, what I was told the first time something like this happened, to edit a file related to initramfs-update to yes from no; after UM 20.04.2 loads and in between the logo and the login screen, I get a black screen with one line saying something about the same thing, saying it is set to no. This is kind of beyond what I ever encountered here, and I saw some weird stuff before I managed to fix myself. But now I got what I should have had when I made this thread, screengrabs of the incidents, too bad I don't have the original one where it kept trying and had a kind of CLI message telling me I can always change that setting to yes in some file related to mkinitramfs/initramfs. I shouldn't be told permission denied when doing sudo initramfs-update, that's for sure.

Thanks to anyone who figures this out in advance!

---

### Post by slaytanicprion on 2021-09-23
I get the board what it truly needs to see and nobody has an idea at all? I agree, it's a weird one, hence me making a thread, it's very difficult to find examples on search engines of what is going on here, especially when I didn't have the full wording of the error messages. Please help if you can, now that I brought you the stuff that doesn't get logged but that causes an issue that might be invisible to me except at boot where I just get that message I cannot take a screengrab of. But otherwise I brought everything I should have pressed Print on the keyboard when I first had this happen before making the thread.

---

