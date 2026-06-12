---
title: "Installer Crashes - Hopes are Dashed."
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by fragmented_user on 2006-07-17
Hi. 

After several very uncomfortable experiences with Linux distributions I decided to turn to Ubuntu for an answer. I had heard great things about the Ubuntu distribution and even greater things about the Ubuntu community. So I set out to try Ubuntu and perhaps find a distribution that I could stick with for good. I loyally waited the 6 hours it took to download the Ubuntu Live CD image, breathlessly burned the image to an empty Disc, and booted the computer with baited breath.

 The configurator worked like a charm and in almost no time I was greeted by a handsome chocolate textured desktop and an exotic tinged startup sound. I wasted no time double clicking on the icon labeled "Install" prominently displayed on the default desktop and waited for my Ubuntu install to begin. I eagerly entered my language/locale,timezone, Name, Computer name, and even username and password and hit the Next button which would start the partioning and install. But alas, it was not meant to be. I was suddenly faced with an ominous looking alert box informing me that the installer had crashed and In one fell swoop my hopes were dashed. This is what I saw.

```


We're sorry; the installer crashed. Please file a bug report at https://launchpad.net/distros/ubuntu/+source/ubiquity/+filebug and a developer will attend to the problem as soon as possible. To help the developers understand what went wrong, include the following detail in your bug report, and attach the files /var/log/installer/syslog, /var/log/syslog, and /var/log/partman:

Traceback (most recent call last):
 File "/usr/lib/python2.4/site-packages/ubiquity/frontend/gtkui.py", line 1169, in watch_debconf_fd_helper
 return callback(source, debconf_condition)
 File "/usr/lib/python2.4/site-packages/ubiquity/filteredcommand.py", line 144, in process_input
 if not self.process_line():
 File "/usr/lib/python2.4/site-packages/ubiquity/filteredcommand.py", line 82, in process_line
 return self.dbfilter.process_line()
 File "/usr/lib/python2.4/site-packages/ubiquity/debconffilter.py", line 219, in process_line
 if not input_widgets[0].run(priority, question):
 File "/usr/lib/python2.4/site-packages/ubiquity/components/partman.py", line 214, in run
 if not self.frontend.set_disk_choices(self.choices(question),
 File "/usr/lib/python2.4/site-packages/ubiquity/filteredcommand.py", line 189, in choices
 choices = unicode(self.db.metaget(question, 'choices'), 'utf-8')
UnicodeDecodeError: 'utf8' codec can't decode byte 0x80 in position 152: unexpected code byte


```

I wondered perhaps that this error had been previously reported and so I scoured the Ubuntu site searching for a possible cause for this error. But to no avail. Here I am left empty-handed, with no distribution to show for my months of effort(testing this and other Distros). Perhaps Fedora Core will work. Perhaps it won't. I hear that Fedora fills 3  CDs and I do not yet want to be forced to use a Distro that is so bloated. Ubuntu Community, I am now at your mercy. I wonder if the community will live up to its reputation. I will no doubt be forever grateful if my dilemma is solved.

URLs of tried solutions
[https://wiki.ubuntu.com/DapperReleaseNotes/UbiquityKnownIssues](https://wiki.ubuntu.com/DapperReleaseNotes/UbiquityKnownIssues)




/var/log/installer/syslog
enclosed in attached file
/crash.tar.gz /var.log.installer.syslog.txt

/var/log/syslog
enclosed in attached file
/crash.tar.gz /var.log.syslog.txt

/var/log/partman
enclosed in attached file
/crash.tar.gz /var.log.partman.txt

PS. A bug report has been filed.
[https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/53291](https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/53291)

Sincerely,
Joseph

---

### Post by scxtt on 2006-07-17
just for curiosity, have you tried again?

if it keeps doing it, you could always give the alternate CD a go (tho i know it's not fun waiting for another download and another burn) ... looks to be some problem w/ ubiquity which could just be a problem w/ the burn or the disk - hard to say ...

---

### Post by fragmented_user on 2006-07-17
I have tried twice with 2 different CDs

---

### Post by fragmented_user on 2006-07-17
Thanks to Ubuntu.FR and Google Translator I found the solution to this problem. All I did was unplug all of my USB Flash drives before Install and Voila, no error :)

---

### Post by scxtt on 2006-07-17
well that's good :) -- gotta love a simple fix ...

---

### Post by blacklantern on 2006-07-25
I have no usb flash drives, and I'm still getting this problem. Any idea what could be causing it?

---

