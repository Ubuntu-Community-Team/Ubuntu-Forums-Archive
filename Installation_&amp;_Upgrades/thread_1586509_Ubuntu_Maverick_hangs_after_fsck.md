---
title: "Ubuntu Maverick hangs after fsck"
date: 2010-10-02
forum: Installation &amp; Upgrades
---

### Post by orador on 2010-10-02
Hello everyone,
yesterday I ran into serious trouble. When I rebooted my Ubuntu machine, fsck took place - I hit cancel as I had no time for that. Than the boot halted. I'm unable to boot ever since. It doesn't matter which kernel I run. There is no error indication whatsoever. My system is Ubuntu Maverick 64-bit, clean beta1 install, no troubles so far. I hadn't done any package update right before it happened.

I tried disabling fsck but wouldn't help. I found similar problems, but nothing exactly like this.

My boot proccess looks like this:
```

Begin: Loading essential drivers ... done.
Begin: Running /scripts/init-premount ... done.
Begin: Mounting root file system ... Begin: Running /scripts/local-top ...done.
Begin: Running /scripts/local-premount ... done.
[    2.615248] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    2.615436] EXT4-fs (sda1): write access will be enabled during recovery
[2.685849] EXT4-fs (sda1): recovery complete
[2.686224] EXT4-fs (sda1): mounted filesystems with ordered data mode. Opts: (null)
Begin: Running /scripts/local-bottom ... done.
done.
Begin: Running /scripts/init-bottom ... done.
fsck from util-linux-ng 2.17.2
/dev/sda1: clean, xxx/xxx files, xxx/xxx blocks

```

And that's it, every time. Does anyone knows, what might be wrong?

Thanks in advance.

---

### Post by wojox on 2010-10-02
> tommorow I ran into serious trouble.

Are you from the future?

---

### Post by orador on 2010-10-02
:-D Not really. More likely explanation is, that I was thinking about something else, when I post the question. I certainly amused myself.

---

### Post by wojox on 2010-10-02
HOw far do you make it before it putter's out? Can you force a fsck?

---

### Post by orador on 2010-10-02
I suppose, I can't, the lines I posted are the last I get. But the fsck ran automatically one time and it didn't solve anything. I also tried fsck -y /dev/sda1 from live cd, no errors there.

---

### Post by santana007 on 2010-10-03
Your problem is not quite the same as the one I had. My system would freeze at the login screen. My prayers were answered in this thread: ```
http://ubuntuforums.org/showthread.php?t=1584931
```Perhaps the above will  help

---

### Post by sendmoreinfo on 2010-12-27
This looks like [https://bugs.launchpad.net/bugs/563916](https://bugs.launchpad.net/bugs/563916) -- Ubuntu expects you to answer the invisible question ;-)

---

### Post by YetiChick on 2011-01-26
I know it's late, but for the sake of future searches:

This happened to me because while setting up networking I got a bit overzealous with CTRL-K and accidentally deleted the lo interface from /etc/network/interfaces.

Put it back in:

# The loopback network interface
auto lo
iface lo inet loopback


and all was well.

Hope this helps someone.

---

