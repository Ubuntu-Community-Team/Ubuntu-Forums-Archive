---
title: "Firefox is still 3.6 after upgrading from 10.10 to 11.10?"
date: 2012-04-10
forum: Installation &amp; Upgrades
---

### Post by ledzepjes on 2012-04-10
as the title says, I just upgraded Ubuntu from 10.10, where in help-->about Firefox says it was 3.6, now after upgrading to Ubuntu 11.10, in help-->about, Firefox still states it's 3.6? and it crashes all the time, which is primarily the only reason I upgraded Ubuntu, since I like gnome 2, (getting used to unity, it's actually nice as well, I would like the option to use both imho) but now that I've upgraded Ubuntu, it's not upgraded my Firefox, which was the whole point of this mess, ugghhh

when I go into synaptic package manager (luckily that's still there) I see Firefox is version 11???

when I went to add the stable ppa, and sudo apt-get update, it fails on the firefox part, so I disabled it in the repos

1) how can I upgrade my firefox?

2) and, if I want to, like in Windows, how do I incrementally upgrade, like from 3.6-5-7 then to 11? instead of letting Ubuntu dictate what version I get upgraded to and when?

---

### Post by raja.genupula on 2012-04-10
open your terminal 

```
sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa
sudo apt-get update && sudo apt-get install firefox
```

and do the following .

---

### Post by ledzepjes on 2012-04-10
this is what I got:


```
sudo add-apt-repository ppa:ubuntu-mozilla-security/ppa
You are about to add the following PPA to your system:
 PPA for Ubuntu Mozilla Security Team
 Mozilla Security/Stability testing archive for ubuntu
 More info: [https://launchpad.net/~ubuntu-mozilla-security/+archive/ppa]("https://launchpad.net/%7Eubuntu-mozilla-security/+archive/ppa")
Press [ENTER] to continue or ctrl-c to cancel adding it

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /tmp/tmp.Orxq5HoVGF --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver hkp://keyserver.ubuntu.com:80/ --recv AF316E81A155146718A6FBD7A6DCF7707EBC211F
gpg: requesting key 7EBC211F from hkp server keyserver.ubuntu.com
gpg: key 7EBC211F: public key "Launchpad PPA for Ubuntu Mozilla Security Team" imported
gpg: no ultimately trusted keys found
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)

then I typed:

sudo apt-get update && sudo apt-get install firefox
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric InRelease
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric InRelease
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release.gpg
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric Release   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release.gpg             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric Release  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages              
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main TranslationIndex           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates Release                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources                   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Sources                   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Sources               
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Sources             
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe i386 Packages         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted TranslationIndex
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe TranslationIndex      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Sources       
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Sources           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Sources     
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe i386 Packages 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main i386 Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main TranslationIndex  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/main Translation-en            
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/restricted Translation-en      
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) oneiric-updates/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Translation-en
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
The following package was automatically installed and is no longer required:
  erlang-base
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

---

### Post by lovinglinux on 2012-04-10
> **ledzepjes said:**
> 
1) how can I upgrade my firefox?


The *firefox-stable* ppa is deprecated. It was used to provide new Firefox versions to Maverick and Lucid, but now all repositories are updated with Firefox 11.

Please also remove *ubuntu-mozilla-security* ppa. There is no reason to use that. You problem is something else.

Please attach the firefox-report.txt file generated in your desktop after running the commands below:

```

echo 'Ubuntu Architecture' > ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
uname -a >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Ubuntu Version' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
cat /etc/lsb-release >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox Packages' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
dpkg --get-selections | grep 'firefox*' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox binaries' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
which firefox >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox >> ~/Desktop/firefox-report.txt
file /usr/local/bin/firefox >> ~/Desktop/firefox-report.txt
file /opt/firefox/firefox >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Firefox divertion' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
file /usr/bin/firefox.ubuntu >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
echo 'Sources' >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
ls /etc/apt/sources.list.d >> ~/Desktop/firefox-report.txt
echo '' >> ~/Desktop/firefox-report.txt
firefox ~/Desktop/firefox-report.txt
```


> **ledzepjes said:**
> a2) and, if I want to, like in Windows, how do I incrementally upgrade, like from 3.6-5-7 then to 11? instead of letting Ubuntu dictate what version I get upgraded to and when?

You don't. There is no such thing. Since Firefox 4, when a new version is released the older one becomes deprecated. So, there is no more Firefox 4,5,6,7,8,9 or 10. There is only Firefox 11. You can freeze the update of Firefox package using Synaptic, but then you will be using a unsupported version that has security issues. What you can do is install Firefox ESR, which is the equivalent of Ubuntu LTS. See [http://www.tuxgarage.com/2012/02/installing-firefox-esr-in-ubuntu-linux.html](http://www.tuxgarage.com/2012/02/installing-firefox-esr-in-ubuntu-linux.html)

---

### Post by ledzepjes on 2012-04-11
Lovinglinux Here is the output:

[PHP]Ubuntu Architecture

Linux ubuntu-01 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 athlon i386 GNU/Linux

Ubuntu Version

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"

Firefox Packages

firefox                        install
firefox-globalmenu                install
firefox-locale-en                install

Firefox binaries

/usr/bin/firefox
/usr/bin/firefox: symbolic link to `/opt/firefox/firefox'
/usr/local/bin/firefox: ERROR: cannot open `/usr/local/bin/firefox' (No such file or directory)
/opt/firefox/firefox: POSIX shell script text executable

Firefox divertion

/usr/bin/firefox.ubuntu: symbolic link to `../lib/firefox-11.0/firefox.sh'

Sources

alexandr-surkov-xbmc-pvr-maverick.list.save
bisigi.list.distUpgrade
bisigi.list.save
bisigi-ppa-maverick.list.distUpgrade
bisigi-ppa-maverick.list.save
bisigi-ppa-natty.list.save
breathe-dev-ppa-maverick.list.distUpgrade
breathe-dev-ppa-maverick.list.save
breathe-icon-theme.list.distUpgrade
breathe-icon-theme.list.save
google-chrome.list.distUpgrade
google-chrome.list.save
medibuntu.list
medibuntu.list.distUpgrade
medibuntu.list.save
moovida.list.distUpgrade
moovida.list.save
moovida-packagers-ppa-karmic.list.distUpgrade
moovida-packagers-ppa-karmic.list.save
mozillateam-firefox-stable-oneiric.list
mozillateam-firefox-stable-oneiric.list.save
openshot.developers-ppa-maverick.list.distUpgrade
openshot.developers-ppa-maverick.list.save
openshot.developers-ppa-natty.list
openshot.developers-ppa-natty.list.distUpgrade
openshot.developers-ppa-natty.list.save
openshot.list.distUpgrade
openshot.list.save
opera.list.distUpgrade
opera.list.save
playdeb.list.distUpgrade
playdeb.list.save
playonlinux.list
playonlinux.list.distUpgrade
playonlinux.list.save
shutter.list.distUpgrade
shutter.list.save
shutter-ppa-maverick.list.distUpgrade
shutter-ppa-maverick.list.save
shutter-ppa-natty.list
shutter-ppa-natty.list.distUpgrade
shutter-ppa-natty.list.save
skype.list.distUpgrade
skype.list.save
team-xbmc-unstable-maverick.list.distUpgrade
team-xbmc-unstable-maverick.list.save
team-xbmc-unstable-natty.list
team-xbmc-unstable-natty.list.distUpgrade
team-xbmc-unstable-natty.list.save
tualatrix-ppa-maverick.list.distUpgrade
tualatrix-ppa-maverick.list.save
tualatrix-ppa-natty.list
tualatrix-ppa-natty.list.distUpgrade
tualatrix-ppa-natty.list.save
ubuntu-mozilla-security-ppa-oneiric.list
ubuntu-tweak-stable.list
ubuntu-tweak-stable.list.distUpgrade
ubuntu-tweak-stable.list.save


[/PHP]and what about Webpage developers that would like to be running different versions of a web-browser to test their work across them? does ESR allow you to do that? and have them installed and multiple versions running at the same time?

---

### Post by lovinglinux on 2012-04-11
Here is the fix to your problem:

```
sudo rm -fr '/opt/firefox' && sudo rm -f '/usr/bin/firefox' && sudo dpkg-divert --rename --remove '/usr/bin/firefox'
```


If you need to run multiple versions of Firefox you can run the ESR or the regular Firefox installed by the package manager and download the old versions from  Mozilla and install in them in the home directory. A simpler alternative, which is what I use and develop, is to use [FoxTester](https://addons.mozilla.org/en-US/firefox/addon/foxtester/).

---

### Post by dino99 on 2012-04-11
having too many ppa (and some be outdated) is clearly not a good idea; clean the room ;)
you can use ppa-purge to remove the unwanted one 

deleting .local folder then log out/in will recreate a clean one.

then open synaptic, reload the archives, select firefox & from the menu, click on "package" to force the Oneiric Firefox version.

---

### Post by ledzepjes on 2012-04-11
Dino99, I thought my ppa's were all disabled, I was using ubuntu tweak in 10.10 and went through and deleted or disalbed all of them before the upgrade process. Are they not stored in sources.list any more? or were they ever, I see that there are a lot in the /etc/apt/sources.list.d folder, if I delete them from there, are they gone? and what about the repositories in synaptic package manager, I don't see any listed for Oneiric? where or what file has all the repositories? and/or ppa's?

Lovinglinux, won't that just remove my currently installed firefox files and folders, will it still be in synaptic somewhere? I will have to try the code after work, and after I do my taxes, get back with you guys in a day or two :-) thanks

and what about ESR, does it allow for usage like BSD where you can install multiple versions? of any software, not just firefox? I'll have to read up with Opera, if I open the link [http://www.tuxgarage.com/2012/02/ins...ntu-linux.html]("http://www.tuxgarage.com/2012/02/installing-firefox-esr-in-ubuntu-linux.html") my firefox crashes, ha, virtually any page that isn't from the ubuntu forums or a text file from my desktop and firefox will eventually crash, very strange

---

### Post by lovinglinux on 2012-04-11
> **ledzepjes said:**
> Lovinglinux, won't that just remove my currently installed firefox files and folders, will it still be in synaptic somewhere? I will have to try the code after work, and after I do my taxes, get back with you guys in a day or two :-) thanks

That will remove version 3.6 that you have installed manually in the /opt folder. You have diverted firefox binary to it, so when you start Firefox, you actually launch 3.6 instead of Firefox 11. Don't worry, Firefox 11 is already installed and will kick in once you use the command I gave you.

Also don't worry about personal settings, since they are stored in the profile folder in your home. BTW, is a good idea to backup your ~/.mozilla folder, in case you find some incompatibilities. Sometimes the bookmark database gets corrupted when upgrading to Firefox 11 from 3.6. Additionally, some old extensions might be disabled due to incompatibility. If that happens let me know.


> **ledzepjes said:**
> and what about ESR, does it allow for usage like BSD where you can install multiple versions? of any software, not just firefox? I'll have to read up with Opera, if I open the link [http://www.tuxgarage.com/2012/02/ins...ntu-linux.html]("http://www.tuxgarage.com/2012/02/installing-firefox-esr-in-ubuntu-linux.html") my firefox crashes, ha, virtually any page that isn't from the ubuntu forums or a text file from my desktop and firefox will eventually crash, very strange

Proceed with the removal of Firefox 3.6 and that problem will probably go away.

If you follow the tutorial from the link, it will install Firefox ESR in the /opt folder, exactly like you have 3.6 now. It won't completely replace Firefox, but will launch instead of the one updated from the repositories. Keep in mind that you will have to download updates for it manually. So, unless you are comfortable with this method, is not a very a very good option. Just stick   with the regular Firefox from the repos and use FoxTester if you need to test different versions. Keep in mind FoxTester is for testing an not for daily Firefox usage.

---

### Post by ledzepjes on 2012-04-12
Dino99, about ppa-purge, throughout the upgrade process, starting with 10.10 ->11.04->11.10 I tried to install ppa-purge, but each time I try to install it, it comes back with an error or 0 packages installed

I did try with each upgrade, with Ubuntu Tweak, to remove all the ppa's, and I thought I had done so, so it wouldn't interfere with the upgrade process. Are they or have they always been kept in the sources.d folder? if I just delete them from there are they gone from the system? but then what happens to the programs I have installed with them, those programs are then ghost programs and are uninstallable then correct? until I add the ppa's back?

---

### Post by ledzepjes on 2012-04-12
I've noticed unity crash on my several times.

I press ctrl+alt+F6 and login, then type:
unity --release
then press ctrl+alt+F7 to get back to my home shell, and unity comes back

---

### Post by ledzepjes on 2012-04-12
lovinglinux I did your command

sudo rm -fr '/opt/firefox' && sudo rm -f '/usr/bin/firefox' && sudo dpkg-divert --rename --remove '/usr/bin/firefox'
and it did exactly like you said, the old version of firefox 3.6 is gone, and I am writing this on firefox 11! all the addon's, including scrapbook and others are still here! (did a backup just in case)

but, now when I open opera, it sometimes crashes, and it's the latest version 11, I'm wondering if I may have a memory issue, off to run memtest

I do know that the hard drive has some read/write errors according to "disk utility" (nice handy little tool), I'm thinking it's either a memory or hard drive issue, and if it's hard drive then it could be corrupting the swap

but, that's for another post, thanks everyone, my issue upgrading firefox is solved

---

### Post by lovinglinux on 2012-04-13
> **ledzepjes said:**
> lovinglinux I did your command

sudo rm -fr '/opt/firefox' && sudo rm -f '/usr/bin/firefox' && sudo dpkg-divert --rename --remove '/usr/bin/firefox'
and it did exactly like you said, the old version of firefox 3.6 is gone, and I am writing this on firefox 11! all the addon's, including scrapbook and others are still here! (did a backup just in case)

but, now when I open opera, it sometimes crashes, and it's the latest version 11, I'm wondering if I may have a memory issue, off to run memtest

I do know that the hard drive has some read/write errors according to "disk utility" (nice handy little tool), I'm thinking it's either a memory or hard drive issue, and if it's hard drive then it could be corrupting the swap

but, that's for another post, thanks everyone, my issue upgrading firefox is solved

You are welcome.

About the new problem, try to delete ~/.opera/operaprefs.ini file. Make a backup first.

Also, start a new Opera profile to see if the problem persists. You can do that from terminal using the -pd switch (personal directory). For example:

```
opera -pd ~/.operatest
```

---

