---
title: "Does do-release-upgrade upgrade Budgie 20.04 to Budgie 22.04?"
date: 2024-01-24
forum: Installation &amp; Upgrades
---

### Post by dorasmith24 on 2024-01-24
I am installing Ubuntu Budgie 22.04 on my laptop, by installing Ubuntu Budgie 20.04 and upgrading to 22.04.   Evidently the developers mangled the install process so that if you directly install Ubuntu 22.04 on an older system first it wants a UFI partition on systems that don't use UEFI, then whether you create one or not you can't boot your system until you jump through five million incomprehensible hoops.   Do. NOT. Even. Think about it.  Someone suggested the install older version and upgrade work around, which is STUPID but it worked.  Atleast with the ubuntu desktop.   (Does everyone with an older computer have to install an older version of Ubuntu and upgrade it until time ends?   Won't be helpful for getting people to use Linux, they want to click install and go.)

I did the same thing with Ubuntu 22.04 last night on my desktop, and ran into many of the same set of things.

On both, soon after I rebooted after installing the 20.04 version, I got a popup telling me to click here if I want to install the upgrade to the latest version, 22.04, and I clicked to install it - and both times, it DIDN'T install it. I could not wait until whenever, maybe in days, or next week, or next month, when the software updater finally deigns to present the option to upgrade again.   

The reason for all of this is to find out if it increases my connection speed, the speed at my end of the ethernet cable being what it is at the modem, whcih is what it's supposed to be - because a work from home job I am applying for requires a screenshot showing I can get the required upload speed before my application will be considered.  The point of a production computer is production, NOT lengthy experiments in whatever.   Solutions to problems need to be quick and efficient, and problems need to get straightforward answers and not incomprehensibility.

   I'm installing Budgie on my laptop, though I use the Ubuntu desktop extensively reworked to my preference, on my desktop, because I don't use my laptop much, only for unusual occasions like library research and hospital stays.   But I need to know if the slightly newer and faster computer, or even just a different computer, can get better upload speed - after updating the kernel and everything.  If I'm in the hospital, I don't want to look at that ugly Ubuntu desktop, and I don't want to spend time reworking it.  Budgie looks close to what I want out of the box.  

 Then I installed Synaptic, debi and Chrome, With the Ubuntu desktop I then ran updates, opened the required port, and ran do-release-upgrade. Last night, that got me beautifully into Ubuntu 22.04.3., and, since the reason for all of this is to find out if it increases my connection speed, the speed at my end of the ethernet cable being what it is at the modem, whcih is what it's supposed to be, I then used Synaptic to install the Linux 6.1 kernel.  The ethernet driver my system needs is incorporated into the kernel, so if I need to update it, and it was hopelessly out of date in 20.04, I need a recent kernel. Or I could have followed a very long and windy and equally incomprehensible method to just install the updated driver. 

When after running updates I went to the software center and made sure it had install new versions when available, it didn't do that.   I needed it to upgrade immediately and not whenever. 

So now I'm doing exactly the same thing in Ubuntu Budgie.  I am in the middle of running the upgrade to Budgie 22.04.   Only I'm not sure if it is upgrading to Budgie or just to the Ubuntu desktop, becasuse the stuff flying by in Terminal mentions Jellyfish constantly but never once mentions Budgie?  It mentions Lubuntu a lot, too, which could logically have been used to create Budgie. 

If I have to reinstall and try again, how will I get it to upgrade to Budgie 22.04?

---

### Post by dorasmith24 on 2024-01-24
It upgraded to Budgie. Or I'm looking at the Budgie desktop.  Thank you, Jesus!   It would have been nice if it said it was upgrading to Budgie.

---

### Post by Tadaen_Sylvermane on 2024-01-24
Stuff like that won't tell you what version you have installed. It will default to something simple for any distro unless someone specifically modifies it. If you are using an official Ubuntu spin of Budgie then in this case as far as the tool is concerned it's Ubuntu. Even many non official derivatives of Ubuntu say this on upgrade. The only thing that changes between spins is what packages get installed. This is automatic because it supposedly only should upgrade what is installed and not dump a bunch of new stuff into the system.

---

