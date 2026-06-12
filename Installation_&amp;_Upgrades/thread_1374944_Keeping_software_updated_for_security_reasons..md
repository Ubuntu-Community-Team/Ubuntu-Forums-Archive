---
title: "Keeping software updated for security reasons."
date: 2010-01-07
forum: Installation &amp; Upgrades
---

### Post by draygen on 2010-01-07
Hi Everyone,

 I've recently built a VM appliance using Ubuntu 8.04 that is given to customers for an easy deployment of our software. Ubuntu works great in a VM and its perfect for our software (which is a web application).

Some customers are paranoid (rightfully so) and they will run a vulnerability assessment on the web application. A particular customers' assessment fails as it finds that the appliance isn't running the latest version the Apache web server. I thought that just running "apt-get upgrade" would upgrade all of the software packages to the latest so that failures in the assessment caused by outdated software packages would be resolved... However this is not the case...

I realize that there is a probably a whole process for submitting/approving the latest versions of software packages in Ubuntu, that then get pushed to the repositories - But how does this work? What exactly does "apt-get upgrade" do if it doesnt upgrade packages to the latest?

For example: I need Apache 2.2.11 to fix a particular vulnerability. But when running apt-get upgrade, it doesnt actually upgrade the Apache version number (or any of the other packages). I'm stuck on Apache 2.2.8, and I can't find a .DEB installer for 2.2.11 or later. I did post on the Apache forums but havent heard anything.

Any pointers/tips would be greatly appreciated!!! 

 Thanks,

draygen

---

### Post by snowpine on 2010-01-07
Ubuntu 8.04 = April 2008. If your customers need more recent application versions, I recommend a newer version of Ubuntu (9.10 is the current as of October 2009).

You should however be able to get the latest Apache from [http://www.apache.org/](http://www.apache.org/) . My point is that, if your clients demand the latest applications, a 20-month-old release is a poor choice.

---

### Post by slakkie on 2010-01-07
Have a look at the changelog to see if your bug is fixed:
[http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.2.8-1ubuntu0.14/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.2.8-1ubuntu0.14/changelog)

---

### Post by draygen on 2010-01-07
Snowpine - Thanks for the reply!

It's not that they need the latest and greatest, but they do need vulnerability patches. Just because 8.04 is from April 2008, shouldn't mean that vulnerability patches wouldn't apply.

The reasons I went with Ubuntu 8.04 is because it is on LTS (Long Term Support) and 9.10 isn't yet... Also 9.10 is not yet officially supported with the VMWare Studio appliance I use to build the appliance 

From my understanding LTS means:

- Enterprise Focused
- Most Tested

The above are very important when deploying a production server in an enterprise.

So I guess specific versions of software are tied to the release version of Ubuntu.. Which means , if I have Ubuntu 8.04, which say for instance comes with Apache 2.2.9 ...  whenever I run 'apt-get upgrade', it wont really upgrade Apache 2.2.9 to the latest version of Apache (?).

 Thanks,

draygen

---

### Post by draygen on 2010-01-07
Thanks! This is exactly what I needed. The specific vulnerabilities are patched , but the version of Apache2 isnt upgraded, which is just fine in my opinion.

I have a feeling the particular vulnerability scanner the customer is using doesnt truly scan for a vulnerability - it just grabs the Apache version and assumes its affected by a flaw in that version.

> **slakkie said:**
> Have a look at the changelog to see if your bug is fixed:
[http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.2.8-1ubuntu0.14/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/a/apache2/apache2_2.2.8-1ubuntu0.14/changelog)

---

### Post by snowpine on 2010-01-07
> **draygen said:**
> So I guess specific versions of software are tied to the release version of Ubuntu.. Which means , if I have Ubuntu 8.04, which say for instance comes with Apache 2.2.9 ...  whenever I run 'apt-get upgrade', it wont really upgrade Apache 2.2.9 to the latest version of Apache (?).

Correct.

Slakkie has good advice, too. The "Ubuntu Way" is to security patch the stable version of the app, rather than upgrade to a newer version.

---

