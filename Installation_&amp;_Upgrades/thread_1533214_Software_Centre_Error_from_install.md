---
title: "Software Centre Error from install"
date: 2010-07-17
forum: Installation &amp; Upgrades
---

### Post by dancemat on 2010-07-17
[SIZE=2]Hello Everyone,

I want to thank all the team behind Ubuntu and in particular Xubuntu. I think it's an excellent distro.

I am currently dual booting Windows and Xubuntu.

When I run the Software Centre it attempts to load, then quits. I tried running from the terminal using 

/usr/bin/software-center

I get the following error:

WARNING:root:No styling hints for Albatross were found... using Human hints.
WARNING:root:No styling hints for Albatross were found... using Human hints.
WARNING:root:No styling hints for Albatross were found... using Human hints.
WARNING:root:No styling hints for Albatross were found... using Human hints.
WARNING:root:No styling hints for Albatross were found... using Human hints.
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 201, in __init__
    self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
    store = ViewSwitcherList(datadir, db, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 204, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 274, in _update_channel_list
    self.channels = self._get_channels()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 352, in _get_channels
    channels.append(partner_channel)
UnboundLocalError: local variable 'partner_channel' referenced before assignment

Any help would be much appreciated!

The only thing I have done, is setup my wireless and installed all security and proposed updates.

As far as I am aware they completed successfully.

I installed and reinstalled the software centre, am still having the same problem.

Using: sudo apt-get purge software-center

and: sudo apt-get install software-center

Kind Regards,

Matthew[/SIZE]

---

### Post by bobnutfield on 2010-07-18
I have just done the most recent updates and am now getting the same issue with Software-center.  It was working just prior to the updates so I am sure it is related to the app-install-data-partner package.  I re-installed this package but it did not solve the issue.  Still investigating, if I find a solution I will post it here.  But, we may have to wait for a further update to fix the problem.

---

### Post by dancemat on 2010-07-18
Thanks for your reply Bob.

I thought it was something I had done, had been rather puzzled about it. Never had the issue happen before.

Do you think this should be reported as a bug, if from your research you cannot find a solution?

---

### Post by bobnutfield on 2010-07-18
Well, I just did the updates about an hour ago.  I had just used the Software center to install an application just prior to the update, so I know it is related to the update and there are a number of other users experiencing the same thing.  There is an app called app-install-data-partner which is part of the gnome-install program.  This what I believe is causing the issues, but as I said re-installing it did not help, so we may have to wait until it is fixed by the developers.  Synaptic still works fine, so it is not really a huge problem for now.

---

### Post by dancemat on 2010-07-18
> **bobnutfield said:**
> Well, I just did the updates about an hour ago.  I had just used the Software center to install an application just prior to the update, so I know it is related to the update and there are a number of other users experiencing the same thing.  There is an app called app-install-data-partner which is part of the gnome-install program.  This what I believe is causing the issues, but as I said re-installing it did not help, so we may have to wait until it is fixed by the developers.  Synaptic still works fine, so it is not really a huge problem for now.

I see. :)

I was just wondering if there was a protocol to notify the developers? I imagine they frequently read the forums though?

---

### Post by bobnutfield on 2010-07-18
It is a bug, and it has already been reported and a fix has been committed:

[https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/606452]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/606452")

---

### Post by dancemat on 2010-07-18
Thanks for the link. :)

---

