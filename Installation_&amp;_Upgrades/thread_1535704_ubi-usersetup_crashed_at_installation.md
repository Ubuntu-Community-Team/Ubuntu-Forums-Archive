---
title: "ubi-usersetup crashed at installation"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by zsjoska on 2010-07-21
Hi,

I have the image on a pen drive and I did several installations from it already.
Now I'm facing a desktop computer where this is shown:
ubi-usersetup failed with exit code 10
Further information may be found in /var/log/syslog

In syslog, i have 
Jul 21 17:11:24 ubuntu ubiquity[24369]: switched to page partman
Jul 21 17:11:25 ubuntu ubiquity[24369]: switched to page partman
Jul 21 13:36:37 ubuntu ntpdate[2207]: step time server 91.189.94.4 offset -12893.318251 sec
Jul 21 13:36:41 ubuntu ubiquity[24369]: switched to page partman
Jul 21 13:36:42 ubuntu ubiquity[24369]: switched to page partman
Jul 21 13:36:44 ubuntu ubiquity[24369]: debconffilter_done: ubi-partman (current: ubi-partman)
Jul 21 13:36:44 ubuntu ubiquity[24369]: Step_before = stepPartAdvanced
Jul 21 13:36:44 ubuntu ubiquity[24369]: debconffilter_done: ubi-usersetup (current: ubi-usersetup)
Jul 21 13:36:44 ubuntu ubiquity[24369]: dbfilter_handle_status: ('ubi-usersetup', 10)

If I select continue anyway, the install button is inactive and could not start the installation.

Any idea how to work around this, or to get more info?
If some additional info is needed, I can provide it.

ZsJoska

---

### Post by travlemon on 2010-11-06
> **zsjoska said:**
> Hi,

I have the image on a pen drive and I did several installations from it already.
Now I'm facing a desktop computer where this is shown:
ubi-usersetup failed with exit code 10
Further information may be found in /var/log/syslog

In syslog, i have 
Jul 21 17:11:24 ubuntu ubiquity[24369]: switched to page partman
Jul 21 17:11:25 ubuntu ubiquity[24369]: switched to page partman
Jul 21 13:36:37 ubuntu ntpdate[2207]: step time server 91.189.94.4 offset -12893.318251 sec
Jul 21 13:36:41 ubuntu ubiquity[24369]: switched to page partman
Jul 21 13:36:42 ubuntu ubiquity[24369]: switched to page partman
Jul 21 13:36:44 ubuntu ubiquity[24369]: debconffilter_done: ubi-partman (current: ubi-partman)
Jul 21 13:36:44 ubuntu ubiquity[24369]: Step_before = stepPartAdvanced
Jul 21 13:36:44 ubuntu ubiquity[24369]: debconffilter_done: ubi-usersetup (current: ubi-usersetup)
Jul 21 13:36:44 ubuntu ubiquity[24369]: dbfilter_handle_status: ('ubi-usersetup', 10)

If I select continue anyway, the install button is inactive and could not start the installation.

Any idea how to work around this, or to get more info?
If some additional info is needed, I can provide it.

ZsJoska

have you found a solution to this yet? i recently posted a thread, having a similar issue.  my installation crashes on ubi-usersetup, with exit code 139.  i can't seem to seem to find a solution.  i've tried booting from usb and cd with the same result all around.

my only suggestion (which i've in the middle of trying) is to find a distro completely unrelated to Ubuntu, and try installing that  on the machine to see what happens. that is provided that you don't have any other operating systems on the machine, and have nothing to lose but time.

if you found a way around it, can you post back with the details? i'm open to any information i can get, it's a very frustrating issue

---

### Post by mabynke on 2010-12-20
I'm also struggling  with this with Linux Mint 10, can't find out what to do on the internet. I would be very thankful if someone could reply with the solution to this.

---

### Post by antonioperez on 2011-01-16
See this:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/527848](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/527848)
and this:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/535630](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/535630)

It seems it's fixed. You have to boot using 'Try ubuntu', then update installer and run installation.

I'll try tomorrow.

Good luck.

---

### Post by antonioperez on 2011-01-16
Another options seems to be: In boot menu, press F6 to show options, and mark 'nodmraid'. After that install it normally. But it didn't work for me.

---

### Post by travlemon on 2011-01-25
> **antonioperez said:**
> See this:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/527848](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/527848)
and this:
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/535630](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/535630)

It seems it's fixed. You have to boot using 'Try ubuntu', then update installer and run installation.

I'll try tomorrow.

Good luck.


I just noticed this thread got some replies.  I tried this solution, and the second one you mentioned, but no luck. 

I'm also getting other weird issues when I boot into the live CD.  When I try to run a terminal window, it opens for just a second and closes by itself.  When I tried to switch over to a console, I tried CTRL + ALT + F1 through F4, and there is a welcome message that keeps looping.  It never gives me a chance to type.  Often times, in the loop, I'll frequently see two messages:

"malloc: block on free list clobbered" and the other message is: "malloc:  assertion botched"

So far, the only two popular distros that will install on this machine are OpenSUSE and DreamLinux, but I'd really like any Ubuntu based distro.

The machine I'm using is a Dell Inspiron 8100 laptop with a 1.2gb CPU, 512mb of ram, and  a 40gb hard drive.

I've grown to dislike Windows so much that I'd rather go through the trouble trying to figure out the problem, rather than just put XP on there!

---

