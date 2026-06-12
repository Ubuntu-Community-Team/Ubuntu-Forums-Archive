---
title: "Installing Gnome from Terminal"
date: 2005-10-27
forum: Installation &amp; Upgrades
---

### Post by greymoose58 on 2005-10-27
I'm in the process of trying to set a machine up for a friend. I have run Hoary on it in my office. The only change I made to the configuration was to replace 2x 1.2 GB hard drives with a 1x 2.1GB drive.

I had a similar problem to this thread: [http://www.ubuntuforums.org/showthread.php?t=77101](http://www.ubuntuforums.org/showthread.php?t=77101) but it stopped at 17% and repeated 'configuring base system' forever.

So I installed the base system using the 'server' install option and set about installing Gnome separately. I used apt-get to install gdm thinking it would take care of the dependancies - no luck. I then installed x-server (I think I got a message saying it was missing). I still can't get either x-server or gdm to start.

I'm sure I've seen instructions about how to do this but I can't find them anywhere.

Does anyone know where I can find them? Or what I need to do?

Thanks.

---

### Post by Chris Cromer on 2005-10-27
Not sure if this will work, but try:

```
sudo apt-get install ubuntu-desktop
```

I see it has all the dependencies for things needed by gnome, so hopefully installing that should get gnome setup for you.

---

### Post by greymoose58 on 2005-11-18
[QUOTE=Chris Cromer]

```
sudo apt-get install ubuntu-desktop
```

[/QUOTE]

Thanks for the great advice. It did the trick. A word of warning to anyone else though: Installing Ubuntu desktop this way took an extra 1.2Gb of space on top of the base system.

---

