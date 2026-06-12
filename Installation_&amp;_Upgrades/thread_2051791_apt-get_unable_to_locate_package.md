---
title: "apt-get unable to locate package"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by jon80 on 2012-09-02
I am trying to install packages using apt-get, however, I am consistently getting an error reading unable to locate package.

Has anyone else experienced a similar problem?  Is it possible that the packages are not searchable or that apt-get is querying a server and not finding the appropriate information?

I am asking this because I have tried the following commands and they were unsuccessful, whilst internet connection exists:

Installing KDE
sudo apt-get install kde-full  
sudo apt-get install kde-standard

Installing nmap
sudo apt-get install nmap

Installing Java Development Kit 1.7 (jdk 1.7)
sudo apt-get openjdk-7-jdk

Installing Yum
sudo apt-get install yum

On a virtual machine within the same network (with connection to the Internet), a version of Ubuntu is running and I tried to install Wine, according to the instructions at [http://www.winehq.org/download/ubuntu:](http://www.winehq.org/download/ubuntu:)

sudo apt-get install wine1.5

The following error is displayed:
Package 'wine1.5' has no installation candidate.

Initially I updated and upgraded apt-get by running the following command, even, though during the installation wizard security updates were selected to be automatically updated:

sudo apt-get install update
sudo apt-get upgrade

This process takes a while.

---

