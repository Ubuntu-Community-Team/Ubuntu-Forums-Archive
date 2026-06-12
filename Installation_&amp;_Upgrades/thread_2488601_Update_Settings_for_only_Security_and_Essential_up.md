---
title: "Update Settings for only Security and Essential updates?"
date: 2023-07-10
forum: Installation &amp; Upgrades
---

### Post by rdnublx on 2023-07-10
Ubuntu 22.04 LTS
I have just received a Software Updater notification prompting to install certain updates. There are two sections displayed in the dialog window, Security updates and Other updates. It appears to match my Updates setting in Software & Updates to “Security and recommended updates”. Since my selection was to install security updates automatically, they were installed and now there are only Other updates waiting for Install confirmation.
My question is whether installing these “recommended” updates would move me off the 22.04 LTS “stable” release or baseline.
Also, second question in the same line, what is the subsection “Ubuntu base”?
Thanks

---

### Post by ian-weisser on 2023-07-10
Oversimplified: There are two types of updates: Security and Bugfixes.

You have set Security updates to automatic (that's good).
But not Bugfixes ("recommended"). There is no automatic setting for Bugfixes. You can do it, but not from the GUI.

"recommended" updates will not change your release. Whether or not they move you off "baseline" depends upon your sources.

The subsection "Ubuntu base" are elements of the operating system. Not applications. Not other add-ons.

---

### Post by rdnublx on 2023-07-10
Thank you. 
I probably misused the word &#8216;baseline&#8217;, which usually refers to source code. What I meant was 22.04 LTS release. My objective is to stay on a stable release level, which 22.04 LTS is.
if I understand you correctly, Recommended is essentially bug fixes, it&#8217;s just that there is no way to set up them to be updated automatically, unlike Security updates (which I already do).
I am a bit less clear on the &#8220;Ubuntu base&#8221; point, which actually may be not that important, if I am understanding it correctly.

---

### Post by ian-weisser on 2023-07-11
> **rdnublx said:**
>  it&#8217;s just that there is no way to set up [bugfixes] to be updated automatically, 

Sure there is.
You just cannot do it through the GUI.

1. Edit the file /etc/apt/apt.conf.d/50unattended-upgrades

2. Uncomment the line: 
```
//      "${distro_id}:${distro_codename}-updates";
```

That's all there is to it. You don't need to logout nor reboot. It just starts working.

It's not enabled by default simply because all patches introduce some small risk of breakage or reversion, some folks don't want any updates, and these are not security patches.

---

### Post by rdnublx on 2023-07-11
Understood, thank for the details, appreciate it!

---

