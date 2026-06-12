---
title: "Unresolvable error upgrading to 14.10"
date: 2014-10-27
forum: Installation &amp; Upgrades
---

### Post by erwin11 on 2014-10-27
I have no unnecesary USB connections. And yes I am running 14.04, so the upgrade to 14.10 should go without a glitch. I tried the standard distro upgrade as suggested by the ubuntu.com site. I am running it on a Lenovo Ideapad s510p. 
However I get the following error message:

An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

However 3rd party is turned of before it runs into this part, so it can not be running unofficial programs. (Besides I turned of any and all programs, before I ran the upgrade)
So I am stuck as to what can cause the problem. When I ran upgrade, I had every other program stopped, and as fasr as I can see this is not a pre-release.

As far as I figure it can be a non supported program, causing this. However I have no clue as how to trace which one that might be.

erwin

---

### Post by Bucky Ball on 2014-10-27
*Post moved to own thread.*

Please do not hijack other users threads. It just gets confusing and is unfair to the original poster (among other things). ;)

---

### Post by grahammechanical on 2014-10-27
How did you start this upgrade process? Did you use Software Updater? Or did you run a command? If so, what was the command? This command will upgrade to a development version

```
sudo do-release-upgrade -d
```

That is not the command to use.

Let me explain the 3 reasons given for that error message.

Up until a couple of weeks ago it would have been possible to upgrade from 14.04 to the 14.10 pre-release (development) version. But since 14.10 has been released the next pre-release version is Vivid Vervet (15.04) and we cannot upgrade from 14.04 to 15.04 (development) version without first upgrading to 14.10.

If we are already running Vivid Vervet (1504) then there is no pre-release version to upgrade to.

That leaves the third reason. "Unofficial packages not provided by Ubuntu." These packages do not have to be running to cause this problem. Their very existence on the system is the problem because the upgrade scripts cannot take into account their existence and cannot work out how to upgrade those packages.

Unofficial packages are programs/applications that were not in the Ubuntu Software Centre but were downloaded from some web site and then installed. If this is the situation it is best to un-install these programs and then run the Upgrade process. And then install the 14.10 versions of those programs.

Regards.

---

### Post by helgman on 2014-10-28
[QUOTE=grahammechanical]Unofficial packages are programs/applications that were not in the Ubuntu Software Centre but were downloaded from some web site and then installed. If this is the situation it is best to un-install these programs and then run the Upgrade process. And then install the 14.10 versions of those programs.[/QUOTE]

I experience the same problem and I want to thank you for the informative answer. Still, it fails to address the main problem:

[QUOTE=erwin11]As far as I figure it can be a non supported program, causing this. However I have no clue as how to trace which one that might be.[/QUOTE]

Me neither. I have been uninstalling everything I can think of and find but I still experience the same problem. How does the upgrade tool come to the conclusion that something is wrong and is there any way to use this to find out how to resolve the problem?

Regards,
Helgman

---

### Post by ian-weisser on 2014-10-28
> **helgman said:**
> How does the upgrade tool come to the conclusion that something is wrong and is there any way to use this to find out how to resolve the problem?

grahammechanical explained how the upgrade tool discovers a problem.

Specifically in what seems to be your case, apt looks for updates to current packages. This problem often means that it cannot figure out which package (current or update) is *really* the updated version - all it knows is the version number. And some non-Ubuntu packages use nonstandard version numbering.

Example: The package manager finds package foo_1.1.3~ppa on the system, and package foo_1.1.3-ubuntu1 in the new repository. Which one should it install? There is no right answer from the data available, so the package manager throws the error and aborts to prevent breaking your system. You, the human, must decide.

That's why the non-Ubuntu software (and all of the non-Ubuntu dependencies) need to be uninstalled.

Is there any tool to tell you which non-Ubuntu software is still installed?
Not that I know of. The upgrade tool is not intended for diagnosis.
Personally, I keep a record of my non-Ubuntu software so I don't run into this problem when I upgrade to the next version of Ubuntu. It's worked for me for nine years without problem.


What to do?
You can look through /etc/apt/sources.list and /etc/apt/sources.list.d/ to see if you can recall the software that attracted you.
You can try autoremoving orphans in case the problem is a dependency (it often is).
You can decide to not upgrade to the next release of Ubuntu. 14.04 is supported until 2019.
You can accept a partial upgrade (if offered), and then try to troubleshoot and remove the problem package.
If you _really_ want to learn about the innards of your system, you can manually update the repository listing and do a manual test-upgrade to find out where the problem package is.
Or you can backup your data and reinstall.

---

### Post by helgman on 2014-10-29
> **ian-weisser said:**
> Example: The package manager finds package foo_1.1.3~ppa on the system, and package foo_1.1.3-ubuntu1 in the new repository. Which one should it install? There is no right answer from the data available, so the package manager throws the error and aborts to prevent breaking your system. You, the human, must decide. (...) The upgrade tool is not intended for diagnosis.

Good points and I definitely agree with you. The upgrade tool is not for diagnosis and I (the human user in this case) should make the decisions, not the machine (or developer). But I need information to be able to make the decision and unless the tool is unaware of why it should not continue why can it not make that information available to me? If it finds package foo_1.1.3~ppa as in your example, why not let me know that this is the offending package?

For all the upgrades I have done over the years I have never had this problem, until now ... If the upgrade tool will not tell me why it will not upgrade (apart from the three general ideas that it gladly tells me every time I try again after remove something) then I guess I will have to go through all the apt-logs since last upgrade. But not knowing what I am looking for ... it feels like a Swedish submarine hunt. The sources.list only holds the official repositories (I will have to look at /etc/apt/sources.list.d/ when I get home) and I have used autoremove a ton of times. I guess it is down to staying with what is running, doing a partial upgrade (I have to research that) or doing a re-install (something I would have gladly done five years ago but now ... not if I do not have to).

Thank you for taking the time to explain things and if you come up with anything that might help, it would be most appreciated.

Regards,
Helgman

---

### Post by Impavidus on 2014-10-29
Synaptic can list the various packages on your system sorted per source, showing the official repositories, any PPAs and stand-alone .debs (or .debs of which the repository has been disabled). I recently did some cleanup on a computer on which I am the most knowledgable maintainer but not the primary user. I found quite some leftovers from 12.04 after a recent upgrade to 14.04.

> **helgman said:**
> But not knowing what I am looking for ... it feels like a Swedish submarine hunt.Nice comparison. That submarine got half a page in dutch newspapers.

---

### Post by ian-weisser on 2014-10-29
> **helgman said:**
> If it finds package foo_1.1.3~ppa as in your example, why not let me know that this is the offending package?
It doesn't know which of the two candidates is offending. It's not that smart.

> **helgman said:**
> it feels like a Swedish submarine hunt
Most excellent analogy!
It sure does. Under the older Debian dist-upgrade method to migrate to the next release of Debian, you don't have this problem. There is no upgrade tool and you use apt directly, so you see all the errors.

You could do something similar; manually editing the repo sources and running a dist-upgrade. That would likely expose the conflict.

I think you are right that the upgrade tool is missing a feature to expose the conflict. Perhaps you might file a bug report.
There's an additional problem of converting the conflict into plain language so most users can understand it...but that seems like more of a dpkg problem than a do-release-upgrade problem. We get a _lot_ of users who don't understand dpkg errors.

---

### Post by helgman on 2014-10-29
> **Impavidus said:**
> Synaptic can list the various packages on your system sorted per source, showing the official repositories, any PPAs and stand-alone .debs (or .debs of which the repository has been disabled).

This was a great idea and it helped me track down some packages packages that are now gone. Unfortunately it did not solve the problem, still the same error message. But at least the computer feels a bit lighter now! ;-)

> **ian-weisser said:**
> Under the older Debian dist-upgrade method to migrate to the next release of Debian, you don't have this problem. There is no upgrade tool and you use apt directly, so you see all the errors. You could do something similar; manually editing the repo sources and running a dist-upgrade. That would likely expose the conflict.

How quickly you forget! After backing up all relevant data I changed the sources.list and then started the upgrade. So far so good and I am writing this from my updated system. It feels like it is a bit early to call it a success but so far so good. Only problem is that it did not expose any conflicts ... good for me* but not really helpful in locating the problem.

Big thanks to both of you for the help!


* Good for me unless something is lurking in the shadows, waiting to bite me in the ...

---

### Post by Bucky Ball on 2014-10-29
And now can we get back to the OP, erwin11 please? helgman: you should have posted a new thread rather than hijacking this one, but glad you got it fixed.

---

