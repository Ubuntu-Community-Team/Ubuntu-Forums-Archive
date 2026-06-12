---
title: "Using Apt-Get or Aptitude with Debian (Deb) Package (Google Chrome Example)"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by snmcdonald on 2011-07-16
Ever download a *.deb package only to find out you were missing a boat load of dependencies. Rather than go through the headache of resolving dependency after dependency I make a simple local repository to handle this problem. I will provide you with a solution that can work with any proper Debian package.

For this example I will be using Google Chrome. Google Chrome is not available within the Debian mirror repositories because it does not fit the Debian free standard. (Yes I know Google Chromium is available, but I need an excuse to download Google Chrome). So head over to [http://www.google.com/chrome]("http://www.google.com/chrome") and download the latest *.debian package. in my case it was google-chrome-stable_current_i386.deb.
After you have downloaded chrome it should be in your Downloads directory. Go to this directory and create a chrome sub directory.

```
cd ~/Downloads
mkdir chrome
```

Next you'll need some additional dpkg tools. They will assist in creating Debian mirrors.

```
sudo aptitude install build-essentials
```

Use these new tools to create local repository listing.  dpkg-scanpackages takes one argument which indicates the current directory to scan and outputs information to stdout. Use gzip to create a zipped text file. The arguments 9 indicates the highest zip and c stdout to the specified location. Use zmore to do a quick sanity check to ensure that the out worked

```
sudo dpkg-scanpackages . | gzip -9c > chrome/Packages.gz
zmore chrome/Packages.gz
```

Now add the package to your apt source list

```
sudo vi /etc/apt/sources.list
 #append this to sources.list
 deb file:/home/shane/Desktop chrome/
```

Now its time to install Google Chrome. Update your repository listing and install.

```
sudo aptitude update
sudo aptitude install google-chrome-stable
```


Untrusted Packages?!?! We'll its because we did not digitally sign and use apt-key. But if you are doing this, you should be the system administrator and have downloaded and followed these instructions and we trust Google :)

For basic housekeeping you should remove the Chrome package from your sources and delete the no longer needed Debian package.

```
sudo vi /etc/apt/sources.list
cd ~/Download
sudo rm -r chrome
sudo rm google-chrome-stable_current_i386.deb
```

Have fun and good luck!

---

