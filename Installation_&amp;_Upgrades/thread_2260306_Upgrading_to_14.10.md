---
title: "Upgrading to 14.10"
date: 2015-01-10
forum: Installation &amp; Upgrades
---

### Post by Pradeep_Samji on 2015-01-10
Hi All,I am a windows user and very new to Ubuntu. I got a CD from a friend and just installed Ubuntu. The version I currently have is 11.04. I would like to upgrade. I have absolutely no idea how to do this. Do I have to download a distribution and do a fresh install or is there a way to directly do an upgrade to my existing installation? Please guide me. Since I have never used any flavors of Linux, please bear with me if my questions seem silly

---

### Post by grahammechanical on 2015-01-10
Is there any other OS on this machine? If not and if you have not used Ubuntu 11.04 very much so that there are few files that you need to back up, then a fresh install would be a good idea.

A new version of Ubuntu is released every six months in April and October. Every 2 years the April version is called a Long Term support (LTS) release and it is supported for 5 years. The versions in between now only have 9 months support. So, Ubuntu 11.10 is the next version after 11.04 but that, like 11.04 is no longer supported. It has reached end of life. You need to get to Ubuntu 12.04 LTS. That is still supported until April 2017. From 12.04 LTS you can upgrade directly to 14.04 LTS. That has support until April 2019.

It is possible to do this without doing a fresh install of 12.04 or 14.04 but a fresh install is best because you need to edit a system file. The system file is called "sources.list" and it lists the URLs of the servers that Ubuntu uses to update. You will need to change the URLs to the URL of the old-releases server.

Open a terminal and type

```
sudo gedit /etc/apt/sources.list
```

look for a line like this one that is from my sources.list file

> deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) vivid main restricted

"gb.archive.ubuntu.com" is the server. You may have some other server. It all depends upon the part of the world that you are living in. This is the change that you must make to every line that has gb.archive.ubuntu.com

> deb [http://old-releases.ubuntu.com/ubuntu/]("http://old-release.ubuntu.com/ubuntu/") vivid main restricted

Save the file and close the editor. Then run

```
sudo apt-get update
sudo apt-get upgrade
```

Then open Software Updater or Update Manager or whatever it is called in Ubuntu 11.04 and it should give you a button to click to upgrade to Ubuntu 11.10. You may be able to go straight away from 11.10 to Ubuntu 12.04 but you may need to edit the sources.list file in the same way, again.

I know this works because last week for an experiment I installed Ubuuntu 9.10 and I used this method to upgrade to 10.04 and then to 10.10.

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

One thing I suggest before you do this is to open the Additional Drivers utility and activate the open source video driver if you are using a proprietary video driver. One more thing. You have not told us the hardware specification of your machine. If the machine is of an age when Windows XP was being installed then it maybe that your machine is under powered for Ubuntu 14.04. You may need to install Xubuntu or Lubuntu instead.

Regards

P.S. Have you worked out by now not to upgrade to 14.10. It only has 9 month support and you will need to then upgrade to 15.04 and then to 15.10 and then to 16.04 LTS.

---

### Post by Pradeep_Samji on 2015-01-11
Thank you very much for your reply Graham. I will try the steps that you have suggested and post my results.

---

### Post by MAFoElffen on 2015-01-11
grahammechanical-- you pointed him to 15.04b instead of 14.10, like he had asked about...

To the OP- change all instances of lucid to utopic, instead of vivid. 

We are still testing Vivid... and it's not released as stable yet. Daily's can break things. I (and I expect Graham also) just expect that as part of the testing process.

---

### Post by nerdtron on 2015-01-11
If you have 11.04, Just download a new one. The current release would be 14.04 or 14.10. It would be safer than just installing an old and upgrading.

I want to remove some complication like terminal commands as much as possible because you are new here.

---

