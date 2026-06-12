---
title: "Auto-login: passwords, passwords.  How to avoid them?"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hexsel on 2009-10-06
This has irritated me for a while.  When I put my machine in auto-login, it is OBVIOUS I consider it to be a in safe-enough environment or just care more for ease-of-use than my oh-so-beloved MSN account password security.

Does anyone know how I can disable:
- password asking for missioncontrol/empathy? (yes, I would prefer  plain-text if I had the option)
- password asking when I close the lid of my laptop?

Thanks!

---

### Post by kaitwospirit on 2009-10-06
Can't help you with the laptop lid question.

What exactly is Empathy doing to ask for your password repeatedly? Is it doing so every time that you start up the program?

---

### Post by dalonso on 2009-10-06
> **hexsel said:**
> This has irritated me for a while.  When I put my machine in auto-login, it is OBVIOUS I consider it to be a in safe-enough environment or just care more for ease-of-use than my oh-so-beloved MSN account password security.

Does anyone know how I can disable:
- password asking for missioncontrol/empathy? (yes, I would prefer  plain-text if I had the option)
- password asking when I close the lid of my laptop?

Thanks!

Could you please try if the procedure explained in this other thread comment works for you:

[http://ubuntuforums.org/showpost.php?p=7271195&postcount=7](http://ubuntuforums.org/showpost.php?p=7271195&postcount=7):

> 1. run gconf-editor (NOT as root -- gconf-editor edits per-user settings)
> 2. navigate to apps / gnome-power-manager / lock
> 3. uncheck the locks for suspend and hibernate, and everything else

Best regards.

---

### Post by Dougie187 on 2009-10-06
I think you might be able to find the lock for the laptop lid in System->Preferences->Power Management. But I don't know if it's there in karmic, worth a shot though.

---

### Post by gali98 on 2009-10-06
@Dougie187
I also thought there was an option in there, but I cannot find it here on Karmic. Maybe it was taken out from Jaunty?
Kory

---

### Post by ikt on 2009-10-06
> **hexsel said:**
> Does anyone know how I can disable:
- password asking for missioncontrol/empathy? (yes, I would prefer  plain-text if I had the option)

[https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/437065](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/437065)

Is a bug.

---

### Post by cantab on 2009-10-06
> **hexsel said:**
> This has irritated me for a while.  When I put my machine in auto-login, it is OBVIOUS I consider it to be a in safe-enough environment or just care more for ease-of-use than my oh-so-beloved MSN account password security.

Someone might choose autologin because they have a boot password at the bios level. Uncommon, but possible. Thus, just because one point at which passwords would be requested is disabled doesn't mean they necessarily all should be.

---

### Post by hexsel on 2009-10-07
> **cantab said:**
> Someone might choose autologin because they have a boot password at the bios level. Uncommon, but possible. Thus, just because one point at which passwords would be requested is disabled doesn't mean they necessarily all should be.

That would not even be the same password.  Not very Gnome-ish, but yeah, it's possible.

---

### Post by hexsel on 2009-10-07
Hey, thanks all for the answers.  I've subscribed to the bug and the gnome-config settings fixed the problem of suspend, restart.

Wouldn't have found it except for you guys!

---

