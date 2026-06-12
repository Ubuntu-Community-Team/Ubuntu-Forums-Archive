---
title: "Disable touchpad when typing - SHMConfig?"
date: 2009-02-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by _oOMOo_ on 2009-02-22
During the development of Intrepid, there were some efforts made to allow the use of syndaemon without having to enable SHMConfig. Now we have effectively moved to .fdi files and xinput to configure input devices, is there a way to disable the touchpad when typing without turning SHMConfig on?

Cheers, Jon

/*=======Bug report======*/

For anyone stumbling on this thread, there is a launchpad bug for this:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/295236]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/295236")

---

### Post by krazyd on 2009-02-22
Yes. Add ```
syndaemon -d -t
``` to automatically run on startup. You may need to install syndaemon if it isn't already.

---

### Post by caryb on 2009-02-22
Cant find that package..

```
root@stinkpad:~# apt-get install syndaemon
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package syndaemon
root@stinkpad:~#

```

It is in xserver-xorg-input-synaptics


Cary

---

### Post by _oOMOo_ on 2009-02-23
> **krazyd said:**
> Yes. Add ```
syndaemon -d -t
``` to automatically run on startup. You may need to install syndaemon if it isn't already.


Thanks but I already have syndaemon set to run at startup. Here's the output when I run it at the command line:

```
:~$ syndaemon -d -t
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  144 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  10
  Current serial number in output stream:  10

```

I'm using x86_64, not sure if the 32 bit version works.

Cheers, Jon

---

### Post by krazyd on 2009-02-23
Huh.. [this bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/295236") is still active in Jaunty? I'm running intrepid and assumed it must have been fixed.

---

### Post by _oOMOo_ on 2009-02-23
> **krazyd said:**
> Huh.. [this bug]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/295236") is still active in Jaunty? I'm running intrepid and assumed it must have been fixed.

Thanks krazyd. That poxy bug never was fixed in Intrepid, I even wrote a blog post about that issue which still gets about 50 views a day. I'd seen a few updates to xserver-xorg-input-synaptics come down the pipe since installing Jaunty a while ago and assumed that we were using a whole new version thanks to the other changes in X.

Thanks again for the pointer to the bug, I'll go and make some noise over there :)

Jon

---

### Post by digitalramble on 2009-04-15
OMG, thank  you thank you thank you for the syndaemon pointer!  It was driving me NUTS having things jump around b/c the touchpad would decide to jump to wherever the cursor was while I was typing... wow... NICE.

FYI: I have the latest version of Jaunty installed, syndaemon was installed and ran with no error messages.   And I typed this without having my cursor jump around!  Sweet!

---

### Post by caryb on 2009-04-15
When I try the command I get the following...

> cary@stinkpad:~$ syndaemon -d -t
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  142 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  12
  Current serial number in output stream:  12
cary@stinkpad:~$


Cary

---

### Post by ConceptJunkie on 2009-04-20
Cary:  Maybe if you didn't call your machine "stinkpad" it would be nicer to you!  ;-) (I should talk, my machine is called "pigmeyer")

Anyhow, I've seen and used the syndaemon command in Intrepid.  I was hoping this was made a little more "automagic" in Jaunty, but apparently it's not there yet.  This is a little frustrating because touchpads are almost ubiquitous on laptops and disabling them with typing is IMO a required ergonomic feature.  Windows does this automatically, and I think Ubuntu should too.  Of course, I'm sure a good solution will come about eventually.  I'm really impressed with other improvements I've seen in Jaunty.
 
Anyhow, my question is this, where would be the appropriate place to put a call to syndaemon in a script for starting up when I log in?  I could put it in .bashrc since I _always_ have a bash window open, but there's obviously a more appropriate place.

Thanks,

Rick

---

### Post by HankB on 2009-04-20
> **ConceptJunkie said:**
> 
Anyhow, my question is this, where would be the appropriate place to put a call to syndaemon in a script for starting up when I log in?  I could put it in .bashrc since I _always_ have a bash window open, but there's obviously a more appropriate place.
If you're logging in using the Gnome desktop, I believe the right place is in System -> Preferences -> Startup Applications. That's where I put it in Intrepid and I see the same menu item in Jaunty.

---

### Post by crjackson on 2009-04-20
> **HankB said:**
> If you're logging in using the Gnome desktop, I believe the right place is in System -> Preferences -> Startup Applications. That's where I put it in Intrepid and I see the same menu item in Jaunty.

Exactly, and after that it is automatic. I just did this to mine a few days ago, and no modifications to the xorg.conf is needed. For me there is no more SHMConfig. In fact, putting that in my xorg.conf file stopped the booting process due to errors. I had to remove that line to return to normal booting. That's when I found that the syndeamon was running and had fixed the issue.

---

### Post by matthewbpt on 2009-04-20
> **ConceptJunkie said:**
> Cary:  Maybe if you didn't call your machine "stinkpad" it would be nicer to you!  ;-) (I should talk, my machine is called "pigmeyer")

Anyhow, I've seen and used the syndaemon command in Intrepid.  I was hoping this was made a little more "automagic" in Jaunty, but apparently it's not there yet.  This is a little frustrating because touchpads are almost ubiquitous on laptops and disabling them with typing is IMO a required ergonomic feature.  Windows does this automatically, and I think Ubuntu should too.  Of course, I'm sure a good solution will come about eventually.  I'm really impressed with other improvements I've seen in Jaunty.
 
Anyhow, my question is this, where would be the appropriate place to put a call to syndaemon in a script for starting up when I log in?  I could put it in .bashrc since I _always_ have a bash window open, but there's obviously a more appropriate place.

Thanks,

Rick

You can add it to your startup programs in Preferences >> Startup Applications. When I used Vista the touchpad wasnt disabled for me automatically and it caused me an endless amount of annoyance, but the syndaemon command works for me in Jaunty on one of my laptops but not the other... not sure why, it works on my EeePC with 32bit jaunty, but not on my HP dv9000 with 64bit jaunty

---

