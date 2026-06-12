---
title: "unattended-upgrades and 3rd party repos"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by chocobanana on 2010-02-08
Greetings everyone

I have searched on the internet but didn't manage to find out how to flag 3rd party repositories in /etc/apt/sources.list.d/50unattended-upgrades.

It installs all updates from the stock Ubuntu repos but none from 3rd party repositories I later added (e.g. Chromium PPA, Skype, etc.). I understand I have to manually add the lines but I'm not sure what's the format for this.

Can somebody give me a hint on how to do this? Here's how my 50unattended-upgrades file looks like:

```
// Automatically upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"Ubuntu karmic-security";
	"Ubuntu karmic-updates";
};

// List of packages to not update
Unattended-Upgrade::Package-Blacklist {
//	"vim";
//	"libc6";
//	"libc6-dev";
//	"libc6-i686";
};

// Send email to this address for problems or packages upgrades
// If empty or unset then no email is sent, make sure that you
// have a working mail setup on your system. The package 'mailx'
// must be installed or anything that provides /usr/bin/mail.
//Unattended-Upgrade::Mail "root@localhost";


// Automatically reboot *WITHOUT CONFIRMATION* if a 
// the file /var/run/reboot-required is found after the upgrade 
//Unattended-Upgrade::Automatic-Reboot "false";
```

Thanks!

---

### Post by chocobanana on 2010-02-19
Help? :)

---

### Post by tweakt on 2010-02-23
You could add "karmic" to the list where it says "karmic-security" and "karmic-updates", but that might pull in more than you want.

It might be possible to filter additional by "Origin", but I'm not familiar enough with PPAs to know if they haven a specific origin set or not.

Perhaps others can help with the details?

---

### Post by chocobanana on 2010-02-27
Well, I would like it to automatically update from any active repository...

So, by adding a line with karmic, it is enough? Does it act like a wildcard?

---

### Post by chocobanana on 2010-03-26
Any clues, anyone? :)

---

### Post by nanonils on 2010-10-31
I'd also like to update ALL active repositories automatically (e.g. latest dev build of the Chrome browser). How do we do that?
(first one has to install unattended-updates: [https://help.ubuntu.com/10.04/serverguide/C/automatic-updates.html](https://help.ubuntu.com/10.04/serverguide/C/automatic-updates.html) and then sudo edit /etc/apt/apt.conf.d/50unattended-upgrades)

---

### Post by nanonils on 2010-10-31
OK, so the challenge is to find the right expression for distro and channel. E.g. while Google calls this "unstable" at [http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_amd64_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_amd64_deb)
I seem to only get this to work if I call it "stable" in my software sources although it is the "unstable" chrome package:
deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

Here is a way of blacklisting that Google's third party "stable" repository (copied from: [http://linuxconfig.org/ubuntu-linux-google-chrome-browser-download-install-and-usage#8-how-to-update-google-chrome-on-ubuntu-linux](http://linuxconfig.org/ubuntu-linux-google-chrome-browser-download-install-and-usage#8-how-to-update-google-chrome-on-ubuntu-linux)). One would have to list it under the automatic update section instead:

In the next step to disable Google Chrome automatic updates we need to add / edit a following block of code into /etc/apt/apt.conf.d/50unattended-upgrades ( root access required ):
// List of packages to not update
Unattended-Upgrade::Package-Blacklist {
        "google-chrome-stable";
};

---

### Post by nanonils on 2010-11-01
**EDIT 11/4/10: the following does not work! I guess I'm too much of a noob to figure it out.** 

11/2/10: I can positively confirm that the following causes automatic updating and installation of all my sources. The only reason I've grown comfortable with this is that I've moved all my files into the Google cloud and see my computers more as a terminal. Plus FroYo on my phone does the same thing so I'm used to it (manual updating apps drove me crazy). 

```
// Automatically upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"Ubntu maverick stable";
	"Ubntu stable";
	"Ubuntu maverick-security";
	"Ubuntu maverick-updates";
	"google-chrome-stable";
	"google-chrome-unstable";
//	"${distro_id} ${distro_codename}-proposed-updates";
};
```

---

### Post by nanonils on 2010-11-04
Found a possible solution here (quote below): [http://blog.ezyang.com/2010/03/third-party-unattended-upgrade/](http://blog.ezyang.com/2010/03/third-party-unattended-upgrade/)

The problem is that the url provided for the Google Chrome repositories cannot be accessed with a browser (from sources.list: deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main). As a result, I cannot look up the "Origin" and "Suite". Maybe I should just install chromium but I like having Flash and additional codes preinstalled in Google's Chrome.


> Third-party unattended upgrades in three steps
by Edward Z. Yang

unattended-upgrades is a nifty little package that will go ahead and automatically install updates for you as they become enabled. No serious system administrator should use this (you are testing updates before pushing them to the servers, right?) but for many personal uses automatic updates are really what you want; if you run sudo aptitude full-upgrade and don't read the changelog, you might as well turn on unattended upgrades. You can do this by adding the line APT::Periodic::Unattended-Upgrade "1" to /etc/apt/apt.conf.d/10periodic (thanks Ken!)

Of course, the default configuration they give you in /etc/apt/apt.conf.d/50unattended-upgrades only pulls updates from their security repository, and they only give you a commented out line for normal updates. People have asked, "well, how do I pull automatic updates from other repositories?" Maybe you have installed Chromium dailies; seeing the "you have updates" icon every day can be kind of tiresome.

Well, here's how you do it:

Find out what URL the PPA you're interested in points to. You can dig this up by looking at /etc/apt/sources.list or /etc/apt/sources.list.d/ (the former is if you manually added a PPA at some point; the latter is likely if you used add-apt-repository).
Navigate to that URL in your browser. Navigate to dists, and then navigate to the name of the distribution you're running (for me, it was karmic). Finally, click Release. (For those who want to just enter the whole URL, it's [http://example.com/apt/dists/karmic/Release](http://example.com/apt/dists/karmic/Release)).
You will see a number of fields Fieldname: Value. Find the field Origin and the field Suite. The two values are the ones to put in Allowed-Origins.
For example, the Ksplice repository has the following Release file:

Origin: Ksplice
Label: Ksplice
Suite: karmic
Codename: karmic
Version: 9.10
Date: Sun, 07 Feb 2010 20:51:12 +0000
Architectures: amd64 i386
Components: ksplice
Description: Ksplice packages for Ubuntu 9.10 karmic
This translates into the following configuration:

Unattended-Upgrade::Allowed-Origins {
       "Ksplice karmic";
};
And that's it! Go forth and make your systems more secure through more timely updates.

Bonus tip. You can turn on unattended kernel updates via Ksplice by editing /etc/uptrack/uptrack.conf and setting autoinstall = yes.

```
// Automatically upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"Ubuntu maverick-security";
	"Ubuntu maverick-main";
	"Ubuntu maverick-universe";
	"Ubuntu maverick-updates";
	"Ubuntu maverick-restricted";
	"LP-PPA-chromium-daily-dev maverick";
	"LP-PPA-app-review-board maverick";
};
```

---

### Post by nanonils on 2011-01-27
OK, so the above didn't work I think (it's actually not so easy to figure out whether updates have been automatically installed or not on a machine that is shut down almost every night).

The unattended-updates really make the most sense on a server that is up all the time. This guide here does provide automatic updates on my machine: [https://help.ubuntu.com/10.10/serverguide/C/automatic-updates.html](https://help.ubuntu.com/10.10/serverguide/C/automatic-updates.html)

> Automatic Updates

The unattended-upgrades package can be used to automatically install updated packages, and can be configured to update all packages or just install security updates. First, install the package by entering the following in a terminal:

sudo apt-get install unattended-upgrades

To configure unattended-upgrades, edit /etc/apt/apt.conf.d/50unattended-upgrades and adjust the following to fit your needs:

// Automatically upgrade packages from these (origin, archive) pairs
Unattended-Upgrade::Allowed-Origins {
	"Ubuntu maverick-security";
	"Ubuntu maverick-main";
	"Ubuntu maverick-universe";
	"Ubuntu maverick-updates";
	"Ubuntu maverick-restricted";
	"LP-PPA-chromium-daily-dev maverick";
	"LP-PPA-app-review-board maverick";
};

Certain packages can also be blacklisted and therefore will not be automatically updated. To blacklist a package, add it to the list:

Unattended-Upgrade::Package-Blacklist {
//      "vim";
//      "libc6";
//      "libc6-dev";
//      "libc6-i686";
};

*	
The double &#8220;//&#8221; serve as comments, so whatever follows "//" will not be evaluated.

To enable automatic updates, edit /etc/apt/apt.conf.d/10periodic and set the appropriate apt configuration options:

APT::Periodic::Update-Package-Lists "1";
APT::Periodic::Download-Upgradeable-Packages "1";
APT::Periodic::AutocleanInterval "7";
APT::Periodic::Unattended-Upgrade "1";

The above configuration updates the package list, downloads, and installs available upgrades every day. The local download archive is cleaned every week.

*	
You can read more about apt Periodic configuration options in the /etc/cron.daily/apt script header.

The results of unattended-upgrades will be logged to /var/log/unattended-upgrades.

Google sent me a Cr-48 Chrome notebook and I love it. Except that I cannot live without a trackpoint and tracklight. I will try to remodel this experience with a Lenovo X201, i7 processor and SSD as I do need the occasional offline program (reference manager, virtualbox). I would like to automatically pull in updates and install them in the background when my computers are turned on (kinda sounds like what Windows does...).

---

### Post by mrsah on 2012-06-04
> **nanonils said:**
> 
The problem is that the url provided for the Google Chrome repositories cannot be accessed with a browser (from sources.list: deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main). As a result, I cannot look up the "Origin" and "Suite". Maybe I should just install chromium but I like having Flash and additional codes preinstalled in Google's Chrome.



This might of help:
```

$ cat /var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_Release
Origin: Google, Inc.
Label: Google
Suite: stable
Codename: stable
Version: 1.0
Date: Wed, 30 May 2012 21:55:44 +0000
Architectures: i386 amd64
Components: main
Description: Google chrome-linux repository.
MD5Sum:

```

---

### Post by lisati on 2012-06-04
[RIGHT]Back to sleep, old thread[/RIGHT]

---

