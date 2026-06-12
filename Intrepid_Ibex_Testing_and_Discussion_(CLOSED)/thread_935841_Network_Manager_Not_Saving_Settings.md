---
title: "Network Manager Not Saving Settings"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by beercz on 2008-10-02
Apologies if this issue has already been posted.  I have searched the forums and am unable to find anyone else with the same issue.

I connect to 4 or 5 wireless networks depending on my location.

I used to run wicd to manage my network wireless connections, but it keeps crashing after a recent update.

So I have switched to nmapplet and gnome-network-manager instead - which work OK

However, when I connect to a new wireless network, and I use gnome network manager to enter the credentials, I can connect without problem.

But if I try and save the settings for the new wireless network gnome network manager closes without saving.

Anyone else experience this problem?

Is there a known bug that has been reported?  If so, can someone please provide the link?

Does anyone know how to fix or work round this issue?

Thanks in advance.

---

### Post by forumache on 2008-10-02
Here it is:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/271097](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/271097)

The proper way to search for bugs must include bugs.launchpad.net, not only forums ;)

---

### Post by beercz on 2008-10-02
Thanks for this :-)

---

### Post by forumache on 2008-10-02
I have the same problem and I posted in that bug report.
It cannot be fixed manually, we need to wait for an updated package. As you can see in the bug report, I provided a link to another bug report where the new package was tested from a PPA and it worked. So, good news :)

I am surprised too, I would have expected more people to complain about this on the forums.

---

### Post by omgbots on 2008-10-02
I was having the same issue.  I was able to workaround it by making the change I wanted, then toggling the "system setting" option twice (if off... turn on and then off or vice versa).

---

### Post by wilsong on 2008-10-03
> **beercz said:**
> Apologies if this issue has already been posted.  I have searched the forums and am unable to find anyone else with the same issue.

I connect to 4 or 5 wireless networks depending on my location.

I used to run wicd to manage my network wireless connections, but it keeps crashing after a recent update.

So I have switched to nmapplet and gnome-network-manager instead - which work OK

However, when I connect to a new wireless network, and I use gnome network manager to enter the credentials, I can connect without problem.

But if I try and save the settings for the new wireless network gnome network manager closes without saving.

Anyone else experience this problem?

Is there a known bug that has been reported?  If so, can someone please provide the link?

Does anyone know how to fix or work round this issue?

Thanks in advance.

See this post, and see if it deals with your issue, [http://ubuntuforums.org/showthread.php?t=934575&page=2](http://ubuntuforums.org/showthread.php?t=934575&page=2)

---

### Post by forumache on 2008-10-03
I had similar problems, see the link to bugs.launchpad.net I indicated.
The bug has been fixed this morning, the new updates to network-manager took care of that.

Update and see if it is fixed for you too.

dan@shuttle:~$ apt-cache policy network-manager
network-manager:
  Installed: 0.7~~svn20080928t225540+eni0-0ubuntu2
  Candidate: 0.7~~svn20080928t225540+eni0-0ubuntu2
  Version table:
 *** 0.7~~svn20080928t225540+eni0-0ubuntu2 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) intrepid/main Packages
        100 /var/lib/dpkg/status
dan@shuttle:~$

---

### Post by lonniehenry on 2008-10-03
The updates solved the password not remembered for me.  It was the biggest bug fix that I needed fixing.  Ibex works better for me over Hardy with this HP dv9000 series machine.

---

### Post by dro0g on 2008-10-03
> **lonniehenry said:**
> The updates solved the password not remembered for me.  It was the biggest bug fix that I needed fixing.  Ibex works better for me over Hardy with this HP dv9000 series machine.

The update fixed it for me as well. Checking off "system" now seems to work too!

Still no love for hidden SSIDs though.

---

### Post by dro0g on 2008-10-03
> **dro0g said:**
> 
Still no love for hidden SSIDs though.

Spoke too soon. Left it alone for about 5 minutes and it eventually connected.

---

