---
title: "kdesvn missing in 15.10"
date: 2015-11-08
forum: Installation &amp; Upgrades
---

### Post by marco-nightlabs on 2015-11-08
Hello *,

I wanted to report this as a new bug in the launchpad bugtracker - [https://bugs.launchpad.net/](https://bugs.launchpad.net/) -, but it seems the web-UI does not provide the feature "report new bug"?! Or did I overlook it? I searched for quite a while.

Anyway, my problem is this: I installed Kubuntu 15.10 on another machine (my wife's) and didn't find kdesvn in the available packages, anymore. When I did some research, I saw that it was seemingly dropped, because it's said to conflict with some kdesdk packages:

kdesdk-dolphin-plugins
kdesdk-kio-plugins

I thus installed these kdesdk packages, but they ABSOLUTELY SUCK!!! They are NOT USABLE!!! Here's why:

1) The KWallet integration does not work at all! Neither at first update, it asks for the SVN repository password and stores it in KWallet, nor does it pop up a dialog to open my KWallet (asking for the KWallet password) when the SVN repo password is already stored in KWallet.

Thus I had to disable KWallet. After disabling all password-stores in ~/.subversion/config and storing the passwords in plaintext using the svn command line client, I was able to use the kdesdk plugins. Am I really supposed to store the passwords in plain-text in the future?!???

2) They do not show any helpful error messages! After installing and enabling said plugins, I indeed saw SVN functionality in Dolphin. Hence I first tried to update a repository. The result: It just told me in a red box that the update failed - no details at all, no button to open a dialog showing details - nothing. It turned out that the kdesdk plugins do not support to prompt for a password and the KWallet integration does not work even if the password was already stored (see (1) above).

3) I do not see what changes I commit! If I simply click on SVN Commit in the context menu, it asks me for a description, but it does not show which files are modified. Maybe I do not want to commit all?! No way to tell which files should be committed and which should not.

4) I cannot easily + reliably commit all changes! If I use the SVN Commit from the context menu, I do not see new files, which are not yet added to SVN, hence I cannot add them all at once here. The only way to add files to SVN is to manually right-click onto each file and use the "SVN Add" from the context menu FOR EACH FILE INDIVIDUALLY!

This is not only very user-UNfriendly and inconvenient, but also very prone to forgetting new files/directories!

5) The kdesdk stuff lacks nearly all functionality needed to work  with SVN! There's no way to access the history (at least I didn't find  any), there's no way to solve collisions, etc. etc.


Only someone who does not use SVN integration in KDE/Dolphin can decide to drop kdesvn in favour of an obviously incomplete and very broken, i.e. totally unusable alternative! kdesvn works fine with KWallet, it shows a list of all modifications when committing and provides the possibility to both bulk-select and individually select/deselect the changes. Additionally, it provides nearly full SVN functionality, like accessing the history, solving collisions and many more. This is what I expect from a usable SVN integration.

I do not expect that kdesdk will have the missing features, any time soon, because there are simply too many issues. Is there a way to install kdesvn? Are you going to re-add kdesvn to the official repositories until the kdesdk stuff is mature enough to replace it?

What's the workaround? Downgrading to Kubuntu 14.04 LTS? Any alternative solution?

Where's the right location to file this bug? After all, functionality that's broken/missing and was working fine in an older version by definition clearly is a regression bug. Since the Kubuntu maintainers decided to drop the kdesvn packages since Kubuntu 15.10 WITHOUT A USABLE ALTERNATIVE, this is a regression bug of Kubuntu.

Best regards, Marco :-)

---

### Post by bapoumba on 2015-11-08
Sorry I cannot help you much with kubuntu.

To report a bug at launchpad :
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)
From the web interface :
[https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)

---

### Post by marco-nightlabs on 2015-11-08
Thanks a lot for the quick response! I'll file a bug in Launchpad, then.

Fortunately, I found a workaround in the meantime: I was able to download and install the packages [FONT=courier new]libsvnqt7[/FONT], [FONT=monospace][FONT=courier new]kdesvn-kio-plugins[/FONT] and [/FONT][FONT=courier new]kdesvn[/FONT] from the Ubuntu 14.04 repositories. They seem to be compatible.

Unfortunately, this way, there's no Dolphin integration, but I (or more precisely my wife) can at least open the working-copy in the self-standing kdesvn program and update+commit (and more) there. However, it's only a question of time until the old 14.04-packages won't be compatible, anymore, hence this can be nothing more than a temporary workaround.

---

### Post by marco-nightlabs on 2015-11-08
Here's the bug report: [https://bugs.launchpad.net/ubuntu/+source/kdesvn/+bug/1514200](https://bugs.launchpad.net/ubuntu/+source/kdesvn/+bug/1514200)

---

### Post by marco-nightlabs on 2015-11-08
Just a short note: I didn't find the "Report a bug" function, because I was looking in [https://bugs.launchpad.net/](https://bugs.launchpad.net/) - there really seems to be no (more or less) direct way to file a new bug. When I go to [https://bugs.launchpad.net/ubuntu/](https://bugs.launchpad.net/ubuntu/) instead, there's "Report a bug" in the right top corner.

---

### Post by bapoumba on 2015-11-08
Well, to report a bug (see the first link in my above post), you have to go to the project page, for ex for kdesvn : [https://launchpad.net/ubuntu/+source/kdesvn](https://launchpad.net/ubuntu/+source/kdesvn)
You have a "Report Bug" link under "Get Involved".
Sometimes the LP interface is a bit convoluted :)

---

