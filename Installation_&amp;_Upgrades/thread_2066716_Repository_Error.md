---
title: "Repository Error"
date: 2012-10-05
forum: Installation &amp; Upgrades
---

### Post by steve oates on 2012-10-05
Whenever I use update-manager I get this message :-
Repository Error Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.
Can anyone help?
I'm using 
Ubuntu 10.04.4
2.6.32-43-generic (i686)
FireFox/TBird 15.0.1

---

### Post by sahabcse on 2012-10-05
sudo apt-get update and try to install the package.

As per the error information no packages in found in the repository url

[http://ppa.launchpad.net/mozillateam...86/Packages.gz](http://ppa.launchpad.net/mozillateam...86/Packages.gz)

---

### Post by Bucky Ball on 2012-10-05
Welcome. 

If that repo is generally reliable then maybe the server is just down and will be back online tomorrow. If not perhaps dig deeper. Especially if that's the only one acting up and this is the first problem it's given. ;)

---

### Post by steve oates on 2012-10-05
> **sahabcse said:**
> sudo apt-get update and try to install the package.

OK. I should have said that package updates and security updates don't fail. I just get those error messages every time the automatic update runs.


Output of  sudo apt-get update
W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu/dists/lucid/main/binary-i386/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.


>>As per the error information no packages in found in the repository url

[http://ppa.launchpad.net/mozillateam...86/Packages.gz](http://ppa.launchpad.net/mozillateam...86/Packages.gz)
..

---

### Post by Bucky Ball on 2012-10-05
Well switch the Mozilla team repo off as it looks broken. Software Sources and untick. (Depending on your flavour open Update Manager then click 'Setting' at the bottom left. Think the tab's 'Other Software.'

Find the offending repo and delete. Restart.

---

### Post by steve oates on 2012-10-05
> **Bucky Ball said:**
> Well switch the Mozilla team repo off as it looks broken. Software Sources and untick. (Depending on your flavour open Update Manager then click 'Setting' at the bottom left. Think the tab's 'Other Software.'

Find the offending repo and delete. Restart.

Thanks. That's cleared the errors. A while ago I put the lines :-
  [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu) lucid main
  [http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu](http://ppa.launchpad.net/mozillateam/thunderbird-stable/ubuntu) lucid main

into my software sources in Synaptic as advised on the Ubuntu website in order to get  the Ubuntu versions of Firefox and and Thunderbird. Does this mean that the UBUNTU versions are no longer supported on Lucid and I will have to go back to getting the packages from Mozilla ?

---

### Post by houseworkshy on 2012-10-05
I had problems with video in firefox some time ago so followed the advice here
[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247) Choosing the bit under removal and downgrade.  This worked, not only fixing video in flash but system wide.  I had been getting stalls in all video players on the system irrespective of whether firefox was open or not, vlc, totem playing files of all formats.  It had been a persistant problem for a couple of years which kicked in within a week or two of any Ubuntu install.  No idea why the above fixed it, but it was an extreemly welcome bonus, for a long time I'd had to boot into another OS if I wanted to watch videos.
Now when updateing I [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  fails.  Has been doing for a week or two.  Don't want to simply go back to the standard version of firefox and have the video problems back.  So is this repository gone or just down for a while and if gone is there some replacement?

---

### Post by steve oates on 2012-10-06
> **houseworkshy said:**
> I had problems with video in firefox some time ago so followed the advice here
[http://ubuntuforums.org/showthread.php?t=1712247](http://ubuntuforums.org/showthread.php?t=1712247) Choosing the bit under removal and downgrade.  This worked, not only fixing video in flash but system wide.  I had been getting stalls in all video players on the system irrespective of whether firefox was open or not, vlc, totem playing files of all formats.  It had been a persistant problem for a couple of years which kicked in within a week or two of any Ubuntu install.  No idea why the above fixed it, but it was an extreemly welcome bonus, for a long time I'd had to boot into another OS if I wanted to watch videos.
Now when updateing I [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  fails.  Has been doing for a week or two.  Don't want to simply go back to the standard version of firefox and have the video problems back.  So is this repository gone or just down for a while and if gone is there some replacement?

Hi. I've just noticed this. Looks like we haven't been using that PPA since January !!
[http://www.iloveubuntu.net/firefox-stable-ppa-abandoned-rapid-release-cycle-adopted-ubuntu-1004-and](http://www.iloveubuntu.net/firefox-stable-ppa-abandoned-rapid-release-cycle-adopted-ubuntu-1004-and)

"Due to the imminent release of Firefox 10 later next week that is to  replace Firefox 3.6.x (on Ubuntu 10.04 LTS), the Firefox stable PPA will  be **abandoned**, furthermore "[starting]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2012-January/001544.html")  on January 17, Ubuntu 10.04 LTS and Ubuntu 10.10 users will be migrated  to the latest Firefox version, and will track the rapid releases going  forward, as is currently done in newer releases of Ubuntu. This will  enable users to get the numerous improvements offered by new Firefox  versions".

---

### Post by houseworkshy on 2012-10-06
January ... gosh?  I must have been leaning more heavily on the other  drive than I thought; a fiddled around with Mepris, I'll have a peek at  the logs.  

I'll switch repros in the hope video problems don't  return and keep my fingers crossed for JDK when Java goes.  Not such a  big deal as it would have been now I've got my head round working in  something closer to debian, zero issues so far.

January??  and it's  October now.  I must be getting old.   Amazing how one doesn't even notice  oneself switch.  Thanks very much for replying to a 'help' on such an  out of date issue.

---

