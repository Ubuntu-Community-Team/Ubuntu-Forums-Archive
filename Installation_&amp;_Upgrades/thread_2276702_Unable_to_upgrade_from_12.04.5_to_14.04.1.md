---
title: "Unable to upgrade from 12.04.5 to 14.04.1"
date: 2015-05-04
forum: Installation &amp; Upgrades
---

### Post by philled on 2015-05-04
I am running Ubuntu 12.04.05 (on a vmWare VM, but I don't think should matter for this) and when I log in it says:
[FONT=courier new]New release '14.04.1 LTS' available.[/FONT]
[FONT=courier new]Run 'do-release-upgrade' to upgrade to it[/FONT].

But when I run "[FONT=courier new]sudo do-release-upgrade[/FONT]" it says:
[FONT=courier new]No new release found.[/FONT]

I've found a lot of posts suggesting things like editing [FONT=courier new]/etc/update-manager/release-upgrades[/FONT], and editing [FONT=courier new]/etc/apt/sources.list[/FONT] but none of these have worked. 

I don't run X on this machine as it's a headless server so I can't use Update Manager or anything like that. So I then tried doing a CD upgrade but pulled out of that when it got to the point of partitioning because it looked like it had failed to detect an existing installation and was just going to do a clean install rather than upgrade what was there.

So...how on earth do you upgrade this thang? Surely it shouldn't be this difficult, especially when there's a command like "[FONT=courier new]do-release-upgrade" [/FONT]to do it?

---

### Post by dino99 on 2015-05-04
i'm always using the  editing /etc/apt/sources.list  way with no trouble. But first i check that no third party repo is activated, and clean the system (clean/autoclean/autoremove/orphan). then simply updating (precise > trusty in your case) and upgrading in that order: languages (gcc, python, ...), tools (apt, dpkg, ...) the meta-packages, then everything else.

That does not take more time than via the often headaches with do-release/update-manager

---

### Post by Bucky Ball on 2015-05-04
It should be showing in the Software Updater that there is a new LTS available. You can just click that. But follow the instructions in the last post re. switching off third-party repos, etc.

---

### Post by philled on 2015-05-04
> **Bucky Ball said:**
> It should be showing in the Software Updater that there is a new LTS available. You can just click that. But follow the instructions in the last post re. switching off third-party repos, etc.
I don't run X therefore there is no Software Updater with any buttons to click. This is a headless server so it needs to be done from the command line.

---

### Post by philled on 2015-05-04
> **dino99 said:**
> i'm always using the  editing /etc/apt/sources.list  way with no trouble. But first i check that no third party repo is activated, and clean the system (clean/autoclean/autoremove/orphan). then simply updating (precise > trusty in your case) and upgrading in that order: languages (gcc, python, ...), tools (apt, dpkg, ...) the meta-packages, then everything else.
Thanks for this. Though I don't quite understand what you mean by "simply updating (precise > trusty)". Do I just replace "precise" with "trusty" in sources.list?

---

### Post by dino99 on 2015-05-04
> **philled said:**
>  Do I just replace "precise" with "trusty" in sources.list?

yes, nothing else, save it then update and upgrade selecting the packages yourself as i'm doing from the terminal.
that way i can control what is happening while upgrading

---

### Post by grahammechanical on 2015-05-04
According to this wiki page we need to have update-manager-core installed. So, there are 2 commands

```
sudo apt-get install updater-manager-core
sudo do-release-upgrade
```

[https://help.ubuntu.com/community/Upgrades](https://help.ubuntu.com/community/Upgrades)

This is the command that I would use to change the repositories in sources.list

```
sudo sed -i 's/precise/trusty/g' /etc/apt/sources.list
```

It changes all the references to precise to trusty in all the URLs in sources.list

I will be using that command in a day or to to change an install of 15.04 (vivid) to the next development release with a w code name (we think).

Follow up with

```
sudo apt-get update
sudo apt-get upgrade
```

Regards.

---

