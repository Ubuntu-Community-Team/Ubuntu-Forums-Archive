---
title: "upgrading last 10.04 box to 12.04 went sideways..."
date: 2012-08-29
forum: Installation &amp; Upgrades
---

### Post by nariub on 2012-08-29
sudo apt-get update
sudo apt-get upgrade

sudo do-release-upgrade

> Processing was halted because there were too many errors.
i do not have the new kernels 
vmlinuz-2.6.32-42-generic is newest in /boot

Is there some way to complete this?

I am a bit wary of rebooting it now..

tried mounting the alternative iso 

sudo mount -o loop /home/marione/Downloads/Torrents/Download/Ubuntu/12.04/ubuntu-12.04.1-alternate-amd64.iso /media/cdrom0

tried online and offline and they all stop in the same place..  
indicating too many errors to complete

edit again
I should have been even more wary of rebooting..
durp..  I did.. she aint coming back up..  I see the splash.. and services coming up.. then she freezes and is not pingable on my network anymore.

Do i attempt recovery with 12.04 or 10.04 disc?

---

### Post by nativehound on 2012-08-29
Read this.

[https://help.ubuntu.com/community/PreciseUpgrades]("https://help.ubuntu.com/community/PreciseUpgrades")

---

### Post by nariub on 2012-08-30
Thanks,
  looked at the link and the release notes 
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

It says that you can use the LiveDesktopCD (connected to the Internet) to install/re-install 

I am wondering.. can i use that to rescue my baby?

I am interpreting install as "format the harddrive and start anew"
I am interpreting re-install as more of a I have detected a version of Ubuntu on the HD and will attempt to reinstall over the top of it (repair) 

I have no basis for this interpretation, other than my wishful thinking.

BTW, I can get to a character terminal on the box, it no longer has an eth0 interface or xwindows.. poor little crippled fellow..  I plan to pull my data off to a USB drive and "install" 12.04 this weekend if i cannot rescue it..   This one has been with me since 9.10 and I was so looking forward to putting another LTS on it and letting it sit for 5years.

---

### Post by nariub on 2012-08-30
This link

[http://www.liberiangeek.net/2012/04/upgrade-to-ubuntu-12-04-from-11-10-using-ubuntu-cd-dvd/]("http://www.liberiangeek.net/2012/04/upgrade-to-ubuntu-12-04-from-11-10-using-ubuntu-cd-dvd/")

seems to indicate i can boot from a 12.04 desktop image
and it will detect the existing 10.04 installation and offer to perform an update from 10.04LTS to 12.04LTS

I have such a disc and booted it 
it sees the network and my 10.04 installation and graciously offers to erase it and install over the top in a destructive fashion..

it does -not- however offer to upgrade in place. as the url above seems to indicate it will.. did i need do download and burn the DVD image for that?

booting the alternative iso
does not give me the option to upgrade existing 10.04
rescue mode fails to see any partitions on my harddrive.

..
ifconfig fails to see eth0, so continuing the do-release upgrade isn't going to work

sudo apt-get -f dist-upgrade  says it needs another 1,188kB of downloads, craters if i tell it to go ahead.
put the alt cd in and 
sudo apt-cdrom add 
and try again, she says she cannot find the repos
try again with --fix-missing and she still fails

 $ sudo dpkg --configure -a
fails too. Same as the install too many errors and an abort

sudo apt-get -f install 
  says it need 341kBs and also aborts..

---

### Post by nariub on 2012-09-01
dug up a 10.04.4 alt x64 iso
and booted from it..

used rescue to login to the root partition

apt-get -f install worked because eth0 was there..
dpkg --configure -a ??  i did it ... don't know if it did anything

rebooted to get off the alt disc

xwindows still not working

CNTL-ALT-F1 to get to a terminal
sudo do-release-upgrade is running again..

should have a verdict in a few

---

### Post by nariub on 2012-09-01
alrighty then,

after rescuing with the 10.04.4 alt disc
and rebooting
CNTL-ALT-F1 into a terminal session (xwindows wasnt working)
and sudo vi /etc/apt/sources.list 
removing those pesky cdrom references i put in there previously

then doing sudo do-release-upgrade
which errored out with libc6 and initramfs errors
rather than exit I chose to ressurect the session
it went through and installed everything..

rebooted into 12.04 perfectly..

woop woop  I am now a very 'precise' gentleman.
and I have no more lucidity

Marking this one solved..

---

