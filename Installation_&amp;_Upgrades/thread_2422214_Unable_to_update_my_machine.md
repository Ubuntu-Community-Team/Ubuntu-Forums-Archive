---
title: "Unable to update my machine"
date: 2019-07-03
forum: Installation &amp; Upgrades
---

### Post by jdosio on 2019-07-03
Good afternoon,
I'm not sure if this is the correct place to post this but if its not please redirect me to some place this would belong.

i am having some difficulty updating my machine. 
after entering:
 
```
jdosio@2io-01:~$ sudo apt-get update
```

i am prompted with...

```
Ign:1 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease
Hit:2 [http://repo.steampowered.com/steam](http://repo.steampowered.com/steam) precise InRelease                     
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                     
Hit:4 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                     
Hit:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease                     
Hit:6 [http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu](http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu) bionic InRelease     
Ign:7 [https://dl.winehq.org/wine-builds/ubunut](https://dl.winehq.org/wine-builds/ubunut) bionic InRelease                
Ign:9 [https://dl.winehq.org/wine-builds/ubunut](https://dl.winehq.org/wine-builds/ubunut) cosmic InRelease                
Hit:10 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) bionic InRelease               
Hit:11 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) artful InRelease               
Ign:12 [https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard](https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard) bionic InRelease
Err:13 [https://dl.winehq.org/wine-builds/ubunut](https://dl.winehq.org/wine-builds/ubunut) bionic Release                 
  404  Not Found [IP: 151.101.58.217 443]
Err:14 [https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard](https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard) bionic Release
  404  Not Found [IP: 2620:113:80c0:8::13 443]
Err:15 [https://dl.winehq.org/wine-builds/ubunut](https://dl.winehq.org/wine-builds/ubunut) cosmic Release            
  404  Not Found [IP: 151.101.58.217 443]
Hit:16 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic InRelease
Ign:17 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) bionic InRelease       
Err:18 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) bionic Release
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done
E: The repository 'https://dl.winehq.org/wine-builds/ubunut bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
E: The repository 'https://dl.winehq.org/wine-builds/ubunut cosmic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
E: The repository 'http://ppa.launchpad.net/wine/wine-builds/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
```




im not quite sure as to how to proceed from here, has anyone had a similar issue ?

Kindest Regards,
JD

---

### Post by deadflowr on 2019-07-03
Your issue is that one of repositories with errors have the wrong name
winehq has a bogus entry for ubunut that needs to be changed to ubuntu in the sources.list entry

I don't know what the correct entry is for opensuse repositories for ubuntu is
I would expect that since it's 18.10 it would be a cosmic entry instead of bionic.

---

### Post by jdosio on 2019-07-03
how can i access the sources.list entry to make this fix ?

also thank you for the quick response!

---

### Post by deadflowr on 2019-07-03
Open Software and Updates go to Other Software
Highlight the entry and click edit
Then edit the entry and click OK.

The wine entry change should be at the end of the URI
The opensuse change should be the Distribution.

Again though I'm not sure what the opensuse entry should be
It's only a guess since 18.10 is the cosmic release for ubuntu.

Worst case it doesn't work you can uncheck the entry for it in Software and Updates to disable it.
That will at least allow you to update.

---

### Post by jdosio on 2019-07-03
after opening Software and Updates and going to Other Software i was shown many entry's  here is a picture of what i was shown(after editing all the "ununuts"'s to "unubtu"'s)

[IMG]file:///home/jdosio/Pictures/Screenshot%20from%202019-07-03%2016-31-23.png[/IMG]

then as i leave the window by clicking "close bottom right i am given the following message 


Failed to download repository information


Check your Internet connection.

details>

```
W:Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:48,
 W:Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:48, 
W:Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:48, 
W:Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:48, W:Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:48, 
W:Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:48, 
W:Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:48, 
W:Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:48, 
W:Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:48, 
W:Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:42 and /etc/apt/sources.list:48, 
W:Skipping acquire of configured file 'bionic/binary-i386/Packages' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'bionic' (component misspelt in sources.list?), 
W:Skipping acquire of configured file 'bionic/binary-amd64/Packages' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'bionic' (component misspelt in sources.list?), 
W:Skipping acquire of configured file 'bionic/i18n/Translation-en' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'bionic' (component misspelt in sources.list?), 
W:Skipping acquire of configured file 'bionic/dep11/Components-amd64.yml' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'bionic' (component misspelt in sources.list?), 
W:Skipping acquire of configured file 'bionic/dep11/icons-48x48.tar' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'bionic' (component misspelt in sources.list?), 
W:Skipping acquire of configured file 'bionic/dep11/icons-64x64.tar' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'bionic' (component misspelt in sources.list?), 
W:Skipping acquire of configured file 'bionic/cnf/Commands-amd64' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'bionic' (component misspelt in sources.list?), 
W:Skipping acquire of configured file 'Release/binary-amd64/Packages' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'Release' (component misspelt in sources.list?), 
W:Skipping acquire of configured file 'Release/binary-i386/Packages' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'Release' (component misspelt in sources.list?), 
W:Skipping acquire of configured file 'Release/i18n/Translation-en' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'Release' (component misspelt in sources.list?), 
W:Skipping acquire of configured file 'Release/dep11/Components-amd64.yml' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'Release' (component misspelt in sources.list?), 
W:Skipping acquire of configured file 'Release/dep11/icons-48x48.tar' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'Release' (component misspelt in sources.list?), 
W:Skipping acquire of configured file 'Release/dep11/icons-64x64.tar' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'Release' (component misspelt in sources.list?), 
W:Skipping acquire of configured file 'Release/cnf/Commands-amd64' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'Release' (component misspelt in sources.list?), E:The repository 'https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard bionic Release' does not have a Release file., 
W:Updating from such a repository can't be done securely, and is therefore disabled by default., 
W:See apt-secure(8) manpage for repository creation and user configuration details., 
E:The repository 'http://ppa.launchpad.net/wine/wine-builds/ubuntu bionic Release' does not have a Release file., 
W:Updating from such a repository can't be done securely, and is therefore disabled by default., 
W:See apt-secure(8) manpage for repository creation and user configuration details., 
W:Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56,
 W:Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56, 
W:Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56, 
W:Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56,
 W:Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56, 
W:Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56, 
W:Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56, 
W:Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56, 
W:Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56, 
W:Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:52 and /etc/apt/sources.list:56
```

i again try to update and am given the same error as before.

---

### Post by deadflowr on 2019-07-03
To preface this first,  use the forums attachment function to attach images.
(In a new post to attach an image click on Go Advanced and then you'll have access to the paperclip item in the toolbar.
The paperclip is the attachment tool option. 
It's fairly simple: it'll give a small popup window to access your computer and allow you to upload an image,
once uploaded it'll be automatically added the post, so just exit the attachment section to get back to the normal post window)
(I hope that makes sense)

We missed another error message for another wine repository.
You need to disable the one for launchpad,
as that repository is dead.
(should be this one: [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) bionic)


Also might as well post the outputs for
```
cat /etc/apt/sources.list
ls /etc/apt/sources.list.d/
```
Use code tags:
[https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168")

---

### Post by jdosio on 2019-07-06
Thank you very for the instructions i have gone ahead and edited my previous post and added the image as an attachment,

as for the two commands you mentioned here are the results i obtained...
```

jdosio@2io-01:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)]/ bionic main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted


## Major bug fix updates produced after the final release of the
## distribution.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu bionic partner
deb-src http://archive.canonical.com/ubuntu bionic partner


# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main
deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
deb https://dl.winehq.org/wine-builds/ubuntu/ cosmic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ cosmic main
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe main restricted multiverse
deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
deb https://dl.winehq.org/wine-builds/ubuntu/ artful main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ artful main
deb https://dl.winehq.org/wine-builds/ubuntu bionic bionic Release
# deb-src https://dl.winehq.org/wine-builds/ubuntu bionic bionic Release
deb https://dl.winehq.org/wine-builds/ubuntu/ artful main
deb https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard bionic main
# deb-src https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard bionic main
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main universe restricted multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ bionic-security main universe restricted multiverse



```

```

jdosio@2io-01:~$ ls /etc/apt/sources.list.d/
dawidd0811-ubuntu-neofetch-bionic.list
dawidd0811-ubuntu-neofetch-bionic.list.save
google-chrome.list
google-chrome.list.save
graphics-drivers-ubuntu-ppa-bionic.list
graphics-drivers-ubuntu-ppa-bionic.list.save
steam.list
steam.list.save
wine-ubuntu-wine-builds-bionic.list
wine-ubuntu-wine-builds-bionic.list.save



```

how should i proceed from here ?

JD

---

### Post by deadflowr on 2019-07-06
I marked which lines are either duplicates or need a change.

```
jdosio@2io-01:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)]/ bionic main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted


## Major bug fix updates produced after the final release of the
## distribution.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu bionic partner
deb-src http://archive.canonical.com/ubuntu bionic partner


# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
**deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main**
deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
deb https://dl.winehq.org/wine-builds/ubuntu/ cosmic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ cosmic main
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe main restricted multiverse
**deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main**
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
**deb https://dl.winehq.org/wine-builds/ubuntu/ artful main**
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ artful main
deb https://dl.winehq.org/wine-builds/ubuntu bionic bionic **Release**
# deb-src https://dl.winehq.org/wine-builds/ubuntu bionic bionic Release
**deb https://dl.winehq.org/wine-builds/ubuntu/ artful main**
deb https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard bionic main
# deb-src https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard bionic main
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main universe restricted multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ bionic-security main universe restricted multiverse
```

change the Release entry in bold to main, just like the rest show.
and either delete or add a comment symbol (#) to two of those bolded lines one for each.
(Keeping one line for bionic and one line for artful)

(In reality you should delete all entries not marked for bionic on 18.04.
Mixing release version in the repos is cruising for a bruising.
But for now just to get things in order, clear out what are known problems first.)

You can edit the file in the terminal using
```
sudo apt edit-sources
```
it'll ask which editor program you want to you.
The default editor is nano.
To save changes in nano and exit you can run ctrl +o to save and ctrl +x to exit.

Hope that makes sense

---

### Post by CatKiller on 2019-07-06
If I'm reading your sources.list correctly on my phone, you've also managed to nuke your main repositories. You've got the partner, backports and updates repositories enabled, but not the main Ubuntu one.

You won't need entries for Wine in your sources.list if you've also got them in sources.list.d. One or the other, not both.

---

### Post by jdosio on 2019-07-07
i have removed one of each of the lines from my source.list
```

[B]deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main
[/B]**deb https://dl.winehq.org/wine-builds/ubuntu/ artful main**

```
now if i execute...
```

jdosio@2io-01:~$ sudo apt edit-sources 
[sudo] password for jdosio: 
Your '/etc/apt/sources.list' file changed, please run 'apt-get update'.jdosio@2io-01:~$ sudo apt edit-sources         cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)]/ bionic main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted


## Major bug fix updates produced after the final release of the
## distribution.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-backports main restricted universe multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu bionic partner
deb-src http://archive.canonical.com/ubuntu bionic partner


# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main
deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
deb https://dl.winehq.org/wine-builds/ubuntu/ cosmic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ cosmic main
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe main restricted multiverse
# deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
deb https://dl.winehq.org/wine-builds/ubuntu/ artful main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ artful main
deb https://dl.winehq.org/wine-builds/ubuntu bionic bionic Release
# deb-src https://dl.winehq.org/wine-builds/ubuntu bionic bionic Release
# deb https://dl.winehq.org/wine-builds/ubuntu/ artful main
deb https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard bionic main
# deb-src https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard bionic main
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates main universe restricted multiverse
deb http://us.archive.ubuntu.com/ubuntu/ bionic-backports main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ bionic-security main universe restricted multiverse

```

now if i try and update 
```

jdosio@2io-01:~$ sudo apt-get update
Hit:1 http://us.archive.ubuntu.com/ubuntu bionic InRelease
Hit:2 http://archive.canonical.com/ubuntu bionic InRelease                                                         
Get:3 http://us.archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]                                       
Get:4 http://us.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]                                     
Get:5 http://us.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [284 kB]                       
Ign:6 https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard bionic InRelease
Err:7 https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard bionic Release
  404  Not Found [IP: 2620:113:80c0:8::13 443]
Get:8 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [66.7 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [134 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [250 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [204 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [430 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,464 B]               
Get:14 http://us.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [7,228 B]               
Ign:15 http://dl.google.com/linux/chrome/deb stable InRelease                                                      
Hit:16 https://dl.winehq.org/wine-builds/ubuntu bionic InRelease                                                   
Hit:17 https://dl.winehq.org/wine-builds/ubuntu cosmic InRelease                                                   
Get:18 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]                                       
Hit:19 https://dl.winehq.org/wine-builds/ubuntu artful InRelease                                                   
Hit:20 http://dl.google.com/linux/chrome/deb stable Release                                                        
Hit:21 http://ppa.launchpad.net/dawidd0811/neofetch/ubuntu bionic InRelease                                 
Hit:22 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic InRelease                                      
Get:24 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [24.1 kB]                  
Hit:25 http://repo.steampowered.com/steam precise InRelease                                                        
Get:26 http://security.ubuntu.com/ubuntu bionic-security/main DEP-11 48x48 Icons [10.4 kB]                     
Get:27 http://security.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64 Icons [31.7 kB]                         
Get:28 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [41.2 kB]                  
Get:29 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 48x48 Icons [16.4 kB]                     
Get:30 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64 Icons [111 kB]                      
Get:31 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 DEP-11 Metadata [2,464 B]                
Ign:32 http://ppa.launchpad.net/wine/wine-builds/ubuntu bionic InRelease                                           
Err:33 http://ppa.launchpad.net/wine/wine-builds/ubuntu bionic Release
  404  Not Found [IP: 91.189.95.83 80]
Reading package lists... Done
E: The repository 'https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
W: Skipping acquire of configured file 'bionic/binary-i386/Packages' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'bionic' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'bionic/binary-amd64/Packages' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'bionic' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'bionic/i18n/Translation-en' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'bionic' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'bionic/i18n/Translation-en_US' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'bionic' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'bionic/dep11/Components-amd64.yml' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'bionic' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'bionic/dep11/icons-48x48.tar' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'bionic' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'bionic/dep11/icons-64x64.tar' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'bionic' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'bionic/cnf/Commands-amd64' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'bionic' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'Release/binary-amd64/Packages' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'Release' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'Release/binary-i386/Packages' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'Release' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'Release/i18n/Translation-en' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'Release' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'Release/i18n/Translation-en_US' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'Release' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'Release/dep11/Components-amd64.yml' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'Release' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'Release/dep11/icons-48x48.tar' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'Release' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'Release/dep11/icons-64x64.tar' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'Release' (component misspelt in sources.list?)
W: Skipping acquire of configured file 'Release/cnf/Commands-amd64' as repository 'https://dl.winehq.org/wine-builds/ubuntu bionic InRelease' doesn't have the component 'Release' (component misspelt in sources.list?)
E: The repository 'http://ppa.launchpad.net/wine/wine-builds/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.



```

if you guys know of any sources i could read up on on how it should be set up i would be very appreciative.
not quite sure what to do know...

---

### Post by jdosio on 2019-07-07
> **CatKiller said:**
> If I'm reading your sources.list correctly on my phone, you've also managed to nuke your main repositories. You've got the partner, backports and updates repositories enabled, but not the main Ubuntu one.

You won't need entries for Wine in your sources.list if you've also got them in sources.list.d. One or the other, not both.

how can i access the sources.list.d file to ensure there are no duplicates?
what should a normal source.list normally contain ?

Kindest regards,
JD

---

### Post by again? on 2019-07-07
**/etc/apt/sources.list.d** is not a file...it's a directory with .list files of third party repos
**/etc/apt/sources.list** is a file containing official ubuntu repositories.
Ideally 3rd party repos shoud create a .list file in /etc/apt/sources.list.d/ but 
quite often they are added to the /etc/apt/sources.list file.

Create a new /etc/apt/sources.list after backing up, as shown [**HERE**]("https://ubuntuforums.org/showthread.php?t=2414194&p=13843080#post13843080")
Also untick all third party repos in the "other software" tab of software-properties-gtk
Then run... 
```
sudo apt update
```

Now you can sort out what third party repos in **/etc/apt/sources.list.d/** (other software tab) 
you want to enable or if you want to add third party repos that were in your old /etc/apt/sources.list file.
You can view third party sources that were in your old /etc/apt/sources.list with
```
cat /etc/apt/sources.list.bak
```

---

### Post by jdosio on 2019-07-07
> **guber2 said:**
> **/etc/apt/sources.list.d** is not a file...it's a directory with .list files of third party repos
**/etc/apt/sources.list** is a file containing official ubuntu repositories.
Ideally 3rd party repos shoud create a .list file in /etc/apt/sources.list.d/ but 
quite often they are added to the /etc/apt/sources.list file.

Create a new /etc/apt/sources.list after backing up, as shown [**HERE**]("https://ubuntuforums.org/showthread.php?t=2414194&p=13843080#post13843080")
Also untick all third party repos in the "other software" tab of software-properties-gtk
Then run... 
```
sudo apt update
```

Now you can sort out what third party repos in **/etc/apt/sources.list.d/** (other software tab) 
you want to enable or if you want to add third party repos that were in your old /etc/apt/sources.list file.
You can view third party sources that were in your old /etc/apt/sources.list with
```
cat /etc/apt/sources.list.bak
```

"Also untick all third party repos in the "other software" tab of software-properties-gtk..."
to be clear you would like me to untick all the ones that are not "Canonical Partners" or "Canonical Partners (source code)"?

---

### Post by CatKiller on 2019-07-07
The Canonical partners repository is also a third-party repository.

The line I was expecting to see in your sources.list was something like ```
deb http://archive.ubuntu.com/ubuntu bionic main universe restricted multiverse
``` If it's there, I didn't see it on my phone. The main, universe, restricted, and multiverse repositories are where your normal Ubuntu software comes from.

> The repository components are:

    Main - Officially supported software.

    Restricted - Supported software that is not available under a completely free license.

    Universe - Community maintained software, i.e. not officially supported software.

    Multiverse - Software that is not free. 

---

### Post by again? on 2019-07-07
> **jdosio said:**
> "Also untick all third party repos in the "other software" tab of software-properties-gtk..."
to be clear you would like me to untick all the ones that are not "Canonical Partners" or "Canonical Partners (source code)"?
Just untick all in the other software tab.

You can re-enable later ones you want.
At the moment you just want to be able to run an update without errors.
After following the guide in my link your /etc/apt/sources.list file should be similar to...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] cat /etc/apt/sources.list**
deb http://archive.ubuntu.com/ubuntu bionic main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ bionic-security multiverse universe restricted main
deb http://archive.ubuntu.com/ubuntu bionic-updates multiverse universe restricted main
deb http://archive.ubuntu.com/ubuntu bionic-backports multiverse universe restricted main
```

You can list all enabled repositories with... 
```
egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list | nl
```

eg (**Note**: I have [COLOR="#0000FF"]3 3rd party repos[/COLOR] enabled)...
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list | nl**
     1	/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu bionic main universe restricted multiverse
     2	/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu/ bionic-security multiverse universe restricted main
     3	/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu bionic-updates multiverse universe restricted main
     4	/etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu bionic-backports multiverse universe restricted main
     [COLOR="#0000FF"]5	/etc/apt/sources.list.d/google-chrome-beta.list:deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
     6	/etc/apt/sources.list.d/megasync.list:deb https://mega.nz/linux/MEGAsync/xUbuntu_18.04/ ./
     7	/etc/apt/sources.list.d/vivaldi-snapshot.list:deb http://repo.vivaldi.com/snapshot/deb/ stable main[/COLOR]
```

---

### Post by jdosio on 2019-07-09
does this look right to you ?

```

jdosio@2io-01:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 18.04.2 LTS _Bionic Beaver_ - Release amd64 (20190210)]/ bionic main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic main restricted


## Major bug fix updates produced after the final release of the
## distribution.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu bionic partner
deb-src http://archive.canonical.com/ubuntu bionic partner


# deb-src http://security.ubuntu.com/ubuntu bionic-security main restricted
# deb-src http://security.ubuntu.com/ubuntu bionic-security universe
# deb-src http://security.ubuntu.com/ubuntu bionic-security multiverse
# deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb https://dl.winehq.org/wine-builds/ubuntu/ cosmic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ cosmic main
deb http://archive.ubuntu.com/ubuntu bionic main universe restricted multiverse
# deb https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ bionic main
# deb https://dl.winehq.org/wine-builds/ubuntu/ artful main
# deb-src https://dl.winehq.org/wine-builds/ubuntu/ artful main
# deb https://dl.winehq.org/wine-builds/ubuntu bionic bionic Release
# deb-src https://dl.winehq.org/wine-builds/ubuntu bionic bionic Release
# deb https://dl.winehq.org/wine-builds/ubuntu/ artful main
# deb https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard bionic main
# deb-src https://download.opensuse.org/repositories/Emulators:/Wine:/Debian/Ubuntu_18.10_standard bionic main
deb http://archive.ubuntu.com/ubuntu bionic-updates main universe restricted multiverse
deb http://archive.ubuntu.com/ubuntu bionic-backports main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ bionic-security main universe restricted multiverse



```

```

jdosio@2io-01:~$ egrep -v '^#|^ *$' /etc/apt/sources.list /etc/apt/sources.list.d/*.list | nl
     1    /etc/apt/sources.list:deb http://archive.canonical.com/ubuntu bionic partner
     2    /etc/apt/sources.list:deb-src http://archive.canonical.com/ubuntu bionic partner
     3    /etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu bionic main universe restricted multiverse
     4    /etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu bionic-updates main universe restricted multiverse
     5    /etc/apt/sources.list:deb http://archive.ubuntu.com/ubuntu bionic-backports main universe restricted multiverse
     6    /etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu/ bionic-security main universe restricted multiverse

```

I am also now able to update!
```

jdosio@2io-01:~$ sudo apt-get update
[sudo] password for jdosio: 
Hit:1 http://archive.canonical.com/ubuntu bionic InRelease
Hit:2 http://archive.ubuntu.com/ubuntu bionic InRelease                                                                
Get:3 http://security.ubuntu.com/ubuntu bionic-security InRelease [88.7 kB]
Get:4 http://archive.ubuntu.com/ubuntu bionic-updates InRelease [88.7 kB]           
Get:5 http://archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]                    
Get:6 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [24.1 kB]
Get:7 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [681 kB]                      
Get:8 http://security.ubuntu.com/ubuntu bionic-security/main DEP-11 64x64 Icons [31.7 kB]
Get:9 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [41.2 kB]
Get:10 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 48x48 Icons [16.4 kB]      
Get:11 http://security.ubuntu.com/ubuntu bionic-security/universe DEP-11 64x64 Icons [102 kB]         
Get:12 http://security.ubuntu.com/ubuntu bionic-security/multiverse amd64 DEP-11 Metadata [2,464 B]
Get:13 http://archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [558 kB]                     
Get:14 http://archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [283 kB]
Get:15 http://archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [66.7 kB]
Get:16 http://archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [138 kB]
Get:17 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [969 kB]
Get:18 http://archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [953 kB]
Get:19 http://archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [250 kB]
Get:20 http://archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [192 kB]
Get:21 http://archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [422 kB]
Get:22 http://archive.ubuntu.com/ubuntu bionic-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:23 http://archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [7,224 B]
Fetched 4,992 kB in 2s (2,427 kB/s)                                   
Reading package lists... Done



```

---

### Post by again? on 2019-07-09
Sources list is fine.
You have the partner repo enabled but that's ok.
Do you get errors when running an upgrade?
```
sudo apt upgrade
```

---

### Post by jdosio on 2019-07-10
no error,
```

jdosio@2io-01:~$ sudo apt-get upgrade
[sudo] password for jdosio: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  dkms libllvm7 libllvm7:i386 libnvidia-common-390 libnvidia-common-430
  libnvidia-compute-390:i386 libnvidia-decode-390:i386
  libnvidia-encode-390:i386 libnvidia-fbc1-390:i386 libnvidia-gl-390:i386
  libnvidia-ifr1-390:i386 libwayland-client0:i386 libwayland-server0:i386
  libxnvctrl0 nvidia-prime nvidia-settings pkg-config screen-resolution-extra
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.



```

---

### Post by again? on 2019-07-10
**deb-src** repos can be disabled or removed unless you are compiling or looking at code.
I mostly remove them using software properties just to unclutter
```
software-properties-gtk --open-tab 1
```

According to post #10 you had 5 repo list files in  /etc/apt/sources.list.d/
```
**jdosio@2io-01:~$ ls /etc/apt/sources.list.d/**
dawidd0811-ubuntu-neofetch-bionic.list
dawidd0811-ubuntu-neofetch-bionic.list.save
google-chrome.list
google-chrome.list.save
graphics-drivers-ubuntu-ppa-bionic.list
graphics-drivers-ubuntu-ppa-bionic.list.save
steam.list
steam.list.save
wine-ubuntu-wine-builds-bionic.list
wine-ubuntu-wine-builds-bionic.list.save
```
They appear to be ok.
If you want updates from those repos, enable them using software-properties-gtk.
You would at least want the google-chrome repo for security concerns.
After enabling...
```
sudo apt update
sudo apt upgrade
```
Any errors, disable them and check which one is giving the error.

---

