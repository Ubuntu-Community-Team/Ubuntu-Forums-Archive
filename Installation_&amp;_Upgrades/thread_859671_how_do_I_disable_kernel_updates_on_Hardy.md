---
title: "how do I disable kernel updates on Hardy?"
date: 2008-07-14
forum: Installation &amp; Upgrades
---

### Post by potiphera on 2008-07-14
I've read [this]("http://ubuntuforums.org/showthread.php?t=242242") old thread, but I still don't understand how to do it, really.  I read man apt_preferences but it didn't make much sense to me.  Basically I want to disable kernel upgrades in the Update Manager and any package managers on this computer, unless I specifically choose to update the kernel (because changing the kernel breaks the only video driver that I've gotten working, and then I have to recompile it).  How do I do this?  Thanks!

---

### Post by iaculallad on 2008-07-14
> **potiphera said:**
> I've read [this]("http://ubuntuforums.org/showthread.php?t=242242") old thread, but I still don't understand how to do it, really.  I read man apt_preferences but it didn't make much sense to me.  Basically I want to disable kernel upgrades in the Update Manager and any package managers on this computer, unless I specifically choose to update the kernel (because changing the kernel breaks the only video driver that I've gotten working, and then I have to recompile it).  How do I do this?  Thanks!

Try this if it works with you:

Create /etc/apt/preferences with the lines of texts below as it's content:

```
gksudo gedit /etc/apt/preferences
```

Preference's content:

> Package: 1001
Pin-Priority: 1001


---

### Post by jimv on 2008-07-14
Seems like you just would not install the new kernels when they come out.  If you're using the update manager, just uncheck them.

If you're using apt, don't use apt-get dist-upgrade.

---

### Post by potiphera on 2008-07-15
iaculallad: Thanks, I'll try that.  What does Package: 1001 mean?  I was under the impression that "Package" had to be followed by a name.

jimv: Yeah, I would probably do that if it were my computer, but it's not, so I'm trying to make things easy for the user.

---

### Post by sdennie on 2008-07-15
Are you talking about breaking a manually installed nvidia driver when the kernel updates?  If so, see this thread: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573).  You can adapt that to just about any driver (I also use it for VirtualBox drivers).

---

### Post by iaculallad on 2008-07-15
> **potiphera said:**
> iaculallad: Thanks, I'll try that.  What does Package: 1001 mean?  I was under the impression that "Package" had to be followed by a name.

My error. That proper format should be:

 ```
    Package: <package>
     Pin: <pin definition>
     Pin-Priority: <pin's priority>
```

---

### Post by potiphera on 2008-07-15
> **vor said:**
> Are you talking about breaking a manually installed nvidia driver when the kernel updates?  If so, see this thread: [http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573).  You can adapt that to just about any driver (I also use it for VirtualBox drivers).Yeah, that is the issue.  Thanks a lot -- I haven't tried your howto yet, but it looks like an excellent solution! Also, this is a Dell XPS m1330, so it looks like some of the other threads linked in your signature could be of use as well.

---

### Post by potiphera on 2008-07-16
Just followed **vor**'s howto and it did the trick! Looks like this issue is solved for me.

---

### Post by sdennie on 2008-07-16
> **potiphera said:**
> Just followed **vor**'s howto and it did the trick! Looks like this issue is solved for me.

Glad it worked.  Hopefully nvidia will include something similar in a future driver release.

---

