---
title: "GDM Taking Long Time to Come Up After Updates"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by m4r4g4t0 on 2010-03-26
I have just made a clean install of Ubuntu 9.10 and after installing all updates, GDM is taking a long time (about one minute) to come up after a clean boot, resulting in a regular console prompt.

If I issue "sudo service gdm start" it does come up promptly.

What can I do? Where can I see startup logs to try and identify any problems?

Thanks!

---

### Post by khelben1979 on 2010-03-26
/var/log/gdm is a place to start looking.

---

### Post by m4r4g4t0 on 2010-03-26
I couldn't find anything unusual in those. I'm starting to think it's not GDM, since it starts manually. I think something that is started before GDM is taking longer to start (or give up). HAL, maybe? Do you know which script calls for /etc/init.d/gdm start? Thanks!

---

### Post by m4r4g4t0 on 2010-03-26
I've tracked the problem down.

I have created two text files; One with the output from ps xa before GDM starts and one after it comes up.

Comparing both files, I've found out that "udevadm settle" along with lots of "udevd --daemon" processes.

Doing a grep -lrs "udevadm settle" under /etc, I've found out that /etc/init/udevtrigger.conf calls it. Adding a "&" after the command made GDM start normally after a reboot.

Now I'm gonna remove that "&" and see what happens on /var/log/udev...

---

### Post by m4r4g4t0 on 2010-03-26
A tail -f on /var/log/udev shows it's stuck with the /module/binfmt_misc thing. But it doesn't go any further after GDM goes on. So I think /module/binfmt_misc is not the problem.

Booting with the previous kernel version, the problem doesn't happen at all.

Looks like I'm gonna have to live with the ugly solution of calling udevadm settle in the background until I get new updates to test, or keep using the old kernel for a while.

---

### Post by m4r4g4t0 on 2010-03-26
Wow! Booting with the old kernel leaves me with no sound, no network device...

Ugly solution... ACTIVATED!!

---

