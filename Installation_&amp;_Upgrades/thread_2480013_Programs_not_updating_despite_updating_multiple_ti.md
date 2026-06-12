---
title: "Programs not updating despite updating multiple times"
date: 2022-10-16
forum: Installation &amp; Upgrades
---

### Post by inator-maker on 2022-10-16
I have tried posting this on other forums, however, the responses I have received so far indicate that those responding are not fully reading the post.  Let me state from the beginning that Thunderbird is no longer the issue.  

[FONT=verdana]I've tried to use Linux off and on over the years. I recently decided to give it another go. Several weeks ago I installed Ubuntu on my second drive. I did a lot of trying different things and programs to see exactly what I like and want to use. After a few weeks of that I decided to do a clean install and only install what I knew I wanted to use.[/FONT]
[FONT=verdana]This morning I deleted the partition and installed Ubuntu off of the same flash drive i used a few weeks ago. While trying to set up Thunderbird to work with my M365 I was referencing the article I saved on which plugins to add to Thunderbird. I had it working before i did the reinstall, but this morning I the same extensions were not showing up when I searched. I removed Thunderbird and reinstalled. When I did that I noticed that a newer version of Thunderbird had been installed.[/FONT]
[FONT=verdana]Having been installing lots of different programs I updated several times so why was this not updated to latest version?[/FONT]
[FONT=verdana]I am still learning Linux so I'm not sure if I should be concerned about something else being borked and not updating. Is there anything I can to make sure that everything is fully up to date? Should I reinstall the OS again in case something went screwy during the install?[/FONT]

[FONT=verdana]tldr; i found that one program didn't update properly is it possible that others are not as well?  [/FONT]

---

### Post by grahammechanical on 2022-10-16
I am confused. You say Thunderbird is no longer the issue but then you describe the issue you are having with Thunderbird. You say this:

> [FONT=verdana]I noticed that a newer version of Thunderbird had been installed.[/FONT]

But then you say this:

> [FONT=verdana]I updated several times so why was this not updated to latest version?[/FONT]

Was the new version of Thunderbird not the latest version of Thunderbird?

Are you using Ubuntu 22.04? I do not know for sure, but I think that with Ubuntu 22.04 we get the snap packaged version of Thunderbird. I know we do get the snap packaged version of Firefox with Ubuntu 22.04. Both Firefox and Thunderbird are maintained by the Mozilla Foundation. I also know that with Mozilla snap packaged applications such as Firefox update/upgrades are pushed out by the Mozilla developers independently of the Ubuntu developers and separate from the usual apt update/upgrade commands. 

If your install of Thunderbird is the snap packaged version then it will not be updated when the other deb packaged software is updated. As regards Thunderbird extensions you may need to change some settings. Snap packaged applications a strictly confined. If we look up the snap application in Ubuntu Software we may find that the application page offers an option to change the permissions of the snap application.

Regards

---

### Post by Impavidus on 2022-10-16
When I upgraded to Xubuntu 22.04 on 14-7, I got Thunderbird version 91. On 5-10 this was upgraded to version 102. There were no intermediate upgrades, according to my logs.

For most applications, the version used for a particular Ubuntu release is frozen shortly before release of that Ubuntu version. Important bugfixes get backported, but you don't get new versions. For a few applications an exception is made. One of these is Thunderbird, but in Thunderbird's case there was (IIRC) some bug that prevented the new versions from being put in the Ubuntu repositories. It was recently fixed and a new version is now available. When a new version is available, it doesn't always get installed right away. When you install something new, you get the latest version from the repos and some dependencies may get upgraded too, but not the unrelated packages. They only get upgraded once a day or once a week or whenever you ask, depending on your settings, and with phased updates it may be delayed for a few more days. So I think that Thunderbird wasn't updated on your previous install because no upgrade was available.

On my 22.04 system, Firefox is a snap (which I'm beginning to dislike), but Thunderbird is still a deb.

---

### Post by TheFu on 2022-10-16
For not having thunderbird issues, there sure is a bunch of words about thunderbird.
BTW, since I patched my 20.04 desktop yesterday, thunderbird HAS been acting odd and looks different than before I patched.  It definitely is not running a snap version.

It did lots of research the last 45 minutes trying to figure out what changed in my setup to make it different.
It isn't a new version of Thunderbird.  The version used is over a week old - perhaps 10 days.
It isn't new nvidia drivers.
I looked through logs and saw that only the kernel update may have been related.  No GUI libraries or programs were updated.
My X/Server and drivers for it are from 2 August, so that hasn't changed.

There are 2 things I've noticed different in Thunderbird from before patching yesterday morning and after.
a) IMAP folder icons are more colorful.
b) IMAP folders that were removed from my "Favorites" perhaps 1-2 yrs ago had the "Favorites" toggle re-enabled.

That's it.  Toggling the favorites off removed those folders again.  

Email, Calendaring, address books are all working as expected otherwise. The system is stable. Thunderbird is stable. Neither has crashed recently.  I looked at the Thunderbird crash data and it hasn't crashed since June.   FYI, I don't usually reboot the system unless there is a new kernel, which happens every few weeks. The rest of the time, the system is up and running.

Thunderbird is running on a 20.04 desktop with FVMW as the WM. It is run inside a firejail environment to restrict where it can see and limit RAM abuse.
My workstation is running 18.04 server with FVMW as the WM.
I run thunderbird over a remote X11 connection using an ssh tunnel. I've been doing this for about a decade, so nothing new there.
Thunderbird connects to a local Zimbra server using standard protocols - IMAPS, CalDAVS, LDAPS. That has been working since 2008, though both Zimbra and Thunderbird have been updated all this time. They sorta "just work."

I'm at a loss for what changed, since the only thing related that might be connected is the new kernel.  I'm running 5.4.0-128-generic on both systems (18.04 HWE and 20.04 standard).

Sorry, I don't know what changed on my side.

---

### Post by #&amp;thj^% on 2022-10-16
> **inator-maker said:**
> tldr; i found that one program didn't update properly is it possible that others are not as well? 

There is what is called Phased-Updates, EG: [https://askubuntu.com/questions/1431940/what-are-phased-updates-and-why-does-ubuntu-use-them](https://askubuntu.com/questions/1431940/what-are-phased-updates-and-why-does-ubuntu-use-them)
I think the OP went a tad bit over explaining the difficulty with MS Office365

---

### Post by inator-maker on 2022-10-16
I can see the confusion.  I am on 22.04  


While trying to get my M365 account to sync with Thunderbird I was trying to install the lightning plugin.  I didn't see it the extensions and it wasn't coming up in search.  Wondering what the deal was I did some googling and saw that lightning was built into later versions.  I search what the currant version of Thunderbird is and I see that it is 10.3.3.  I was on 10.2.2.  After further troubleshooting this morning I see that there are two versions of Thunderbird.  Thunderbird Mail and Thunderbird. I apparently had Thunderbird Mail.  


I did run into the same issue with Lutirs.  Installing Lutris through the software store was giving me version 4.x, but current version is 5.x

---

### Post by inator-maker on 2022-10-16
I used Thunderbird as the example of how I came to conclusion programs were not updating as they should.  I also saw the same thing with Lutris.  I had version 4.x and current version is 5.x.  It also was not updating.  

For Thunderbird I found there are actually two different applications.  Thunderbird and Thunderbird mail.  I was using Mail which is v 10.2.2.    That, however, doesnt explain Lutris.

---

### Post by Impavidus on 2022-10-16
There are multiple ways to install packages. The classical way is using debs. This is what the apt command line tool and synaptic use. That will, on Ubuntu 22.04, give Thunderbird 102.2.2. For Lutris, the current version is 0.5.9.1. Another way to install applications, somewhat pushed in recent years but not very popular amongst the more experience forum users here, are snaps. They can be managed by the snap command line tool. The snap version of Thunderbird is at 102.3.3. The software centre or whatever its current name is will handle both types of packaging, without always being clear what method is used for the package you want to install. There are some more packaging methods.

To update the deb packages, you first run```
sudo apt update
```That will refresh the list of available software. Then run```
sudo apt upgrade
```which will download and install the packages. It can also be done using the GUI and with default settings you'll get a popup to tell you when updates are available. You can tune the settings if you like. You don't have to use the command line tools, but using them will teach you more about the internals of the system and helps to fix it if broken.

To update the snaps, you can use```
sudo snap refresh
```but that shouldn't be necessary, as these get updated automatically.

---

### Post by TheFu on 2022-10-16
I think someone else covered the LTS being stable and only getting bug fixes, not upgrades for most packages.  Thunderbird and Firefox get the latest version a few days or week after it is released, but most other programs only get security fixes so the interface, capabilities and features don't change during the life of the LTS release.  

If you want the newer versions of programs, which many companies do not, then for each of those programs either a PPA needs to be configured or some other latest package solution like flatpaks or snap packages.

Think about it this way. You are a company with 20,000 employees all working together, using exactly the same version of program X.  There are newer versions available, but those new versions add new features and change the data file contents slightly which may or may not be compatible with the old version.  You don't want any changes deployed to your users, so you've specifically decided to install Ubuntu LTS releases only.

If you want the latest and greatest of all programs, might I suggest Arch as the distro for you or some other "rolling release"?  Having the latest has some downsides, but until you try to use one of those and see those downsides for yourself, it just isn't the same as being told about them.
[https://www.zdnet.com/article/linux-distributions-rolling-releases-versus-point-releases-which-should-you-choose/](https://www.zdnet.com/article/linux-distributions-rolling-releases-versus-point-releases-which-should-you-choose/) has a discussion about both types of releases. There are some aspects that are worth considering for each choice.  Isn't it great that we have the choice?

---

