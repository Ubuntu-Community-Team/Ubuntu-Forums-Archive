---
title: "Flash - no sound"
date: 2010-04-25
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by lerrup on 2010-04-25
Flash would show video but no sound,this was the case with all sites including iplayer,you tube,etc - no sound.  This was on 2 computers, an upgrade from Karmic and a new installation (with an old Home directory).

I tried all the solutions I could find on the net,but these didn't work.  However, a new user did have sound with flash.  Odd.

The solution is to delete any plugin with the word "flash" in it (such as libflashplugin.so) that is in the /home/[user]/.mozilla/plugins directory.  Restart firefox and you can hear all the singing dogs that you want.

I am posting this just in case it helps someone.

---

### Post by Didius Falco on 2010-04-25
Thanks for taking the time to report both the problem and a solution.

Please mark this thread solved - that will help others searching for a solution to find it.

Regards,

Didius

---

### Post by RickyCodes on 2010-04-25
> **lerrup said:**
> Flash would show video but no sound,this was the case with all sites including iplayer,you tube,etc - no sound.  This was on 2 computers, an upgrade from Karmic and a new installation (with an old Home directory).

I tried all the solutions I could find on the net,but these didn't work.  However, a new user did have sound with flash.  Odd.

The solution is to delete any plugin with the word "flash" in it (such as libflashplugin.so) that is in the /home/[user]/.mozilla/plugins directory.  Restart firefox and you can hear all the singing dogs that you want.

I am posting this just in case it helps someone.


Are you using 64bit by any chance. Also having trouble with flash not being able to control the volume or placement of video. Was reading flash has a beta for 64bit systems.

---

### Post by cariboo on 2010-04-25
Try the [script]("http://ubuntuforums.org/showthread.php?t=1358591") in this post to install the 64-bit version.

---

### Post by lerrup on 2010-04-25
> **RickyCodes said:**
> Are you using 64bit by any chance. Also having trouble with flash not being able to control the volume or placement of video. Was reading flash has a beta for 64bit systems.

No -32 bit.

It's an old configuration problem.

---

### Post by lovinglinux on 2010-04-25
> **lerrup said:**
> No -32 bit.

It's an old configuration problem.

See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by lerrup on 2010-04-25
> **lovinglinux said:**
> See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

Thanks for the link, but this particular problem was due to a file that dated back to 2007 when I originally installed Ubuntu on both computers.  It was this that caused sound to die so when it was deleted I was able to hear again.

I do not know why!

Other than that everything works well.

---

