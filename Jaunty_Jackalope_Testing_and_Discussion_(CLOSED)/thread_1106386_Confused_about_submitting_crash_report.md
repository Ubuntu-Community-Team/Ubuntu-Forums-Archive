---
title: "Confused about submitting crash report"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by cl333r on 2009-03-25
Hi folks,
I got latest Jaunty build and when an app crashes the tool to report the crash auto-starts, collects info and only asks me to hit "send report" - easy enough, but, the most important thing (that I have to be a registered launchpad user) is being told _after_ the tool finished uploading with words like "to complete the report go to .. login..".
So, does one have to login to the site to "complete the report"?
Is anywhere this briefly described, cause I'm confused.

---

### Post by douham on 2009-03-25
> **cl333r said:**
> Hi folks,
I got latest Jaunty build and when an app crashes the tool to report the crash auto-starts, collects info and only asks me to hit "send report" - easy enough, but, the most important thing (that I have to be a registered launchpad user) is being told _after_ the tool finished uploading with words like "to complete the report go to .. login..".
So, does one have to login to the site to "complete the report"?
Is anywhere this briefly described, cause I'm confused.

The tool that generates the crash report is called **Apport**.
The site that you need to log into is called [Launchpad.]("http://www.launchpad.net")

Nullacks  [sticky ]("http://www.ubuntuforums.org/showthread.php?t=996538") at the top of the Jaunty forum explains more.

Doug

---

### Post by cl333r on 2009-03-25
thanks

---

### Post by Polygon on 2009-03-25
yeah, create a launchpad account, and if it says you need to login after apport finishes uploading, simply login and it will take you through the steps.

However, one limitation of apport is that it does not include all the stacktrace stuff if you subscribe to a existing report, but those crash files are useful. So i always submit a new bug report so that the files get uploaded somewhere, and if its a duplicate then someone will mark it as such.

---

