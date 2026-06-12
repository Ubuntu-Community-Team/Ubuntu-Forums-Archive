---
title: "How to install python-gnome2-extras???"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by adnan_wns on 2010-05-01
hi

I have been using usbadslmodemmanager(speedtouch 330) driver for last 4 months in karmic and it was working fine but now I have installed Lucid and it is not working because it depends on **python-gnome2-extras**.

I have tried this:

adnan@adnan-laptop:~$ sudo apt-get install python-gnome2-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package python-gnome2-extras is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  python-gtkspell python-gtkmozembed python-gksu2 python-gdl python-gda python-eggtrayicon
E: Package python-gnome2-extras has no installation candidate


now what to do ???

---

### Post by fomaa on 2010-05-05
I have same problem.
[http://packages.ubuntu.com/lucid/python-gnome2-extras](http://packages.ubuntu.com/lucid/python-gnome2-extras) page is entered with an error.

---

### Post by RodGer GR on 2010-05-25
We are three! I hope somebody finds an answer.

---

### Post by DJ_Peng on 2010-05-27
I ran into the same problem with Webilder and discovered Bug #572040: [can't install in Ubuntu 10.04 because python-gnome2-extras deprecated]("https://bugs.launchpad.net/blogtk/+bug/572040").
> python-gnome2-extras has been split up into smaller packages in Ubuntu 10.04 Lucid Lynx and BloGTK 2.0 cannot be installed via the repository because of that.
 While that bug specifically refers to BloGTK it identifies the problem in a number of apps. Your best solution would be to contact the devs and/or maintainers for your apps and let them know about the change in python-gnome2-extras so they can fix the code to reflect the way the extras are now available.

---

### Post by dino99 on 2010-05-27
some changes have been done:

[https://bugs.launchpad.net/gdecrypt/+bug/509166](https://bugs.launchpad.net/gdecrypt/+bug/509166)

[http://packages.debian.org/lenny/python-gnome2-extras](http://packages.debian.org/lenny/python-gnome2-extras)
[http://packages.debian.org/sid/python-gnome2-extras](http://packages.debian.org/sid/python-gnome2-extras)

---

### Post by DJ_Peng on 2010-05-28
Thanks for the links, dino. I tried to install it from Lenny and Synaptic wanted to remove other apps I use. I'm afraid that as of right now I'm unable to install python-gnome2-extras in lucid, which stinks because I really want to reinstall Webilder.

---

### Post by infinitejones on 2010-06-14
I just successfully built Webilder from source on Lucid, by downloading and compiling python-gnome2-extras from source.

Basic instructions:

As per the Webilder download page, run
```
apt-get install python python-gtk2-dev python-gnome2 python-gnome2-dev libglib2.0-dev python-gnome2-extras-dev python-imaging
```
(note I've deleted python-gnome2-extras from that list - all the others can be installed)

Download the latest .tar.gz file from this page: [http://ftp.gnome.org/pub/GNOME/sources/gnome-python-extras/2.25/]("http://ftp.gnome.org/pub/GNOME/sources/gnome-python-extras/2.25/")

It was 2.25.3 when I did it, but it might not be when you read this. It tells you at the top of the list which one is the latest.

In the folder where you downloaded it:

```
tar -zxvf gnome-python-extras-2.25.3.tar.gz
cd gnome-python-extras-2.25.3.tar.gz
./configure
make
sudo make install
```

Then from the [Webilder download page]("http://www.webilder.org/download.html") download the source from this link:

[http://www.webilder.org/static/downloads/Webilder-0.6.5.tar.gz]("http://www.webilder.org/static/downloads/Webilder-0.6.5.tar.gz")

Then on the download page, go to part 2 of the Manual Install section and follow those instructions. I had to put sudo in front of the last one (python setup.py install --install-data=/usr) even though I'd typed su and entered my password before that. Not sure why.

Then, right click on a blank area of the panel, click Add to Panel, and it'll be down at the bottom of the list. 

It's working just fine for me, right now!

---

### Post by BloGTK on 2010-06-15
It's probably easier to manually add all the components that were in the old python-gnome2-extras package - i.e.

```
sudo apt-get install python-gtkspell python-gtksourceview2 ...
```

I don't remember what specific packages were in the old python-gnome2-extras metapackage, but installing them individually would fix any problems.

---

