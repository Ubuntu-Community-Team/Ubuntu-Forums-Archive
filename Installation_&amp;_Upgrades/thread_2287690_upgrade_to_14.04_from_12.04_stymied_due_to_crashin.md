---
title: "upgrade to 14.04 from 12.04 stymied due to crashing update manager and software ctr."
date: 2015-07-21
forum: Installation &amp; Upgrades
---

### Post by Eagle Nest on 2015-07-21
Hi friends:

I have a dual boot environment with Windoze Vista and Ubuntu 12.04. I want to** upgrade** the 12.04, which hasn't been** updated** in some time, to 14.04 and keep the dual boot arrangement for now. Both the update manager and software centers crash immediately upon opening. 

Some advice on terminal commands would be helpful. 

Also, I want to resize the Vista partition once the upgrade is complete. I'd like to make it smaller. Any advice here would be appreciated as well. The Windows OS is useful for chess software but my plan is to make use of WINE or VM or something like that to switch entirely over to a Linux environment. 

OK, the key thing for now is that I can neither update or upgrade the 12.04. I printed myself a copy of William Shotts' Linux Command Line text but have only started to look at it.

(I will stick around for any quick replies and then check back daily or more often after than. Cheers. )

---

### Post by ubfan1 on 2015-07-21
From a terminal try the update,
sudo apt-get update
Then you can try the GUI software updater again.
Otherwise, just continue at the terminal with
sudo apt-get upgrade
sudo apt-get dist-upgrade
The 12.04 to 14.04 upgrade is the normal one for the LTS 12.04.

---

### Post by Eagle Nest on 2015-07-21
> **ubfan1 said:**
> From a terminal try the update,
sudo apt-get update
Then you can try the GUI software updater again.
Otherwise, just continue at the terminal with
sudo apt-get upgrade
sudo apt-get dist-upgrade
The 12.04 to 14.04 upgrade is the normal one for the LTS 12.04.

**Good advice but nothing much happened**. No updating or upgrading is happening. In addition, not only is the software updater crashing, and the icon for the update manager no longer appearing on the left hand list of icons (it can be found in DASH), but the program "report a problem" is also crashing. Blecch. 

The BIOS list includes something I have seen with strict Windows BIOS; I mean "safety" or "recovery" mode for Ubuntu. However, since I don't know what the problem is, I just noticed the list and got out of there. 

I really don't want to have to re-install the Windows OS and then install the 14.04 beside it. Ive done it before with 12.04 and its a lot of work. Suggestions? 

PS - if you think I should be logging some of these steps with log.txt, etc., , then please say so and don't wait until after Ive done something. Cheers.
PPS - I am getting some (unreadable) messages on reboot. There used to be a way to slow these down so they were readable.

---

### Post by grahammechanical on 2015-07-21
We cannot give you much help if all you are going to say is "nothing much happened."

When we run apt-get update and apt-get upgrade we get error messages that can give us clues as to what is causing the problem. If you post any error messages and enclosed them in QUOTE tags then we can look through them. You need to be settled in your mind as to what you want to do. Fix the updating problems with Ubuntu 12.04? Or, upgrade from Ubuntu 12.04 to Ubuntu 14.04? Or install again Windows Vista and fresh install Ubuntu 14.04?

By the way, that BIOS list that you are seeing is the boot menu from the Linux Grub boot loader. Or so I am guessing. Linux system loading messages are printed to the screen very quickly. They are mostly hidden behind a splash screen. If the system loads to a login screen and a desktop user interface then we should not be distracted by them. You did not mention in your first post that you were having problems loading to a Ubuntu desktop. You did say that Update Manager and Software Centre were crashing on opening.

Remember, error messages are useful to us.

Regards.

---

### Post by Bucky Ball on 2015-07-21
Just a note. _Always_ run 'sudo apt-get update' prior to 'sudo apt-get upgrade'.

In Software and Updates, go to the 'Updates' tab and set it to only notify of long-term support (LTS) releases.

Open a terminal and:

```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Copy and paste any and all errors here between code tags, thanks (see the last link in my signature).

You must run the above commands (at least update, upgrade, dist-upgrade) prior to upgrading your OS to a newer release. Also, switch off any third-party PPAs you have installed manually. You want the machine as 'vanilla' as possible. Be aware that if you have installed third-party drivers from anywhere other than the repos they may break after the upgrade. This generally applies to wireless and graphics.

Good luck.

PS: Use an ethernet cable during the upgrade. Wireless is not advisable. Wireless breaking part-way through an upgrade can leave you with a very broken system. Also wise to do a backup of valuable data.

---

### Post by Eagle Nest on 2015-07-21
> **Bucky Ball said:**
> 

In Software and Updates, go to the 'Updates' tab and set it to only notify of long-term support (LTS) releases. 

If you mean a tab in either update manager OR the software center, then I don't have access to it. They just crash. 

> Open a terminal and:

```
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

Copy and paste any and all errors here between code tags, thanks (see the last link in my signature). 

ok, i will use the > file.txt and >> file.txt feature to keep a record. 

> Use an ethernet cable during the upgrade. Wireless is not advisable. Wireless breaking part-way through an upgrade can leave you with a very broken system. Also wise to do a backup of valuable data.

thanks for the reminder. 

ok, here goes...

```
 

Reading package lists...Reading package lists...Hit http://ca.archive.ubuntu.com precise Release.gpg
Get:1 http://ca.archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://ca.archive.ubuntu.com precise Release
Hit http://archive.canonical.com natty Release.gpg
Hit http://archive.canonical.com precise Release.gpg
Get:2 http://ca.archive.ubuntu.com precise-updates Release [196 kB]
Hit http://archive.canonical.com natty Release
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://extras.ubuntu.com precise Release.gpg
Hit http://archive.canonical.com precise Release
Hit http://extras.ubuntu.com precise Release
Get:4 http://security.ubuntu.com precise-security Release [54.3 kB]
Hit http://archive.canonical.com natty/partner i386 Packages
Ign http://archive.canonical.com natty/partner TranslationIndex
Hit http://ca.archive.ubuntu.com precise/main Sources
Hit http://ca.archive.ubuntu.com precise/restricted Sources
Hit http://ca.archive.ubuntu.com precise/universe Sources
Hit http://ca.archive.ubuntu.com precise/multiverse Sources
Hit http://ca.archive.ubuntu.com precise/main i386 Packages
Hit http://ca.archive.ubuntu.com precise/restricted i386 Packages
Hit http://ca.archive.ubuntu.com precise/universe i386 Packages
Hit http://ca.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com precise/main TranslationIndex
Hit http://ca.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://extras.ubuntu.com precise/main Sources
Hit http://ca.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://ca.archive.ubuntu.com precise/universe TranslationIndex
Get:5 http://ca.archive.ubuntu.com precise-updates/main Sources [490 kB]
Hit http://archive.canonical.com precise/partner Sources
Hit http://archive.canonical.com precise/partner i386 Packages
Hit http://archive.canonical.com precise/partner TranslationIndex
Hit http://extras.ubuntu.com precise/main i386 Packages
Ign http://extras.ubuntu.com precise/main TranslationIndex
Get:6 http://security.ubuntu.com precise-security/main Sources [131 kB]
Hit http://archive.canonical.com precise/partner Translation-en
Get:7 http://ca.archive.ubuntu.com precise-updates/restricted Sources [7,981 B]
Get:8 http://ca.archive.ubuntu.com precise-updates/universe Sources [122 kB]
Get:9 http://ca.archive.ubuntu.com precise-updates/multiverse Sources [9,714 B]
Get:10 http://ca.archive.ubuntu.com precise-updates/main i386 Packages [969 kB]
Hit https://private-ppa.launchpad.net precise Release.gpg
Hit https://private-ppa.launchpad.net precise Release
Hit https://private-ppa.launchpad.net precise/main i386 Packages
Get:11 https://private-ppa.launchpad.net precise/main TranslationIndex [374 B]
Ign https://private-ppa.launchpad.net precise/main TranslationIndex
Get:12 http://ca.archive.ubuntu.com precise-updates/restricted i386 Packages [13.6 kB]
Get:13 http://ca.archive.ubuntu.com precise-updates/universe i386 Packages [277 kB]
Get:14 http://ca.archive.ubuntu.com precise-updates/multiverse i386 Packages [16.7 kB]
Get:15 http://ca.archive.ubuntu.com precise-updates/main TranslationIndex [10.6 kB]
Get:16 http://ca.archive.ubuntu.com precise-updates/multiverse TranslationIndex [7,613 B]
Get:17 http://ca.archive.ubuntu.com precise-updates/restricted TranslationIndex [7,297 B]
Get:18 http://ca.archive.ubuntu.com precise-updates/universe TranslationIndex [8,333 B]
Hit http://ca.archive.ubuntu.com precise/main Translation-en_CA
Hit http://ca.archive.ubuntu.com precise/main Translation-en
Hit http://ca.archive.ubuntu.com precise/multiverse Translation-en
Hit http://ca.archive.ubuntu.com precise/restricted Translation-en
Hit http://ca.archive.ubuntu.com precise/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com precise/universe Translation-en
Get:19 http://security.ubuntu.com precise-security/restricted Sources [3,759 B]
Get:20 http://security.ubuntu.com precise-security/universe Sources [43.8 kB]
Ign http://extras.ubuntu.com precise/main Translation-en_CA
Ign http://archive.canonical.com natty/partner Translation-en_CA
Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en_CA
Hit http://ca.archive.ubuntu.com precise-updates/main Translation-en
Hit http://ca.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://ca.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en_CA
Hit http://ca.archive.ubuntu.com precise-updates/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en
Ign http://archive.canonical.com natty/partner Translation-en
Get:21 http://security.ubuntu.com precise-security/multiverse Sources [2,199 B]
Get:22 http://security.ubuntu.com precise-security/main i386 Packages [574 kB]
Ign https://private-ppa.launchpad.net precise/main Translation-en_CA
Ign https://private-ppa.launchpad.net precise/main Translation-en
Get:23 http://security.ubuntu.com precise-security/restricted i386 Packages [8,939 B]
Get:24 http://security.ubuntu.com precise-security/universe i386 Packages [131 kB]
Get:25 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,864 B]
Get:26 http://security.ubuntu.com precise-security/main TranslationIndex [208 B]
Get:27 http://security.ubuntu.com precise-security/multiverse TranslationIndex [199 B]
Get:28 http://security.ubuntu.com precise-security/restricted TranslationIndex [202 B]
Get:29 http://security.ubuntu.com precise-security/universe TranslationIndex [205 B]
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 3,090 kB in 4s (627 kB/s)
Reading package lists...Reading package lists...Reading package lists...


```

---

### Post by Bucky Ball on 2015-07-21
That looks like the output from one of those commands, but you haven't actually included the command you've run. Run them all, post the output if there is an error.

---

### Post by Eagle Nest on 2015-07-22
> **Bucky Ball said:**
> That looks like the output from one of those commands, but you haven't actually included the command you've run. Run them all, post the output if there is an error.

OK, yes, that was the output from the** sudo apt-get update** command. There were no errors (other than one when I mis-typed the command).  At least, I typed the commands, one line at a time, and no error messages appeared. 

Now what?

---

### Post by Bucky Ball on 2015-07-22
Software Centre and Software Updater still do not function? That is odd as you have just updated via the terminal, doing exactly the same thing as the Software Updater would have done via a GUI. :-k

So there seems to be nothing wrong with apt-get but something wrong elsewhere. Are SCentre and SUpdater the only apps you're having issues with?

Bottom line: if those update/upgrade commands, all of them, went through without error, you have successfully updated/upgraded you system. I wouldn't upgrade to 14.04 LTS, though, until you've figured out why you can't update via the GUI. Upgrading a broken system to a newer release to fix it doesn't 99% of the time. The original problem generally remains, sometimes with added confusion.

---

### Post by deadflowr on 2015-07-22
This maybe your problem:
```
[COLOR=#000000][FONT=Ubuntu Mono]Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release[/FONT][/COLOR]
```
Post the output for
```
cat /etc/apt/sources.list
```
I think you need to disable the partner repo marked for natty.

It would seem odd that it wasn't coming up with errors...

**Edit:** Nevermind
Canonical doesn't seem to disable or remove the old release version from canonical partner repo.
(Unlike all the other repos...)
So you can keep connecting to it, indefinitely. Regardless of which release you are on and which release is named in the partner repo line.
Odd.

---

### Post by Eagle Nest on 2015-07-22
> **Bucky Ball said:**
> So there seems to be nothing wrong with apt-get but something wrong elsewhere. Are SCentre and SUpdater the only apps you're having issues with?

The same thing happens with Synaptic Package Manager. 

> Bottom line: if those update/upgrade commands, all of them, went through without error, you have successfully updated/upgraded you system. I wouldn't upgrade to 14.04 LTS, though, until you've figured out why you can't update via the GUI. Upgrading a broken system to a newer release to fix it doesn't 99% of the time. The original problem generally remains, sometimes with added confusion.

ok, good point.

---

### Post by Eagle Nest on 2015-07-22
just a note - without much detail here - I have been getting dialogue boxes in regard to "system error" or something like that, and more than once. I click on "send a report" and then carry on. ok, its late, need some sleep and Ive never fixed a machine by staying up late and being tired...

---

### Post by Bucky Ball on 2015-07-22
No help to us. We can not give you much help if you do not give us the appropriate information. Just drags the thread out. 

Take a not of the details of the error and report them here, please, rather than ''system error' or something like that'. We can't work with that. You need to make not of the details of the error and let us know. Please do that.

Include any other information you think might be relevant that you haven't as yet mentioned.

---

### Post by deadflowr on 2015-07-22
If there is a system error then there might be a crash report in /var/crash.

---

### Post by Eagle Nest on 2015-07-22
> **deadflowr said:**
> If there is a system error then there might be a crash report in /var/crash.

Ok, will check that and get back.

---

### Post by Eagle Nest on 2015-07-23
> **deadflowr said:**
> If there is a system error then there might be a crash report in /var/crash.

Yes, there are a set of 7 such reports. They include:

_usr_share_apport_apport_gtk.0.crash
_usr_share_apport_apport_gtk.1000.crash
_usr_share_software-center_update-software-center-agent.1000.crash
_usr_share_software-center_software-center.1000.crash
_usr_share_bin_update-manager.1000.crash
_usr_share_bin_apt-get.0.crash
_usr_share_sbin_synaptic.0.crash

ok, so the apport feature can access sensitive information, such as passwords, credit card numbers, etc., so I don't want to try to display everything here.** how to proceed?**

---

### Post by Eagle Nest on 2015-07-23
After looking at apport, etc., I have found that** the Update Manager and Software Center are both working now.** I am madly installing updates, making sure I am using an ethernet cable, a few updates at a time, not going for the upGRADE as advised.** I have no idea why these things are working now and were not working before.** The Ubuntu God moves in mysterious ways. I am doing ALL the updates as I do not really know what is important and what isn't (important security updates, then i will look at recommended ones)

Not using the Ubuntu 12.04 much, I had a mountain of updates to do. And, as I recall now, I had had some problems updating way back when, maybe last year or earlier, and just let the issue alone. Perhaps this is connected to my recent problems. Maybe someone could address this general point; if you don't do your updates for some time, and wind up accumulating a big pile of them, what to do? 

I think I will probably use the 12.04 for some time, work on my skills with the Linux command line, complete the switch over, and then look at the upgrade. If this is not wise, then could someone let me know why not? thanks. 

Ok, if all goes well I will mark the thread as solved.

---

### Post by Bucky Ball on 2015-07-23
You should be running:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

... one at a time. If you can't run these without error then your machine is still broken and I wouldn't proceed from here without fixing as your machine will not be up to date and your update manager or something else is broken. Post any and all errors from the above commands.

12.04 LTS is supported until 2017 so there's no rush.

---

### Post by Eagle Nest on 2015-07-24
> **Bucky Ball said:**
> You should be running:

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

... one at a time. If you can't run these without error then your machine is still broken and I wouldn't proceed from here without fixing as your machine will not be up to date and your update manager or something else is broken. Post any and all errors from the above commands.

There were no errors. Both the update manager and the software center are working. 

> 12.04 LTS is supported until 2017 so there's no rush.

yeah, true. 

OK, I think this issue is solved. Ive got plenty to do: some re-partitioning, develop some skills with the command line, make sure all the software I need is working, move some bookmarks, yadda yadda. Definitely overdue. Cheers.

---

### Post by Bucky Ball on 2015-07-24
Good news there's no errors. All seems to be good with 12.04 LTS.

Make sure Software and Updates> Updates> 'Notify of LTS releases only' is set and then ignore the reminder you can upgrade to 14.04 LTS until you're ready to do so. When that time comes, run the commands I gave you in that last post, disable any PPAs you have set yourself (you'll find them in the 'Other Software' tab near 'Updates' in Software and Updates) prior to upgrading. 

Good luck. Please mark the thread as solved. See the first link in my signature below. Enjoy the learning curve. :)

---

