---
title: "HELP! Screwed up my working version. Now cli only!"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by Mugsy323 on 2010-10-02
**Help!** I really screwed up (I'm using the LiveCD at the moment, though I also have Windows.)

I have two installations of Ubuntu 10.04. I have (had?) the 32bit version on a Flash drive that I take with me on the job, and the 64bit version on an external hard drive at home for personal use.

(Note, I'm a pro at Windows, but when it comes to Linux, I'm still pretty remedial.)

My 32bit version was running dog slow, so I thought I could speed things up by deleting what seemed to be old installations of Ubuntu... you know, all the old kernal choices you get on the Grub menu when booting? I had several (thinking I was smart, I simply *Moved* the files to another hard drive in case I needed to put them back.) The files in question: all the "redundant" files inside /usr/lib/libgconf2-4".

Removing the files did not remove them from the Grub boot menu, and instead prevented Ubu from loading, resulting in a warning message on a black screen that says "the configuration files for gnome-power-manager were installed incorrectly".

So I booted my 64bit version of Ubu, logged in as root, and tried to MOVE the files back to their original location. But I goofed and accidentally overwrote the 32bit "libgconf2-4" files onto my 64bit installation! Now, neither will boot, giving me the same black screen error.

Using "Recovery Mode" (THAT'S a joke), I tried to repair the installation, but it failed. I can get to the CLI, and can even get online using "pppoeconf", but no GUI.

I tried to uninstall/reinstall "gnome-power-manager" using apt-get, but it won't uninstall (even using --purge) and keeps telling me I "already have the latest version" when I try to reinstall.

Somehow, I need to force a repair/reinstall of "gnome-power-manager" from the CLI. Any help is appreciated.

---

### Post by kotnik on 2010-10-02
dpkg -P gnome-power-manager

Afterwards install it with apt-get install.

But, since you're not yet versioned in repairing borked systems, I'd suggest you backup your /home directory and reinstall Ubuntu. If you kept your stuff in your home directory, that'd be fine. YMMV.

---

### Post by Mugsy323 on 2010-10-02
> **kotnik said:**
> dpkg -P gnome-power-manager

Afterwards install it with apt-get install.
Thanks for the quick reply (sorry for my slow response).

Unfortunately, that didn't work. I get a near-endless stream of:

```
dpkg: warning: files list file for package '(different program on every line)' missing. ...
```
If I wait it out, eventually it tries and fails to complete the installation. Apparently, there is something wrong with the following packages:

samba-common
clamav-base
smbclient
ubuntu-desktop
samba-common-bin
winbind
clamav-freshclam

Before everything went to hell, I had tried to do a Symantic Update, which reported a bunch of errors for these same programs and refused to update... disabling things like the Flash-plugin, which was included in the update. This is what started me down the path of trying to clear things out to get the update to work.

I also tried "sudo apt-get install ubuntu-desktop" from the CLI, to no avail.

When I try to get Recovery Mode to fix the packages, it reports

```
"dpkg error - dependency problems. ...
```

If I have to, I can always reformat and reinstall 32bit Ubu on the (32GB) Flash Drive as there wasn't anything important on it, but I'd hate to lose my 64bit install at home.

Any ideas? TIA.

---

### Post by oldfred on 2010-10-03
If you can still get to command line try a full set of updates or chroot into your system and run the updates.

If command line then use sudo -i to get into sudo mode
Commands once in chroot:
#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop

---

### Post by Mugsy323 on 2010-10-03
> **oldfred said:**
> If you can still get to command line try a full set of updates or chroot into your system and run the updates.

If command line then use sudo -i to get into sudo mode
Commands once in chroot:
#Then run whatever other commands needed - no sudo needed (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
...

Sorry for the late reply. I spent the day "fixing" the problem, and found a "solution" before I saw your post.

Writing the 32bit Thumb-drive installation off as a lost cause, and not containing anything terribly important, I got the clever idea to reformat and install the same version (the 64bit) of Ubu on the Flash-drive, then overwrite the files I screwed up on my home/64bit drive from "root" with the proper version from the Flash-drive.

I then booted the drive with my screwed-up installation into Recovery mode and told it to do a dpkg fix. It worked.

I lost one installation in the process (my old 32bit installation on the Flash drive), but I'm just glad to have my main home installation working again.

Big thanks for the help.

---

### Post by Mugsy323 on 2010-10-03
> **oldfred said:**
> If you can still get to command line try a full set of updates or chroot into your system and run the updates.
Hmmm. Seems I wasn't as clever as I thought. While I now have the desktop back up and running again, "gnome-power-manager" is still screwed up (part of the files I replaced). This means no printer (USB) is being detected, and most of my toolbar icons, like the connection manager, are missing.

Trying to use Synaptic and marking GPM for "Complete Removal" reports:

```
E: gnome-power-manager: Package is in a very bad inconsistent state
- you should  reinstall it before attempting a removal.
```

When I try mark GPM for Reinstallation, I get:

```
E: /var/cache/apt/archives/gnome-power-manager_2.30.0-0ubuntu1_amd64.deb: subprocess
new post-removal script returned error exit status 1
```

...an error that directs me to /var/cache/apt/archives, where I find several uninstalled packages. Deleting them makes no difference.

Trying to fix the installation from Recovery Mode reports the same errors, plus mention of a corrupt or invalid XML file(?)

I'll try your previous instructions next to see if they fix the problem. In the meantime, I'm switching this back to "unsolved". :(

Thanks.

---

### Post by Mugsy323 on 2010-10-04
> **oldfred said:**
> #houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean[COLOR="Red"][/COLOR]
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
...
Unfortunately, this didn't work. "Autoclean" made some changes, "clean" after that did nothing (immediately returning to prompt), "update" recognizes all the packages that have failed to install and redownloads then, but then I get a slew of errors and nothing updates.

I don't remember all the errors reported (too many), but I do remember something about "wrong ELF class: ELFCLASS32" [COLOR="Red"](Failed to access configuration source(s): Failed: Error opening module `xml': /usr/lib/libgconf2-4/2/libgconfbackend-xml.so: wrong ELF class: ELFCLASS32)[/COLOR]

Is there a way to record the error messages to a file that I can upload here?

Thanks.

---

### Post by Mugsy323 on 2010-10-04
By attempting an update from the terminal, I was able to copy all the output from an update:

First, I show which version of Ubuntu I'm running: the 32bit x86 version on a 64bit cpu. Notice all the files appear to be coming from 64bit repositories:
```
$ uname -m
x86_64

$ sudo apt-get update
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429) lucid Release.gpg
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)/ lucid/main Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)/ lucid/restricted Translation-en_US
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429) lucid Release
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429) lucid/main Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429) lucid/restricted Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429) lucid/main Packages
Ign cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429) lucid/restricted Packages
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429) lucid/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429) lucid/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit http://security.ubuntu.com lucid-security Release.gpg                      
Ign http://security.ubuntu.com/ubuntu/ lucid-security/main Translation-en_US   
Hit http://archive.canonical.com lucid Release.gpg                   
Ign http://archive.canonical.com/ubuntu/ lucid/partner Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/main Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/restricted Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/universe Translation-en_US
Ign http://security.ubuntu.com/ubuntu/ lucid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com lucid-security Release
Hit http://archive.canonical.com lucid Release 
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid-updates Release.gpg
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com/ubuntu/ lucid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com lucid Release 
Hit http://archive.canonical.com lucid/partner Packages                        
Hit http://security.ubuntu.com lucid-security/main Packages          
Hit http://us.archive.ubuntu.com lucid-updates Release
Hit http://security.ubuntu.com lucid-security/restricted Packages
Hit http://security.ubuntu.com lucid-security/main Sources
Hit http://security.ubuntu.com lucid-security/restricted Sources
Hit http://security.ubuntu.com lucid-security/universe Packages
Hit http://us.archive.ubuntu.com lucid/main Packages
Hit http://us.archive.ubuntu.com lucid/restricted Packages
Hit http://us.archive.ubuntu.com lucid/main Sources
Hit http://us.archive.ubuntu.com lucid/restricted Sources
Hit http://us.archive.ubuntu.com lucid/universe Packages
Hit http://us.archive.ubuntu.com lucid/universe Sources
Hit http://security.ubuntu.com lucid-security/universe Sources
Hit http://security.ubuntu.com lucid-security/multiverse Packages
Hit http://security.ubuntu.com lucid-security/multiverse Sources
Hit http://us.archive.ubuntu.com lucid/multiverse Packages
Hit http://us.archive.ubuntu.com lucid/multiverse Sources
Hit http://us.archive.ubuntu.com lucid-updates/main Packages
Hit http://us.archive.ubuntu.com lucid-updates/restricted Packages
Hit http://us.archive.ubuntu.com lucid-updates/main Sources
Hit http://us.archive.ubuntu.com lucid-updates/restricted Sources
Hit http://us.archive.ubuntu.com lucid-updates/universe Packages
Hit http://us.archive.ubuntu.com lucid-updates/universe Sources
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com lucid-updates/multiverse Sources
W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)/dists/lucid/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release amd64 (20100429)/dists/lucid/restricted/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.
```
Any ideas on how to fix this?

---

### Post by oldfred on 2010-10-04
Did you somehow copy from the 64 bit install some files that then made the 32 bit install think it is the 64 bit version and now you have a mixed system? There probably is a way to uninstall and reinstall but I do not know.

---

### Post by Mugsy323 on 2010-10-04
> **oldfred said:**
> Did you somehow copy from the 64 bit install some files that then made the 32 bit install think it is the 64 bit version and now you have a mixed system? There probably is a way to uninstall and reinstall but I do not know.
Yes. As noted above, I accidentally overwrote some key system files from my 64bit system over files on my 32bit system thinking I was copying them back to the same drive.

I was able to get the GUI back up and running again by overwriting the files I mistakenly replaced with fresh copies from another 32bit install. But apparently, somewhere along the line, the system thought it was now a 64bit install, and now nothing will update. :(

I would do a reinstall if I didn't have so much to lose.

(Note to Ubuntu: Until Ubuntu can fix itself via a non-destructive "repair install" the way Windows can w/o losing anything, Ubuntu will never replace Windows as a serious operating system. I say this in hopes this won't always be the case.)

---

