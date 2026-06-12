---
title: "Apache 2.2.20 on 10.04?"
date: 2012-11-14
forum: Installation &amp; Upgrades
---

### Post by dpouliot on 2012-11-14
Our vendor that runs the vulnerability scans just failed my server:

[http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2011-3192]("http://web.nvd.nist.gov/view/vuln/detail?vulnId=CVE-2011-3192")

 according to them I need to upgrade to 2.2.20 ( currently, 2.2.14).

```
apt-get install -s apache2
```

says

```
apache2 is already the newest version.
```

I understand I should not deviate from package managers as they do a lot of testing to ensure that latest versions do not cause problems. I also understand that my Apache version number may not indicate additional patches that have been installed. I'll run another scan tonight, perhaps I updated my Apache since the failure and didn't pay close enough attention (since the version number doesn't change, that throws me).

Assuming it fails again, what are my options? I would rather not deviate from the package managers. Are there any devs here who can give me an idea when a newer version of Apache will become available to 10.04?

---

### Post by drmrgd on 2012-11-14
This is an Ion Torrent server I take it ;)

We had the same problem with ours and actually did patch Apache2 v20 from a different repo.  That causes all kinds of havoc and we needed to reimage it.  So, I would be very cautious about that approach.

I'm told (and this could be complete bunk!) that the security patches that are rolled out take care of vulnerabilities beyond the version numbers (I don't understand exactly how that works), and if one tests for the known exploits in v14 rather than just on version number they'll find it is secure.  

If this is what I think it is, we should all come up with a plan to get these things secure, because all of use are having this problem and I think is going to really interfer with out work moving forward.

---

### Post by dpouliot on 2012-11-14
it is lucid amazon ami by alestic
ami-2cc83145

[http://alestic.com/]("http://alestic.com/")

---

### Post by drmrgd on 2012-11-14
Ahh...seems like it's the same problem but different circumstances.  Funny, though.  I got the same answer you did from a different vendor.  Maybe there is something to the security patches not always being reflected in the version numbers.

---

### Post by dpouliot on 2012-11-15
I cross-posted here:
[https://groups.google.com/forum/?fromgroups=#!topic/ec2ubuntu/3m6Mob2ILNk]("https://groups.google.com/forum/?fromgroups=#!topic/ec2ubuntu/3m6Mob2ILNk")

---

