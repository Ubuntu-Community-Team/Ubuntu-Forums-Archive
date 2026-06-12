---
title: "Cannot download / reload in Software Source"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by xiaoqi on 2009-04-01
Can anyone help on this?

I've just installed Ubuntu 9.04. Network interface is OK.
But when open the Software Source and wish to reload the package information, following error occurred:

===START===
The following details are provided:

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg](http://archive.canonical.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/jaunty/partner/i18n/Translation-en_US.bz2)  Could not resolve 'archive.canonical.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_US.bz2)  Could not resolve 'us.archive.ubuntu.com'

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg](http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg)  Could not resolve 'wine.budgetdedicated.com'

W: Failed to fetch [http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_US.bz2](http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-en_US.bz2)  Could not resolve 'wine.budgetdedicated.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.

===E N D===

I'm locating in China, but here I've tried "downlord from" either Main Server or US Server, none of them work.

What's the reason or point I can configure? Thanks.

Regards,
Xiaoqi
[email]xiaoqi@163bj.com[/email]

---

### Post by thewolfman on 2009-04-01
hi,

open synaptic and go to settings, click on repositories and then select a different download location and try that, one near to you would speed up your downloads a bit but not necessarily!.

Hope this helps!.

Stephen

---

### Post by thewolfman on 2009-04-01
sorry me again, I forgot to say select other and pick a location near to you from the long list not just from the main server.

Stephen

---

### Post by xiaoqi on 2009-04-01
Thanks, but unfortunatly it's not work.
I can access web site without problem, but when I use "select best server" in Update Manager, after all of ping actions of 270 servers, it told that "no suitable download server was found, please check your internet connection."

---

### Post by xiaoqi on 2009-04-02
I've just installed 9.04 on another laptop at home, the download/reload is working fine.
Consider the difference, I suspect that cannot work was due to that's located in enterprise environment. It need Proxy, but that proxy need password authentication when in browser, so possible the Software Source need that authentication and don't have field to fill in.
I'll keep observing that...

---

### Post by xiaoqi on 2009-04-06
W: Failed to fetch [http://mirror.lupaworld.com/ubuntu/dists/jaunty/Release.gpg](http://mirror.lupaworld.com/ubuntu/dists/jaunty/Release.gpg)  Could not resolve 'mirror.lupaworld.com'

Same error message when I changed to nearer location for downloading.

Already changed my DNS server IP address through typing, but seems the problem still have.

What can I do? Thanks.

---

### Post by Kareeser on 2009-04-07
System -> Preferences -> Network Proxy

Update-manager *should* honour that... we'll see, now won't we :)

---

### Post by xiaoqi on 2009-04-07
Thanks all for your help, now it works after changing the Proxy configuration.

The root cause is I should not use "automatic proxy configuration", instead of that, after I input one static proxy IP in "manually proxy configuration", the problem solved.

As I observed, my company need the user ID (your NT account) and password for using the proxy, that's fine in Windows environment, as the SSO works so you do not need to type in ID/password again in Internet Explorer. 

But in Linux, since you're not using Windows ID to login, when in Firefox (not tested in IE over WINE yet), sometimes it popup and ask your ID/Password to activate the Proxy. This is not work in Synaptic at all.

Good to see the repository is being updated. Let me move on to test further in Ubuntu, and let's enjoy the Linux life together ;--)

---

