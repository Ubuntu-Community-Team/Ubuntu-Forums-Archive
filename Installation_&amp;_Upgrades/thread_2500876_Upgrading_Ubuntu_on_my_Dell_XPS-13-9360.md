---
title: "Upgrading Ubuntu on my Dell XPS-13-9360"
date: 2024-09-14
forum: Installation &amp; Upgrades
---

### Post by rudy5 on 2024-09-14
Hi Friends,

I've been struggling with this for a few years now: I'm stuck on Ubuntu 18.04 LTS on my laptop, must have missed the last-chance-to-upgrade window a few years ago, but can't do it.

I've searched the web, incl. this forum, & went down numerous rabbit holes before encountering a new obstacle, usually, the " .. . now THIS will happen, and then you .. ." didn't match what was happening on my computer. I'm probably out of my depth. 

So .. . I'm wondering if THIS approach might work: 

1. Copy the contents of my home directory onto an external medium.

2. Do a fresh install of 24.04. [ Will that be compatible with my slightly older XPS-13? ]

3. Copy the backed up home directory onto the new install.

4. Proceed to cleaning up the problems, anticipated & otherwise, on the new install.

Am I insane? Is there a better way? 

 --- Rudy

---

### Post by Dennis N on 2024-09-14
It may still upgrade without needing a new OS installation. On my 18.04 LTS, I get an offer to upgrade:
```
dmn@Tyana:~$ do-release-upgrade -c
Checking for a new Ubuntu release
New release '20.04.6 LTS' available.
Run 'do-release-upgrade' to upgrade to it.

```
Run the same command as above, and do you get the same message? If so, try the command suggested in the output with sudo and see if it works.

Note: I am running an  Ubuntu 18.04 LTS with Ubuntu Pro support, which lasts until 2028. I have no plans to upgrade. That is another option.

---

### Post by rudy5 on 2024-09-15
Thanks, Dennis.  Entering the command you suggested, I got "New release 20.04.05 is available," but when I ran do-release-upgrade, this error message was generated:

"Please install all available updates for your release before upgrading."

Suggestion?

---

### Post by rudy5 on 2024-09-16
I should have mentioned that the path of installing available updates  led down another series of rabbit holes, generating such error messages  as:

"Error: Broken Count >0. This usually means that your installed packages have unmet dependencies." and

"xxx is configured multiple times." and

"The package system is broken." and

"Could not open lock file /var/lib/dpkg/lock-frontend" and (running apt-get install -f) 

"Unable  to fetch, try running apt-get or apt-get --fix-missing" and (running  sudo do-release-upgrade -c, & finding 20.04.05 LTS on a repository)

"Run do-release upgrade to upgrade to it" (which I do, and which generates)

"Please install all available updates for your release before upgrading."

Sounds  like my old install is messy, & in fact so messy it can't be  upgraded .. .? Anyway, I'm trying to cut across all this trial and error  that keeps bringing me back to the Universal Error Message 000000001 :  "**** ain't working."

So back to my original question in this  thread: Can I leave this Groundhog Day troubleshooting behind, save my  data as described, and do a fresh Linux install?

---

### Post by rudy5 on 2024-09-18
Well, I'm gonna try it anyway. Wish me luck.

I have been using  Linux systems continuously since 2004 (home) / 2005 (work), and have  almost all my data, including e-mail history, saved. I want to stay on  that path. But my formerly bullet-proof Ubuntu installs (since ca 2008)  have become more unstable since 2018, and various websites and streaming  services I would like to subscribe to aren't working.

My  hesitation is that I tried this approach on my work Ubuntu machine, and  now the upgrade path on that one is (differently) bricked!

---

### Post by rudy5 on 2024-09-23
I've now spend the last 4 days struggling to implement this plan, which is to do a completely fresh install of Ubuntu 24.04 on this Dell XPS-13-9360. I would like however to be able to keep my data.

True or false: I can copy my entire HOME folder to an external drive; install the new OS; copy my saved HOME folder onto the new installation; and have my historical data. Yes? No?

A critical piece of data that I would very much like to keep is my e-mail history. In the past, I've been able to copy my Thunderbird profile onto an external drive, and copy that profile onto a new instance of Thunderbird. However, I can't seem to do that this time, for the following reason:

Unable to copy the profile folder. Instead, an error message: "Error while copying "lock" "
- Filesystem does not support symbolic links.

Neither dragging & dropping; cut-and-paste to the external drive; nor the command line cp command is able to copy my files.

What am I looking at here? I'd rather not have to throw away 13 years of e-mail history.

My Thunderbird is version 91.5.0. It lacks an export filter. I am not able to upgrade my Thunderbird to a version that does. This is one of the reasons I'd like to get off this broken 18.04 install.

---

### Post by oldfred on 2024-09-23
New installs now use snaps for Firefox & Thunderbird.
I uninstall snaps & install the .debs. Then structure is same as it was.
Often a lock is from system being open, or shutdown incorrectly when open so lock file still there.

You also have to reset priorities as shown or it will reinstall the Firefox or Thunderbird snap. 22.04 instructions same for 24.04
[https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04](https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04)
[https://www.omgubuntu.co.uk/2024/08/install-thunderbird-deb-not-snap-in-ubuntu-24-04](https://www.omgubuntu.co.uk/2024/08/install-thunderbird-deb-not-snap-in-ubuntu-24-04)

apt info thunderbird
[https://ubuntuhandbook.org/index.php/2024/03/install-thunderbird-deb-ubuntu-2404/](https://ubuntuhandbook.org/index.php/2024/03/install-thunderbird-deb-ubuntu-2404/)
[https://askubuntu.com/questions/1280707/how-to-uninstall-snap](https://askubuntu.com/questions/1280707/how-to-uninstall-snap)

[https://askubuntu.com/questions/1399383/how-to-install-firefox-as-a-traditional-deb-package-without-snap-in-ubuntu-22](https://askubuntu.com/questions/1399383/how-to-install-firefox-as-a-traditional-deb-package-without-snap-in-ubuntu-22)

---

### Post by rudy5 on 2024-09-24
Thanks. oldfred. I've now looked at the links you provided. They are all about upgrading Thunderbird *on* 22.04. But I'm not on 22.04, I'm running 18.04. I don't know what snap is, I don't know what DEB is, I don't know what the difference is, and I don't know what the effect on my over-all installation is if I change the upgrade method. It also feels like an overly complicated way of dealing with this problem, which at this point is just an obstacle that I'm more interested in MOVING PAST, than I am in understanding & repairing.

Is it possible to

(a) make a copy of my home directory to an external drive;
(b) install a fresh instance of 22.04; and
(c) copy my saved home directly back onto the hard drive?

---

### Post by oldfred on 2024-09-24
Backup should include /home, list of installed apps to make it easier to reinstall any you have added, and perhaps /etc, if you have modified any system files. I edit grub, but copy into /home so that is backed up & easily restored.
If you installed any server type apps like database, web etc, you need to back those up separately.

Backup should be a regular process and to multiple places.
discussion of alternatives/strategy backups
[https://ubuntuforums.org/showthread.php?t=2465713](https://ubuntuforums.org/showthread.php?t=2465713)
[https://ubuntuforums.org/showthread.php?t=2368992](https://ubuntuforums.org/showthread.php?t=2368992)[[://ubuntuforums.org/showthread.php?t=2368992&p=13677224#post13677224|&p=13677224#post13677224]]
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem) & 
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)


.deb is the standard was an app is distributed for Debian based systems like Ubuntu.
But Ubuntu now also uses snaps for some apps and is converting more to snaps with every release.

Older but has some info on snaps
[https://itsfoss.com/use-snap-packages-ubuntu-16-04/](https://itsfoss.com/use-snap-packages-ubuntu-16-04/)

---

### Post by rudy5 on 2024-09-25
Hi Oldfred,

Thank you for your detailed and help-filled response to my question. I am using only a limited number of apps here, & all of them pretty basic / part of the installation (e.g., Libre Office, Firefox, Thunderbird, Gimp). Never mod'd any system-level files, nor GRUB, & I don't run any cloud-based stuff. So it should be fairly straightforward, eh?

Wish me luck! Probably won't be until the weekend now before I can block out the time to do this with the proper care &c. And I will report back to the forum.

---

### Post by rudy5 on 2024-10-15
Hi all, I'm back. Unf., none of these pathways offered has led me out of my trapped situation. I'm wondering if re-stating my question(s) might help.

I have a Thunderbird profile in my /home/.thunderbird folder, let's just call it tbirdprofile.default. I want to copy tbirdprofile.default to an external drive, a USB drive set up for the purposes; let's call it "target".

Dragging and dropping won't do. My (admittedly rickety) Ubuntu 18.04 install cannot do the drag and drop --- an issue with symbolic links, that I haven't been able to find a work-around for. It'll copy over the name of the folder, but none of the contents.

Solution:terminal  command line, right? However, I have not been able to stumble my way to the right string of alphanumeric characters entered at the command line to do this. Admittedly, I'm not a command line master, though it often enough to work around this or that obstacle. 

Could somebody please to the enormous favour of typing out the exact command that I need to enter from my command line (home directory) to do this? Folder, all contents.

rudy@rudy-XPS-13-9360:~$          [ from there, please! ]

Much obliged if anyone can yelp!

---

### Post by rudy5 on 2024-10-15
Meanwhile, I'm also trying to make a copy of my entire /home folder onto my external USB drive. 

A few weeks ago, I was able to copy *most* of that folder using this command in terminal:

:$ sudo cp -prv /home /media/rudy/TARGET

.. . which threw up a handful of error messages ("Cannot create regular file", "Error writing downloads/factory_image_iso"). When copying completed, 2 more error messages:

cannot create symbolic link /media/rudy/TARGET/home/rudy/snap/zoom-client/current 
and
failed to preserve ownership for /media/rudy/TARGET/home: operation not permitted

When I examined file properties, I saw that /home on my hard drive was 76,902 items / 26.3gb; but only 73,453 items / 25.0 gb had copied over. Didn't give me a whole lot of confidence that my folder was effectively copied.

I have since gone through downloads and deleted any .iso's that were there. Today I tried the same copying command, with an alarmingly different result:

Terminal seemed to show the copying taking place. No error messages were displayed. After (seemingly) completing the copy, the command line prompt re-appeared. All seemed to have gone well this time 

.. . until I looked at the file properties. 

The TARGET drive is empty. There are no files on it. There are a couple of other baffling aspects to it 

-- the TARGET folder is EMPTY.
-- "Used" = 16.4 gb
-- "Free" = 31.3 gb 

.. . but it's a 32gb drive .. .? What is the 16.4gb of files that isn't showing up in the file manager?

Entering ls at the command line shows my "rudy" folder, but with no contents, on the TARGET USB drive.

Thanks for help, & for bearing with my frustration / confusion. Sigh. All I want to do is make a copy of my /home folder on an external drive; install a fresh instance of 22.04; and copy my data back over. 

The old 18.04 OS is broken, & needs to be paved over. I just want to save my data!

---

### Post by oldfred on 2024-10-15
What format is TARGET?
lsblk -e 7 -o name,fstype,size,fsused,label,UUID,mountpoint

---

