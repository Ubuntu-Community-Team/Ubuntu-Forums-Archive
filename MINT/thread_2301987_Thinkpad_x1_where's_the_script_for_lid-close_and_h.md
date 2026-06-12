---
title: "Thinkpad x1: where's the script for lid-close and hibernate?"
date: 2015-11-06
forum: MINT
---

### Post by hearts2 on 2015-11-06
Hi all,  I have a thinkpad W510 (old), when I close the lid, it won't hibernate.  So I went into /etc/acpi, and found that there's no code for lid close (although in power settings panel, I did set).  So I added code in /etc/acpi/events, and /etc/acpi to support lid close->pm_suspend  It worked like a charm.   Now I have another thinkpad X1 (quite new), when I close the lid, it will hibernate. When I open the lid, it will wake up, but 5 out of 10 times, the wakeup will cause video driver to glitch, the graphics (browsers, console printing etc.) will become slow. The only way to solve it is to logout, and login again (but my work will be gone and I have to restart all windows). This is very annoying.  Now I go to /etc/acpi and try to find what happened. But to my surprise, there's no code regarding lid close->pm_suspend in /etc/acpi (just the same as thinkpad w510).  I think they must be somewhere else.  I tried to manually type "sudo pm_suspend", and there's no problem for thinkpad x1! It means the default lenovo driver somewhere, massed up the graphics driver.  May I know where is the lenovo thinkpad driver script for lid close and hibernate support?   Thanks.

---

### Post by matt_symes on 2015-11-06
Hi

What version of Ubuntu are you using ?

pm-utils was dropped when systemd was introduced and systemd now handles hibernation.

Kind regards

---

### Post by hearts2 on 2015-11-07
> **matt_symes said:**
> Hi

What version of Ubuntu are you using ?

pm-utils was dropped when systemd was introduced and systemd now handles hibernation.

Kind regards


Hi, thanks for answering.

I tried to type systemctl (from systemd ArchWiki helps), it seems that there's no systemctl installed.

I am sorry that I probably shouldn't ask here but I thought Mint is same as Ubuntu and this forum is more active.

I am using latest mint with the following information.

> lsb_release -a
No LSB modules are available.
Distributor ID:	LinuxMint
Description:	Linux Mint 17.2 Rafaela
Release:	17.2
Codename:	rafaela

---

### Post by matt_symes on 2015-11-07
Hi

I'm downloading it now to take a look. I've been meaning to do this for a while.

When i've downloaded it, i'll install it to a VM and see if i can find out what's going on with hibernation for you.

Kind regards

---

### Post by kurt18947 on 2015-11-07
I don't have a Mint install right now but isn't there a power app of some sort where you can choose what happens (suspend,hibernate, backlight off etc.)when you close the lid? I'm thinking that might be more tailored for Mint that a solution for another distro.

---

### Post by howefield on 2015-11-07
> **hearts2 said:**
> I am sorry that I probably shouldn't ask here but I thought Mint is same as Ubuntu and this forum is more active.

Course you can, in this sub forum specifically for MINT questions.

Thread moved.

---

