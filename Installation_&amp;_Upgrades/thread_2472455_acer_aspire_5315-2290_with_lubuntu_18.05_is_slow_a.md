---
title: "acer aspire 5315-2290 with lubuntu 18.05 is slow at boot"
date: 2022-02-27
forum: Installation &amp; Upgrades
---

### Post by luis6termi on 2022-02-27
boot in 4 min but the system doesn't have a problem when start to the main menu but when trying to shut down the pc it had a lot of errors

---

### Post by luis6termi on 2022-02-27
boot in 4 min but the system doesn't have a problem when start to  the main menu but when trying to shut down the pc it had a lot of error
the machine has a proccesor intel celeron 550 2.0 ghz 533 mhz FSB, 1mb L2 cache
ram 2.5 gb 
graphics card 252 mobile intel graphi


cs media accelerator X3100

---

### Post by guiverc on 2022-02-27
Don't forget Lubuntu 18.04 LTS is *End of Life* - [https://lubuntu.me/bionic-eol/](https://lubuntu.me/bionic-eol/)

*There was no release in 2018-May ( 18.05 )* *but that was likely a typo*[I].


[/I]If your machine is *amd64* and thus capable of upgrade; don't forget 18.04 was the *end-of-the-road* with regards *upgrades*, due to the change of desktops, ie. with [20.04's release notes]("https://lubuntu.me/focal-2-released/") you'll read 

> ***Note***, due to the extensive changes required  for the shift in desktop environments, the Lubuntu team does not support  upgrading from 18.04 or below to any greater release. Doing so will  result in a broken system. If you are on 18.04 or below and would like  to upgrade, please do a fresh install.

---

### Post by guiverc on 2022-02-27
-- *merged post from duplicate thread*
-- *content removed via edit as unhelpful (duplicate)*

---

### Post by GhX6GZMB on 2022-02-27
My recommendation:
Do a fresh install to Lubuntu 20.04 LTS. Your machine supports it
Backup your /home directories first.
Unfortunately, your installed programs and settings will be lost.
I'm not aware of a method to avoid that.

---

### Post by grahammechanical on 2022-02-27
Are you sure you are seeing errors?

Linux is command line. System messages are printed to the screen. At some point video drivers are loaded and the loading of Ubuntu switches to another terminal and a graphical splash screen hides those messages. When Ubuntu shuts down it switches back to Linux running as command line on a terminal and the original system messages are revealed again until Linux itself shuts down.

Regards

---

### Post by guiverc on 2022-02-27
> **ml9104 said:**
> 
I'm not aware of a method to avoid that.

I'd suggest scanning [Testing Checklist - Understanding our testcases]("https://discourse.lubuntu.me/t/testing-checklist-understanding-the-testcases/2743") and how I describe the "*Installing using existing partition*".

I have an install of each supported release of Lubuntu I keep for *testing* & *support* purposes, for the *focal* release I don't perform anypackage upgrades, but achieve them via a re-install which accomplishes two tasks at once (*a QA-test install is performed + my packages get upgraded*). It allows up to go to a later release or even backwards (*though some applications may have side effects going backwards; rare but can be a hassle if it's data that is important*).  When 21.04 reached EOL; I used this method to *switch* it's release to *jammy*; that install also gets weekly re-installs (*my current impish used to be groovy or bionic - whatever went EOL before it* *released*). 

Key to understanding the install is the *manually installed* flag, so if end-users use commands like `apt install --reinstall`to try and fix package issues; that causes the package to be marked as *manually installed* that can complicate upgrades such as LXDE to LXQt as occurs in 18.04 to 20.04; but if any such *flags* are removed prior to re-install I'd expect a *~clean* install.

This is not a *Lubuntu supported* upgrade path; ie. the Lubuntu team doesn't support it, but in my own experience it works well; and I use it. 

It works with Ubuntu Desktop & all [*flavors*]("https://ubuntu.com/download/flavours") of Ubuntu (`ubiquity` or `calamares` installer anyway), but I don't *test/use* it with 3rd party packages.

---

### Post by CharlesA on 2022-02-27
Threads merged. @luis6termi: Please post only one thread on a topic as posting the same topic in multiple subforums can reduce the number of people who respond to it.

---

### Post by ActionParsnip on 2022-02-28
Could use Lubuntu 22.04 or install Ubuntu 22.04 server then install lxqt or lxde.

---

