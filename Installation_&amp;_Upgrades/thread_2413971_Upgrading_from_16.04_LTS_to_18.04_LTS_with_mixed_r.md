---
title: "Upgrading from 16.04 LTS to 18.04 LTS with mixed results"
date: 2019-03-04
forum: Installation &amp; Upgrades
---

### Post by rsteinmetz70112 on 2019-03-04
For what it's worth, I am posting my experience of upgrading several computers to 18.04 LTS.

So far I've upgraded 4 of 7 computers 2 of the Up[grades went wee and I had minimal problems.
2 encountered substantial, but different problems.

One machine didn't create the proper links for /var/run and /run. Once I figured that out it worked OK but I had video problems due to the old Nvidia driver. removing that solved the problems.

The other machine I still have issues with is a mess. There are many unconfigured packages but it doesn't have a working network connection. I' can use a live session to download .debs and install them but so many packages are unconfigured most won't install because of unmet dependencies.

I've made some recent posts looking for help and posting what I've done to hopefully help others and provide some clues.

After I post this I'm going to post something specific about the machine I'm still having trouble with.

---

### Post by jdeca57 on 2019-03-04
Upgrading an OS is always chancy. It works best in environments with little or no divergence from the original install. Mostly in a VM with no hardware issues, then it&#8217;s next to failsafe. But otherwise a clean install is always preferable. It&#8217;s more work, of course. But aside of the backup issue (evidently everyone makes a backup) there is the installation of modifications, software, tinkering and so and it is an illusion to think that between major LTS installations everything remains the same. Not that I think your approach is wrong: by any means, upgrade. If it works, fine. Just be prepared to reinstall.

---

### Post by rsteinmetz70112 on 2019-05-06
OK I'm back to update my progress. I've completed 4 of 7 but do-release upgrade failed on the 5th machine apparently do to a corrupt python package python3-pkg-resources. Reinstalling it fixed that problem but I've been traveling so I haven't been able to actually run the upgrade.

Probably 2 weeks before I can try the upgrade.

---

### Post by rsteinmetz70112 on 2019-05-18
I now completed the 5th of 7 upgrades. This ome went pretty well. There were errors during the set up but 
```
# apt install -f
# dpkg --configure -a
# apt full-upgrade 
```
cleaned things up. I did have a problem being unable to log into a graphic session but
```
# Dpkg-reconfigure gdm
```

---

### Post by rsteinmetz70112 on 2019-06-05
I've now completed the 6th of 7 upgrades.

This one went pretty well there were no errors during the process except for two problems:

The correct Nvidia driver was not install but some supporting libraries were. That meany tha the nouveau drived wouldn't start correctly

```
#apt purge nvidia*
``` solved that problem.

The second problem related to samba. Apparently when winbind is installed certain necessary packages relating to winbind were not installed.

```
# apt install  libnss-winbind libpam-winbind
```

It took a while to figure it out but the solution was petty easy.

The 7th upgrade will be the most complicated. It's a i386 install going back many years I've put oof dealing with it but I've got a strategy, I've install and amd64 kernel on a seperate partition I'm duplicating the i386 configuration on it and will substitute the new install for the old one when I've got it fully working. The machine is a server running Samba as a Domain Controller, Apache2 and postfix as an outgoing email server. Sounds easy, I'm sure it won't be.

---

### Post by mastablasta on 2019-06-07
looks like desktop linux and the way it is setup is causing the issues. i did home server upgrade and it was very smooth.

---

### Post by rsteinmetz70112 on 2019-06-07
> **mastablasta said:**
> looks like desktop Linux and the way it is setup is causing the issues. i did home server upgrade and it was very smooth.

These systems continuously upgraded from LTS to LTS for more than 10 years. The hardware has all been changed more than once and Ubuntu Desktop is installed. I'm amazed it works as well as it does. Some of the problems are no doubt carried over from previous upgrades. However all of the problems I've encountered have been encountered by other users and most of the solutions have been found from postings online. A few of problems seem recurring, 
[LIST]
[*]Problems with Nvidia driver upgrades and with nouveau. 
I'd like to use nouveau but I've had problems with it in the past causing freezes but it seems to be getting better.
[*]Problems with samba upgrades especially winbind, usually the upgrade process failing to download necessary packages for my installation.
[*]Problems downloading the upgraded packages including interrupted downloads and corrupt package downloads.
[*]Problems with changes to the graphic environment from one version to another.
[/LIST]

I suspect a lot of it is using LTS versions only since there are more changes between upgrades and the process doesn't get tested as thoroughly on those.
I've also found no good way of detecting and eliminating unnecessary packages which are upgraded from version to version but are not necessary. The Best example of this is the changes Ubuntu has made over the years in the graphic Desktop going from Gnome to Unity back to Gnome with other changes in between.

Many people here recommend always doing clean installs but with servers there is the problem of the configuration of the server services.
Of the 6 servers I've upgraded most have gone OK, with only minor problems. Only one was seriously screwed up and is was virtually identical to another machine which went fine except with a relatively minor problem with the Nvidia driver.

---

### Post by rishrules on 2020-01-16
Mine may prove an interesting case then.  A friend recently gifted me a Dell XPS-13-9360 with Intel Core i5-7200U 64 Bit machine.  Ubuntu 16.04 came factory installed, and my friend, disliking the key action and usually on a tower never, ever, ever used it.  So I look to transform it into a faux Mac for my girlfriend.  Thing is, when I click the Install Updates button I'm told it failed todownload the repository and to check my internet connection.  I canbrowse Chromium just fine, so its not the connection.  Indeed when Ichoose to use the US or main Server to download updates I get the following-  

"W:GPG error:[http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release: The followingsignatures couldn't be verified because the public key is notavailable: NO_PUBKEY 6494C6D6997C215E, W:The repository'http://dl.google.com/linux/chrome/deb stable Release' is notsigned., W:Data from such a repository can't be authenticated and istherefore potentially dangerous to use., W:See apt-secure(8) manpagefor repository creation and user configuration details., W:There isno public key available for the following key IDs:
6494C6D6997C215E  ,E:Problem executing scripts APT::Update::Post-Invoke-Success 'if/usr/bin/test -w /var/cache/app-info -a -e /usr/bin/appstreamcli;then appstreamcli refresh > /dev/null; fi', E:Sub-process returnedan error code"

So I did some of my own homework, notably on the public key.   I checked the LinuxMint[https://forums.linuxmint.com/viewtopic.php?f=42&p=1351074#p1350799](https://forums.linuxmint.com/viewtopic.php?f=42&p=1351074#p1350799)and tried their apt-get update suggestion.  The add command seemed towork.  It tells me &#8220;ok&#8221;.  But the update fails.  First there&#8217;sthe report *** Error in `appstreamcli': double free or corruption(fasttop): 0x00000000014dd430 *** &#8220; Shell runs a backtrace, thenstarts a memory map.  After a long string of files it says aborted &#8211;core dumped.  E: Problem executing scriptsAPT::Update::Post-Invoke-Success 'if /usr/bin/test -w/var/cache/app-info -a -e /usr/bin/appstreamcli; then appstreamclirefresh > /dev/null; fi'  I'm also crashing for a number of obsolete packages when I boot up.  

  It looks like I have the public key right.  Is it my current distro simply doesn't know where to look for updates?

---

### Post by jimmyrus on 2020-01-17
> **rsteinmetz70112 said:**
> These systems continuously upgraded from LTS to LTS for more than 10 years. The hardware has all been changed more than once and Ubuntu Desktop is installed. I'm amazed it works as well as it does. Some of the problems are no doubt carried over from previous upgrades. However all of the problems I've encountered have been encountered by other users and most of the solutions have been found from postings online. A few of problems seem recurring, 
[LIST]
[*]Problems with Nvidia driver upgrades and with nouveau. 
I'd like to use nouveau but I've had problems with it in the past causing freezes but it seems to be getting better.
[*]Problems with samba upgrades especially winbind, usually the upgrade process failing to download necessary packages for my installation.
[*]Problems downloading the upgraded packages including interrupted downloads and corrupt package downloads.
[*]Problems with changes to the graphic environment from one version to another.
[/LIST]

I suspect a lot of it is using LTS versions only since there are more changes between upgrades and the process doesn't get tested as thoroughly on those.
I've also found no good way of detecting and eliminating unnecessary packages which are upgraded from version to version but are not necessary. The Best example of this is the changes Ubuntu has made over the years in the graphic Desktop going from Gnome to Unity back to Gnome with other changes in between.

Many people here recommend always doing clean installs but with servers there is the problem of the configuration of the server services.
Of the 6 servers I've upgraded most have gone OK, with only minor problems. Only one was seriously screwed up and is was virtually identical to another machine which went fine except with a relatively minor problem with the Nvidia driver.
I never upgrade and always do clean installs. Just too much junk left around and too many gremlins from multiple versions of libraries mixing old and new etc etc. The services have config files that you can just put on a flash drive and copy
to the fresh system. could have problems anyway since sometimes the configs and directives are different from one version to the next and you'll have to reconfigure and tweak anyways. besides thats what you have backups for right?

---

### Post by CelticWarrior on 2020-01-17
There are many differences between 16.04 and 18.04 but the main one is the change of Desktop Environment from Unity to plain Gnome.

This alone recommends a clean install instead of the usual online upgrade.

---

