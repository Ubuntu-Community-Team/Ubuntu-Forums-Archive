---
title: "I upgraded, and now I have this error..."
date: 2012-03-24
forum: Installation &amp; Upgrades
---

### Post by mörgæs on 2012-03-24
Ubuntu offers to upgrade to the next release by the push of a button. It is a convenient way of upgrading but it is also a huge process and many steps can fail, especially if the system was not stable from the beginning.


This guide is for you, who have tried the upgrade without luck. A lot of different problems can arise from a bad upgrade, for example trouble with the screen card, a slow system, network problems, problems with mice and keyboard or a system which simply does not boot.

A failed upgrade sometimes leads to wrong conclusions like 'The new version of Buntu has bugs' or 'The new version of Buntu does not work with my hardware'. Don't believe that before you have done more testing, most often the upgrade process itself is to blame. 

Whether or not an upgrade is generally safe compared to a clean install is not the topic. If you are reading this you probably have trouble with an upgrade and it is not relevant to know how often it works on other machines.

The guide applies to the entire Ubuntu family (Ubuntu, Lubuntu, Xubuntu, Kubuntu...), in short 'Buntu'. It is intended to be a low-tech step-by-step solution suitable for everyone. It does not solve all possible problems, but hopefully it serves as a first attempt. The process is:
 

** 1 - How does the new version of Buntu work in a live boot?**

Best is to try the new version in a live boot before installing/upgrading but if the damage is done and you are sitting in a failed upgrade it's still an important test. A live boot does not change anything on the hard drive unless one decides to do so actively so there's no reason not to do it.

If the computer is newer than around 2004 it can boot from a USB memory stick, else you need to boot from DVD. In both cases it might be necessary to set the boot order in BIOS. 

Buntu has a built-in USB creator and if you want to create the USB stick using Windows [Unetbootin]("http://unetbootin.sourceforge.net/") is recommended. Best is to download the ISO to the hard drive before running Unetbootin. If a present Buntu install is used then [Mkusb]("https://help.ubuntu.com/community/mkusb") is a good tool.

Burning a DVD should be done with the slowest speed available. Some reports indicate that write-once DVD's work better than rewritable ones. Should the boot fail, test the DVD itself from the boot menu or try booting another machine with the DVD. 

Remember that the ISO is one big packaged file and not the installation program itself. Hence one needs to choose 'create DVD from image' or similar before burning, not transfer the ISO file itself to the DVD.


More on booting from USB, including how to get rid of the annoying U3 software found on some USB sticks:
[http://psychocats.net/ubuntu/usb](http://psychocats.net/ubuntu/usb)
In Buntu, U3 can be removed using u3-tool found in the repositories.


Sometimes boot options (=kernel parameters) are needed in order to get a particular version running: 
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If that does not work:


**2 - Does the machine work with other versions of Buntu?**

There are always more than one supported release of your Buntu version. They could differ regarding hardware support so don't take for granted that the newest is always best. If your first pick does not behave try some of the other releases. Never install an unsupported release, though.
[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Version_timeline)
Remember that LTS is three years for X/L/Kubuntu and not five as for Ubuntu. 

The fastest way of getting an ISO is through a torrent, but you can also download them from here:
[https://launchpad.net/ubuntu/+cdmirrors](https://launchpad.net/ubuntu/+cdmirrors) or from the drop-down lists at the orange menu bar of Ubuntuforums.

Another - and often better - solution is trying one of the other members of the family:
[Xubuntu]("http://www.xubuntu.org") [Lubuntu]("http://www.lubuntu.me") [Kubuntu]("http://www.kubuntu.org/feature-tour") [Ubuntu]("http://www.ubuntu.com/")

-or even better: Try another distro like [Debian]("https://www.debian.org/").


In most cases there are workarounds for the missing hardware support, first of all the boot options mentioned above, but that is outside the scope of this guide. As a first step, ask our friend Google. 

Ubuntu used to be a light operative system, but the latest releases are heavy and put quite a demand on the graphics card. Here's a selection of advice for [old hardware]("http://ubuntuforums.org/showthread.php?t=2130640"). 

Some people skip this point and cling to Ubuntu in stead of the other Buntus demanding it to work, no matter what, simply because it is perceived as the 'real' Buntu. This means asking for problems. Don't make up your mind before you know the options.

If that does not work:
 

**3 - Is there a hardware problem on the machine?**

Bad memory blocks can give a lot of strange symptoms. When booting a live Buntu one gets the option of testing the memory. Let the test run for an hour or more and see what comes up.

If the test indicates errors best is to take out the RAM sticks one by one and repeat the test to isolate the error. Beware of static electricity when doing this.


Problems with keyboard and / or mice freezing are sometimes related to the BIOS. Check that you are using the newest BIOS release.


If you have the slightest doubt of the conditions of the hard drive(s) it's a good idea to erase everything with Killdisk before installing.
[http://www.killdisk.com/](http://www.killdisk.com/)

Just burn the Killdisk ISO to a CD (like with Buntu) and boot from it. 

When you are adding a used disk to the system, you should always clean it first, especially if it has been used in RAID.

If Killdisk does not run it is likely that the hard drive has physical errors and should not be used.


If that does not work:


** 4 - Ask the forum**

If the machine still does not boot a live Buntu it is time for posting a question in the relevant forum. Remember to write everything you know of the hardware and describe thoroughly the attempts you have done. You could also try a live boot of Knoppix, Puppy or other Linux distros for comparison.

If you are posting for the first time, take a look at this:
[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)



[SIZE=3]**Assuming that a live boot works now:**[/SIZE]
After these steps we know that the desired version of Buntu works on the hardware in question when booted in a live environment but the attempted upgrade did not. This gives us two options: Trying to fix the problem(s) or installing a new Buntu from scratch.

It is not possible to give advice on solving specific problems in this general guide. However, if one decides to do a clean install these are the steps:


** 5 - Back up important files**

The /home directory contains user files. They must be copied to a safe location, for example a USB drive.

/home also contains hidden configuration files and directories, indicated by a name beginning with a . (dot). Also these should be copied to the backup drive. With control + h, most file managers will show hidden files.

In addition to this it is wise to back up /etc/X11/xorg.conf, if the file is present. If you are doing web development you probably also have important files in /var/www.

Note: If /home sits on its own partition it is strictly speaking not necessary to back up any of its files since it is possible to delete only the other partitions and keep /home. Nevertheless, a backup is always a good precaution against Murphys Law.

If you can, best is to physically remove the backup drive from the system before proceeding.

If the installed system is unstable or simply FUBAR the back up can be done in a live boot. 


**6 - Create space for the new installation**

If you don't want to keep anything from the hard drive just skip to the next step and let Buntu wipe the entire drive during installation.

If the machine has one or more operative systems next to Buntu (for example Windows or Mac OS) and you want to keep it/them, boot the live CD again. Open the program Gparted and delete only the Buntu partitions.

If you have a separate /home partition and want to keep it as described above, take care when deleting!
 

**7 - Installation**

Remove all unnecessary USB devices before installing but keep the internet cable attached.

Boot with the Buntu version of your choice and follow the instructions on screen. If a question does not make sense to you just follow the defaults.

If you have a separate /home partition check that you have not selected it to be formatted during install.

During install Buntu offers to add closed-source drivers automatically. Normally this is convenient but if you encounter unexplainable problems try an install without this option.


**8 - User files**

Now the new system is ready for use, and it is time to copy the user files (documents, music, film,...) back to the /home/<username> location. Keep the config files on the backup drive but don't use them unless you are absolutely sure what you are doing. 

Beware that some program pollute /home with a lot of (often hidden) garbage files which do not serve any purpose and only take up space. Because of this I recommend to copy only select files into the new /home and not the entire folder.


 
Now you should have a working installation. I hope you also had fun in the process and learned something.
 

Happy hacking
Mörgæs





[COLOR=Red]**Well, I get your point, but I have installed so many applications on my system that a clean install is basically out of the question**.[/COLOR]

This goes around a lot in the fora. I believe that the wording ought to be "I have installed so many applications on my system that an online upgrade is basically out of the question". Here is why:


**A)** The more modified a system is, the more you can assume that an upgrade of this particular system has not been tested by the developers. 

One of the blessings of free and open source software is the abundance of available applications. By all means give them a test, but remember that this moves your system further towards one-of-a-kind.

If one of these applications does not run in the new Buntu release or if the upgrade of this particular application has not been thoroughly tested the whole process could fail leaving the system in a neither-nor state.

A customisation does not need to be very exotic to disturb the upgrade. Changing drivers for the graphics card or adding a personal package archive to the Software Sources might be enough.


**B)** There can be many good reasons for abandoning an old application and switching to something different. 

Default applications are not switched 'just because' in Buntu. Before changing apps a long debate is going on in the community and all arguments pro et contra have been considered. In stead of complaining that a particular app is no longer installed by default it might be worthwhile to give the successor a chance to prove its worth. 


**C)** Are all your applications actually needed or are they just there because you installed them once and forgot about them? For people like me who end up with a lot of unneeded applications on the system over time ('they might come in handy some day' - but seldom do), it is actually good to begin from scratch and actively select the applications rather than bringing them along to another version. If you need a list to remember what was installed in your old system it is a sure sign that you had too much.




If you in spite of this want to keep exactly the same packages in the new Ubuntu installation there is an alternative to the online upgrade. Running the command

```
dpkg --get-selections > installed-software
```gives a text file with all installed packages on the system. If you run the command on the old system you will have the option of running 

```
sudo dpkg --set-selections < installed-software
sudo apt-get dselect-upgrade
```on the new system after a clean install and get the same selection of packages. Thanks to **bcscomp** for this suggestion.


If you want to make a complete back-up of both applications and settings before experimenting (and an online upgrade is indeed experimenting) here is some advice:
[http://ubuntuforums.org/showpost.php?p=9931677&postcount=4](http://ubuntuforums.org/showpost.php?p=9931677&postcount=4)




[COLOR=Red]**So... maybe I should have done a clean install, but before I flush the machine, is there one last thing I could try to get it running?**[/COLOR]

Yes, there are some:

1) Boot the machine (into recovery mode, if necessary) and run

```
sudo apt clean
sudo apt update
sudo apt dist-upgrade
```Read carefully the error messages, if any. The solution might be explained here.

If the problem is lack of space then ```
sudo apt autoremove
``` is worth trying.


2) Rebuild your /etc/apt/sources.list

Make a backup copy of the file mentioned above and build a new one using 
[http://repogen.simplylinux.ch/index.php](http://repogen.simplylinux.ch/index.php)

Select all branches, updates and third-party repositories that may have been on the system. After applying the new sources.list, run again the three apt-commands above.

Thanks to **artoonie** for this idea.

Enabling the "proposed" repository will give you access to more bug fixes but they are in an experimental stage. It could solve the problem but it could also create another one. Be careful here.


3) Boot into an older kernel.
In the boot proces you might see a list of available kernels. Try going through them step by step and test if one works. 

If the list does not appear by itself, repeatedly pressing left-shift early during boot will show it, provided you have the Grub 2 boot loader. If your initial install was Ubuntu 9.10 or later, you have Grub 2 - if it was older than 9.10, it is most definitely time for a reinstall.


4) If you can boot into a command prompt but not the graphical environment, you could try the command **startx**. 


5) Adding boot options as described earlier in this post is also worth trying.

---

### Post by YSK on 2012-04-28
I had just upgrade the new version of ubuntu and found that some of the usual.

1. Auto hide launcher could auto hide the launcher, but cannot show back after we point the mouse to the position we selected( neither left nor top left).

2. Some of my installed software gone and I need to reinstall them back.... 

3. Firefox history been cleared.

Please kindly consider at future patches or upgrades.

Best regards
YSK

---

### Post by user_linux08 on 2012-04-28
One element which was not addressed in more details, is the /home directory in its own partition, which is the way I have been doing since early versions of ubuntu.

In addition to the fact, personal data is more secured against unintended deletion (due to upgrades, etc.) 

I like to emphasis that, if you do go this path. it is paramount to make absolutely sure during the installation, to select the existing /home directory and let the system know, this is the /home directory, and not the default one. it is also important  NOT click the FORMAT box.

Hope it helps

---

### Post by jadtech on 2012-04-28
great guide  !! 

hope many will take time to check it out  before they upgrade :)

---

### Post by IPEX-731BA5DD06 on 2012-04-28
:popcorn:Great Guide, I can only add my own experiences.

1) Separate Home Partition - This should be MANDATORY .... Safe guarding data , simplicity etc.
            - Notes on this
                 a) Do select you home partition at INSTILLATION as you default /home partition.
                 b) DON'T select it to be formatted. (yes done that)
                 c) Separate partition for operating system, select / as root for that partition.
                 d) Pyscho cat has a selection of EXCELLENT tutorials on 
                          i) Creating a separate home partition UPON instillation.
                          ii) Creating a separate home partition AFTER installation.
                          iii) Various other tutorials of other topics.

2) Try to figure out why, what, where who when has gone wrong, don't :cry: and issue ultimatums of leaving Ubuntu to go back to windooze !!!!!1 (I say good riddance).

3) Search this forum and Internet search. ( I've found some solutions while searching other's), processor.nocst=1
 for P4 processor systems on linux 3.0.0-12 -> 17 solves the kernel panic issue and allows use of dual core processors.

4) Remember the software is free, the only cost is your time and effort (oh hardware if your too foolish, not yet but trying).

5) Try put back at least twice what you take out, if you find a solution to a hardware issue (HP laserjet 1300, use Guetenburg print setting, 4th on list) is an example of what I've found out playing with settings on my own. Cost 10 pages printed and 1 hr of time.

Foolish thing I've done ;

1) Creating a new user Name, and complain that Firefox loses bookmarks, installed programs are missing etc, even though using same separate home partition. IPEX-...doesn't equal ipex-... or brian for that matter.
2) formatting separate home partition, (Brain explosion that day)
3) Used usb 2.0 Connection for upgrade (OMF'n!!!! its sooo slow.....compared to CD)
4) Deleted ALL kernels and wondered why it wont' boot :redface:
5) Posted my errors here for all to SEEE!!!!!! :lolflag:

---

### Post by YSK on 2012-04-29
Indeed I just click on the upgrade on the software updater, not redownload and format install of it. my personal data is save. Just some of the program just needed to be install again. 

Thanks for any concern. 

BTW: Before this update(1204) the auto hide launcher function good but now new version become not functioning?

---

### Post by mörgæs on 2012-04-30
Thanks for all contributions. Please keep them coming.

I have now added more on the separate /home in the guide.

---

### Post by mörgæs on 2012-04-30
> **YSK said:**
>  
Before this update(1204) the auto hide launcher function good but now new version become not functioning?

[http://ubuntuforums.org/showthread.php?t=1965991](http://ubuntuforums.org/showthread.php?t=1965991)

---

### Post by Elmware on 2012-04-30
I just upgraded in Virtual Box and now it goes all weird.

---

### Post by zaentzpantz on 2012-05-02
After a complete Ubuntu 12.04 upgrade, bootup message says "your screen, graphics card and input device settings could not be detected properly".
Click on OK (the mouse cursor works) and I am asked for a login and then a password which then gives me a black screen with the command prompt.
Only 8 hours ago I had a working 11.10 operating system which worked for the past six months without many problems apart from the flaky applications. 
Now I only have good old Windows XP.
Ubuntu 11.04 worked sort of ok,
Ubuntu 11.10 the printer stopped working,
Ubuntu 12.04 the whole desktop has stopped working.
Reverting to earlier versions via the GRUB menu shows the same problem, only the command prompt, no graphics.
Far from upgrading, Ubuntu seems to be on a steady downward spiral over the past few releases. I have had to rely on XP more and more over the past year, it's far more robust and reliable. 
So I'm afraid it's goodbye Ubuntu and I will wipe the hard drive tomorrow. It's been interesting but I really need to do work with my computer, not tinker with it endlessly trying to get things to work.
Ubuntu will never be universally accepted until these reliability problems are solved.

---

### Post by mörgæs on 2012-05-02
If you want an easy (last) test you could try a live boot of X/Lubuntu 12.04 and see how stable it is. My guess is that you'll get a completely different experience.

---

### Post by patalicious on 2012-05-05
Hello, this is my first post so please feel free to call me a massive noob if this problem is screamingly obvious to fix. Lol.

Just upgraded to Ubuntu 12.4. It looks great but the dash cannot find anything.

I've tried searching for programs that I know are there by name yet dash finds nothing and shows me no shortcuts. The only apps I can launch are in the ones in the launcher.

The Software Centre works fine and I can see the apps in the installed apps section of the software centre but obviously I can't open them.

Many thanks in advance for your kind assistance.

---

### Post by mörgæs on 2012-05-06
If you are a noob, you have come to the right place. 

The idea behind the guide is not trying to bring a failed upgrade back to live, as I believe it is generally not worth the effort, but to encourage people to proceed systematically and get a working system in the shortest time possible. 

The only advice I can give is written in the first post. Getting into the habit of testing and reinstalling is a good investment. 

So, back to your problem... Step 1: How does it work in a live boot?

---

### Post by directhex on 2012-05-06
> **mörgæs said:**
> some Mono-based applications like Tomboy and F-spot were replaced with true open source alternatives. Let's hope we can put the old ones to rest.

I'd expect a forum moderator to understand what Open Source is.

---

### Post by aditya3098 on 2012-05-10
There is also the manual approach I used:

Change the sources to the next version i.e:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe

becomes:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe

Become root (sudo su) on tty1 (ctrl-alt-f1) . Then run the following commands multiple times in the same order until the all of them show that the distro is up to date and dpkg --configure -a has no output:

apt-get update
apt-get upgrade
dpkg --configure -a
apt-get dist-update
dpkg --configure -a

Finnaly reboot with:

reboot

and use the new distro

---

### Post by mörgæs on 2012-05-11
> **aditya3098 said:**
> There is also the manual approach I used:

Change the sources to the next version i.e:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) oneiric universe

becomes:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) precise universe

Become root (sudo su) on tty1 (ctrl-alt-f1) . Then run the following commands multiple times in the same order until the all of them show that the distro is up to date and dpkg --configure -a has no output:

apt-get update
apt-get upgrade
dpkg --configure -a
apt-get dist-update
dpkg --configure -a

Finnaly reboot with:

reboot

and use the new distro

It might work :-) and if it doesn't you know what to try in stead.

I recommend using sudo and not su:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aditya3098 on 2012-05-11
> **mörgæs said:**
> It might work :-) and if it doesn't you know what to try in stead.

I recommend using sudo and not su:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

In that case, use sudo -i

And yes, this IS for advanced users

---

### Post by ahso4271 on 2012-05-12
Never update things you're not sure about.

---

### Post by Hexxus on 2012-05-14
> **IPEX-731BA5DD06 said:**
> :popcorn:Great Guide, I can only add my own experiences.

1) Separate Home Partition - This should be MANDATORY .... Safe guarding data , simplicity etc.
            - Notes on this
                 a) Do select you home partition at INSTILLATION as you default /home partition.
                 b) DON'T select it to be formatted. (yes done that)
                 c) Separate partition for operating system, select / as root for that partition.
                 d) Pyscho cat has a selection of EXCELLENT tutorials on 
                          i) Creating a separate home partition UPON instillation.
                          ii) Creating a separate home partition AFTER installation.
                          iii) Various other tutorials of other topics.

2) Try to figure out why, what, where who when has gone wrong, don't :cry: and issue ultimatums of leaving Ubuntu to go back to windooze !!!!!1 (I say good riddance).

3) Search this forum and Internet search. ( I've found some solutions while searching other's), processor.nocst=1
 for P4 processor systems on linux 3.0.0-12 -> 17 solves the kernel panic issue and allows use of dual core processors.

4) Remember the software is free, the only cost is your time and effort (oh hardware if your too foolish, not yet but trying).

5) Try put back at least twice what you take out, if you find a solution to a hardware issue (HP laserjet 1300, use Guetenburg print setting, 4th on list) is an example of what I've found out playing with settings on my own. Cost 10 pages printed and 1 hr of time.

Foolish thing I've done ;

1) Creating a new user Name, and complain that Firefox loses bookmarks, installed programs are missing etc, even though using same separate home partition. IPEX-...doesn't equal ipex-... or brian for that matter.
2) formatting separate home partition, (Brain explosion that day)
3) Used usb 2.0 Connection for upgrade (OMF'n!!!! its sooo slow.....compared to CD)
4) Deleted ALL kernels and wondered why it wont' boot :redface:
5) Posted my errors here for all to SEEE!!!!!! :lolflag:
Hello there, I've searched for a little while looking for psycho cat's guide but I didn't see it.  You wouldn't have a linky handy by any chance would you?

Thanks! :)

---

### Post by StarGazer83 on 2012-05-15
Link: [http://psychocats.net/ubuntu/index.php]("http://psychocats.net/ubuntu/index.php")
many guides, always worked fine for me

---

### Post by dalbir on 2012-05-18
i upgraded to 12.04 from 11.10 
there was some problem while clearing the files and i didn't take notice of that.
the process was finished successfully.
now the ubuntu 12.04 is not working only the startpage appears and neither the keyboard or the mouse work when it starts?
i am dying to use the new ubuntu 12.04.
what should i do ?

---

### Post by chipchop on 2012-05-24
This will help somebody, I wish I had read what I am about to write before upgrading from 11.10 to 12.04...

The upgrade might fail right in the middle.  If you do decide to go with a fresh install of 12.04 make sure you are certain that you choose the proper drive to install it to.  Don't choose sda when you should be choosing sdb, for example.  Especially if sda has all of your family pictures that your wife has told you to backup several times, and you hadn't gotten around to it, and all of your music that you tirelessly ripped from the cds that are gathering dust in the attic.  
Upon realizing that you have just written over your pictures and music, you may want to log back into your previously working 11.10 only to find that gparted won't load, and testdisk is taking forever to analyze the 750GB disk, cross your fingers that the Ubuntu load didn't write over the files you want to recover.

Just don't be apathetic about the upgrade, it isn't a seamless as you would hope.  Be very careful and don't do stupid stuff. Oh boy, what a day!  Oh man, compiz just failed as I wrote this, oh please don't interrupt the testdisk, its at 50%!

---

### Post by elosier on 2012-05-30
> **dalbir said:**
> i upgraded to 12.04 from 11.10 
there was some problem while clearing the files and i didn't take notice of that.
the process was finished successfully.
now the ubuntu 12.04 is not working only the startpage appears and neither the keyboard or the mouse work when it starts?
i am dying to use the new ubuntu 12.04.
what should i do ?

I'm in a similar position as you are (I started the upgrade, came back a few times to fill in the blanks and and the end didn't take notice of errors and rebooted when asked to).  Now I got the start page (only the page with the background color and nothing else) and the keyboard/mouse don't work.

Have you found a solution?

---

### Post by pdvrosado on 2012-06-18
I've tried to install ubuntu 12.04 but the installation crashed every time it went to the phase when it turns on the webcam to take the user photo. I installed version 11 and all was going well, all worked out fine, even the webcam. Then I upgraded to 12.04 and the camera doesn't work. how do i solve this? I'm using a  Sony vaio VGN-FE31M.

Whe i use cheese, i only see a green screen and some distorted colours, i don't know how to make the webcam work.

---

### Post by mörgæs on 2012-06-18
You have posted the same question several times without getting an answer. This indicates that noone has an exact solution to offer, and I doubt that posting again changes this.

As 12.04 does not represent any major news compared to 11.10, my advice is to stay with 11.10 for as long as it is supported. When 12.10 is released and getting stable (say, two months after release) you could give this one a try, still having 11.10 as plan B.

---

### Post by pdvrosado on 2012-06-19
That's what i'm doing :/ cleaning up my pc to get a new fresh install of ubuntu 11 oneiric... are there any differences between 11 and 12? The unity and kernel and stuff is the same if we do the updates right? what are the differences? i can't find anything online about that

---

### Post by mörgæs on 2012-06-20
There are always lots of small changes, but nothing major. Best is if you try a live boot and judge for yourself.

---

### Post by pdvrosado on 2012-06-20
11 is cool. the monitor brightness now works (i could change the light on the screen on version 12) and the webcam is working fine. But there are some minor bugs with the unity bar, some icons disappear and appears a ghost app square, it's kind of weird. but it works pretty smoothly, even better than 12.04

---

### Post by AraiBob on 2012-06-24
1) My desktop pc's 22 inch Samsung monitor is not a 'laptop monitor?

I have a UPS on my pc, perhaps because it has a battery, the entire PC is considered a laptop?  Silly.   SIlverStone Fortress FT02 case, with 5 hard drives, etc does NOT make a laptop.

1) My sound card sometimes works, sometimes not.

My Asus Xonar D2 has worked wonderfully under 11.04 and 11.10. I used to get 5.1 sound (I saw another complain about this), but I turned it off and made it stereo for better sound. I do NOT play games on my PC.

I used to see an icon in the upper right of the screen for sound, all gone.

All worked just fine under 11.04 and 11.10. 12.04 is giving me more grief than the initial install.

Has the quality department taken a vacation?

---

### Post by Python Jedi on 2012-06-26
[COLOR=Silver][COLOR=Black]Solved[/COLOR][COLOR=Black]: NVIDIA Driver not enabled[/COLOR][I]
As could be expected, I upgraded from 11.10 to 12.04, but I was using Xubuntu 11.10, and now I only get a terminal login, and must manually start the XServer, severely limiting what I can do.  I thought it might have something to do with the fact that the upgrade was for Ubuntu, and it messed up the packages (Desktop environments don't play nice together in my experience), but even manually erasing the disk (backed up to 16GB flash drive first) and installing Xubuntu 12.04 fresh has this same problem.  Any suggestions?  I'd like to stay with Xubuntu, Unity is too Mac-like for my tastes.[/I][/COLOR]

[COLOR=Black]Deleted problematic user, saved home folder, then created a new one with the same name[/COLOR]
[COLOR=Silver]New Problem: I now boot to the normal login screen, except that when I attempt to login, it just blanks the screen for a moment, and then opens up the login screen again.  The guest account works okay, but not my main account, either through the button, or using "other" with the username and password.  I will attempt to create another user and login as that user.

More info on New issue: Creating another user makes everything work okay for that user, I'll see about mucking with the user settings somewhere to fix my main account.

[COLOR=Black]Now I don't have the panels, but I've fixed that problem before by starting the window manager in .bashrc.  I'll try it in .profile this time so it doesn't do that every time I open up a terminal emulator.[/COLOR]
[/COLOR]

---

### Post by ArbiterOfTruth on 2012-07-12
Hello all. I upgraded from 11.10 to 12.04 & now my wired internet keeps disconnecting & reconnecting.

I am dual booted with Win7 Ultimate & I do not get that problem in Windows. I decided to give the upgrade a try & everything went as normal just like my previous upgrades. When the upgrade was finished, I booted into Ubuntu & everything ran smoothly, for about two minutes. Then the internet disconnected (Wired Network disconnected - you are now offline). It stayed like that for about  3 seconds then reconnected (Wired Connection 1 - Connection Established). It stayed reconnected for 43 seconds, then disconnects for 3 seconds & the whole thing starts over until I go back to Windows.

I am hoping somebody else got this problem & solved it. I will also take the OP's advice & run a new version live first to test it out in the future.

Thanks in advance,

---

### Post by jkuzenka on 2012-09-06
Hello All,

I tried to upgrade from Ubuntu 10.04.4 LTS to 12.04.1 LTS.   Everything seemed to go great until the system rebooted and had the message "The disk drive for / is not ready yet or not present".  I waited for over an hour with no change.  I then attempted different manual steps to try to mount the drive, installed and used boot repair with Live CD 12.04.1 LTS, and some other command line options based on google searches and Ubuntu form searches without success.   I didn't want to waste anymore time so I just did a fresh install of 12.04.1 LTS and now everything now works as expected.  I will have to spend a little bit of time installing applications I had before the fresh install and my data is backed up to USB drive.

No luck on upgrade.  Fixed by fresh install.  Thankfully I had my important data backed up.

PC used Dell Dimension E510.

~ Josh

---

### Post by MUK3SH on 2012-09-07
You are developer, cant keep old files saved during upgrade ?? :(
all Important files, Lost :(

---

### Post by pixideps on 2012-09-07
> **jkuzenka said:**
> Hello All,

I tried to upgrade from Ubuntu 10.04.4 LTS to 12.04.1 LTS.   Everything seemed to go great until the system rebooted and had the message "The disk drive for / is not ready yet or not present".  I waited for over an hour with no change.  I then attempted different manual steps to try to mount the drive, installed and used boot repair with Live CD 12.04.1 LTS, and some other command line options based on google searches and Ubuntu form searches without success.   I didn't want to waste anymore time so I just did a fresh install of 12.04.1 LTS and now everything now works as expected.  I will have to spend a little bit of time installing applications I had before the fresh install and my data is backed up to USB drive.

No luck on upgrade.  Fixed by fresh install.  Thankfully I had my important data backed up.

PC used Dell Dimension E510.

~ Josh

The same problem here .... is there any chance to patch up such broken upgrade? Namely, I do not like idea to reinstall all the third party programs ... However if there is no other way ....
thanx in advance

---

### Post by jkuzenka on 2012-09-10
>  
Originally Posted by **pixideps**
The same problem here .... is there any chance to patch up such broken upgrade? Namely, I do not like idea to reinstall all the third party programs ... However if there is no other way ....
thanx in advance 

 
I am sorry to hear you had same issue that I had during the upgrade. I don't have any good news on this except that I did a fresh install of Ubuntu 12.04 LTS from Live CD, installed updates, and then everything worked as expected. I understand what you are saying as I also chose the upgrade path so I would not have to do many re-installs of the applications that don't come out of the box with Ubuntu 12.04 LTS. I don't have an alternative way around this. Maybe another Ubuntu 12.04 user that has experience this issue during an upgrade, fixed it, and has done it differently can respond to our posts.
 
~ Josh

---

### Post by YannBuntu on 2012-09-12
Hello

If any upgrade fails via the Update Manager, the first thing I recommend to do is:
1) boot on a Ubuntu CD, choose "Try Ubuntu", backup documents on an external disk (or DVDs)
2) fix the system files via this simple way: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)

---

### Post by jkuzenka on 2012-09-13
> Originally Posted by **YannBuntu**
Hello

If any upgrade fails via the Update Manager, the first thing I recommend to do is:
1) boot on a Ubuntu CD, choose "Try Ubuntu", backup documents on an external disk (or DVDs)
2) fix the system files via this simple way: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) 

I read the link you gave and this looks pretty easy.  I wasn't aware of this when I tried the Upgrade from 10.04 LTS to 12.04 LTS.  I will keep this in mind if I try to upgrade again to another Ubuntu release.

Thanks,

~Josh

---

### Post by katopippin on 2012-09-18
i upgraded, now have many problems very slow loading everything,do not like the new upgrade at all! how do i uninstall the new upgrade and go back to the one i had before the upgrade?

---

### Post by YannBuntu on 2012-09-18
> **katopippin said:**
> i upgraded, now have many problems very slow loading everything,do not like the new upgrade at all! how do i uninstall the new upgrade and go back to the one i had before the upgrade?

You can downgrade by:
- either reinstalling the old Ubuntu above the new one, this way: [https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation) , but this is NOT recommended as software settings may not be retro-compatible.
- or saving your documents, then reinstalling a "fresh" old version

I recommend a 3rd alternative: create a dualboot "old version" + "new version", so that you can use your old version while searching solutions for the problems you may have with the new version.

---

### Post by jcwinnie on 2012-09-30
I upgraded Ubuntu 12.04 LTS again this morning as I regular do. I have a dual system on this PC. Or had until Ubuntu upgraded this morning and wiped out my Lubuntu 12.04, which is what I used most often.

How do I get Lubuntu back with everything the way it was?

---

### Post by bogan on 2012-09-30
Hi!, **jcwinnie,**

Please Post details of what you actually experience when you try to boot, and what you have tried to solve things;

EG,. how far does it get?,
what do you see?
What response you get to keystrokes? - such as 'Crtl+Alt+F1',  'Crtl+Alt+Del', or 'Shift'[ the later during boot sequence].

If you get a grub menu: Have you tried:
Booting to recovery?
Editing the grubmenu script?, eg to put in 'nomodeset'

Or tried Booting from a LiveCD/USB?

Please also Post details of your setup: computer make and model, CPU, integrated Graphics?, GPU,video card, memory, and how Ubuntu/Lubuntu is installed, ie with 'wubi' or direct, and if dual with Windows.[ If the later, does it work??]

Also please Post the output of the following, if you can get to a terminal [ or tty]. ```
uname -ar
lspci -nnk | grep -iA3 VGA
/usr/lib/nux/unity_support_test -p
```Copy/Paste the command and output to a 'New Reply' edit box. highlight it and press the '#' icon in the toolbar at the top of the edit box.

Chao!,[B] bogan.
[/B]

---

### Post by jcwinnie on 2012-09-30
Stuff happens so quickly around here.

My dual Linux PC (Lubuntu and Ubuntu) is back to normal. Earlier today I tried running Ubuntu and it gave me Lubuntu. I upgraded 4 selections for boot loader. Now everything seems back to normal, i.e., Lubuntu starts from the default selection. It has the previous setup. Now I guess I go test Ubuntu and start the craziness all over again.

):P

---

### Post by bwanab on 2012-10-10
Upgraded my highly customized 10.04 to 12.04. This went mostly without a hitch. I had to tinker with pulseaudio (which I didn't use with 10.04), but otherwise no problems, except I'm seeing very sluggish movement of windows around the screen. This is a relatively old machine, but it has a 3D graphics card which I've verified is working by running a game (bzflag) that I know works poorly without 3D acceleration. In addition, I've done clean installs of 12.04 on two other machines (a high spec laptop and a low spec netbook) and I don't see this behavior on either of them. When I say sluggish, I mean that when I grab a screen and move it, it's like it's moving in molasses - I move the mouse and after a pause, the window slowly drifts over to where I've stopped. In 10.04, this same machine was able to run compiz on medium settings, so I don't think it's the hardware. I suspect it's a simple setting, but I need some clues as to where to look.

---

### Post by mörgæs on 2012-10-11
> **bwanab said:**
> This is a relatively old machine...

Please give a complete hardware description.

---

### Post by bwanab on 2012-10-14
Processor: AMD Athlon 64 3000+
Graphics: Nvidia GeForce FX5200/AGP/SSE2
Memory: 1G

Don't know if this helps:


bill@amddesktop:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce FX 5200/AGP/SSE2
OpenGL version string:  2.1.2 NVIDIA 173.14.35

Not software rendered:    yes
Not blacklisted:          no
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

One more data point: I logged into an xfce session for the first time since upgrading. I don't have this molasses problem at all. Screens move around as they should.

---

### Post by mörgæs on 2012-10-15
I have a Dell with the same screen card. Works fine with L/Xubuntu, as you have also seen yourself, but Ubuntu is too heavy.

---

### Post by bwanab on 2012-10-17
> **mörgæs said:**
> I have a Dell with the same screen card. Works fine with L/Xubuntu, as you have also seen yourself, but Ubuntu is too heavy.

Thanks. I upgraded to an NVidia 6200 and Unity works fine. I'm still mostly an XFCE guy, but my family prefers Gnome/Unity.

---

### Post by agualdino on 2012-10-22
I upgraded from 12.04 to 12.10 and now lost all the email tags in thunderbird. 
Anyone knows why or how to fix this?

---

### Post by zelemo on 2012-10-28
Hi

I've just upgraded from 12.04 to 12.10 and discovered a problem, which I solved myself after a couple of hours of scratching about - so I thought I'd post here in the hopes that someone else might find it useful.

On 12.04 (and several previous versions) I've had a /etc/fstab which does a few mounts to Windows and/or Samba servers using cifs (smbfs as was).

When I upgraded, I discovered on first boot that none of them worked.  When I tried to mount manually, I got an error saying something like "bad sector block or other possible error - please do "dmesg | tail" to find out more."

So, I did a dmesg | tail and discovered the following errors:-

[  432.864261] CIFS VFS: Connecting to DFS root not implemented yet
[  432.864388] CIFS VFS: cifs_mount failed w/return code = -22

I'm going to cut a long story short.  What happened was that, for some reason, the upgrade to 12.10 removed the old version of cifs-utils and didn't replace it with a new one.

I just did

sudo apt-get install cifs-utils

...and it all came back to life again.

---

### Post by MickM on 2012-11-03
I upgraded a week ago from 12.04 to 12.10 and all is fine. However, I tried to check for any software updater but I receive the following error.
W:Failed to fetch [http://ppa.launchpad.net/upubuntu-com/office/ubuntu/dists/quantal/main/source/Sources](http://ppa.launchpad.net/upubuntu-com/office/ubuntu/dists/quantal/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/upubuntu-com/office/ubuntu/dists/quantal/main/binary-i386/Packages](http://ppa.launchpad.net/upubuntu-com/office/ubuntu/dists/quantal/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.
I will place in another thread.

---

### Post by hollywoodpete on 2012-11-03
> **zelemo said:**
> Hi

I've just upgraded from 12.04 to 12.10 and discovered a problem, which I solved myself after a couple of hours of scratching about - so I thought I'd post here in the hopes that someone else might find it useful.

On 12.04 (and several previous versions) I've had a /etc/fstab which does a few mounts to Windows and/or Samba servers using cifs (smbfs as was).

When I upgraded, I discovered on first boot that none of them worked.  When I tried to mount manually, I got an error saying something like "bad sector block or other possible error - please do "dmesg | tail" to find out more."

So, I did a dmesg | tail and discovered the following errors:-

[  432.864261] CIFS VFS: Connecting to DFS root not implemented yet
[  432.864388] CIFS VFS: cifs_mount failed w/return code = -22

I'm going to cut a long story short.  What happened was that, for some reason, the upgrade to 12.10 removed the old version of cifs-utils and didn't replace it with a new one.

I just did

sudo apt-get install cifs-utils

...and it all came back to life again.

You are my HERO

---

### Post by turboscrew on 2012-11-06
When I updated my oneiric (to Precise), the update messed up the linux boot altogether.

I have Vista dual boot with Vista primary boot loader.
This time the update left the MBR alone, but grub gave the menu, and every boot option ended up with "partition not found".

The first time I used alternate install and installed Grub in the beginning of the root partition. Then the update (Lucid -> Oneiric) wrote Grub2 onto the MBR and messed up the Vista boot too. The Oneiric didn't boot either, so I fixed the Vista boot and installed Oneiric from a DVD.

Why does Ubuntu push upgrades if they are NOT recommended?
Why doesn't upgrade respect the boot loader installation of the older system? (If Grub is installed, not Grub2, why does it write upgrade to Grub2 without asking?)

---

### Post by YannBuntu on 2012-11-07
@turboscrew: you should create bug reports on Launchpad.net  [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by turboscrew on 2012-11-07
> **turboscrew said:**
> When I updated my oneiric (to Precise), the update messed up the linux boot altogether.

I have Vista dual boot with Vista primary boot loader.
This time the update left the MBR alone, but grub gave the menu, and every boot option ended up with "partition not found".

The first time I used alternate install and installed Grub in the beginning of the root partition. Then the update (Lucid -> Oneiric) wrote Grub2 onto the MBR and messed up the Vista boot too. The Oneiric didn't boot either, so I fixed the Vista boot and installed Oneiric from a DVD.

Why does Ubuntu push upgrades if they are NOT recommended?
Why doesn't upgrade respect the boot loader installation of the older system? (If Grub is installed, not Grub2, why does it write upgrade to Grub2 without asking?)

Aha: I check with the EasyBCD and the upgrading only messed up the linux entry in the BCD. I deleted the old entry (it pointed into the Vista partition) and created a new entry.

Ubuntu booted fine! :-)

---

### Post by neiljmac on 2012-11-14
Actually not an error as such, but a number of apps are consistently crashing after my upgrade and I am not yet sure why. Additionally and annoyingly, a number of apps don't seem to want to re-install properly either.
Netbeans crashes often, Aptana (won't actually start from a fresh copy). Perhaps a Java problem?
Unity keeps losing title bars and window decoration, gnome-shell keeps falling over.
A very odd one - LibreOffice Writer and Math don't appear to be installed when running Gnome or Unity but do appear when running Xfce (Xubuntu).  I think that might be one for the LibreOffice folk.
I updated Crossover Office, yet the old version still loads up.  I couldn't see that issue reported on Codeweavers.

Secondlife won't run at all - some sort of LibGL error.

My recommendation to anyone thinking of upgrading from a heavily modded 12.04, is DON'T!!  Do a full backup then a clean install. It really is the only way to have a good chance of having a production-worthy (desktop) system afterwards.

If I had some spare cash, I would update my hardware from this 5 year old Dell Studio 1535 but I don't.

I have a lot of work to do tomorrow and unfortunately I am going to have use that OS made in Redmond in order to do it.  The very thought of that makes my skin crawl!

Peace.

---

### Post by mörgæs on 2012-11-15
If we are talking of this one
[http://www.cnet.com/laptops/dell-studio-s1535-125b/4507-3121_7-33088555.html](http://www.cnet.com/laptops/dell-studio-s1535-125b/4507-3121_7-33088555.html)
I don't think you need any more investments. Forget Ubuntu and go for a fresh install of Xubuntu 12.10. 

Since 12.10 is still young it is a good idea to enable the *proposed* repository.

---

### Post by neiljmac on 2012-11-15
Hi Mörgæs
Thanks for the advice.  I will give that a go.
It isn't that notebook but the chipset is the same, I believe, so the SecondLife issue may be helped by that.
I'll drop a quick response here once I have put Xubuntu 12.10 on here.

All the best

Neil.

---

### Post by ionFreeman on 2012-11-17
My problem is fixed, but I thought I'd share my story.

I've stayed on 12.04 LTS Precise Pangolin, but let the update manager do its thing after 12.10 Quantal Quetzal came out.

I lost the use of my touchpad and wireless antenna. After a week of living off my smartphone, I plugged in an Ethernet cable and ran
sudo apt-get update

It told me that I had to run 
sudo dpgk --configure -a

which I did. After that, it failed to acknowledge the battery. My little charging-time-left display went to '(not found)' or something similar, and in short order the laptop suspended. I brought it back out of suspension, ran
sudo shutdown -h now

and let it charge for a while. Now it works great. Battery's charging, I have wireless and I can point and click. I guess if I'd gone ahead and run apt-get without an internet connection, it would probably have worked out as well.

I'm using a 2007 ZaReason BigLap which came originally with 7.04 Feisty Fawn.

---

### Post by zvacet on 2012-11-22
I could be wrong,but I think you will get more precise results about installed software with 

```
aptitude --display-format '%p' search '?installed!?automatic' > ~/my-packages

```

---

### Post by annie987 on 2013-01-14
> [COLOR=Red]**So... maybe I should have done a clean install, but  before I flush the machine, is there one last thing I could try to get  it running?**[/COLOR]

<snip>

3) Boot into an older kernel.
In the boot proces you might see a list of available kernels. Try going through them step by step and test if one works. 

If the list does not appear by itself, pressing left-shift early in the  boot will show it, provided you have the Grub 2 boot loader. If your  initial install was Ubuntu 9.10 or later, you have Grub 2 - if it was  older than 9.10, it is most definitely time for a reinstall.
After an update my server 'failed to boot default or fallback entries' so I went to the previous linux versions and booted 3.2.0-35-generic (3.2.0-36-generic being the one that failed). How do I get rid of 3.2.0-36-generic and make 3.2.0-35-generic the default?  Maybe then I'll can workout what went wrong.

Thanks
Annie

$ uname -a
Linux bioinf5 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"

---

### Post by mörgæs on 2013-01-15
[http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)

Remember to give newer kernels a chance, when they are released.

---

### Post by rishabh sachan on 2013-01-18
no problem bro 1st u uninstall your ubuntu for ur system then use original CD of ur ubuntu and then install it and while installng pls dont be off your system

---

### Post by Elfy on 2013-01-18
> **rishabh sachan said:**
> no problem bro 1st u uninstall your ubuntu for ur system then use original CD of ur ubuntu and then install it and while installng pls dont be off your system

> Do not shorten your words to acronyms or abbreviations or use URL-shortening services, as is often done when texting or in a Twitter-style update. It is very difficult to read and understand and you are not limited to a small number of characters.

This isn't texting or twitter - please use proper words. 

Some of us grew up in the old world ;)

---

### Post by azharumar on 2013-01-22
> **Elmware said:**
> I just upgraded in Virtual Box and now it goes all weird.
brother elmware,

I have the same problem. Did you find a solution.

I was a windows user till last week, and suddenly i felt like changing to Linux. Lunux sucks big time. Its so complicated. even the installations etc. The upgrade took me an entire night to have all the things on the desktop gone. Windows was much better....

---

### Post by mörgæs on 2013-01-24
If you open a new thread and post the exact problem there is a good chance that someone can help you. It's difficult to respond to"Something does not work".

---

### Post by bogan on 2013-01-24
Hi!, **moerges,**

Your Link to: "About problems due to upgrading" leads back to itself. Not, I assume, what you intended,

Chao!, **bogan.**

---

### Post by mörgæs on 2013-01-25
Yes, it's in the signature, so it comes by default and I have to remember to remove them each time (in this thread). 

Thanks, I shall take a look at it.

---

### Post by bogan on 2013-01-25
> **mörgæs said:**
> Yes, it's in the signature, so it comes by default and I have to remember to remove them each time (in this thread). 

Thanks, I shall take a look at it.How about if you put  " _***Signature: ***_" in front & before the link.

Chao!, bogan.

---

### Post by bixiobix on 2013-01-31
thanks for this great guide, I only wish I had read it before trying to upgrade.
Now that the system is not responding should I just post a new thread with details on what happened? I'm new here and not sure what's best. I've searched previous posts and run an advanced search on the topic with no luck. From what I understand in your post all suggestions are to be tried while one's computer still switches on, except for the last 3 or 4 attempts.
Thanks
bix

---

### Post by mörgæs on 2013-02-01
You're welcome. If you find something which needs better explanation please let me know.


Regarding your problem: It's hard to give advice based upon 'something is not working'. 

Best is you begin with a complete hardware description and run the first three tests. Please post the results here.

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by spideryada on 2013-04-28
I thought I would share this tip.

When doing a fresh install all of your software will have to be reinstalled. First I save all of the hidden configuration files from my home directory. Then I create a bash file to reload my software after the fresh install.

apt-get -y install filezilla
apt-get -y install glabels
apt-get -y install dosbox
apt-get -y install stellarium
apt-get -y install gparted
apt-get -y install thunderbird
exit

Make an apt-get for all the software that you usually run.

Save as loadapps.sh

After a fresh install open a terminal and in the directory of your bash file, run:

sudo bash loadapps.sh

This will install all of your software. Takes some time if you have a long list.

After this finishes copy all your old hidden files for your software from your old home directory to your new home directory; .thunderbird, .filezilla, etc.

I hope this helps and is understandable ::::=§

---

### Post by mörgæs on 2013-04-29
Thanks, if you have more you are always welcome to post.

---

### Post by JKyleOKC on 2013-06-04
I'd like to add my thanks for this great guide. I use only the LTS releases, and wait for at least the x.1 release of those to give bugs a chance to surface and die. With the EOL of 10.04 last month, I was quite concerned about upgrading this machine because of its unusual configuration and plethora of added utilities.

After going through all four pages, I decided to bite the bullet and try for an in-place upgrade; if it failed, I decided, I would be in no worse position for recovering than I would be if I tried just a clean install first. I backed up all dozen VirtualBox VMs, took careful note of my "udev" customizations and the three network cards, and hit the "Install" button.

I'm happy to report that the upgrade went quite smoothly! Despite my apprehension about having to reconfigure the network settings, iptables, and the resident daemons, the only problem I encountered was having to migrate the Xubuntu panels -- and even that was nicely automated, requiring only that I replace the icons on the various launchers.

Since the vast majority of posts in support forums deal with problems, I thought it might help balance things a bit to report when all went well. And had it not been for this great thread, I might not have gotten up the courage to try it!

---

### Post by mörgæs on 2013-06-05
Thanks for the kind words. Good to see that someone is reading the thread.

---

### Post by Aquijadar on 2013-10-14
[FONT=arial] ESPERO SU RESPUESTA PARA SOLUCIÓN DE PROBLEMA:QUE REITERO:[/FONT]
[FONT=arial]> No puedo inicializar la información de los paquetes.[/FONT]
[FONT=arial]> Tengo un fallo en el paquete <<update manager>>[/FONT]
[FONT=arial]> ¡Gracias![/FONT]
[FONT=arial]> Aquijadar[/FONT]

[FONT=arial]al parecer, he agregado alguna fuente de paquetes (parece google earth) y ha[/FONT]
[FONT=arial]sido de manera incompleta.
Ruego informes para solucionar el problema, pues me impide actualizar Ubuntu[/FONT]

---

### Post by mörgæs on 2013-10-14
Most people here prefer English. 
If you want to post in another language it's better to try our [international pages]("http://ubuntuforums.org/forumdisplay.php?f=183").

---

### Post by mörgæs on 2013-10-17
The text is revised and valid for 13.10 as well.

---

### Post by dmtparker on 2014-01-05
Moved post to Ubuntu Studio. Sorry for confusion

---

### Post by mörgæs on 2014-04-23
Original post has been changed to better suit 14.04.

---

### Post by SteveL1990 on 2014-04-24
Well, okay, here's an error: I can't watch YouTube anymore on 14.04 after upgrading from 13.10.....even though Flash seems to have been updated(It says "You need the latest Flash Player to watch this video). What's up with that?

I did receive a message after booting that the plugin had failed to install for some reason, but I managed to get it successfully installed before I tried YouTube.....so I dunno if that was it or not. Any help appreciated.

---

### Post by mörgæs on 2014-04-25
Did you proceed through the steps outlined in the original post?

---

### Post by SteveL1990 on 2014-04-26
> **mörgæs said:**
> Did you proceed through the steps outlined in the original post?

I hadn't gotten around to it yet, but thankfully. the problem actually resolved itself after a few hours.....maybe I should've been more patient, I guess. :o

Thanks anyway, though. :D

---

### Post by wvonstockhausen on 2014-04-26
Mr. Moderator we don't expect from "push button" upgrade to have to do extra things especially if we are not that technical. The developer should test the new version first with the basic configuration most people have like downloading from camera using USB. All other previous upgrades I did, have no problems with this very basic feauture.

---

### Post by mörgæs on 2014-04-27
1) From original post:
> **mörgæs said:**
> 
Whether or not an upgrade is generally safe compared to a clean install is not the topic.

2) I'm not a developer. If you have a suggestion for them it's not efficient to post it here.

---

### Post by john_a2 on 2014-11-21
Hello, I wish I had taken the precautions mentioned in this thread for the /home directory. I didn't make any backup which I know wasn't smart. I ran an upgrade from 12.04 to 14.04, and my user home dir seems to have vanished. Is there any hope for recovering the directory? If anyone more knowledgeable could point me in the right direction in getting to the bottom of this, or at least confirm that I'm probably out of luck, I'd appreciate it.

---

### Post by mörgæs on 2014-11-22
Hi, welcome to the fora.

When something goes bad during an upgrade it's normally not a problem of lost files. They might be harder to access, but not gone. 

Have you done a live boot?

---

### Post by john_a2 on 2014-11-24
> **mörgæs said:**
> Hi, welcome to the fora.

When something goes bad during an upgrade it's normally not a problem of lost files. They might be harder to access, but not gone. 

Have you done a live boot?

Thank you for your reply, mörgæs. I have not yet tried a live boot, but will do so. Is there any particular actions I should be taking once I live boot? In the meantime I'll get it set up and just poke around a bit.

---

### Post by dankegel on 2014-12-08
I upgraded an Ubuntu 14.04 system (using fglrx) to Ubuntu 14.10, and I could not get a working session after that; it would just hang after logging in.
Logging in to a text VT with ALT F1 worked, but gave me the funny error
"systemd-logind[1057]: Failed to start unit [email]user@1000.servic[/email]e: Unknown unit: [email]user@1000.servic[/email]e"

I did three things that seem to have helped:
1) linux-generic wasn't installed; I was still running kernel 3.13 ?!  So I did 
  sudo apt-get install linux-generic
2) linux-source wasn't installed; it couldn't recompile the fglrx module on install (and apt-get install fglrx... complained) ?!  So I did
  sudo apt-get install linux-source
3) /etc/ati was empty, so I needed to reinstall fglrx and friends.  But just doing dpkg -r and sudo apt-get install on them didn't seem to help.
But as suggested in [https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1359439](https://bugs.launchpad.net/ubuntu/+source/systemd-shim/+bug/1359439),
rebooting after uninstalling them might be important, e.g.
 sudo dpkg --purge fglrx fglrx-amdcccle fglrx-core 
 sudo shutdown -r now
 sudo apt-get install fglrx fglrx-amdcccle fglrx-core 
Or maybe it was the --purge that was important.

ubuntu 14.10 was the most painful upgrade I've done in a long time.   I usually prefer clean installs, and this is an example of why.

---

### Post by dreamer2 on 2014-12-28
After action report:

We live in the woods. Mifi is all we got. So, Christmas Eve I needed to bump up another 2 gig. Well, looking at the data allowance, somehow it showed more like 4 gig. So, calculations in place, upgrade from 12.04 to 14.04. It did not go well. It seems that my separate home partition was not big enough and caused all kinds of havoc. Had to go through a LiveDVD to get a gparted that wanted to work. Did a couple of partial upgrades and stuff (who knows, sometimes I just keep pounding on the keys til something works). So I like it. Looks good. Wireless works. I'm hacking this out on it.

When trying to get a shell, the terminal pops up, displays a message that I can't seem to grab, and promptly disappears.  Lurking has not found a similar problem or solution. Is there a setting or option for the shell that I've fat fingered?

What have I done? What can I do?

Thanks,

Gary

Acer T3-600 (yes, the emachines lawsuit one)
T1620 dual core 2.7GHz
4 Gb Ram
Dual Boot 14.04 (was 10.04, then 12.04) Xubuntu, CAELinux 2013 / Windows 8.1 (only turned it on once in three months)
1/2 TB SATA

---

### Post by ubfan1 on 2015-01-06
Have you tried to run an xterm?  Can you start a gnome-terminal (I assume that's what you are trying to start and it fails) from another user login like the guest?  Might be a config issue if those two things work.  Try this:  rename the .config directory in your home drectory (thats dot config) to something like .configold and try the terminal again.  If that works, you can just keep the new (newly created ) .config directory.  Anything you think you need from the .configold directory, just copy over.  If no improvement, just remove the newly created .config and rename the .configold back.  You should always be able to get to one of the virtual terminals (Ctrl-Alt-F1  through F6).

---

### Post by mörgæs on 2015-10-21
Now 15.10 is underway and we expect a lot of questions as usual. 
If anyone has suggestions for original post please let me know and I'll add them.

---

### Post by psmrima on 2015-12-20
I upgraded from 14.10 to 15 using the release upgrade command. Now I get this error
Drag and drop of image is not working so
"Target filesystem doesn't have requested /sbin/init.
/bin/sh: 0: Can't open auto"

I went through a bunch of steps as found on google search but I am unable to fix it.
Rebooted using 15.0 iso image, clicked on try ubuntu  and did boot-repair -- failed
[http://paste.ubuntu.com/14113161/](http://paste.ubuntu.com/14113161/)

As [http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html](http://pinoy-computing-tips.blogspot.com/2010/08/how-to-fix-ubuntu-error-no-init-found.html)
did the "fsck command" but it is still giving this error.

I have a lot of important data on this OS so I desperately want to fix this. Please help

---

### Post by mörgæs on 2015-12-20
Are you able to see your data from the live boot?

---

### Post by psmrima on 2015-12-20
No I didn't.

Also I am running ubuntu in vmplayer on windows 10 desktop.

---

### Post by pyrophorus2 on 2016-02-10
I upgraded my desktop from 15.04 to 15.10 no problem

The Laptop I tried and left it. I'm not getting an error, but the splash is on constantly
How can I resume/restart the installation or even go back to 15.04 to again attempt it?

I can created and burned a 15.10 iso...and it is working, but I would rather avoid a clean reinstall

---

### Post by melo-o on 2016-11-04
I can no longer set interlingua with the "Language Support".
In Ubuntu version 15.04, although the Interlingua as the basis language change was not available during the intallation of Ubuntu, I could set with the "Language Support". Making the upgrade to version 16.04 of Ubuntu application "Language Support" no longer function to interlanguage, while other language, for example the Italian, it works correctly. Have you any suggestions?

---

### Post by mörgæs on 2016-11-05
Looks like it should be available: [http://packages.ubuntu.com/search?keywords=language-pack-ia](http://packages.ubuntu.com/search?keywords=language-pack-ia)

How does 16.04.1 or 16.10 work in a live boot?

---

### Post by wireman67 on 2016-11-20
I think I am on the right "Thread", please review and move to appropriate thread if I am incorrect to post in this thread.  I am into my third day of using my Ubuntu 14.04 LTS "Trusty Tahr".  My first "Thread" is titled "Installing Ubuntu on old Desktop without any OS" in the _New to Ubuntu Section_.  I am happy thus far, but I have much to learn i.e., Linux terminology, Linux architecture, etc.,,,  I installed Ubuntu 12.04 Precise Pangolin, but I don't recall if I was prompted to upgrade to Ubuntu 14.04 LTS during the installation or after the installation was complete.  I elected to upgrade Trusty Tahr and immediately after installing 14.04 I again was prompted if I wanted to upgrade to Ubuntu 16.04 LTS, "Xenial Xerus".  In the past two days I accepted a few updates that I believe are part of the Trusty Tahr baseline or is the appropriate term "Distros" because I haven't initiated any downloads from the Ubuntu Software Center.  I read on this board, other Linux resources on the internet and in several Linux publications [I have a questions about the publications too] that Linux users should only use the Linux operating systems that have "support teams".  

Do you recommend upgrading to 16.04 or that I should stay with 14.04?
What are the advantages vice the disadvantages between 16.04 and 14.04?
What is the difference between a distros and a flavor?

I observed that my system details illustrates 2.9 GiB Memory, but I know I have 4GB of RAM installed in my desktop; however, I also noticed a 1.0 GB Volume.  I opened it and noticed that it is my windows and WinXP stuff.  

I don't recall, but I think I accidentally mounted both my hard drive and the my WinXP partition (the 1.0 GB Volume) when I was attempting to view the properties.  Do I need to unmount both or did this occur automatically during the installation?  

 What command and/or program may I use to see a report stating the configuration my Linux Ubuntu 14.04?


Thank you,

---

### Post by mörgæs on 2016-11-21
> **wireman67 said:**
> 
 What command and/or program may I use to see a report stating the configuration my Linux Ubuntu 14.04?

I don't know exactly what you mean by configuration but the command ```
sudo lshw -sanitize > lshw.txt
``` should provide a beginning. Please post lshw.txt in CODE tags.

If 14.04 does all that you need you can use it for as long as it's supported. For Ubuntu this means through april 2019, for the other Buntus 2017.

---

### Post by mikenh on 2017-06-25
FWIW, the tutorials mentioned in Post 5 are by psychocats. [http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by jonno-in-uk on 2017-11-04
[COLOR=#000000]I was running [/COLOR][COLOR=#417394]Banshee[/COLOR][COLOR=#000000] quite happily on 16.04.[/COLOR]

[COLOR=#000000]I just upgraded ubuntu to 17.04 and now Banshee won't play anything. It doesn't seem to matter what I click on, it just sits there on Idle![/COLOR]

[COLOR=#000000]I know a bit of unix but I am pretty much of an ubuntu novice, so I have no idea how to fix this.

I tried uninstalling and reinstalling Banshee but that makes no difference.[/COLOR]

---

### Post by mörgæs on 2017-11-05
Is Ubuntu 17.04 your final destination? It's only supported through January.

---

### Post by bacizone on 2018-02-07
Hi, 

since the last full update (07/02/2018), all video players in **Lubuntu** stopped working. Not sure but I think I started from Lubuntu 14.04 LTS and install updates regularly.

Neither VLC nor Gnome MPlayer plays any video: they just crash and exit when I load and press play on a simple mp4 video file that was played previously without any problem. 

Tried reinstalling the players, but it seems to be a Lubuntu problem. 


**When can I expect a hotfix for this serious defect?**

---

### Post by mörgæs on 2018-02-08
We don't know yet if it's a defect or not.

Please try a live boot of Lubuntu 17.10.1 and see if there is any difference.

---

### Post by bacizone on 2018-02-08
See also: [https://ubuntuforums.org/showthread.php?t=2384497](https://ubuntuforums.org/showthread.php?t=2384497)

---

### Post by bahadirer34 on 2018-05-09
I've upgraded from 17.10 to 18.04 today, and now when I try to log in to my account, login screen reappears.  

I can login using gnome-shell, and I've created another user to see if I can login as another user, and it seems to be working.

Thanks in advance.

---

### Post by mörgæs on 2018-05-11
If user settings have been damaged during the upgrade a situation like this can happen.
I think you found a good solution: Just use another user name for the future. Often easier than trying to fix the damaged settings.

When you some day are switching to a new release I suggest a fresh install and not an upgrade.

---

### Post by bahadirer34 on 2018-07-05
Sorry, it's a bit late but thanks for the help. I already did a fresh install back then, and did not check here. :)

---

### Post by Rick St. George on 2019-05-22
***********************

started new thread

***********************

---

### Post by keithupton7496 on 2019-07-05
Put Ubuntu on a old laptop solo gateway 5300 Administrator x Commander

---

### Post by keithupton7496 on 2019-07-05
Ip addresse

---

