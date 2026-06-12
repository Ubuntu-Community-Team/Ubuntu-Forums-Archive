---
title: "Installing Google chrome and Dropbox through terminal"
date: 2014-08-04
forum: Installation &amp; Upgrades
---

### Post by tom119 on 2014-08-04
I would like to run a bash-script after the installation of lubuntu where, so that the software I want is installed automatically. Now, I would like to know what terminal command do I use to install
- Google Chrome
- Dropbox
- Skype

also if anyone knows:
How can I put a "info.txt" on the desktop by a bash-shell-script?

Thanks

---

### Post by tom119 on 2014-08-04
I now did it "myself". Thanks for reading.

```
#install Google Chrome and Dropbox
cd ~/
mkdir extra0123
cd extra0123
wget -c https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
wget -c https://www.dropbox.com/download?dl=packages/ubuntu/dropbox_1.6.0_amd64.deb
sudo dpkg -i *.deb
cd ..
rm -rf extra0123

#Installing Skype
sudo dpkg --add-architecture i386
sudo add-apt-repository "deb http://archive.canonical.com/ $(lsb_release -sc) partner"
sudo apt-get update && sudo apt-get install -y skype

#make file on Desktop
touch ~/Desktop/info.txt

#write into file on desktop
echo "line 1
line 2
line 3" >> ~/Desktop/info.txt | sudo -s

```

---

### Post by ian-weisser on 2014-08-05
The Chromium browser, and dropbox-nautilus integration (which includes Dropbox) are both already in the Ubuntu repositories.
That would simplify your script.

Using sudo in a shell script is unwise. Run the entire script as sudo instead.

I don't see the need for a script. You really only need to know three package names.
```
sudo apt-get install chromium-browser skype nautilus-dropbox
```
You don't even need to *remember* the package names. You can install the services from Software Center as you need them by searching for the service name....

---

### Post by HL84 on 2014-08-05
- Chromium isn't the same as Chrome
- nautilus isn't part of Lubuntu afaik. so nautilus-dropbox doesn't make sense.
- why not use a script to install 30 apps at once after a reinstall. software center takes way more time.

(it's my thread btw. this is an older account of me.)

---

### Post by ian-weisser on 2014-08-06
Sure, those are perfectly valid points. I missed that you were using Lubuntu (lower-case 'l' is so easy to miss).

> **HL84 said:**
> - why not use a script to install 30 apps at once after a reinstall. 

You can...it's entirely a matter of preference.
To me, it's a question of 'why?' instead of 'why not?'

When I reinstall, I deliberately don't install the same applications...until my workflow needs them. Several never get installed, or something new replaces them.
 
For multiple installs, like in an office where you need uniformity, a preseed file can be even easier than a script.

---

### Post by David_Wright on 2014-08-06
> **HL84 said:**
> - nautilus isn't part of Lubuntu afaik. so nautilus-dropbox doesn't make sense.


Coincidentally, I finalled installed Dropbox on Lubuntu last night.  Despite having the same concerns that "*nautilus-dropbox*" implies that it would not work in Lubuntu, it actually appears to work perfectly - ie, the Dropbox icon appears in the taskbar and PCManFM can be used to navigate all of the dropbox folders.

Perhaps a better package name would help.

---

