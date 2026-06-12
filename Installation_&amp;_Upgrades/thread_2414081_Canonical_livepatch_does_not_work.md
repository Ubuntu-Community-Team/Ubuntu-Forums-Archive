---
title: "Canonical livepatch does not work?"
date: 2019-03-05
forum: Installation &amp; Upgrades
---

### Post by joehack on 2019-03-05
I am wondering, why the Canonical livepatch mechanism does not work. It suppose to check and if needed update every 60 minutes (default setting).

However, today I got the a new kernel version (linux-generic/bionic-security 4.15.0.46.48). But when I execute ```
sudo canonical-livepatch status --verbose
```, I get the following output:
```
client-version: 8.2.0
machine-id: XXX
machine-token: XXX
architecture: x86_64
cpu-model: Intel(R) Celeron(R) CPU  N3150  @ 1.60GHz
last-check: 2019-03-05T18:33:14+01:00
boot-time: 2019-01-31T22:08:05+01:00
uptime: 789h4m25s
status:
- kernel: 4.15.0-45.48-generic
  running: true
  livepatch:
    checkState: checked
    patchState: nothing-to-apply
    version: ""
    fixes: ""
```


I thought, I could force the installation running ```
sudo canonical-livepatch status refresh
```, unfortunately without success:
```
client-version: 8.2.0
architecture: x86_64
cpu-model: Intel(R) Celeron(R) CPU  N3150  @ 1.60GHz
last-check: 2019-03-05T18:33:14+01:00
boot-time: 2019-01-31T22:08:05+01:00
uptime: 789h4m34s
status:
- kernel: 4.15.0-45.48-generic
  running: true
  livepatch:
    checkState: checked
    patchState: nothing-to-apply
    version: ""
    fixes: ""

```

Do I get something wrong here?

---

### Post by PaulW2U on 2019-03-06
You still need to reboot if you are advised by the Software Updater that a new kernel version is available. It appears that you last rebooted on 31st January which is why you still have the 4.15.0-45.48 kernel. 

Enabling livepatch doesn't negate the need to reboot as not all updates can be applied by patching. I seldom check my livepatch output but when I do I usually see that there is nothing to apply. Only once have I seen anything listed against 'fixes' and that was a short list of CVEs which were removed from the listing when I next updated the kernel by rebooting.

This is my current livepatch status:
```
paul@N1642:~$ canonical-livepatch status 
client-version: 8.2.0
architecture: x86_64
cpu-model: Intel(R) Core(TM) i3-7100T CPU @ 3.40GHz
last-check: 2019-03-06T09:39:43Z
boot-time: 2019-03-06T09:02:51Z
uptime: 37m7s
status:
- kernel: 4.15.0-46.49-generic
  running: true
  livepatch:
    checkState: checked
    patchState: nothing-to-apply
    version: ""
    fixes: ""
```

Quoting from the [Livepatch]("https://wiki.ubuntu.com/Kernel/Livepatch") wiki page:
> Since there are limitations to the kernel livepatch technology, some Linux kernel code paths cannot be safely patched while running. There may be occasions when the traditional kernel upgrade and reboot might still be necessary.
Does that help?

---

### Post by mtodorov69 on 2019-03-07
Hi PaulW2U,

Where could we see the list of patches which were implemented live?

IMHO canonical-livepatch should notify the client if some patches are not installable in live mode and require reboot. The way it is done it feels a bit deaf and dumb.

Thanks,

---

### Post by PaulW2U on 2019-03-07
> **mtodorov69 said:**
> Where could we see the list of patches which were implemented live?
I can't help with that one I'm afraid but the announcements are made on the [Ubuntu Security Announce]("https://lists.ubuntu.com/mailman/listinfo/ubuntu-security-announce") mailing list.

[LSN-0044-1]("https://lists.ubuntu.com/archives/ubuntu-security-announce/2018-October/004611.html") is an example of such an announcement.

---

### Post by mtodorov69 on 2019-03-11
I've just seen the size of the changes and I can understand if a patch this big cannot be live patched.

[https://launchpad.net/ubuntu/+source/linux/4.15.0-46.49](https://launchpad.net/ubuntu/+source/linux/4.15.0-46.49)

---

