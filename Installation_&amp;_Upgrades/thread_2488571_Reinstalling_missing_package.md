---
title: "Reinstalling missing package?"
date: 2023-07-09
forum: Installation &amp; Upgrades
---

### Post by James Fitzpatrick on 2023-07-09
First of all, I'm NOT a computer saavy person, so any help will have to be explained to me in the simplest terms.

I can't install any updates because whenever I check the software updater, a message says: "Update manager crashed with apt_pkg.Error in open():E:The package linux-headers 5.15.0-53-generic needs to be reinstalled, but I can't find an archive for it"

What do I do?

---

### Post by TheFu on 2023-07-09
So, first you'll want to open a terminal and run these commands:

```
sudo apt update && sudo apt upgrade
```
Post the commands and output back here ... not all the output. We don't need to see 50 lines that show downloading updates worked.  We need to see when a new sub-task happens and if there are issues in that subtask.

Select and paste the terminal output here and wrap it all with 'code tags'.  Make it easy for people to help and they will. Make it difficult and they won't.

---

### Post by Rubi1200 on 2023-07-09
In essence, just copy and post here if there are errors from the above command asked for by TheFu

To use code tags, click on Go Advanced when you reply and look for the # icon and paste the content between the tags.

Please also post the content of these 2 commands:

```
lsb_release -a
```

and also

```
cat /etc/apt/sources.list
```

Thanks.

---

### Post by James Fitzpatrick on 2023-07-10
Thanks.  Here's what I got:

```
$ sudo apt update && sudo apt upgrade
[sudo] password for james: 
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security InRelease [110 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy-updates InRelease [119 kB] 
```

Then (after 61 other 'gets':

```
Fetched 8,660 kB in 5s (1,642 kB/s)               
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
426 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: The package linux-headers-5.15.0-53-generic needs to be reinstalled, but I can't find an archive for it.
```


```
$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy restricted main
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy-updates restricted main
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy-backports restricted universe multiverse main
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security restricted main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
```
```
james@james-Compaq-Presario-CQ60-Notebook-PC:~$ 
$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 18.04 LTS _Bionic Beaver_ - Release amd64 (20180426)]/ bionic main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy restricted main
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy-updates restricted main
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy-updates universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy-updates multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) jammy-backports restricted universe multiverse main
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) bionic-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security restricted main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jammy-security multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security multiverse
james@james-Compaq-Presario-CQ60-Notebook-PC:~$

```

I'm not getting anything for the command, cat /etc/apt/sources.list

---

### Post by TheFu on 2023-07-10
**_Standard support for 18.04 ended._**

If you've signed up for ESM support, then the sources.d/ and other repository files would have been updated to point to new locations and your credentials will be used to access those locations.

At this point, it is difficult to perform an OS upgrade, so a fresh install of 20.04 or 22.04 is required.  Had you performed the upgrade 2 months ago, it could have worked, maybe.  Always upgrade releases BEFORE support ends.

---

### Post by James Fitzpatrick on 2023-07-10
I'm running 22.04, and I've been very prompt with my updates.

---

### Post by ian-weisser on 2023-07-10
You are about to become computer-savvy. This is how you fix the error.

1. Go to [https://packages.ubuntu.com/focal/linux-headers-5.15.0-53-generic](https://packages.ubuntu.com/focal/linux-headers-5.15.0-53-generic)

2. Figure out how to download the package to your system.

3. Tell apt to reinstall the package:  sudo apt install --reinstall /full/path/to/your/downloaded/deb_package


These are not copy-it-exactly instructions. You must read the web page. You must figure out what a "full path" is. You're capable of this.

---

### Post by TheFu on 2023-07-10
> **James Fitzpatrick said:**
> I'm running 22.04, and I've been very prompt with my updates.

**My mistake.  **  I saw all the Bionic stuff in the output and didn't look too closely.  You should remove those lines.  

Upgrades from LTS-to-LTS-to-LTS is about the limit for being successful.  I only do 1 LTS upgrade, then it is a fresh install to clean out the crap.  Lots of things have changed since 18.04. Having a system with multiple subsystems for many of the infrastructure subsystems can be a problem, or just confusing at the minimum.
I do have a few servers that are 100% stock that have been upgraded from LTS-to-LTS and seem to work, but there were also a number that failed the upgrade process and forced a fresh install.

I'm fairly practical.  When I do an upgrade and it fails, it is time for a fresh install. Usually I can restore data and settings from prior programs into the fresh install, then install 99% of the packages that were their before and have a running system, on a new OS, in 30-45 minutes.  There are always a few programs that are removed between LTS release so I need to either do without or find an alternative.   The last upgrade I attempted was from 18.04 --> 20.04 and took almost 3 hrs.  That convinced me that doing fresh installs was a better option for me.

---

### Post by James Fitzpatrick on 2023-07-11
I downloaded the AMD64 thing.  Is that right?  I still can't figure it out.  Please give me a break!  I'm 70 years old, and I'll be dead soon enough!

---

### Post by ian-weisser on 2023-07-11
> **James Fitzpatrick said:**
> I downloaded the AMD64 thing.  Is that right?

What exactly did you download? (file name, please)

And where on your system, exactly, did you download it to?

You can do this.

---

### Post by James Fitzpatrick on 2023-07-11
The one marked AMD64:

Architecture	Package Size	Installed Size	Files
amd64	2,747.4 kB	26,010.0 kB	[list of files]

I downloaded to my desktop.

---

### Post by ian-weisser on 2023-07-11
You are making good progress.

It might be marked "amd64" on the website, but it has a different filename on your system. What is that filename?

Take that filename, and your username, and substitute them into this command:

```

sudo apt install --reinstall /home/$USERNAME/Desktop/$FILENAME

```

Then run that command.

If there are any errors, then show us the complete input and output of that command.

---

### Post by James Fitzpatrick on 2023-07-11
I downloaded AMD64:

Architecture	Package Size	Installed Size	Files
amd64	2,747.4 kB	26,010.0 kB	[list of files]

---

### Post by James Fitzpatrick on 2023-07-11
linux-headers 5.15.0-53- generic... ?

---

### Post by James Fitzpatrick on 2023-07-11
I'm typing in:
sudo apt install-reinstall/home/james/Desktop/linux-headers-5.15.05-53-generic

It's telling me this is an invalid operation.  Am I typing something wrong?  Is the username the same as the password? Am I leaving something off?

---

### Post by #&amp;thj^% on 2023-07-11
Do this for us please:
```
cd Desktop && ls -a

```
paste back what shows

---

### Post by #&amp;thj^% on 2023-07-11
> **James Fitzpatrick said:**
> I'm typing in:
sudo apt install-reinstall/home/james/Desktop/linux-headers-5.15.05-53-generic

It's telling me this is an invalid operation.  Am I typing something wrong?  Is the username the same as the password? Am I leaving something off?
This is wrong:
```
apt install-reinstall
```
Should be:
There is a space and another "-" in "install --reinstall"
```
sudo apt install --reinstall/home/james/Desktop/linux-headers-5.15.05-53-generic
```
If that is the correct path and name, see more below.
Do this for us please:
```
cd Desktop && ls -a

```
paste back what shows

---

### Post by James Fitzpatrick on 2023-07-11
$ cd Desktop && ls -a
bash: cd: Desktop: No such file or directory

---

### Post by James Fitzpatrick on 2023-07-11
Also, I tried this :
$ sudo apt install --reinstall/home/james/Desktop/linux-headers-5.15.05-53-generic
[sudo] password for james: 
and got this back:
E: Command line option --reinstall/home/james/Desktop/linux-headers-5.15.05-53-generic is not understood in combination with the other options

---

### Post by TheFu on 2023-07-11
> **James Fitzpatrick said:**
> Also, I tried this :
$ sudo apt install --reinstall/home/james/Desktop/linux-headers-5.15.05-53-generic
[sudo] password for james: 
and got this back:
E: Command line option --reinstall/home/james/Desktop/linux-headers-5.15.05-53-generic is not understood in combination with the other options

You are missing a space.  That's what the error is saying.  Help yourself _by using tab-completion whenever a filename is needed._  I ensure that all my beginning Linux students know how to do this on their first day.  Effectively, it prevents the normal mistakes that humans make, since the computer fills in the path/to/the/file for you with just a few hints.  There are hundreds of youtube videos to explain it.  This is 1 time when a video or in-person seeing what happens explains things better than reading. It takes 10 seconds to learn, but will save you years of frustration.

---

### Post by James Fitzpatrick on 2023-07-12
Okay, I found the missing space.  But then I get this back:

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: The package linux-headers-5.15.0-53-generic needs to be reinstalled, but I can't find an archive for it.

---

### Post by #&amp;thj^% on 2023-07-12
Please try this from a terminal and copy back all output wrapped in code tags please.
```
sudo apt --fix-broken install
```
See my signature for Code Tags.

---

### Post by James Fitzpatrick on 2023-07-12
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: The package linux-headers-5.15.0-53-generic needs to be reinstalled, but I can't find an archive for it.

---

### Post by deadflowr on 2023-07-12
> **James Fitzpatrick said:**
> Okay, I found the missing space.  But then I get this back:

Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: The package linux-headers-5.15.0-53-generic needs to be reinstalled, but I can't find an archive for it.

Unless you rename the file when you downloaded it, you are trying to install a non-existent package.
Your install output shows it as 5.15.05-53, the 05 never existed.
Drop the 5, it should be 5.15.0-53-generic

---

### Post by James Fitzpatrick on 2023-07-12
I tried dropping it, but it still says:

$ sudo apt install - reinstall/home/james/Desktop/linux-headers-5.15.0-53-generic
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
E: The package linux-headers-5.15.0-53-generic needs to be reinstalled, but I can't find an archive for it.

---

### Post by deadflowr on 2023-07-12
Space and a dash
```
sudo apt install --reinstall /home/james/Desktop/linux-headers-5.15.0-53-generic
```

---

### Post by James Fitzpatrick on 2023-07-12
This is what I'm getting:

$ sudo apt install --reinstall /home/james/Desktop/linux-headers-5.15.0-53-generic
Reading package lists... Done
E: Unsupported file /home/james/Desktop/linux-headers-5.15.0-53-generic given on commandline
 I'm about ready to give up.

---

### Post by deadflowr on 2023-07-12
What is the full name of the file you downloaded to the desktop?
Probably ends in .deb

---

### Post by James Fitzpatrick on 2023-07-12
linux-headers-5.15.0-53-generic_5.15.0-53.59~20.04.1_amd64,deb [read only]

---

### Post by deadflowr on 2023-07-12
Try
```
sudo apt install --reinstall /home/james/Desktop/linux-headers-5.15.0-53-generic_5.15.0-53.59~20.04.1_amd64.deb
```

Did you copy/paste that or write it out?
I ask because what you posted had a comma instead of a period before the deb.
i changed it in what I wrote.
should be a period.
.deb is a file name extension, like .txt or .html, or whatever.

---

### Post by James Fitzpatrick on 2023-07-12
It is a period.

---

### Post by TheFu on 2023-07-12
> **James Fitzpatrick said:**
> linux-headers-5.15.0-53-generic_5.15.0-53.59~20.04.1_amd64,deb [read only]

Did you use tab completion?  Errors like you are having just don't happen when that is used.  

Also, there are 3+ separate packages for kernels.  the kernel image, headers, and modules.  Normally, people install the image package and let APT solve the dependencies for the other two.

Learning tab-completion really is worth your time.  I can't imagine doing anything in a shell without out.

---

### Post by James Fitzpatrick on 2023-07-12
As I've said, I'm NOT computer saavy - at all.  I've looked at and read the Youtube and other stuff on this tab completion, and I really just don't get it.  I can't even understand the guy on Youtube because his accent is so heavy.  I guess it's my fault for not having kept up with technology.  At one time Ubuntu was so easy, and that's one of the main reasons I switched from Windows to it.  Now, it's become, in many ways, as obtuse as Windows.

Thank you for having done what you've done, but I just seem to be too dense.

---

### Post by TheFu on 2023-07-13
There are 500 people showing tab-completion on youtube.  Pick one that you can understand.  It is worth your time.

BTW, tab-completion has been around since the mid-1990s, so it isn't new.  I used it on MS-DOS/MS-Windows and OS/2 with 4dos and 4nt (those were command line replacements for command.com).

---

### Post by James Fitzpatrick on 2023-07-13
Thanks for your efforts, but I'm giving up.  My time is too short.  I just wanted to know how to fix a problem - not learn about something I'm never likely to use again.  Again, thanks.

---

### Post by TheFu on 2023-07-13
> **James Fitzpatrick said:**
> Thanks for your efforts, but I'm giving up.  My time is too short.  I just wanted to know how to fix a problem - not learn about something I'm never likely to use again.  Again, thanks.

I would have troubleshot this for about 1 hour. If I couldn't solve it in that time, I'd have wiped the system, reloaded a fresh install and restored my backup data, settings, and list of programs.  

So, I completely understand.  2 hrs to a fix is about the limit of my patience.

---

