---
title: "Karmic 9.10 fails to install on Dell Mini 9"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ngfrazier on 2009-10-02
Beta UNR image was downloaded and checked. Tried to install many times. Keeps failing. Excerpt of user.log file provided below:
-------------------------------------------
Oct  1 23:25:16 ubuntu python: Not copying usr/share/ubiquity-slideshow/slides/loc.zh_CN/welcome.html
Oct  1 23:26:03 ubuntu ubiquity: umount: /target/cdrom: not mounted
Oct  1 23:26:03 ubuntu python: log-output -t ubiquity umount /target/cdrom
Oct  1 23:26:03 ubuntu python: log-output -t ubiquity mount --bind /cdrom /target/cdrom
Oct  1 23:26:07 ubuntu ubiquity: tempfile: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot read file data: Input/output error
Oct  1 23:26:07 ubuntu python: log-output -t ubiquity umount /target/cdrom
Oct  1 23:26:08 ubuntu ubiquity: grep: 
Oct  1 23:26:08 ubuntu ubiquity: /target/etc/apt/sources.list
Oct  1 23:26:08 ubuntu ubiquity: : No such file or directory
Oct  1 23:26:08 ubuntu ubiquity: 
Oct  1 23:26:08 ubuntu python: Exception during installation:
Oct  1 23:26:08 ubuntu python: Traceback (most recent call last):
Oct  1 23:26:08 ubuntu python:   File "/usr/share/ubiquity/install.py", line 2323, in <module>
Oct  1 23:26:08 ubuntu python:     install.run()
Oct  1 23:26:08 ubuntu python:   File "/usr/share/ubiquity/install.py", line 403, in run
Oct  1 23:26:08 ubuntu python:     self.configure_apt()
Oct  1 23:26:08 ubuntu python:   File "/usr/share/ubiquity/install.py", line 1215, in configure_apt
Oct  1 23:26:08 ubuntu python:     raise InstallStepError("AptSetup failed with code %d" % ret)
Oct  1 23:26:08 ubuntu python: InstallStepError: AptSetup failed with code 127
Oct  1 23:26:08 ubuntu python: 
Oct  1 23:26:08 ubuntu ubiquity[3534]: debconffilter_done: ubiquity.components.install (current: None)
Oct  1 23:26:08 ubuntu ubiquity[3534]: Exception in GTK frontend (invoking crash handler):
Oct  1 23:26:08 ubuntu ubiquity[3534]: Traceback (most recent call last):
Oct  1 23:26:08 ubuntu ubiquity[3534]:   File "/usr/lib/ubiquity/bin/ubiquity", line 457, in <module>
Oct  1 23:26:08 ubuntu ubiquity[3534]:     main(oem_config)
Oct  1 23:26:08 ubuntu ubiquity[3534]:   File "/usr/lib/ubiquity/bin/ubiquity", line 442, in main
Oct  1 23:26:08 ubuntu ubiquity[3534]:     install(args[0], query=options.query)
Oct  1 23:26:08 ubuntu ubiquity[3534]:   File "/usr/lib/ubiquity/bin/ubiquity", line 245, in install
Oct  1 23:26:08 ubuntu ubiquity[3534]:     ret = wizard.run()
Oct  1 23:26:08 ubuntu ubiquity[3534]:   File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 457, in run
Oct  1 23:26:08 ubuntu ubiquity[3534]:     self.progress_loop()
Oct  1 23:26:08 ubuntu ubiquity[3534]:   File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 967, in progress_loop
Oct  1 23:26:08 ubuntu ubiquity[3534]:     (ret, realtb))
Oct  1 23:26:08 ubuntu ubiquity[3534]: RuntimeError: Install failed with exit code 1
Oct  1 23:26:08 ubuntu ubiquity[3534]: Traceback (most recent call last):
Oct  1 23:26:08 ubuntu ubiquity[3534]:   File "/usr/share/ubiquity/install.py", line 2323, in <module>
Oct  1 23:26:08 ubuntu ubiquity[3534]:     install.run()
Oct  1 23:26:08 ubuntu ubiquity[3534]:   File "/usr/share/ubiquity/install.py", line 403, in run
Oct  1 23:26:08 ubuntu ubiquity[3534]:     self.configure_apt()
Oct  1 23:26:08 ubuntu ubiquity[3534]:   File "/usr/share/ubiquity/install.py", line 1215, in configure_apt
Oct  1 23:26:08 ubuntu ubiquity[3534]:     raise InstallStepError("AptSetup failed with code %d" % ret)
Oct  1 23:26:08 ubuntu ubiquity[3534]: InstallStepError: AptSetup failed with code 127
------------------------------------------------
:confused:

---

### Post by ngfrazier on 2009-10-03
Just went back to 9.04. Everything works. Kinda silly, but 9.10 Alpha 1 was the most stable for me... Wonder why the Beta will not properly install?

Anyone else having problems installing 9.10?

---

### Post by imaca on 2009-10-08
Not sure if its the same problem, but Ubiquity crashes for me just after the install begins ( i  presume setting up the partitions)
I got alpha installed at least, but went bad after update last week.

---

### Post by pharnet on 2009-10-08
Beta UNR installed for me on the Mini 9, 8GB SSD.

Initially tried it with an ext2 partition but it wouldn't perform the partitioning. I was replacing the XP partition so I blamed it on that. So I selected "back", created a new partition table and used ext4. 

Installed fine.

I think I would try downloading another copy of the iso from a different source, check the md5 sums (again), try a different computer to create the flash drive on, try a different flash drive? 

Possibly a newer daily build might help. I looked for it briefly before going with the official Beta.

---

### Post by KegHead on 2009-10-08
hi!

i too had problems with my mini 9.

reinstalled 9.04 and then went back to 9.10 with no problems since.

KegHead

---

### Post by rockin_goliath on 2009-10-08
Strange. Installing the beta worked perfectly for me. I used the usb-creator utility found in the repositories to write the image to a 4 gb flash drive.
Dell Mini 9, 32 gb ssd, 2 gb ram.

---

### Post by ngfrazier on 2009-10-08
Thanks for the comments. I went back to 9.04 until 9.10 is finally released. I am just so eager to enjoy the new kernel and new Intel video improvements (kernel mode FTW :guitar:)!

FYI: dell mini 9, 32gb ssd, 2gb ram. Kernel mode video REALLY improves flash performance. Also recommended: download chrome from the  ubuntu chromium project.

---

### Post by HankB on 2009-10-10
I'm running into a problem with the UNR beta too. I'm using the USB boot disk creator on another PC to create the boot USB drive and have done so twice now. When I try to check the US drive on my Eee PC 901, it reports "errors found in 1 files!"

When I try to install, it gets past partitioniung and reformatting the drive and gets an I/O error reading .../Debian.Changelog.gz (from memory...)

I've installed several different versions of Ubuntu from this flash drive so I'd be surprised if it is bad. I'll have a go with one of the alpha Karmic releases and see how that works.

I'm not sure if this is related to the problem you face. It sounds like you made more progress.

---

