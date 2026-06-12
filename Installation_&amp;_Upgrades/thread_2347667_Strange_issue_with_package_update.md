---
title: "Strange issue with package update"
date: 2016-12-27
forum: Installation &amp; Upgrades
---

### Post by jdowdster on 2016-12-27
This problem seems benign but I'm getting it repeatedly and I'm wondering how to get rid of it.

After running the package update tool I began to get a desktop notification that some data files failed to download and did it want me to run the update now. When start the update up comes a console which seems to be running some 3rd party tool and this is the dialog I see in the konsole:

ttf-mscorefonts-installer: processing...
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe)
Get:1 [http://downloads.sourceforge.net/corefonts/andale32.exe](http://downloads.sourceforge.net/corefonts/andale32.exe) [198 kB]
Fetched 198 kB in 1s (169 kB/s)                                                              
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/andale32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
ttf-mscorefonts-installer: downloading [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)
Err:1 [http://downloads.sourceforge.net/corefonts/arial32.exe](http://downloads.sourceforge.net/corefonts/arial32.exe)
  404  Not Found
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/arial32.exe' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
E: Failed to fetch [https://pilotfiber.dl.sourceforge.net/project/corefonts/the](https://pilotfiber.dl.sourceforge.net/project/corefonts/the) fonts/final/arial32.exe 404  Not Found

E: Download Failed

I've tried to run the tool "ttf-mscorefonts-installer" by hand but I can't find it anywhere.

Any thoughts or advice?

Cheers!!

---

### Post by howefield on 2016-12-27
Try the following command in a terminal..

```
sudo touch /var/lib/update-notifier/package-data-downloads/ttf-mscorefonts-installer
```

You won't get any feedback in the terminal after entering the command but it should stop the prompts.

---

### Post by jdowdster on 2016-12-27
howfield,

Thanks for the response.

Any ideas as to why this is happening? My setup is pretty standard. Why would this particular package update cause my installation grief?

Cheers!!

---

### Post by howefield on 2016-12-27
The script that the the package runs in order to download the fonts from the sourceforge server is pointing at the wrong location, as I understand it. There are a ton of bugs on launchpad if you want to read more ;)

What I do to get around this is to install the 3.6 version of the ttf-mscorefonts-installer rather than the repository 3.4 version, for info as follows..

```
wget [http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb](http://ftp.de.debian.org/debian/pool/contrib/m/msttcorefonts/ttf-mscorefonts-installer_3.6_all.deb) -P ~/Downloads
```

will download the package to your Downloads folder, and

```
sudo apt install ~/Downloads/ttf-mscorefonts-installer_3.6_all.deb
```

will install the package.

---

### Post by jdowdster on 2016-12-27
howefield,

Thank you sir. I actually installed using your described steps. You can never have too many fonts.

Seasons Greeting to you and yours and have a Great New Year!!

---

### Post by howefield on 2016-12-27
And seasons best to you too :)

Feel free to mark the thread as solved if you feel that it is.

---

### Post by jdowdster on 2016-12-27
Desperately trying to figure how to do that!! lol...

---

### Post by colin.p on 2017-01-12
Thanks, I just started to get this error....and now I don't.

---

