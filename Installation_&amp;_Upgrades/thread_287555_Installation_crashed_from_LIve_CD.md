---
title: "Installation crashed from LIve CD"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by kagashe on 2006-10-28
Hi,

I am doing fresh install (instead of upgrade) every time a new version of Ubuntu is released.

Since Ubuntu 6.06 Live and Install CD has been combined. I could install Ubuntu 6.06 from Live CD on my Laptop.

When I tried Ubuntu 6.10 Live CD the installation crashed. I got the following report after the crash. Since I could not open the Text Editor I had to write down the crash report in my Diary which is reproduced below:

> We are sorry; the installer crashed. Please file a new bug report at [Launchpad]("https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug") and a developer will attend. Include the following details in your bug report and attach the files var/log/syslog and var/log/partman.

Traceback (most recent call last)
File "/usr/bin/ubiquity", line 166, in?
main()

File "/usr/bin/ubiquity", line 161, in main
install(sys.argv[1])

File "/usr/bin/ubiquity", line 57, in install
ret=wizard.run()

File "/usr/bin/ubiquity/ubiquity/frontend/gtkui.py", line 305, in run
self.progress_loop()

File "/usr/bin/ubiquity/ubiquity/frontend/gtkui.py", line 856, in process_step
self.progress_loop()

File "/usr/bin/ubiquity/ubiquity/frontend/gtkui.py", line 628 in progress_loop
raise RuntimeError, ("Install failed with exit code %s\n%s")

Runtime Error: Install failed exit code 1

Traceback (most recent call last):

File "/usr/share/ubiquity/install.py", line 1404, in?
install run()

File "/usr/share/ubiquity/install.py", line 306, in run
self.copy_all()

File "/usr/share/ubiquity/install.py", line 484, in copy_all
shutil.copyfile (sourcepath, targetpath)

File "shutil.py", line 49, in copyfile
copyfileobj(fsrc, fdst)

File "shutil.py", line 25, in copyfileobj
fdst.write(buf)

IOError: [Errno 30] Read-only file sytem


After the crash gui was not working so I could not copy the files var/log/syslog and var/log/partman.

Later on I installed Ubuntu 6.10 using the alternate CD.

My question is:
> once the Live CD installer of last Ubuntu version worked on my Laptop how come it did not work this time?

kagashe

---

### Post by taurus on 2006-10-28
It could be the LiveCD was corrupted while downloading to your machine and/or you burned it too fast!!!  Did you checksum to see if your iso image passed the integrity test before you burned it?

---

### Post by kagashe on 2006-10-29
> **taurus said:**
> It could be the LiveCD was corrupted while downloading to your machine and/or you burned it too fast!!!  Did you checksum to see if your iso image passed the integrity test before you burned it?I have checked the integrity of the CD.

Later on I discovered that the hard disc had problems because I could not login to newly installed Ubuntu 6.10 after reboot. I am getting the following message from the BIOS:
> 05h: Imminent FailureThe same message appears after the Comprehensive Hard Drive Self Test in the BIOS.

I don't have any working operating system on the hard disc now and using the Live CD to access internet. I have googled and learnt that the hard disc needs to be replaced as soon as possible.

I can mount the /home partition and hope to recover the files by transferring them to a portable hard disc being borrowed from one of my friends. I hope I can do this while using the operating system from the Live CD.

kagashe

---

