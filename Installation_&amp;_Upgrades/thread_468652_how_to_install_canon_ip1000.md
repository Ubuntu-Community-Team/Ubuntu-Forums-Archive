---
title: "how to install canon ip1000?"
date: 2007-06-09
forum: Installation &amp; Upgrades
---

### Post by amdfanboy on 2007-06-09
i'm still a newbie...can anybody tell me how to do it?

---

### Post by amdfanboy on 2007-06-10
i tried installing it via 

"Printing"

but it is not included in the lists of printers...how am i supposed to install this?

---

### Post by thelinuxguy on 2007-06-10
Take a look here: [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon)

I have a Pixma IP 1000 but haven't tried it out.

Its for Edgy. Can't say if it will work with Feisty.

---

### Post by amdfanboy on 2007-06-10
hmm, ok i'll try it out...

maybe someone can give me some ideas on what canon drivers also work with ip1000

---

### Post by amdfanboy on 2007-06-11
still can't manage to make it work though..need some help here...

---

### Post by thelinuxguy on 2007-06-11
I have it working at my end.

Install the appropriate drivers from [http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon](http://mambo.kuhp.kyoto-u.ac.jp/~takushi/#canon) (I have Edgy).
Attach the printer to one of the USB ports and turn it on.

I) Method 1
[INDENT]It will be autodetected and the "Add a Printer" dialog will pop up.
Canon iP1000 should already be selected.
On the next screen, click on Install Driver.
Navigate to /usr/share/ppd/pstocanonbj and select canonpixmaip1000.ppd
Provide any other details such as the name and a description. 
Your printer should be installed.[/INDENT]

II) Method 2
[INDENT]When the Add a printer program starts automatically, cancel it.
Go to [http://localhost:631](http://localhost:631)
The CUPS Printers page should open.
Select administration.
Under "New Printers found" an entry which reads like "Canon iP1000 (Canon iP1000 USB #1)" should be present.
"Add this printer"
Click on browse to provide the ppd file as above.
Click on "Add printer"
Your printer should be installed.[/INDENT]

PS: If you have some "default" printers added by Ubuntu, delete them. It says Canon Pixma IP1000 but selects the wrong driver. I didn't try modifying it and selecting the correct driver.

I printed a test page from OpenOffice and it printed fine. The only problem is, I couldn't find the option to change the print quality to "draft" as is available in the Windows driver to save some ink. Let me know if you come across it.

Regards,
thelinuxguy.

---

### Post by amdfanboy on 2007-06-12
ok im gonna try this one out

---

### Post by amdfanboy on 2007-06-12
tried this one out...but feisty can't recognize the command "deb"

---

### Post by thelinuxguy on 2007-06-12
```

deb http://mambo.kuhp.kyoto-u.ac.jp/~takushi/ubuntu ./

```
This is not a command. You have to append it to the /etc/apt/sources.list file.

---

### Post by amdfanboy on 2007-06-12
ah i see...how stupid of me...i'm gonna try that one out after a new installation of ubuntu...

my system got messed up while installing vmware ^_^

---

### Post by amdfanboy on 2007-06-13
it says something like, "libcnbj-2.5 can not be found"

---

### Post by thelinuxguy on 2007-06-14
on which step are you getting this error? If its while doing the apt-get then /etc/apt/sources.list is not setup properly. Did you edit /etc/apt/sources.list as instructed at the site? Also make sure you have added the deb line meant for Ubuntu and not the one for Debian.

Again, since you are installing a driver meant for Edgy, it may or may not work. Let me know more about the error.

---

### Post by amdfanboy on 2007-06-14
that error happens when i'm trying to download the drivers...

the repository is good, double checked it...

just when i enter the line

# apt-get install libcnbj-2.5 bjfilter-2.5 pstocanonbj

it says that it can't find that libcnbj-2.5

---

### Post by amdfanboy on 2007-06-14
managed to do it finally..

error on my part...

the line that's supposed to be appended to /etc/apt/sources.list was misplaced..

i placed it on the automatix repositories....just corrected it and poof....

managed to install the printer...

just to confirm...

edgy printer drivers works with feisty..

---

### Post by thelinuxguy on 2007-06-15
> **amdfanboy said:**
> 
managed to install the printer...
just to confirm...
edgy printer drivers works with feisty..

That sounds good. Consider marking this thread as resolved.
And if you come across a way to change the print mode (to draft specifically) to save on ink and other settings that are available in the Windows version of the driver, do update this thread.

Regards,
thelinuxguy.

---

### Post by tdm on 2008-02-16
**I have built a package which automatically install the driver.**
 
[Click Here]("http://ubuntuforums.org/showthread.php?t=730598")

---

