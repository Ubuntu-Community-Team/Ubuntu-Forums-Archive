---
title: "Ubuntu Server 12.10 to 13.04 Upgrade Failure"
date: 2013-05-07
forum: Installation &amp; Upgrades
---

### Post by Bob Fletcher on 2013-05-07
Hello

To give your background my server is tucked away in a cupboard and I really don't have to do anything with it that's the wonderful thing about Ubuntu Linux. When I need to access the server I do this for my Windows box using FTP Telnet etc. The upgrade I attempted was using the Telnet client.

During the upgrade something failed and all I got running down the screen was a 'y' I was open for this to time out but eventually I had to do a CTRL-C I then ran a reboot and this did bring some life back into the system. On first reboot it told me that I had 496 packages to upgrade on second reboot it told me there was too many packages to list that needed upgrading. I take it from this that most of the upgrade to 13.04 was a failure.

If I run apt-get update I get a failure that says "dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."

When I attempt to run be above I get the following error, "Package it is in a very bad inconsistent state - you should reinstalled it be before attempting configuration."

I get the same error if I run "apt-get upgrade".

The last thing I want to do is to reinstall the OS. Can I do what it says and install dpkg manually as my understanding is that dpkg is needed to install all packages. Also what other options are by got to repair the system either online or using a life disk. As I said earlier the system is running and all servers appear to be running so it would seem to me that 13.04 is only partly installed.

Robert…

---

### Post by darkod on 2013-05-07
I'm not sure how telnet works, I usually use ssh.

I don't think it complains about dpkg itself, but on a particular package. Try to see if it can fix any broken packages with:
```
sudo apt-get install -f
```

That's for fixing broken packages.

On another note, if all your services are running, why are you upgrading a server to 13.04? And why do you have it running 12.10 first of all? Unless you really, really, need something that's included only in the latest versions, the best thing is to stick to LTS for servers. In this case 12.04 LTS. With the LTS version you can upgrade from LTS directly to the next LTS in case you choose to. Running a "normal" release and upgrading one by one as they come out, will definitely get you into trouble sooner or later. Something, sometimes, will fail during the upgrade. And there are new releases very 6 months.

You said this is a server, but is it the server OS or the desktop OS running as server for you?

PS. If error messages continue when trying to use apt-get or dpkg, post the complete message if you can. Copy and paste all of it. It usually includes the package name, or the path/file that's bothering it. In many cases just deleting that file is enough, but post it first, just in case it's some system file.

---

### Post by Bob Fletcher on 2013-05-07
Hi Darko

Thank you to getting back to me. "apt-get install -f" was unable to run it just return the same error that dpkg needs to be reconfigured.

Is there is some way that I can reinstall the OS but still leave intact all the servers config files etc.?

Yes I know exactly what you mean about the reason for upgrading. I did question this myself before I went ahead and did it. What makes things worse is that I am always advising other people not to upgrade software it routinely unless there is a good reason for doing so. I just don't listen to my own advice.

Robert&#8230;

---

### Post by darkod on 2013-05-07
Unless you boot the machine with the desktop live cd in live mode, and manually fish and copy all files you need, I'm not aware how to save them intact during clean install. The point of clean install is to format the / partition otherwise all sorts of files will remain and it won't be "clean".

Run again the command that gives you the message about the package name, and try to see what it says. In case you do receive such message. If I understand your first post, when you attemtped ti run the dpkg --configure -a it sais that some package is inconsistent and should be reinstalled. That would refer to that package only, not to dpkg.

Try running it again and look very closely in the message, try to figure out the package name.
After that you can either try reinstalling like:
sudo apt-get install --reinstall <package>

or even just removing it with either apt-get or dpkg. Just so you can get it out of the way. Later you can add it again.

---

### Post by Bob Fletcher on 2013-05-09
I finally did the inevitable and did a clean install. I've done quite a lot of reading on the net both in this forum and elsewhere and the problem I experienced is not uncommon for an upgrade to fail halfway through. Apparently this can leave you stuck between versions, this was evident from the login screen telling me that I was running 13.04 and also telling me that an upgrade was a available for 13.04 which wouldn't work anyway.

---

