---
title: "Installer Crashed"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by thehenryfam on 2011-09-19
Greetings, all.

I am experienced with computers but not so much with Linux. We decided to install Ubuntu on a box here at work and play around with it. However, I have been unable to install Ubuntu Desktop 11.04 (32 bit) due to getting an "Installer Crashed" message after about 20 minutes into the process. It says something about sending log files, however I am not even certain how to go about getting to those files to send them.

I am not trying to install it alongside any other operating system, and when given the option in the installer, I always choose to have it "erase and install."

I have tried several things to isolate the problem:

-- Re-downloaded the i386-iso
-- burned several different CDs
-- Tried it on three different computers (two Dells, one HP)
-- Reformatted the hard drive(s)

The computers I am attempting to install this on are of the 2 GHz processor, 2 GB RAM, on-board video variety. I made sure there were no 3rd-party cards or other devices plugged in during installation.

In any event, I am at a loss what to try now. Should I go back to the previous version and give that a try? Kind of hate to do that. I'm an IT Specialist in my full-time work and would much rather just figure this out if possible.

Thanks for any help you can provide!

Scott

---

### Post by Blasphemist on 2011-09-19
Are you installing from the live cd? Have you tried the "try ubuntu" option before you start the install? If so, does it come up to a desktop and are you able to connect the network and run firefox? For that matter, are you connected to the internet while running the installation? It is recommended. What is the install doing when it fails? Is it getting to the slides and completely through asking all of the questions? Are the pc's BIOS or EFI?

This is very odd so I'm just thinking of all the basics.

---

### Post by thehenryfam on 2011-09-19
Installing from Live CD? Yes

Attempted "Try Ubuntu" option? Yes

Can connect to network and run Firefox? Yes

Connected to internet while installing? The PCs have always been connected to our network (and internet) while doing the installations. However, it was only the last time I attempted the installation that the Ubuntu installer recognized that I was indeed connected (with the check mark).

What is it doing when it fails? It is going through the slideshow (it seems to stay in the slideshow loop for quite some time). I have expanded the little window to watch the installation activity. I have noticed a couple errors that occasionally appear there, and I am not sure if they are relevant or important:

1) stdin: file format not recognized
2) in-target: Decoder error
3) (stdin) is not a bzip2 file

Also, when the "Installer Crashed" box appears, the last thing in the activity window is "pluginstall.py", whatever that is.

Are the PCs BIOS or EFI? They are BIOS.

Thanks again,
Scott

---

### Post by Blasphemist on 2011-09-19
Well, ain't that a kick in the pants!

I have a bunch of distros including 4 that use the ubuntu installer on this laptop. I install different flavors at least once a week and don't think I've ever run into this. So lets at least try something different.

When you get to the allocate disk space screen, choose "something else". This is the manual partitioning option. Delete any partitions that show up, if any do. Then create a primary EXT4 formatted partition of at least 20GB and set its mount point as /. Also create an extended that includes the rest of the disk. In that extended partition create a logical partition formatted as EXT4 with a mount point of /Home that is say 50GB. Lastly create a swap partition of a bit over 2GB (larger than the amount of memory). 

Then try to watch closely just what all happens while the slides are up. Maybe even write down what things it says it is doing. 

Do start with the try ubuntu option and verify the network connection has access to the internet. If you have been plugged in to the network, that is best but do test it before you start the install. You should be prompted during the install for whether or not to download updates while installing, do select that and the option below it about installing the restricted extras.

---

### Post by thehenryfam on 2011-09-19
Thank you, Jim. I will give this a try tomorrow when back in the office and will let you know how it goes!

Scott

---

### Post by PrimordialAstronaut on 2011-09-19
Hi guys,

I am having exactly the same problem as thehenryfam. Found this thread while searching for some help. Basically, same deal... my "try ubuntu" option works fine, it's only when I go to install that I get an error. I get through the first couple of windows just fine, but then I get either a "ubiquity has crashed" error or a general "problem with installation error."

I have tried creating boot cds using InfraRecorder, ImgBurn, and as a last ditch effort, Nero. I seem to have the most success with ImgBurn and Infrarecorder... but I'm not really sure where the problem is.

Is there a preference of speed when writing these cds? I read somewhere to go with the slowest burn speed possible, but it doesn't specify in the informational page on Ubuntu.com so I'm really sure what to think. Unfortunately I do not have the option of booting from 
USB, so that's no help. 

Halp?

---

### Post by Blasphemist on 2011-09-19
Can you try this iso for me please? [http://sourceforge.net/projects/ubuntu-secured/files/](http://sourceforge.net/projects/ubuntu-secured/files/)

It has clean-ubiquity and I'm hopein that will make a difference. 

The other possibility would be try downloading from a torrent if you haven't been. I have better luck and they are even faster. I don't know of a torrent of the secured cd though.

---

### Post by PrimordialAstronaut on 2011-09-19
Hi Blasphemist!

Okay, well I finally did get my install to work. I used the alternative version of the ISO file (from a torrent) and the install worked fine on the second try. Now I'm having an all new problem... which is really weird...

I finished install, was prompted to remove my boot cd which I did, and restarted the computer. Well, now it's asking for the password I just created to log in. But when I put in the password it says the password is wrong. I know for a fact it is not... cause I just created it not 5 minutes ago! I tried all caps, no caps, every configuration I can think of to no avail. Wtf? Is there a way to reset the password, or am I going to have to re-install all over again?

---

### Post by thehenryfam on 2011-09-20
Jim, I am getting ready to try your suggestions. In the meantime, I am attaching the log files that the installer recommended I send to the Ubuntu folks for submitting a bug report. Thought you might want to look at those for any clues they might contain.

Thanks!

Scott

---

### Post by Blasphemist on 2011-09-20
[http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/](http://www.howtogeek.com/howto/linux/reset-your-forgotten-ubuntu-password-in-2-minutes-or-less/)


This should walk you through changing the password.

---

### Post by Quackers on 2011-09-20
Have you checked the md5sum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out ok when booting from the live cd and at the FIRST purple screen (with the little man icon at the bottom) press any key.
Then choose your language and on the next screen choose the "check for errors" menu item.
Let that run and if it comes up with a single error the disc is faulty.

It is generally good advice to select the slowest burn speed available when burning an iso file to disc.

Having said all that though, I have come across this type of error myself.
I have "cured" it a couple of ways.
One time I just cleaned the disc and the laser in the cd drive - just with a dry lint-free cloth.
Another time the installation kept failing until I disconnected from internet. Then it went fine. After installation it connected to internet just fine and ran all the updates without a problem.

Have fun :-)

---

### Post by thehenryfam on 2011-09-20
Ok, Jim. I followed your suggested steps for the manual partitioning, but it still did not work.

The installer gets all the way to the "Removing extra packages..." stage. In the window below it is again showing: "ubuntu plugininstall.py". 

I am downloading the secure iso you mentioned before. I will next see if that makes any difference.

Thanks,
Scott

---

### Post by Blasphemist on 2011-09-20
> **thehenryfam said:**
> Jim, I am getting ready to try your suggestions. In the meantime, I am attaching the log files that the installer recommended I send to the Ubuntu folks for submitting a bug report. Thought you might want to look at those for any clues they might contain.

Thanks!

Scott

I'm looking at the logs Scott and I don't really have a solution but I do see something that makes me wonder. What are you using for a monitor? There are a lot of errors trying to read the EDID data from the monitor. Do you have anything different to try?

I think from the logs that grub does get installed. When you reboot after a failed install, what happens? Do you see grub and if so do any of the options boot?

I'll look through the logs some more until I hear back from you.

---

### Post by Blasphemist on 2011-09-20
What version are you installing? I see some bugs that might be related but it seems they were resolved just prior to release of 11.04.

---

### Post by thehenryfam on 2011-09-20
When I reboot, it actually loads the OS without any issue. I can log in and get to the desktop and everything. I even launched a couple apps (Firefox and Office) and they seemed to work well. However, when I went to the update manager, I was presented with the following error message:

"Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update manager' package and include the following error message:

'E:Encountered a section with no Package: header, E: Problem with MergeList/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.' "

The monitor I am using is an HP L717g. I have another one handy that I can try if you think that might make any difference at all.

Scott

> **Blasphemist said:**
> I'm looking at the logs Scott and I don't really have a solution but I do see something that makes me wonder. What are you using for a monitor? There are a lot of errors trying to read the EDID data from the monitor. Do you have anything different to try?

I think from the logs that grub does get installed. When you reboot after a failed install, what happens? Do you see grub and if so do any of the options boot?

I'll look through the logs some more until I hear back from you.

---

### Post by thehenryfam on 2011-09-20
11.04

> **blasphemist said:**
> what version are you installing? I see some bugs that might be related but it seems they were resolved just prior to release of 11.04.

---

### Post by Quackers on 2011-09-20
The syslog reports a missing package header too. I'm not sure of the significance though.

---

### Post by thehenryfam on 2011-09-20
Disc checked out OK, no errors.

Yes, I did an MD5 check on the iso file, and it was also fine. I have not tried burning at a lower speed. I was using ImgBurn's default speed, whatever that is. Maybe I will try that. I don't think the disc is dirty as I have burned about 5 of them now. I will try to blow out the drive itself.

Scott

> **Quackers said:**
> Have you checked the md5sum of the downloaded iso file?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out ok when booting from the live cd and at the FIRST purple screen (with the little man icon at the bottom) press any key.
Then choose your language and on the next screen choose the "check for errors" menu item.
Let that run and if it comes up with a single error the disc is faulty.

It is generally good advice to select the slowest burn speed available when burning an iso file to disc.

Having said all that though, I have come across this type of error myself.
I have "cured" it a couple of ways.
One time I just cleaned the disc and the laser in the cd drive - just with a dry lint-free cloth.
Another time the installation kept failing until I disconnected from internet. Then it went fine. After installation it connected to internet just fine and ran all the updates without a problem.

Have fun :-)

---

### Post by Quackers on 2011-09-20
Good advice but sadly, I hadn't seen your post about a successful install. So largely useless now :-)

---

### Post by Blasphemist on 2011-09-20
Running these commands from a terminal should fix the package list issue and run an update.
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

I don't know if you are back into the install or not but the above solution came from this page.  [http://askubuntu.com/questions/25307/how-do-i-fix-the-package-lists-or-status-file-could-not-be-parsed-or-opened-dur](http://askubuntu.com/questions/25307/how-do-i-fix-the-package-lists-or-status-file-could-not-be-parsed-or-opened-dur)

---

### Post by PrimordialAstronaut on 2011-09-20
Should I go to another thread with this problem? You guys are all really helpful but I don't want to derail your thread...

Anyway, yeah Blasphemist: I read about that fix somewhere else last night while researching this... but I'm confused because I never get that "Grub Loading" text during my boot at all. I'm starting to think something went wrong with my install after all... I hit esc over and over throughout the boot process and get nothing. It just goes to the login screen and I still can't login with my password.

So confused...

---

### Post by Blasphemist on 2011-09-20
I think you need to press the shift key a few times as soon as the system starts to go to the hard drive during boot. This should bring up the grub menu.

I think that will allow you to make the change. If it doesn't it may be best to start a new thread on as you'll be able to name the thread more appropriately and you may get help from others that wouldn't touch this thread :D

---

### Post by PrimordialAstronaut on 2011-09-20
Okay yeah Shift also does nothing. I'll go start a new thread. Thanks for your help. ^_^

---

### Post by thehenryfam on 2011-09-20
Running another install attempt right now using the "secure" iso you mentioned earlier, which I also burned at a speed of 1X just for good measure.

Also switched monitors this time.

Failing those things, I will try these commands to clean up the update process.

Thanks,
Scott


> **Blasphemist said:**
> Running these commands from a terminal should fix the package list issue and run an update.
```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```I don't know if you are back into the install or not but the above solution came from this page.  [http://askubuntu.com/questions/25307/how-do-i-fix-the-package-lists-or-status-file-could-not-be-parsed-or-opened-dur](http://askubuntu.com/questions/25307/how-do-i-fix-the-package-lists-or-status-file-could-not-be-parsed-or-opened-dur)

---

### Post by Blasphemist on 2011-09-20
We are getting close to 11.10 release. A person could install that now and automatic updates would have you at the release level in about 3 weeks. This shows that additional nvidia drivers are included in the dvd iso that could be installed from dvd or usb. I'd download it from a torrent as I have better luck with it completely downloading and it is faster. I don't know that the additional drivers would help but if you are going to reinstall anyway it might be worth a shot.
[http://askubuntu.com/questions/10844/what-is-on-the-dvd-edition-of-ubuntu/62282#62282](http://askubuntu.com/questions/10844/what-is-on-the-dvd-edition-of-ubuntu/62282#62282)

---

### Post by thehenryfam on 2011-09-20
Ok. Well, the latest install attempt failed at the same point.

So I am running the apt update right now to see if it can repair whatever didn't get installed properly.

Failing that, I may try the 11.10 beta. Got nothing to lose at this point. Can't believe I am having so much trouble with this. I'm a big believer in open source, but this has been more arduous than I had imagined. I am hoping to run an FTP server off of this box. Hopefully I can get that configured without too much of an issue.

Question: so if I jump to 11.10 beta, you don't see the migration to the release version as a big deal?

Thanks,
Scott

> **Blasphemist said:**
> We are getting close to 11.10 release. A person could install that now and automatic updates would have you at the release level in about 3 weeks. This shows that additional nvidia drivers are included in the dvd iso that could be installed from dvd or usb. I'd download it from a torrent as I have better luck with it completely downloading and it is faster. I don't know that the additional drivers would help but if you are going to reinstall anyway it might be worth a shot.
[http://askubuntu.com/questions/10844/what-is-on-the-dvd-edition-of-ubuntu/62282#62282](http://askubuntu.com/questions/10844/what-is-on-the-dvd-edition-of-ubuntu/62282#62282)

---

### Post by thehenryfam on 2011-09-20
Ok, here's the latest.

I deleted the apt lists and ran the apt update.

I watched much of the process and saw tons of decoder and file format not recognizes errors. Not sure if that is normal or not.

It got about 81% of the way through and then stopped, while reporting the following:

"Reading package lists... Error!

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease: The following signatures were invalid: NODATA NODATA 1 NODATA 2
W: GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease: The following signatures were invalid: NODATA 1 NODATA 2
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened."

UGH!

Should I give 11.10 a try?

Scott

---

### Post by thehenryfam on 2011-09-21
Well, I'm about to give up and go try CentOS or something. Still no luck. I downloaded 11.10 Beta 1, and it has been "stuck" on "Retrieving file 28 of 63" for about 30 minutes, so I am guessing it is frozen. I'll give it a little while longer since it is not reporting a running log below it like the other installations were doing. I guess I could try to go back to 10.10.

Anyone else have any ideas before I throw in the towel?

This has been very frustrating...

Scott

---

### Post by thehenryfam on 2011-09-21
I finally got success!

It dawned on me that the only variable I had not tested was my network connection. I decided to take the box home and try the install. Well, I was able to get through the entire install as well as the updates with no problem while connected to my cable internet provider at my house.

Wondering if our firewall and other network management here at work was somehow interfering with the installer. Could be that Cymphonix was blocking access to some sites. Anyone else run into that sort of thing before?

In order for me to be able to run updates without issues in the future, what URL patterns should I add to our exceptions list in Cymphonix? Obviously *.ubuntu.com. Anything else?

Thanks for all your assistance.

Scott

---

