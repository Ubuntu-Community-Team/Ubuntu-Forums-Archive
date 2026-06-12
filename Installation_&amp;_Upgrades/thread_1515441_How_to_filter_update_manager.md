---
title: "How to filter update manager"
date: 2010-06-22
forum: Installation &amp; Upgrades
---

### Post by txtinman on 2010-06-22
I would like to be able to filter what software the update manager updates. For instance, I don't use Evolution so I would like all evolution related programs to not show up on the update manager screen. Right now I have to manually uncheck the programs I don't want to update. 

Mike White

---

### Post by arubislander on 2010-06-22
I'm not sure not updating stuff you don't use is a good idea... I'd at least always apply the security updates. Even on apps that I don't use but can't/won't uninstall. Security vulnerabilities could be exploited even in apps that you don't actively use.

---

### Post by tommcd on 2010-06-22
> **txtinman said:**
> I would like to be able to filter what software the update manager updates. For instance, I don't use Evolution so I would like all evolution related programs to not show up on the update manager screen.
Why not do it the simple way??
Simply uninstall evolution:
```
sudo apt-get remove --purge evolution
```
You will then no longer have to bother with evolution updates.
Evolution is not an integral part of Ubuntu, or any linux distro. It is just an email app.

---

### Post by snowpine on 2010-06-22
You only *think* you don't use Evolution; it is used to display (a "dependency" of) the clock/calendar on your Gnome panel. You should either keep Evolution up to date or uninstall it if you're *sure* you don't need it; there is zero benefit to maintaining a Linux system that is a mix of updated and outdated packages. :)

---

### Post by tommcd on 2010-06-22
> **snowpine said:**
> You only *think* you don't use Evolution; it is used to display (a "dependency" of) the clock/calendar on your Gnome panel
I have uninstalled evolution using the command I posted in my last post.
My calendar on the Gnome panel still works.
I don't actually use the calendar to schedule appointments or stuff like that. Is there some functionality that would be missing if evolution is uninstalled?
If you would rather blacklist than uninstall evolution, see this:
[http://ubuntuforums.org/showthread.php?t=464448](http://ubuntuforums.org/showthread.php?t=464448)
However, this may lead to other problems with upgrading other packages due to the way APT handles dependencies.
You have discovered the dark side to dependency management in linux!!

---

### Post by snowpine on 2010-06-22
> **tommcd said:**
> I have uninstalled evolution using the command I posted in my last post.
My calendar on the Gnome panel still works.
I don't actually use the calendar to schedule appointments or stuff like that. Is there some functionality that would be missing if evolution is uninstalled?

I don't think it will be a problem in your case. :) The point I was trying to make is that the user should not try to selectively determine which updates are needed and which are not. A package that you don't think you use might actually be an unexpected dependency of an application that you use every day. It is better to apply all updates than to partially update and keep certain obsolete packages on your system. Let the Update Manager do its thing. In my opinion of course. ;)

---

### Post by tommcd on 2010-06-22
> **snowpine said:**
> I don't think it will be a problem in your case. :) The point I was trying to make is that the user should not try to selectively determine which updates are needed and which are not. A package that you don't think you use might actually be an unexpected dependency of an application that you use every day.
Of course, before uninstalling any package, one should investigate the potential consequences. My point was that many of the apps that are packaged with Ubuntu are not essential and can be removed.

In this particular case, evolution can easily be reinstalled.

---

