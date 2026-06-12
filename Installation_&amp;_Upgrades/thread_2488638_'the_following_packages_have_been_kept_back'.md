---
title: "'the following packages have been kept back'"
date: 2023-07-11
forum: Installation &amp; Upgrades
---

### Post by martago on 2023-07-11
This "informative" message is occurring recently every time I run apt update, it happened very rarely in former times.  I do have many computers, most of them with xubuntu, and this message is a nuisance I hope someone find a way to avoid it.  I have read in itsfoss that one should ignore this message because a few hours or days later, ubuntu will update the software listed under the message "the following packages have been kept back".  If this is the case, why bother the user with a list of software that will be updated later but in that moment it is not possible?  This is something I cannot imagine the reason for such behavior other than nag the user.

---

### Post by ian-weisser on 2023-07-11
> **martago said:**
> this message is a nuisance I hope someone find a way to avoid it.
  
Sometimes it can be avoided (self-inflicted version conflicts), sometime it cannot (phased updates).


> **martago said:**
> I have read in itsfoss that one should ignore this message because a few hours or days later, ubuntu will update the software listed under the message "the following packages have been kept back".

itsfoss is sometimes a dubious source. Sometimes it's accurate. Sometimes it's not.

In the first case (self-inflicted version conflicts) the message should NOT be ignored.
In the second case (phased updates) the message will indeed go away on its own in a week or so.

It's very easy to tell which is which by using "apt policy <package_name>"


> **martago said:**
> This is something I cannot imagine the reason for such behavior other than nag the user.

You don't need to imagine anything. See [https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345/](https://discourse.ubuntu.com/t/phased-updates-in-apt-in-21-04/20345/) for the whole story.
If, after that, you still feel aggrieved enough to tell folks how you feel, chime in on that topic and let the developers know.

---

### Post by TheFu on 2023-07-11
When a package is kept back, that can mean a few different things.  

Depending on the held package(s), this could be a trivial thing or a huge, bad, security, fail.  Only a human can know the difference, so that's why the message is displayed.  With many APT issues, my standard response is to wait a few days and see if it self-corrects.  Sometimes packages made by humans have incorrect dependency information or some of those dependent packages don't get released before the one that appears to be causing the issue.  Over the decades I've been a Linux Admin, I've found that patching weekly, only on weekends, let's me avoid many of these types of dependency problems.

People that patch daily are alpha testers. Thank you for your service. I'm old enough not to want that anymore. I did my time in the 1990s.

Often it is due to a .deb file being manually installed and locking the current dependencies.  The solution for this situation is to remove the .deb package, perform system updates and then look for a newer version of the .deb package which is compatible with the new libraries installed.  Whenever someone goes outside the core Ubuntu Repos for software, they risk causing dependency issues.  It doesn't always happen, but it happens often enough that I keep a list of manually installed .deb files so when it happens in 3-6 months, I know exactly which packages need to be removed so I can patch my systems.

I'll let other people address other possible causes.

---

### Post by martago on 2023-07-12
Thank you guys for your helpful information, I am now fully informed about this feature and how to overcome it if I want to.

---

