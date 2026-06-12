---
title: "Unsuccessfull download of web browsers."
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by Sofo on 2012-02-03
I have tried downloading Google Chrome and Opera for ubuntu, but each time i click the deb-file the sofware center returns with an internal error.
What could be wrong?

---

### Post by haqking on 2012-02-03
> **Sofo said:**
> I have tried downloading Google Chrome and Opera for ubuntu, but each time i open the software center to install i get an invalid file when opening the deb-file. 
What is wrong?

likely to be corrupt downloads or wrong architecture maybe.

compare the hash to see if downloaded file is same as source

also if you have downloaded the .debs then double click them no need to open software centre unless you are installing from the repos

cheers

---

### Post by satanselbow on 2012-02-03
Where did you download them from? And what is the exact error?

Copy/paste the exact error would be more helpful than an abridged description of it ;)

---

### Post by doobrie on 2012-02-03
> **Sofo said:**
> I have tried downloading Google Chrome and Opera for ubuntu, but each time i open the software center to install i get an invalid file when opening the deb-file. 
What is wrong?

Are you installing directly from the Software Centre, or are you manually installing a .deb file?

What's the error that you are getting?

---

### Post by Bucky Ball on 2012-02-03
> **doobrie said:**
> Are you installing directly from the Software Centre, or are you manually installing a .deb file?



+1. Download them straight from Software Centre. That way it will be tailored to your release and architecture. Don't bother about downloading the debs manually and then installing. Not quite like Windows that way. ;)

---

### Post by haqking on 2012-02-03
> **Bucky Ball said:**
> +1. Download them straight from Software Centre. That way it will be tailored to your release and architecture. Don't bother about downloading the debs manually and then installing. Not quite like Windows that way. ;)

edit: whoops replied thinking it was a different thread than it was ;-)

Cheers

---

### Post by Sofo on 2012-02-03
I ran a general software update for Ubuntu and now the installation works. 
Now the problem is: where did Google Chrome go? I see no icons anywhere and nothin like the Windows startfolder?

---

### Post by haqking on 2012-02-03
> **Sofo said:**
> I ran a general software update for Ubuntu and now the installation works. 
Now the problem is: where did Google Chrome go? I see no icons anywhere and nothin like the Windows startfolder?

```
/opt/google
```

make a shortcut to it

Cheers

---

### Post by Sofo on 2012-02-03
Hmm. It seems like user friendlyness somehow vanished upon installation of Ubuntu.

---

### Post by satanselbow on 2012-02-03
> **Sofo said:**
> Hmm. It seems like user friendlyness somehow vanished upon installation of Ubuntu.

I've experienced plenty of failed software installations on Windows in my time ;) 

You haven't actually answered any of the questions put to you - which would make solving your problem much simpler.

Where did you download the browsers from? And what steps exactly have you tried to install them?

---

### Post by Sofo on 2012-02-03
I downloaded the deb.file from the net. I clicked on it and finally got the message that it was installed. 
Now my only question is: where dies it hide and why is it hiding? Userfriendlyness would indicate that there was an icon i could click on somewhere and drag to the taskbar. Why  hiding souch obvious things upon installation?

---

### Post by haqking on 2012-02-03
> **Sofo said:**
> I downloaded the deb.file from the net. I clicked on it and finally got the message that it was installed. 
Now my only question is: where dies it hide and why is it hiding? Userfriendlyness would indicate that there was an icon i could click on somewhere and drag to the taskbar. Why  hiding souch obvious things upon installation?

i already told you where it is, and where it is and goes is often down to the installer.

```
/opt/google/chrome
```

or

```
usr/bin/google-chrome
```

or you can use

```
whereis google-chrome
```

Complain to google about your free browser in your free operating system ;-)

also you can read the other similar posted threads about this

[http://ubuntuforums.org/showthread.php?t=1476465](http://ubuntuforums.org/showthread.php?t=1476465)
[http://ubuntuforums.org/showthread.php?t=1800423&page=2](http://ubuntuforums.org/showthread.php?t=1800423&page=2)
[http://ubuntuforums.org/showthread.php?t=1586140](http://ubuntuforums.org/showthread.php?t=1586140)

Peace

---

### Post by Sofo on 2012-02-05
Hello satanselbow. I downloaded Chrome from: [http://www.google.de/chrome?hl=da&platform=linux_ubuntu_i386#eula](http://www.google.de/chrome?hl=da&platform=linux_ubuntu_i386#eula)
Clicked the deb-file. Software center opens and i get an install successful message, but no info on where it went and no clickable icon.

---

### Post by haqking on 2012-02-05
> **Sofo said:**
> Hello satanselbow. I downloaded Chrome from: [http://www.google.de/chrome?hl=da&platform=linux_ubuntu_i386#eula](http://www.google.de/chrome?hl=da&platform=linux_ubuntu_i386#eula)
Clicked the deb-file. Software center opens and i get an install successful message, but no info on where it went and no clickable icon.

as i have already written twice now and this being the third time.

```
whereis google-chrome
```

or if you dont want to search for it it is likely in

```
/opt/google/google-chrome
```

or

```
/usr/bin/google-chrome
```

---

### Post by howefield on 2012-02-05
> **Sofo said:**
> i get an install successful message, but no info on where it went and no clickable icon.

Are you running the Unity interface ?

If so, open the Dash and search for Chrome, you can drag it to the launcher where it will stay.

---

### Post by Sofo on 2012-02-05
Well commandlines died for me at least 10 years ago. 
If thats how Ubuntu works its not for me.

Bye Ubuntu.

---

### Post by haqking on 2012-02-05
> **Sofo said:**
> Well commandlines died for me at least 10 years ago. 
If thats how Ubuntu works its not for me.

Bye Ubuntu.

you dont need to use the command line to navigate to where i told you it would be, or use the dash if in Unity like howefeld said above me. and those commands and locations are the same whatever version of linux you use, if you dont like linux or its commands then dont use it, and in Windows there is still the command prompt for power users.

However use what works for you or what you can make work

Peace

---

