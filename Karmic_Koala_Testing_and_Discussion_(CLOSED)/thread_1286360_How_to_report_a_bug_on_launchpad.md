---
title: "How to report a bug on launchpad?"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mosestruong on 2009-10-08
I can't seem to find the Report a Bug link on the launchpad site at [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

Could anyone please point me to the right place thanks.

---

### Post by kansasnoob on 2009-10-08
[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by mosestruong on 2009-10-08
Finally found it on a wiki page, the URL is [https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)

It would be nice to have a link from launchpad though...

---

### Post by kklimonda on 2009-10-08
> **mosestruong said:**
> Finally found it on a wiki page, the URL is [https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)

It would be nice to have a link from launchpad though...

Well, the link was disabled on purpose and the ?no-redirect parameter should be used only for special cases.

---

### Post by 23meg on 2009-10-08
Please report bugs with ```
ubuntu-bug package_name
``` whenever possible.

---

### Post by nanog on 2009-10-09
Package name musical chairs has become truly maddening. It seems like a significant fraction of Ubuntu packages change their names each release. Moreover, the instructions for finding packages on the wiki are confusing and overly complicated.

For example:

      ```
dpkg -S /usr/bin/gnome-display-properties
```

...but there is no "gnome-display-properties" package.

---

### Post by FuturePilot on 2009-10-09
> **nanog said:**
> Package name musical chairs has become truly maddening. It seems like a significant fraction of Ubuntu packages change their names each release. Moreover, the instructions for finding packages on the wiki are confusing and overly complicated.

For example:

      ```
dpkg -S /usr/bin/gnome-display-properties
```

...but there is no "gnome-display-properties" package.

That command will tell you what package it is in.

```
$ dpkg -S /usr/bin/gnome-display-properties
**gnome-control-center**: /usr/bin/gnome-display-properties
```

---

### Post by mosestruong on 2009-10-09
> **23meg said:**
> Please report bugs with ```
ubuntu-bug package_name
``` whenever possible.

Here, we have to access the internet through a proxy. Does ubuntu-bug work behind a proxy server or is it like apport?

---

### Post by slakkie on 2009-10-09
> **kklimonda said:**
> Well, the link was disabled on purpose and the ?no-redirect parameter should be used only for special cases.

Yeah, and people are annoyed by that behaviour: [https://bugs.launchpad.net/bugs/432324](https://bugs.launchpad.net/bugs/432324)

It is remarkably irritating when you want to report a bug when you are not running Ubuntu for whatever reason.

---

### Post by slakkie on 2009-10-09
> **mosestruong said:**
> Here, we have to access the internet through a proxy. Does ubuntu-bug work behind a proxy server or is it like apport?

ubuntu-bug is apport :)

dpkg -S $(which ubuntu-bug)

---

### Post by hanzomon4 on 2009-10-09
I understand what they're trying to do but package names in Ubuntu don't always match. What if you can't boot into Ubuntu? I like they're push but they should include an option for these special cases that's clearly on the website.

---

### Post by mgol on 2009-10-11
I think that especially if browser's UA points out that a user is using Windows at the moment, launchpad shouldn't hide the "report bug" button - what if they just can't boot into their Ubuntu and they only do have Windows installed aside?

I also agree with hanzomon4 in what he says.

---

### Post by 23meg on 2009-10-11
> **hanzomon4 said:**
> I understand what they're trying to do but package names in Ubuntu don't always match. What if you can't boot into Ubuntu? I like they're push but they should include an option for these special cases that's clearly on the website.

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) includes information on what should be done in both of those cases.

---

### Post by philinux on 2009-10-11
+1 23meg.

ubuntu-bug is the best way as it collects system info, but if you dont know the package then go here.
[https://help.ubuntu.com/community/Re...0Launchpad.net](https://help.ubuntu.com/community/Re...0Launchpad.net)
then this link
[https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect](https://bugs.launchpad.net/ubuntu/+filebug/?no-redirect)

Too many bugs had not enough info. I agree with the new way.

---

### Post by mosestruong on 2009-10-27
I agree with the new way too - but I think they really ought to make it workable with proxy for people who have to work behind a firewall... or does that take a lot of work to implement? because there are a few new default programs that don't support proxies like empathy and ubuntuone...

---

