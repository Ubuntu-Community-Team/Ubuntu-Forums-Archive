---
title: "Can't Use Software Centre"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by aydee on 2010-07-15
I can't use software center. I recently tried ti install mint menu (failed) and Mints software center works but I prefer Ubuntu's

---

### Post by cj.surrusco on 2010-07-15
I can't really understand your situation, I think you need to explain it more.

---

### Post by aydee on 2010-07-15
I click on software center and it says starting software center in window list applet and it disappears  and nothing happens

---

### Post by cj.surrusco on 2010-07-15
There is a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/470564").

It says to try removing the package 'frei0r-plugins'.

---

### Post by lisar915 on 2010-07-15
Hi, 

I have the same problem.  I tried using the terminal to remove that plugin, but I just got a message saying it's not installed on my system to begin with.

---

### Post by mörgæs on 2010-07-15
I have never understood the idea behind Software Centre. Just install your packages through Synaptic, and there will be no hassle.

---

### Post by cj.surrusco on 2010-07-15
+1 for synaptic; it's as good, or maybe better than the Software Center.

---

### Post by aydee on 2010-07-19
> **cj.surrusco said:**
> There is a bug report [here]("https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/470564").

It says to try removing the package 'frei0r-plugins'.

Sorry, I'm a n00b, how do you do that???  and I HATE synaptic because I prefer GUI's that do BASICALLY ALL the work... I'm lazy...

---

### Post by lisati on 2010-07-19
> **aydee said:**
> Sorry, I'm a n00b, how do you do that???  and I HATE synaptic because I prefer GUI's that do BASICALLY ALL the work... I'm lazy...
On my system, synaptic package manager comes with a GUI - it can be found on the System->Administration menu.

---

### Post by aydee on 2010-07-19
> **lisati said:**
> On my system, synaptic package manager comes with a GUI - it can be found on the System->Administration menu.
I mean That takes 1 butten push (Install)  and I Always Forget to keep the dependancies

---

### Post by Eliot89 on 2010-07-19
I'm having the same problem and I removed the plugins with no avail.

when I try to open it in a terminal I get this:

eliot89@smash:~$ software-center
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
eliot89@smash:~$ 



any ideas?

---

### Post by aydee on 2010-07-26
Well now GRUB thinks I am running Mint

---

