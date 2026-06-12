---
title: "Upgrade security risks in software not yet avail with Ubuntu"
date: 2012-03-18
forum: Installation &amp; Upgrades
---

### Post by robinnelu on 2012-03-18
I ran a security check on my server and found software that needs to be updated, but Ubuntu is not yet providing the update through normal software upgrade channels yet. An example is bzip2; Ubuntu only provides 1.0.5, but 1.0.6 fixes security issues. I know how to either download 1.0.6 or get the latest branch from launchpad.net to get the code fix. The issue I am running into is that the current 1.0.5 installation is in (logged in as root): /bin and /usr/share, /usr/share/man, but the installs are going to install to /usr/local/bin etc.

Should I accept the default installation directories? What will happen to 1.0.5, will both version now exists? Should I uninstall 1.0.5?

If I manually change the location for installation for 1.0.6 to try to replace 1.0.5 I am concerned that I will not get this right for all directories and I don't know if this is how I would essentially replace 1.0.5.

How do you update patches prior to being released by Ubuntu? Also, am I better off just updating Ubuntu. I am currently on 10.04. Thanks.

---

### Post by CharlesA on 2012-03-18
They would both exist on the system. If you remove bzip 1.0.5, you risk breaking programs that depend on it.

What version of Ubuntu are you using? I just checked my lucid machine and I had version 1.0.5.

What security issue are you referring to?

---

### Post by robinnelu on 2012-03-18
Thanks for your reply. I ran CloudPassage.com security check and bzip2 is one out of eleven software security issues it found. For the bzip2 package, here are the details: [http://people.canonical.com/~ubuntu-security/cve/2010/CVE-2010-0405.html]("http://people.canonical.com/%7Eubuntu-security/cve/2010/CVE-2010-0405.html")

If the link is obscured, you can find it by searching for CVE-2010-0405 or going to bzip2 website.

---

### Post by CharlesA on 2012-03-18
> **robinnelu said:**
> Thanks for your reply. I ran CloudPassage.com security check and bzip2 is one out of eleven software security issues it found. For the bzip2 package, here are the details: [http://people.canonical.com/~ubuntu-security/cve/2010/CVE-2010-0405.html]("http://people.canonical.com/%7Eubuntu-security/cve/2010/CVE-2010-0405.html")

If the link is obscured, you can find it by searching for CVE-2010-0405 or going to bzip2 website.
Looks like it was fixed:
[https://launchpad.net/ubuntu/lucid/+source/bzip2/+changelog](https://launchpad.net/ubuntu/lucid/+source/bzip2/+changelog)

---

### Post by robinnelu on 2012-03-19
That link is for the 1.0.5 security updates, not 1.0.6.

---

### Post by CharlesA on 2012-03-20
> **robinnelu said:**
> That link is for the 1.0.5 security updates, not 1.0.6.
The thing is the issue was fixed without having to move to the next version. The change log says it was fixed upstream, and so it was fixed in the version that Ubuntu uses.

---

### Post by robinnelu on 2012-03-20
Ok, I see how it works now. Most of these warning I see are already fixed. So as long as I keep Ubuntu updated, I should be fine. 

Thanks for the clarification and the help!

---

### Post by CharlesA on 2012-03-20
As long as you are checking the changelogs and making sure vulnerabilities are fixed, you should be good to go. :)

You can also check here (warning long, long page):
[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

---

### Post by SeijiSensei on 2012-03-20
Not all bugs are real risks, either.  The bzip2 problem concerns specially-crafted files that take advantage of an integer overflow problem.  I can't think of anyone who would try and exploit this by sending a bzip2-encoded binary in an email; only geeky folks like us use bzip2.  I suppose you could download a file from a website in the bzip2 format, but I rarely encounter these except for source code archives.  

My point is that you need to consider the likelihood that a threat really affects you and not just rely on automated system scans.

---

