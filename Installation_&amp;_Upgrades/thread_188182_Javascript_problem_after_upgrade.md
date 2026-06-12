---
title: "Javascript problem after upgrade"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by nate on 2006-06-03
I upgraded from Breezy to Dapper Drake last night. Now when I try to login to my school website, Firefox fails the Javascript version check. It says Java 1.5 but Javascript 1.4, with 1.5 being required for both. On Breezy, I've never had any problems using the site.

The upgrade moved me from Firefox 1.0.x to 1.5.0.3.

Any ideas how to fix this? I'm not even sure how to go about updating Javascript. Could just this be an issue with their version check somehow? I had to reinstall Java after the upgrade for it to register with the new version of Firefox, but I have no idea how to fix the Javascript problem.

Thanks.

---

### Post by pointym5 on 2006-06-03
That doesn't make any sense.  There's no relationship between Java and Javascript.

What exactly do you see in terms of errors?

---

### Post by nate on 2006-06-03
Sorry, I shouldn't have mentioned Java. The only reason I did was because it is also a requirement for the web application.

When I login, it says "JavaScript 1.5 or higher is required for use with WebTycho. Please click Refresh/Reload for upgrade information and follow the instructions."

If I do the browser check on the login page, it says Javascript fails because 1.5 is required.

You can look at their version check by going to any WebTycho login page and clicking Check Your Browser. Try [https://usa5.tycho.ubalt.edu/sys/browserinfo.html](https://usa5.tycho.ubalt.edu/sys/browserinfo.html) or [https://tychousa7.umuc.edu/sys/browserinfo.html](https://tychousa7.umuc.edu/sys/browserinfo.html).

---

### Post by nate on 2006-06-05
Bump.

Any ideas on this? I already tried creating a new Firefox profile and tried a new user profile on the system. Konqueror passes the browser check but nothing happens when I hit the "Login" button.

I know some of this is probably because of the web application, but Breezy worked without any problems on the site, including passing the Javascript version check. It also works fine from my Slackware box at work.

---

### Post by shannon.cummins on 2006-07-21
Nate,
  I also have this issue, did you ever find a fix??

---

### Post by breakthestate on 2006-07-23
oooof, i am having the same problem with webtycho.  anybody find a fix?

---

### Post by breakthestate on 2006-07-24
quick fix found:

see [http://www.ubuntuforums.org/showthread.php?t=220311&highlight=webtycho](http://www.ubuntuforums.org/showthread.php?t=220311&highlight=webtycho)

---

### Post by cwej on 2007-12-30
After suffering this issue on and off throughout my entire Masters program (I have one course left for Spring 2008 semester), I finally found a solution that doesn't require any workarounds and delivers 100% compatability -- even with the Text formatting Editor (TFE) -- the solution is the Gnome Epiphany web browser. It can be downloaded in Ubuntu using Add/Remove in the Applications menu. I tested it, and its fast and fully functional with all WebTycho functions. 

(BTW, the solution evidently isn't new, just newly discovered on my part. My sincere thanks to the GNOME folks and the Epiphany developers! What a fast browser! Excellent job!)

---

