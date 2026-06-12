---
title: "[SOLVED] ubuntu install dvd vs repository dvd"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by Circus-Killer on 2008-02-04
**Problem:** I need to do a fresh install of Ubuntu. After the fresh install I need to install the Vodafone Mobile Connect Driver for Linux. The problem is that the Vodafone thingum has dependencies. I have no other way to connect to the Internet, only have 3G. I need a connection in order to get the dependencies so that I can install the Vodafone software.

**Question:** So now my question is, if I want to install the dependencies required, do I need the repository dvd or the install dvd?

---

### Post by Partyboi2 on 2008-02-04
I would say use the repository dvd. Or if you know already what packages you require you could download and save them to cd or usb before you reinstall.

---

### Post by hyperair on 2008-02-04
First of all you need to find out what packages are depended upon by the Vodafone Mobile Connect thing. Then run this command:
```
sudo apt-get install <packages> --print-uris > ~/Desktop/files.txt
```

Then go to a computer with a network connection and download the files. After you're done, copy everything to /var/cache/apt/archives.

---

### Post by Circus-Killer on 2008-02-04
okay, well, i'm not at home at the moment, so i can't run that command, but i do know off-hand that the dependcies are all python extensions.

do you guys think that the required python extensions would be on the install dvd?

---

### Post by hyperair on 2008-02-04
No idea really. But it's worth a try.

---

### Post by Circus-Killer on 2008-02-05
okay, well, the packages i need are as follows:

[LIST=1]
[*]python-dbus
[*]python-twisted
[*]python-serial
[*]python-glade2
[*]python-pysqlite2
[*]wvdial
[*]nozomi-source
[*]python-notify
[*]python-gnome2-extras
[/LIST]

does anyone perhaps know how i can find out if those packages are on the dvd or not?

---

### Post by zvacet on 2008-02-05
Why don´t you look in **var/cache/apt/archives **and see if these packages are there?If they are simply copy them to CD or stick and install them again after you do fresh install.

---

### Post by hyperair on 2008-02-05
```
apt-get install python-dbus python-twisted python-serial python-glade2 python-pysqlite2 wvdial nozomi-source python-notify python-gnome2-extras --print-uris
```

Get the output from that and download all the url's specified. Then put them into your /var/cache/apt/archives folder, and then install the deb by double clicking on it. The dependencies will be "downloaded" but since it's all in the cache, nothing is really downloaded, but just fetched from the cache.

---

### Post by Circus-Killer on 2008-02-05
> **zvacet said:**
> Why don´t you look in **var/cache/apt/archives **and see if these packages are there?If they are simply copy them to CD or stick and install them again after you do fresh install.

As stated in my first post, i'm working from a freh install, so the packages are not in /var/cache/apt/archives. Currently, I'm posting this message from my work computer that runs Windows.

---

### Post by hyperair on 2008-02-05
Uhm I'm fairly sure that what I just said would work. Try it out won't you.

---

### Post by Circus-Killer on 2008-02-05
> **hyperair said:**
> ```
apt-get install python-dbus python-twisted python-serial python-glade2 python-pysqlite2 wvdial nozomi-source python-notify python-gnome2-extras --print-uris
```

Get the output from that and download all the url's specified. Then put them into your /var/cache/apt/archives folder, and then install the deb by double clicking on it. The dependencies will be "downloaded" but since it's all in the cache, nothing is really downloaded, but just fetched from the cache.

thanks for that tip. think i'll first try the ubuntu dvd repository, otherwise i'll have to do it the way you suggested. its a bit of a mission, but i gotta do what i gotta do.

---

### Post by Circus-Killer on 2008-02-05
One last question about getting the URL's for the dependencies. Usually to install the required package along with dependencies, I execute the following two commands:

```

sudo dpkg -i <package>.deb
sudo apt-get install -f

```

the first command kicks back dependencies errors, the second installs the dependencies and the package named in the first command.

my question is, if i change the second command to:
```
sudo apt-get install -f --print-uris
```
will it still print out the URL's for the packages i need?

---

### Post by zvacet on 2008-02-05
If you are runing windows righ now [this](http://www.nonetdebs.homeip.net/) can help you.

---

### Post by hyperair on 2008-02-05
> **Circus-Killer said:**
> One last question about getting the URL's for the dependencies. Usually to install the required package along with dependencies, I execute the following two commands:

```

sudo dpkg -i <package>.deb
sudo apt-get install -f

```

the first command kicks back dependencies errors, the second installs the dependencies and the package named in the first command.

my question is, if i change the second command to:
```
sudo apt-get install -f --print-uris
```
will it still print out the URL's for the packages i need?

Yes it will. Either way you should just use the GUI to do the installation. It'll automatically install all your dependencies for you as I said in my previous post. And considering you've already placed the dependencies in cache, you don't need to have an internet connection for it.

---

### Post by Circus-Killer on 2008-02-11
okay, problem. when i try install vodafone it sais it requires python-serial, but when i try get the url for the package, it tells me that there is no candidate for that package.

after placing all the other dependencies into the /var/cache/apt/archives folder, it still would not install. basically, it looks like if i don't already have a functioning internet connection on this laptop, i can't set up my 3G modem, which is my only way of connecting to the internet.

so now, i don't know what to actually do about this. really want to run ubuntu but can't if i can't get my 3G modem working in ubuntu :(

---

### Post by Circus-Killer on 2008-02-11
okay, i just ordered the ubuntu install dvd. it's my last attempt at tryna get this thing working without an internet connection.

to get a bit off-topic, how do i go about installing extra stuff off the dvd? do i need to add the dvd to sources.list?

anyways, i should get the dvd by thursday, maybe try it out this coming weekend. who knows, maybe i'll get lucky. but if i don't, i guess it will be vista for me then. :(

will report back with news on my success or failure. any other suggestions welcome.

---

### Post by Partyboi2 on 2008-02-11
[here ]("http://packages.ubuntu.com/gutsy/python/python-serial")is the package, if you can download it from windows then copy it over to ubuntu an install it on. It requires that you have python and python-central installed. (Which I think you should already have) If you don't have those  packages installed use [this]("http://www.nonetdebs.homeip.net/")

---

### Post by Partyboi2 on 2008-02-11
when you are booted into ubuntu, just stick the dvd in and it should ask you if you want to add the packages to synaptic package manager list. Say Yes then open up synaptic package manager and click on reload then use the search feature of synaptic to look for your needed packages.

---

### Post by Circus-Killer on 2008-02-14
okay, i downloaded all the dependencies and installed them using dpkg, cos putting the debs in /var/cache/apt/archives didnt work. (i'll only be using this download-first method until my ubuntu dvd arrives, which should be this weekend).

my question is this, if i installed the packages using dpkg, and the packages are available through the repos, when i run an update with apt-get, will it update those packages that i installed with dpkg?

---

### Post by Partyboi2 on 2008-02-14
Yes, correct :)

---

