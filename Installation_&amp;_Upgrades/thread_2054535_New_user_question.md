---
title: "New user question"
date: 2012-09-07
forum: Installation &amp; Upgrades
---

### Post by jmorr24 on 2012-09-07
Hello All, just started using ubuntu yesterday and I love it.  One question though, when downloading new software, where is it actually downloading from as there is no url or ip address?

Ex. - sudo add-apt-repository ppa:webupd8team/themes
sudo apt-get update
sudo apt-get install zukitwo-gtk-theme zukitwo-brave-gtk-theme

When getting the install it just says what to get, but not where to get it from, so 1. Where does the file come from and 2.  How does it know where to get the file?

Thanks for your time and help,
Jmorr

---

### Post by Petro Dawg on 2012-09-07
My best guess is that the ppa is an abbreviated web address, perhaps [http:/ppa.launchpad.net/webupd8team/themes]("http://ppa.launchpad.net/webupd8team/themes/")

After adding the ppa, apt-get will then search it for the program name entered.

---

### Post by Frogs Hair on 2012-09-07
The PPA is Here.[https://launchpad.net/~webupd8team/+archive/themes](https://launchpad.net/~webupd8team/+archive/themes)

When you add the repository it becomes part of your software sources and when you update that repository along with the default repository is checked for updates. I have a number of themes PPAS because they update automatically and this saves a lot of work.

---

### Post by grahammechanical on 2012-09-07
I assume that you are using Precise Pangolin (A.K.A. 12.04). It helps to know.

With Ubuntu we have software repositories - servers where the software is stored. It is from those repositories the updates and actual applications/programs are downloaded and then installed.

Go to the power cog menu and select Software Updater. When the utility opens click on the Settings button. Go to the Ubuntu Software tab and the Other Software tab. Those tabs will tell you where the software is being downloaded from.

You can also download compressed files of software from where ever you may get it from but it is always better to use the Ubuntu Software Centre to get the applications you want as the applications there are adjusted a little bit to work better with Ubuntu.

Regards.

---

### Post by papibe on 2012-09-07
Hi jmorr24. Welcome to the forums ):P

Ubuntu works with pre determine 'repositories' where you can download software from. If you are interested in seeing the list of repositories do this: open the 'Software Center' then select Edit -> Software Sources. Your software will be downloaded form where it says 'Download from' (first tab), and from the list on the tab named 'Other Software'.

This command:
```
 sudo add-apt-repository ppa:webupd8team/themes
```
will be adding a new line on the 'Other Software' tab.

This one:
```
sudo apt-get update
```
will update the list of software available for installation, and finally this one:
```
sudo apt-get install zukitwo-gtk-theme zukitwo-brave-gtk-theme
```
will actually download and install the software.

Does that help a little?
Regards.

---

### Post by jmorr24 on 2012-09-07
Awesome, thanks to you and everyone else who commented.
So one more question, when I run the command
sudo apt-get update
How does it know which software to update?  Is it for all repositories or just the one I created?

---

### Post by cortman on 2012-09-07
> **jmorr24 said:**
> Awesome, thanks to you and everyone else who commented.
So one more question, when I run the command
sudo apt-get update
How does it know which software to update?  Is it for all repositories or just the one I created?

apt-get update simply updates the lists of available software on the repository; it doesn't touch any programs at all. It does update the lists for all repositories that came with your system and ones that you have added.
apt-get upgrade upgrades all packages on your computer to the latest version. If it's not on your computer, it doesn't (obviously) get upgraded.

---

