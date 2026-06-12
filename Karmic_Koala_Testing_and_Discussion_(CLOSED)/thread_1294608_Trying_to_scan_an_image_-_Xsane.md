---
title: "Trying to scan an image - Xsane"
date: 2009-10-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by cjnkns on 2009-10-18
Hi all - 

I have an HP Office JEt 7400 which I have used on previous Ubuntu installs with 0 problems.

But, I am currenlty running 9.10 and when I load up xsane to scan an image it tells me it "No available devices".

I looked in synaptic and had the xsane package installed but not sane. So I installed sane but, still no luck. 

Is there anyone familiar with this issue?

I would appreciate any help as I have to scan some homework for my wifes grad class :(....

Thanks so much.

---

### Post by darco on 2009-10-18
Does Karmic see your printer? I had some recent issues where the CUPS daemon had to be started after each reboot for it to see my printer. Not sure if xsane needs cups running tho..

darco

---

### Post by cjnkns on 2009-10-18
Thanks for the reply! 

Yes I have no problem printing at all... Which is weird it's the same device!

---

### Post by darco on 2009-10-18
Maybe a permission issue...I remember seeing under Administration/Users and Groups that you could add permission to scan but I dont see that option any longer. Have you tried running sudo xsane?

darco

---

### Post by cjnkns on 2009-10-18
Yes - still receive the same message.

I also tried installating 'hpoj' which from the description looks like a package for 'all-in-ones' from HP. 
But, that didn't seem to do the trick either.

---

### Post by kansasnoob on 2009-10-18
Run through this:

[http://hplipopensource.com/hplip-web/supported_devices/index.html](http://hplipopensource.com/hplip-web/supported_devices/index.html)

Easier for you than me since you have all the info.

It's possible that you may need to download an earlier version of the hplip software and we can do that!

It's also remotely possible that you might need to downgrade sane, but I doubt that.

Just as an FYI, even though it's still in Alpha stage I much prefer "flegita" (aka: Gnome scan utility) to Xsane. You need not remove one to try the other.

---

### Post by cjnkns on 2009-10-18
Thanks I'll try the link and report back.

I have tried Gnome Scan, but once I click scan it says "job completed". I then click forward and it just sits there. Nothing happnes...

---

### Post by cjnkns on 2009-10-18
> Run through this:

[http://hplipopensource.com/hplip-web...ces/index.html](http://hplipopensource.com/hplip-web...ces/index.html)

Easier for you than me since you have all the info.

I tried the link, but it looks like the version offered by HP is the same version in the Ubuntu repo.

---

### Post by kansasnoob on 2009-10-18
> **cjnkns said:**
> I tried the link, but it looks like the version offered by HP is the same version in the Ubuntu repo.

OK, I ran across this in Jaunty (not so far in Karmic) but even though the version is identical running the HPLIP script would always get things working.

There were times it would notify me of unmet dependencies and then I'd have to shut down the terminal and go to Synaptic (only one package manager can operate at one time) and try to resolve those dependencies. There were even times that I had to download .debs from a previous package list to get things done.

That's why they say "testing only", but if I were you I'd run the HPLIP script after running the commands:

```
sudo apt-get remove hplip && sudo apt-get -f install
```

The "-f install" part might ask you whether or not to remove or install something. I should see that before you decide yes or no!

---

### Post by cjnkns on 2009-10-18
> 
Code:

sudo apt-get remove hplip && sudo apt-get -f install

The "-f install" part might ask you whether or not to remove or install something. I should see that before you decide yes or no!


I executed the above and also removed hplip-data. 
After trying to run the HP script I downloaded i get the message below.




> warning: There are 7 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: This installer cannot install 'gcc' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.


I have gcc installed already. I even tried re-installing through snaptic. Not sure what other programs the message is talking about as it doesn't specify and just mentions gcc.

---

### Post by kansasnoob on 2009-10-18
I'm going to run the download script myself in Karmic.

---

### Post by kansasnoob on 2009-10-18
So far:

> lance@lance-desktop:~$ cd Desktop
lance@lance-desktop:~/Desktop$ sh hplip-3.9.8.run
Creating directory hplip-3.9.8
Verifying archive integrity... All good.
Uncompressing HPLIP 3.9.8 Self Extracting Archive..........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................

HP Linux Imaging and Printing System (ver. 3.9.8)
HPLIP Installer ver. 5.1

Copyright (c) 2001-9 Hewlett-Packard Development Company, LP
This software comes with ABSOLUTELY NO WARRANTY.
This is free software, and you are welcome to distribute it
under certain conditions. See COPYING file for more details.

Installer log saved in: hplip-install_Sun-18-Oct-2009_15:44:26.log

/
note: Defaults for each question are maked with a '*'. Press <enter> to accept the default.


INSTALLATION MODE
-----------------
Automatic mode will install the full HPLIP solution with the most common options.
Custom mode allows you to choose installation options to fit specific requirements.

Please choose the installation mode (a=automatic*, c=custom, q=quit) : 


I'll be back!

---

### Post by kansasnoob on 2009-10-18
Same thing here:

```
warning: There are 7 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: This installer cannot install 'gcc' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.

```

Development releases are fun!

Give me a few minutes.

In the meanwhile if you need to get some work done can you do it from an older Live CD?

---

### Post by cjnkns on 2009-10-18
Thanks much for your assistance!

My computer works fine with the exception of scanning... and misc bugs of course.

---

### Post by kansasnoob on 2009-10-18
OK, I removed gcc, and installed the Jaunty version:

[http://packages.ubuntu.com/jaunty/devel/gcc](http://packages.ubuntu.com/jaunty/devel/gcc)

(i386 for me)

And it installed OK ............. but I still get this:

> warning: There are 7 missing REQUIRED dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency: gcc (gcc - GNU Project C and C++ Compiler)
warning: This installer cannot install 'gcc' for your distro/OS and/or version.
error: Installation cannot continue without this dependency. Please manually install this dependency and re-run this installer.


So it's a bug! It's broken!

---

### Post by cjnkns on 2009-10-18
Bummer :( 

Thanks for the help.

---

### Post by kansasnoob on 2009-10-18
Can you get done what you need from a Live CD?

I think I should write a tutorial about multi-booting being the safest way to try any new distro (dev or not).

Be that as it may, Karmic scares me so far.

It's working well for me, but I see lots of complaints and we have 10 or 11 days to go!

---

### Post by cjnkns on 2009-10-18
yes - thanks. 

Just decided to create a new document from scractch insted of scanning.

It was alot more work unfortunatley, but that's what I get for installing  beta software :)

---

### Post by kansasnoob on 2009-10-18
I dozed off while originally trying (launchpad can do that to you) but I need to file a bug report. Once done I'll report back here.

---

### Post by kansasnoob on 2009-10-18
Possibly the worst bug report I ever wrote but:

[https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/455102](https://bugs.launchpad.net/ubuntu/+source/gcc-defaults/+bug/455102)

I hate that I misspelled full! ](*,)

What a foll! or is that fool?

---

