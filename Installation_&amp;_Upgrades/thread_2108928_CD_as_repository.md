---
title: "CD as repository"
date: 2013-01-26
forum: Installation &amp; Upgrades
---

### Post by cyanidetaco on 2013-01-26
Installed 12.04 ubuntu at my house which currently has no internet access at the moment. was wondering if there was a way for me to load packages onto a cd then use the software center to install all dependencies along with the programs. Currently using Windows at a mate's so would need to make the cd with his OS.

I know the install cd has some things, but I need a Genesis emulator, dosbox, fluxbox, etc.. All packages found on launchpad built for ppc ubuntu 12.04

---

### Post by purity89 on 2013-01-26
I think you should be able to use the method described here: [http://askubuntu.com/a/129543](http://askubuntu.com/a/129543)

Just boot a Live CD, and run the commands from Ubuntu. Then put the files on a USB drive or burn them to a CD/DVD and execute the two last commands on your machine.

I have quoted the method below, for simplicity. 

I don't know how this would integrate with the Software Center though. Maybe you could add the CD/USB directory as a repository or something... Someone more clever than me might be able to help you with that. 

If my mind serves me right you might be able to open and install the .deb files in Software Center just by double clicking them. I don't know how this would work with regards to dependencies though.

> 
**Step 1:** Get the download URLs in a file :

Execute the following command replacing package-names with required ones, separating by a space.

```
apt-get -y install --print-uris package-name | cut -d\' -f2 | grep http:// > apturls
```

**Step 2:** Copy this file (apturls) to a machine which has high-speed Internet access, and execute the following command to download the packages:

```
wget -i path-to-apturls-file 
```
[B]
Step 3:[/B] Now get those downloaded packages to your machine, and install them using :

```
cd path-to-the-downloaded-packages-directory

sudo dpkg -i *.deb
```

Done!


---

### Post by ibjsb4 on 2013-01-26
There are several ways to install packages without the internet.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+package+without+internet&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+package+without+internet&as_qdr=all&sa=Google+Search&lang=en)

Or buy the works.

[http://www.osdisc.com/products/linux/ubuntu/ubuntu-1204-lts-software-repository-64bit-pc.html](http://www.osdisc.com/products/linux/ubuntu/ubuntu-1204-lts-software-repository-64bit-pc.html)

---

