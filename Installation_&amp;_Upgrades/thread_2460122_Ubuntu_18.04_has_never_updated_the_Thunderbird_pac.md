---
title: "Ubuntu 18.04 has never updated the Thunderbird package, why not? Fedora did."
date: 2021-04-02
forum: Installation &amp; Upgrades
---

### Post by david503 on 2021-04-02
Ubuntu 18.04.5 LTS

Apparently I'm stuck with the (ancient)  68.10.0 unless I bypass apt-get and use a raw .deb file.   (Current version is [COLOR=#333333][FONT=&amp]78.8.1) [/FONT][/COLOR]Isn't this supposed to be "LTS"? [COLOR=#333333][FONT=&amp]When can I expect it to be update, thanks.[/FONT][/COLOR]

And yes of course I ran apt-get update first. 

d

---

### Post by guiverc on 2021-04-02
Ubuntu standard procedure is to back-port security patches only, with few exceptions, one such relates to Thunderbird on Ubuntu 20.04 LTS (*focal*)

> **Ubuntu Backports a Major App Update to Ubuntu 20.04 LTS**

 Joey  Sneddon tells us that Thunderbird 68 is no longer supported upstream,  thus, because it's more work to backport all security fixes to it, the  Ubuntu developers have opted to replace it with Thunderbird 78, quoting  Canonical's Oliver Tilloy. Joey notes the Ubuntu warning that this may  cause disruption for some users due to changes outlined in the post. 


[https://www.omgubuntu.co.uk/2021/02/thunderbird-78-in-ubuntu-20-04-lts](https://www.omgubuntu.co.uk/2021/02/thunderbird-78-in-ubuntu-20-04-lts)

[URL="https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue670"]https://wiki.ubuntu.com/UbuntuWeeklyNewsletter/Issue670
[https://ubuntuforums.org/showthread.php?t=2458076](https://ubuntuforums.org/showthread.php?t=2458076)
[/URL]

---

### Post by walts48 on 2021-04-03
So, how many security patches have been applied between Thunderbird 68.10.0 and the current 78.9.0 release?

I'll let users check at  [URL="https://www.mozilla.org/en-US/security/known-vulnerabilities/thunderbird/"]https://www.mozilla.org/en-US/security/known-vulnerabilities/thunderbird/
[/URL]
I count 3 critical advisories.

Yes, there is the disclaimer:

> *In general, these flaws cannot be exploited through email in the  Thunderbird product because scripting is disabled when reading mail, but  are potentially risks in browser or browser-like contexts.*

EDIT: Forgot to mention that it was updated in 20.04.

[https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1895643](https://bugs.launchpad.net/ubuntu/+source/thunderbird/+bug/1895643)

---

### Post by mikewhatever on 2021-04-03
Thunderburd 78.8.1 is available for 18.04 from the [Mozilla Security PPA]("https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa/+index"). You are more then welcome to use it.

---

### Post by walts48 on 2021-04-05
> **mikewhatever said:**
> Thunderbird 78.8.1 is available for 18.04 from the [Mozilla Security PPA]("https://launchpad.net/~ubuntu-mozilla-security/+archive/ubuntu/ppa/+index"). You are more than welcome to use it.

I'm also welcome to use another Linux distro that doesn't require me to add PPA's to get software I can get from its software updater.

The question still unanswered, is why isn't it in the distributions update PPA.

---

### Post by TheFu on 2021-04-05
walts48 - LTS means something different for companies than it does for you.  We don't want major version changes in software packages without DIRECT ACTION.  That can break workflows. 
You can disagree.  
You can use other distros.  
Having a PPA is a reasonable compromise for the people who wish to use the newer version.  For people who like change, they can move to a new OS every 6 months by using non-LTS releases OR running Arch or any of the other rolling distros.  LTS is LTS. It means something, especially to companies. It is a key reason why we choose Ubuntu and not Arch or the other options.

I like the new thunderbird version. The migration was well handled - for my specific uses. It made lots of things "better" for me compared to the old version.   It would be arrogant to assume that everyone else would be happy with a forced migration that goes against the core meaning of LTS.  The world doesn't revolve around me ... or you.

---

