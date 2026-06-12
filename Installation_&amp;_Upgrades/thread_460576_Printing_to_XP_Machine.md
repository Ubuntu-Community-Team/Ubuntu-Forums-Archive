---
title: "Printing to XP Machine"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by jdmrsx05 on 2007-05-31
OK, I've been on different forums for years and I know to search for answers first, but despite the 100's of forums I've read I have not been able to resolve my problem yet.  Here's the deal.

I have Ubuntu 7.04 installed on my laptop.  I have an XP machine with an HP PSC 1210 all-in-one on it via USB.  The two other XP machines in my house are able to print through our network, however I am not able to correctly set it up in Ubuntu.

I go to System -> Administration -> Printing
I open New Printer
I select Network Printer then click the dropdown
I am prompted for a username/password to access my WORKGROUP.  I don't enter anything because I don't know username/password to use.
I select the computer that the printer is connected to (again I get prompted for a username/password that I don't know what to use)
I then select the printer on that computer (it shows up with no problem)
I click forward -> HP -> PSC 1210 -> apply

The printer shows up as "ready" and when I try to print a test page, it sends the test, the printer starts up, but then never does anything.  Paper doesn't move or anything.  I check the printer status on that computer, and it says "Printing" and the queue on Ubuntu has become empty.  If I try to cancel, the printer hangs up and the XP machine has to be rebooted to clear the queue.  

I've thoroughly enjoyed Ubuntu until this point.  Can anyone offer any help?  Thank you!

---

### Post by obrient on 2007-05-31
First off is the printer shared in Windows?

Next would be try the username and password you login to Windows with to access the Workgroup. I have done this at home and it works, but I had to share the printer in XP and used my username and password. Also make sure that you are using Windows (SMB).

The name of your Windows Machine is needed so Linux knows where to send the file. Hope this helps.

---

### Post by jdmrsx05 on 2007-06-01
Yes, the printer is shared in Windows.  I have two other XP machines that can print to it from opposite ends of the house.  When I added each computer to the workgroup, I was never prompted for a username/password.  There are four users set up on the machine that the printer is hooked up to, so which one would I log on with?  Only one of them has a password associated with it.  Can I set up a specific username and password to set up the workgroup with?

---

