---
title: "Trouble updating ubuntu 14.04 LTS"
date: 2016-09-12
forum: Installation &amp; Upgrades
---

### Post by ines-k on 2016-09-12
Hi,

I recently wanted to prepare myself for the upgrade to ubuntu 16.04 LTS from my ubuntu 14.04 LTS but encountered problems with updating my current version. I just can't get past the updates step for some reason. I have attached (see pics) the results I am getting when I try to run the updates. Any guesses on how to solve this?

Many thanks in advance for the help,
Inês

---

### Post by ian-weisser on 2016-09-12
DO NOT run a 'Partial Upgrade'. It may (or may not) cause big problems later.

Return your Ubuntu system to as near stock condition as possible:
1) Uninstall ALL software that come from non-Ubuntu sources.
2) Then delete your package cache ('sudo apt clean')

Open a terminal and install all Ubuntu updates before release-upgrading:
3) sudo apt update
4) sudo apt upgrade

If you get ANY error messages, then please copy-and-paste the complete output here.
If you don't get any error messages, then try the release upgrade again.

---

### Post by ines-k on 2016-09-12
Hi,

Many thanks for your reply!  Back when I was still trying to run the updates I did hit the "partial upgrade" option as it was the recommended one but it wouldn't perform as it said "Required depends are not installed" (posted a picture of it in my first post). 

How do I get started with uninstalling all software that comes from non-Ubuntu servers? Is there a way of seeing all of it?

---

### Post by ian-weisser on 2016-09-12
> **ines-k said:**
> How do I get started with uninstalling all software that comes from non-Ubuntu servers? Is there a way of seeing all of it?

Look in your System Settings --> Software and Updates --> Other Software Tab.
Those are your non-Ubuntu sources. If one says 'Canonical Partners', ignore it and focus on the rest of the list.
Rack your memory. Why did you install that source? What application(s)were you trying to update or install?
THAT is what you need to uninstall.

Uninstall using Software Center or apt or any other package manager front-end. Any should work to uninstall.

---

### Post by ines-k on 2016-09-14
Hi,

Thanks for your reply! To the question of what was I installing or updating the answer is nothing that the software updater didn't ask me to. I simply chose to proceed with the updates the software updater prompted me with which included code from non-Ubuntu sources.

I have removed all of these non-Ubuntu sources in the "Other Software tab" (leaving only Canonical Partners) yet still running into problems as when I try to run an update via the software updater it still tells me that not all updates can be installed and prompts me with running a partial upgrade or continuing.

---

### Post by ines-k on 2016-09-14
Also, at the moment I lost access to my laptop as when I restarted it after deleting non-Ubuntu software and uninstalled Opera and Dropbox, the system now displays a console log with "Kernel panic - not syncing: Attempted to kill init! Exitcode..."

---

