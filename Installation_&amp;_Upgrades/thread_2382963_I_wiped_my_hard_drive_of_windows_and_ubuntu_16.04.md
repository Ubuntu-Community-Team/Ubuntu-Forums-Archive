---
title: "I wiped my hard drive of windows and ubuntu 16.04"
date: 2018-01-19
forum: Installation &amp; Upgrades
---

### Post by rusty377 on 2018-01-19
Now that I have a clean disk I cannot install 1710 I get a grub loader error and cannot select any other sda or sda1. Help please! Do I have to have a system of some form to load iso disk? what might I do if I am required to have an existing system to load?

---

### Post by TheFu on 2018-01-19
The ISO needs to be on some media that the computer knows how to boot. This is usually a CDROM/DVD or Flash USB drive.  The target disk cannot be in-use already.

Or am I misunderstanding the issue?

---

### Post by oldos2er on 2018-01-19
If you formatted the two OSes you had installed (assuming here) you lost part of grub which is why your system won't boot.

Please clarify your hardware specs, and the hardware's current state. (Assuming again) if you have access to another computer you can create an Ubuntu live medium from there.

---

### Post by rusty377 on 2018-01-19
I have a Dell laptop with cd-drive but it has this weird thing of a "single boot" option. I tried using the cd drom with some luck loading systen until it gets to grub insltall where it gives error message "faltl error" do you want to terminate this process or use several different boot options I don't uderstand. I go into settings for boot options and click both on hdd and cdrom, then go to f12 and select onetime cd-rom to load but it fails every time. Any ideas?

I have another computer with cdrom drive and can create media DVD. The offending machine is an older Dell bios version a4610 with cdrom drive as well.

If I even do the "try me" function it gets to the grub stage and fails anyway

[I] was able to get ubuntu back up by installing ubuntu 16.4.3? I do not know why? But back on ubuntu- wish it was 17.10 though. Is it possible to upgrade to 17.10 thru some mysterious way?

---

### Post by TheFu on 2018-01-19
It isn't a mystery.  
* sudo apt update
* sudo apt dist-upgrade
* sudo do-release-upgrade

Make a backup BEFORE doing this so the worst situation you have is restoring to 16.04.  BTW, I prefer 16.04 LTS over any 6-month-supported release.  Newer isn't always better.

---

### Post by rusty377 on 2018-01-20
THEFU

I tried your update stream but it did not update

---

### Post by TheFu on 2018-01-20
Any warnings or errors?  Can't read minds from here, sorry. ;)
What, exactly, was the step where it happened and what, exactly, was the error?

---

### Post by rusty377 on 2018-01-23
I only got fatall error....

---

### Post by sudodus on 2018-01-23
Edit: Please remember the backup as suggested by TheFu.

-o-

The following *should* work.

Older syntax,

```
sudo apt-get update
sudo apt-get dist-upgrade
sudo do-release-upgrade

```

or (newer syntax),

```
sudo apt update
sudo apt full-upgrade
sudo do-release-upgrade

```

*Please post the whole output of each of the command lines.* It will help us help you. (Otherwise we can only guess.)

-o-

Please post the output between code tags like this
 
[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

---

