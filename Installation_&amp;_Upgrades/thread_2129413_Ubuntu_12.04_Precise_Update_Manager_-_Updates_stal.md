---
title: "Ubuntu 12.04 Precise Update Manager - Updates stalling / Hanging during installation"
date: 2013-03-26
forum: Installation &amp; Upgrades
---

### Post by GRMoreton on 2013-03-26
Hi

Sorry if this issue is a common one and it has been posted before, I did a search of the forums however couldent find anything on this particular issue.

I have a Webserver built on a Ubuntu 12.04 (Precise)  32bit platform. Version - Kernel Linux 3.2.0-39-generic-pae / gnome 3.4.2

Output when trying to perform an update using apt-get update / apt-get upgrade

Get:1 Changelog for libruby1.8 ([http://changelogs.ubuntu.com/changelogs/pool/main/r/ruby1.8/ruby1.8_1.8.7.352-2ubuntu1.2/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/r/ruby1.8/ruby1.8_1.8.7.352-2ubuntu1.2/changelog)) [86.3 kB]
ruby1.8 (1.8.7.352-2ubuntu1.2) precise-security; urgency=low

  * SECURITY UPDATE: REXML entity expansion DoS
    - debian/patches/CVE-2013-1821.patch: set an expansion limit in
      lib/rexml/document.rb, lib/rexml/text.rb, added test to
      test/rexml/test_document.rb.
    - Patch taken from Debian's 1.8.7.358-7
    - CVE-2013-1821

 -- Marc Deslauriers <marc.deslauriers@ubuntu.com>  Fri, 22 Mar 2013 14:52:43 -0400

Output when using the Update Manager (I realise the files in both outputs are different. this is because the captures were taken at different times

[ATTACH=CONFIG]240573[/ATTACH]

I only seem to have this problem after installing ISPConfig3 (which is working great by the way) 
Can anyone please help me identify the cause of this issue as I have tried to backtrack on what I may hae done to cause this however cannot find a reason.. Potentially it could be something relating to the pre-install requirements of installing ISPConfig 3

Is this a known issue seen by anyone else?
Any help would be appreciated.
GRMoreton

---

### Post by schragge on 2013-03-26
I don't see any errors. The messages you're seeing probably come from [apt-listchanges](http://manpages.ubuntu.com/manpages/precise/en/man1/apt-listchanges.1.html).

---

### Post by GRMoreton on 2013-03-26
Hi [U][URL="http://ubuntuforums.org/member.php?u=1783515"][COLOR=#000000]schrage 

Thanks for the reply

Are you saying that there is not a problem with the update Manager, as when i perform an update using the normal method the update manager program just hangs and freezes / crashes.. how can i resolve this .

As mentioned apt-get update runs fine but them apt-get upgrade simply hangs also just at the same point at the update Manager?
[/COLOR][/URL][/U]

---

### Post by schragge on 2013-03-26
It doesn't hang. It waits for you reading the changelog and pressing **q** afterwards. If you don't want this behaviour, configure apt-listchanges accordingly.

---

### Post by GRMoreton on 2013-03-26
Ahhhh I was missing the point you were making. apologies. I dont understand why it has just started doing this though, possibly something i did during my preconfig work before installing ISPconfig 3... Many thanks for your help. :)

---

