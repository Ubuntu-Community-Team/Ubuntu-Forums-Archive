---
title: "Software Updates frozen but not really?"
date: 2012-03-11
forum: Installation &amp; Upgrades
---

### Post by JustinR on 2012-03-11
Hey everybody,

Just installed Kubuntu 11.10 onto an HP Mini 110 w/ a Intel Atom 1.6GHZ processor and 1GB of ram.

It runs fine, but when I started the update through Muon Software Center it started updating but stopped working at "Preparing to configure plasma-widgets-workspace" at 43%.

It's not frozen, everything on the computer still works, keyboard + mouse, switching terminals and even opening new applications. The kickstarter menu is empty, no applications show up.

The DPKG.log in /var/log/dpkg.log shows it successfully unpacked libnm-glib4 0.9.1.90-0ubuntu5.1, at 5:01 PM my time, and it's been over an hour and it's still like this.

I can't shutdown, restart, logout, etc; the action is canceled by muon software center.

Should I just wait it out or is there anything I can do to check the progress? Thanks.

---

### Post by whatthefunk on 2012-03-11
I had the same thing happen yesterday.  You cant shut down at all?  Did you try to shutdown through the terminal?

```
sudo shutdown -r now
```

You basically need to get rid of muon so that you can complete the process through the terminal.

```
sudo dpkg --configure -a
```

That should finish the job.

---

### Post by JustinR on 2012-03-11
> **whatthefunk said:**
> I had the same thing happen yesterday.  You cant shut down at all?  Did you try to shutdown through the terminal?

```
sudo shutdown -r now
```

You basically need to get rid of muon so that you can complete the process through the terminal.

```
sudo dpkg --configure -a
```

That should finish the job.

It wouldn't let me shutdown graphically, but in the end I just did sudo shtudown -r now, it restarted but the keyboard and mouse stopped working.

In the end I just reinstalled and updated through the terminal than Muon.
Thanks for the help though, it Muon every freezes again I'll exit and repair dpkg with the code above.

Thanks.

---

