---
title: "I'm not even getting to the login screen"
date: 2010-01-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by NCLI on 2010-01-05
I just boot straight to a CLI. By removing "quiet splash" from the grub boot line, I was able to find... nothing. Only the usual "mountall: Could not connect to Plymouth", and: "run-parts: /etc/update-motd.d/91-release-upgrade exited with return code 1", which I've heard people who have done a fresh install have had as well.

The strange thing is that first, I did an upgrade, which crashed without finishing. I was then able to easily get to the graphical desktop and run "sudo aptitude safe-upgrade". I rebooted, and then this happened... I did notice that it updated xorg-xserver-nv-driver, which I don't need on my netbook, as it is intel-based. Removing it changed nothing though.

I have also tried a fresh install, though that was before A1.

---

### Post by ronacc on 2010-01-05
if you can ,check to see that your xserver-xorg is still there , an update the other day took that out on me , I ended up having to reinstall . if you can get to a cmd line try running 
```
 sudo apt-get update 
```
and then 
```
sudo apt-get -f install 
```
the -f tells it to fix broken pkgs .

---

### Post by NCLI on 2010-01-06
Ok, finally got in by running "sudo start gdm", but now I'm in low-graphics mode :(

@ronacc: Nope, no effect.

---

### Post by NCLI on 2010-01-06
Does anyone have any idea what could be causing this? If not, I guess I'll report a bug in a few hours.

---

### Post by LKjell on 2010-01-06
I would try to reinstall xorg and remove /etc/X11/xorg.conf file if you have it.

---

### Post by NCLI on 2010-01-06
No Xorg file. If there was one, I'd be able to fix this myself :(

---

### Post by LKjell on 2010-01-06
Well then create one?

---

### Post by VMC on 2010-01-06
> **NCLI said:**
> Does anyone have any idea what could be causing this? If not, I guess I'll report a bug in a few hours.

This is exactly the same problem I'm having with Kubuntu Lucid. I think I have a fix on it. I also noticed right after the Plymouth line I'm brought to a text log in prompt.

---

### Post by caryb on 2010-01-06
Ditto!

---

### Post by NCLI on 2010-01-07
> **VMC said:**
> This is exactly the same problem I'm having with Kubuntu Lucid. I think I have a fix on it. I also noticed right after the Plymouth line I'm brought to a text log in prompt.
What's the fix? :)

> **LKjell said:**
> Well then create one?
If I knew the command to do so, sure, but everything's changed with Xorg recently.

---

### Post by b3t0n on 2010-01-07
Hello. I'm also encountering problem with login screen. Seems that after updating packages yesterday, GDM won't start.
```
root@b3t0n-desktop:/home/b3t0n# gdm
gdm[1906]: ******************* START **********************************
gdm[1906]: [Thread debugging using libthread_db enabled]
gdm[1906]: 0x00cc3422 in __kernel_vsyscall ()
gdm[1906]: #0  0x00cc3422 in __kernel_vsyscall ()
gdm[1906]: #1  0x0069bd23 in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
gdm[1906]: #2  0x08066b19 in ?? ()
gdm[1906]: #3  0x08066c11 in ?? ()
gdm[1906]: #4  <signal handler called>
gdm[1906]: #5  0x00433043 in strchr () from /lib/tls/i686/cmov/libc.so.6
gdm[1906]: #6  0x08059472 in ?? ()
gdm[1906]: #7  0x0805bda2 in ?? ()
gdm[1906]: #8  0x0805c253 in ?? ()
gdm[1906]: #9  0x00155251 in ?? () from /lib/libglib-2.0.so.0
gdm[1906]: #10 0x00156fd8 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
gdm[1906]: #11 0x0015a880 in ?? () from /lib/libglib-2.0.so.0
gdm[1906]: #12 0x0015acef in g_main_loop_run () from /lib/libglib-2.0.so.0
gdm[1906]: #13 0x0804eb08 in ?? ()
gdm[1906]: #14 0x003d6bd6 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
gdm[1906]: #15 0x0804dd81 in ?? ()
gdm[1906]: 
gdm[1906]: Thread 1 (Thread 0xb776d720 (LWP 1899)):
gdm[1906]: #0  0x00cc3422 in __kernel_vsyscall ()
gdm[1906]: No symbol table info available.
gdm[1906]: #1  0x0069bd23 in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
gdm[1906]: No symbol table info available.
gdm[1906]: #2  0x08066b19 in ?? ()
gdm[1906]: No symbol table info available.
gdm[1906]: #3  0x08066c11 in ?? ()
gdm[1906]: No symbol table info available.
gdm[1906]: #4  <signal handler called>
gdm[1906]: No symbol table info available.
gdm[1906]: #5  0x00433043 in strchr () from /lib/tls/i686/cmov/libc.so.6
gdm[1906]: No symbol table info available.
gdm[1906]: #6  0x08059472 in ?? ()
gdm[1906]: No symbol table info available.
gdm[1906]: #7  0x0805bda2 in ?? ()
gdm[1906]: No symbol table info available.
gdm[1906]: #8  0x0805c253 in ?? ()
gdm[1906]: No symbol table info available.
gdm[1906]: #9  0x00155251 in ?? () from /lib/libglib-2.0.so.0
gdm[1906]: No symbol table info available.
gdm[1906]: #10 0x00156fd8 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
gdm[1906]: No symbol table info available.
gdm[1906]: #11 0x0015a880 in ?? () from /lib/libglib-2.0.so.0
gdm[1906]: No symbol table info available.
gdm[1906]: #12 0x0015acef in g_main_loop_run () from /lib/libglib-2.0.so.0
gdm[1906]: No symbol table info available.
gdm[1906]: #13 0x0804eb08 in ?? ()
gdm[1906]: No symbol table info available.
gdm[1906]: #14 0x003d6bd6 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
gdm[1906]: No symbol table info available.
gdm[1906]: #15 0x0804dd81 in ?? ()
gdm[1906]: No symbol table info available.
gdm[1906]: A debugging session is active.
gdm[1906]: 
gdm[1906]: 	Inferior 1 [process 1899] will be detached.
gdm[1906]: 
gdm[1906]: Quit anyway? (y or n) [answered Y; input not from terminal]

```

Is it caused by different packages versions, do I have to wait for other debs to update?

Oh yeah. I used apt-get update and then apt-get upgrade so I have new packages from repository.

EDIT: Running```
locale-gen --purge
```seems to solve the issue.

---

### Post by VMC on 2010-01-07
> **NCLI said:**
> What's the fix?The [**fix**]("http://ubuntuforums.org/showpost.php?p=8621023&postcount=8") is for Kubuntu. I checked Ubuntu equivalent file gdm.conf. It doesn't reference hal.

---

