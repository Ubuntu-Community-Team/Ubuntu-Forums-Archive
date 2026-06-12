---
title: "systemd, synaptic, local or obsolete temporarily"
date: 2022-06-27
forum: Installation &amp; Upgrades
---

### Post by Claus7 on 2022-06-27
Hello,

for the last couple of days, while checking synaptic package manager under ubuntu 22.04, I noticed that systemd and some other relevant libraries were in the local or obsolete section. This ended today with the latest updates, which removed systemd from obsolete files, as a result if this happens to your system just ignore it and do not remove these libraries, yet just wait for them to go back to normal.

Regards!

---

### Post by mIk3_08 on 2022-06-27
> **Claus7 said:**
> Hello,
for the last couple of days, while checking synaptic package manager under ubuntu 22.04, I noticed that systemd and some other relevant libraries were in the local or obsolete section. This ended today with the latest updates, which removed systemd from obsolete files, as a result if this happens to your system just ignore it and do not remove this libraries, yet just wait for them to go back to normal.
Regards!
Thanks a lot for this information. This may help a lot. Regards and cheers.

---

### Post by TheFu on 2022-06-27
Patching too often is a risk.  Certainly, don't patch daily.  Once a week or 2x a month is a reasonable compromise, methinks.  Of course, there are specific attacks which might require immediate patching for high risk systems, but most desktop users don't need to worry about those if they have a patched WAN router.

"New" is the enemy of "stable."

---

### Post by mIk3_08 on 2022-06-28
> **TheFu said:**
> "New" is the enemy of "stable." Amen! I strongly agree. New and Shiny doesn't mean that it is Good. :-) Thanks a lot TheFu. Regards and cheers.

---

### Post by Claus7 on 2022-06-28
Hello,

> **mIk3_08 said:**
> Thanks a lot for this information. This may help a lot. Regards and cheers.
Glad this sounds helpful.

> **TheFu said:**
> Patching too often is a risk.  Certainly, don't patch daily.  Once a week or 2x a month is a reasonable compromise, methinks.  Of course, there are specific attacks which might require immediate patching for high risk systems, but most desktop users don't need to worry about those if they have a patched WAN router.

"New" is the enemy of "stable."

if by patching you mean: checking for updates/upgrades < week, then I should mention that I have never seen such a thing before (at least concerning libraries that are system important), yet only in development versions, which seems normal in those cases. I didn't know that I should check my system less frequently in case this happens, yet good to know. 

Regards!

---

### Post by TheFu on 2022-06-28
> **Claus7 said:**
>  

if by patching you mean: checking for updates/upgrades < week, then I should mention that I have never seen such a thing before (at least concerning libraries that are system important), yet only in development versions, which seems normal in those cases. I didn't know that I should check my system less frequently in case this happens, yet good to know. 

Every day there are packages which get updated.  Sometimes, those updates aren't correct and need reworking.  By waiting until a weekend to patch, we've 
a) avoided bad packages that **will** be released.  
b) allowed other people to be impacted and report package/program issues.
c) kept a stable system for the work-week, when we all have less time to troubleshoot.
d) installing patches on the weekend is when we usually don't really **need** the computer to earn money or make out living.  Having a few hours to figure out new issues is easier on weekends.

Of course, if you are patching your enterprise computer, you might want to patch on a Monday morning?  I'm paid for results, not for wasting time during the week. My clients don't want to hear excuses, but I'm owner of the company and don't want anyone wasting time over something that can be avoided.

OTOH, we do need to patch often enough to limit risks to a reasonable level. I've had to patch some servers that were under active internet attacks a few times in the last 20 yrs.  I patched only the single server which would be impacted and only with the specific update that could cause problems. I did not patch desktops early at all.  

Security is all about risk management.

1) Have excellent, daily, automatic, versioned, backups that you can 100% restore, if necessary.  This also provides a way to see what has changed from day to day when troubleshooting issues or attacks.

2) Patch based on risks.  Systems directly connected to the internet, are higher risk. Systems running a system firewall AND behind a network firewall AND without running any high-risk daemons, just don't need to be patched so often.

3) Any change to a system is a risk.  That includes patching and OS migrations to new releases. We need to be cognizant of these risks, but not get trapped into the false risk mode.  Humans are much more likely to be struck by lightning than die in an air crash.  But we're 10,000x more likely to die from heart disease.  Basically, we shouldn't really worry about air travel and should only worry about lightning if we hear thunder.  But every day, we should worry about heart disease and certain forms of cancer.  Pay attention to the risks and worry about the most likely things.  Basically, nobody should worry about dying from a shark.

There don't appear to be any statistically valid articles about desktop computer failures. I'd hoped to list the causes, in order, like how we can get govt statistics on mortality causes.  So sad.  I think there are 4 major groups of failures.
* user error
* configuration error
* software error
* hardware error

We can control all of those, to some degree.  Buy better hardware.  

Avoid "new" software. Only time can prove that software is fit for any use, not claims by any company.  Ubuntu's LTS method will drastically reduce the "new" issues, since only security or critical bugs should be corrected post-release. That's the theory, but Canonical also makes it possible to perform some high risk actions for the sake of "new" when it isn't needed.  Things like HWE updates for kernels and GPU drivers.  If your system is working well with the current, supported, kernel line and the current GPU drivers are working, why change?  There's 1 valid reason - security. And that only matters if there is an attack of which the system is susceptible.  If you have desktop that never leaves your home, then only remote attacks matter. Local attacks don't matter at all, unless you leave the door open and invite people inside to try cracking your desktop.  But if you have a laptop and leave it unattended in a cafe for 30 seconds, then you definitely do need to be concerned by local attacks.  Some random person can insert a USB flash drive with special drivers on it and completely pwn the system for ever - at least until you wipe the OS and start over.  The physical aspect of this attack takes less than 15 seconds.  There is a mitigation - don't allow storage to be accessed without explicit permission by you.  Sure, that's inconvenient, but sometimes security is inconvenient.

User error where we visit dangerous parts of the web or open email attachments, or download, then install software from suspect locations.  Or thinking that antivirus software works better than it does (the best A/V software is 50% effective). Knowing that, you've be much more cautious online, right?  Of course, A/V on Linux isn't really a thing, since those tools generally look for virus signatures for other OSes.  

I suppose configuration errors can be considered user errors, but nobody can possibly know all the configuration options for all the software on their systems. Nobody.

---

### Post by Claus7 on 2022-06-28
Hello,

> **TheFu said:**
> ... Of course, A/V on Linux isn't really a thing, since those tools generally look for virus signatures for other OSes.  ...

your answer is very informative, yet, if you please, I will stick to those quoted lines, since I had some discussion, not many months ago, about this exact issue. I didn't know or ...I should say I had a very long time to year that, and even if I had heard it, it wasn't so clearly stated as above.

By the way I had some unknown words: govt->government I suppose.

As a general response to what you wrote is that yes indeed, keeping updates to happen less often, unless there is a serious security issue is something new to me. From your experience, which is much much greater than mine, it explains what had happened, yet, as I mentioned, this is the first time that such thing happens to any of my systems, after the official release of an ubuntu version. I'm not accusing it, just mentioning it, and I have to tell you that initially I thought that this was a general procedure of reforming ubuntu: with the advent of gnome 30+ versions many changes have taken place: loosing desktop icons, getting them back, loosing copy paste functionality from desktop to other folders, loosing sharing screen with some applications: daily things. Luckily, with synaptic, anyone can see easily that if a package is about to get removed, which packages will be affected as well, so someone can be cautious before attempting such an action. 

edit: now should I open a new thread or should I mention here that some moment ago (only) the package ubuntu-advantage-tool behaves exactly the same? Do you face such an issue?

Regards!

---

### Post by TheFu on 2022-06-28
> **Claus7 said:**
>  Luckily, with synaptic, anyone can see easily that if a package is about to get removed, which packages will be affected as well, so someone can be cautious before attempting such an action. 

edit: now should I open a new thread or should I mention here that some moment ago (only) the package ubuntu-advantage-tool behaves exactly the same? Do you face such an issue?

The solution for many issues is to have excellent, versioned, backups and know how to restore them fully or selectively.

I've never used ubuntu-advantage-tool. There are some things I don't trust Canonical with.  For example, I'll never have a landscape account and I won't ever deploy using Ubuntu Core IoT images because they can be abused for anti-privacy things. Everyone needs to make their own choices in those things based on their comfort levels.  I don't use Ubuntu time servers either.  Lots of little tweaks like that are part of my normal setup, many avoided completely by running the most common services locally.

---

### Post by Claus7 on 2022-06-29
Hello,

> **TheFu said:**
> ...

I've never used ubuntu-advantage-tool. ...

I found out that it is part of my system for the last 4 years or so, at least this is what is reported from synaptic. One of the dependants is ubuntu-advantage-pro, which is not installed in my system.

One other thing is the ~ symbol in its version name: 27.8~22.04.1: I guess that it might be something like a transition package for the point release of ubuntu jummy. I cannot uninstall it since other packages will be affected as well. JFYI.

edit: ditto today with latest updates

Regards!

---

