---
title: "Blacklist"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by jncocontrol on 2010-01-08
Hey, i'm trying to install Ubuntu 9.10.

I requested a Live CD via mail, So it should work fine, I've even did a disc check, and it even said it's fine.

But anyways, When i try to install Ubuntu 9.10 It always give me a "terminated with status <whatever number>" Sometimes it's 2 sometimes it 255.
But as i roam the forums i found out i could bypass it by adding this code into the installation ```
Intel_agp.blacklist=yes
```
Is there a way i can add this code to the start-up of Ubuntu so it could work fine, so that i can use ubuntu without trouble? If that makes any sense.

If anyone can help me out here, i would greatly appreciate it.

---

### Post by mikewhatever on 2010-01-08
Well, this, so called, code, needs to be added as a boot option to the boot line. To get to the boot line, hit f6 at the live cd menu, then don't choose anything and hit Esc, then type the option you want to add to the boot line right below the menu.

---

### Post by jncocontrol on 2010-01-08
> **mikewhatever said:**
> Well, this, so called, code, needs to be added as a boot option to the boot line. To get to the boot line, hit f6 at the live cd menu, then don't choose anything and hit Esc, then type the option you want to add to the boot line right below the menu.

I know that already, I already tested it out and it bypassed the "terminated with status <number>" problem was i having with it.
But i wanna know is how can add that Permanently to my boot option,
So that i maybe able to use ubuntu without the "terminated with status <number>" problem again.

Cause i did that, Installed it, Restarted computer, and WA-LAH, Terminated with status.

---

### Post by mikewhatever on 2010-01-08
Open /etc/default/grub for editing, find the following line:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and add your boot option with the final result being:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash Intel_agp.blacklist=yes"
```

save and exit, then rub <sudo update-grub>.

---

### Post by jncocontrol on 2010-01-09
> **mikewhatever said:**
> Open /etc/default/grub for editing, find the following line:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```

and add your boot option with the final result being:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash Intel_agp.blacklist=yes"
```

save and exit, then rub <sudo update-grub>.

What you mean by rub, Sorry if this sounds like a retarded question.

---

### Post by mikewhatever on 2010-01-09
> **jncocontrol said:**
> What you mean by rub, Sorry if this sounds like a retarded question.

Sorry, that was supposed to be 'run'.

---

