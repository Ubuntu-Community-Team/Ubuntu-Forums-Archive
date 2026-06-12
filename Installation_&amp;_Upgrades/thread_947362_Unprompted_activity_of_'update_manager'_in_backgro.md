---
title: "Unprompted activity of 'update manager' in background (bug?)"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by vermoos on 2008-10-14
I am using Hardy Heron 8.04

I have noticed the application launcher icon for the update manager intermittently appear in the top right hand corner of the desktop.

There is no prompt for a password, and I noted the following:

0) The system monitor indicated the thread was 'sleeping';
1) No download activity was apparent;
2) In 'System>Administration>Software Sources', the 'download all updates in the background' was _unchecked_

I assume this is a zombie thread with possible security implications. 

Is this problem unique to my box or is it more common?

MIKLE

---

### Post by kostkon on 2008-10-14
> **vermoos said:**
> I am using Hardy Heron 8.04

I have noticed the application launcher icon for the update manager intermittently appear in the top right hand corner of the desktop.

There is no prompt for a password, and I noted the following:

0) The system monitor indicated the thread was 'sleeping';
1) No download activity was apparent;
2) In 'System>Administration>Software Sources', the 'download all updates in the background' was _unchecked_

I assume this is a zombie thread with possible security implications. 

Is this problem unique to my box or is it more common?

MIKLE
Nothing strange there.

First of all, the icon appears when there are updates you have to install. You click on it and then the update manager starts (it may not ask you for a admin password).

Now, sometimes the icon may appear and then instantly dissappear. This happens because every day (in most cases during the morning hours) the system checks if there are new updates. So, the *update-notifier* process (which if you check runs all the time in the background) pops-up the icon for some reason during the checking.

Of course, if there are some updates, the icon appears and stays.

Thus, it happens sometimes, nothing to worry about.

---

