---
title: "Upgraded to Jaunty, and &quot;Extra&quot; keyboard keys not working"
date: 2009-02-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by markjensen on 2009-02-14
I just upgraded (sudo update-manager -d) and the extended keys I had previously assigned to start up specific apps are not working.

I am using Xubuntu with fluxbox as my WM of choice.   I am familiar with editing the ~/.fluxbox/keys file to enter the keycodes as reported by xev to make these extra keys (like browser, email, etc) do what I need them to do.   However, now that I have upgraded to the Alphas of Jaunty, xev isn't reporting **anything** for events when I press these keys.

My keyboard is a Logitech Cordless EX110, and it worked fine previously.

As a bit of background, when I did an upgrade though the package manager from 8.04 to 8.10, the extra keys would not initially work because (for reasons I did not care to investigate) the keycodes, as reported by xev, changed on me.

At that time, I just fired up xev, and modified my keys file to the new values reported under 8.10.   However, this time, there are no events reported by xev when I press these extended keys.   Would that indicate a config issue in my xorg.conf file?

I am attaching an old xorg, the new one, and my fluxbox keys file, so you can see the lines I added right at the end to use these extra keys.

---

### Post by cariboo on 2009-02-14
The correct place for this post is [Jaunty Jackalope Testing and Disscussion]("http://ubuntuforums.org/forumdisplay.php?f=352"). I have asked the mods to move this post there.

Jim

---

### Post by bapoumba on 2009-02-14
So moved, thanks cariboo :)

---

### Post by olskar on 2009-02-14
I have the same problem with a Deltaco Keyboard

---

### Post by conehead77 on 2009-02-15
I have the same problem with a Logitech Cordless keyboard.

There is a bug report about media keys not working: [https://bugs.launchpad.net/ubuntu/+bug/328502](https://bugs.launchpad.net/ubuntu/+bug/328502)
Maybe we get some attention when we post there :)

---

### Post by markjensen on 2009-02-15
> **conehead77 said:**
> I have the same problem with a Logitech Cordless keyboard.

There is a bug report about media keys not working: [https://bugs.launchpad.net/ubuntu/+bug/328502](https://bugs.launchpad.net/ubuntu/+bug/328502)
Maybe we get some attention when we post there :)

Good idea.  I put what I know in a post there, and attached my xorg.conf file, which might contain important information since this is an issue with X and the keyboard.

---

### Post by markjensen on 2009-02-23
Just to update the thread, a recent update to the development releases of Jaunty fixed this issued.

---

