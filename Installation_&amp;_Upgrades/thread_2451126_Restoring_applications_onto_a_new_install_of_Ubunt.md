---
title: "Restoring applications onto a new install of Ubuntu"
date: 2020-09-27
forum: Installation &amp; Upgrades
---

### Post by stevecoh1 on 2020-09-27
I want to try to replace my hard drive with an SSD drive.  The computer store that was going to install the drive was unable to "ghost" the drive due to some error.  The computer would not boot off the new SSD afterwards. They said it was a disk error, but that may or may not be the case.  The laptop is a Thinkpad T-540P about six years old.  When I bought it from Lenovo it came with Windows 8 and I remember that there are all kinds of issues with getting Linux onto it.  I eventually "succeeded", with the complication that Windows was no longer accessible, which was fine by me.  Grub workedfor the Linux and I was okay with that.  This may possibly have something to do with the Ghost failure, but I'm not sure.  In any event, they put the HD back in and we've set up an appointment to try again this week.

Be that as it may, I want to move forward with the replacement of HD with SSD.  However, with Ghosting ruled out, the store is telling me that the only way to go is to put the SSD in, fresh, install a new Ubuntu and they copy my stuff over from the old HD.  That would be find for my /home /usr/local, /opt, etc. but what about my base of installed applications?  What I'd ideally like would be something that could produce a listing of the installed software in a format that could then be fed back through apt once the new drive is installed, reinstalling all the applications I now have.  If that isn't doable, what would be other ways of accomplishing the same thing?

Thanks

---

### Post by scorp123 on 2020-09-27
> **stevecoh1 said:**
>  What I'd ideally like would be something that could produce a listing of the installed software in a format that could then be fed back through apt once the new drive is installed, reinstalling all the applications I now have.

That functionality is built-in into "apt".

On your old installation, do:
```

 sudo dpkg --get-selections > packagelist.txt
```

and maybe also copy away these files, e.g. onto an USB stick:
```

/etc/apt/sources.list
/etc/apt/sources.list.d/*

```

Don't forget to copy them back onto your new installation.

Once you're on your new installation:
```

sudo dpkg --set-selections < packagelist.txt
sudo apt-get dselect-upgrade

```

=> Result should then be that your new installation has exactly the same packages and software that your old installation had. And if you copied away your /home and then also restored it, all your personal settings (e.g. bookmarks, mails, office document preferences, etc.) should be back too.

---

### Post by stevecoh1 on 2020-09-27
This looks like a winner!  Thanks.

---

### Post by TheFu on 2020-09-28
There is also apt-mark, but that depends on your use to set manually installed packages as manually installed and others as auto-installed. In my backup scripts where package lists are captured, I also store the method to restore:
```
`$aptmark showauto | tee $local_backup/apt-mark.auto`;
`$aptmark showmanual | tee $local_backup/apt-mark.manual`;
######[ to restore pkgs ]#######
### sudo apt-mark auto $(cat apt-mark.auto)
### sudo apt-mark manual $(cat apt-mark.manual)
### sudo apt-get -u dselect-upgrade

```
Some of the packages may not be found. That's because a new installation doesn't have any PPAs. You'll want to enable those from the list in /etc/apt/sources.d/ as needed. Often new releases include software that was only available via PPA, so re-enabling them all isn't necessary. I let the errors guide.

As for byte-for-byte cloning, there are a few challenges around that when the storage doesn't have the same sector size or starting block. There can be issues when GPT partition tables are used too, because the 2nd copy of the partition table is stored at the far end of the storage.  If the source and target storage devices aren't exactly the same size - bit for bit - then that 2nd copy won't be at the end of the new disk.  The 1st copy is at the beginning and there are tools to "fix" the 2nd copy, but most people don't bother to run them, so that 2nd copy is never created correctly.

Cloning storage brings some other problems for backup restores as well.  Suppose you need to move to completely new hardware, so none of the drivers match?  A bit-for-bit clone makes that harder, since port devices, numbers, and bus locations all change inside the new machine.

For a slight amount more hassle, we can have a bunch more flexibility for our restores, provided we backup the stuff needed to make that smooth. I used to use rsync for backups for a very long time.  But the time to backup kept getting longer and longer and longer. Eventually, I couldn't backup all the systems within the allowed backup window, so I searched for a faster backup that was faster, didn't slow down over time, supported multiple versions, selective installs, and could restore a system or 1 file quickly from 45 days ago.

For about a month, as I tried different backup tools, I was suffering with rsync + new tools. Eventually, it was clear which tool was fast, efficient, encrypted, versioned, easily (relatively) automated.  Next was the need to test the restore process. Because I stopped backing up the OS and installed applications, the backups saved about 4G-10G for each system.  Backups for systems without any data became just configuration file backups.  For example, our email gateway server has 180 versioned backups and used under 60MB of storage for all of that.  My desktops typically use less than 10G of backup storage for 90 days of versioned backups.  Audio and video files are not included in these versioned backups. Those get simple rsync mirrors.

All my restore steps begin by doing a fresh install of the OS I want onto new storage. For more details about restoring:
[https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986](https://ubuntuforums.org/showthread.php?t=2389631&p=13757986#post13757986)
A backup script: [https://ubuntuforums.org/showthread.php?t=2436006](https://ubuntuforums.org/showthread.php?t=2436006)

The only time I use bit-for-bit cloning anymore is when data recovery is needed.  It is just too inefficient otherwise for a number of reasons.

---

### Post by ubfan1 on 2020-09-28
If you still have the original installer list left in /var/log/installer/initial-status.gz , you can use that and apt-mark to produce the packages you installed with the below command:
comm -23 <(apt-mark showmanual | sort -u) <(gzip -dc /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort -u)
This eliminates the uninteresting things like tar updates.

---

### Post by stevecoh1 on 2020-09-28
This looks good, but are there any gotchas I need to know about?  I was recommended elsewhere to use apt-clone, but that complained about some non-standard packages.  I removed those, they weren't truly needed, and after I did so, I found that apt-clone just died without doing anything.  I realize that dpkg is more established software than app-clone, but there are a lot of options, some of which I might need to know about.

---

### Post by scorp123 on 2020-09-28
> **stevecoh1 said:**
> This looks good, but are there any gotchas I need to know about?

The method I mentioned above works 100%, I've used it many many times. The only "gotchas" you could run into are these:
[LIST]
[*]A package cannot be found on the new installation
[*]A package source is not trusted, you get complaints about missing GPG keys
[*]
[/LIST]

**A package cannot be found on the new installation:**

Most likely reason is that you forgot to restore a repository file underneath the **/etc/apt/sources.list.d/** directory. **How to fix:** Restore the repository file or check the software's instructions online on how to get its repository list again. Typical candidates are e.g. **Google Chrome** which loves to put its repository info into a file named **/etc/apt/sources.list.d/google-chrome.list** . If you forget to restore that file "apt" will complain that it does not know anything about the "google-chrome-stable" package you're trying to install.


**A package source is not trusted, you get complaints about missing GPG keys:**

Most likely reason is that you haven't told your new installation yet that it can trust that GPG key. Usually happens if you only restore repository files underneath  **/etc/apt/sources.list.d/** but not their keys. **How to fix:** write down the key "apt" is complaining about and then try if you can get your system to trust it again, try e.g.:

```

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys 123KEYAPTCOMPLAINEDABOUT4567890

```

Or check online if you can find the software's / repository's instructions again on how to add their repo keys. Typical candidates are e.g. Google Chrome, Oracle Virtualbox (when installed from their repository), commercial software such as Teamviewer or AnyDesk which have their own keys and own repositories, Ubuntu PPA's, third-party app repositories that are not in the default repositories, and so on.

In many cases you can simply ignore the complaints about missing keys and install the software anyway.

Because of this I have developed the habit to edit any non-standard repository file and write down how I got the GPG key. E.g. this is how my Oracle Virtualbox repository file for Ubuntu 18.04 looks like:
```

# Add the key:
#
# wget -q https://www.virtualbox.org/download/oracle_vbox_2016.asc -O- | sudo apt-key add -
# wget -q https://www.virtualbox.org/download/oracle_vbox.asc -O- | sudo apt-key add -
#
#
deb [arch=amd64] http://download.virtualbox.org/virtualbox/debian bionic contrib

```

Or for commercial software that I use such as AnyDesk:
```

#
# http://deb.anydesk.com/howto.html
#
# wget -qO - https://keys.anydesk.com/repos/DEB-GPG-KEY | apt-key add -
#
deb http://deb.anydesk.com/ all main

```

So if for some reason I were to clone my system the way I described above and restore my repository files, I'd most likely run into GPG errors because on my new installation "apt" will not know these keys yet. Easy fix: I just need to look at the comments again I left behind in those repo files....

But that's just me, you can do fine without it, e.g. a quick Google search "gpg keys for software XYZ" would tell you the same thing. I'm just lazy and skipping that step.

If you stick to the default repositories that belong to Ubuntu (e.g. partner, universe, multiverse, etc.) you should not have these kinds of problems at all, because your new installation will definitely know those default repositories and how to restore the packages from there.

---

### Post by TheFu on 2020-09-28
I have some simple rules about dpkg use.  
Use it to gather information only, not to modify things.  For modification, there are better answers.

---

