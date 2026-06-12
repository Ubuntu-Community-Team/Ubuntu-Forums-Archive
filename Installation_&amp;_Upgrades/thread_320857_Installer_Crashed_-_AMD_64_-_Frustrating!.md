---
title: "Installer Crashed - AMD 64 - Frustrating!"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by erickster on 2006-12-18
Hey guys.  I'm trying to install ubuntu into my desktop.  I've formatted the HD, and have tried so many CD's.  The most current CD I've downloaded/burned is the newest version of Ubuntu , the 64 bit version.  I've run disk checks-- 0 sums failed.  I receive this error at 15% of the installation process:

(Be aware that I typed all this manually, so I might have made a mistake or two in the current error post)

Traceback (most recenty call last):
File "/usr/bin/ubiquity", line 166, in ?
 main ()
File "/usr/bin/ubiquity", line 161, in main
 isntall(sys.argv[1])
File "/usr/bin/ubiqiuty", line 57, in install
 ret = wizard.run()
File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 305, in run
 self.process_step()
File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 856, in process_step
 self.progress_loop()
File "/usr/lib/ubiquity/ubiquity/frontend/gtkui.py", line 618, in progress_loop
 ret = dbfilter.run_command(auto_process=True)
File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 153, in run_command
 self.start(auto_process=auto_process)
File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 63, in start
 prep = self.prepare()
File "/usr/lib/ubiquity/ubiquity/components/install.py", line 27, in prepare
 self.preseed('netcfg/get_hostname', hostname)
File "/usr/lib/ubiquity/ubiquity/filteredcommand.py", line 273 in preseed
 self.db.register('debian-installer/dummy', name)
File "/usr/lib/python2.4/site-packages/debconf.py", line 60, in <lambda>
 lambda *args, **kw: self.command(command, *args, **kw))
File "/usr/lib/python2.4/site-packages/debconf.py", line 81, in command status = int(status)
 ValueError: invalid literal for int():


not too sure where to go from here... please help!

---

### Post by gn2 on 2006-12-18
Waste no more time.

Download burn and install standard 32-bit 6.06 LTS.

---

### Post by erickster on 2006-12-18
I tried that too.  You're talking about: unbuntu-6.06.1-desktop-i386  right?

I tried these:
ubuntu-6.10-desktop-amd64.iso
ubuntu-6.06.1-desktop-amd64
unbuntu-6.10-desktop-i386

When I try unbuntu-6.10-desktop-i386
It freezes up at 15%, just sits there and never goes away.  So I tried mem-512m, and got an error during bootup.  I was going to try the alternative CD next-- I'm almost done with this mess.  I've burned about 5 to 6 CD's.  I could go back and try the 32 bit 6.06, I feel I'll get the same issue.

---

### Post by gn2 on 2006-12-18
> **erickster said:**
> I tried that too.  You're talking about: unbuntu-6.06.1-desktop-i386  right?

I tried these:
ubuntu-6.10-desktop-amd64.iso
ubuntu-6.06.1-desktop-amd64
unbuntu-6.10-desktop-i386

When I try unbuntu-6.10-desktop-i386
It freezes up at 15%, just sits there and never goes away.  So I tried mem-512m, and got an error during bootup.  I was going to try the alternative CD next-- I'm almost done with this mess.  I've burned about 5 to 6 CD's.  I could go back and try the 32 bit 6.06, I feel I'll get the same issue.

ubuntu-6.06.1-desktop-i386 is the one I meant.

Do you have 256mb RAM or more?

If the checksum's OK and you've burned it to a cd-r not cd-rw, have you tried the F6 boot options, eg "noapic nolapic" ?

There's a few different options to try.

---

### Post by erickster on 2006-12-18
I have 512 MB of RAM I believe.  I burned nothing but CD-R's.  I tried F6, but not with noapic or nolapic.  I'm not familiar with those options.  Is it just "noapic nolapic" that I type?  I also tried downloading/installing SUSE because I was so frustrated-- I downloaded the whole DVD,  but got about 50% through and that froze also.  Pretty frustrating.

---

### Post by wpshooter on 2006-12-18
Erickster:

Do you have any other O/Ss on this computer ?

And have you ran the memtest function from the Ubuntu CD ?

Are you burning the CDs at 4X or less ?

I would highly recommend that you get yourself a few good name brand CD-RW, so that you can use the over & over & over again.

---

### Post by erickster on 2006-12-18
The HD was formatted-- before it was formatted, it had win XP on it.  I'm not sure I ran the memtest-- I'm sure I did-- I ran everything else.  I burned at 4X, and like I said, 0 sums failed.  :-/

---

### Post by 454redhawk on 2006-12-18
For whatever reason it took me about 4 tries and 3 cd's to get it to install. Keep trying is the only thing I can suggest.

---

### Post by wpshooter on 2006-12-18
Erickster:

Get the **KILLDISK **program and **WIPE** your hard drive completely clean.

[http://www.killdisk.com/](http://www.killdisk.com/)

Then give the installation another try.  I would suggest that you try the 32 bit DESKTOP version of Dapper 6.06.1 first and if that will not work, try the KILLDISK again and try the installation with 32 bit version of ALTERNATE version of Dapper 6.06.1.

Good luck.

---

### Post by erickster on 2006-12-19
OK-  so I ran KILLDISK, and decided to try OpenSUSE since I had downloaded the whole DVD.  It didn't work-- I tried another DVD burned at 2X, didn't work.  Finally I tried Ubuntu 64 bit alternate--- and it worked!  I think I burned a total of 9 to 10 CD's/DVD's.  Now all I have to do it put all my original hardware back into my comp and hope that the system recognizes it all.  I'm not familiar with Ubuntu, but my main reason of installing it was that it was free, and I want to use my PC to play DVD's and also install a TV tuner.  (I have it hooked up to a home theatre projector)

Any ideas on where I should begin with software?  I was thinking of WINE HQ?

---

### Post by wpshooter on 2006-12-19
Suggestion, get yourself a few CD-RWs.  More expensive but useful in this type of situation.

Good luck.

---

### Post by erickster on 2006-12-19
By the way-- I can't get Ubuntu to recognize my wireless linksys card.  Any ideas?

---

