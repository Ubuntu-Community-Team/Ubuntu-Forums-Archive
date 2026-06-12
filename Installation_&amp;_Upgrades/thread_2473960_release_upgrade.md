---
title: "release upgrade"
date: 2022-04-19
forum: Installation &amp; Upgrades
---

### Post by coley9225 on 2022-04-19
Hello all. I'm putting together a game plan to upgrade my lubuntu 20.04.4 to 22.04,but I have a couple of questions first. My overall plan, at this point, is to run the following commands:
```
sudo apt update
sudo apt full-upgrade -y
sudo reboot
sudo apt auto-remove
sudo apt do-release-upgrade

```

My first question is, is this the proper procedure?
I plan to do full backup(with timeshift) of my current install, full backup of my /home patition with back-in-time, and a copy of my important files, all to external hdd. I am going to disconnect external drive during upgrade.
I keep a current copy of apt-mark showmanual in my home dir, So I can reinstall apps if need be.
Does this look like a good method to use, or should I run in a different direction?
Does the release upgrade do anything to the grub install? When I install a linux distrro, I MUST do it without a bootloader, and if install is on a fresh drive, then bootrepair to install grub, My computer will not allow grub to install for some reason, I would prefer to avoid this issue if I can.
If I do the release upgrade and things go south, can I use a live usb with timeshift and restore my system to a working state?
I want o make sure I have all my squirrels in the same tree before I do this, probably this weekend. If all goes horribly wrong, I will just do fresh install, and leave my home partition formatted, and cross my fingers. Any advise or insight would be greatly appreciated.
P.S. My current set up is a Lenovo ideapad 320 laptop, 1.1 gig processor, on-board graphics, 8 GB ddr3 memory, 1 TB ssd, lubuntu 20.04.4 single boot. Thanks in advance.

---

### Post by deadflowr on 2022-04-19
> My first question is, is this the proper procedure?
No.
The first two, yes,
but switch reboot and autoremove (yes it's one word autoremove, no hyphen)
and it's simply do-release-upgrade, no apt, and also no sudo required.
So it should look like this
```
sudo apt update
sudo apt full-upgrade -y
sudo apt autoremove
sudo reboot
do-release-upgrade
```
But beyond that, upgrades from 20..04 to 22.04 are not officially available yet and will not be until August.
(This is right around the time of the first point release for 22.04.)

There is a way to get it to upgrade sooner and that is to use the -d flag in the do-release-upgrade command
Like
```
do-release-upgrade -d
```
The -d flag means development, typically used when the release to be upgraded to is still under development.
Technically, this is correct for the 20.04 to 22.04 upgrade as this specific upgrade is still considered to be under development.

I have no comment on the backup strategy beyond that it seems like with both timeshift and backintime you should at least be able to revert back to 20.04 easily.
Which I think is probably the point of those snapshot backup utilities

> Does the release upgrade do anything to the grub install? When I install a linux distrro, I MUST do it without a bootloader, and if install is on a fresh drive, then bootrepair to install grub, My computer will not allow grub to install for some reason, I would prefer to avoid this issue if I can.
I do not know.
That's just plain weird, maybe boot-info summary could shed some light on why that is.

---

### Post by coley9225 on 2022-04-19
Thanks deadflowr, I have made the noted changes in my backup plan. As far as the bootloader problem, I fought it for ~2 years until I found a post about installing the file system without the grub package. With any install, I install file system, install and run boot-repair before rebooting, then have to purge and reinstall grub to eliminate all the error messages. I started with lubuntu 18.04, and to this day, can't find an explanation for the issue. If I'm installing an additional distro alongside lubuntu, I don't run boot repair, just boot to lubuntu and update grub. That's the part I was most interested in avoiding, if possible, was fighting the grub install part. If push were to become shove, I am willing to do fresh install(may do anyway, just to clean out everything) and keep my /home partition intact. Thanks again, all of you guys on these forums are great, and don't get thanked enough for sharing your knowledge and experience with those of use with less skill.

---

### Post by GhX6GZMB on 2022-04-19
Another case of someone suffering from "upgradeitis". If your 20.04 runs, leave it be until at least the 22.04.1 LTS is out.

You seem to have another serious problem that should be solved first (grub).

---

### Post by coley9225 on 2022-04-19
Thanks ml9104. My current system is running great, and based on what deadflowr said about it still being 'developmental', I will probably wait until 22.04.1 hits. I did download 22.04 daily build and made live usb with persistence, so I can "test drive" it before doing any release upgrade.
Any suggestions on where to start looking for my grub issue? I have a large amount of allocated space on ssd, so a full install of a new distro is an option, if that will be find the issues with grub. Another 'quirk' of my laptop, I have to show grub menu as I have tried everything I can find to access uefi settings, and can't with out that option in grub menu. No key combo works. I guess the lenovo ideapad 320 just isn't very user friendly. Thanks

---

### Post by deadflowr on 2022-04-19
> Any suggestions on where to start looking for my grub issue?
I posted you should run the boot-info from boot-repair which will give a basic summary of what's going on, 
It should give information about hard drives and any the  common boot settings.
[https://help.ubuntu.com/community/Boot-Info]("https://help.ubuntu.com/community/Boot-Info")
And while I'm pushing out diagnostic tools you might take a look at the ubuntuforums system info script here:
[https://github.com/UbuntuForums/system-info]("https://github.com/UbuntuForums/system-info")
Not that it will be helpful, but it too, might shed more light on the issue.

---

### Post by grahammechanical on 2022-04-19
During the period of life support of Ubuntu and its flavours an update/upgrade may upgrade the version of Grub more than once. An online upgrade of 20.04 to 22.04 will replace the 20.04 version of Grub with the 22.04 version of Grub. I do not see how this is different from Grub being upgraded during an update/upgrade.

Of course, the only way to find out in your case is to do the upgrade in the course of time.

Regards

---

### Post by coley9225 on 2022-04-19
Thanks guys. I think I will try to do a full install of a disto(maybe kubuntu, or even 22.04 daily build) in next couple days. If the install errors out trying to install grub, I'll go back to my work around, install w/o bootloader and run boot repair. I'll post the pastbin link in a new thread, since it's a little off topic for this one. Hopefully, someone with more knowledge than I have can shed some light on the matter. As I said, the work around does work fine, I get a grub menu at every reboot, it's just a royal pain in the southern regions.

---

### Post by guiverc on 2022-04-19
I'm not sure I can add much, however I'll add the following

Lubuntu's upgrade documentation can be found here, where you'll note it pretty much matches what you've done/documented.

- [https://manual.lubuntu.me/stable/D/upgrading.html](https://manual.lubuntu.me/stable/D/upgrading.html)

I'll provide the following, though you may **not** find it helpful (it lists two ways of upgrade without reason why you'd use either; it's for team use really)

- [https://phab.lubuntu.me/w/release-team/testing-checklist/](https://phab.lubuntu.me/w/release-team/testing-checklist/)

I'd suggest reading all documentation on release prior to upgrade; as all issues we experienced during QA (*Quality Assurance*) that we felt were important, get documented there. If they impact all *flavors* the issues are generally only documented in the Ubuntu specific notes, which is why we provide links to that page.  Lubuntu is mentioned in the main Ubuntu *jammy upgrade* notes, though it's little more than a link to the page I've provided here if I recall correctly ([https://help.ubuntu.com/community/JammyUpgrades](https://help.ubuntu.com/community/JammyUpgrades))

There is a pretty significant change to `grub` in upgrades to 22.04/*jammy* , as it was a first issue listed on our [tracker]("https://discourse.lubuntu.me/t/lubuntu-jammy-jellyfish-22-04-issue-tracker/3101") , so *release-upgrades* can cause issues that normal *dist-upgrades* do not experience with the change of releases, however that issue was deemed solved some time ago & no longer appears at in the top of our tracker (*first post in provided link, the wiki bit*)

Be aware the upgrade from 20.04 to 22.04 does **not**get opened until **after** the release of Ubuntu 22.04.1 LTS, so the `-d` option mentioned in the Lubuntu testing checklist will be required if you want to *release-upgrade* before that time; upgrades from 21.10 to 22.04 open **after** the release of Ubuntu 22.04 LTS (*usually early the following week*) but it's ~three months before upgrades from 20.04 LTS will be opened.

I'm not the *primary* QA-tester of upgrades; however the few problems we've experienced have been resolved, and I experienced no issues on my own *upgrades*.

(FYI:  When I'm using the *plural* such as We; I'm referring to the Lubuntu (*or Ubuntu*) team)

---

### Post by ActionParsnip on 2022-04-20
[https://computingforgeeks.com/upgrade-from-ubuntu-focal-fossa-to-ubuntu-jammy-jellyfish/](https://computingforgeeks.com/upgrade-from-ubuntu-focal-fossa-to-ubuntu-jammy-jellyfish/)

Remember to do a full backup of your important data before starting and do a test restore so you know it is good. This will protect your data

---

### Post by coley9225 on 2022-04-20
Thanks everyone. After a very frustrating 4 hours, I was able to install lubuntu 22.04. The install failed, couldn't install grub. Ran boot-repair and uploaded boot info summary to pastebin:  [https://paste.ubuntu.com/p/kg8zGsN9sb/](https://paste.ubuntu.com/p/kg8zGsN9sb/)
I ran the installer again, install system only, and the install completed. On both attempts, I marked efi partition to keep, no format. I rebooted and got a grub prompt. I had to remove ssd, reboot to live usb, reinstall ssd, and run boot-repair with recommend repair to get grub back. That summary is at  [https://paste.ubuntu.com/p/Wvf5QQYpsn/](https://paste.ubuntu.com/p/Wvf5QQYpsn/)
I also ran the system info script, that report is at  [https://paste.ubuntu.com/p/pPPqwqswDY/](https://paste.ubuntu.com/p/pPPqwqswDY/)
I fear that an in place upgrade may not be the best option for my case. I may configure 22.04 to be as close as possible to my 20.04 install, and see how it runs. If it works as well as 20.04, then I'll keep 20.04 around as an emergency fall back system and run the newer install as my daily os. Any tips on where to turn  to resolve the grub install failure would be appreciated., as that would make it a much easier process to test other distros. I don't understand why the installer is unable to install grub, but boot-repair can...just seems strange to me. Anyway, thanks again for all the help.

---

