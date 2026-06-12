---
title: "Sync - Software Center"
date: 2012-04-30
forum: Installation &amp; Upgrades
---

### Post by reldridge80 on 2012-04-30
I have just upgraded two machines to 12.04 and I am trying to use the new Sync feature in the Software Center.

When selecting file -  "sync between computers", I only see results for the machine that I am on.

Both machines are logged in to the Ubuntu one account, but i am not sure if this is what software center is using for this sync?

Also if i run software-center from terminal i get the following errors:

> cereal@Ubuntu-Black:~$ software-center
2012-04-30 11:28:16,818 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-04-30 11:28:16,829 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-04-30 11:28:17,717 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file


On selecting file -"sync between computers" I receive this error in the terminal:

> 2012-04-30 11:29:31,909 - softwarecenter.backend.login_sso - ERROR - _on_credentails_error for Ubuntu Software Center: dbus.Dictionary({dbus.String(u'errtype'): dbus.String(u'AssertionError'), dbus.String(u'message'): dbus.String(u'Assertion failed.')}, signature=dbus.Signature('ss')) ()


Any help would be appreciated - Thanks.
Ryan.

---

### Post by reldridge80 on 2012-05-01
I guess i am going to do a full install on one of these machines and see if that changes the issues to figure out if the upgrade was the issue or not. 

Will post what i find.


Anyone having any issues with sync, or better yet have sync in software center working?

Thanks again - 
Ryan

---

### Post by reldridge80 on 2012-05-03
I have re-installed one of these machines and a clean install has fixed the software center sync issue.

I am guessing i will have to do this to the other machine? I am hoping not too but I have not found an answer to this any other way.

As far as just resetting the account that software sync now uses how can i try this?

I have tried to re-install software center and delete its cache but that didn't seem to fix the issue. 

I am not sure if this is also playing into the issues but i get a token keyring prompt that i need to type the password in every time i reboot the machine as well.

Thanks again
ryan.

---

### Post by rybu on 2012-05-23
I'm having exactly the same problem, with two freshly-installed (today!) Ubuntu 12.04 distributions.   Have you made any progress?

---

