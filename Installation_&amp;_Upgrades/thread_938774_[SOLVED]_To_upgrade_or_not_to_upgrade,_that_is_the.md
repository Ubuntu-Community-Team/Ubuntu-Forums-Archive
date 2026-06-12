---
title: "[SOLVED] To upgrade or not to upgrade, that is the question."
date: 2008-10-05
forum: Installation &amp; Upgrades
---

### Post by lovinglinux on 2008-10-05
Despite the fact that I already feel very comfortable (and happy) using Ubuntu Hardy Heron, I'm still a Linux newbie and I'm not familiar with the 6 month release cycles. So I'm wondering if upgrading will be a good move. Not that I have upgrade fever, but I would like to have the most stable and updated system. Since Intrepid countdown is almost finished, I think it's time to ask a few questions.

I understand that Ubuntu Hardy is a LTS version, so it will be supported for a few years. Does this applies to all applications on the official repositories? For example, gnome-voice-control repository version is broken, but people say the Intrepid package works. So, having a LTS release means that at some point the broken gnome-voice package should be fixed or I would only be able to use it if I upgrade or download the Intrepid repository package?

Despite a few minor issues, I think Hardy Heron works great for me and I am still learning and discovering cool useful stuff every day. Nevertheless, should I expect better hardware support only on newer releases or can I expect patches for the current version that could make things work better? Not that I have any issues with a specific hardware right now.

I have a separate partition for my home directory and I frequently generate a list of all applications I have installed using the following command:

```
dpkg --get-selections > ~/my-packages 
```

So if I decide to re-install Hardy I can install all applications that I currently have with a single command and since most of the configuration files are in the home directory, I can restore my stuff pretty fast and without much hassle. If I upgrade to Intrepid, can I keep my config files? Can I expect that all applications I have now will install and work if I use the file generated in the previous command?

If something goes wrong with the upgrade (clean install keeping /home), can I downgrade (clean install keeping /home) without screwing something?

If everything is working, why should I upgrade? Are there any new feature on Intrepid that is a must-have? Should I expect better performance on Intrepid?

Last question:

Does the Live CD allows to install applications without touching my current install? I don't know if this is kind of stupid to ask, since I will not actually install Ubuntu itself, but does it have some sort of temporary install directory when just using the Live CD for testing purposes?

---

### Post by pytheas22 on 2008-10-05
Ubuntu's policy on package updates is that once a release of Ubuntu comes out in stable form (as Intrepid will at the end of this month), updates to that release for the duration of its life cycle are generally limited to those that fix security vulnerabilities or major bugs.  For example, the version of OpenOffice that came with Ubuntu Gutsy (7.10, released in October 2007) was 2.3.  Although OO version 2.4 came out in April 2008, the Gutsy packages for OO in the repository will never be updated to version 2.4, because that would be a feature upgrade, not a bug or security fix.

I'm not sure what's wrong with gnome-voice-control.  If it's a problem with the package itself (it doesn't install properly or something), that would probably be fixed in the Hardy version eventually.  But if the Hardy version of gnome-voice-control lacks features that are available in more recent versions of gnome-voice-control, it will always lack those features in Hardy.

Of course, if you want a more recent version of a certain application than the repositories offer, you can always compile it from source or install it using packages from a third party (Gutsy users can install OO 2.4 using the packages on the OO website if they want, for instance).

> 
If I upgrade to Intrepid, can I keep my config files? Can I expect that all applications I have now will install and work if I use the file generated in the previous command?

Yes, this should work fine.  There might be a handful of exceptions, but most people would be able to do this with no problem.
> 
If something goes wrong with the upgrade (clean install keeping /home), can I downgrade (clean install keeping /home) without screwing something?

Yes, just reinstall Hardy, keeping your /home directory intact, and everything should be identical to what it is now.

> 
If everything is working, why should I upgrade? Are there any new feature on Intrepid that is a must-have? Should I expect better performance on Intrepid?

Sure, there will be [new features in Intrepid]("http://www.ubuntu.com/testing/intrepid/beta#New%20Features%20since%20Ubuntu%208.04").  None of them are earth-shattering, but there's cool new stuff.  You'll also get a more recent version of the Linux kernel, which will give you better hardware support (in particular, wireless support for many chipsets should be vastly improved) and may work a bit faster, etc.
> 
Does the Live CD allows to install applications without touching my current install? I don't know if this is kind of stupid to ask, since I will not actually install Ubuntu itself, but does it have some sort of temporary install directory when just using the Live CD for testing purposes?

Yes, you can install applications in the live session and run them just as you would with your normal Ubuntu system.  Any changes you make to the live session will be erased when you reboot your computer--there's no way to make the changes permanent, since everything is running in RAM--but if you just want to test out Intrepid or a few applications in it, you can boot to a live CD and install the packages you want to test in Synaptic.

---

### Post by lovinglinux on 2008-10-05
Thank you very much. Everything I need to know to make my decision.

---

