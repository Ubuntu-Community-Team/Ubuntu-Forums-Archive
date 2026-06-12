---
title: "Possible solution for anyone having NM7 and cellmodem problems..."
date: 2008-10-04
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Jim March on 2008-10-04
I was having trouble with two different cellmodems: my KPC680 (Expresscard) on the Verizon network, and a friend's U680 (USB) on Sprint.  These devices aren't at all similar despite sharing "680".  Both had connections that would die out after a few minutes.  I had tested these under Intrepid Alpha6, and then the KPC680 under Beta1, no change.

I was able to completely fix the KPC680, however I don't have the U680 available for testing.  But because the symptoms were the same, I'm guessing the cure was the same...

**[COLOR="Red"]The fix is to edit /etc/ppp/options:[/COLOR]**

sudo gedit /etc/ppp/options

...and find the lines for "lcp-echo-failure" and "lcp-echo-interval" and set both to 0.  You can see my actual file at:

[http://ubuntuforums.org/showpost.php?p=5903831&postcount=9](http://ubuntuforums.org/showpost.php?p=5903831&postcount=9)

I also tested this without NM7 (just set it to "network off") and then did a WVdial script as described at that link, so I'm guessing that would work in Hardy.  See additional notes at that link.

**Other notes:** I had tried a Verizon USB720 device under Intrepid Alpha5 and had no problems at all with NM7, so this issue isn't going to affect every cellmodem.  This post is provided for anyone having troubles but if you're not, cool.

---

### Post by dro0g on 2008-10-28
Thank you! I was having the same problem on Verizon - the connection would drop every 2.5 minutes with
> No response to 4 echo-requests
Serial link appears to be disconnected.
Connect time 2.5 minutes.

in syslog. I spent a long while changing lcp-echo-failure and lcp-echo-interval in /etc/ppp/peers/ppp0 rather than /etc/ppp/options. Changing both in /etc/ppp/options to 0 fixed it.

The options in the NetworkManager GUI don't seem to do anything.

---

### Post by reg-sux on 2008-10-28
The options on NM do something, but pppd gives a higher priority to the values on that file.


This has been discussed recently on NM's mailing list, and the latest SVN version already has this issue fixed.


The thread starts here:
[http://mail.gnome.org/archives/networkmanager-list/2008-October/msg00272.html](http://mail.gnome.org/archives/networkmanager-list/2008-October/msg00272.html)


ChangeLog entry:

2008-10-23  Dan Williams  <dcbw@======.===>

* src/ppp-manager/nm-ppp-manager.c
- (create_pppd_cmd_line): pppd always parses /etc/ppp/options, so always add really important stuff to the command line to ensure that NM overrides /etc/ppp/options (bgo #556781)

---

